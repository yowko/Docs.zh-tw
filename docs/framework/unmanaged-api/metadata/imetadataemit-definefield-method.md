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
ms.openlocfilehash: 8ca5ab70f60de4d783800fb18612a8f04cb9cee1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177707"
---
# <a name="imetadataemitdefinefield-method"></a>IMetaDataEmit::DefineField 方法
為具有指定中繼資料簽名的欄位創建定義，並獲取該欄位定義的權杖。  
  
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
 [在]封閉`mdTypeDef`類或介面的權杖。  
  
 `szName`  
 [在]Unicode 中的欄位名稱。  
  
 `dwFieldFlags`  
 [在]欄位屬性。 這是值的`CorFieldAttr`位元遮罩。  
  
 `pvSigBlob`  
 [在]欄位簽名作為 BLOB。  
  
 `cbSigBlob`  
 [在]中的`pvSigBlob`位元組計數。  
  
 `dwCPlusTypeFlag`  
 [在]常`ELEMENT_TYPE_`*\** 量值的 。 這是一個`CorElementType`值。 如果未為欄位定義常量值，請使用`ELEMENT_TYPE_END`。  
  
 `pValue`  
 [在]欄位的常量值。  
  
 `cchValue`  
 [在]的大小（Unicode）字元。 `pValue`  
  
 `pmd`  
 [出]分配的`mdFieldDef`權杖。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MSCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
