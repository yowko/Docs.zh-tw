---
title: IMetaDataEmit::Merge 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Merge
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Merge
helpviewer_keywords:
- IMetaDataEmit::Merge method [.NET Framework metadata]
- Merge method [.NET Framework metadata]
ms.assetid: 7596220c-f699-4b6c-8ae7-c83220610650
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98997bfbb7d3c9343f78438b1195222565c5b9ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitmerge-method"></a>IMetaDataEmit::Merge 方法
將指定的匯入的範圍加入至要合併的範圍清單。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Merge (   
    [in]  IMetaDataImport  *pImport,   
    [in]  IMapToken        *pHostMapToken,   
    [in]  IUnknown         *pHandler   
);  
```  
  
#### <a name="parameters"></a>參數  
 `pImport`  
 [in]指標[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)物件，可識別要合併的匯入的範圍。  
  
 `pIMap`  
 [in]指標[IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)指定語彙基元重新對應的物件。  
  
 `pHandleer`  
 [in]指標<!--<<!--zzxref:IUnknown --> `IUnknown` >-->  `IUnknown`物件，指定的錯誤。  
  
## <a name="remarks"></a>備註  
 呼叫[imetadataemit:: Mergeend](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md)觸發在中繼資料的合併成單一範圍。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
