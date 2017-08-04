---
title: "Wtd (MDX) |Microsoft 文档"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- WTD
dev_langs:
- kbMDX
helpviewer_keywords:
- Wtd function
ms.assetid: 41066e1b-e802-4582-be4b-3ed7807b033e
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 1010b6d7aef59c5bb4eb18e93ba63bc972e8b7fa
ms.contentlocale: zh-cn
ms.lasthandoff: 08/02/2017

---
# <a name="wtd-mdx"></a>Wtd (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  按照时间维度中的周级别的约束，从给定成员所在的级别返回一组同级成员，从第一个同级成员开始到给定成员为止。  
  
## <a name="syntax"></a>語法  
  
```  
  
Wtd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>参数  
 *Member_Expression*  
 返回成员的有效多维表达式 (MDX)。  
  
## <a name="remarks"></a>注释  
 如果未指定一个成员表达式，默认值是第一个层次结构使用的类型级别的当前成员类型时的第一个维度中的周数 (**Time.CurrentMember**) 度量值组中。  
  
 **Wtd**函数是快捷函数[PeriodsToDate](../mdx/periodstodate-mdx.md)函数其中的级别设置为*周*。 也就是说，`Wtd(Member_Expression)` 等效于 `PeriodsToDate(Week_Level_Expression,Member_Expression)`。  
  
## <a name="see-also"></a>另请参阅  
 [Qtd &#40;MDX &#41;](../mdx/qtd-mdx.md)   
 [Mtd &#40;MDX &#41;](../mdx/mtd-mdx.md)   
 [Ytd &#40;MDX &#41;](../mdx/ytd-mdx.md)   
 [MDX 函数引用 &#40;MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
