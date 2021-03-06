---
title: 筛选器设置 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.filtersettings.f1
ms.assetid: 1b401d7d-db8a-4ba1-acb1-b8dec14e3311
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a972e2487ed9ec0470f21a9ba8c99b3300ab9e83
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "48114997"
---
# <a name="filter-settings"></a>筛选器设置
  可以使用 **“筛选设置”** 对话框为复制监视器中的网格定义筛选器。 例如，若要只显示 **“所有订阅”** 选项卡上处于活动状态的订阅，请从 **“列名”** 列选择 **“状态”** ，从 **“运算符”** 列选择 **“等于”** 并从 **“值1”** 列选择 **“活动”** 。 在您基于一个或多个列定义筛选器之后，将应用筛选器以便网格中只显示与筛选器条件匹配的子集行。  
  
## <a name="options"></a>选项  
 **“状态”**  
 选择要对其进行筛选的列的名称。 您可以使筛选器基于一个或多个列。  
  
 **“等于”**  
 为筛选器选择一个运算符，例如 **“小于或等于”**。  
  
 **“值1”** 和 **“值2”**  
 为筛选器输入或选择一个值。 大多数运算符只要求在 **“值1”** 列中提供值，但 **“介于”** 和 **“不介于”** 运算符还要求在 **“值2”** 列中提供值。  
  
 **清除筛选器**  
 单击此按钮可以清除已定义的所有筛选器。 若要删除某个筛选器，请选中此筛选器行并按 Delete 键。  
  
## <a name="see-also"></a>请参阅  
 [监视复制](monitoring-replication.md)  
  
  
