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
# <a name="imetadataemitdefineimportmember-method"></a><span data-ttu-id="a74b6-102">IMetaDataEmit::DefineImportMember 方法</span><span class="sxs-lookup"><span data-stu-id="a74b6-102">IMetaDataEmit::DefineImportMember Method</span></span>
<span data-ttu-id="a74b6-103">創建對在當前作用域之外定義的類型或模組的指定成員的引用，並為該引用定義權杖。</span><span class="sxs-lookup"><span data-stu-id="a74b6-103">Creates a reference to the specified member of a type or module that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a74b6-104">語法</span><span class="sxs-lookup"><span data-stu-id="a74b6-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="a74b6-105">參數</span><span class="sxs-lookup"><span data-stu-id="a74b6-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="a74b6-106">[在][IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)，表示從中導入目標成員的程式集。</span><span class="sxs-lookup"><span data-stu-id="a74b6-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target member is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="a74b6-107">[在]包含 的陣列，其中包含 由 指定的`pAssemImport`程式集的雜湊值。</span><span class="sxs-lookup"><span data-stu-id="a74b6-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="a74b6-108">[in] `pbHashValue` 陣列中的位元組數。</span><span class="sxs-lookup"><span data-stu-id="a74b6-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="a74b6-109">[在][IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)介面，表示從中導入目標成員的中繼資料範圍。</span><span class="sxs-lookup"><span data-stu-id="a74b6-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target member is imported.</span></span>  
  
 `mbMember`  
 <span data-ttu-id="a74b6-110">[在]指定目標成員的中繼資料權杖。</span><span class="sxs-lookup"><span data-stu-id="a74b6-110">[in] The metadata token that specifies the target member.</span></span> <span data-ttu-id="a74b6-111">權杖可以是`mdMethodDef`（對於成員方法）、（`mdProperty`對於成員屬性）或`mdFieldDef`（對於成員欄位）的權杖。</span><span class="sxs-lookup"><span data-stu-id="a74b6-111">The token can be an `mdMethodDef` (for a member method), `mdProperty` (for a member property), or `mdFieldDef` (for a member field) token.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="a74b6-112">[在][IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)介面，表示將目標成員導入到的程式集。</span><span class="sxs-lookup"><span data-stu-id="a74b6-112">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target member is imported.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="a74b6-113">[在]分別`mdTypeRef`擁有`mdModuleRef`目標成員的類型或模組的 或 權杖。</span><span class="sxs-lookup"><span data-stu-id="a74b6-113">[in] The `mdTypeRef` or `mdModuleRef` token for the type or module, respectively, that owns the target member.</span></span>  
  
 `pmr`  
 <span data-ttu-id="a74b6-114">[出]在`mdMemberRef`成員引用的當前作用域中定義的權杖。</span><span class="sxs-lookup"><span data-stu-id="a74b6-114">[out] The `mdMemberRef` token that is defined in the current scope for the member reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a74b6-115">備註</span><span class="sxs-lookup"><span data-stu-id="a74b6-115">Remarks</span></span>  
 <span data-ttu-id="a74b6-116">方法`DefineImportMember`查找由`mbMember`指定的成員，該成員在由 指定的另一個作用域中定義`pImport`，由 指定並檢索其屬性。</span><span class="sxs-lookup"><span data-stu-id="a74b6-116">The `DefineImportMember` method looks up the member, specified by `mbMember`, that is defined in another scope, specified by `pImport`, and retrieves its properties.</span></span> <span data-ttu-id="a74b6-117">它使用此資訊調用當前作用域中的[IMetaDataEmit：:Define會員Ref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)方法來創建成員引用。</span><span class="sxs-lookup"><span data-stu-id="a74b6-117">It uses this information to call the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method in the current scope to create the member reference.</span></span>  
  
 <span data-ttu-id="a74b6-118">通常，在使用`DefineImportMember`方法之前，必須在當前作用域中為目標成員的父類、介面或模組創建類型引用或模組引用。</span><span class="sxs-lookup"><span data-stu-id="a74b6-118">Generally, before you use the `DefineImportMember` method, you must create, in the current scope, a type reference or module reference for the target member's parent class, interface, or module.</span></span> <span data-ttu-id="a74b6-119">然後，在參數中傳遞此引用的`tkParent`中繼資料權杖。</span><span class="sxs-lookup"><span data-stu-id="a74b6-119">The metadata token for this reference is then passed in the `tkParent` argument.</span></span> <span data-ttu-id="a74b6-120">如果編譯器或連結器稍後將解析目標成員的父項，則無需創建對目標成員的父項的引用。</span><span class="sxs-lookup"><span data-stu-id="a74b6-120">You do not need to create a reference to the target member's parent if it will be resolved later by the compiler or linker.</span></span> <span data-ttu-id="a74b6-121">總結：</span><span class="sxs-lookup"><span data-stu-id="a74b6-121">To summarize:</span></span>  
  
- <span data-ttu-id="a74b6-122">如果目標成員是欄位或方法，請使用[IMetaDataEmit：:DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md)或[IMetaDataEmit：:DefineImportType 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)，為成員的父類或父介面在當前作用域中創建類型引用。</span><span class="sxs-lookup"><span data-stu-id="a74b6-122">If the target member is a field or method, use either the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) or the [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
- <span data-ttu-id="a74b6-123">如果目標成員是全域變數或全域函數（即不是類或介面的成員），請使用[IMetaDataEmit：:DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md)方法為成員的父模組在當前作用域中創建模組引用。</span><span class="sxs-lookup"><span data-stu-id="a74b6-123">If the target member is a global variable or global function (that is, not a member of a class or interface), use the [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) method to create a module reference, in the current scope, for the member's parent module.</span></span>  
  
- <span data-ttu-id="a74b6-124">如果稍後編譯器或連結器將解析目標成員的父成員的父級，則將傳遞`mdTokenNil``tkParent`。</span><span class="sxs-lookup"><span data-stu-id="a74b6-124">If the target member's parent will be resolved later by the compiler or linker, then pass `mdTokenNil` in `tkParent`.</span></span> <span data-ttu-id="a74b6-125">唯一適用這種情況的情況是，全域函數或全域變數從 .obj 檔導入，該檔最終將連結到當前模組併合並中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a74b6-125">The only scenario in which this applies is when a global function or global variable is being imported from a .obj file that will ultimately be linked into the current module and the metadata merged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a74b6-126">需求</span><span class="sxs-lookup"><span data-stu-id="a74b6-126">Requirements</span></span>  
 <span data-ttu-id="a74b6-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a74b6-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a74b6-128">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="a74b6-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a74b6-129">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a74b6-129">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a74b6-130">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a74b6-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a74b6-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a74b6-131">See also</span></span>

- [<span data-ttu-id="a74b6-132">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="a74b6-132">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="a74b6-133">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="a74b6-133">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
