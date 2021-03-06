---
title: 列可见性对话框 （报表生成器） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10127"
ms.assetid: 0c030cab-6087-45a5-99f0-c7bd693f20a1
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f6ab67682afc00057085fe3d0f793c51a28258d7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "48057752"
---
# <a name="column-visibility-dialog-box-report-builder"></a>“列可见性”对话框（报表生成器）
  在报表首次运行时使用 **“列可见性”** 对话框来显示或隐藏选中的列，其他时候可通过此对话框使用另一报表项来切换该列的可见性。  
  
## <a name="options"></a>选项  
 **在报表最初运行时**  
 选择一个选项以指示报表项在报表中的初始显示方式。  
  
 **显示**  
 选择此选项可显示列。  
  
 **隐藏**  
 选择此选项可隐藏列。  
  
 **显示或隐藏基于表达式**  
 选择此选项可以使初始可见性根据表达式相应变化。  
  
 键入一个表达式的计算结果为`Boolean`的值`True`可以隐藏项和`False`表示显示该项。 单击“表达式”(*fx*) 按钮可编辑表达式。  
  
 **可以通过此报表项切换显示**  
 选择此选项可以显示一个切换图像，用户可以使用该图像在 HTML 报表查看器中显示或隐藏此列。  
  
 您需要键入或选择报表中要用来显示切换图像的文本框的名称；例如，Textbox1。 所选择的文本框必须在此报表项的当前或包含作用域中。 例如，若要切换与子组关联的行的可见性，请在与父组关联的行中选择一个文本框。 若要切换图表的可见性，请选择一个与该图表位于同一包含作用域中的文本框；例如，表体或矩形。  
  
## <a name="see-also"></a>请参阅  
 [表达式示例（报表生成器和 SSRS）](report-design/expression-examples-report-builder-and-ssrs.md)   
 [为项添加展开或折叠操作（报表生成器和 SSRS）](report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md)   
 [映像&#40;报表生成器和 SSRS&#41;](report-design/images-report-builder-and-ssrs.md)   
 [用于对话框、窗格和向导的报表生成器帮助](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [“图像属性”对话框 ->“常规”（报表生成器和 SSRS）](../../2014/reporting-services/image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
