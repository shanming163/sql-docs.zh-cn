---
title: "DB_NAME (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 07/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DB_NAME
- DB_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database names [SQL Server], DB_NAME
- names [SQL Server], databases
- viewing database names
- displaying database names
- DB_NAME function
ms.assetid: e21fb33a-a3ea-49b0-bb6b-8f789a675a0e
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c5743ccb1374640078a77d84a140e9e5d0fdaef0
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="dbname-transact-sql"></a>DB_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

返回数据库名称。
  
![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>语法  
  
```sql
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
DB_NAME ( [ database_id ] )  
```  
  
## <a name="arguments"></a>参数  
*database_id*  
要返回的数据库的标识号 (ID)。 *database_id*是**int**，无默认值。 如果未指定 ID，则返回当前数据库名称。
  
## <a name="return-types"></a>返回类型
**nvarchar （128)**
  
## <a name="permissions"></a>Permissions  
如果调用方**DB_NAME**不是数据库的所有者和该数据库未**master**或**tempdb**，请参阅相应的行所需的最小权限是ALTER ANY DATABASE 或 VIEW ANY DATABASE 服务器级权限，或者在 CREATE DATABASE 权限**master**数据库。 始终可以在 **sys.databases**中查看调用方连接的数据库。
  
> [!IMPORTANT]  
>  默认情况下，公共角色具有 VIEW ANY DATABASE 权限，允许所有登录名，若要查看数据库信息。 若要阻止来自能够检测到数据库的登录名，请撤消从公共的的 VIEW ANY DATABASE 权限或拒绝单个登录名的 VIEW ANY DATABASE 权限。  
  
## <a name="examples"></a>示例  
  
### <a name="a-returning-the-current-database-name"></a>A. 返回当前数据库名称  
以下示例返回当前数据库的名称。
  
```sql
SELECT DB_NAME() AS [Current Database];  
GO  
```  
  
### <a name="b-returning-the-database-name-of-a-specified-database-id"></a>B. 返回指定数据库 ID 的数据库名称  
以下示例返回数据库 ID `3` 的数据库名称。
  
```sql
USE master;  
GO  
SELECT DB_NAME(3)AS [Database Name];  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>示例：[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]和[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-return-the-current-database-name"></a>C. 返回当前的数据库名称  
  
```sql
SELECT DB_NAME() AS [Current Database];  
```  
  
### <a name="d-return-the-name-of-a-database-by-using-the-database-id"></a>D. 使用的数据库 ID 返回数据库的名称  
下面的示例返回的数据库名称和每个数据库的 database_id。
  
```sql
SELECT DB_NAME(database_id) AS [Database], database_id  
FROM sys.databases;  
```  
  
## <a name="see-also"></a>另请参阅
[DB_ID &#40;Transact SQL &#41;](../../t-sql/functions/db-id-transact-sql.md)  
[元数据函数 &#40;Transact SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)  
[sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)
  
  

