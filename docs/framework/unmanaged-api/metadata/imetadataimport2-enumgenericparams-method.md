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
ms.openlocfilehash: 6b1a8e66eea6caec9dfc8d99e343c987cefa1b0c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702754"
---
# <a name="imetadataimport2enumgenericparams-method"></a>IMetaDataImport2::EnumGenericParams 方法

取得與指定的 TypeDef 或 MethodDef token 相關聯之泛型參數標記陣列的列舉值。  
  
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
 [in，out]列舉值的指標。  
  
 `tk`  
 在要列舉其泛型參數的 TypeDef 或 MethodDef 標記。  
  
 `rGenericParams`  
 擴展要列舉之泛型參數的陣列。  
  
 `cMax`  
 在要求的最大權杖數目 `rGenericParams` 。  
  
 `pcGenericParams`  
 擴展所傳回的權杖數目 `rGenericParams` 。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|`EnumGenericParams` 傳回成功。|  
|`S_FALSE`|`phEnum` 沒有成員元素。 在此情況下， `pcGenericParams` 會設定為 0 (零) 。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MsCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport2 介面](imetadataimport2-interface.md)
- [IMetaDataImport 介面](imetadataimport-interface.md)
