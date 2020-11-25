---
title: IMetaDataImport::EnumParams 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumParams
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumParams
helpviewer_keywords:
- IMetaDataImport::EnumParams method [.NET Framework metadata]
- EnumParams method [.NET Framework metadata]
ms.assetid: 52118dc9-fe6e-4b39-aa48-c3cc3ea4214d
topic_type:
- apiref
ms.openlocfilehash: b41f9bb05a43ac4c6dd8a89c45ef4826741e5679
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728260"
---
# <a name="imetadataimportenumparams-method"></a>IMetaDataImport::EnumParams 方法

列舉 ParamDef 語彙基元，其代表指定 MethodDef 語彙基元所參考之方法的參數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumParams (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,  
   [out] mdParamDef      rParams[],  
   [in]  ULONG           cMax,  
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a>參數  

 `phEnum`  
 [in，out]列舉值的指標。 此方法的第一個呼叫必須是 Null。  
  
 `mb`  
 在以列舉的參數表示方法的 MethodDef 標記。  
  
 `rParams`  
 擴展用來儲存 ParamDef 標記的陣列。  
  
 `cMax`  
 [in] `rParams` 陣列的大小上限。  
  
 `pcTokens`  
 擴展傳回的 ParamDef 權杖數目 `rParams` 。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|`EnumParams` 傳回成功。|  
|`S_FALSE`|沒有要列舉的權杖。 在此情況下， `pcTokens` 是零。|  
  
## <a name="requirements"></a>需求  

 **平臺：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MsCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
