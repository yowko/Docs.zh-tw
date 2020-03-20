---
title: IMetaDataImport2::EnumGenericParams 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumGenericParams
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumGenericParams
helpviewer_keywords:
- EnumGenericParams method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParams method [.NET Framework metadata]
ms.assetid: b50488a5-3cf0-483c-82dc-2892a3ec61ac
topic_type:
- apiref
ms.openlocfilehash: 55709e79cd8bdb36fe1e32ee8a699fccb1b1bbc8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175300"
---
# <a name="imetadataimport2enumgenericparams-method"></a>IMetaDataImport2::EnumGenericParams 方法
獲取與指定 TypeDef 或 MethodDef 權杖關聯的泛型參數權杖陣列的枚舉器。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT EnumGenericParams (  
   [in, out] HCORENUM     *phEnum,
   [in]  mdToken          tk,  
   [out] mdGenericParam   rGenericParams[],
   [in]  ULONG            cMax,
   [out] ULONG            *pcGenericParams  
);  
```  
  
## <a name="parameters"></a>參數  
 `phEnum`  
 [進出]指向枚舉器的指標。  
  
 `tk`  
 [在]要枚舉泛型參數的 TypeDef 或 MethodDef 權杖。  
  
 `rGenericParams`  
 [出]要枚舉的泛型參數陣列。  
  
 `cMax`  
 [在]要放置在 中`rGenericParams`的最大權杖數。  
  
 `pcGenericParams`  
 [出]放置在 的`rGenericParams`返回的權杖數。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|`EnumGenericParams`已成功返回。|  
|`S_FALSE`|`phEnum`沒有成員元素。 在這種情況下，`pcGenericParams`設置為 0（零）。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MsCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
