---
title: "ALTER SERVICE MASTER KEY (TRANSACT-SQL) |Microsoft 文档"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_SERVICE_MASTER_KEY_TSQL
- ALTER SERVICE MASTER KEY
dev_langs:
- TSQL
helpviewer_keywords:
- REGENERATE phrase
- FORCE option
- ALTER SERVICE MASTER KEY statement
- cryptography [SQL Server], Service Master Key
- modifying Service Master Key
- decryption [SQL Server], Service Master Key
- encryption [SQL Server], Service Master Key
- service master key [SQL Server], modifying
ms.assetid: a1e9be0e-4115-47d8-9d3a-3316d876a35e
caps.latest.revision: 41
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4ee9fd8a888ed796b4d01b007aec5f8217cce5d9
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="alter-service-master-key-transact-sql"></a>ALTER SERVICE MASTER KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  更改 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的服务主密钥。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
ALTER SERVICE MASTER KEY   
    [ { <regenerate_option> | <recover_option> } ] [;]  
  
<regenerate_option> ::=  
    [ FORCE ] REGENERATE  
  
<recover_option> ::=  
    { WITH OLD_ACCOUNT = 'account_name' , OLD_PASSWORD = 'password' }  
    |      
    { WITH NEW_ACCOUNT = 'account_name' , NEW_PASSWORD = 'password' }  
```  
  
## <a name="arguments"></a>参数  
 FORCE  
 指示即使存在数据丢失的风险，也应当重新生成服务主密钥。 有关详细信息，请参阅[更改 SQL Server 服务帐户](#_changing)本主题中更高版本。  
  
 REGENERATE  
 指示应当重新生成服务主密钥。  
  
 OLD_ACCOUNT **=***account_name*  
 指定旧的 Windows 服务帐户的名称。  
  
> [!WARNING]  
>  此选项已过时。 请勿使用。 请改用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器。  
  
 OLD_PASSWORD **=***密码*  
 指定旧的 Windows 服务帐户的密码。  
  
> [!WARNING]  
>  此选项已过时。 请勿使用。 请改用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器。  
  
 NEW_ACCOUNT **=***account_name*  
 指定新的 Windows 服务帐户的名称。  
  
> [!WARNING]  
>  此选项已过时。 请勿使用。 请改用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器。  
  
 NEW_PASSWORD **=***密码*  
 指定新的 Windows 服务帐户的密码。  
  
> [!WARNING]  
>  此选项已过时。 请勿使用。 请改用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器。  
  
## <a name="remarks"></a>注释  
 当第一次需要使用服务主密钥对链接服务器密码、凭据或数据库主密钥进行加密时，便会自动生成服务主密钥。 使用本地计算机密钥和 Windows 数据保护 API 对服务主密钥进行加密。 该 API 使用从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务帐户的 Windows 凭据中派生的密钥。  
  
 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 使用 AES-256 加密算法来保护服务主密钥 (SMK) 和数据库主密钥 (DMK)。 AES 是一种比早期版本中使用的 3DES 更新的加密算法。 在将[!INCLUDE[ssDE](../../includes/ssde-md.md)]实例升级到 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 后，应重新生成 SMK 和 DMK 以便将主密钥升级到 AES。 有关重新生成 DMK 的详细信息，请参阅 [ALTER MASTER KEY (Transact-SQL)](../../t-sql/statements/alter-master-key-transact-sql.md)。  
  
##  <a name="_changing"></a>更改 SQL Server 服务帐户  
 若要更改 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务帐户，请使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器。 为了对服务帐户的变更进行管理，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将存储服务主密钥的冗余副本，该密钥由具有授予 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务组的必要权限的计算机帐户对其加以保护。 在重建计算机时，将可以为该服务帐户以前使用的同一域用户恢复服务主密钥。 这不适用于本地帐户或本地系统、 本地服务或网络服务帐户。 当您准备移动[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]到另一台计算机，通过使用备份和还原迁移服务主密钥。  
  
 REGENERATE 短语可以重新生成服务主密钥。 当重新生成服务主密钥时，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 会对所有使用该主密钥加密的密钥进行解密，然后使用新的服务主密钥对这些密钥进行加密。 这是一种消耗大量资源的操作。 在不危及密钥安全性的前提下，应当将该操作安排在资源需求较低的时段执行。 如果有任意一种解密操作失败，则整个语句将会失败。  
  
 即使密钥重新生成过程无法检索当前的主密钥，或者无法对所有使用该主密钥加密的私钥进行解密，使用 FORCE 选项也可以使得密钥重新生成过程继续进行。 使用 FORCE 只有当重新生成失败时，你无法通过使用还原服务主密钥[RESTORE SERVICE MASTER KEY](../../t-sql/statements/restore-service-master-key-transact-sql.md)语句。  
  
> [!CAUTION]  
>  服务主密钥为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 加密层次结构的根。 服务主密钥直接或间接地保护树中的所有其他密钥和机密内容。 如果在强制的重新生成过程中不能对某个相关密钥进行解密，则由该密钥所保护的数据会丢失。  
  
 如果将 SQL 移到另一计算机，则必须使用相同的服务帐户来解密 SMK – SQL Server 将自动修复计算机帐户加密。  
  
## <a name="permissions"></a>Permissions  
 需要对服务器的 CONTROL SERVER 权限。  
  
## <a name="examples"></a>示例  
 下面的示例重新生成服务主密钥。  
  
```  
ALTER SERVICE MASTER KEY REGENERATE;  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [还原 SERVICE MASTER KEY &#40;Transact SQL &#41;](../../t-sql/statements/restore-service-master-key-transact-sql.md)   
 [BACKUP SERVICE MASTER KEY &#40;Transact SQL &#41;](../../t-sql/statements/backup-service-master-key-transact-sql.md)   
 [加密层次结构](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  