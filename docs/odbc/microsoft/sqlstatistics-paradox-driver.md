---
title: "SQLStatistics （Paradox 驱动程序） |Microsoft 文档"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Paradox driver [ODBC], SQLStatistics
- SQLStatistics function [ODBC], Paradox Driver
ms.assetid: 886cab83-d599-4fbc-9c88-e8cb833aac4b
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9d857190e0e98f80605da8568d131290ccb66634
ms.contentlocale: zh-cn
ms.lasthandoff: 09/09/2017

---
# <a name="sqlstatistics-paradox-driver"></a>SQLStatistics （Paradox 驱动程序）
> [!NOTE]  
>  本主题提供 Paradox 特定于驱动程序信息。 有关此函数的常规信息，请参阅下的相应主题[ODBC API 参考](../../odbc/reference/syntax/odbc-api-reference.md)。  
  
|列|注释|  
|------------|--------------|  
|TABLE_QUALIFIER|目录的路径。<br /><br /> 模式匹配中不支持*szTableQualifier*自变量。|  
|TABLE_OWNER|因为不支持所有者名称，将在此列中返回 NULL。|  
|TABLE_NAME|未分隔的表名。<br /><br /> 模式匹配中不支持*szTableName*自变量。|  
|INDEX_QUALIFIER|始终返回 NULL。|  
|INDEX_NAME|索引相关。|  
|TYPE|只有 SQL_TABLE_STAT 或 SQL_INDEX_OTHER 将返回类型。|  
|SEQ_IN_INDEX|索引相关。|  
|COLUMN_NAME|索引相关。|  
|COLLATION|索引相关。|  
|PAGES|始终返回 NULL。|  
  
 筛选基于唯一性 ( *fUnique*自变量)。 *FAccuracy*参数将被忽略。