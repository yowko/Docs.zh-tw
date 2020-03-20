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
ms.openlocfilehash: 759358822ed865c89f6f55084d1e7f6143506e93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175703"
---
# <a name="imetadataemitmerge-method"></a>IMetaDataEmit::Merge 方法
將指定的導入作用域添加到要合併的範圍清單中。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Merge (
    [in]  IMetaDataImport  *pImport,
    [in]  IMapToken        *pHostMapToken,
    [in]  IUnknown         *pHandler
);  
```  
  
## <a name="parameters"></a>參數  
 `pImport`  
 [在]指向[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)物件的指標，用於標識要合併的導入作用域。  
  
 `pIMap`  
 [在]指向[IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)物件的指標，用於指定權杖重新映射。  
  
 `pHandler`  
 [在]指向指定錯誤的[IUnknown](/cpp/atl/iunknown)物件的指標。  
  
## <a name="remarks"></a>備註  
 調用[IMetaDataEmit：：合併結束](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md)以觸發將中繼資料合併到單個作用域中。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MSCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
