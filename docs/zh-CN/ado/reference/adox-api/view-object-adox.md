---
title: 查看对象 (ADOX) |Microsoft 文档
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- View
helpviewer_keywords:
- View object [ADOX]
ms.assetid: 653421ce-7b94-43d0-9bc6-4900f8f2af45
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 025ceb637342f2f4ab0f2bb9a576518b9b255bcc
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="view-object-adox"></a>视图对象 (ADOX)
表示经过筛选的记录或一个虚拟表集。 用 ADO 结合使用时[命令](../../../ado/reference/ado-api/command-object-ado.md)对象，**视图**对象可以用于添加、 删除或修改视图。  
  
## <a name="remarks"></a>注释  
 视图是从其他数据库表或视图创建一个虚拟表。 **视图**对象允许你创建一个视图，而无需知道，或使用提供程序的"创建视图"语法。  
  
 使用的属性**视图**对象，你可以：  
  
-   指定与视图[名称](../../../ado/reference/adox-api/name-property-adox.md)属性。  
  
-   指定 ADO**命令**可以用于添加、 删除或修改具有的视图对象[命令](../../../ado/reference/adox-api/command-property-adox.md)属性。  
  
-   返回与日期信息[时间](../../../ado/reference/adox-api/datecreated-property-adox.md)和[DateModified](../../../ado/reference/adox-api/datemodified-property-adox.md)属性。  
  
 本部分包含以下主题。  
  
-   [视图对象属性、方法和事件](../../../ado/reference/adox-api/view-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>另请参阅  
 [视图和字段集合示例 (VB)](../../../ado/reference/adox-api/views-and-fields-collections-example-vb.md)   
 [视图追加方法示例 (VB)](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [视图集合，CommandText 属性示例 (VB)](../../../ado/reference/adox-api/views-collection-commandtext-property-example-vb.md)   
 [视图删除方法示例 (VB)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)   
 [视图集合 (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)