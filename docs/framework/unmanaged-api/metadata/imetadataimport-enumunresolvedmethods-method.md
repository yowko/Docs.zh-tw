---
title: IMetaDataImport::EnumUnresolvedMethods 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumUnresolvedMethods
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumUnresolvedMethods
helpviewer_keywords:
- EnumUnresolvedMethods method [.NET Framework metadata]
- IMetaDataImport::EnumUnresolvedMethods method [.NET Framework metadata]
ms.assetid: eb3187d7-74cf-44b1-aeeb-7a8d2b60e3b7
topic_type:
- apiref
ms.openlocfilehash: ff9827174e43fd62f3a995e9f477c6fff66b227a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449962"
---
# <a name="imetadataimportenumunresolvedmethods-method"></a>IMetaDataImport::EnumUnresolvedMethods 方法
列舉 MemberDef 語彙基元，其代表目前中繼資料範圍內無法解析的方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumUnresolvedMethods (  
   [in, out] HCORENUM    *phEnum,  
   [out]     mdToken     rMethods[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a>參數  
 `phEnum`  
 [in、out]列舉值的指標。 第一次呼叫此方法時，此值必須為 Null。  
  
 `rMethods`  
 脫銷用來儲存 MemberDef 標記的陣列。  
  
 `cMax`  
 [in] `rMethods` 陣列的大小上限。  
  
 `pcTokens`  
 脫銷`rMethods`中傳回的 MemberDef token 數目。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|已成功傳回 `EnumUnresolvedMethods`。|  
|`S_FALSE`|沒有要列舉的權杖。 在此情況下，`pcTokens` 為零。|  
  
## <a name="remarks"></a>備註  
 無法解析的方法是已宣告但未實作為的方法。 如果方法標記為 `miForwardRef`，且 `mdPinvokeImpl` 或 `miRuntime` 設定為零，則方法會包含在列舉中。 換句話說，未解析的方法是標示為 `miForwardRef` 但未在非受控碼中執行的類別方法（透過 PInvoke 取得），也不會在內部由執行時間本身執行  
  
 列舉會排除在模組範圍（globals）或介面或抽象類別中定義的所有方法。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
