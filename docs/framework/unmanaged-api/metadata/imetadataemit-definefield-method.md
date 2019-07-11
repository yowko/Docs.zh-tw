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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 057bae1d702fa091ebc3d3178c9fba35d5dd3d90
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777651"
---
# <a name="imetadataemitdefinefield-method"></a>IMetaDataEmit::DefineField 方法
建立欄位的定義，具有指定之中繼資料簽章，並取得該欄位定義的語彙基元。  
  
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
 [in]`mdTypeDef`封入類別或介面的語彙基元。  
  
 `szName`  
 [in]以 Unicode 欄位名稱。  
  
 `dwFieldFlags`  
 [in]欄位的欄位屬性。 這是位元遮罩`CorFieldAttr`值。  
  
 `pvSigBlob`  
 [in]為 BLOB 欄位簽章。  
  
 `cbSigBlob`  
 [in]中的位元組計數`pvSigBlob`。  
  
 `dwCPlusTypeFlag`  
 [in]`ELEMENT_TYPE_` *\** 常數的值。 這是`CorElementType`值。 如果未定義欄位的常數值，使用`ELEMENT_TYPE_END`。  
  
 `pValue`  
 [in]欄位的常值。  
  
 `cchValue`  
 [in]\(Unicode\) 字元的大小`pValue`。  
  
 `pmd`  
 [out]`mdFieldDef`指派權杖。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
