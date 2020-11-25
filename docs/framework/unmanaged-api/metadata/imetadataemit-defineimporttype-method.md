---
title: IMetaDataEmit::DefineImportType 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineImportType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineImportType
helpviewer_keywords:
- DefineImportType method [.NET Framework metadata]
- IMetaDataEmit::DefineImportType method [.NET Framework metadata]
ms.assetid: 37fd27af-8062-4904-ace4-51bb78ec600a
topic_type:
- apiref
ms.openlocfilehash: 94ce4443be210fdfeb1bab197c3e603255e1cc4c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723242"
---
# <a name="imetadataemitdefineimporttype-method"></a>IMetaDataEmit::DefineImportType 方法

建立在目前範圍之外定義之指定型別的參考，並定義該參考的權杖。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DefineImportType (
    [in]  IMetaDataAssemblyImport  *pAssemImport,
    [in]  const void               *pbHashValue,
    [in]  ULONG                    cbHashValue,
    [in]  IMetaDataImport          *pImport,
    [in]  mdTypeDef                tdImport,
    [in]  IMetaDataAssemblyEmit    *pAssemEmit,
    [out] mdTypeRef                *ptr  
);  
```  
  
## <a name="parameters"></a>參數  

 `pAssemImport`  
 在 [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) 介面，表示匯入目標型別的元件。  
  
 `pbHashValue`  
 在陣列，其中包含所指定之元件的雜湊 `pAssemImport` 。  
  
 `cbHashValue`  
 [in] `pbHashValue` 陣列中的位元組數。  
  
 `pImport`  
 在 [IMetaDataImport](imetadataimport-interface.md) 介面，表示要從中匯入目標型別的中繼資料範圍。  
  
 `tdImport`  
 在 `mdTypeDef` 指定目標型別的標記。  
  
 `pAssemEmit`  
 在 [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) 介面，表示要匯入目標型別的元件。  
  
 `ptr`  
 擴展在 `mdTypeRef` 目前範圍中針對型別參考定義的標記。  
  
## <a name="remarks"></a>備註  

 在呼叫 [IMetaDataEmit：:D efineimportmember](imetadataemit-defineimportmember-method.md) 方法之前，您可以使用方法， `DefineImportType` 在目前的範圍中，為成員的父類別或父介面建立型別參考。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MSCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](imetadataemit-interface.md)
- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
