---
title: 算术运算符 (DMX) |Microsoft 文档
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- arithmetic operators
ms.assetid: befe4f0c-e5dd-4ae1-b88e-6ac7aab2181a
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 10894ee5f3ab7d0a7defecf324a297b4bd3ad6ed
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="operators---arithmetic"></a>操作员-算术
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  你可以使用算术运算符在数据挖掘扩展插件 (DMX) 用于中的算术计算[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]，包括加法、 减法、 乘法和除法。  
  
 下表标识了 DMX 支持的算术运算符。  
  
|运算符|Description|  
|--------------|-----------------|  
|[+&#40;添加&#41; &#40;DMX&#41;](../dmx/add-dmx.md)|将两个数相加。|  
|[-&#40;减去&#41; &#40;DMX&#41;](../dmx/subtract-dmx.md)|从一个数中减去另一个数。|  
|[&#42;&#40;乘&#41; &#40;DMX&#41;](../dmx/multiply-dmx.md)|将一个数与另一个数相乘。|  
|[&#40;将划分&#41; &#40;DMX&#41;](../dmx/divide-dmx.md)|将一个数除以另一个数。|  
  
 下列规则确定了各种运算符在 DMX 表达式中的优先顺序：  
  
-   如果表达式中有多个算术运算符，则先计算乘除，后计算加减。  
  
-   如果表达式中的所有算术运算符具有相同的优先顺序，则运算顺序为从左到右。  
  
-   括号中的表达式运算优先于其他所有运算。  
  
## <a name="see-also"></a>另请参阅  
 [数据挖掘扩展插件 & #40; DMX & #41;引用](../dmx/data-mining-extensions-dmx-reference.md)   
 [数据挖掘扩展插件&#40;DMX&#41;函数引用](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [数据挖掘扩展插件&#40;DMX&#41;运算符参考](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [数据挖掘扩展插件 & #40; DMX & #41;语句引用](../dmx/data-mining-extensions-dmx-statements.md)   
 [数据挖掘扩展插件&#40;DMX&#41;语法约定](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [数据挖掘扩展插件&#40;DMX&#41;语法元素](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [表达式&#40;DMX&#41;](../dmx/expressions-dmx.md)   
 [常规预测函数&#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [运算符&#40;DMX&#41;](../dmx/operators-dmx.md)   
 [结构和使用情况的 DMX 预测查询](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [了解 DMX Select 语句](../dmx/understanding-the-dmx-select-statement.md)  
  
  
