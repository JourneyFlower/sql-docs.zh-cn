---
title: "REVOKE 类型权限 (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- REVOKE statement, types
- permissions [SQL Server], types
- type permissions [SQL Server]
ms.assetid: 3969c7e9-ca10-4c67-971b-25d2dfccf650
caps.latest.revision: 30
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b7421493593b931d8178e2b4b3377ef7d9fcdd80
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="revoke-type-permissions-transact-sql"></a>REVOKE 类型权限 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  撤消对类型的权限。  
  
  ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
REVOKE [ GRANT OPTION FOR ] permission [ ,...n ]   
    ON TYPE :: [ schema_name ]. type_name   
    { FROM | TO } <database_principal> [ ,...n ]   
    [ CASCADE ]  
    [ AS <database_principal> ]  
  
<database_principal> ::=   
      Database_user   
    | Database_role   
    | Application_role   
    | Database_user_mapped_to_Windows_User   
    | Database_user_mapped_to_Windows_Group   
    | Database_user_mapped_to_certificate   
    | Database_user_mapped_to_asymmetric_key   
    | Database_user_with_no_login    
```  
  
## <a name="arguments"></a>参数  
 *权限*  
 指定可对类型撤消的权限。 有关权限的列表，请参阅本主题后面的“备注”部分。  
  
 在类型上**::** [ *schema_name* ] **。** *类型 _ 名称*  
 指定要对其撤消权限的类型。 作用域限定符 (**::**) 是必需的。 如果*schema_name*未指定，则使用默认架构。 如果*schema_name*指定，则架构作用域限定符 (**。**) 是必需的。  
  
 {从 |为} \<database_principal > 指定要从中撤消权限的主体。  
  
 GRANT OPTION  
 指示要撤消向其他主体授予指定权限的权限。 不会撤消该权限本身。  
  
> [!IMPORTANT]  
>  如果主体具有不带 GRANT 选项的指定权限，则将撤消该权限本身。  
  
 CASCADE  
 指示要撤消的权限也会从此主体授予或拒绝该权限的其他主体中撤消。  
  
> [!CAUTION]  
>  如果对授予了 WITH GRANT OPTION 权限的权限执行级联撤消，将同时撤消该权限的 GRANT 和 DENY 权限。  
  
 AS \<database_principal > 指定的主体执行此查询的主体从中派生其权限以撤消的权限。  
  
 *Database_user*  
 指定数据库用户。  
  
 *Database_role*  
 指定数据库角色。  
  
 *Application_role*  
**适用于**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]通过[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]，[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]
  
 指定应用程序角色。  
  
 *Database_user_mapped_to_Windows_User*  
**适用于**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]通过[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 指定映射到 Windows 用户的数据库用户。  
  
 *Database_user_mapped_to_Windows_Group*  
**适用于**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]通过[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 指定映射到 Windows 组的数据库用户。  
  
 *Database_user_mapped_to_certificate*  
**适用于**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]通过[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 指定映射到证书的数据库用户。  
  
 *Database_user_mapped_to_asymmetric_key*  
**适用于**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]通过[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 指定映射到非对称密钥的数据库用户。  
  
 *Database_user_with_no_login*  
 指定无相应服务器级主体的数据库用户。  
  
## <a name="remarks"></a>注释  
 类型是架构级的安全对象，包含于权限层次结构中作为其父级的架构中。  
  
> [!IMPORTANT]  
>  **授予**， **DENY**和**撤消**权限不适用于系统类型。 可以为用户定义类型授予权限。 有关用户定义类型的详细信息，请参阅[使用 SQL Server 中的用户定义类型](../../relational-databases/clr-integration-database-objects-user-defined-types/working-with-user-defined-types-in-sql-server.md)。  
  
 下表列出了可撤消的对类型最为具体的限定权限，以及隐含这些权限的更为通用的权限。  
  
|类型权限|类型权限隐含的权限|架构权限隐含的权限|  
|---------------------|--------------------------------|----------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|在运行 CREATE 语句前执行|CONTROL|在运行 CREATE 语句前执行|  
|REFERENCES|CONTROL|REFERENCES|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 需要对类型的 CONTROL 权限。 如果使用 AS 子句，则指定的主体必须拥有类型。  
  
## <a name="examples"></a>示例  
 以下示例从用户 `VIEW DEFINITION` 中撤消对用户定义类型 `PhoneNumber` 的 `KhalidR` 权限。 `CASCADE` 选项指示 `VIEW DEFINITION` 权限也会从 `KhalidR` 授予该权限的主体中撤消。 `PhoneNumber` 位于架构 `Telemarketing` 中。  
  
```  
REVOKE VIEW DEFINITION ON TYPE::Telemarketing.PhoneNumber   
    FROM KhalidR CASCADE;  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [GRANT 类型权限 &#40;Transact SQL &#41;](../../t-sql/statements/grant-type-permissions-transact-sql.md)   
 [DENY 类型权限 &#40;Transact SQL &#41;](../../t-sql/statements/deny-type-permissions-transact-sql.md)   
 [CREATE TYPE (Transact-SQL)](../../t-sql/statements/create-type-transact-sql.md)   
 [权限（数据库引擎）](../../relational-databases/security/permissions-database-engine.md)   
 [主体（数据库引擎）](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [安全对象](../../relational-databases/security/securables.md)  
  
  

