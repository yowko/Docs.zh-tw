---
title: "IMetaDataEmit::DefineImportMember 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineImportMember
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineImportMember
helpviewer_keywords:
- DefineImportMember method [.NET Framework metadata]
- IMetaDataEmit::DefineImportMember method [.NET Framework metadata]
ms.assetid: c7dd94c6-335b-46ff-9dfe-505056db5673
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1bbe2c3144372ba66a0b3bad6198aefeeb7e12d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefineimportmember-method"></a>IMetaDataEmit::DefineImportMember 方法
會建立所指定成員的類型或模組，定義在目前的範圍之外，以及定義該參考的語彙基元的參考。  
  
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
  
#### <a name="parameters"></a>參數  
 `pAssemImport`  
 [in][IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)代表組件匯入的目標成員的介面。  
  
 `pbHashValue`  
 [in]陣列，其中包含所指定的組件的雜湊`pAssemImport`。  
  
 `cbHashValue`  
 [in] `pbHashValue` 陣列中的位元組數。  
  
 `pImport`  
 [in][IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)代表從中匯入目標成員的中繼資料範圍的介面。  
  
 `mbMember`  
 [in]指定目標成員的中繼資料語彙基元。 可以是語彙基元`mdMethodDef`（適用於成員方法）、 `mdProperty` （適用於成員屬性），或`mdFieldDef`（適用於成員欄位） 權杖。  
  
 `pAssemEmit`  
 [in][IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)表示目標成員匯入的組件介面。  
  
 `tkParent`  
 [in]`mdTypeRef`或`mdModuleRef`語彙基元的類型或模組，分別擁有目標成員。  
  
 `pmr`  
 [out]`mdMemberRef`成員參考目前範圍中定義的語彙基元。  
  
## <a name="remarks"></a>備註  
 `DefineImportMember`方法會查詢指定成員`mbMember`，也就是定義在另一個範圍內，由指定`pImport`，並擷取其屬性。 它會使用此資訊來呼叫[imetadataemit:: Definememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)建立成員參考目前範圍中的方法。  
  
 一般而言，當您使用`DefineImportMember`方法，您必須建立，在目前範圍、 型別參考或目標成員的父類別、 介面或模組的模組參考。 這個參考的中繼資料語彙基元然後傳入`tkParent`引數。 您不需要建立目標成員的父代參考，如果它由編譯器或連結器將會稍後解決。 總括來說：  
  
-   如果目標成員的欄位或方法，請使用  [imetadataemit:: Definetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md)或[imetadataemit:: Defineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)方法來建立型別參考，在目前範圍中，成員的父類別或父介面。  
  
-   如果目標成員的全域變數或全域函式 （也就是不是成員的類別或介面），請使用[imetadataemit:: Definemoduleref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md)方法來建立模組參考，在目前範圍中，成員的父系模組。  
  
-   如果將會由編譯器或連結器稍後解決目標成員的父系，則傳遞`mdTokenNil`中`tkParent`。 僅限適用的案例是在全域函式或全域變數從最後會連結到目前模組的.obj 檔案匯入和中繼資料合併。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
