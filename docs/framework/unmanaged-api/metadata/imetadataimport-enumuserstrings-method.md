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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98b99493e54b123d37eb281455180b9a25baddd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimportenumuserstrings-method"></a>IMetaDataImport::EnumUserStrings 方法
列舉字串語彙基元，其代表目前中繼資料範圍內的硬式編碼字串。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT EnumUserStrings (  
   [in, out]  HCORENUM    *phEnum,  
   [out]  mdString        rStrings[],  
   [in]   ULONG           cMax,  
   [out]  ULONG           *pcStrings  
);  
```  
  
#### <a name="parameters"></a>參數  
 `phEnum`  
 [in、 out]列舉值的指標。 這必須是 NULL 的第一個呼叫此方法。  
  
 `rStrings`  
 [out]陣列，用來儲存的字串語彙基元。  
  
 `cMax`  
 [in] `rStrings` 陣列的大小上限。  
  
 `pcStrings`  
 [out]傳回的字串語彙基元數目`rStrings`。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|`EnumUserStrings` 已成功傳回。|  
|`S_FALSE`|沒有列舉語彙基元。 在此情況下，`pcStrings`為零。|  
  
## <a name="remarks"></a>備註  
 所建立的字串語彙基元[imetadataemit:: Defineuserstring](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md)方法。 這個方法被為了由中繼資料瀏覽器，而不是由編譯器使用。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
