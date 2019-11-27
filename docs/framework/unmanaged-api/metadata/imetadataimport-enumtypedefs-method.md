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
ms.openlocfilehash: 3854cb4aa3d229c87466c0a35a72447ceb235624
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450002"
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
 脫銷`rTypeDefs`中傳回的 TypeDef 標記數目。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|已成功傳回 `EnumTypeDefs`。|  
|`S_FALSE`|沒有要列舉的權杖。 在此情況下，`pcTypeDefs` 為零。|  
  
## <a name="remarks"></a>備註  
 TypeDef token 代表類別或介面等類型，以及透過擴充性機制新增的任何類型。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
