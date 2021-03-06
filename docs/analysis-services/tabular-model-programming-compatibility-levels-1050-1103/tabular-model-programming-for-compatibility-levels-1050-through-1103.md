---
title: 表格模型编程的兼容性级别 1050 通过 1103年 |Microsoft 文档
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a1e14033255d45eaacda1d553c71224e11dfe964
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2018
---
# <a name="tabular-model-programming-for-compatibility-levels-1050-through-1103"></a>表格模型编程的兼容性级别 1050年通过 1103
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  表格模型使用关系构造对分析和报表应用程序使用的 Analysis Services 数据建模。 这些模型运行在配置用于表格模式的 Analysis Service 实例上，使用内存中分析引擎执行存储和快速表扫描（支持在请求数据时对其进行聚合和计算）。  
  
 如果表格模型数据库最能满足您的自定义 BI 解决方案的要求，则可以使用任意 Analysis Services 客户端库和编程接口将您的应用程序集成到 Analysis Services 实例上的表格模型。 若要查询和计算表格模型数据，可以在代码中使用嵌入的 MDX 或 DAX。  
  
 在早期版本的 Analysis Services，兼容级别 1050 1103，通过在特定模型中创建的表格模型以编程方式在 AMO、 ADOMD.NET、 XMLA 或 OLE DB 中使用的对象是从根本上相同表格和多维解决方案。 具体而言，对于多维模型定义的对象元数据也适用于表格模型兼容性级别 1050年 1103年。  
  
 从 SQL Server 2016 开始，表格模型可以生成，或升级到 1200年或更高的兼容性级别，使用表格元数据来定义模型。 在此级别是完全不同的元数据和可编程性。 请参阅[表格模型编程的兼容性级别 1200年及更高版本](../../analysis-services/tabular-model-programming-compatibility-level-1200/tabular-model-programming-for-compatibility-level-1200.md)和[升级 Analysis Services](../../database-engine/install-windows/upgrade-analysis-services.md)有关详细信息。  
  
## <a name="in-this-section"></a>本節內容  
 [Business Intelligence & #40; 有关的 CSDL 批注CSDLBI & #41;](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/csdl-annotations-for-business-intelligence-csdlbi.md)  
  
 [了解表格对象模型在兼容性级别 1050年通过 1103](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
 [BI 批注的 CSDL 的技术参考](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/technical-reference-for-bi-annotations-to-csdl.md)  
  

[IMDEmbeddedData 接口](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/imdembeddeddata-interface.md)


  
  
