---
title: "sp_syspolicy_delete_policy_category_subscription (Transact SQL) |Microsoft 文档"
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
- sp_syspolicy_delete_policy_category_subscription_TSQL
- sp_syspolicy_delete_policy_category_subscription
dev_langs: TSQL
helpviewer_keywords: sp_syspolicy_delete_policy_category_subscription
ms.assetid: eeab0120-c869-4c95-a79d-6dc418d0b23a
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 79b610cf653f58b89f461f65049fcbdf66cbbb97
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/27/2017
---
# <a name="spsyspolicydeletepolicycategorysubscription-transact-sql"></a>sp_syspolicy_delete_policy_category_subscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  删除特定数据库的策略类别订阅。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_syspolicy_delete_policy_category_subscription [ @policy_category_subscription_id = ] policy_category_subscription_id  
```  
  
## <a name="arguments"></a>参数  
 [  **@policy_category_subscription_id=** ] *policy_category_subscription_id*  
 策略类别订阅的标识符。 *policy_category_subscription_id*是**int**。  
  
## <a name="return-code-values"></a>返回代码值  
 **0** （成功） 或**1** （失败）  
  
## <a name="remarks"></a>注释  
 您必须在 msdb 系统数据库的上下文中运行 sp_syspolicy_delete_policy_category_subscription。  
  
 如果某一策略类别订阅被托管，则不能删除该订阅。  
  
## <a name="permissions"></a>Permissions  
 此存储过程在其当前所有者的上下文中运行。  
  
 若要获取的值*policy_category_subscription_id*，你可以使用以下查询：  
  
```  
SELECT a.policy_category_subscription_id, a.target_object, b.name AS category_name  
FROM msdb.dbo.syspolicy_policy_category_subscriptions AS a  
INNER JOIN msdb.dbo.syspolicy_policy_categories AS b  
ON a.policy_category_id = b.policy_category_id;  
```  
  
## <a name="examples"></a>示例  
 下面的示例将删除 ID 为 1 的策略类别订阅。  
  
```  
EXEC msdb.dbo.sp_syspolicy_delete_policy_category_subscription @policy_category_subscription_id = 1;  
  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [基于策略的管理存储过程 &#40;Transact SQL &#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [sp_syspolicy_update_policy_category_subscription &#40;Transact SQL &#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-update-policy-category-subscription-transact-sql.md)  
  
  