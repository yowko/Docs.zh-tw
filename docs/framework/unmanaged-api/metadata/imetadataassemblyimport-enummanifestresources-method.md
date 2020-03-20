---
title: IMetaDataAssemblyImport::EnumManifestResources 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumManifestResources
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumManifestResources
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumManifestResources method [.NET Framework metadata]
- EnumManifestResources method [.NET Framework metadata]
ms.assetid: 9543b111-5705-40c9-935c-a3ffc7a581aa
topic_type:
- apiref
ms.openlocfilehash: 22141cf46a965c0624c076bd1d86d2624e5a09f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176015"
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a>IMetaDataAssemblyImport::EnumManifestResources 方法
獲取當前組件資訊清單中引用的資源的指向枚舉器的指標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,
    [out] mdManifestResource   rManifestResources[],
    [in]  ULONG                cMax,
    [out] ULONG                *pcTokens  
);
```  
  
## <a name="parameters"></a>參數  
 `phEnum`  
 [進出]指向枚舉器的指標。 當首次調用該方法時，`EnumManifestResources`這必須是 null 值。  
  
 `rManifestResources`  
 [出]用於存儲中繼資料權杖的`mdManifestResource`陣列。  
  
 `cMax`  
 [在]可放置在 中`mdManifestResource`的最大權杖數`rManifestResources`。  
  
 `pcTokens`  
 [出]實際放置在`mdManifestResource`中的`rManifestResources`權杖數。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|`EnumManifestResources`已成功返回。|  
|`S_FALSE`|沒有要枚舉的權杖。 在這種情況下，`pcTokens`設置為零。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MsCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
