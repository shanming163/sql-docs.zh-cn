---
title: SQL Server - Backup Device 对象 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Backup Device
- Backup Device object
ms.assetid: 52e7febf-d5e0-4674-945b-aacc40a9ad6e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 286c33ac5314321e69c183cfd1ef336da782bfbe
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "48064097"
---
# <a name="sql-server-backup-device-object"></a>SQL Server Backup Device 对象
  **Backup Device** 对象提供的计数器可监视用于备份和还原操作的 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 备份设备。 在希望基于每个设备确定吞吐量或备份和还原操作的进度及性能时，可以监视备份设备。 若要监视整个数据库备份或还原操作的吞吐量，请使用  Databases [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Databases** object. 有关详细信息，请参阅 [SQL Server, Databases Object](sql-server-databases-object.md)。  
  
 此表介绍了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Backup Device** 计数器。  
  
|SQL Server Backup Device 计数器|Description|  
|---------------------------------------|-----------------|  
|**Device Throughput Bytes/sec**|一个备份设备在备份或还原数据库时所用的读写操作的吞吐量（以每秒字节数表示）。 这一计数器只有在备份或还原操作执行时才存在。|  
  
## <a name="see-also"></a>请参阅  
 [备份设备 (SQL Server)](../backup-restore/backup-devices-sql-server.md)   
 [监视资源使用情况（系统监视器）](monitor-resource-usage-system-monitor.md)  
  
  
