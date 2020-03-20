---
title: IMetaDataEmit::DefineImportMember 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineImportMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineImportMember
helpviewer_keywords:
- DefineImportMember method [.NET Framework metadata]
- IMetaDataEmit::DefineImportMember method [.NET Framework metadata]
ms.assetid: c7dd94c6-335b-46ff-9dfe-505056db5673
topic_type:
- apiref
ms.openlocfilehash: a7449ffc8a8ccf2db62ab3cff2f9cfaffd0c72a9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175859"
---
# <a name="imetadataemitdefineimportmember-method"></a>IMetaDataEmit::DefineImportMember 方法
創建對在當前作用域之外定義的類型或模組的指定成員的引用，並為該引用定義權杖。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DefineImportMember (
    [in]  IMetaDataAssemblyImport  *pAssemImport,
    [in]  const void               *pbHashValue,
    [in]  ULONG                    cbHashValue,  
    [in]  IMetaDataImport          *pImport,
    [in]  mdToken                  mbMember,
    [in]  IMetaDataAssemblyEmit    *pAssemEmit,
    [in]  mdToken                  tkParent,
    [out] mdMemberRef              *pmr
);  
```  
  
## <a name="parameters"></a>參數  
 `pAssemImport`  
 [在][IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)，表示從中導入目標成員的程式集。  
  
 `pbHashValue`  
 [在]包含 的陣列，其中包含 由 指定的`pAssemImport`程式集的雜湊值。  
  
 `cbHashValue`  
 [in] `pbHashValue` 陣列中的位元組數。  
  
 `pImport`  
 [在][IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)介面，表示從中導入目標成員的中繼資料範圍。  
  
 `mbMember`  
 [在]指定目標成員的中繼資料權杖。 權杖可以是`mdMethodDef`（對於成員方法）、（`mdProperty`對於成員屬性）或`mdFieldDef`（對於成員欄位）的權杖。  
  
 `pAssemEmit`  
 [在][IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)介面，表示將目標成員導入到的程式集。  
  
 `tkParent`  
 [在]分別`mdTypeRef`擁有`mdModuleRef`目標成員的類型或模組的 或 權杖。  
  
 `pmr`  
 [出]在`mdMemberRef`成員引用的當前作用域中定義的權杖。  
  
## <a name="remarks"></a>備註  
 方法`DefineImportMember`查找由`mbMember`指定的成員，該成員在由 指定的另一個作用域中定義`pImport`，由 指定並檢索其屬性。 它使用此資訊調用當前作用域中的[IMetaDataEmit：:Define會員Ref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)方法來創建成員引用。  
  
 通常，在使用`DefineImportMember`方法之前，必須在當前作用域中為目標成員的父類、介面或模組創建類型引用或模組引用。 然後，在參數中傳遞此引用的`tkParent`中繼資料權杖。 如果編譯器或連結器稍後將解析目標成員的父項，則無需創建對目標成員的父項的引用。 總結：  
  
- 如果目標成員是欄位或方法，請使用[IMetaDataEmit：:DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md)或[IMetaDataEmit：:DefineImportType 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)，為成員的父類或父介面在當前作用域中創建類型引用。  
  
- 如果目標成員是全域變數或全域函數（即不是類或介面的成員），請使用[IMetaDataEmit：:DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md)方法為成員的父模組在當前作用域中創建模組引用。  
  
- 如果稍後編譯器或連結器將解析目標成員的父成員的父級，則將傳遞`mdTokenNil``tkParent`。 唯一適用這種情況的情況是，全域函數或全域變數從 .obj 檔導入，該檔最終將連結到當前模組併合並中繼資料。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MSCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
