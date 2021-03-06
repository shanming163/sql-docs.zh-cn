---
title: 配置报表服务器以进行远程管理 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services Configuration tool
- WMI provider [Reporting Services], remote configuration
- configuration management [WMI]
- report servers [Reporting Services], configuring
- remote server administration [Reporting Services]
ms.assetid: 8c7f145f-3ac2-4203-8cd6-2a4694395d09
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: f778380427f0c542346442a6f694b87a04d4dd80
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "48159543"
---
# <a name="configure-a-report-server-for-remote-administration"></a>配置报表服务器以进行远程管理
  在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]中，您可以通过本地或远程方式配置报表服务器实例。 若要配置远程报表服务器实例，可以使用 Reporting Services 配置工具或编写使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Windows Management Instrumentation (WMI) 提供程序的自定义代码。 Reporting Services 配置工具为 WMI 提供程序提供了一个图形界面，这样您便可以直接配置报表服务器，而不必编写代码。 启动该工具时，可以指定要连接的远程服务器。  
  
 在可以使用该工具配置远程报表服务器之前，必须按照本主题中的说明在 Windows 防火墙中启用端口、启用远程连接并启用远程 WMI 请求。  
  
 正确的配置可帮助您避免出现以下错误：  
  
 `The machine could not be found.`  
  
 `"The RPC server is unavailable. (Exception from HRESULT: 0x800706BA)".`  
  
## <a name="prerequisites"></a>必要條件  
 若要修改防火墙设置，必须从本地登录，并且您必须是本地 Administrators 组的成员。 不能通过远程连接来修改远程计算机的 Windows 防火墙设置。  
  
 如果要为非管理员用户启用远程管理，则必须为该帐户授予对分布式组件对象模型 (DCOM) 的远程激活权限。 本主题提供了有关配置服务器以供非管理员访问的说明。  
  
 某些组织的组策略阻止某些操作系统或用户进行远程服务器管理。 开始修改防火墙设置之前，请与网络管理员进行核实，以确认是否存在对远程管理的限制。  
  
 有关详细信息，请参阅 MSDN 上 Platform SDK 文档中的 [Connecting Through Windows Firewall](http://go.microsoft.com/fwlink/?LinkId=63615) （通过 Windows 防火墙连接）。  
  
## <a name="tasks"></a>“任务”  
 启用远程报表服务器配置的任务包括：  
  
-   在 Windows 防火墙中启用端口以允许报表服务器和 SQL Server 数据库引擎实例所使用的端口的请求。  
  
-   启用与承载报表服务器数据库的数据库引擎实例之间的远程连接。 远程连接是配置报表服务器数据库连接和管理加密密钥所必需的。  
  
-   启用远程 WMI 请求以通过 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 防火墙。  
  
-   如果要配置远程报表服务器以便由非管理用户进行管理，则必须设置 DCOM 权限以启用对标准 Windows 用户帐户的远程 WMI 访问。 由于 WMI 使用 DCOM 作为远程调用传输方式，因此必须设置 DCOM 权限，以使不是以本地管理员身份登录的用户可以配置服务器。  
  
-   如果要配置远程报表服务器以便由非管理用户进行管理，则还必须设置对报表服务器 WMI 命名空间的 WMI 权限。 默认情况下，本地管理员组的所有成员都有权访问报表服务器 WMI 命名空间。 如果要对非管理员授予访问权限，则必须设置权限。  
  
 本主题中提供了有关如何执行这些任务的说明。  
  
### <a name="to-open-ports-in-windows-firewall"></a>在 Windows 防火墙中打开端口  
  
1.  [为数据库引擎访问配置 Windows 防火墙](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)。  
  
2.  [为报表服务器访问配置防火墙](configure-a-firewall-for-report-server-access.md)。  
  
### <a name="to-configure-remote-connections-to-the-report-server-database"></a>配置与报表服务器数据库的远程连接  
  
1.  单击 **“开始”**，依次指向 **“程序”**、 [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]、 **“配置工具”**，然后单击 **“SQL Server 配置管理器”**。  
  
2.  在左窗格中，展开“SQL Server 网络配置”，然后针对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例单击“协议”。  
  
3.  在详细信息窗格中，启用“TCP/IP”和“命名管道”协议，然后重启 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务。  
  
### <a name="to-enable-remote-administration-in-windows-firewall"></a>在 Windows 防火墙中启用远程管理  
  
1.  以本地管理员身份登录要启用远程管理功能的计算机。  
  
2.  如果报表服务器正在运行 Windows Vista 上，右键单击**命令提示符**，然后选择**以管理员身份运行**。 对于其他操作系统，请打开一个命令提示符窗口。  
  
3.  运行以下命令：  
  
    ```  
    netsh.exe firewall set service type=REMOTEADMIN mode=ENABLE scope=ALL  
    ```  
  
     可以指定不同的作用域选项。 有关详细信息，请参阅 Windows 防火墙产品文档。  
  
4.  验证是否已启用远程管理。 可以运行以下命令以显示状态：  
  
    ```  
    netsh.exe firewall show state  
    ```  
  
5.  重新启动计算机。  
  
### <a name="to-set-dcom-permissions-to-enable-remote-wmi-access-for-non-administrators"></a>设置 DCOM 权限为非管理员启用远程 WMI 访问  
  
1.  在“开始”菜单中，指向 **“管理工具”**，单击 **“组件服务”**。  
  
     对于 Windows Vista 中，在开始菜单中，单击**所有程序**，单击**运行**，然后输入`mmc comexp.msc`。  
  
2.  打开“组件服务”文件夹。  
  
3.  打开“计算机”文件夹。  
  
4.  选择“我的电脑”。  
  
5.  在 **“操作”** 菜单中，选择 **“属性”**。  
  
6.  单击 **“COM 安全”**。  
  
7.  在 **“启动和激活权限”** 中单击 **“编辑限制”**。  
  
8.  如果在 **“启动权限”** 中没有看到您的名称，请单击 **“添加”**。  
  
9. 键入您的用户帐户名，然后单击 **“确定”**。  
  
10. 在“\<用户或组> 权限”的“允许”列中，选择“远程启动”和“远程激活”，然后单击“确定”。  
  
### <a name="to-set-permissions-on-the-report-server-wmi-namespace-for-non-administrators"></a>为非管理员设置报表服务器 WMI 命名空间的权限  
  
1.  在“开始”菜单中，指向 **“管理工具”**，单击 **“计算机管理”**。  
  
2.  打开“服务和应用程序”文件夹。  
  
3.  右键单击“WMI 控件”，然后选择“属性”。  
  
4.  单击 **“安全性”**。  
  
5.  打开 Root 文件夹。  
  
6.  打开 Microsoft 文件夹。  
  
7.  打开 SQLServer 文件夹。  
  
8.  打开 ReportServer 文件夹。  
  
9. 打开实例文件夹。 如果安装了默认实例，则文件夹为 MSSQLSERVER。  
  
10. 打开 v10 文件夹。  
  
11. 选中 Admin 文件夹，然后单击 **“安全性”**。  
  
12. 单击 **“添加”**，然后键入将用于管理服务器的用户帐户。  
  
13. 在 **“允许”** 列中，选择 **“启用帐户”**、 **“远程启用”** 和 **“读取安全”**，然后单击 **“确定”**。  
  
## <a name="see-also"></a>请参阅  
 [Reporting Services Configuration Manager（本机模式）](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
