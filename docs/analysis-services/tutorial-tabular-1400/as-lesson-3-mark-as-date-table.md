---
title: Analysis Services 教程第 3 课： 标记为日期表 |Microsoft 文档
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 82b4093aa1a46cf1a7bb14b4c689ba6ba09e4d2b
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2018
---
# <a name="mark-as-date-table"></a>将标记为日期表

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

在第 2 课： 获取数据，你导入名为的维度表**DimDate**。 虽然您的模型中此表的名称为 DimDate，它可以也被称为*日期表*，因为它包含日期和时间数据。  
  
每当使用 DAX 时间智能函数，如当你创建的度量值更高版本，你必须指定属性包括*日期表*和唯一标识符*日期列*该表中。
  
在本课程中，你将标记**DimDate**表作为*日期表*和**日期**列 （在日期表中） 作为*日期列*（唯一标识符）。  

将标记日期表和日期列之前，它是执行少量的管理，以便更轻松地了解您的模型的好时机。 请注意 DimDate 表中一个名为列**FullDateAlternateKey**。 此列的表中包含每个日历年中每一天中占一行。 在度量值公式和报表中大量使用此列。 但是，FullDateAlternateKey 不是真正此列的良好标识符。 你将其命名为**日期**，使其更轻松地识别和在公式中包含。 只要有可能，它是重命名对象，如表和列，以使它们更轻松地识别 SSDT 和客户端报告应用程序中的一个好办法。 
  
估计的时间才能完成本课程：**三分钟**  
  
## <a name="prerequisites"></a>必要條件  

本文摘自表格建模教程中，应按顺序完成。 之前在本课程中执行任务，你应完成上一课： [Lesson 2： 获取数据](../tutorial-tabular-1400/as-lesson-2-get-data.md)。 

### <a name="to-rename-the-fulldatealternatekey-column"></a>若要重命名 FullDateAlternateKey 列

1.  在模型设计器中，单击**DimDate**表。

2.  双击的标头**FullDateAlternateKey**列，然后将其命名为和**日期**。

  
### <a name="to-set-mark-as-date-table"></a>标记为日期表  
  
1.  选择“日期”列，然后在“属性”窗口的“数据类型”下面确保已选中“日期”。  
  
2.  单击“表”菜单，然后依次单击“日期”和“标记为日期表”。  
  
3.  在“标记为日期表”对话框的“日期”列表框中，选择“日期”列作为唯一标识符。 默认情况下通常选择它。 单击 **“确定”**。 

    ![as-lesson3-date-table](../tutorial-tabular-1400/media/as-lesson3-date-table.png)
  

## <a name="whats-next"></a>下一步是什么？

[第 4 课： 创建关系](../tutorial-tabular-1400/as-lesson-4-create-relationships.md)。
  
