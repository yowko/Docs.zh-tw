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
# <a name="imetadataemitdefineimportmember-method"></a><span data-ttu-id="37134-102">IMetaDataEmit::DefineImportMember 方法</span><span class="sxs-lookup"><span data-stu-id="37134-102">IMetaDataEmit::DefineImportMember Method</span></span>

<span data-ttu-id="37134-103">建立在目前範圍之外定義之類型或模組之指定成員的參考，並定義該參考的標記。</span><span class="sxs-lookup"><span data-stu-id="37134-103">Creates a reference to the specified member of a type or module that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37134-104">語法</span><span class="sxs-lookup"><span data-stu-id="37134-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="37134-105">參數</span><span class="sxs-lookup"><span data-stu-id="37134-105">Parameters</span></span>  

 `pAssemImport`  
 <span data-ttu-id="37134-106">在 [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) 介面，表示要從中匯入目標成員的元件。</span><span class="sxs-lookup"><span data-stu-id="37134-106">[in] An [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) interface that represents the assembly from which the target member is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="37134-107">在陣列，其中包含所指定之元件的雜湊 `pAssemImport` 。</span><span class="sxs-lookup"><span data-stu-id="37134-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="37134-108">[in] `pbHashValue` 陣列中的位元組數。</span><span class="sxs-lookup"><span data-stu-id="37134-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="37134-109">在 [IMetaDataImport](imetadataimport-interface.md) 介面，表示要從中匯入目標成員的中繼資料範圍。</span><span class="sxs-lookup"><span data-stu-id="37134-109">[in] An [IMetaDataImport](imetadataimport-interface.md) interface that represents the metadata scope from which the target member is imported.</span></span>  
  
 `mbMember`  
 <span data-ttu-id="37134-110">在指定目標成員的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="37134-110">[in] The metadata token that specifies the target member.</span></span> <span data-ttu-id="37134-111">標記可以是 `mdMethodDef` 成員方法的 () 、 `mdProperty` 成員屬性) 的 (，或 `mdFieldDef` 成員欄位 (token 的) 。</span><span class="sxs-lookup"><span data-stu-id="37134-111">The token can be an `mdMethodDef` (for a member method), `mdProperty` (for a member property), or `mdFieldDef` (for a member field) token.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="37134-112">在 [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) 介面，表示要匯入目標成員的元件。</span><span class="sxs-lookup"><span data-stu-id="37134-112">[in] An [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) interface that represents the assembly into which the target member is imported.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="37134-113">在 `mdTypeRef` `mdModuleRef` 類型或模組的或標記，分別擁有目標成員。</span><span class="sxs-lookup"><span data-stu-id="37134-113">[in] The `mdTypeRef` or `mdModuleRef` token for the type or module, respectively, that owns the target member.</span></span>  
  
 `pmr`  
 <span data-ttu-id="37134-114">擴展 `mdMemberRef` 在成員參考的目前範圍中定義的標記。</span><span class="sxs-lookup"><span data-stu-id="37134-114">[out] The `mdMemberRef` token that is defined in the current scope for the member reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37134-115">備註</span><span class="sxs-lookup"><span data-stu-id="37134-115">Remarks</span></span>  

 <span data-ttu-id="37134-116">方法會查閱由指定的成員（由指定）， `DefineImportMember` `mbMember` 並抓取 `pImport` 其屬性。</span><span class="sxs-lookup"><span data-stu-id="37134-116">The `DefineImportMember` method looks up the member, specified by `mbMember`, that is defined in another scope, specified by `pImport`, and retrieves its properties.</span></span> <span data-ttu-id="37134-117">它會使用這項資訊來呼叫目前範圍中的 [IMetaDataEmit：:D efinememberref](imetadataemit-definememberref-method.md) 方法，以建立成員參考。</span><span class="sxs-lookup"><span data-stu-id="37134-117">It uses this information to call the [IMetaDataEmit::DefineMemberRef](imetadataemit-definememberref-method.md) method in the current scope to create the member reference.</span></span>  
  
 <span data-ttu-id="37134-118">一般來說，在使用方法之前， `DefineImportMember` 您必須在目前的範圍中建立目標成員之父類別、介面或模組的型別參考或模組參考。</span><span class="sxs-lookup"><span data-stu-id="37134-118">Generally, before you use the `DefineImportMember` method, you must create, in the current scope, a type reference or module reference for the target member's parent class, interface, or module.</span></span> <span data-ttu-id="37134-119">然後，會在引數中傳遞此參考的元資料標記 `tkParent` 。</span><span class="sxs-lookup"><span data-stu-id="37134-119">The metadata token for this reference is then passed in the `tkParent` argument.</span></span> <span data-ttu-id="37134-120">如果編譯器或連結器稍後將會解決，您就不需要建立目標成員父系的參考。</span><span class="sxs-lookup"><span data-stu-id="37134-120">You do not need to create a reference to the target member's parent if it will be resolved later by the compiler or linker.</span></span> <span data-ttu-id="37134-121">總括來說：</span><span class="sxs-lookup"><span data-stu-id="37134-121">To summarize:</span></span>  
  
- <span data-ttu-id="37134-122">如果目標成員是欄位或方法，請使用 [IMetaDataEmit：:D efinetyperefbyname](imetadataemit-definetyperefbyname-method.md) 或 [IMetaDataEmit：:D efineimporttype](imetadataemit-defineimporttype-method.md) 方法，在目前的範圍中，為成員的父類別或父介面建立型別參考。</span><span class="sxs-lookup"><span data-stu-id="37134-122">If the target member is a field or method, use either the [IMetaDataEmit::DefineTypeRefByName](imetadataemit-definetyperefbyname-method.md) or the [IMetaDataEmit::DefineImportType](imetadataemit-defineimporttype-method.md) method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
- <span data-ttu-id="37134-123">如果目標成員是全域變數或全域函式 (也就是，而不是) 類別或介面的成員，請使用 [IMetaDataEmit：:D efinemoduleref](imetadataemit-definemoduleref-method.md) 方法，在目前的範圍中建立成員父模組的模組參考。</span><span class="sxs-lookup"><span data-stu-id="37134-123">If the target member is a global variable or global function (that is, not a member of a class or interface), use the [IMetaDataEmit::DefineModuleRef](imetadataemit-definemoduleref-method.md) method to create a module reference, in the current scope, for the member's parent module.</span></span>  
  
- <span data-ttu-id="37134-124">如果編譯器或連結器稍後將解析目標成員的父系，則傳入 `mdTokenNil` `tkParent` 。</span><span class="sxs-lookup"><span data-stu-id="37134-124">If the target member's parent will be resolved later by the compiler or linker, then pass `mdTokenNil` in `tkParent`.</span></span> <span data-ttu-id="37134-125">唯一適用的情況是，當從 .obj 檔案匯入全域函式或全域變數時，最後會連結到目前的模組，併合並中繼資料。</span><span class="sxs-lookup"><span data-stu-id="37134-125">The only scenario in which this applies is when a global function or global variable is being imported from a .obj file that will ultimately be linked into the current module and the metadata merged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37134-126">需求</span><span class="sxs-lookup"><span data-stu-id="37134-126">Requirements</span></span>  

 <span data-ttu-id="37134-127">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="37134-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37134-128">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="37134-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="37134-129">連結 **庫：** 當做 MSCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="37134-129">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="37134-130">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37134-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37134-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37134-131">See also</span></span>

- [<span data-ttu-id="37134-132">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="37134-132">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="37134-133">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="37134-133">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
