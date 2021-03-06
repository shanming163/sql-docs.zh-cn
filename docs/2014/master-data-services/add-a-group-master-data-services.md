---
title: 添加组 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- groups [Master Data Services], adding
- adding groups [Master Data Services]
ms.assetid: c7a88381-3b2c-4af7-9cf7-3a930c1abdee
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: d78b69946ebb068933a7691d454a792ad8f1ed07
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "48056787"
---
# <a name="add-a-group-master-data-services"></a>添加组 (Master Data Services)
  在 **中将某一组添加到** “组” [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 列表中，以便开始向 Web 应用程序分配权限。 在该组中的某一用户可以访问 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]之前，必须为该组提供针对一个或多个功能区域和模型对象的权限。  
  
## <a name="prerequisites"></a>必要條件  
 若要执行此过程：  
  
-   您必须有权访问 **“用户和组权限”** 功能区域。  
  
### <a name="to-add-a-group"></a>添加组  
  
1.  在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“用户和组权限”**。  
  
2.  在 **“用户”** 页上，从菜单栏中，单击 **“管理组”**。  
  
3.  单击 **“添加组”**。  
  
4.  输入该组的名称，组名之前应放置 Active Directory 域名或服务器计算机的名称，例如 *domain\group_name* 或 *computer\group_name*。  
  
5.  或者单击 **“检查名称”**。  
  
6.  单击“确定” 。  
  
    > [!NOTE]  
    >  当用户第一次访问 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]时，将用户的名称添加到 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 用户列表。  
  
## <a name="next-steps"></a>后续步骤  
  
-   [分配功能区域权限&#40;Master Data Services&#41;](assign-functional-area-permissions-master-data-services.md)  
  
## <a name="see-also"></a>请参阅  
 [安全性 (Master Data Services)](../../2014/master-data-services/security-master-data-services.md)  
  
  
