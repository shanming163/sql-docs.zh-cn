---
title: MSsubscriber_schedule (Transact SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSsubscriber_schedule
- MSsubscriber_schedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscriber_schedule system table
ms.assetid: ff428306-0ef4-49a3-b536-07ccdf6e2196
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 91b04c358adcce0aa1cb02b702096d215298a11a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2018
ms.locfileid: "47856485"
---
# <a name="mssubscriberschedule-transact-sql"></a>MSsubscriber_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSsubscriber_schedule**表包含默认合并和每个发布服务器/订阅服务器上对事务同步计划。 此表存储在分发数据库中。  
  
> [!NOTE]  
>  此系统表已弃用，并维护以支持旧版[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|**publisher**|**sysname**|发布服务器的名称。|  
|**订阅服务器**|**sysname**|订阅服务器的名称。|  
|**agent_type**|**smallint**|代理的类型：<br /><br /> 0 = 分发代理。<br /><br /> 1 = 合并代理。|  
|**frequency_type**|**int**|调度分发代理的频率：<br /><br /> **1** = 一次。<br /><br /> **2** = 按需。<br /><br /> **4** = 每日。<br /><br /> **8** = 每周。<br /><br /> **16** = 每月。<br /><br /> **32** = 每月相对。<br /><br /> **64** = 自动启动。<br /><br /> **128** = 重复执行。|  
|**frequency_interval**|**int**|要将应用于设置频率的值**frequency_type**。|  
|**frequency_relative_interval**|**int**|分发代理的日期：<br /><br /> **1** = 第一次。<br /><br /> **2** = 第二个。<br /><br /> **4** = 第三次。<br /><br /> **8** = 第四次。<br /><br /> **16** = 最后一次。|  
|**frequency_recurrence_factor**|**int**|通过使用的重复因子**frequency_type**。|  
|**frequency_subday**|**int**|在定义的周期内的重新调度频率：<br /><br /> **1** = 一次。<br /><br /> **2** = 第二个。<br /><br /> **4** = 分钟。<br /><br /> **8** = 小时。|  
|**frequency_subday_interval**|**int**|间隔**frequency_subday**。|  
|**active_start_time_of_day**|**int**|首次调度分发代理的时间，格式为 HHMMSS。|  
|**active_end_time_of_day**|**int**|停止调度分发代理的时间，格式为 HHMMSS。|  
|**active_start_date**|**int**|首次调度分发代理的日期，格式为 YYYYMMDD。|  
|**active_end_date**|**int**|分发代理将停止时的日期安排，格式为 YYYYMMDD。|  
  
## <a name="see-also"></a>请参阅  
 [复制表&#40;Transact SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [复制视图 (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
