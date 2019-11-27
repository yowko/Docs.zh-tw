---
title: IMetaDataImport::EnumFieldsWithName 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFieldsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFieldsWithName
helpviewer_keywords:
- IMetaDataImport::EnumFieldsWithName method [.NET Framework metadata]
- EnumFieldsWithName method [.NET Framework metadata]
ms.assetid: 42145e8d-000f-4d0b-ae43-c08201190fa2
topic_type:
- apiref
ms.openlocfilehash: b240be3e5b0127de42cea43dd8e89a2cc656b28e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449521"
---
# <a name="imetadataimportenumfieldswithname-method"></a>IMetaDataImport::EnumFieldsWithName 方法
列舉具有指定名稱之指定類型的 FieldDef 語彙基元。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumFieldsWithName (  
   [in, out] HCORENUM    *phEnum,   
   [in]  mdTypeDef       cl,   
   [in]  LPCWSTR         szName,   
   [out] mdFieldDef      rFields[],   
   [in]  ULONG           cMax,   
   [out] ULONG           *pcTokens   
);  
```  
  
## <a name="parameters"></a>參數  
 `phEnum`  
 [in、out]列舉值的指標。  
  
 `cl`  
 在要列舉其欄位之類型的 token。  
  
 `szName`  
 在限制列舉範圍的功能變數名稱。  
  
 `rFields`  
 脫銷用來儲存 FieldDef 標記的陣列。  
  
 `cMax`  
 [in] `rFields` 陣列的大小上限。  
  
 `pcTokens`  
 脫銷`rFields`中傳回的實際 FieldDef token 數目。  
  
## <a name="remarks"></a>備註  
 不同于[IMetaDataImport：： EnumFields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md)，`EnumFieldsWithName` 捨棄所有沒有指定名稱的欄位標記。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|已成功傳回 `EnumFieldsWithName`。|  
|`S_FALSE`|沒有可列舉的欄位。 在此情況下，`pcTokens` 為零。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
