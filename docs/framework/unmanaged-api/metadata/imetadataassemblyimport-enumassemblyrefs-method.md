---
title: IMetaDataAssemblyImport::EnumAssemblyRefs 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumAssemblyRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs method [.NET Framework metadata]
- EnumAssemblyRefs method [.NET Framework metadata]
ms.assetid: 8844d0dd-730e-4592-8a7b-c1462d312c70
topic_type:
- apiref
ms.openlocfilehash: 06b81615565a04db7d6cfef4da9b5372a85afd68
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450341"
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a>IMetaDataAssemblyImport::EnumAssemblyRefs 方法
列舉在組件資訊清單中定義的 `mdAssemblyRef` 實例。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,   
    [out]     mdAssemblyRef   rAssemblyRefs[],   
    [in]      ULONG           cMax,   
    [out]     ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a>參數  
 `phEnum`  
 [in、out]列舉值的指標。 第一次呼叫 `EnumAssemblyRefs` 方法時，這必須是 null 值。  
  
 `rAssemblyRefs`  
 脫銷`mdAssemblyRef` 元資料標記的列舉。  
  
 `cMax`  
 在可以放在 `rAssemblyRefs` 陣列中的標記數目上限。  
  
 `pcTokens`  
 脫銷實際放在 `rAssemblyRefs`中的權杖數目。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|已成功傳回 `EnumAssemblyRefs`。|  
|`S_FALSE`|沒有要列舉的權杖。 在此情況下，`pcTokens` 會設定為零。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
