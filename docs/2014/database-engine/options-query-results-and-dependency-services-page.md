---
title: 选项 （查询结果和依赖关系服务页） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryResults.DependencyServicesGeneral
ms.assetid: dd7f6c31-7d7f-4972-854a-1419a2826dca
author: mashamsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8f587ee792809f9612ca9fca1264794e843172a0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "48118617"
---
# <a name="options-query-results-and-dependency-services-page"></a>选项（“查询结果”和“依赖关系服务”页）
  使用此页可为依赖关系服务指定要连接的服务器。 通过依赖关系服务，您可以提取与在不同服务器上存储的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 和 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 对象之间的依赖关系有关的信息。 通过查看对象依赖关系**对象依赖关系**对话框中的[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]。  
  
 **您希望做什么？**  
  
1.  [打开选项 （查询结果/依赖关系服务页） 对话框](#open_dialog)  
  
2.  [配置选项](#options)  
  
##  <a name="open_dialog"></a> 打开选项 （查询结果/依赖关系服务页） 对话框  
  
1.  在中[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]，单击**选项**上**工具**菜单。  
  
2.  展开“查询结果”，然后单击“依赖关系服务”。  
  
##  <a name="options"></a> 配置选项  
  
### <a name="options"></a>选项  
 **依赖关系服务服务器**  
 指定安装依赖关系服务的服务器。  
  
 **身份验证**  
 选择 Windows 身份验证以便使用 Microsoft Windows 用户帐户登录，或者选择 SQL Server 身份验证。  
  
 当用户使用指定的登录名和密码从不可信连接进行连接时，SQL Server 将通过检查是否已设置 SQL Server 登录帐户以及指定的密码是否与以前记录的密码匹配，自行进行身份验证。 如果 SQL Server 找不到登录帐户，则身份验证会失败，用户将收到错误消息。  
  
 **用户名**  
 如果使用 SQL Server 身份验证，请提供用户名。  
  
 **密码**  
 如果使用 SQL Server 身份验证，请提供密码。  
  
 **测试**  
 单击此选项可对连接进行测试。  
  
  
