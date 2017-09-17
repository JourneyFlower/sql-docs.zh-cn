---
title: "ALTER 消息类型 (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_MESSAGE_TYPE_TSQL
- ALTER MESSAGE TYPE
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER MESSAGE TYPE statement
- modifying message types
- message types [Service Broker], modifying
ms.assetid: 98c94176-2bdf-4725-b4bc-d33b6b14817d
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1ed67afafb33faa22ececbea51c1ed502b1e5725
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="alter-message-type-transact-sql"></a>ALTER MESSAGE TYPE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  更改消息类型的属性。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
ALTER MESSAGE TYPE message_type_name  
   VALIDATION =  
    {  NONE   
     | EMPTY   
     | WELL_FORMED_XML   
     | VALID_XML WITH SCHEMA COLLECTION schema_collection_name }  
[ ; ]  
```  
  
## <a name="arguments"></a>参数  
 *message_type_name*  
 要更改的消息类型的名称。 不能指定服务器、数据库和架构名称。  
  
 VALIDATION  
 指定 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 对此类型消息的消息正文的验证方式。  
  
 无  
 不执行任何验证。 消息正文可以包含任何数据，也可以为 NULL。  
  
 EMPTY  
 消息正文必须为 NULL。  
  
 WELL_FORMED_XML  
 消息正文必须包含格式正确的 XML。  
  
 VALID_XML_WITH_SCHEMA = *schema_collection_name*  
 消息正文必须包含符合指定架构集合中的某一架构的 XML。 *Schema_collection_name*必须是现有 XML 架构集合的名称。  
  
## <a name="remarks"></a>注释  
 更改消息类型的验证不会影响已传递到队列的消息。  
  
 若要更改消息类型的 AUTHORIZATION，请使用 ALTER AUTHORIZATION 语句。  
  
## <a name="permissions"></a>Permissions  
 更改消息类型的权限默认为消息类型的成员的所有者**db_ddladmin**或**db_owner**固定数据库角色和成员的**sysadmin**固定的服务器角色。  
  
 如果 ALTER MESSAGE TYPE 语句指定了一个架构集合，则执行该语句的用户必须对指定的架构集合具有 REFERENCES 权限。  
  
## <a name="examples"></a>示例  
 以下示例更改消息类型 `//Adventure-Works.com/Expenses/SubmitExpense`，以要求消息正文包含格式正确的 XML 文档。  
  
```  
ALTER MESSAGE TYPE  
    [//Adventure-Works.com/Expenses/SubmitExpense]  
    VALIDATION = WELL_FORMED_XML ;  
```  
  
## <a name="see-also"></a>另请参阅  
 [ALTER AUTHORIZATION &#40;Transact SQL &#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [创建消息类型 &#40;Transact SQL &#41;](../../t-sql/statements/create-message-type-transact-sql.md)   
 [删除消息类型 &#40;Transact SQL &#41;](../../t-sql/statements/drop-message-type-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
  