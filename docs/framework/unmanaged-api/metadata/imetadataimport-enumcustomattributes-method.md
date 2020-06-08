---
title: IMetaDataImport::EnumCustomAttributes 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumCustomAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method [.NET Framework metadata]
- IMetaDataImport::EnumCustomAttributes method [.NET Framework metadata]
ms.assetid: 798513a0-68b1-4d04-bc5b-782a4445ea68
topic_type:
- apiref
ms.openlocfilehash: 9b0da8a06259fe99da52497da3011da94289d301
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492313"
---
# <a name="imetadataimportenumcustomattributes-method"></a>IMetaDataImport::EnumCustomAttributes 方法
列舉與指定的類型或成員相關聯的自訂屬性定義標記。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumCustomAttributes (
   [in, out] HCORENUM      *phEnum,  
   [in]  mdToken            tk,
   [in]  mdToken            tkType,
   [out] mdCustomAttribute  rCustomAttributes[],
   [in]  ULONG              cMax,  
   [out, optional] ULONG   *pcCustomAttributes  
);  
```  
  
## <a name="parameters"></a>參數  
 `phEnum`  
 [in、out]傳回之列舉值的指標。  
  
 `tk`  
 在列舉範圍的 token，如果是所有自訂屬性，則為零。  
  
 `tkType`  
 在要列舉之屬性類型的函式的 token，或 `null` 適用于所有類型的標記。  
  
 `rCustomAttributes`  
 脫銷自訂屬性標記的陣列。  
  
 `cMax`  
 [in] `rCustomAttributes` 陣列的大小上限。  
  
 `pcCustomAttributes`  
 [out，optional]在中傳回的實際標記值數目 `rCustomAttributes` 。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|說明|  
|-------------|-----------------|  
|`S_OK`|`EnumCustomAttributes`已成功傳回。|  
|`S_FALSE`|沒有可列舉的自訂屬性。 在此情況下， `pcCustomAttributes` 是零。|  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
