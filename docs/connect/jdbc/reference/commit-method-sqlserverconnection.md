---
title: commit 方法 (SQLServerConnection) |Microsoft 文档
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerConnection.commit
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c7346165-51bf-4844-b64c-29833c147236
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 42cd2c1d8a189e353d4bfd6bbd2f67b3c14e0df1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="commit-method-sqlserverconnection"></a>commit 方法 (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  进行所有更改以来所做的上一次提交或回滚永久性的并释放当前持有这任何数据库锁[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)对象。  
  
## <a name="syntax"></a>语法  
  
```  
  
public void commit()  
```  
  
## <a name="exceptions"></a>异常  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>注释  
 由 java.sql.Connection 接口中的提交方法指定此 commit 方法。  
  
 仅当已禁用自动提交模式时才应使用此方法。  
  
 请注意，如果客户端启动了手动事务，随后出于某种原因 SQL Server 回滚了该手动事务，此时此方法将失败并引发异常。 例如，如果客户端调用的存储的过程的显式调用 ROLLBACK TRANSACTION，引发异常，然后客户端调用了 commit 方法。 此外，如果 SQL Server 将引发错误的足够严重性 （16 个或更高版本） 回滚客户端启动手动事务;commit 方法的后续调用将引发异常。  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerConnection 成员](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection 类](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
