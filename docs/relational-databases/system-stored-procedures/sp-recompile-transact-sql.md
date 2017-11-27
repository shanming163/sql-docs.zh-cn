---
title: "sp_recompile (TRANSACT-SQL) |Microsoft 文档"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_recompile_TSQL
- sp_recompile
dev_langs: TSQL
helpviewer_keywords: sp_recompile
ms.assetid: 6192ca87-febd-4075-8199-14b4fa609b8c
caps.latest.revision: "36"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: e802de07e5113d9cf12ba65df56153646361f715
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="sprecompile-transact-sql"></a>sp_recompile (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  导致存储过程、触发器和用户定义函数在下次运行时重新编译。 具体方法是：从过程缓存中删除现有计划，强制在下次运行该过程或触发器时创建新计划。 在 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 集合中，记录事件 SP:CacheInsert 而不是事件 SP:Recompile。  
  
||  
|-|  
|**适用范围**： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] （[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 到 [当前版本](http://go.microsoft.com/fwlink/p/?LinkId=299658)）、 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。|  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```tsql  
  
sp_recompile [ @objname = ] 'object'  
```  
  
## <a name="arguments"></a>参数  
 [ @objname=] '*对象*  
 当前数据库中存储过程、触发器、表、视图或用户定义函数的限定或未限定的名称。 *对象*是**nvarchar(776)**，无默认值。 如果*对象*是存储过程、 触发器或用户定义函数，存储过程，触发器的名称或函数将运行在下一步时重新编译。 如果*对象*是表或视图中，所有存储过程，触发器的名称或引用表或视图的用户定义函数将在运行时的下一步时重新编译。  
  
## <a name="return-code-values"></a>返回代码值  
 0（成功）或非零数字（失败）  
  
## <a name="remarks"></a>注释  
 sp_recompile 只在当前数据库中寻找对象。  
  
 存储过程或触发器和用户定义函数使用的查询仅在编译时优化。 对数据库进行了索引或其他会影响数据库统计的更改后，已编译的存储过程、触发器和用户定义函数可能会失去效率。 通过对作用于表上的存储过程和触发器进行重新编译，可以重新优化查询。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 会在便利时自动对存储过程、触发器和用户定义函数进行重新编译。  
  
## <a name="permissions"></a>Permissions  
 需要具有对指定对象的 ALTER 权限。  
  
## <a name="examples"></a>示例  
 下面的示例使作用于 `Customer` 表的存储过程、触发器和用户定义函数在下次运行时重新编译。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_recompile N'Sales.Customer';  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [CREATE PROCEDURE (Transact-SQL)](../../t-sql/statements/create-procedure-transact-sql.md)   
 [CREATE TRIGGER (Transact-SQL)](../../t-sql/statements/create-trigger-transact-sql.md)   
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  