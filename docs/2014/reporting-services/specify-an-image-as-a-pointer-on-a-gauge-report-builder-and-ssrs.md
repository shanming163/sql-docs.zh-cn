---
title: 指定一个图像作为仪表 （报表生成器和 SSRS） 的指针 |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 9d73b3c3-a068-4868-a2be-0cd261b6e92b
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2e2fbf2593ae5f85e12555d469ebe77b11539a20
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "48178877"
---
# <a name="specify-an-image-as-a-pointer-on-a-gauge-report-builder-and-ssrs"></a>指定图像作为仪表的指针（报表生成器和 SSRS）
  仪表包含三个可用于自定义指针外观的内置样式。 对于径向仪表，内置样式为：针、标记和图条。 对于线性仪表，内置样式为：标记、图条和温度计。 如果需要一个唯一指针，则用户可以创建一个图像并指定其作为全功能指针。  
  
 为指针指定图像时，图像必须满足以下规范：  
  
-   指针的原点或旋转中心必须位于图像的顶部。  
  
-   指针的末端必须指向下方。  
  
 由于指针形状不规则，所以您需要指定透明色，以隐藏不必要的图像部分。 请考虑使用通常仪表中不显示的颜色作为透明色，因为所指定的颜色不显示在仪表中。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-an-image-as-a-pointer-on-the-gauge"></a>指定一个图像作为仪表上的指针  
  
1.  在“设计”视图中，单击仪表指针。  
  
2.  （可选）如果没有指针存在仪表上，右键单击仪表并选择**添加指针**。 此时将会有一个指针添加到仪表上。  
  
3.  单击**插入**功能区上选项卡，然后双击图像图标。 将打开“图像属性”对话框。  
  
4.  向报表添加图像。 有关详细信息，请参阅[在报表中嵌入图像&#40;报表生成器和 SSRS&#41;](report-design/embed-an-image-in-a-report-report-builder-and-ssrs.md)。  
  
5.  打开“属性”窗格。  
  
6.  在设计图面上，单击该指针。 指针的属性将显示在“属性”窗格中。  
  
7.  展开 PointerImage 节点。  
  
8.  在中**源**，选择**嵌入**从下拉列表。  
  
    > [!NOTE]  
    >  如果图像存储在数据库中或 Web 上，则可以为此属性指定适当的选项。 有关详细信息，请参阅[图像属性对话框，常规&#40;报表生成器和 SSRS&#41;](../../2014/reporting-services/image-properties-dialog-box-general-report-builder-and-ssrs.md)。  
  
9. 在中**值**，从下拉列表中选择映像的名称。  
  
10. 在中**TransparentColor**，选择你想要从映像中删除的颜色值。 这将使指针的外观无缝地融入仪表。  
  
## <a name="see-also"></a>请参阅  
 [设置仪表上指针的格式（报表生成器和 SSRS）](report-design/formatting-pointers-on-a-gauge-report-builder-and-ssrs.md)   
 [向报表添加仪表&#40;报表生成器和 SSRS&#41;](report-design/add-a-gauge-to-a-report-report-builder-and-ssrs.md)   
 [设置线条、颜色和图像的格式（报表生成器和 SSRS）](report-design/images-report-builder-and-ssrs.md)   
 [仪表（报表生成器和 SSRS）](report-design/gauges-report-builder-and-ssrs.md)  
  
  
