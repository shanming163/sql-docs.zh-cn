---
title: sys.sysusers (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sysusers
- sys.sysusers_TSQL
- sysusers_TSQL
- sysusers
dev_langs:
- TSQL
helpviewer_keywords:
- sysusers system table
- sys.sysusers compatibility view
ms.assetid: 5f0e6a8d-c983-44f6-97e9-aab5bff67d18
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e1b5ade681827e28a67262c8514be35e1e914015
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2018
ms.locfileid: "47658875"
---
# <a name="syssysusers-transact-sql"></a>sys.sysusers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  为每个包含一行[!INCLUDE[msCoName](../../includes/msconame-md.md)]Windows 用户、 Windows 组[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]用户，或[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据库角色中的。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|**uid**|**smallint**|用户 ID，在此数据库中是唯一的。<br /><br /> 1 = 数据库所有者<br /><br /> 如果用户数和角色数超过 32,767，则发生溢出或返回 NULL。|  
|**status**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**名称**|**sysname**|用户名或组名，在此数据库中是唯一的。|  
|**sid**|**varbinary(85)**|此项的安全性标识符。|  
|**角色**|**varbinary(2048)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**createdate**|**datetime**|帐户的添加日期。|  
|**updatedate**|**datetime**|帐户的上次更改日期。|  
|**altuid**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]<br /><br /> 如果用户数和角色数超过 32,767，则发生溢出或返回 NULL。|  
|**password**|**varbinary(256)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**gid**|**smallint**|此用户所属的组 ID。 如果**uid**等同于**gid**，此项定义组。 如果组和用户的总数超过 32,767，则发生溢出或返回 NULL。|  
|**environ**|**varchar(255)**|保留。|  
|**hasdbaccess**|**int**|1 = 帐户具有数据库访问权。|  
|**islogin**|**int**|1 = 帐户是具有登录帐户的 Windows 组、Windows 用户或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用户。|  
|**isntname**|**int**|1 = 帐户是 Windows 组或 Windows 用户。|  
|**isntgroup**|**int**|1 = 帐户是 Windows 组。|  
|**isntuser**|**int**|1 = 帐户是 Windows 用户。|  
|**issqluser**|**int**|1 = 帐户是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用户。|  
|**isaliased**|**int**|1 = 帐户化名为另一个用户。|  
|**issqlrole**|**int**|1 = 帐户是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 角色。|  
|**isapprole**|**int**|1 = 帐户是应用程序角色。|  
  
## <a name="see-also"></a>请参阅  
 [系统表映射到系统视图&#40;Transact SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [兼容性视图 (Transact SQL)](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
