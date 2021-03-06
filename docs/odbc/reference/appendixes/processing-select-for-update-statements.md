---
title: 处理 UPDATE 语句的选择 |Microsoft 文档
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
- ODBC cursor library [ODBC], statement processing
- SQL statements [ODBC], select for update statements
- select for update [ODBC]
- SQL statements [ODBC], cursor library
- cursor library [ODBC], select for update statements
- ODBC cursor library [ODBC], select for update statements
- cursor library [ODBC], statement processing
ms.assetid: 8d2e79a4-5daf-458e-a536-d8b6e588753e
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ede999422f6b52112356aa7c9c4b7715eafb96c6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="processing-select-for-update-statements"></a>处理 UPDATE 语句的选择
> [!IMPORTANT]  
>  将 Windows 的未来版本中删除该功能。 避免在新的开发工作中使用此功能，并计划修改当前使用此功能的应用程序。 Microsoft 建议使用驱动程序的游标功能。  
  
 最大互操作性，应用程序应生成将通过执行更新与定位的 update 语句的结果集**选择更新**语句。 虽然游标库不需要它，但它仍需要由支持定位的更新语句的大多数数据源。  
  
 游标库忽略中的列**FOR UPDATE**子句**选择 FOR UPDATE**语句; 它会此子句删除然后再将该语句传递到驱动程序。 在光标库中，SQL_ATTR_CONCURRENCY 语句属性的以及在上一节中所述的限制，控件是否在结果中的列设置可以更新。
