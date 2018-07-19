---
title: 'Ibcpsession:: Bcpinit (OLE DB) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- IBCPSession::BCPInit (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPInit method
ms.assetid: 583096d7-da34-49be-87fd-31210aac81aa
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 11ddae5bacdd5428a4381ec034d9dc9f0f22b6b7
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2018
ms.locfileid: "37413396"
---
# <a name="ibcpsessionbcpinit-ole-db"></a>IBCPSession::BCPInit (OLE DB)
  初始化大容量复制结构，执行某些错误检查，验证数据和格式化文件名是否正确，然后打开文件。  
  
## <a name="syntax"></a>语法  
  
```  
  
HRESULT BCPInit(   
const wchar_t *pwszTable,  
const wchar_t *pwszDataFile,  
const wchar_t *pwszErrorFile,  
inteDirection);  
```  
  
## <a name="remarks"></a>Remarks  
 **BCPInit**应在任何其他大容量复制方法之前调用方法。 **BCPInit**工作站之间的数据大容量复制方法执行必要的初始化和[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
  
 **BCPInit**方法将检查数据库源或目标表，不是数据文件的结构。 该方法将基于数据库表、视图或 SELECT 结果集中的每一列为数据文件指定数据格式值。 此指定包括每一列的数据类型、数据中是否存在长度或 Null 指示符和终止符字节字符串以及固定长度的数据类型的宽度。 **BCPInit**方法设置这些值，如下所示：  
  
-   指定的数据类型是数据库表、视图或 SELECT 结果集中的列的数据类型。 枚举数据类型[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]本机数据类型中指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client 头文件 (sqlncli.h)。 数据类型的值为 BCP_TYPE_XXX 模式。 数据将以其计算机形式表示。 也就是说，整数数据类型的列中的数据通过一个由四个字节组成的序列表示，该序列采用 big-endian 或 little-endian 格式，具体使用哪种格式取决于创建该数据文件的计算机。  
  
-   如果数据库数据类型的长度是固定的，则该数据文件中的数据长度也是固定的。 用于处理数据的大容量复制方法 (例如， [ibcpsession:: Bcpexec](ibcpsession-bcpexec-ole-db.md)) 要与数据库表、 视图或 SELECT 列中指定的数据的长度相同的数据文件中的数据长度预期的数据行进行分析列表。 例如，对于定义为 `char(13)` 的数据库列的数据，该文件中每行数据必须由 13 个字符来表示。 如果数据库列允许 Null 值，则可以使用 Null 指示符作为固定长度的数据的前缀。  
  
-   向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 复制数据时，数据文件必须包含数据库表中的每列数据。 从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 复制数据时，数据库表、视图或 SELECT 结果集中所有列的数据均将复制到数据文件。  
  
-   向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 复制数据时，数据文件中列的序号位置必须与数据库表中列的序号位置相同。 复制中的数据时[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，则**BCPExec**方法是将基于数据库表中的列的序号位置的数据。  
  
-   如果数据库数据类型的长度是可变的（如 `varbinary(22)`），或者如果数据库列可以包含 Null 值，则在数据文件中使用长度/Null 指示符作为数据的前缀。 指示符的宽度因数据类型和大容量复制的版本而异。 [Ibcpsession:: Bcpcontrol](ibcpsession-bcpcontrol-ole-db.md)方法选项 BCP_OPTION_FILEFMT 提供早期大容量复制数据文件和运行更高版本的服务器之间的兼容性[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，用于指示何时通过中的指示符的宽度数据是窄于预期。  
  
> [!NOTE]  
>  若要更改数据文件指定的数据格式值，请使用[ibcpsession:: Bcpcolumns](ibcpsession-bcpcolumns-ole-db.md)并[ibcpsession:: Bcpcolfmt](ibcpsession-bcpcolfmt-ole-db.md)方法。  
  
 大容量复制到[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]可以通过将数据库选项设置不包含索引的表的优化**选择到 / bulkcopy**。  
  
## <a name="arguments"></a>参数  
 *pwszTable*[in]  
 要复制进或复制出的数据库表的名称。 该名称可以包含数据库名称或所有者名称。 例如，"pubs.username.titles"、"pubs..titles"、"username.titles"。  
  
 如果 eDirection 参数设置为 BCP_DIRECTION_OUT，则 pwszTable 参数可以为数据库视图的名称。  
  
 如果 eDirection 参数设置为 BCP_DIRECTION_OUT 并使用指定的 SELECT 语句**BCPControl**方法，然后再**BCPExec**调用方法时， *pwszTable*参数必须设置为 NULL。  
  
 *pwszDataFile*[in]  
 要复制进或复制出的用户文件的名称。  
  
 *pwszErrorFile*[in]  
 错误文件的名称，该文件将用进度消息、错误消息以及无法从用户文件复制到表的任何行的副本进行填充。 如果*pwszErrorFile*参数设置为 NULL，不使用任何错误文件。  
  
 *eDirection*[in]  
 复制操作的方向，BCP_DIRECTION_IN 或 BCP_DIRECTION _OUT。 BCP_DIRECTION _IN 指示从用户文件向数据库表进行复制；BCP_DIRECTION _OUT 指示从数据库表向用户文件进行复制。  
  
## <a name="return-code-values"></a>返回代码值  
 S_OK  
 方法成功。  
  
 E_FAIL  
 出现提供程序特定的错误详细信息，请使用[ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)接口。  
  
 E_OUTOFMEMORY  
 内存不足错误。  
  
 E_INVALIDARG  
 未正确指定一个或多个参数。 例如，给定的文件名无效。  
  
## <a name="see-also"></a>请参阅  
 [IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md)   
 [执行大容量复制操作](../native-client/features/performing-bulk-copy-operations.md)  
  
  