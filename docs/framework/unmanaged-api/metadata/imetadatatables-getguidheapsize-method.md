---
title: IMetaDataTables::GetGuidHeapSize 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuidHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuidHeapSize
helpviewer_keywords:
- GetGuidHeapSize method [.NET Framework metadata]
- IMetaDataTables::GetGuidHeapSize method [.NET Framework metadata]
ms.assetid: e875cbee-1ad9-4f1a-bf03-38cdb8ff371a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 97d196769b549022ce498958fc34cf08df442d0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="imetadatatablesgetguidheapsize-method"></a>IMetaDataTables::GetGuidHeapSize 方法
取得以位元組為單位 GUID 堆積的大小。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetGuidHeapSize (  
    [out] ULONG   *pcbGuids  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pcbGuids`  
 [out]大小，以位元組為單位 GUID 堆積的指標。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataTables 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [IMetaDataTables2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
