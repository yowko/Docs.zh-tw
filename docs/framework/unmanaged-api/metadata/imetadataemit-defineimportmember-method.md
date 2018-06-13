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
ms.openlocfilehash: f9995fda70d1d5a3c19c30496de6c32f20015d47
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449386"
---
# <a name="imetadataemitdefineimportmember-method"></a><span data-ttu-id="99c11-102">IMetaDataEmit::DefineImportMember 方法</span><span class="sxs-lookup"><span data-stu-id="99c11-102">IMetaDataEmit::DefineImportMember Method</span></span>
<span data-ttu-id="99c11-103">會建立所指定成員的類型或模組，定義在目前的範圍之外，以及定義該參考的語彙基元的參考。</span><span class="sxs-lookup"><span data-stu-id="99c11-103">Creates a reference to the specified member of a type or module that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99c11-104">語法</span><span class="sxs-lookup"><span data-stu-id="99c11-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="99c11-105">參數</span><span class="sxs-lookup"><span data-stu-id="99c11-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="99c11-106">[in][IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)代表組件匯入的目標成員的介面。</span><span class="sxs-lookup"><span data-stu-id="99c11-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target member is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="99c11-107">[in]陣列，其中包含所指定的組件的雜湊`pAssemImport`。</span><span class="sxs-lookup"><span data-stu-id="99c11-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="99c11-108">[in] `pbHashValue` 陣列中的位元組數。</span><span class="sxs-lookup"><span data-stu-id="99c11-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="99c11-109">[in][IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)代表從中匯入目標成員的中繼資料範圍的介面。</span><span class="sxs-lookup"><span data-stu-id="99c11-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target member is imported.</span></span>  
  
 `mbMember`  
 <span data-ttu-id="99c11-110">[in]指定目標成員的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="99c11-110">[in] The metadata token that specifies the target member.</span></span> <span data-ttu-id="99c11-111">可以是語彙基元`mdMethodDef`（適用於成員方法）、 `mdProperty` （適用於成員屬性），或`mdFieldDef`（適用於成員欄位） 權杖。</span><span class="sxs-lookup"><span data-stu-id="99c11-111">The token can be an `mdMethodDef` (for a member method), `mdProperty` (for a member property), or `mdFieldDef` (for a member field) token.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="99c11-112">[in][IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)表示目標成員匯入的組件介面。</span><span class="sxs-lookup"><span data-stu-id="99c11-112">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target member is imported.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="99c11-113">[in]`mdTypeRef`或`mdModuleRef`語彙基元的類型或模組，分別擁有目標成員。</span><span class="sxs-lookup"><span data-stu-id="99c11-113">[in] The `mdTypeRef` or `mdModuleRef` token for the type or module, respectively, that owns the target member.</span></span>  
  
 `pmr`  
 <span data-ttu-id="99c11-114">[out]`mdMemberRef`成員參考目前範圍中定義的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="99c11-114">[out] The `mdMemberRef` token that is defined in the current scope for the member reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99c11-115">備註</span><span class="sxs-lookup"><span data-stu-id="99c11-115">Remarks</span></span>  
 <span data-ttu-id="99c11-116">`DefineImportMember`方法會查詢指定成員`mbMember`，也就是定義在另一個範圍內，由指定`pImport`，並擷取其屬性。</span><span class="sxs-lookup"><span data-stu-id="99c11-116">The `DefineImportMember` method looks up the member, specified by `mbMember`, that is defined in another scope, specified by `pImport`, and retrieves its properties.</span></span> <span data-ttu-id="99c11-117">它會使用此資訊來呼叫[imetadataemit:: Definememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)建立成員參考目前範圍中的方法。</span><span class="sxs-lookup"><span data-stu-id="99c11-117">It uses this information to call the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method in the current scope to create the member reference.</span></span>  
  
 <span data-ttu-id="99c11-118">一般而言，當您使用`DefineImportMember`方法，您必須建立，在目前範圍、 型別參考或目標成員的父類別、 介面或模組的模組參考。</span><span class="sxs-lookup"><span data-stu-id="99c11-118">Generally, before you use the `DefineImportMember` method, you must create, in the current scope, a type reference or module reference for the target member's parent class, interface, or module.</span></span> <span data-ttu-id="99c11-119">這個參考的中繼資料語彙基元然後傳入`tkParent`引數。</span><span class="sxs-lookup"><span data-stu-id="99c11-119">The metadata token for this reference is then passed in the `tkParent` argument.</span></span> <span data-ttu-id="99c11-120">您不需要建立目標成員的父代參考，如果它由編譯器或連結器將會稍後解決。</span><span class="sxs-lookup"><span data-stu-id="99c11-120">You do not need to create a reference to the target member's parent if it will be resolved later by the compiler or linker.</span></span> <span data-ttu-id="99c11-121">總括來說：</span><span class="sxs-lookup"><span data-stu-id="99c11-121">To summarize:</span></span>  
  
-   <span data-ttu-id="99c11-122">如果目標成員的欄位或方法，請使用  [imetadataemit:: Definetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md)或[imetadataemit:: Defineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)方法來建立型別參考，在目前範圍中，成員的父類別或父介面。</span><span class="sxs-lookup"><span data-stu-id="99c11-122">If the target member is a field or method, use either the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) or the [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
-   <span data-ttu-id="99c11-123">如果目標成員的全域變數或全域函式 （也就是不是成員的類別或介面），請使用[imetadataemit:: Definemoduleref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md)方法來建立模組參考，在目前範圍中，成員的父系模組。</span><span class="sxs-lookup"><span data-stu-id="99c11-123">If the target member is a global variable or global function (that is, not a member of a class or interface), use the [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) method to create a module reference, in the current scope, for the member's parent module.</span></span>  
  
-   <span data-ttu-id="99c11-124">如果將會由編譯器或連結器稍後解決目標成員的父系，則傳遞`mdTokenNil`中`tkParent`。</span><span class="sxs-lookup"><span data-stu-id="99c11-124">If the target member's parent will be resolved later by the compiler or linker, then pass `mdTokenNil` in `tkParent`.</span></span> <span data-ttu-id="99c11-125">僅限適用的案例是在全域函式或全域變數從最後會連結到目前模組的.obj 檔案匯入和中繼資料合併。</span><span class="sxs-lookup"><span data-stu-id="99c11-125">The only scenario in which this applies is when a global function or global variable is being imported from a .obj file that will ultimately be linked into the current module and the metadata merged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99c11-126">需求</span><span class="sxs-lookup"><span data-stu-id="99c11-126">Requirements</span></span>  
 <span data-ttu-id="99c11-127">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="99c11-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99c11-128">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="99c11-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="99c11-129">**程式庫：** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="99c11-129">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99c11-130">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99c11-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99c11-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99c11-131">See Also</span></span>  
 [<span data-ttu-id="99c11-132">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="99c11-132">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="99c11-133">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="99c11-133">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
