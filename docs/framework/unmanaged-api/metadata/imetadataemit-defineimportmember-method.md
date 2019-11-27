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
ms.openlocfilehash: 75711b3d87699ff5db21a04351ff0acaccabb5aa
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431866"
---
# <a name="imetadataemitdefineimportmember-method"></a><span data-ttu-id="34765-102">IMetaDataEmit::DefineImportMember 方法</span><span class="sxs-lookup"><span data-stu-id="34765-102">IMetaDataEmit::DefineImportMember Method</span></span>
<span data-ttu-id="34765-103">建立在目前範圍外定義之類型或模組之指定成員的參考，並定義該參考的 token。</span><span class="sxs-lookup"><span data-stu-id="34765-103">Creates a reference to the specified member of a type or module that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34765-104">語法</span><span class="sxs-lookup"><span data-stu-id="34765-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="34765-105">參數</span><span class="sxs-lookup"><span data-stu-id="34765-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="34765-106">在[IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)介面，表示從中匯入目標成員的元件。</span><span class="sxs-lookup"><span data-stu-id="34765-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target member is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="34765-107">在陣列，其中包含 `pAssemImport`所指定之元件的雜湊。</span><span class="sxs-lookup"><span data-stu-id="34765-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="34765-108">[in] `pbHashValue` 陣列中的位元組數。</span><span class="sxs-lookup"><span data-stu-id="34765-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="34765-109">在[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)介面，表示要從中匯入目標成員的中繼資料範圍。</span><span class="sxs-lookup"><span data-stu-id="34765-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target member is imported.</span></span>  
  
 `mbMember`  
 <span data-ttu-id="34765-110">在指定目標成員的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="34765-110">[in] The metadata token that specifies the target member.</span></span> <span data-ttu-id="34765-111">Token 可以是 `mdMethodDef` （針對成員方法）、`mdProperty` （針對成員屬性），或 `mdFieldDef` （針對成員欄位） token。</span><span class="sxs-lookup"><span data-stu-id="34765-111">The token can be an `mdMethodDef` (for a member method), `mdProperty` (for a member property), or `mdFieldDef` (for a member field) token.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="34765-112">在[IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)介面，表示要匯入目標成員的元件。</span><span class="sxs-lookup"><span data-stu-id="34765-112">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target member is imported.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="34765-113">在分別擁有目標成員之類型或模組的 `mdTypeRef` 或 `mdModuleRef` token。</span><span class="sxs-lookup"><span data-stu-id="34765-113">[in] The `mdTypeRef` or `mdModuleRef` token for the type or module, respectively, that owns the target member.</span></span>  
  
 `pmr`  
 <span data-ttu-id="34765-114">脫銷在成員參考的目前範圍中定義的 `mdMemberRef` token。</span><span class="sxs-lookup"><span data-stu-id="34765-114">[out] The `mdMemberRef` token that is defined in the current scope for the member reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34765-115">備註</span><span class="sxs-lookup"><span data-stu-id="34765-115">Remarks</span></span>  
 <span data-ttu-id="34765-116">`DefineImportMember` 方法會查閱由 `mbMember`指定的成員（由 `pImport`指定的其他範圍），並抓取其屬性。</span><span class="sxs-lookup"><span data-stu-id="34765-116">The `DefineImportMember` method looks up the member, specified by `mbMember`, that is defined in another scope, specified by `pImport`, and retrieves its properties.</span></span> <span data-ttu-id="34765-117">它會使用這項資訊來呼叫目前範圍中的[IMetaDataEmit：:D efinememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)方法，以建立成員參考。</span><span class="sxs-lookup"><span data-stu-id="34765-117">It uses this information to call the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method in the current scope to create the member reference.</span></span>  
  
 <span data-ttu-id="34765-118">一般來說，在您使用 `DefineImportMember` 方法之前，您必須先在目前的範圍中建立目標成員之父類別、介面或模組的類型參考或模組參考。</span><span class="sxs-lookup"><span data-stu-id="34765-118">Generally, before you use the `DefineImportMember` method, you must create, in the current scope, a type reference or module reference for the target member's parent class, interface, or module.</span></span> <span data-ttu-id="34765-119">然後會在 `tkParent` 引數中傳遞此參考的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="34765-119">The metadata token for this reference is then passed in the `tkParent` argument.</span></span> <span data-ttu-id="34765-120">如果目標成員的父系稍後將由編譯器或連結器解析，您就不需要建立該參考。</span><span class="sxs-lookup"><span data-stu-id="34765-120">You do not need to create a reference to the target member's parent if it will be resolved later by the compiler or linker.</span></span> <span data-ttu-id="34765-121">總結來說：</span><span class="sxs-lookup"><span data-stu-id="34765-121">To summarize:</span></span>  
  
- <span data-ttu-id="34765-122">如果目標成員是欄位或方法，請使用[IMetaDataEmit：:D efinetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md)或[IMetaDataEmit：:D efineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)方法，針對成員的父類別或父介面，在目前的範圍中建立類型參考。</span><span class="sxs-lookup"><span data-stu-id="34765-122">If the target member is a field or method, use either the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) or the [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
- <span data-ttu-id="34765-123">如果目標成員是全域變數或全域函式（也就是，而不是類別或介面的成員），請使用[IMetaDataEmit：:D efinemoduleref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md)方法，在目前的範圍中，為成員的父模組建立模組參考。</span><span class="sxs-lookup"><span data-stu-id="34765-123">If the target member is a global variable or global function (that is, not a member of a class or interface), use the [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) method to create a module reference, in the current scope, for the member's parent module.</span></span>  
  
- <span data-ttu-id="34765-124">如果稍後會由編譯器或連結器解析目標成員的父系，請在 `tkParent`中傳遞 `mdTokenNil`。</span><span class="sxs-lookup"><span data-stu-id="34765-124">If the target member's parent will be resolved later by the compiler or linker, then pass `mdTokenNil` in `tkParent`.</span></span> <span data-ttu-id="34765-125">只有當全域函式或全域變數是從 .obj 檔案匯入，而此檔案最後會連結到目前的模組和合併的中繼資料時，才適用這種情況。</span><span class="sxs-lookup"><span data-stu-id="34765-125">The only scenario in which this applies is when a global function or global variable is being imported from a .obj file that will ultimately be linked into the current module and the metadata merged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34765-126">需求</span><span class="sxs-lookup"><span data-stu-id="34765-126">Requirements</span></span>  
 <span data-ttu-id="34765-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="34765-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34765-128">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="34765-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="34765-129">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="34765-129">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="34765-130">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34765-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34765-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34765-131">See also</span></span>

- [<span data-ttu-id="34765-132">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="34765-132">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="34765-133">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="34765-133">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
