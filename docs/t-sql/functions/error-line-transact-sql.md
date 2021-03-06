---
title: ERROR_LINE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ERROR_LINE
- ERROR_LINE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- errors [SQL Server], line number
- messages [SQL Server], line number
- TRY...CATCH [SQL Server]
- line number of error [SQL Server]
- ERROR_LINE function
- CATCH block
ms.assetid: 47335734-0baf-45a6-8b3b-6c4fd80d2cb8
caps.latest.revision: 39
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 44745c0f27527872abd1b63c3fa5b3954328c1be
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="errorline-transact-sql"></a>ERROR_LINE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  返回发生错误的行号，该错误导致运行 TRY…CATCH 构造的 CATCH 块。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
ERROR_LINE ( )  
```  
  
## <a name="return-type"></a>返回类型  
 **int**  
  
## <a name="return-value"></a>返回值  
 当在 CATCH 块中调用时：  
  
-   返回出现错误的行号。  
  
-   如果错误发生在存储过程或触发器中，则返回例程中的行号。  
  
 如果在 CATCH 块作用域以外调用，则返回 NULL。  
  
## <a name="remarks"></a>Remarks  
 可以在 CATCH 块的作用域内的任何位置调用此函数。  
  
 ERROR_LINE 返回发生错误的行号，而不考虑它被调用的次数或在 CATCH 块的作用域内被调用的位置。 它与 @@ERROR 之类的函数不同，后者会在导致错误的语句之后的语句中立即返回错误号，或在 CATCH 块的第一个语句中返回错误号。  
  
 在嵌套 CATCH 块中，ERROR_LINE 返回特定于引用它的 CATCH 块作用域的错误行号。 例如，TRY…CATCH 构造的 CATCH 块可以包含一个嵌套 TRY…CATCH 构造。 在嵌套 CATCH 块中，ERROR_LINE 返回调用嵌套 CATCH 块的错误的行号。 如果 ERROR_LINE 在 CATCH 块以外运行，则会返回调用该 CATCH 块的错误的行号。  
  
## <a name="examples"></a>示例  
  
### <a name="a-using-errorline-in-a-catch-block"></a>A. 在 CATCH 块中使用 ERROR_LINE  
 下面的代码示例显示生成被零除错误的 `SELECT` 语句。 返回发生错误的行号。  
  
```  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_LINE() AS ErrorLine;  
END CATCH;  
GO  
```  
  
### <a name="b-using-errorline-in-a-catch-block-with-a-stored-procedure"></a>B. 带存储过程在 CATCH 块中使用 ERROR_LINE  
 下面的代码示例演示一个生成被零除错误的存储过程。 `ERROR_LINE` 返回发生错误的存储过程中的行号。  
  
```  
-- Verify that the stored procedure does not already exist.  
IF OBJECT_ID ( 'usp_ExampleProc', 'P' ) IS NOT NULL   
    DROP PROCEDURE usp_ExampleProc;  
GO  
  
-- Create a stored procedure that   
-- generates a divide-by-zero error.  
CREATE PROCEDURE usp_ExampleProc  
AS  
    SELECT 1/0;  
GO  
  
BEGIN TRY  
    -- Execute the stored procedure inside the TRY block.  
    EXECUTE usp_ExampleProc;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_LINE() AS ErrorLine;  
END CATCH;  
GO  
```  
  
### <a name="c-using-errorline-in-a-catch-block-with-other-error-handling-tools"></a>C. 带其他错误处理工具在 CATCH 块中使用 ERROR_LINE  
 下面的代码示例显示生成被零除错误的 `SELECT` 语句。 错误的相关信息与发生错误的行号一同返回。  
  
```  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT  
        ERROR_NUMBER() AS ErrorNumber,  
        ERROR_SEVERITY() AS ErrorSeverity,  
        ERROR_STATE() AS ErrorState,  
        ERROR_PROCEDURE() AS ErrorProcedure,  
        ERROR_LINE() AS ErrorLine,  
        ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [TRY...CATCH (Transact-SQL)](../../t-sql/language-elements/try-catch-transact-sql.md)   
 [sys.messages (Transact-SQL)](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)   
 [ERROR_NUMBER (Transact-SQL)](../../t-sql/functions/error-number-transact-sql.md)   
 [ERROR_MESSAGE (Transact-SQL)](../../t-sql/functions/error-message-transact-sql.md)   
 [ERROR_PROCEDURE (Transact-SQL)](../../t-sql/functions/error-procedure-transact-sql.md)   
 [ERROR_SEVERITY (Transact-SQL)](../../t-sql/functions/error-severity-transact-sql.md)   
 [ERROR_STATE (Transact-SQL&)](../../t-sql/functions/error-state-transact-sql.md)   
 [RAISERROR (Transact-SQL)](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [@@ERROR (Transact-SQL)](../../t-sql/functions/error-transact-sql.md)  
  
  
