---
title: "创建 CDATA 部分使用 sql:use-cdata (SQLXML 4.0) |Microsoft 文档"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- markup characters [SQLXML]
- special characters [SQLXML]
- use-cdata annotation
- plain text [SQLXML]
- CDATA sections
- escaping blocks of text [SQLXML]
- annotated XSD schemas, CDATA sections
- sql:use-cdata
ms.assetid: 26d2b9dc-f857-44ff-bcd4-aaf64ff809d0
caps.latest.revision: "26"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1b886efd0a8d792d52ebd8de94bd47f2351d15fc
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2017
---
# <a name="creating-cdata-sections-using-sqluse-cdata-sqlxml-40"></a>使用 sql:use-cdata 创建 CDATA 节 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]在 XML 中，CDATA 节用于转义包含否则将识别为标记字符的字符的文本块。  
  
 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的数据库有时会包含被 XML 语法分析程序视为标记字符的字符；例如，尖括号（< 和 >）、小于或等于符号 (<=) 和 & 符号被视为标记字符。 但是，可以在 CDATA 节中对这类特殊字符进行包装，使它们不被视为标记字符。 XML 语法分析程序将 CDATA 节中的文本视为纯文本。  
  
 **Sql:use-cdata**批注用于指定返回的数据[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]应在 CDATA 部分包装 (也就是说，它指示从某一列的值是否指定**sql:field**应括在 CDATA 节中)。 **Sql:use-cdata**批注可以指定仅在将映射到数据库列的元素上。  
  
 **Sql:use-cdata**批注采用布尔值 (0 = false、 1 = true)。 可接受的值为 0、1、true 和 false。  
  
 此批注不能与使用**sql:url-编码**或上 ID、 IDREF、 IDREFS、 NMTOKEN 和 NMTOKENS 属性类型。  
  
## <a name="examples"></a>示例  
 若要创建使用以下示例的工作示例，必须满足某些要求。 有关详细信息，请参阅[要求运行 SQLXML 示例](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md)。  
  
### <a name="a-specifying-sqluse-cdata-on-an-element"></a>A. 在元素上指定 sql:use-cdata  
 在以下架构中， **sql:use-cdata**设为 1 (True)  **\<AddressLine1 >**内**\<地址 >**元素。 结果，将在 CDATA 节中返回数据。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Address"   
               sql:relation="Person.Address"   
               sql:key-fields="AddressID" >  
   <xsd:complexType>  
        <xsd:sequence>  
          <xsd:element name="AddressID"  type="xsd:string" />  
          <xsd:element name="AddressLine1" type="xsd:string"   
                       sql:use-cdata="1" />  
        </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>若要测试示例 XPath 查询根据架构  
  
1.  复制上面的架构代码，并将它粘贴到文本文件中。 将文件另存为 UseCData.xml。  
  
2.  复制以下模板，并将它粘贴到文本文件中。 在保存 UseCData.xml 的相同目录中将文件另存为 UseCDataT.xml。  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="UseCData.xml">  
            /Address[AddressID < 11]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     为映射架构 (UseCData.xml) 指定的目录路径相对于保存模板的目录。 也可以指定绝对路径，例如：  
  
    ```  
    mapping-schema="C:\SqlXmlTest\UseCData.xml"  
    ```  
  
3.  创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。  
  
     有关详细信息，请参阅[到执行 SQLXML 4.0 查询使用 ADO](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。  
  
 部分结果集如下：  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Address>   
    <AddressID>1</CustomerID>   
    <AddressLine1>   
      <![CDATA[ 1970 Napa Ct.  ]]>   
    </AddressLine1>   
  </Address>  
  <Address>  
    <AddressLine1>   
      <![CDATA[ 9833 Mt. Dias Blv. ]]>   
    </AddressLine1>   
  </Address>  
  ...  
</ROOT>  
```  
  
  