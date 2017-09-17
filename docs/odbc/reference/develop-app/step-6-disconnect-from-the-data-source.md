---
title: "步骤 6： 从数据源断开连接 |Microsoft 文档"
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
- application process [ODBC], disconnecting from data source
- data sources [ODBC], disconnecting
- disconnecting from data source [ODBC]
ms.assetid: 6ad759ba-4721-4d8f-9b26-de976d4fc1a0
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ce3ea03a637e8edce89c83f196e4fcafd97dfdc8
ms.contentlocale: zh-cn
ms.lasthandoff: 09/09/2017

---
# <a name="step-6-disconnect-from-the-data-source"></a>步骤 6： 从数据源断开连接
最后一步是从数据源断开连接下图中所示。 首先，应用程序通过调用释放任何语句句柄**SQLFreeHandle**。 有关详细信息，请参阅[释放语句处理](../../../odbc/reference/develop-app/freeing-a-statement-handle-odbc.md)。  
  
 ![显示与数据源断开连接](../../../odbc/reference/develop-app/media/pr17.gif "pr17")  
  
 接下来，从数据源断开连接的应用程序**SQLDisconnect**并释放与连接句柄**SQLFreeHandle**。 有关详细信息，请参阅[断开与数据源或驱动程序的连接](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md)。  
  
 最后，应用程序释放使用的环境句柄**SQLFreeHandle**和卸载驱动程序管理器。 有关详细信息，请参阅[分配环境处理](../../../odbc/reference/develop-app/allocating-the-environment-handle.md)。