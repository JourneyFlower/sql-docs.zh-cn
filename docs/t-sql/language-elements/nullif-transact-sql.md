---
title: "NULLIF (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 09/08/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- NULLIF
- NULLIF_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- null values [SQL Server], equivalent expressions
- expressions [SQL Server], null values
- NULLIF function
- equivalent expressions [SQL Server]
ms.assetid: 44c7b67e-74c7-4bb9-93a4-7a3016bd2feb
caps.latest.revision: 48
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fe8e4663688ce510d9600ebeba9d3c30703ee3aa
ms.contentlocale: zh-cn
ms.lasthandoff: 09/09/2017

---
# <a name="nullif-transact-sql"></a>NULLIF (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  如果两个指定的表达式相等，则返回空值。 例如， `SELECT NULLIF(4,4) AS Same, NULLIF(5,7) AS Different;` （4 和 4） 的第一列返回 NULL，因为两个输入的值都是相同。 因为两个输入的值不同，第二列将返回第一个值 (5)。 
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
NULLIF ( expression , expression )  
```  
  
## <a name="arguments"></a>参数  
 *expression*  
 是任何有效的标量[表达式](../../t-sql/language-elements/expressions-transact-sql.md)。  
  
## <a name="return-types"></a>返回类型  
 返回相同的类型与第一个*表达式*。  
  
 NULLIF 返回第一个*表达式*如果两个表达式是否不相等。 如果表达式相等，则 NULLIF 返回的第一个类型的 null 值*表达式*。  
  
## <a name="remarks"></a>注释  
 如果两个表达式相等且结果表达式为 NULL，则 NULLIF 等价于 CASE 搜索表达式。  
  
 我们建议在 NULLIF 函数内不要使用依赖于时间的函数，如 RAND()。 这可能会导致函数两次计算，并从两个调用返回不同的结果。  
  
## <a name="examples"></a>示例  
  
### <a name="a-returning-budget-amounts-that-have-not-changed"></a>A. 返回尚未更改的预算数量  
 以下示例创建 `budgets` 表以显示部门 (`dept`) 的当年预算 (`current_year`) 以及上一年预算 (`previous_year`)。 对于当年预算，那些同上一年相比预算没有改变的部门使用 `NULL`，那些预算还没有确定的部门使用 `0`。 若要只计算那些接收预算的部门的预算平均值，并包含上一年的预算值（`previous_year` 为 `current_year` 时，使用 `NULL` 的值），请组合使用 `NULLIF` 和 `COALESCE` 函数。  
  
```sql  
CREATE TABLE dbo.budgets  
(  
   dept            tinyint   IDENTITY,  
   current_year      decimal   NULL,  
   previous_year   decimal   NULL  
);  
INSERT budgets VALUES(100000, 150000);  
INSERT budgets VALUES(NULL, 300000);  
INSERT budgets VALUES(0, 100000);  
INSERT budgets VALUES(NULL, 150000);  
INSERT budgets VALUES(300000, 250000);  
GO    
SET NOCOUNT OFF;  
SELECT AVG(NULLIF(COALESCE(current_year,  
   previous_year), 0.00)) AS 'Average Budget'  
FROM budgets;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 Average Budget  
 --------------  
 212500.000000  
 (1 row(s) affected)
 ```  
  
### <a name="b-comparing-nullif-and-case"></a>B. 比较 NULLIF 和 CASE  
 若要显示 `NULLIF` 和 `CASE` 之间的相似性，则以下查询将计算 `MakeFlag` 和 `FinishedGoodsFlag` 列中的值是否相同。 第一个查询使用 `NULLIF`。 第二个查询使用 `CASE` 表达式。  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT ProductID, MakeFlag, FinishedGoodsFlag,   
   NULLIF(MakeFlag,FinishedGoodsFlag)AS 'Null if Equal'  
FROM Production.Product  
WHERE ProductID < 10;  
GO  
  
SELECT ProductID, MakeFlag, FinishedGoodsFlag,'Null if Equal' =  
   CASE  
       WHEN MakeFlag = FinishedGoodsFlag THEN NULL  
       ELSE MakeFlag  
   END  
FROM Production.Product  
WHERE ProductID < 10;  
GO  
```  

### <a name="c-returning-budget-amounts-that-contain-no-data"></a>C： 返回不包含数据的预算金额  
 下面的示例创建`budgets`表，将加载数据，并使用`NULLIF`返回 null，如果既没有`current_year`也不`previous_year`包含数据。  
  
```sql  
CREATE TABLE budgets (  
   dept           tinyint,  
   current_year   decimal(10,2),  
   previous_year  decimal(10,2)  
);  
  
INSERT INTO budgets VALUES(1, 100000, 150000);  
INSERT INTO budgets VALUES(2, NULL, 300000);  
INSERT INTO budgets VALUES(3, 0, 100000);  
INSERT INTO budgets VALUES(4, NULL, 150000);  
INSERT INTO budgets VALUES(5, 300000, 300000);  
  
SELECT dept, NULLIF(current_year,  
   previous_year) AS LastBudget  
FROM budgets;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 dept   LastBudget  
 ----   -----------  
 1      100000.00  
 2      null 
 3      0.00  
 4      null  
 5      null
 ```  
  
## <a name="see-also"></a>另请参阅  
 [用例 &#40;Transact SQL &#41;](../../t-sql/language-elements/case-transact-sql.md)   
 [小数和数值 &#40;Transact SQL &#41;](../../t-sql/data-types/decimal-and-numeric-transact-sql.md)   
 [系统函数 &#40;Transact SQL &#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
  
  

