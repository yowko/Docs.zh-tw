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
ms.openlocfilehash: 6825a5198976cc7ab2c04ebd6e782418dcf4a8f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177686"
---
# <a name="imetadataemitdefineimporttype-method"></a>IMetaDataEmit::DefineImportType 方法
創建對在當前作用域之外定義的指定類型的引用，並為該引用定義權杖。  
  
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
 [在][IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)，表示從中導入目標型別的程式集。  
  
 `pbHashValue`  
 [在]包含 的陣列，其中包含 由 指定的`pAssemImport`程式集的雜湊值。  
  
 `cbHashValue`  
 [in] `pbHashValue` 陣列中的位元組數。  
  
 `pImport`  
 [在][IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)介面，表示從中導入目標型別的中繼資料範圍。  
  
 `tdImport`  
 [在]指定`mdTypeDef`目標型別的權杖。  
  
 `pAssemEmit`  
 [在][IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)介面，表示將目標型別導入到的程式集。  
  
 `ptr`  
 [出]類型`mdTypeRef`引用的當前作用域中定義的權杖。  
  
## <a name="remarks"></a>備註  
 在調用[IMetaDataEmit：:DefineImportI成員](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md)方法之前，可以使用`DefineImportType`該方法為成員的父類或父介面在當前作用域中創建類型引用。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MSCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
