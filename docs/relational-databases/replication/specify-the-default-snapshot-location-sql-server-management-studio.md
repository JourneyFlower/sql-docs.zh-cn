---
title: 指定默认快照位置 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], default locations
- default snapshot locations
ms.assetid: 27c5d9ad-a915-4c59-a8b7-82e3af61ac4d
caps.latest.revision: 38
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0debb4f21922bdf9d54fb5a3920249ae3c6aada3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="specify-the-default-snapshot-location-sql-server-management-studio"></a>指定默认快照位置 (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  可以在配置分发向导的 **“快照文件夹”** 页上指定默认快照位置。 有关使用此向导的详细信息，请参阅[配置发布和分发](../../relational-databases/replication/configure-publishing-and-distribution.md)。 如果在未配置为分发服务器的服务器上创建发布，请在新建发布向导的 **“快照文件夹”** 页上指定默认快照位置。 有关使用此向导的详细信息，请参阅[创建发布](../../relational-databases/replication/publish/create-a-publication.md)。  
  
 在“分发服务器属性 - \<分发服务器>”对话框的“发布服务器”页上，修改默认快照位置。 有关详细信息，请参阅[查看和修改分发服务器和发布服务器属性](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)。 在“发布属性 - \<发布>”对话框中设置每个发布的快照文件夹。 有关详细信息，请参阅 [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)。  
  
### <a name="to-modify-the-default-snapshot-location"></a>修改默认快照位置  
  
1.  在“分发服务器属性 - \<分发服务器>”对话框的“发布服务器”页上，单击要更改其默认快照位置的发布服务器的属性按钮 (**…**)。  
  
2.  在“分发服务器属性 - \<分发服务器>”对话框中，为“默认快照文件夹”属性输入一个值。  
  
    > [!NOTE]  
    >  快照代理必须对指定的目录具有写权限，而分发代理或合并代理必须具有读权限。 如果使用的是请求订阅，则必须指定一个共享目录作为通用命名约定 (UNC) 路径，如 \\\computername\snapshot。 有关详细信息，请参阅[保护快照文件夹](../../relational-databases/replication/security/secure-the-snapshot-folder.md)。  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [备用快照文件夹位置](../../relational-databases/replication/alternate-snapshot-folder-locations.md)   
 [使用快照初始化订阅](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  
