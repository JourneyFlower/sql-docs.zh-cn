---
title: "RollbackTransaction 元素 (XMLA) |Microsoft 文档"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- RollbackTransaction Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#RollbackTransaction
- microsoft.xml.analysis.rollbacktransaction
- urn:schemas-microsoft-com:xml-analysis#RollbackTransaction
helpviewer_keywords:
- RollbackTransaction command
ms.assetid: 40e7dc00-656f-412f-97f0-d05bf7caa196
caps.latest.revision: 13
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a74a55f0d5325ca37b47ce0544bfe7dab44dfef6
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="rollbacktransaction-element-xmla"></a>RollbackTransaction 元素 (XMLA)
  回滚事务上与的实例的当前会话[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]。  
  
## <a name="syntax"></a>语法  
  
```xml  
  
<Command>  
   <RollbackTransaction />  
</Command>  
```  
  
## <a name="element-characteristics"></a>元素特征  
  
|特征|说明|  
|--------------------|-----------------|  
|数据类型和长度|无|  
|默认值|无|  
|基数|0-n：可多次出现的可选元素。|  
  
## <a name="element-relationships"></a>元素关系  
  
|关系|元素|  
|------------------|-------------|  
|父元素|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|子元素|无|  
  
## <a name="remarks"></a>注释  
 **RollbackTransaction**命令回滚所有活动的事务，使用显式定义**BeginTransaction**元素，在当前会话。 如果不存在活动事务，则会出现错误。 如果存在活动事务，则 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 实例会将当前会话的事务引用计数减少到零，以回滚所有活动事务。  
  
## <a name="see-also"></a>另请参阅  
 [BeginTransaction 元素 &#40;XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md)   
 [取消元素 &#40;XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)   
 [CommitTransaction 元素 &#40;XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)   
 [命令 &#40;XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  