---
title: 删除 PowerPivotSystemServiceInstance cmdlet |Microsoft 文档
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: powershell
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c4f6feb69b3375b5ed5d0d69407ef5a033991f96
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2018
---
# <a name="remove-powerpivotsystemserviceinstance-cmdlet"></a>Remove-PowerPivotSystemServiceInstance cmdlet
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  从场中删除 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 系统服务实例。  

>[!NOTE] 
>这篇文章可能包含过期的信息和示例。 有关最新的使用 Get-help cmdlet。
  
 **适用范围：** SharePoint 2010 和 SharePoint 2013。  
  
## <a name="syntax"></a>语法  
  
```  
Remove-PowerPivotSystemServiceInstance [-Confirm <switch>] [-DeleteLocal <switch>] [-Identity <PowerPivotMidTierServiceInstancePipeBind>] [<CommonParameters>]  
```  
  
## <a name="description"></a>Description  
 Remove-PowerPivotSystemServiceInstance cmdlet 从场中删除与 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 系统服务有关的实例信息。 它不会删除程序文件。 若要永久删除程序文件，您必须卸载它们。  
  
 如果删除 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 系统服务，请确保还运行 Remove-PowerPivotEngineServiceInstance 以便删除关联的 Analysis Services 实例，之后使用 Remove-PowerPivotServiceApplication 删除所有 PowerPivot 服务应用程序。 在这些服务都被删除后，服务应用程序将不再运行。  
  
 若要还原此更改，可以运行 New-PowerPivotSystemServiceInstance -Provision:$true 以便重新启用实例信息。  
  
## <a name="parameters"></a>Parameters  
  
### <a name="-identity-powerpivotmidtierserviceinstancepipebind"></a>标识\<PowerPivotMidTierServiceInstancePipeBind >  
 指定要删除的 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 系统服务实例的 GUID。 在安装有 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint 的每个应用程序服务器上只有一个服务实例。  
  
|||  
|-|-|  
|必需？|false|  
|位置？|0|  
|默认值||  
|接受管道输入？|true|  
|接受通配符？|false|  
  
### <a name="-deletelocal-switch"></a>-DeleteLocal\<切换 >  
 删除在本地计算机上安装的 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 系统服务实例，并且允许你不必指定对象标识即删除实例。  
  
|||  
|-|-|  
|必需？|false|  
|位置？|所指定位置|  
|默认值||  
|接受管道输入？|false|  
|接受通配符？|false|  
  
### <a name="-confirm-switch"></a>确认\<切换 >  
 在执行命令前提示您进行确认。 默认情况下将启用该值。 若要在命令中跳过确认响应，请在命令中指定 Confirm:$false。  
  
|||  
|-|-|  
|必需？|false|  
|位置？|所指定位置|  
|默认值||  
|接受管道输入？|false|  
|接受通配符？|false|  
  
### <a name="commonparameters"></a>\<CommonParameters >  
 此 cmdlet 支持以下常用参数：Verbose、Debug、ErrorAction、ErrorVariable、WarningAction、WarningVariable、OutBuffer 和 OutVariable。 有关详细信息，请参阅 [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825)。  
  
## <a name="inputs-and-outputs"></a>输入和输出  
 输入类型是可以传送到 cmdlet 的对象的类型。 返回类型是 cmdlet 所返回的对象的类型。  
  
|||  
|-|-|  
|输入|无。|  
|输出|无。|  
  
## <a name="example-1"></a>示例 1  
  
```  
C:\PS>Remove-PowerPivotSystemServiceInstance -deletelocal  
```  
  
 此示例演示如何删除在本地应用程序服务器上运行的 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 系统服务实例。  
  
## <a name="example-2"></a>示例 2  
  
```  
C:\PS>Remove-PowerPivotSystemServiceInstance -identity 1234567-890a-bcde-fghijklmn  
```  
  
 此示例演示如何基于其标识删除特定的 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 系统服务。  
  
  
