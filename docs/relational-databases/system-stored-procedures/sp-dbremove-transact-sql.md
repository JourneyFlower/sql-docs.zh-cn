---
title: "sp_dbremove (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_dbremove
- sp_dbremove_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_dbremove
ms.assetid: a8513f4a-c025-49c8-99c3-4c83cb7f51ed
caps.latest.revision: "32"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5df6704da740e610385494ce488e222bab0e4ccf
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/27/2017
---
# <a name="spdbremove-transact-sql"></a>sp_dbremove (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  删除数据库及其所有相关文件。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]我们建议你使用[DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md)相反。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_dbremove [ @dbname = ] 'database' [ , [ @dropdev = ] 'dropdev' ]   
```  
  
## <a name="arguments"></a>参数  
 [  **@dbname=** ] *数据库*  
 要删除的数据库的名称。 *数据库*是**sysname**，默认值为 NULL。  
  
 [  **@dropdev=** ] *dropdev*  
 提供该标志只是为了向后兼容，当前忽略此标志。 *dropdev*具有值**dropdev**。  
  
## <a name="return-code-values"></a>返回代码值  
 0（成功）或 1（失败）  
  
## <a name="result-sets"></a>结果集  
 无  
  
## <a name="permissions"></a>Permissions  
 要求具有 **sysadmin** 固定服务器角色的成员身份。  
  
## <a name="examples"></a>示例  
 以下示例将删除名为 `sales` 的数据库及其相关的所有文件。  
  
```  
EXEC sp_dbremove sales;  
```  
  
## <a name="see-also"></a>另请参阅  
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [DBCC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-transact-sql.md)   
 [sp_detach_db (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md)  
  
  