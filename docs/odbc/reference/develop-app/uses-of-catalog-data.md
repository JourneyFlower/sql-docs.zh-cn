---
title: 使用目录数据 |Microsoft 文档
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- catalog data [ODBC]
- functions [ODBC], catalog functions
- catalog functions [ODBC], using catalog data
ms.assetid: d5915d0c-eec3-4382-850e-bd863763c99a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b4d510a0f7e0d0c401e0f8ea8a8c346a917f05c3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="uses-of-catalog-data"></a>使用的目录数据
应用程序使用各种不同的方式的目录数据。 下面是一些常见用途：  
  
-   **在运行时构造 SQL 语句。** 垂直应用程序，如顺序条目应用程序，包含硬编码 SQL 语句。 表和应用程序使用的列被固定的提前，如访问这些表的语句。 例如，一个顺序输入应用程序通常包含单个参数化**插入**语句将新订单添加到系统。  
  
     泛型应用程序，如电子表格程序，使用 ODBC 来检索数据，通常在运行时根据用户输入构造 SQL 语句。 此类应用程序可能需要用户键入的表和要使用列的名称。 但是，它将会便于用户如果应用程序显示的表和用户无法从中进行选择的列的列表。 若要生成这些列表，该应用程序将调用**SQLTables**和**SQLColumns**目录函数。  
  
-   **在开发过程中构造 SQL 语句。** 通常情况下，应用程序开发环境允许程序员也要在开发程序时创建数据库查询。 然后，查询是硬编码在构建应用程序。  
  
     此外可以使用此类环境**SQLTables**和**SQLColumns**创建程序员无法从中进行选择的列表。 此外可以使用这些环境**SQLPrimaryKeys**和**SQLForeignKeys**自动确定，显示所选表之间的关系并将**SQLStatistics**来确定并突出显示编制索引的字段，因此程序员可以创建高效的查询。  
  
-   **构造游标。** 可以使用应用程序、 驱动程序或提供了一个可滚动游标引擎的中间件**SQLSpecialColumns**来确定哪些列或多列唯一标识行。 无法生成程序*键集*包含每个已提取的行的这些列中的值。 当应用程序滚动回行时，它将使用这些值提取行的最新数据。 有关可滚动游标和游标的详细信息，请参阅[可滚动游标](../../../odbc/reference/develop-app/scrollable-cursors.md)。
