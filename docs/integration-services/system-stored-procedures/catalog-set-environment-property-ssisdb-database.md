---
title: "catalog.set_environment_property （SSISDB 数据库） |Microsoft 文档"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: a345675b-d32e-4624-96cf-ec656730b114
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 8eedfe6919a69759cc6de3645b3e1f965dcdd0c6
ms.contentlocale: zh-cn
ms.lasthandoff: 09/26/2017

---
# <a name="catalogsetenvironmentproperty-ssisdb-database"></a>catalog.set_environment_property（SSISDB 数据库）
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 目录中设置环境的属性。  
  
## <a name="syntax"></a>语法  
  
```tsql  
set_environment_property [ @folder_name = ] folder_name  
    , [ @environment_name = ] environment_name  
    , [ @property_name = ] property_name  
    , [ @property_value = ] property_value  
```  
  
## <a name="arguments"></a>参数  
 [ @folder_name =] *folder_name*  
 包含环境的文件夹的名称。 *Folder_name*是**nvarchar （128)**。  
  
 [ @environment_name =] *environment_name*  
 环境的名称。 *Environment_name*是**nvarchar （128)**。  
  
 [ @property_name =] *property_name*  
 环境属性的名称。 *Property_name*是**nvarchar （128)**。  
  
 [ @property_value =] *property_value*  
 环境属性的值。 *Property_value*是**nvarchar(1024)**。  
  
## <a name="return-code-value"></a>返回代码值  
 0（成功）  
  
## <a name="result-sets"></a>结果集  
 无  
  
## <a name="permissions"></a>Permissions  
 此存储过程需要下列权限之一：  
  
-   针对环境的 READ 和 MODIFY 权限  
  
-   成员资格**ssis_admin**数据库角色  
  
-   成员资格**sysadmin**服务器角色  
  
## <a name="errors-and-warnings"></a>错误和警告  
 下面的列表描述了一些可能引发错误或警告的情况：  
  
-   文件夹名称无效  
  
-   属性名称无效  
  
-   环境名称无效  
  
## <a name="remarks"></a>注释  
 在这一版本中，仅可设置 `Description` 属性。 `Description` 属性的属性值不能超过 4000 个字符。  
  
  