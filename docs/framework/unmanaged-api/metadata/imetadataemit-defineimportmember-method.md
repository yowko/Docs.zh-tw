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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 81acda4d395563fc8e0000e38036d1aaa0f14471
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222688"
---
# <a name="imetadataemitdefineimportmember-method"></a>IMetaDataEmit::DefineImportMember 方法
建立指定的成員類型或模組，可定義在目前的範圍之外，並定義該參考語彙基元的參考。  
  
## <a name="syntax"></a>語法  
  
```  
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
 [in][IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)介面，表示從其中匯入的目標成員的組件。  
  
 `pbHashValue`  
 [in]陣列，其中包含所指定的組件的雜湊`pAssemImport`。  
  
 `cbHashValue`  
 [in] `pbHashValue` 陣列中的位元組數。  
  
 `pImport`  
 [in][IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)介面，表示從其中匯入的目標成員的中繼資料範圍。  
  
 `mbMember`  
 [in]指定目標成員的中繼資料語彙基元。 權杖可被`mdMethodDef`（適用於成員方法）， `mdProperty` （適用於成員屬性中），或`mdFieldDef`（適用於成員欄位） 語彙基元。  
  
 `pAssemEmit`  
 [in][IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)代表組件匯入到其中的目標成員的介面。  
  
 `tkParent`  
 [in]`mdTypeRef`或`mdModuleRef`的語彙基元的類型或模組，分別擁有目標成員。  
  
 `pmr`  
 [out]`mdMemberRef`成員參考目前範圍中定義的語彙基元。  
  
## <a name="remarks"></a>備註  
 `DefineImportMember`方法會指定成員查閱`mbMember`，也就是定義在另一個範圍內，由指定`pImport`，並擷取其屬性。 它會使用此資訊來呼叫[imetadataemit:: Definememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)建立成員參考目前範圍中的方法。  
  
 一般而言，您使用`DefineImportMember`方法，您必須建立，在目前範圍、 型別參考或目標成員的父類別、 介面或模組的模組參考。 此參考的中繼資料語彙基元然後傳入`tkParent`引數。 您不需要建立目標成員的父系的參考，如果它由編譯器或連結器將會稍後解決。 總括來說：  
  
-   如果目標成員是欄位或方法，使用任何一種[imetadataemit:: Definetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md)或[imetadataemit:: Defineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)方法來建立型別參考，在目前的範圍內，成員的父類別或父介面。  
  
-   如果目標成員的全域變數或全域函式 （也就是不在成員的類別或介面），請使用[imetadataemit:: Definemoduleref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md)方法用來建立模組參考，在目前範圍中，成員的父系模組。  
  
-   如果目標成員的父系的解決方法的編譯器或連結器的更新版本，然後傳遞`mdTokenNil`在`tkParent`。 這適用的唯一案例是當全域函式或全域變數從.obj 檔案，最後會連結到目前的模組匯入和中繼資料合併。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 做為 MSCorEE.dll 中的資源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
