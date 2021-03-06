---
title: SQLServerStatement 类 |Microsoft 文档
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ec24963c-8b51-4838-91e9-1fbfa2347451
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 14add0b451947092946129c9388366eb10186dce
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="sqlserverstatement-class"></a>SQLServerStatement 类
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  表示 JDBC 语句功能的基本实现。  
  
 **包：** com.microsoft.sqlserver.jdbc  
  
 **实现：** [ISQLServerStatement](../../../connect/jdbc/reference/isqlserverstatement-interface.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
public class SQLServerStatement  
```  
  
## <a name="remarks"></a>注释  
 有关准备语句，可调用语句 JDBC，SQLServerStatement 类还提供大量的基类实现方法。 SQLServerStatement 类的基本角色是运行 SQL 语句，然后返回更新计数和结果将设置为用户应用程序。  
  
 此类支持到 SQLServerStatement 类、 ISQLServerStatement 接口以及 java.sql.Statement 接口解包。 有关详细信息，请参阅[包装和接口](../../../connect/jdbc/wrappers-and-interfaces.md)。  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerStatement 成员](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [JDBC 驱动程序 API 参考](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
