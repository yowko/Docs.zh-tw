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
ms.openlocfilehash: feb81b86190f953b50f43f244f4e58a0a482f86e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003915"
---
# <a name="imetadataemitmergeend-method"></a><span data-ttu-id="4090b-102">IMetaDataEmit::MergeEnd 方法</span><span class="sxs-lookup"><span data-stu-id="4090b-102">IMetaDataEmit::MergeEnd Method</span></span>

<span data-ttu-id="4090b-103">將一個或多個先前呼叫[IMetaDataEmit：： Merge](imetadataemit-merge-method.md)所指定的所有中繼資料範圍合併到目前的範圍。</span><span class="sxs-lookup"><span data-stu-id="4090b-103">Merges into the current scope all the metadata scopes specified by one or more prior calls to [IMetaDataEmit::Merge](imetadataemit-merge-method.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="4090b-104">語法</span><span class="sxs-lookup"><span data-stu-id="4090b-104">Syntax</span></span>

```cppcpp
HRESULT MergeEnd ();
```

## <a name="parameters"></a><span data-ttu-id="4090b-105">參數</span><span class="sxs-lookup"><span data-stu-id="4090b-105">Parameters</span></span>

<span data-ttu-id="4090b-106">這個方法不接受任何參數。</span><span class="sxs-lookup"><span data-stu-id="4090b-106">This method takes no parameters.</span></span>

## <a name="remarks"></a><span data-ttu-id="4090b-107">備註</span><span class="sxs-lookup"><span data-stu-id="4090b-107">Remarks</span></span>

<span data-ttu-id="4090b-108">此常式會將先前呼叫所指定的所有匯入範圍之中繼資料的實際合併，觸發 `IMetaDataEmit::Merge` 至目前的輸出範圍。</span><span class="sxs-lookup"><span data-stu-id="4090b-108">This routine triggers the actual merge of metadata, of all import scopes specified by preceding calls to `IMetaDataEmit::Merge`, into the current output scope.</span></span>

<span data-ttu-id="4090b-109">下列特殊條件適用于合併：</span><span class="sxs-lookup"><span data-stu-id="4090b-109">The following special conditions apply to the merge:</span></span>

- <span data-ttu-id="4090b-110">模組版本識別碼（MVID）永遠不會匯入，因為它對匯入範圍中的中繼資料是唯一的。</span><span class="sxs-lookup"><span data-stu-id="4090b-110">A module version identifier (MVID) is never imported, because it is unique to the metadata in the import scope.</span></span>

- <span data-ttu-id="4090b-111">不會覆寫任何現有的模組範圍屬性。</span><span class="sxs-lookup"><span data-stu-id="4090b-111">No existing module-wide properties are overwritten.</span></span>

  <span data-ttu-id="4090b-112">如果已針對目前的範圍設定模組屬性，則不會匯入任何模組屬性。</span><span class="sxs-lookup"><span data-stu-id="4090b-112">If module properties were already set for the current scope, no module properties are imported.</span></span> <span data-ttu-id="4090b-113">不過，如果目前的範圍內尚未設定模組屬性，則會在第一次遇到時匯入。</span><span class="sxs-lookup"><span data-stu-id="4090b-113">However, if module properties have not been set in the current scope, they are imported only once, when they are first encountered.</span></span> <span data-ttu-id="4090b-114">如果再次發現這些模組屬性，它們就是重複的。</span><span class="sxs-lookup"><span data-stu-id="4090b-114">If those module properties are encountered again, they are duplicates.</span></span> <span data-ttu-id="4090b-115">如果比較所有模組屬性（MVID 除外）的值，但找不到任何重複專案，就會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="4090b-115">If the values of all module properties (except MVID) are compared and no duplicates are found, an error is raised.</span></span>

- <span data-ttu-id="4090b-116">若為類型定義（ `TypeDef` ），則不會將任何重複專案合併到目前的範圍。</span><span class="sxs-lookup"><span data-stu-id="4090b-116">For type definitions (`TypeDef`), no duplicates are merged into the current scope.</span></span> <span data-ttu-id="4090b-117">`TypeDef`系統會針對每個*完整的物件名稱*  +  *GUID*  +  *版本號碼*，檢查物件是否有重複的專案。</span><span class="sxs-lookup"><span data-stu-id="4090b-117">`TypeDef` objects are checked for duplicates against each *fully-qualified object name* + *GUID* + *version number*.</span></span> <span data-ttu-id="4090b-118">如果名稱或 GUID 有相符專案，而且其他兩個專案的任何一個都不同，就會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="4090b-118">If there is a match on either name or GUID, and any of the other two elements is different, an error is raised.</span></span> <span data-ttu-id="4090b-119">否則，如果這三個專案都相符， `MergeEnd` 會粗略檢查以確保專案確實重複; 如果不是，則會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="4090b-119">Otherwise, if all three items match, `MergeEnd` does a cursory check to ensure the entries are indeed duplicates; if not, an error is raised.</span></span> <span data-ttu-id="4090b-120">這個粗略的檢查會尋找：</span><span class="sxs-lookup"><span data-stu-id="4090b-120">This cursory check looks for:</span></span>

  - <span data-ttu-id="4090b-121">相同的成員宣告，以相同的順序出現。</span><span class="sxs-lookup"><span data-stu-id="4090b-121">The same member declarations, occurring in the same order.</span></span> <span data-ttu-id="4090b-122">標記為 `mdPrivateScope` （請參閱[CorMethodAttr](cormethodattr-enumeration.md)列舉）的成員不會包含在這項檢查中，而是以特殊方式合併。</span><span class="sxs-lookup"><span data-stu-id="4090b-122">Members that are flagged as `mdPrivateScope` (see the [CorMethodAttr](cormethodattr-enumeration.md) enumeration) are not included in this check; they are merged specially.</span></span>

  - <span data-ttu-id="4090b-123">相同的類別版面配置。</span><span class="sxs-lookup"><span data-stu-id="4090b-123">The same class layout.</span></span>

  <span data-ttu-id="4090b-124">這表示物件在宣告的 `TypeDef` 每個中繼資料範圍中一律必須完全且一致地定義; 如果其成員執行（針對類別）會分散到多個編譯單位，則完整定義會假設存在於每個範圍中，而不會累加到每個範圍。</span><span class="sxs-lookup"><span data-stu-id="4090b-124">This means that a `TypeDef` object must always be fully and consistently defined in every metadata scope in which it is declared; if its member implementations (for a class) are spread across multiple compilation units, the full definition is assumed to be present in every scope and not incremental to each scope.</span></span> <span data-ttu-id="4090b-125">例如，如果參數名稱與合約有關，則它們必須以相同方式發出到每個範圍;如果不相關，則不應該將它們發出至中繼資料。</span><span class="sxs-lookup"><span data-stu-id="4090b-125">For example, if parameter names are relevant to the contract, they must be emitted the same way into every scope; if they are not relevant, they should not be emitted into metadata.</span></span>

  <span data-ttu-id="4090b-126">例外狀況是 `TypeDef` 物件可以有標記為的累加成員 `mdPrivateScope` 。</span><span class="sxs-lookup"><span data-stu-id="4090b-126">The exception is that a `TypeDef` object can have incremental members flagged as `mdPrivateScope`.</span></span> <span data-ttu-id="4090b-127">遇到這些情況時，以 `MergeEnd` 累加方式將它們加入至目前的範圍，而不考慮重複專案。</span><span class="sxs-lookup"><span data-stu-id="4090b-127">On encountering these, `MergeEnd` incrementally adds them to the current scope without regard for duplicates.</span></span> <span data-ttu-id="4090b-128">因為編譯器瞭解私用範圍，所以編譯器必須負責強制執行規則。</span><span class="sxs-lookup"><span data-stu-id="4090b-128">Because the compiler understands the private scope, the compiler must be responsible for enforcing rules.</span></span>

- <span data-ttu-id="4090b-129">相對虛擬位址（Rva）不會匯入或合併;編譯器應該會重新發出這則資訊。</span><span class="sxs-lookup"><span data-stu-id="4090b-129">Relative virtual addresses (RVAs) are not imported or merged; the compiler is expected to re-emit this information.</span></span>

- <span data-ttu-id="4090b-130">自訂屬性只有在其附加的專案合併時才會合並。</span><span class="sxs-lookup"><span data-stu-id="4090b-130">Custom attributes are merged only when the item to which they are attached is merged.</span></span> <span data-ttu-id="4090b-131">例如，當第一次遇到類別時，會合並與類別相關聯的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="4090b-131">For example, custom attributes associated with a class are merged when the class is first encountered.</span></span> <span data-ttu-id="4090b-132">如果自訂屬性與 `TypeDef` `MemberDef` 特定于編譯單位的或相關聯（例如成員編譯的時間戳記），它們就不會合並，而是由編譯器負責移除或更新這類中繼資料。</span><span class="sxs-lookup"><span data-stu-id="4090b-132">If custom attributes are associated with a `TypeDef` or `MemberDef` that is specific to the compilation unit (such as the time stamp of a member compile), they are not merged and it is up to the compiler to remove or update such metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="4090b-133">需求</span><span class="sxs-lookup"><span data-stu-id="4090b-133">Requirements</span></span>

<span data-ttu-id="4090b-134">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4090b-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="4090b-135">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="4090b-135">**Header:** Cor.h</span></span>

<span data-ttu-id="4090b-136">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="4090b-136">**Library:** Used as a resource in MSCorEE.dll</span></span>

<span data-ttu-id="4090b-137">**.NET Framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4090b-137">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="4090b-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4090b-138">See also</span></span>

- [<span data-ttu-id="4090b-139">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="4090b-139">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="4090b-140">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="4090b-140">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
