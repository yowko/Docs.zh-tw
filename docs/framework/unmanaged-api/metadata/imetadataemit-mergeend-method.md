---
title: "IMetaDataEmit::MergeEnd 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.MergeEnd
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::MergeEnd
helpviewer_keywords:
- MergeEnd method [.NET Framework metadata]
- IMetaDataEmit::MergeEnd method [.NET Framework metadata]
ms.assetid: 2d64315a-1af1-4c60-aedf-f8a781914aea
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 57fbecd05f0eaee48e9dc8a599e3174ac97033f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitmergeend-method"></a><span data-ttu-id="6a811-102">IMetaDataEmit::MergeEnd 方法</span><span class="sxs-lookup"><span data-stu-id="6a811-102">IMetaDataEmit::MergeEnd Method</span></span>
<span data-ttu-id="6a811-103">合併到目前範圍的一個或多個先前呼叫所指定的所有中繼資料範圍[imetadataemit:: Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)。</span><span class="sxs-lookup"><span data-stu-id="6a811-103">Merges into the current scope all the metadata scopes specified by one or more prior calls to [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a811-104">語法</span><span class="sxs-lookup"><span data-stu-id="6a811-104">Syntax</span></span>  
  
```  
HRESULT MergeEnd ();  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6a811-105">參數</span><span class="sxs-lookup"><span data-stu-id="6a811-105">Parameters</span></span>  
 <span data-ttu-id="6a811-106">這個方法會採用任何參數。</span><span class="sxs-lookup"><span data-stu-id="6a811-106">This method takes no parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a811-107">備註</span><span class="sxs-lookup"><span data-stu-id="6a811-107">Remarks</span></span>  
 <span data-ttu-id="6a811-108">這個常式會觸發實際的合併中繼資料，所有的匯入前的呼叫中指定的範圍`IMetaDataEmit::Merge`，到目前的輸出範圍。</span><span class="sxs-lookup"><span data-stu-id="6a811-108">This routine triggers the actual merge of metadata, of all import scopes specified by preceding calls to `IMetaDataEmit::Merge`, into the current output scope.</span></span>  
  
 <span data-ttu-id="6a811-109">下列的特殊情況適用於合併式：</span><span class="sxs-lookup"><span data-stu-id="6a811-109">The following special conditions apply to the merge:</span></span>  
  
-   <span data-ttu-id="6a811-110">模組版本識別項 (MVID) 永遠不會匯入，因為它是唯一的中繼資料匯入範圍中。</span><span class="sxs-lookup"><span data-stu-id="6a811-110">A module version identifier (MVID) is never imported, because it is unique to the metadata in the import scope.</span></span>  
  
-   <span data-ttu-id="6a811-111">會覆不寫任何現有的整個模組的屬性。</span><span class="sxs-lookup"><span data-stu-id="6a811-111">No existing module-wide properties are overwritten.</span></span>  
  
     <span data-ttu-id="6a811-112">如果模組屬性已設定為目前的範圍，會匯不入任何模組的屬性。</span><span class="sxs-lookup"><span data-stu-id="6a811-112">If module properties were already set for the current scope, no module properties are imported.</span></span> <span data-ttu-id="6a811-113">不過，如果模組屬性尚未設定在目前範圍中，它們會匯入一次，當第一次遇到。</span><span class="sxs-lookup"><span data-stu-id="6a811-113">However, if module properties have not been set in the current scope, they are imported only once, when they are first encountered.</span></span> <span data-ttu-id="6a811-114">如果這些模組內容發生一次，它們是重複的項目。</span><span class="sxs-lookup"><span data-stu-id="6a811-114">If those module properties are encountered again, they are duplicates.</span></span> <span data-ttu-id="6a811-115">如果 （MVID 除外） 的所有模組屬性的值進行比較並發現沒有重複項目，則會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="6a811-115">If the values of all module properties (except MVID) are compared and no duplicates are found, an error is raised.</span></span>  
  
-   <span data-ttu-id="6a811-116">類型定義 (`TypeDef`)，沒有重複項目會合併到目前的範圍。</span><span class="sxs-lookup"><span data-stu-id="6a811-116">For type definitions (`TypeDef`), no duplicates are merged into the current scope.</span></span> <span data-ttu-id="6a811-117">`TypeDef`物件會檢查是否有重複項目針對每個*完整物件名稱* + *GUID* + *版本號碼*。</span><span class="sxs-lookup"><span data-stu-id="6a811-117">`TypeDef` objects are checked for duplicates against each *fully-qualified object name* + *GUID* + *version number*.</span></span> <span data-ttu-id="6a811-118">如果沒有符合項目名稱或 GUID，且任何其他兩個項目不同，則會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="6a811-118">If there is a match on either name or GUID, and any of the other two elements is different, an error is raised.</span></span> <span data-ttu-id="6a811-119">否則，如果所有的三個項目相符，`MergeEnd`未執行快速檢查，以確保項目確實是重複項目; 如果沒有，則會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="6a811-119">Otherwise, if all three items match, `MergeEnd` does a cursory check to ensure the entries are indeed duplicates; if not, an error is raised.</span></span> <span data-ttu-id="6a811-120">這項快速檢查會尋找：</span><span class="sxs-lookup"><span data-stu-id="6a811-120">This cursory check looks for:</span></span>  
  
    -   <span data-ttu-id="6a811-121">相同成員宣告中的相同順序發生。</span><span class="sxs-lookup"><span data-stu-id="6a811-121">The same member declarations, occurring in the same order.</span></span> <span data-ttu-id="6a811-122">成員標示為`mdPrivateScope`(請參閱[CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md)列舉型別) 中這項檢查; 不包含特殊合併。</span><span class="sxs-lookup"><span data-stu-id="6a811-122">Members that are flagged as `mdPrivateScope` (see the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration) are not included in this check; they are merged specially.</span></span>  
  
    -   <span data-ttu-id="6a811-123">相同的類別配置。</span><span class="sxs-lookup"><span data-stu-id="6a811-123">The same class layout.</span></span>  
  
     <span data-ttu-id="6a811-124">這表示`TypeDef`物件必須一律完整且一致地定義每個中繼資料範圍內宣告中，如果其成員的實作 （類別） 會橫跨多個編譯單位中，假設為完整定義每個範圍中存在且不增量至每個範圍。</span><span class="sxs-lookup"><span data-stu-id="6a811-124">This means that a `TypeDef` object must always be fully and consistently defined in every metadata scope in which it is declared; if its member implementations (for a class) are spread across multiple compilation units, the full definition is assumed to be present in every scope and not incremental to each scope.</span></span> <span data-ttu-id="6a811-125">比方說，如果參數名稱與合約相關，他們必須發出相同的方式納入每個範圍中。如果不相關，他們應該不發出至中繼資料。</span><span class="sxs-lookup"><span data-stu-id="6a811-125">For example, if parameter names are relevant to the contract, they must be emitted the same way into every scope; if they are not relevant, they should not be emitted into metadata.</span></span>  
  
     <span data-ttu-id="6a811-126">例外狀況是，`TypeDef`物件可以有標示為增量成員`mdPrivateScope`。</span><span class="sxs-lookup"><span data-stu-id="6a811-126">The exception is that a `TypeDef` object can have incremental members flagged as `mdPrivateScope`.</span></span> <span data-ttu-id="6a811-127">在發生時，這些項目，`MergeEnd`以累加方式將它們加入至目前的範圍，而不考慮重複項目。</span><span class="sxs-lookup"><span data-stu-id="6a811-127">On encountering these, `MergeEnd` incrementally adds them to the current scope without regard for duplicates.</span></span> <span data-ttu-id="6a811-128">由於編譯器了解私人範圍，編譯器必須負責強制執行規則。</span><span class="sxs-lookup"><span data-stu-id="6a811-128">Because the compiler understands the private scope, the compiler must be responsible for enforcing rules.</span></span>  
  
-   <span data-ttu-id="6a811-129">相對虛擬位址 (Rva) 不會匯入或合併。編譯器預期會重新發出這項資訊。</span><span class="sxs-lookup"><span data-stu-id="6a811-129">Relative virtual addresses (RVAs) are not imported or merged; the compiler is expected to re-emit this information.</span></span>  
  
-   <span data-ttu-id="6a811-130">自訂屬性合併只能附加至的項目會合併。</span><span class="sxs-lookup"><span data-stu-id="6a811-130">Custom attributes are merged only when the item to which they are attached is merged.</span></span> <span data-ttu-id="6a811-131">比方說，第一次遇到類別時，會合併類別相關聯的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="6a811-131">For example, custom attributes associated with a class are merged when the class is first encountered.</span></span> <span data-ttu-id="6a811-132">如果自訂屬性相關聯`TypeDef`或`MemberDef`專屬於編譯單位 （例如成員編譯的時間戳記），它們不會合併會決定移除或更新中繼資料，這類編譯器。</span><span class="sxs-lookup"><span data-stu-id="6a811-132">If custom attributes are associated with a `TypeDef` or `MemberDef` that is specific to the compilation unit (such as the time stamp of a member compile), they are not merged and it is up to the compiler to remove or update such metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a811-133">需求</span><span class="sxs-lookup"><span data-stu-id="6a811-133">Requirements</span></span>  
 <span data-ttu-id="6a811-134">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6a811-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a811-135">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6a811-135">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6a811-136">**程式庫：**做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6a811-136">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6a811-137">**.NET framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a811-137">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a811-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a811-138">See Also</span></span>  
 [<span data-ttu-id="6a811-139">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="6a811-139">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="6a811-140">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="6a811-140">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
