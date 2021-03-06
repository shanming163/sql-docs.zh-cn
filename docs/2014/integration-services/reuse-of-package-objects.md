---
title: 重用包对象 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- GUID regenerating [Integration Services]
- reusing packages
- templates [Integration Services]
- copying packages
- regenerating package GUID
ms.assetid: 08f723bf-15b5-44bd-9a46-04e8781bfbfb
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a2b9179a6c94c6bffd0a7ebc9f5c9b1bb2897605
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "48156667"
---
# <a name="reuse-of-package-objects"></a>重用包对象
  要经常重用的包功能。 例如，如果创建了一组任务，可能希望将这些项作为一个组一起重用，或者可能希望重用单个项，如在其他 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目中创建的连接管理器。  
  
## <a name="copy-and-paste"></a>复制和粘贴  
 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 和 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器支持复制和粘贴包对象，包对象可以包括控制流项、数据流项和连接管理器。 可以在项目之间和包之间进行复制和粘贴。 如果解决方案包含了多个项目，则可以在项目之间进行复制，并且项目可以属于不同类型。  
  
 如果解决方案包含多个包，则可以在它们之间进行复制和粘贴。 包可以位于相同或不同的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目中。 但是，包对象可能对其他对象有依赖关系，没有这些对象它们将无效。 例如，“执行 SQL”任务使用连接管理器，因此还必须复制连接管理器才能使任务工作。 而且，某些包对象需要包已经包含某个对象，如果没有此对象，则无法将所复制的对象成功粘贴到包中。 例如，包至少要有一个“数据流”任务，否则无法将数据流粘贴到该包。  
  
 您可能会发现自己重复地复制了同一个包。 若要避免复制进程，可以将这些包指定为模板，并在创建新包时使用它们。  
  
 复制包对象时，[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 会向新对象的 `ID` 属性自动分配新的 GUID，并更新 `Name` 属性。  
  
 无法复制变量。 如果诸如任务这样的对象使用了变量，则必须在目标包中重新创建变量。 相比之下，如果复制整个包，则包中的变量也会被复制。  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [复制包对象](../../2014/integration-services/copy-package-objects.md)  
  
-   [复制项目项](../../2014/integration-services/copy-project-items.md)  
  
-   [将包保存为包模板](../../2014/integration-services/save-a-package-as-a-package-template.md)  
  
  
