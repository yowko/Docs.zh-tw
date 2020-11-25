---
title: IMetaDataImport2::EnumMethodSpecs 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumMethodSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumMethodSpecs
helpviewer_keywords:
- IMetaDataImport2::EnumMethodSpecs method [.NET Framework metadata]
- EnumMethodSpecs method [.NET Framework metadata]
ms.assetid: b3fc1e6c-bcb6-4915-baf8-7dc0a31b8724
topic_type:
- apiref
ms.openlocfilehash: 26b345567699c5780827ed835cff13069ea8f609
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702741"
---
# <a name="imetadataimport2enummethodspecs-method"></a>IMetaDataImport2::EnumMethodSpecs 方法

取得與指定的 MethodDef 或 MemberRef token 相關聯的 MethodSpec 標記陣列的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);
```  
  
## <a name="parameters"></a>參數  

 `phEnum`  
 [in，out]列舉值的指標 `rMethodSpecs` 。  
  
 `tk`  
 在MemberRef 或 MethodDef token，代表要列舉其 MethodSpec 權杖的方法。 如果的值 `tk` 為 0 (零) ，將會列舉範圍中的所有 MethodSpec 標記。  
  
 `rMethodSpecs`  
 擴展要列舉的 MethodSpec 權杖陣列。  
  
 `cMax`  
 在要求的最大權杖數目 `rMethodSpecs` 。  
  
 `pcMethodSpecs`  
 擴展所傳回的權杖數目 `rMethodSpecs` 。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSpecs` 傳回成功。|  
|`S_FALSE`|`phEnum` 沒有成員元素。 在此情況下， `pcMethodSpecs` 會設定為 0 (零) 。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MsCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport2 介面](imetadataimport2-interface.md)
- [IMetaDataImport 介面](imetadataimport-interface.md)
