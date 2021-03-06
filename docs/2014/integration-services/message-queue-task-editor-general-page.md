---
title: 消息队列任务编辑器 （常规页） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.msgqueuetask.general.f1
helpviewer_keywords:
- Message Queue Task Editor
ms.assetid: 09368b18-37a5-4321-a173-7cfe5d42d2a2
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ea436e349a19d10eeb86a62b74f154b56b60ef7a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "48204007"
---
# <a name="message-queue-task-editor-general-page"></a>消息队列任务编辑器（“常规”页）
  可以使用 **“消息队列任务编辑器”** 对话框的 **“常规”** 页，对消息队列任务进行命名和说明，指定消息格式，以及指示任务是发送还是接收消息。  
  
 若要了解此任务，请参阅 [Message Queue Task](control-flow/message-queue-task.md)。  
  
## <a name="options"></a>选项  
 **名称**  
 为消息队列任务提供唯一的名称。 此名称用作任务图标中的标签。  
  
> [!NOTE]  
>  任务名称在一个包内必须是唯一的。  
  
 **Description**  
 键入对消息队列任务的说明。  
  
 **Use2000Format**  
 指示是否使用消息队列（也称为 MSMQ）的 2000 格式。 默认值为 `False`。  
  
 **MSMQConnection**  
 选择现有 MSMQ 连接管理器，或单击“\<新建连接...>”以创建新的连接管理器。  
  
 **相关主题**：[MSMQ 连接管理器](connection-manager/msmq-connection-manager.md)、[MSMQ 连接管理器编辑器](../../2014/integration-services/msmq-connection-manager-editor.md)  
  
 **Message**  
 指定消息队列任务是发送消息还是接收消息。 如果选择了 **“发送消息”**，则该对话框的左窗格将列出“发送”页；如果选择了 **“接收消息”**，则将列出“接收”页。 默认情况下，此值设置为 **“发送消息”**。  
  
## <a name="see-also"></a>请参阅  
 [Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [消息队列任务编辑器&#40;接收页&#41;](../../2014/integration-services/message-queue-task-editor-receive-page.md)   
 [消息队列任务编辑器&#40;发送页&#41;](../../2014/integration-services/message-queue-task-editor-send-page.md)   
 [“表达式”页](expressions/expressions-page.md)  
  
  
