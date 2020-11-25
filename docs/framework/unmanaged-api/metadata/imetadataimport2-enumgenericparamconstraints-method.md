---
title: IMetaDataImport2::EnumGenericParamConstraints 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumGenericParamConstraints
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumGenericParamConstraints
helpviewer_keywords:
- EnumGenericParamConstraints method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParamConstraints method [.NET Framework metadata]
ms.assetid: 8a7d4e40-28fe-4e14-b801-4049880130e7
topic_type:
- apiref
ms.openlocfilehash: 27c3ec349cf6c83f6783e252e6c5af5e99fa4b37
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702832"
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a>IMetaDataImport2::EnumGenericParamConstraints 方法

取得泛型參數條件約束陣列的列舉值，這些條件約束與指定標記所表示的泛型參數相關聯。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
## <a name="parameters"></a>參數  

 `phEnum`  
 [in，out]列舉值的指標。  
  
 `tk`  
 在  Token，代表要列舉其條件約束的泛型參數。  
  
 `rGenericParamConstraints`  
 擴展要列舉之泛型參數條件約束的陣列。  
  
 `cMax`  
 在  要求的最大權杖數目 `rGenericParamConstraints` 。  
  
 `pcGenericParamConstraints`  
 擴展放入的標記數目指標 `rGenericParamConstraints` 。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|`EnumGenericParameterConstraints` 傳回成功。|  
|`S_FALSE`|`phEnum` 沒有成員元素。 在此情況下， `pcGenericParameterConstraints` 會設定為 0 (零) 。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MsCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport2 介面](imetadataimport2-interface.md)
- [IMetaDataImport 介面](imetadataimport-interface.md)
