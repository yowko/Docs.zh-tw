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
ms.openlocfilehash: 7ebc86ad9c1f84156e7e228c1ddf3fe7b86b7e60
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576261"
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
 [in]指標[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)可識別要合併之匯入的範圍的物件。  
  
 `pIMap`  
 [in]指標[IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)指定語彙基元重新對應的物件。  
  
 `pHandleer`  
 [in]指標[IUnknown](/cpp/atl/iunknown)指定錯誤的物件。  
  
## <a name="remarks"></a>備註  
 呼叫[imetadataemit:: Mergeend](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md)觸發的中繼資料合併成單一範圍。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：** 做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
