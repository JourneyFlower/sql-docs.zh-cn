---
title: GetDataProviderDSO 方法 |Microsoft 文档
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- GetDataProviderDSO Method [ADO]
ms.assetid: 5a4c6bd5-0c79-4f81-a977-0561392d8d50
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 687ba2301edfbd944bc9feafdbce2c528b26b58c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="getdataproviderdso-method"></a>GetDataProviderDSO 方法
从 Shape 提供程序检索基础的 OLE DB 数据源对象。  
  
## <a name="syntax"></a>语法  
  
```  
  
HRESULT GetDataProviderDSO(  
      IUnknown **ppDataProviderDSOIUnknown  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 *ppDataProviderDSOIUnknown*  
 [out] 指向返回基础的 OLE DB 数据源对象的 IUnknown 的指针的指针。  
  
## <a name="remarks"></a>注释  
 此方法执行不 addref 接口指针。 如果调用方计划以容纳指针，调用方必须执行所需的 addref 和发布。  
  
## <a name="applies-to"></a>适用于  
 [IDSOShapeExtensions 接口](../../../ado/reference/ado-api/idsoshapeextensions-interface.md)
