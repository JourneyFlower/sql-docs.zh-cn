---
title: 创建带有参数的钻取 (RDLC) 报表 - ReportViewer | Microsoft Docs
ms.custom: ''
ms.date: 05/18/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: reporting-services
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: 628c8775-c62d-45ac-b349-23db86fa4e6c
caps.latest.revision: 8
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: f90ac792fe849ca91735e5a9b22a399d7798cf23
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="create-drillthrough-rdlc-report-with-parameters---reportviewer"></a>创建带有参数的钻取 (RDLC) 报表 - ReportViewer
[钻取](http://technet.microsoft.com/library/ff519554.aspx) 报表是指用户通过单击其他报表中的链接打开的报表。 钻取报表通常包含某原始汇总报表中所包含的某项的详细信息。 本教程将带你演练以下在 [本地模式报表](http://msdn.microsoft.com/library/ff487969.aspx)中使用参数和查询创建钻取报表的课程。  
  
## <a name="requirements"></a>要求  
若要使用此演练，必须具有访问 **AdventureWorks2014** 示例数据库的权限。 有关如何获取 AdventureWorks2014 示例数据库的详细信息，请参阅 [AdventureWorks sample databases](https://github.com/Microsoft/sql-server-samples/releases)（AdventureWorks 示例数据库）。  
  
此演练假定你熟悉 Transaction-SQL 查询和 ADO.NET [DataSet](https://msdn.microsoft.com/library/system.data.dataset.aspx) 和 [DataTable](http://msdn.microsoft.com/library/system.data.datatable.aspx) 对象。  
  
使用 Visual Studio 2015 和 ASP.NET Web 应用程序创建具有 ReportViewer 控件的 ASP.NET 网页。 该控件被配置为查看您创建的报表。 对于本演练，您在 Microsoft Visual C# 中创建应用程序。  
  
## <a name="tasks"></a>“任务”  
[第 1 课：创建新网站](../reporting-services/lesson-1-create-a-new-web-site.md)  
[第 2 课：定义用于父报表的数据连接和数据表](../reporting-services/lesson-2-define-a-data-connection-and-data-table-for-parent-report.md)  
[第 3 课：使用报表向导设计父报表](../reporting-services/lesson-3-design-the-parent-report-using-the-report-wizard.md)  
[第 4 课：定义用于子报表的数据连接和数据表](../reporting-services/lesson-4-define-a-data-connection-and-data-table-for-child-report.md)  
[第 5 课：使用报表向导设计子报表](../reporting-services/lesson-5-design-the-child-report-using-the-report-wizard.md)  
[第 6 课：将 ReportViewer 控件添加到应用程序](../reporting-services/lesson-6-add-a-reportviewer-control-to-the-application.md)  
[第 7 课：在父报表上添加钻取操作](../reporting-services/lesson-7-add-drillthrough-action-on-parent-report.md)  
[第 8 课：创建数据筛选器](../reporting-services/lesson-8-create-a-data-filter.md)  
[Lesson 9: Build and Run the Application](../reporting-services/lesson-9-build-and-run-the-application.md)  
  
## <a name="see-also"></a>另请参阅  
[Reporting Services 教程 (SSRS)](../reporting-services/reporting-services-tutorials-ssrs.md)  
[使用报表设计器设计报表 (SSRS)](../reporting-services/tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  

