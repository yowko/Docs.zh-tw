---
title: IMetaDataEmit::DefineField 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineField
helpviewer_keywords:
- IMetaDataEmit::DefineField method [.NET Framework metadata]
- DefineField method, IMetaDataEmit interface [.NET Framework metadata
ms.assetid: 6b5be4fc-2e86-499c-8b09-833160bca767
topic_type:
- apiref
ms.openlocfilehash: 40f24a4ea628ce92a27ab1bfe97fc87a57dfa4f0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432554"
---
# <a name="imetadataemitdefinefield-method"></a>IMetaDataEmit::DefineField 方法
使用指定的中繼資料簽章建立欄位的定義，並取得該欄位定義的 token。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DefineField (   
    [in]  mdTypeDef   td,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwFieldFlags,   
    [in]  PCCOR_SIGNATURE pvSigBlob,   
    [in]  ULONG       cbSigBlob,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue,   
    [out] mdFieldDef  *pmd   
);  
```  
  
## <a name="parameters"></a>參數  
 `td`  
 在封入類別或介面的 `mdTypeDef` token。  
  
 `szName`  
 在Unicode 中的功能變數名稱。  
  
 `dwFieldFlags`  
 在欄位屬性。 這是 `CorFieldAttr` 值的位元遮罩。  
  
 `pvSigBlob`  
 在做為 BLOB 的欄位簽章。  
  
 `cbSigBlob`  
 在`pvSigBlob`中的位元組計數。  
  
 `dwCPlusTypeFlag`  
 在常數值的 `ELEMENT_TYPE_` *\** 。 這是 `CorElementType` 值。 如果未定義欄位的常數值，請使用 `ELEMENT_TYPE_END`。  
  
 `pValue`  
 在欄位的常數值。  
  
 `cchValue`  
 在`pValue`的（Unicode）字元大小。  
  
 `pmd`  
 脫銷指派的 `mdFieldDef` token。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
