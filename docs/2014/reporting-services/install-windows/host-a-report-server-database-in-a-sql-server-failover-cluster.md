---
title: 在 SQL Server 故障转移群集中承载报表服务器数据库 | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 7bd5f019-2857-452f-a023-cc3b9e93aec4
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: fe8172c8fd277dc590428fb5cd16506412e56b44
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "48192757"
---
# <a name="host-a-report-server-database-in-a-sql-server-failover-cluster"></a>在 SQL Server 故障转移群集中承载报表服务器数据库
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供了对故障转移群集的支持，用户可以针对一个或多个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例使用多个磁盘。 对故障转移群集的支持仅限于报表服务器数据库；您不能将报表服务器服务作为故障转移群集的一部分运行。  
  
 若要在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 故障转移群集上承载报表服务器数据库，必须已安装并配置了群集。 然后，当您在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置工具的“数据库安装”页中创建报表服务器数据库时，可以选择该故障转移群集作为服务器名称。  
  
 尽管报表服务器服务不能参与故障转移群集，但是您可以在装有 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 故障转移群集的计算机中安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。 报表服务器的运行独立于故障转移群集。 如果在作为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 故障转移实例一部分的计算机上安装了报表服务器，则不需要将故障转移群集用于报表服务器数据库；可以使用不同的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例来承载该数据库。  
  
## <a name="see-also"></a>请参阅  
 [报表服务器数据库&#40;SSRS 本机模式&#41;](../report-server/report-server-database-ssrs-native-mode.md)   
 [创建报表服务器数据库&#40;SSRS 配置管理器&#41;](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md)  
  
  
