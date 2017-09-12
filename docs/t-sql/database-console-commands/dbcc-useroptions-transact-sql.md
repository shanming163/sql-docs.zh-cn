---
title: "DBCC USEROPTIONS (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DBCC USEROPTIONS
- DBCC_USEROPTIONS_TSQL
- USEROPTIONS_TSQL
- USEROPTIONS
dev_langs:
- TSQL
helpviewer_keywords:
- DBCC USEROPTIONS statement
- active SET options
- SET statement, active SET options
ms.assetid: 565ab112-7af1-4c18-a579-07cdb332f539
caps.latest.revision: 41
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a94a29317bef21f784d2b0b927577627434ce7d9
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-useroptions-transact-sql"></a>DBCC USEROPTIONS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

返回当前连接的活动（设置）的 SET 选项。
  
![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>语法  
  
```sql
DBCC USEROPTIONS  
[ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>参数  
NO_INFOMSGS  
取消严重级别从 0 到 10 的所有信息性消息。
  
## <a name="result-sets"></a>结果集  
DBCC USEROPTIONS 返回 SET 选项的名称列和该选项的值列（值和项可能会变化）：

```sql

| `Set Option                   Value`  
 `---------------------------- ---------------------------`  
 `textsize                     64512`  
 `language                     us_english`  
 `dateformat                   mdy`  
 `datefirst                    7`  
 `lock_timeout                 -1`  
 `quoted_identifier            SET`  
 `arithabort                   SET`  
 `ansi_null_dflt_on            SET`  
 `ansi_warnings                SET`  
 `ansi_padding                 SET`  
 `ansi_nulls                   SET`  
 `concat_null_yields_null      SET`  
 `isolation level              read committed`  
 `(13 row(s) affected)`  
 `DBCC execution completed. If DBCC printed error messages, contact your system administrator.`
 ```  
  
## <a name="remarks"></a>注释  
当数据库选项 READ_COMMITTED_SNAPSHOT 设置为 ON 并且事务隔离级别设置为 'read committed' 时，DBCC USEROPTIONS 会报告 'read committed snapshot' 的隔离级别。 实际的隔离级别是已提交读。
  
## <a name="permissions"></a>Permissions  
要求 **公共** 角色具有成员身份。
  
## <a name="examples"></a>示例  
以下示例返回当前连接的活动 SET 选项。
  
```sql  
DBCC USEROPTIONS;  
```  
  
## <a name="see-also"></a>另请参阅  
[DBCC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[SET 语句 (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)  
[SET TRANSACTION ISOLATION LEVEL (Transact-SQL)](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)
  
  
