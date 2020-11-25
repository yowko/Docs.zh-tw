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
ms.openlocfilehash: e64d644b511f7c3249c48b9642bfd3163142af3c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722007"
---
# <a name="imetadataemitmerge-method"></a>IMetaDataEmit::Merge 方法

將指定的匯入範圍加入要合併的範圍清單。  
  
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
 在 [IMetaDataImport](imetadataimport-interface.md) 物件的指標，該物件會識別要合併的匯入範圍。  
  
 `pIMap`  
 在 [IMapToken](imaptoken-interface.md) 物件的指標，該物件會指定重新對應的標記。  
  
 `pHandler`  
 在指定錯誤之 [IUnknown](/cpp/atl/iunknown) 物件的指標。  
  
## <a name="remarks"></a>備註  

 呼叫 [IMetaDataEmit：： MergeEnd](imetadataemit-mergeend-method.md) ，以觸發將中繼資料合併到單一範圍中。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MSCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](imetadataemit-interface.md)
- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
