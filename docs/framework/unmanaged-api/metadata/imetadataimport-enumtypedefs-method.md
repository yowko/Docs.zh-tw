---
title: IMetaDataImport::EnumTypeDefs 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeDefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeDefs
helpviewer_keywords:
- EnumTypeDefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeDefs method [.NET Framework metadata]
ms.assetid: 4e508711-da92-4381-aaf8-6803075cdaa2
topic_type:
- apiref
ms.openlocfilehash: cdfd4e10236d546af2555b125d44233172849a21
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503727"
---
# <a name="imetadataimportenumtypedefs-method"></a>IMetaDataImport::EnumTypeDefs 方法
列舉代表目前範圍內的所有類型的 TypeDef 語彙基元。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,
   [out] ULONG      *pcTypeDefs  
);  
```  
  
## <a name="parameters"></a>參數  
 `phEnum`  
 脫銷新枚舉器的指標。 第一次呼叫此方法時，此值必須為 Null。  
  
 `rTypeDefs`  
 在用來儲存 TypeDef 標記的陣列。  
  
 `cMax`  
 [in] `rTypeDefs` 陣列的大小上限。  
  
 `pcTypeDefs`  
 脫銷在中傳回的 TypeDef 標記數目 `rTypeDefs` 。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|說明|  
|-------------|-----------------|  
|`S_OK`|`EnumTypeDefs`已成功傳回。|  
|`S_FALSE`|沒有要列舉的權杖。 在此情況下， `pcTypeDefs` 是零。|  
  
## <a name="remarks"></a>備註  
 TypeDef token 代表類別或介面等類型，以及透過擴充性機制新增的任何類型。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
