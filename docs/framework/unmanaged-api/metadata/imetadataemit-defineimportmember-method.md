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
ms.openlocfilehash: 60210bc8f93294c3c3380c36096f3e80e5b26643
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723255"
---
# <a name="imetadataemitdefineimportmember-method"></a>IMetaDataEmit::DefineImportMember 方法

建立在目前範圍之外定義之類型或模組之指定成員的參考，並定義該參考的標記。  
  
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
 在 [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) 介面，表示要從中匯入目標成員的元件。  
  
 `pbHashValue`  
 在陣列，其中包含所指定之元件的雜湊 `pAssemImport` 。  
  
 `cbHashValue`  
 [in] `pbHashValue` 陣列中的位元組數。  
  
 `pImport`  
 在 [IMetaDataImport](imetadataimport-interface.md) 介面，表示要從中匯入目標成員的中繼資料範圍。  
  
 `mbMember`  
 在指定目標成員的元資料標記。 標記可以是 `mdMethodDef` 成員方法的 () 、 `mdProperty` 成員屬性) 的 (，或 `mdFieldDef` 成員欄位 (token 的) 。  
  
 `pAssemEmit`  
 在 [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) 介面，表示要匯入目標成員的元件。  
  
 `tkParent`  
 在 `mdTypeRef` `mdModuleRef` 類型或模組的或標記，分別擁有目標成員。  
  
 `pmr`  
 擴展 `mdMemberRef` 在成員參考的目前範圍中定義的標記。  
  
## <a name="remarks"></a>備註  

 方法會查閱由指定的成員（由指定）， `DefineImportMember` `mbMember` 並抓取 `pImport` 其屬性。 它會使用這項資訊來呼叫目前範圍中的 [IMetaDataEmit：:D efinememberref](imetadataemit-definememberref-method.md) 方法，以建立成員參考。  
  
 一般來說，在使用方法之前， `DefineImportMember` 您必須在目前的範圍中建立目標成員之父類別、介面或模組的型別參考或模組參考。 然後，會在引數中傳遞此參考的元資料標記 `tkParent` 。 如果編譯器或連結器稍後將會解決，您就不需要建立目標成員父系的參考。 總括來說：  
  
- 如果目標成員是欄位或方法，請使用 [IMetaDataEmit：:D efinetyperefbyname](imetadataemit-definetyperefbyname-method.md) 或 [IMetaDataEmit：:D efineimporttype](imetadataemit-defineimporttype-method.md) 方法，在目前的範圍中，為成員的父類別或父介面建立型別參考。  
  
- 如果目標成員是全域變數或全域函式 (也就是，而不是) 類別或介面的成員，請使用 [IMetaDataEmit：:D efinemoduleref](imetadataemit-definemoduleref-method.md) 方法，在目前的範圍中建立成員父模組的模組參考。  
  
- 如果編譯器或連結器稍後將解析目標成員的父系，則傳入 `mdTokenNil` `tkParent` 。 唯一適用的情況是，當從 .obj 檔案匯入全域函式或全域變數時，最後會連結到目前的模組，併合並中繼資料。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MSCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](imetadataemit-interface.md)
- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
