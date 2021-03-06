---
title: XQuery 运算符对 xml 数据类型 |Microsoft 文档
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: sql
ms.component: xquery
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- XQuery, operators
- operators [XQuery]
- xml data type [SQL Server], XQuery
ms.assetid: 39ca3d2e-e928-4333-872b-75c4ccde8e79
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 62c4875c74d6ff67e8d1760a29ac48672fc7765a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="xquery-operators-against-the-xml-data-type"></a>针对 xml 数据类型的 XQuery 运算符
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  XQuery 支持下列运算符：  
  
-   数字运算符（+、-、*、div、mod）  
  
-   值比较运算符（eq、ne、lt、gt、le、ge）  
  
-   有关常规比较运算符 (=、 ！ =、 \<，>， \<=、 > =)  
  
 有关这些运算符的详细信息，请参阅[比较表达式&#40;XQuery&#41;](../xquery/comparison-expressions-xquery.md)  
  
## <a name="examples"></a>示例  
  
### <a name="a-using-general-operators"></a>A. 使用一般运算符  
 此查询说明了应用于序列和比较序列的一般运算符的使用方法。 查询检索从每个客户的电话号码序列**AdditionalContactInfo**列**联系人**表。 然后，将这个序列与两个电话号码（“111-111-1111”、“222-2222”）序列进行比较。  
  
 该查询使用**=** 比较运算符。 在右侧的序列中的每个节点**=** 运算符比较与左侧序列中的每个节点。 如果匹配节点，节点比较将**TRUE**。 然后将其转换为整数并与 1 进行比较，然后查询将返回客户 ID。  
  
```  
WITH XMLNAMESPACES (  
'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo' AS ACI,  
'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes' AS ACT)  
SELECT ContactID   
FROM   Person.Contact  
WHERE  AdditionalContactInfo.value('  
      //ACI:AdditionalContactInfo//ACT:telephoneNumber/ACT:number =   
          ("111-111-1111", "222-2222")',  
      'bit')= cast(1 as bit)  
```  
  
 还有一种方法，以观察前面的查询的工作原理： 检索从每个电话电话号码值**AdditionalContactInfo**列与两个电话号码的集进行比较。 如果该值处于集中，则该客户将返回到结果中。  
  
### <a name="b-using-a-numeric-operator"></a>B. 使用数字运算符  
 此查询中的运算符 + 是一个值运算符，因为它应用于单个项。 例如，将值 1 添加到查询返回的许多大小值上：  
  
```  
SELECT ProductModelID, Instructions.query('  
     declare namespace   
 AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
     for $i in (/AWMI:root/AWMI:Location)[1]  
     return   
       <Location LocationID="{ ($i/@LocationID) }"  
                   LotSize  = "{  number($i/@LotSize) }"  
                   LotSize2 = "{ number($i/@LotSize) + 1 }"  
                   LotSize3 = "{ number($i/@LotSize) + 2 }" >  
  
       </Location>  
') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
### <a name="c-using-a-value-operator"></a>C. 使用值运算符  
 下列查询将检索图片大小为“小”的产品型号的 <`Picture`> 元素：  
  
```  
SELECT CatalogDescription.query('  
     declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     for $P in /PD:ProductDescription/PD:Picture[PD:Size eq "small"]  
     return  
           $P  
    ') as Result  
FROM Production.ProductModel  
where ProductModelID=19  
```  
  
 因为两个操作数**eq**运算符原子值，在查询中使用值运算符。 你可以通过使用常规的比较运算符来编写相同的查询 ( **=** )。  
  
## <a name="see-also"></a>另请参阅  
 [对 xml 数据类型的 XQuery 函数](../xquery/xquery-functions-against-the-xml-data-type.md)   
 [XML 数据 (SQL Server)](../relational-databases/xml/xml-data-sql-server.md)   
 [XQuery 语言参考 (SQL Server)](../xquery/xquery-language-reference-sql-server.md)  
  
  
