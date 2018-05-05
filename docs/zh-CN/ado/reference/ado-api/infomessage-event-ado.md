---
title: InfoMessage 事件 (ADO) |Microsoft 文档
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection::InfoMessage
- InfoMessage
helpviewer_keywords:
- InfoMessage event [ADO]
ms.assetid: 468c87dd-e3bc-4084-9941-94d10743d4e9
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3216c9dfb31fdc7ac27051d409bbb6c658c2b091
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="infomessage-event-ado"></a>InfoMessage 事件 (ADO)
**InfoMessage**每当期间出现警告时就会调用事件**ConnectionEvent**操作。  
  
## <a name="syntax"></a>语法  
  
```  
  
InfoMessage pError, adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Parameters  
 *pError*  
 [错误](../../../ado/reference/ado-api/error-object.md)对象。 此参数将包含返回任何错误。 如果返回了多个错误，枚举**错误**集合可以找到它们。  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md)状态值。 如果出现警告时， *adStatus*设置为**adStatusOK**和*pError*条警告消息。  
  
 此事件返回之前，将此参数设置为**adStatusUnwantedEvent**以防止后续的通知。  
  
 *pConnection*  
 A[连接](../../../ado/reference/ado-api/connection-object-ado.md)对象。 警告发生的连接。 例如，可能出现警告，打开时**连接**对象或执行[命令](../../../ado/reference/ado-api/command-object-ado.md)上**连接**。  
  
## <a name="see-also"></a>另请参阅  
 [ADO 事件模型示例 （VC + +）](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO 事件处理程序摘要](../../../ado/guide/data/ado-event-handler-summary.md)   
 [连接对象 (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)