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
ms.openlocfilehash: 2bc2b983171dc41d5ac37eda0359f1aaee4ebd6e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725751"
---
# <a name="imetadataemitdefinefield-method"></a>IMetaDataEmit::DefineField 方法

使用指定的中繼資料簽章建立欄位的定義，並取得該欄位定義的標記。  
  
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
 在 `mdTypeDef` 封閉類別或介面的標記。  
  
 `szName`  
 在Unicode 中的功能變數名稱。  
  
 `dwFieldFlags`  
 在欄位屬性。 這是值的位元遮罩 `CorFieldAttr` 。  
  
 `pvSigBlob`  
 在作為 BLOB 的欄位簽名。  
  
 `cbSigBlob`  
 在中的位元組計數 `pvSigBlob` 。  
  
 `dwCPlusTypeFlag`  
 在`ELEMENT_TYPE_` *\** 常數值的。 這是一個 `CorElementType` 值。 如果未定義欄位的常數值，請使用 `ELEMENT_TYPE_END` 。  
  
 `pValue`  
 在欄位的常數值。  
  
 `cchValue`  
 在 (Unicode) 字元的大小 `pValue` 。  
  
 `pmd`  
 擴展 `mdFieldDef` 指派的權杖。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MSCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](imetadataemit-interface.md)
- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
