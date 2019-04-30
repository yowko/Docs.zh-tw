---
title: IMetaDataEmit::GetSaveSize 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetSaveSize
helpviewer_keywords:
- IMetaDataEmit::GetSaveSize method [.NET Framework metadata]
- GetSaveSize method [.NET Framework metadata]
ms.assetid: 8aea2e2c-23a3-4cda-9a06-e19f97383830
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d9279808e4ad15b693d06ac8a99dd33a609e5a8f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992507"
---
# <a name="imetadataemitgetsavesize-method"></a><span data-ttu-id="491ee-102">IMetaDataEmit::GetSaveSize 方法</span><span class="sxs-lookup"><span data-stu-id="491ee-102">IMetaDataEmit::GetSaveSize Method</span></span>
<span data-ttu-id="491ee-103">目前範圍中取得的二進位的估計的大小，組件和它的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="491ee-103">Gets the estimated binary size of the assembly and its metadata in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="491ee-104">語法</span><span class="sxs-lookup"><span data-stu-id="491ee-104">Syntax</span></span>  
  
```  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="491ee-105">參數</span><span class="sxs-lookup"><span data-stu-id="491ee-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="491ee-106">[in]值為[CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md)列舉，指定是否要取得精確或近似大小。</span><span class="sxs-lookup"><span data-stu-id="491ee-106">[in] A value of the [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) enumeration that specifies whether to get an accurate or approximate size.</span></span> <span data-ttu-id="491ee-107">只有三個值都有效： cssAccurate，cssQuick，和 cssDiscardTransientCAs:</span><span class="sxs-lookup"><span data-stu-id="491ee-107">Only three values are valid: cssAccurate, cssQuick, and cssDiscardTransientCAs:</span></span>  
  
- <span data-ttu-id="491ee-108">cssAccurate 傳回的確切的儲存大小，但所花費的時間來計算。</span><span class="sxs-lookup"><span data-stu-id="491ee-108">cssAccurate returns the exact save size but takes longer to calculate.</span></span>  
  
- <span data-ttu-id="491ee-109">cssQuick 傳回基於安全考量，填補的大小，但需要較少的時間來計算。</span><span class="sxs-lookup"><span data-stu-id="491ee-109">cssQuick returns a size, padded for safety, but takes less time to calculate.</span></span>  
  
- <span data-ttu-id="491ee-110">cssDiscardTransientCAs 告訴`GetSaveSize`，它可以擲出可捨棄的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="491ee-110">cssDiscardTransientCAs tells `GetSaveSize` that it can throw away discardable custom attributes.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="491ee-111">[out]指標，才能儲存檔案的大小。</span><span class="sxs-lookup"><span data-stu-id="491ee-111">[out] A pointer to the size that is required to save the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="491ee-112">備註</span><span class="sxs-lookup"><span data-stu-id="491ee-112">Remarks</span></span>  
 <span data-ttu-id="491ee-113">`GetSaveSize` 計算所需的空間，以位元組為單位，將組件和其所有中繼資料儲存在目前的範圍。</span><span class="sxs-lookup"><span data-stu-id="491ee-113">`GetSaveSize` calculates the space required, in bytes, to save the assembly and all its metadata in the current scope.</span></span> <span data-ttu-id="491ee-114">(呼叫[imetadataemit:: Savetostream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md)方法會發出此位元組數目。)</span><span class="sxs-lookup"><span data-stu-id="491ee-114">(A call to the [IMetaDataEmit::SaveToStream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) method would emit this number of bytes.)</span></span>  
  
 <span data-ttu-id="491ee-115">如果呼叫者會實作[IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)介面 (透過[imetadataemit:: Sethandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)或是[imetadataemit:: Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md))，`GetSaveSize`會執行兩個階段若要最佳化，並將它壓縮之中繼資料。</span><span class="sxs-lookup"><span data-stu-id="491ee-115">If the caller implements the [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) interface (through [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) or [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` will perform two passes over the metadata to optimize and compress it.</span></span> <span data-ttu-id="491ee-116">否則，不會執行最佳化。</span><span class="sxs-lookup"><span data-stu-id="491ee-116">Otherwise, no optimizations are performed.</span></span>  
  
 <span data-ttu-id="491ee-117">如果執行最佳化，則第一次傳遞只是排序的中繼資料結構，以微調效能的匯入時的搜尋。</span><span class="sxs-lookup"><span data-stu-id="491ee-117">If optimization is performed, the first pass simply sorts the metadata structures to tune the performance of import-time searches.</span></span> <span data-ttu-id="491ee-118">此步驟通常會導致移動，具有副作用，保留供日後參考工具的權杖都會失效的記錄。</span><span class="sxs-lookup"><span data-stu-id="491ee-118">This step typically results in moving records around, with the side effect that tokens retained by the tool for future reference are invalidated.</span></span> <span data-ttu-id="491ee-119">中繼資料並不會通知呼叫端的這些語彙基元的變更，直到之後的第二個階段，不過。</span><span class="sxs-lookup"><span data-stu-id="491ee-119">The metadata does not inform the caller of these token changes until after the second pass, however.</span></span> <span data-ttu-id="491ee-120">在第二個階段中，各種最佳化所執行的目的為了避免，請在中繼資料，例如最佳化離開 （早期繫結） 的整體大小`mdTypeRef`和`mdMemberRef`語彙基元型別或成員中所宣告的參考時目前的中繼資料範圍。</span><span class="sxs-lookup"><span data-stu-id="491ee-120">In the second pass, various optimizations are performed that are intended to reduce the overall size of the metadata, such as optimizing away (early binding) `mdTypeRef` and `mdMemberRef` tokens when the reference is to a type or member that is declared in the current metadata scope.</span></span> <span data-ttu-id="491ee-121">在此階段中，就會發生另一回合的語彙基元對應。</span><span class="sxs-lookup"><span data-stu-id="491ee-121">In this pass, another round of token mapping occurs.</span></span> <span data-ttu-id="491ee-122">在此階段之後, 的中繼資料引擎會通知呼叫端，透過其`IMapToken`介面，任何變更語彙基元值。</span><span class="sxs-lookup"><span data-stu-id="491ee-122">After this pass, the metadata engine notifies the caller, through its `IMapToken` interface, of any changed token values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="491ee-123">需求</span><span class="sxs-lookup"><span data-stu-id="491ee-123">Requirements</span></span>  
 <span data-ttu-id="491ee-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="491ee-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="491ee-125">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="491ee-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="491ee-126">**LIBRARY:** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="491ee-126">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="491ee-127">**.NET framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="491ee-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="491ee-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="491ee-128">See also</span></span>

- [<span data-ttu-id="491ee-129">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="491ee-129">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="491ee-130">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="491ee-130">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
