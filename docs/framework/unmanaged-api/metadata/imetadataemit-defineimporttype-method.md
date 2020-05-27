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
ms.openlocfilehash: edce5cb93b770fb5730e5a06633ffffacf332f7a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004684"
---
# <a name="imetadataemitdefineimporttype-method"></a>IMetaDataEmit::DefineImportType 方法
建立定義于目前範圍外之指定類型的參考，並定義該參考的 token。  
  
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
 在[IMetaDataAssemblyImport](imetadataassemblyimport-interface.md)介面，表示從中匯入目標型別的元件。  
  
 `pbHashValue`  
 在陣列，其中包含所指定之元件的雜湊 `pAssemImport` 。  
  
 `cbHashValue`  
 [in] `pbHashValue` 陣列中的位元組數。  
  
 `pImport`  
 在[IMetaDataImport](imetadataimport-interface.md)介面，表示從中匯入目標型別的中繼資料範圍。  
  
 `tdImport`  
 在`mdTypeDef`指定目標型別的 token。  
  
 `pAssemEmit`  
 在[IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md)介面，表示要匯入目標型別的元件。  
  
 `ptr`  
 脫銷`mdTypeRef`在類型參考的目前範圍中定義的 token。  
  
## <a name="remarks"></a>備註  
 呼叫[IMetaDataEmit：:D efineimportmember](imetadataemit-defineimportmember-method.md)方法之前，您可以使用 `DefineImportType` 方法，針對成員的父類別或父介面，在目前的範圍中建立類型參考。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](imetadataemit-interface.md)
- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
