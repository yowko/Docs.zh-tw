---
title: IMetaDataEmit::MergeEnd 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.MergeEnd
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::MergeEnd
helpviewer_keywords:
- MergeEnd method [.NET Framework metadata]
- IMetaDataEmit::MergeEnd method [.NET Framework metadata]
ms.assetid: 2d64315a-1af1-4c60-aedf-f8a781914aea
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 45d85be4e4987e5a5234ca2d57c85a56f9f544bc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54657021"
---
# <a name="imetadataemitmergeend-method"></a><span data-ttu-id="2a599-102">IMetaDataEmit::MergeEnd 方法</span><span class="sxs-lookup"><span data-stu-id="2a599-102">IMetaDataEmit::MergeEnd Method</span></span>
<span data-ttu-id="2a599-103">合併到目前的範圍由一或多個先前的呼叫，以指定的所有中繼資料領域[imetadataemit:: Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)。</span><span class="sxs-lookup"><span data-stu-id="2a599-103">Merges into the current scope all the metadata scopes specified by one or more prior calls to [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a599-104">語法</span><span class="sxs-lookup"><span data-stu-id="2a599-104">Syntax</span></span>  
  
```  
HRESULT MergeEnd ();  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2a599-105">參數</span><span class="sxs-lookup"><span data-stu-id="2a599-105">Parameters</span></span>  
 <span data-ttu-id="2a599-106">這個方法會接受任何參數。</span><span class="sxs-lookup"><span data-stu-id="2a599-106">This method takes no parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a599-107">備註</span><span class="sxs-lookup"><span data-stu-id="2a599-107">Remarks</span></span>  
 <span data-ttu-id="2a599-108">這個常式會觸發實際的合併中繼資料，所有匯入指定的方法是呼叫範圍`IMetaDataEmit::Merge`，到目前的輸出範圍。</span><span class="sxs-lookup"><span data-stu-id="2a599-108">This routine triggers the actual merge of metadata, of all import scopes specified by preceding calls to `IMetaDataEmit::Merge`, into the current output scope.</span></span>  
  
 <span data-ttu-id="2a599-109">合併，適用下列的特殊狀況：</span><span class="sxs-lookup"><span data-stu-id="2a599-109">The following special conditions apply to the merge:</span></span>  
  
-   <span data-ttu-id="2a599-110">模組版本識別項 （mvid） 發生會永遠不會匯入，因為它是唯一的中繼資料匯入範圍中。</span><span class="sxs-lookup"><span data-stu-id="2a599-110">A module version identifier (MVID) is never imported, because it is unique to the metadata in the import scope.</span></span>  
  
-   <span data-ttu-id="2a599-111">會覆不寫任何現有的整個模組的屬性。</span><span class="sxs-lookup"><span data-stu-id="2a599-111">No existing module-wide properties are overwritten.</span></span>  
  
     <span data-ttu-id="2a599-112">如果模組屬性已設定為目前的範圍，則會匯不入任何模組屬性。</span><span class="sxs-lookup"><span data-stu-id="2a599-112">If module properties were already set for the current scope, no module properties are imported.</span></span> <span data-ttu-id="2a599-113">不過，如果模組屬性尚未設定目前範圍中，它們會匯入一次，當他們第一次發生。</span><span class="sxs-lookup"><span data-stu-id="2a599-113">However, if module properties have not been set in the current scope, they are imported only once, when they are first encountered.</span></span> <span data-ttu-id="2a599-114">如果這些模組內容發生一次，它們是重複的項目。</span><span class="sxs-lookup"><span data-stu-id="2a599-114">If those module properties are encountered again, they are duplicates.</span></span> <span data-ttu-id="2a599-115">如果 （MVID) 除外的所有模組屬性的值進行比較，而且沒有重複項目找到，則會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="2a599-115">If the values of all module properties (except MVID) are compared and no duplicates are found, an error is raised.</span></span>  
  
-   <span data-ttu-id="2a599-116">如需類型定義 (`TypeDef`)，沒有重複項目會合併到目前的範圍。</span><span class="sxs-lookup"><span data-stu-id="2a599-116">For type definitions (`TypeDef`), no duplicates are merged into the current scope.</span></span> <span data-ttu-id="2a599-117">`TypeDef` 物件會檢查是否有重複項目，針對每個*完整物件名稱* + *GUID* + *版本號碼*。</span><span class="sxs-lookup"><span data-stu-id="2a599-117">`TypeDef` objects are checked for duplicates against each *fully-qualified object name* + *GUID* + *version number*.</span></span> <span data-ttu-id="2a599-118">如果沒有相符項目名稱或 GUID，而且有任何其他兩個項目不同，則會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="2a599-118">If there is a match on either name or GUID, and any of the other two elements is different, an error is raised.</span></span> <span data-ttu-id="2a599-119">否則，如果所有的三個項目相符，`MergeEnd`粗略的檢查，以確保項目確實是在重複的項目; 如果沒有，則會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="2a599-119">Otherwise, if all three items match, `MergeEnd` does a cursory check to ensure the entries are indeed duplicates; if not, an error is raised.</span></span> <span data-ttu-id="2a599-120">這項快速檢查會尋找：</span><span class="sxs-lookup"><span data-stu-id="2a599-120">This cursory check looks for:</span></span>  
  
    -   <span data-ttu-id="2a599-121">同一個成員宣告，以相同的順序發生。</span><span class="sxs-lookup"><span data-stu-id="2a599-121">The same member declarations, occurring in the same order.</span></span> <span data-ttu-id="2a599-122">標示為的成員`mdPrivateScope`(請參閱 < [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md)列舉型別) 中這項檢查; 不包含特殊合併。</span><span class="sxs-lookup"><span data-stu-id="2a599-122">Members that are flagged as `mdPrivateScope` (see the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration) are not included in this check; they are merged specially.</span></span>  
  
    -   <span data-ttu-id="2a599-123">相同的類別配置。</span><span class="sxs-lookup"><span data-stu-id="2a599-123">The same class layout.</span></span>  
  
     <span data-ttu-id="2a599-124">這表示`TypeDef`物件必須一律完整且一致地定義每個中繼資料範圍內宣告中，如果其成員的實作 （類別） 會分散到多個編譯單位中，完整的定義假設為每個範圍中存在且不增量至每個範圍。</span><span class="sxs-lookup"><span data-stu-id="2a599-124">This means that a `TypeDef` object must always be fully and consistently defined in every metadata scope in which it is declared; if its member implementations (for a class) are spread across multiple compilation units, the full definition is assumed to be present in every scope and not incremental to each scope.</span></span> <span data-ttu-id="2a599-125">比方說，如果參數名稱與合約相關，它們必須發出相同的方式為每個範圍中，如果它們不相關，它們應該不發出至中繼資料。</span><span class="sxs-lookup"><span data-stu-id="2a599-125">For example, if parameter names are relevant to the contract, they must be emitted the same way into every scope; if they are not relevant, they should not be emitted into metadata.</span></span>  
  
     <span data-ttu-id="2a599-126">例外狀況是，`TypeDef`物件可以有標示為增量成員`mdPrivateScope`。</span><span class="sxs-lookup"><span data-stu-id="2a599-126">The exception is that a `TypeDef` object can have incremental members flagged as `mdPrivateScope`.</span></span> <span data-ttu-id="2a599-127">在發生這些`MergeEnd`以累加方式將它們新增至目前的範圍，而不必考慮重複項目。</span><span class="sxs-lookup"><span data-stu-id="2a599-127">On encountering these, `MergeEnd` incrementally adds them to the current scope without regard for duplicates.</span></span> <span data-ttu-id="2a599-128">因為編譯器了解私用範圍，編譯器必須負責強制執行規則。</span><span class="sxs-lookup"><span data-stu-id="2a599-128">Because the compiler understands the private scope, the compiler must be responsible for enforcing rules.</span></span>  
  
-   <span data-ttu-id="2a599-129">未匯入或合併; 相對虛擬位址 (Rva)編譯器應該重新發出這項資訊。</span><span class="sxs-lookup"><span data-stu-id="2a599-129">Relative virtual addresses (RVAs) are not imported or merged; the compiler is expected to re-emit this information.</span></span>  
  
-   <span data-ttu-id="2a599-130">只有在所連接的項目合併時，才合併自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="2a599-130">Custom attributes are merged only when the item to which they are attached is merged.</span></span> <span data-ttu-id="2a599-131">比方說，第一次遇到類別時，會合併與類別相關聯的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="2a599-131">For example, custom attributes associated with a class are merged when the class is first encountered.</span></span> <span data-ttu-id="2a599-132">如果自訂屬性相關聯`TypeDef`或`MemberDef`專屬於編譯單位 （例如將成員編譯的時間戳記），它們不會合併，將由編譯器移除或更新這類中繼資料。</span><span class="sxs-lookup"><span data-stu-id="2a599-132">If custom attributes are associated with a `TypeDef` or `MemberDef` that is specific to the compilation unit (such as the time stamp of a member compile), they are not merged and it is up to the compiler to remove or update such metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a599-133">需求</span><span class="sxs-lookup"><span data-stu-id="2a599-133">Requirements</span></span>  
 <span data-ttu-id="2a599-134">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2a599-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a599-135">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2a599-135">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2a599-136">**程式庫：** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2a599-136">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2a599-137">**.NET framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a599-137">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a599-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a599-138">See also</span></span>
- [<span data-ttu-id="2a599-139">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="2a599-139">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="2a599-140">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="2a599-140">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
