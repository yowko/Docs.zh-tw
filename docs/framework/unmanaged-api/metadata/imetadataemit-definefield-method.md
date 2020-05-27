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
ms.openlocfilehash: ccc4843864f375c167acdb12575c282dbe3a49e1
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004799"
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
 在`mdTypeDef`封閉式類別或介面的 token。  
  
 `szName`  
 在Unicode 中的功能變數名稱。  
  
 `dwFieldFlags`  
 在欄位屬性。 這是值的位元遮罩 `CorFieldAttr` 。  
  
 `pvSigBlob`  
 在做為 BLOB 的欄位簽章。  
  
 `cbSigBlob`  
 在中的位元組計數 `pvSigBlob` 。  
  
 `dwCPlusTypeFlag`  
 在`ELEMENT_TYPE_` *\** 常數值的。 這是 `CorElementType` 值。 如果未定義欄位的常數值，請使用 `ELEMENT_TYPE_END` 。  
  
 `pValue`  
 在欄位的常數值。  
  
 `cchValue`  
 在的大小（Unicode）字元 `pValue` 。  
  
 `pmd`  
 脫銷`mdFieldDef`指派的 token。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](imetadataemit-interface.md)
- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
