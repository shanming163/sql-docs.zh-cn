---
title: 扩展 OLAP 功能 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 49a17ff3-94e9-4969-84fc-37d49e63933b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 34e900268c42f1bc4541b1ddf6aad5901fc35480
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "48212957"
---
# <a name="extending-olap-functionality"></a>扩展 OLAP 功能
  作为一名程序员，您可以通过编写程序集、个性化扩展插件和存储过程来扩展 Analysis Services，以便提供您要在多个数据库应用程序中使用并重新确定其用途的功能。 程序集用于通过向 MDX 语言添加新的过程和函数或通过个性化外接程序来扩展多维模型功能。  
  
 存储过程可用于调用外部例程，并通过允许一次性开发常用代码并将其存储在单个位置来简化 Analysis Services 数据库的开发和实现。 存储过程可用来向应用程序中添加 MDX 的本机功能未提供的商业功能。  
  
 个性化设置是添加到多维数据集的自定义对象，可提供随用户的不同而不同的行为。 个性化设置并不是多维数据集中的永久对象，而是在用户会话期间客户端应用程序动态应用的对象。 例如，根据访问数据的人员更改货币值的币种、提供单个 KPI 或为网上购物的老客户提供针对性建议的列表。  
  
## <a name="in-this-section"></a>本节内容  
 [通过个性化设置扩展 OLAP](extending-olap-through-personalizations.md)  
  
 [Analysis Services 个性化设置扩展](analysis-services-personalization-extensions.md)  
  
 [定义存储过程](../../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
