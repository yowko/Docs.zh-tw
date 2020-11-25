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
ms.openlocfilehash: 6b5e7bbe2303a200d7829fea12e228a513595f97
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716547"
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
 [in，out]列舉值的指標。 此方法的第一個呼叫必須是 Null。  
  
 `rMethods`  
 擴展用來儲存 MemberDef 標記的陣列。  
  
 `cMax`  
 [in] `rMethods` 陣列的大小上限。  
  
 `pcTokens`  
 擴展傳回的 MemberDef 權杖數目 `rMethods` 。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|`EnumUnresolvedMethods` 傳回成功。|  
|`S_FALSE`|沒有要列舉的權杖。 在此情況下， `pcTokens` 是零。|  
  
## <a name="remarks"></a>備註  

 未解析的方法是已宣告但未執行的方法。 如果方法標示為 `miForwardRef` ，而且 `mdPinvokeImpl` 或 `miRuntime` 設定為零，則方法會包含在列舉中。 換句話說，未解析的方法是標示為 `miForwardRef` 但未在非受控程式碼中執行的類別方法 (透過 PInvoke) ，也不是由執行時間本身內部執行  
  
 列舉會排除在模組範圍 (globals) 或在介面或抽象類別中定義的所有方法。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
