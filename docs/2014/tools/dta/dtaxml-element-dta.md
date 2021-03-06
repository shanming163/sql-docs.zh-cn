---
title: DTAXML 元素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- DTAXML element
ms.assetid: 3d9942ed-8a27-40db-a7c9-808984d914a2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d567c422299809f04be97c8db298aadecc22dde8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "48192217"
---
# <a name="dtaxml-element-dta"></a>DTAXML 元素 (DTA)
  数据库引擎优化顾问 XML 输入文件或输出文件的根元素 **DTAXML** 包含用于对数据库引擎优化顾问生成的优化输入和优化输出进行说明的所有元素。  
  
## <a name="syntax"></a>语法  
  
```  
  
<DTAXML   
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"   
    xmlns="http://schemas.microsoft.com/sqlserver/2004/07/dta">  
    ...code removed here...  
</DTAXML>  
```  
  
## <a name="element-attributes"></a>元素属性  
  
|Attribute|Description|  
|---------------|-----------------|  
|`xmlns:xsi`|必需的。 标识 XML 架构实例命名空间。 可以使用此命名空间中的属性来引用用于验证数据库引擎优化顾问 XML 文件的架构。<br /><br /> 必需的值：[http://www.w3.org/2001/XMLSchema-instance](http://www.w3.org/2001/XMLSchema-instance)|  
|`xmlns`|必需的。 标识数据库引擎优化顾问命名空间。<br /><br /> 如果在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中使用 XML 编辑器编辑数据库引擎优化顾问 XML 文件，则“F1 帮助”和“动态帮助”将使用此值在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中定位可能的引用主题。<br /><br /> 必需的值：<br /><br /> [Database Engine Tuning Advisor XML Schema](http://go.microsoft.com/fwlink/?LinkId=43100) （数据库引擎优化顾问 XML 架构）命名空间|  
  
## <a name="element-characteristics"></a>元素特征  
  
|特征|Description|  
|--------------------|-----------------|  
|**数据类型和长度**|无。|  
|**默认值**|无。|  
|**出现次数**|每个 DTA XML 文件必须出现一次。|  
  
## <a name="element-relationships"></a>元素关系  
  
|关系|元素|  
|------------------|--------------|  
|**父元素**|None|  
|**子元素**|[DTAInput 元素&#40;DTA&#41;](dtainput-element-dta.md)<br /><br /> `DTAOutput` 元素 (请参阅[数据库引擎优化顾问 XML 架构](http://schemas.microsoft.com/sqlserver/)信息)|  
  
## <a name="remarks"></a>备注  
 有关 XML namespaces 的详细信息，请参阅 [MSDN Library 中的](http://go.microsoft.com/fwlink/?LinkId=7341) Namespaces in an XML Document [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。  
  
## <a name="example"></a>示例  
 有关典型 **DTAXML** 元素的示例，请参阅 [XML 输入文件实例 (DTA)](xml-input-file-samples-dta.md)。  
  
## <a name="see-also"></a>请参阅  
 [XML 输入文件引用&#40;数据库引擎优化顾问&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)   
 [启动并使用数据库引擎优化顾问](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)  
  
  
