---
title: IMetaDataImport::EnumMethodsWithName 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodsWithName
helpviewer_keywords:
- IMetaDataImport::EnumMethodsWithName method [.NET Framework metadata]
- EnumMethodsWithName method [.NET Framework metadata]
ms.assetid: a8624913-2e23-46ad-a0c1-bb8eccbbf20f
topic_type:
- apiref
ms.openlocfilehash: 66a09baea1df2e2de418bdce8821672802f1f51f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491728"
---
# <a name="imetadataimportenummethodswithname-method"></a>IMetaDataImport::EnumMethodsWithName 方法
列舉具有指定名稱的方法，且該方法由指定 TypeDef 語彙基元所參考的類型定義。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumMethodsWithName (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdTypeDef       cl,  
   [in]  LPCWSTR         szName,  
   [out] mdMethodDef     rMethods[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a>參數  
 `phEnum`  
 [in、out]列舉值的指標。 第一次呼叫此方法時，此值必須為 Null。  
  
 `cl`  
 在TypeDef token，代表要列舉其方法的類型。  
  
 `szName`  
 在限制列舉範圍的名稱。  
  
 `rMethods`  
 脫銷用來儲存 MethodDef 標記的陣列。  
  
 `cMax`  
 [in] `rMethods` 陣列的大小上限。  
  
 `pcTokens`  
 脫銷在中傳回的 MethodDef 標記數目 `rMethods` 。  
  
## <a name="remarks"></a>備註  
 這個方法會列舉欄位和方法，而不是屬性或事件。 不同于[IMetaDataImport：： EnumMethods](imetadataimport-enummethods-method.md)，會 `EnumMethodsWithName` 捨棄所有沒有指定名稱的方法標記。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|說明|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodsWithName`已成功傳回。|  
|`S_FALSE`|沒有要列舉的權杖。 在此情況下， `pcTokens` 是零。|  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
