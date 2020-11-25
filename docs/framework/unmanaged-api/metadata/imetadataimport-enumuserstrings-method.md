---
title: IMetaDataImport::EnumUserStrings 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumUserStrings
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumUserStrings
helpviewer_keywords:
- IMetaDataImport::EnumUserStrings method [.NET Framework metadata]
- EnumUserStrings method [.NET Framework metadata]
ms.assetid: 2b1f1418-4be8-4cdb-b418-b3abccc527a7
topic_type:
- apiref
ms.openlocfilehash: c7dcc740dcf9b228713693a57dc8ef96d215ebad
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716557"
---
# <a name="imetadataimportenumuserstrings-method"></a>IMetaDataImport::EnumUserStrings 方法

列舉字串語彙基元，其代表目前中繼資料範圍內的硬式編碼字串。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumUserStrings (  
   [in, out]  HCORENUM    *phEnum,  
   [out]  mdString        rStrings[],  
   [in]   ULONG           cMax,  
   [out]  ULONG           *pcStrings  
);  
```  
  
## <a name="parameters"></a>參數  

 `phEnum`  
 [in，out]列舉值的指標。 此方法的第一個呼叫必須是 Null。  
  
 `rStrings`  
 擴展用來儲存字串標記的陣列。  
  
 `cMax`  
 [in] `rStrings` 陣列的大小上限。  
  
 `pcStrings`  
 擴展傳回的字串標記數目 `rStrings` 。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|`EnumUserStrings` 傳回成功。|  
|`S_FALSE`|沒有要列舉的權杖。 在此情況下， `pcStrings` 是零。|  
  
## <a name="remarks"></a>備註  

 字串標記是由 [IMetaDataEmit：:D efineuserstring](imetadataemit-defineuserstring-method.md) 方法所建立。 這個方法是設計來供中繼資料瀏覽器使用，而不是編譯器。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
