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
ms.openlocfilehash: 22c0a317777a12294ba7a90f7af1ceeca3ad0a47
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009258"
---
# <a name="imetadataemitgetsavesize-method"></a><span data-ttu-id="ce239-102">IMetaDataEmit::GetSaveSize 方法</span><span class="sxs-lookup"><span data-stu-id="ce239-102">IMetaDataEmit::GetSaveSize Method</span></span>
<span data-ttu-id="ce239-103">取得元件及其中繼資料在目前範圍中的估計二進位大小。</span><span class="sxs-lookup"><span data-stu-id="ce239-103">Gets the estimated binary size of the assembly and its metadata in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce239-104">語法</span><span class="sxs-lookup"><span data-stu-id="ce239-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce239-105">參數</span><span class="sxs-lookup"><span data-stu-id="ce239-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="ce239-106">在[CorSaveSize](corsavesize-enumeration.md)列舉的值，指定是否要取得精確或近似的大小。</span><span class="sxs-lookup"><span data-stu-id="ce239-106">[in] A value of the [CorSaveSize](corsavesize-enumeration.md) enumeration that specifies whether to get an accurate or approximate size.</span></span> <span data-ttu-id="ce239-107">只有三個有效的值： cssAccurate、cssQuick 和 cssDiscardTransientCAs：</span><span class="sxs-lookup"><span data-stu-id="ce239-107">Only three values are valid: cssAccurate, cssQuick, and cssDiscardTransientCAs:</span></span>  
  
- <span data-ttu-id="ce239-108">cssAccurate 會傳回完全相同的儲存大小，但需要較長的時間來計算。</span><span class="sxs-lookup"><span data-stu-id="ce239-108">cssAccurate returns the exact save size but takes longer to calculate.</span></span>  
  
- <span data-ttu-id="ce239-109">cssQuick 會傳回大小，以填補安全性，但花費較少的時間來計算。</span><span class="sxs-lookup"><span data-stu-id="ce239-109">cssQuick returns a size, padded for safety, but takes less time to calculate.</span></span>  
  
- <span data-ttu-id="ce239-110">cssDiscardTransientCAs `GetSaveSize` 會告訴它可以捨棄可捨棄的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="ce239-110">cssDiscardTransientCAs tells `GetSaveSize` that it can throw away discardable custom attributes.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="ce239-111">脫銷儲存檔案所需大小的指標。</span><span class="sxs-lookup"><span data-stu-id="ce239-111">[out] A pointer to the size that is required to save the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce239-112">備註</span><span class="sxs-lookup"><span data-stu-id="ce239-112">Remarks</span></span>  
 <span data-ttu-id="ce239-113">`GetSaveSize`計算所需的空間（以位元組為單位），以將元件及其所有中繼資料儲存在目前的範圍中。</span><span class="sxs-lookup"><span data-stu-id="ce239-113">`GetSaveSize` calculates the space required, in bytes, to save the assembly and all its metadata in the current scope.</span></span> <span data-ttu-id="ce239-114">（呼叫[IMetaDataEmit：： SaveToStream](imetadataemit-savetostream-method.md)方法會發出此位元組數目）。</span><span class="sxs-lookup"><span data-stu-id="ce239-114">(A call to the [IMetaDataEmit::SaveToStream](imetadataemit-savetostream-method.md) method would emit this number of bytes.)</span></span>  
  
 <span data-ttu-id="ce239-115">如果呼叫端實[IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)介面（透過[IMetaDataEmit：： SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)或[IMetaDataEmit：： Merge](imetadataemit-merge-method.md)）， `GetSaveSize` 將會對中繼資料執行兩次傳遞，以將它優化並加以壓縮。</span><span class="sxs-lookup"><span data-stu-id="ce239-115">If the caller implements the [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) interface (through [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) or [IMetaDataEmit::Merge](imetadataemit-merge-method.md)), `GetSaveSize` will perform two passes over the metadata to optimize and compress it.</span></span> <span data-ttu-id="ce239-116">否則，不會執行任何優化。</span><span class="sxs-lookup"><span data-stu-id="ce239-116">Otherwise, no optimizations are performed.</span></span>  
  
 <span data-ttu-id="ce239-117">如果執行優化，第一次傳遞只會將元資料結構排序，以微調匯入時間搜尋的效能。</span><span class="sxs-lookup"><span data-stu-id="ce239-117">If optimization is performed, the first pass simply sorts the metadata structures to tune the performance of import-time searches.</span></span> <span data-ttu-id="ce239-118">此步驟通常會導致移動記錄，而副作用是由工具所保留以供日後參考的權杖會失效。</span><span class="sxs-lookup"><span data-stu-id="ce239-118">This step typically results in moving records around, with the side effect that tokens retained by the tool for future reference are invalidated.</span></span> <span data-ttu-id="ce239-119">不過，中繼資料不會通知呼叫者這些權杖變更，直到第二次傳遞為止。</span><span class="sxs-lookup"><span data-stu-id="ce239-119">The metadata does not inform the caller of these token changes until after the second pass, however.</span></span> <span data-ttu-id="ce239-120">在第二個階段中，會執行各種優化，以減少中繼資料的整體大小，例如， `mdTypeRef` `mdMemberRef` 當參考指向目前中繼資料範圍內所宣告的類型或成員時，將其優化（早期繫結）和標記。</span><span class="sxs-lookup"><span data-stu-id="ce239-120">In the second pass, various optimizations are performed that are intended to reduce the overall size of the metadata, such as optimizing away (early binding) `mdTypeRef` and `mdMemberRef` tokens when the reference is to a type or member that is declared in the current metadata scope.</span></span> <span data-ttu-id="ce239-121">在此階段中，會發生另一個標記對應的迴圈。</span><span class="sxs-lookup"><span data-stu-id="ce239-121">In this pass, another round of token mapping occurs.</span></span> <span data-ttu-id="ce239-122">在此階段之後，中繼資料引擎會透過其介面，通知呼叫端 `IMapToken` 任何已變更的 token 值。</span><span class="sxs-lookup"><span data-stu-id="ce239-122">After this pass, the metadata engine notifies the caller, through its `IMapToken` interface, of any changed token values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce239-123">需求</span><span class="sxs-lookup"><span data-stu-id="ce239-123">Requirements</span></span>  
 <span data-ttu-id="ce239-124">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ce239-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce239-125">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="ce239-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ce239-126">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="ce239-126">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ce239-127">**.NET Framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce239-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce239-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce239-128">See also</span></span>

- [<span data-ttu-id="ce239-129">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="ce239-129">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="ce239-130">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="ce239-130">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
