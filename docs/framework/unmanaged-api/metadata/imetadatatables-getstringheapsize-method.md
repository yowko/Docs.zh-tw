---
title: "IMetaDataTables::GetStringHeapSize 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetStringHeapSize
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetStringHeapSize
helpviewer_keywords:
- IMetaDataTables::GetStringHeapSize method [.NET Framework metadata]
- GetStringHeapSize method [.NET Framework metadata]
ms.assetid: ed8f6335-81f5-4c09-81a9-2a909fc530c9
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a0e664192ac39dd12085346738dbc283a11d3381
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgetstringheapsize-method"></a>IMetaDataTables::GetStringHeapSize 方法
取得大小，單位為位元組字串堆積。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetStringHeapSize (  
    [out] ULONG   *pcbStrings  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pcbStrings`  
 [out]大小，單位為位元組字串堆積的指標。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataTables 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [IMetaDataTables2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
