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
ms.openlocfilehash: 125a63638a41707b8eed918253cb1f93abb907eb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434330"
---
# <a name="imetadataemitgetsavesize-method"></a><span data-ttu-id="715d2-102">IMetaDataEmit::GetSaveSize 方法</span><span class="sxs-lookup"><span data-stu-id="715d2-102">IMetaDataEmit::GetSaveSize Method</span></span>
<span data-ttu-id="715d2-103">取得元件及其中繼資料在目前範圍中的估計二進位大小。</span><span class="sxs-lookup"><span data-stu-id="715d2-103">Gets the estimated binary size of the assembly and its metadata in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="715d2-104">語法</span><span class="sxs-lookup"><span data-stu-id="715d2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="715d2-105">參數</span><span class="sxs-lookup"><span data-stu-id="715d2-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="715d2-106">在[CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md)列舉的值，指定是否要取得精確或近似的大小。</span><span class="sxs-lookup"><span data-stu-id="715d2-106">[in] A value of the [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) enumeration that specifies whether to get an accurate or approximate size.</span></span> <span data-ttu-id="715d2-107">只有三個有效的值： cssAccurate、cssQuick 和 cssDiscardTransientCAs：</span><span class="sxs-lookup"><span data-stu-id="715d2-107">Only three values are valid: cssAccurate, cssQuick, and cssDiscardTransientCAs:</span></span>  
  
- <span data-ttu-id="715d2-108">cssAccurate 會傳回完全相同的儲存大小，但需要較長的時間來計算。</span><span class="sxs-lookup"><span data-stu-id="715d2-108">cssAccurate returns the exact save size but takes longer to calculate.</span></span>  
  
- <span data-ttu-id="715d2-109">cssQuick 會傳回大小，以填補安全性，但花費較少的時間來計算。</span><span class="sxs-lookup"><span data-stu-id="715d2-109">cssQuick returns a size, padded for safety, but takes less time to calculate.</span></span>  
  
- <span data-ttu-id="715d2-110">cssDiscardTransientCAs 會告訴 `GetSaveSize` 它可以捨棄可捨棄的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="715d2-110">cssDiscardTransientCAs tells `GetSaveSize` that it can throw away discardable custom attributes.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="715d2-111">脫銷儲存檔案所需大小的指標。</span><span class="sxs-lookup"><span data-stu-id="715d2-111">[out] A pointer to the size that is required to save the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="715d2-112">備註</span><span class="sxs-lookup"><span data-stu-id="715d2-112">Remarks</span></span>  
 <span data-ttu-id="715d2-113">`GetSaveSize` 會計算所需的空間（以位元組為單位），以將元件及其所有中繼資料儲存在目前的範圍中。</span><span class="sxs-lookup"><span data-stu-id="715d2-113">`GetSaveSize` calculates the space required, in bytes, to save the assembly and all its metadata in the current scope.</span></span> <span data-ttu-id="715d2-114">（呼叫[IMetaDataEmit：： SaveToStream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md)方法會發出此位元組數目）。</span><span class="sxs-lookup"><span data-stu-id="715d2-114">(A call to the [IMetaDataEmit::SaveToStream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) method would emit this number of bytes.)</span></span>  
  
 <span data-ttu-id="715d2-115">如果呼叫者執行[IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)介面（透過[IMetaDataEmit：： SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)或[IMetaDataEmit：： Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)），`GetSaveSize` 將會對中繼資料執行兩次行程，以將其優化並加以壓縮。</span><span class="sxs-lookup"><span data-stu-id="715d2-115">If the caller implements the [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) interface (through [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) or [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` will perform two passes over the metadata to optimize and compress it.</span></span> <span data-ttu-id="715d2-116">否則，不會執行任何優化。</span><span class="sxs-lookup"><span data-stu-id="715d2-116">Otherwise, no optimizations are performed.</span></span>  
  
 <span data-ttu-id="715d2-117">如果執行優化，第一次傳遞只會將元資料結構排序，以微調匯入時間搜尋的效能。</span><span class="sxs-lookup"><span data-stu-id="715d2-117">If optimization is performed, the first pass simply sorts the metadata structures to tune the performance of import-time searches.</span></span> <span data-ttu-id="715d2-118">此步驟通常會導致移動記錄，而副作用是由工具所保留以供日後參考的權杖會失效。</span><span class="sxs-lookup"><span data-stu-id="715d2-118">This step typically results in moving records around, with the side effect that tokens retained by the tool for future reference are invalidated.</span></span> <span data-ttu-id="715d2-119">不過，中繼資料不會通知呼叫者這些權杖變更，直到第二次傳遞為止。</span><span class="sxs-lookup"><span data-stu-id="715d2-119">The metadata does not inform the caller of these token changes until after the second pass, however.</span></span> <span data-ttu-id="715d2-120">在第二個階段中，會執行各種優化，以減少中繼資料的整體大小，例如在參考到目前中繼資料範圍內所宣告的類型或成員時，優化離開（早期繫結） `mdTypeRef` 和 `mdMemberRef` token。</span><span class="sxs-lookup"><span data-stu-id="715d2-120">In the second pass, various optimizations are performed that are intended to reduce the overall size of the metadata, such as optimizing away (early binding) `mdTypeRef` and `mdMemberRef` tokens when the reference is to a type or member that is declared in the current metadata scope.</span></span> <span data-ttu-id="715d2-121">在此階段中，會發生另一個標記對應的迴圈。</span><span class="sxs-lookup"><span data-stu-id="715d2-121">In this pass, another round of token mapping occurs.</span></span> <span data-ttu-id="715d2-122">經過此傳遞之後，中繼資料引擎會透過其 `IMapToken` 介面，通知呼叫者任何已變更的 token 值。</span><span class="sxs-lookup"><span data-stu-id="715d2-122">After this pass, the metadata engine notifies the caller, through its `IMapToken` interface, of any changed token values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="715d2-123">需求</span><span class="sxs-lookup"><span data-stu-id="715d2-123">Requirements</span></span>  
 <span data-ttu-id="715d2-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="715d2-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="715d2-125">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="715d2-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="715d2-126">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="715d2-126">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="715d2-127">**.NET framework 版本：** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="715d2-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="715d2-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="715d2-128">See also</span></span>

- [<span data-ttu-id="715d2-129">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="715d2-129">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="715d2-130">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="715d2-130">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
