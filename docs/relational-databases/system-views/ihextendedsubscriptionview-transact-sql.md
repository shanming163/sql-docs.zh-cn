---
title: "IHextendedSubscriptionView (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- IHextendedSubscriptionView_TSQL
- IHextendedSubscriptionView
dev_langs: TSQL
helpviewer_keywords: IHextendedSubscriptionView view
ms.assetid: 124756a4-463a-4a81-bf5b-de7e8ffc7a62
caps.latest.revision: "11"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b7aa47e213552b5351c1dc1c7fc685ec96cd4a45
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2017
---
# <a name="ihextendedsubscriptionview-transact-sql"></a>IHextendedSubscriptionView (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **IHextendedSubscriptionView**视图公开对非 SQL Server 发布的订阅上的信息。 此视图存储在**分发**数据库。  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|**article_id**|**int**|项目的唯一标识符。|  
|**dest_db**|**sysname**|目标数据库的名称。|  
|**srvid**|**int**|订阅服务器的唯一标识符。|  
|**login_name**|**sysname**|用于连接到订阅服务器的登录名。|  
|**distribution_jobid**|**binary**|标识分发代理作业。|  
|**publisher_database_id**|**int**|标识发布数据库。|  
|**subscription_type**|**int**|订阅的类型：<br /><br /> **0** = 推送-订阅服务器上运行分发代理。<br /><br /> **1** = 请求的分发服务器上运行分发代理。|  
|**sync_type**|**tinyint**|初始同步的类型：<br /><br /> **1** = automatic<br /><br /> **2** = none|  
|**status**|**tinyint**|订阅的状态：<br /><br /> **0** = 处于非活动状态<br /><br /> **1** = 订阅<br /><br /> **2** = 活动|  
|**snapshot_seqno_flag**|**bit**|指示是否使用快照序列号。|  
|**independent_agent**|**bit**|指定是否为此发布一个独立的分发代理。<br /><br /> **0** = 发布使用共享的分发代理，并且每个发布服务器订阅服务器数据库/数据库对具有共享代理。<br /><br /> **1** = 此发布的独立分发代理。|  
|**subscription_time**|**datetime**|仅限内部使用。|  
|**loopback_detection**|**bit**|适用于作为双向事务复制拓扑的一部分的订阅。 环回检测将确定分发代理是否将在订阅服务器上发起的事务发送回订阅服务器：<br /><br /> **1** = 不发回。<br /><br /> **0**回 = 发送。|  
|**agent_id**|**int**|分发代理的唯一标识符。|  
|**update_mode**|**tinyint**|指示更新模式的类型，可以为下列值之一：<br /><br /> **0** = 只读的。<br /><br /> **1** = 立即更新。<br /><br /> **2** = 使用消息队列的已排队更新。<br /><br /> **3** = 即时使用排队更新作为故障转移使用消息队列来更新。<br /><br /> **4** = 使用 SQL Server 队列的已排队更新。<br /><br /> **5** = 具有排队的更新故障转移功能，使用 SQL Server 队列立即更新。|  
|**publisher_seqno**|**varbinary(16)**|该订阅在发布服务器上的事务序列号。|  
|**ss_cplt_seqno**|**varbinary(16)**|用于表示并发快照处理已完成的序列号。|  
  
## <a name="see-also"></a>另请参阅  
 [异类数据库复制](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [复制表 &#40;Transact SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [复制视图 (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  