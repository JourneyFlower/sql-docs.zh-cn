---
title: 会话元素 (XMLA) |Microsoft 文档
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6be7e6cde72908273261e09020305441d6a42738
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2018
---
# <a name="session-element-xmla"></a>Session 元素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  使用在 SOAP 请求消息的 SOAP 标头来标识实例上的现有的显式会话[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]。  
  
 **Namespace** urn： 架构-microsoft-com:xml-分析  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
   <soap:Header>  
      ...  
      <Session  
         xmlns="urn:schemas-microsoft-com:xml-analysis"  
         SessionId="string" />  
      ...  
   </soap:Header>  
   <soap:Body>  
      ...  
   </soap:Body>  
</soap:Envelope>  
```  
  
## <a name="element-characteristics"></a>元素特征  
  
|特征|说明|  
|--------------------|-----------------|  
|数据类型和长度|无|  
|默认值|无|  
|基数|0-1：可出现一次且仅出现一次的可选元素。|  
  
## <a name="element-relationships"></a>元素关系  
  
|关系|元素|  
|------------------|-------------|  
|父元素|无|  
|子元素|无|  
  
## <a name="attributes"></a>属性  
  
|Attribute|Description|  
|---------------|-----------------|  
|SessionId|所需**字符串**标识要使用的会话的属性。 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 使用全局唯一标识符 (GUID) 识别会话。|  
  
## <a name="remarks"></a>注释  
 **会话**标头元素标识的现有的显式启动的会话上[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]实例。 **会话**元素是在以下类型的消息的 SOAP 标头的一部分：  
  
-   包含的 SOAP 响应[BeginSession](../../../analysis-services/xmla/xml-elements-headers/beginsession-element-xmla.md) SOAP 标头元素。  
  
-   SOAP 请求来标识在其上运行会话[发现](../../../analysis-services/xmla/xml-elements-methods-discover.md)或[执行](../../../analysis-services/xmla/xml-elements-methods-execute.md)方法。  
  
 会话标识符并不保证会话保持有效。 在指定的会话**会话**元素可能会过期。 例如，如果会话超时或与会话相关联的连接断开，则该会话将过期。 如果会话过期并且不再有效，则 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 将结束该会话并回滚当前正在处理的所有事务。 使用不再有效的会话标识符发送的任何 SOAP 消息将失败，相应 SOAP 错误指示找不到指定的会话。  
  
 如果**会话**元素不会发送 SOAP 请求的一部分[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]实例隐式开始的会话的持续时间**发现**或**执行**方法调用，然后结束完成方法调用后该会话。  
  
## <a name="see-also"></a>另请参阅  
 [EndSession 元素 & #40;XMLA & #41;](../../../analysis-services/xmla/xml-elements-headers/endsession-element-xmla.md)   
 [管理连接和会话 & #40;XMLA & #41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [标头 & #40;XMLA & #41;](../../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)  
  
  
