---
title: "PUBLISHINGSERVERNAME (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PUBLISHINGSERVERNAME_TSQL
- PUBLISHINGSERVERNAME
dev_langs:
- TSQL
helpviewer_keywords:
- PUBLISHINGSERVERNAME function
- Publishers [SQL Server replication], names
ms.assetid: e7c278e5-ab23-419e-ab3e-3bb20b0636df
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a5aeeb414f9c980429d20f123e1f9c986b147eee
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="replication-functions---publishingservername"></a>复制功能-PUBLISHINGSERVERNAME
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  为参与数据库镜像会话的已发布数据库返回起始发布服务器的名称。 此函数在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 发布服务器实例的发布数据库中执行。 使用它可确定已发布数据库的起始发布服务器。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
PUBLISHINGSERVERNAME()  
```  
  
## <a name="return-types"></a>返回类型  
 **nvarchar**  
  
## <a name="remarks"></a>注释  
 PUBLISHINGSERVERNAME 用于所有类型的复制。  
  
 当数据库镜像会话存在于发布服务器与镜像伙伴实例之间的发布数据库中时，将使用 PUBLISHINGSERVERNAME。  
  
 必须在发布数据库的上下文中执行此函数。 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 镜像服务器实例的发布数据库中执行 PUBLISHINGSERVERNAME 时，将返回已发布数据库源自的发布服务器实例的名称。 在镜像服务器实例的未发布数据库中或在故障转移后从镜像服务器实例发布的数据库中执行此函数时，将返回此镜像服务器实例的名称。 在起始发布服务器实例中执行此函数时，将返回此发布服务器的名称。  
  
## <a name="see-also"></a>另请参阅  
 [数据库镜像和复制 (SQL Server)](../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md)   
 [复制的功能 &#40;Transact SQL &#41;](http://msdn.microsoft.com/library/53702dee-de58-47d5-a552-7f32000f77d4)  
  
  