---
title: IMetaDataImport::EnumTypeSpecs 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeSpecs
helpviewer_keywords:
- EnumTypeSpecs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeSpecs method [.NET Framework metadata]
ms.assetid: 75331c7b-988b-436c-9eb9-a270d37b4f06
topic_type:
- apiref
ms.openlocfilehash: 94b4c3935c949c0c4008e41244713b6bfa4dba84
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503714"
---
# <a name="imetadataimportenumtypespecs-method"></a>IMetaDataImport::EnumTypeSpecs 方法
列舉在目前中繼資料範圍中定義的 TypeSpec 語彙基元。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumTypeSpecs (  
   [in, out] HCORENUM    *phEnum,  
   [out] mdTypeSpec      rTypeSpecs[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTypeSpecs  
);  
```  
  
## <a name="parameters"></a>參數  
 `phEnum`  
 [in、out]列舉值的指標。 這個方法的第一次呼叫時，這個值必須是 Null。  
  
 `rTypeSpecs`  
 脫銷用來儲存 TypeSpec 標記的陣列。  
  
 `cMax`  
 [in] `rTypeSpecs` 陣列的大小上限。  
  
 `pcTypeSpecs`  
 脫銷在中傳回的 TypeSpec token 數目 `rTypeSpecs` 。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|說明|  
|-------------|-----------------|  
|`S_OK`|`EnumTypeSpecs`已成功傳回。|  
|`S_FALSE`|沒有要列舉的權杖。 在此情況下， `pcTypeSpecs` 是零。|  
  
## <a name="remarks"></a>備註  
 TypeSpec 標記是由[IMetaDataEmit：： GetTokenFromTypeSpec](imetadataemit-gettokenfromtypespec-method.md)方法所建立。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
