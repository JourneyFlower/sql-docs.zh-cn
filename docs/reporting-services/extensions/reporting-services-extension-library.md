---
title: Reporting Services 扩展插件库 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: extensions
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- namespaces [Reporting Services]
- Reporting Services, extending
- extensions [Reporting Services], library
- library [Reporting Services]
ms.assetid: e8eff470-64d6-41c3-b98b-5ec916c121c3
caps.latest.revision: 33
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: ac3318a455259b8471dbe2f8e1912d352cc1eacc
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="reporting-services-extension-library"></a>Reporting Services 扩展插件库
  Reporting Services 扩展插件库是 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中包含的一系列类、接口和值类型。 该库提供对系统功能的访问，它是可以使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 应用程序来扩展 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 组件的基础。  
  
## <a name="namespaces"></a>命名空间  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 扩展插件库提供以下命名空间。  
  
 <xref:Microsoft.ReportingServices.DataProcessing>  
 包含的类和接口使您能够生成用于扩展 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的数据处理功能的组件。  
  
 <xref:Microsoft.ReportingServices.Interfaces>  
 包含的类和接口使您能够通过您自己的传递扩展插件构造和向用户发送自定义通知，并且使您能够为 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 生成自定义安全扩展插件。  
  
 **Microsoft.ReportingServices.ReportRendering**  
 包含的类和接口使您能够扩展 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的呈现功能。 将此命名空间的成员与 <xref:Microsoft.ReportingServices.Interfaces> 命名空间的成员一起使用，您可以为 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 生成您自己的自定义呈现扩展插件。  
  
## <a name="see-also"></a>另请参阅  
 [Reporting Services 扩展插件](../../reporting-services/extensions/reporting-services-extensions.md)  
  
  
