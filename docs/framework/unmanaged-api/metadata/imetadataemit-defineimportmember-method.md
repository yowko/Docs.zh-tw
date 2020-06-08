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
ms.openlocfilehash: 2facc63023a20dd6aaac64d7d036324c31658bc8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501309"
---
# <a name="imetadataemitdefineimportmember-method"></a>IMetaDataEmit::DefineImportMember 方法
建立在目前範圍外定義之類型或模組之指定成員的參考，並定義該參考的 token。  
  
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
 在[IMetaDataAssemblyImport](imetadataassemblyimport-interface.md)介面，表示從中匯入目標成員的元件。  
  
 `pbHashValue`  
 在陣列，其中包含所指定之元件的雜湊 `pAssemImport` 。  
  
 `cbHashValue`  
 [in] `pbHashValue` 陣列中的位元組數。  
  
 `pImport`  
 在[IMetaDataImport](imetadataimport-interface.md)介面，表示要從中匯入目標成員的中繼資料範圍。  
  
 `mbMember`  
 在指定目標成員的元資料標記。 Token 可以是 `mdMethodDef` （針對成員方法）、 `mdProperty` （針對成員屬性），或 `mdFieldDef` （針對成員欄位） token。  
  
 `pAssemEmit`  
 在[IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md)介面，表示要匯入目標成員的元件。  
  
 `tkParent`  
 在`mdTypeRef` `mdModuleRef` 分別擁有目標成員之類型或模組的或 token。  
  
 `pmr`  
 脫銷`mdMemberRef`在成員參考的目前範圍中定義的 token。  
  
## <a name="remarks"></a>備註  
 `DefineImportMember`方法會查閱由指定的成員， `mbMember` 其定義于另一個範圍中，由指定 `pImport` ，並抓取其屬性。 它會使用這項資訊來呼叫目前範圍中的[IMetaDataEmit：:D efinememberref](imetadataemit-definememberref-method.md)方法，以建立成員參考。  
  
 一般來說，在您使用 `DefineImportMember` 方法之前，您必須先在目前的範圍中建立目標成員之父類別、介面或模組的類型參考或模組參考。 然後會在引數中傳遞此參考的元資料標記 `tkParent` 。 如果目標成員的父系稍後將由編譯器或連結器解析，您就不需要建立該參考。 總括來說：  
  
- 如果目標成員是欄位或方法，請使用[IMetaDataEmit：:D efinetyperefbyname](imetadataemit-definetyperefbyname-method.md)或[IMetaDataEmit：:D efineimporttype](imetadataemit-defineimporttype-method.md)方法，針對成員的父類別或父介面，在目前的範圍中建立類型參考。  
  
- 如果目標成員是全域變數或全域函式（也就是，而不是類別或介面的成員），請使用[IMetaDataEmit：:D efinemoduleref](imetadataemit-definemoduleref-method.md)方法，在目前的範圍中，為成員的父模組建立模組參考。  
  
- 如果稍後會由編譯器或連結器解析目標成員的父系，則請傳入 `mdTokenNil` `tkParent` 。 只有當全域函式或全域變數是從 .obj 檔案匯入，而此檔案最後會連結到目前的模組和合併的中繼資料時，才適用這種情況。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](imetadataemit-interface.md)
- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
