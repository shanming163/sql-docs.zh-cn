---
title: "创建数据库加密密钥 (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 08/24/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATABASE_ENCRYPTION_KEY_TSQL
- ENCRYPTION_KEY_TSQL
- sql13.swb.dbencryptionkeyo.f1
- ENCRYPTION KEY
- DATABASE ENCRYPTION KEY
- CREATE_DATABASE_ENCRYPTION_KEY_TSQL
- CREATE DATABASE ENCRYPTION KEY
- sql13.swb.dbencryptionkeyg.f1
- CREATE DATABASE ENCRYPTION
- CREATE_DATABASE_ENCRYPTION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database encryption key
- CREATE DATABASE ENCRYPTION KEY statement
- database encryption key, create
ms.assetid: 2ee95a32-5140-41bd-9ab3-a947b9990688
caps.latest.revision: 30
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 559e85cf5ba8e565a6afc86d3537b476365bd980
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="create-database-encryption-key-transact-sql"></a>CREATE DATABASE ENCRYPTION KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

 创建用于以透明方式加密数据库的加密密钥。 有关透明数据库加密的详细信息，请参阅[透明数据加密 &#40;TDE &#41;](../../relational-databases/security/encryption/transparent-data-encryption.md).  
  
![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
-- Syntax for SQL Server  

CREATE DATABASE ENCRYPTION KEY  
       WITH ALGORITHM = { AES_128 | AES_192 | AES_256 | TRIPLE_DES_3KEY }  
   ENCRYPTION BY SERVER   
    {  
        CERTIFICATE Encryptor_Name |  
        ASYMMETRIC KEY Encryptor_Name  
    }  
[ ; ]  
```  
  
```  
-- Syntax for Parallel Data Warehouse  

CREATE DATABASE ENCRYPTION KEY  
       WITH ALGORITHM = { AES_128 | AES_192 | AES_256 | TRIPLE_DES_3KEY }  
   ENCRYPTION BY SERVER CERTIFICATE Encryptor_Name   
[ ; ]  
```  
  
## <a name="arguments"></a>参数  
WITH ALGORITHM = { AES_128 | AES_192 | AES_256 | TRIPLE_DES_3KEY  }  
指定用于加密密钥的加密算法。   
>  [!NOTE]
>    从 SQL Server 2016 开始，已弃用 AES_128、 AES_192 和 AES_256 以外的所有算法。 若要使用旧算法（不推荐），必须将数据库设置为兼容级别 120 或更低。  
  
通过服务器证书 Encryptor_Name 加密  
指定用于加密数据库加密密钥的加密程序的名称。  
  
通过服务器非对称密钥 Encryptor_Name 加密  
指定用于加密数据库加密密钥的非对称密钥的名称。 要使用非对称密钥对数据库加密密钥进行加密，非对称密钥必须驻留在可扩展密钥管理提供程序上。  
  
## <a name="remarks"></a>注释  
可以通过使用加密数据库之前需要数据库加密密钥*透明数据库加密*(TDE)。 以透明方式加密数据库时，将在文件级别上加密整个数据库，而无需对代码进行特殊修改。 用于加密数据库加密密钥的证书或非对称密钥必须位于 master 系统数据库中。  
  
只允许对用户数据库使用数据库加密语句。  
  
数据库加密密钥不能从数据库中导出。 它只能供系统、对服务器拥有调试权限的用户以及能够访问证书（用于加密和解密数据库加密密钥）的用户使用。  
  
数据库所有者 (dbo) 发生更改时不必重新生成数据库加密密钥。  
  
为自动创建数据库加密密钥[!INCLUDE[ssSDS](../../includes/sssds-md.md)]数据库。 不需要使用 CREATE DATABASE ENCRYPTION KEY 语句来创建项。  
  
## <a name="permissions"></a>Permissions  
需要数据库的 CONTROL 权限和用于加密数据库加密密钥的证书或非对称密钥的 VIEW DEFINITION 权限。  
  
## <a name="examples"></a>示例  
有关使用 TDE 的其他示例，请参阅[透明数据加密 &#40;TDE &#41;](../../relational-databases/security/encryption/transparent-data-encryption.md)，[在使用 EKM 的 SQL Server 上启用 TDE](../../relational-databases/security/encryption/enable-tde-on-sql-server-using-ekm.md)，和[使用 Azure Key Vault &#40; 可扩展密钥管理SQL server&#41;](../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md).  
  
下面的示例使用 `AES_256` 算法创建一个数据库加密密钥，并使用名为 `MyServerCert` 的证书保护私钥。  
  
```  
USE AdventureWorks2012;  
GO  
CREATE DATABASE ENCRYPTION KEY  
WITH ALGORITHM = AES_256  
ENCRYPTION BY SERVER CERTIFICATE MyServerCert;  
GO  
```  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>示例：[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
有关使用 TDE 的其他示例，请参阅[透明数据加密 (SQL Server PDW)](http://msdn.microsoft.com/en-us/b82ad21d-09dd-43dd-8fab-bcf2c8c3ac6d)。  
  
下面的示例使用 `AES_256` 算法创建一个数据库加密密钥，并使用名为 `MyServerCert` 的证书保护私钥。  
  
```  
-- Uses AdventureWorks  
  
CREATE DATABASE ENCRYPTION KEY  
WITH ALGORITHM = AES_256  
ENCRYPTION BY SERVER CERTIFICATE MyServerCert;  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
[透明数据加密 (TDE)](../../relational-databases/security/encryption/transparent-data-encryption.md)   
[SQL Server 加密](../../relational-databases/security/encryption/sql-server-encryption.md)   
[SQL Server 和数据库加密密钥（数据库引擎）](../../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)   
[加密层次结构](../../relational-databases/security/encryption/encryption-hierarchy.md)   
[ALTER DATABASE SET 选项 (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
[ALTER DATABASE ENCRYPTION KEY &#40;Transact SQL &#41;](../../t-sql/statements/alter-database-encryption-key-transact-sql.md)   
[DROP DATABASE ENCRYPTION KEY &#40;Transact SQL &#41;](../../t-sql/statements/drop-database-encryption-key-transact-sql.md)   
[sys.dm_database_encryption_keys (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md)  
    
