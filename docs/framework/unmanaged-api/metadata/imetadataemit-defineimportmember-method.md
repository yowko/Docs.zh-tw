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
ms.openlocfilehash: ec8a24251ac4f0701b1adab19829078270229ced
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004591"
---
# <a name="imetadataemitdefineimportmember-method"></a><span data-ttu-id="60dac-102">IMetaDataEmit::DefineImportMember 方法</span><span class="sxs-lookup"><span data-stu-id="60dac-102">IMetaDataEmit::DefineImportMember Method</span></span>
<span data-ttu-id="60dac-103">建立在目前範圍外定義之類型或模組之指定成員的參考，並定義該參考的 token。</span><span class="sxs-lookup"><span data-stu-id="60dac-103">Creates a reference to the specified member of a type or module that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60dac-104">語法</span><span class="sxs-lookup"><span data-stu-id="60dac-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="60dac-105">參數</span><span class="sxs-lookup"><span data-stu-id="60dac-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="60dac-106">在[IMetaDataAssemblyImport](imetadataassemblyimport-interface.md)介面，表示從中匯入目標成員的元件。</span><span class="sxs-lookup"><span data-stu-id="60dac-106">[in] An [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) interface that represents the assembly from which the target member is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="60dac-107">在陣列，其中包含所指定之元件的雜湊 `pAssemImport` 。</span><span class="sxs-lookup"><span data-stu-id="60dac-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="60dac-108">[in] `pbHashValue` 陣列中的位元組數。</span><span class="sxs-lookup"><span data-stu-id="60dac-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="60dac-109">在[IMetaDataImport](imetadataimport-interface.md)介面，表示要從中匯入目標成員的中繼資料範圍。</span><span class="sxs-lookup"><span data-stu-id="60dac-109">[in] An [IMetaDataImport](imetadataimport-interface.md) interface that represents the metadata scope from which the target member is imported.</span></span>  
  
 `mbMember`  
 <span data-ttu-id="60dac-110">在指定目標成員的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="60dac-110">[in] The metadata token that specifies the target member.</span></span> <span data-ttu-id="60dac-111">Token 可以是 `mdMethodDef` （針對成員方法）、 `mdProperty` （針對成員屬性），或 `mdFieldDef` （針對成員欄位） token。</span><span class="sxs-lookup"><span data-stu-id="60dac-111">The token can be an `mdMethodDef` (for a member method), `mdProperty` (for a member property), or `mdFieldDef` (for a member field) token.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="60dac-112">在[IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md)介面，表示要匯入目標成員的元件。</span><span class="sxs-lookup"><span data-stu-id="60dac-112">[in] An [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) interface that represents the assembly into which the target member is imported.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="60dac-113">在`mdTypeRef` `mdModuleRef` 分別擁有目標成員之類型或模組的或 token。</span><span class="sxs-lookup"><span data-stu-id="60dac-113">[in] The `mdTypeRef` or `mdModuleRef` token for the type or module, respectively, that owns the target member.</span></span>  
  
 `pmr`  
 <span data-ttu-id="60dac-114">脫銷`mdMemberRef`在成員參考的目前範圍中定義的 token。</span><span class="sxs-lookup"><span data-stu-id="60dac-114">[out] The `mdMemberRef` token that is defined in the current scope for the member reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60dac-115">備註</span><span class="sxs-lookup"><span data-stu-id="60dac-115">Remarks</span></span>  
 <span data-ttu-id="60dac-116">`DefineImportMember`方法會查閱由指定的成員， `mbMember` 其定義于另一個範圍中，由指定 `pImport` ，並抓取其屬性。</span><span class="sxs-lookup"><span data-stu-id="60dac-116">The `DefineImportMember` method looks up the member, specified by `mbMember`, that is defined in another scope, specified by `pImport`, and retrieves its properties.</span></span> <span data-ttu-id="60dac-117">它會使用這項資訊來呼叫目前範圍中的[IMetaDataEmit：:D efinememberref](imetadataemit-definememberref-method.md)方法，以建立成員參考。</span><span class="sxs-lookup"><span data-stu-id="60dac-117">It uses this information to call the [IMetaDataEmit::DefineMemberRef](imetadataemit-definememberref-method.md) method in the current scope to create the member reference.</span></span>  
  
 <span data-ttu-id="60dac-118">一般來說，在您使用 `DefineImportMember` 方法之前，您必須先在目前的範圍中建立目標成員之父類別、介面或模組的類型參考或模組參考。</span><span class="sxs-lookup"><span data-stu-id="60dac-118">Generally, before you use the `DefineImportMember` method, you must create, in the current scope, a type reference or module reference for the target member's parent class, interface, or module.</span></span> <span data-ttu-id="60dac-119">然後會在引數中傳遞此參考的元資料標記 `tkParent` 。</span><span class="sxs-lookup"><span data-stu-id="60dac-119">The metadata token for this reference is then passed in the `tkParent` argument.</span></span> <span data-ttu-id="60dac-120">如果目標成員的父系稍後將由編譯器或連結器解析，您就不需要建立該參考。</span><span class="sxs-lookup"><span data-stu-id="60dac-120">You do not need to create a reference to the target member's parent if it will be resolved later by the compiler or linker.</span></span> <span data-ttu-id="60dac-121">總括來說：</span><span class="sxs-lookup"><span data-stu-id="60dac-121">To summarize:</span></span>  
  
