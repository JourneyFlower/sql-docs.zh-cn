---
title: 估计数据库的大小 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: databases
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- space allocation [SQL Server], database size
- calculating database size
- increasing database size
- database size [SQL Server], estimating
- predicting database size
- size [SQL Server], databases
- estimating database size
- designing databases [SQL Server], estimating size
ms.assetid: 5b240161-eba4-44b0-946c-61a8fc00fc8c
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 24ac34c991401a8fb7a2687befb894d1e175a668
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="estimate-the-size-of-a-database"></a>估计数据库的大小
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  在设计数据库时，可能需要估计填入数据后数据库的大小。 估计数据库的大小可以帮助您确定执行下列操作所需的硬件配置：  
  
-   获得应用程序所需的性能。  
  
-   保证有足够的物理磁盘空间用于存储数据和索引。  
  
 估计数据库的大小还可以帮助您确定是否需要修改数据库设计。 例如，您可能会发现估计的数据库大小太大，无法在您的单位中实现，因此需要进行更多的规范化处理。 相反，也可能估计大小比需要的更小。 这就允许您降低数据库的规范化以提高查询性能。  
  
 若要估计数据库的大小，请分别估计每个表的大小，然后将各个值累加起来即可。 表的大小取决于表是否有索引，如果有索引，还取决于索引的类型。  
  
## <a name="in-this-section"></a>本节内容  
  
|主题|Description|  
|-----------|-----------------|  
|[估计表的大小](../../relational-databases/databases/estimate-the-size-of-a-table.md)|定义估计用于存储表和相关索引中的数据的空间量所需的步骤和计算。|  
|[估计堆的大小](../../relational-databases/databases/estimate-the-size-of-a-heap.md)|定义估计用于存储堆中的数据的空间量所需的步骤和计算。 堆是没有聚集索引的表。|  
|[估计聚集索引的大小](../../relational-databases/databases/estimate-the-size-of-a-clustered-index.md)|定义估计用于存储聚集索引中的数据的空间量所需的步骤和计算。|  
|[估计非聚集索引的大小](../../relational-databases/databases/estimate-the-size-of-a-nonclustered-index.md)|定义估计用于存储非聚集索引中的数据的空间量所需的步骤和计算。|  
  
  