- <span data-ttu-id="60dac-122">如果目標成員是欄位或方法，請使用[IMetaDataEmit：:D efinetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md)或[IMetaDataEmit：:D efineimporttype](imetadataemit-defineimporttype-method.md)方法，針對成員的父類別或父介面，在目前的範圍中建立類型參考。</span><span class="sxs-lookup"><span data-stu-id="60dac-122">If the target member is a field or method, use either the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) or the [IMetaDataEmit::DefineImportType](imetadataemit-defineimporttype-method.md) method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
- <span data-ttu-id="60dac-123">如果目標成員是全域變數或全域函式（也就是，而不是類別或介面的成員），請使用[IMetaDataEmit：:D efinemoduleref](imetadataemit-definemoduleref-method.md)方法，在目前的範圍中，為成員的父模組建立模組參考。</span><span class="sxs-lookup"><span data-stu-id="60dac-123">If the target member is a global variable or global function (that is, not a member of a class or interface), use the [IMetaDataEmit::DefineModuleRef](imetadataemit-definemoduleref-method.md) method to create a module reference, in the current scope, for the member's parent module.</span></span>  
  
- <span data-ttu-id="60dac-124">如果稍後會由編譯器或連結器解析目標成員的父系，則請傳入 `mdTokenNil` `tkParent` 。</span><span class="sxs-lookup"><span data-stu-id="60dac-124">If the target member's parent will be resolved later by the compiler or linker, then pass `mdTokenNil` in `tkParent`.</span></span> <span data-ttu-id="60dac-125">只有當全域函式或全域變數是從 .obj 檔案匯入，而此檔案最後會連結到目前的模組和合併的中繼資料時，才適用這種情況。</span><span class="sxs-lookup"><span data-stu-id="60dac-125">The only scenario in which this applies is when a global function or global variable is being imported from a .obj file that will ultimately be linked into the current module and the metadata merged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60dac-126">需求</span><span class="sxs-lookup"><span data-stu-id="60dac-126">Requirements</span></span>  
 <span data-ttu-id="60dac-127">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="60dac-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60dac-128">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="60dac-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="60dac-129">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="60dac-129">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="60dac-130">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60dac-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60dac-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60dac-131">See also</span></span>

- [<span data-ttu-id="60dac-132">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="60dac-132">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="60dac-133">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="60dac-133">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
