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
ms.openlocfilehash: 5cb202f5284c1c18545ec750b2fa0f04d4b0d2e2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722059"
---
# <a name="imetadataemitgetsavesize-method"></a><span data-ttu-id="842c7-102">IMetaDataEmit::GetSaveSize 方法</span><span class="sxs-lookup"><span data-stu-id="842c7-102">IMetaDataEmit::GetSaveSize Method</span></span>

<span data-ttu-id="842c7-103">取得元件的估計二進位大小及其在目前範圍中的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="842c7-103">Gets the estimated binary size of the assembly and its metadata in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="842c7-104">語法</span><span class="sxs-lookup"><span data-stu-id="842c7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="842c7-105">參數</span><span class="sxs-lookup"><span data-stu-id="842c7-105">Parameters</span></span>  

 `fSave`  
 <span data-ttu-id="842c7-106">在 [CorSaveSize](corsavesize-enumeration.md) 列舉值，指定是否要取得精確或近似的大小。</span><span class="sxs-lookup"><span data-stu-id="842c7-106">[in] A value of the [CorSaveSize](corsavesize-enumeration.md) enumeration that specifies whether to get an accurate or approximate size.</span></span> <span data-ttu-id="842c7-107">只有三個值有效： cssAccurate、cssQuick 和 cssDiscardTransientCAs：</span><span class="sxs-lookup"><span data-stu-id="842c7-107">Only three values are valid: cssAccurate, cssQuick, and cssDiscardTransientCAs:</span></span>  
  
- <span data-ttu-id="842c7-108">cssAccurate 會傳回確切的儲存大小，但需要較長的時間來計算。</span><span class="sxs-lookup"><span data-stu-id="842c7-108">cssAccurate returns the exact save size but takes longer to calculate.</span></span>  
  
- <span data-ttu-id="842c7-109">cssQuick 會傳回大小，以填補安全，但需要較少的時間來計算。</span><span class="sxs-lookup"><span data-stu-id="842c7-109">cssQuick returns a size, padded for safety, but takes less time to calculate.</span></span>  
  
- <span data-ttu-id="842c7-110">cssDiscardTransientCAs 指出 `GetSaveSize` 它可能會擲回 discardable 的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="842c7-110">cssDiscardTransientCAs tells `GetSaveSize` that it can throw away discardable custom attributes.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="842c7-111">擴展儲存檔案所需的大小指標。</span><span class="sxs-lookup"><span data-stu-id="842c7-111">[out] A pointer to the size that is required to save the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="842c7-112">備註</span><span class="sxs-lookup"><span data-stu-id="842c7-112">Remarks</span></span>  

 <span data-ttu-id="842c7-113">`GetSaveSize` 以位元組為單位計算要儲存元件的空間，以及其在目前範圍中的所有中繼資料。</span><span class="sxs-lookup"><span data-stu-id="842c7-113">`GetSaveSize` calculates the space required, in bytes, to save the assembly and all its metadata in the current scope.</span></span> <span data-ttu-id="842c7-114"> ([IMetaDataEmit：： SaveToStream](imetadataemit-savetostream-method.md) 方法的呼叫會發出此位元組數目。 ) </span><span class="sxs-lookup"><span data-stu-id="842c7-114">(A call to the [IMetaDataEmit::SaveToStream](imetadataemit-savetostream-method.md) method would emit this number of bytes.)</span></span>  
  
 <span data-ttu-id="842c7-115">如果呼叫端透過[IMetaDataEmit：： SetHandler](imetadataemit-sethandler-method.md)或[IMetaDataEmit：： Merge](imetadataemit-merge-method.md)) 來執行[IMapToken](imaptoken-interface.md)介面 (， `GetSaveSize` 將會對中繼資料執行兩次傳遞，以將其優化並加以壓縮。</span><span class="sxs-lookup"><span data-stu-id="842c7-115">If the caller implements the [IMapToken](imaptoken-interface.md) interface (through [IMetaDataEmit::SetHandler](imetadataemit-sethandler-method.md) or [IMetaDataEmit::Merge](imetadataemit-merge-method.md)), `GetSaveSize` will perform two passes over the metadata to optimize and compress it.</span></span> <span data-ttu-id="842c7-116">否則，不會執行任何優化。</span><span class="sxs-lookup"><span data-stu-id="842c7-116">Otherwise, no optimizations are performed.</span></span>  
  
 <span data-ttu-id="842c7-117">如果執行優化，則第一次傳遞只會排序元資料結構來調整匯入時間搜尋的效能。</span><span class="sxs-lookup"><span data-stu-id="842c7-117">If optimization is performed, the first pass simply sorts the metadata structures to tune the performance of import-time searches.</span></span> <span data-ttu-id="842c7-118">此步驟通常會導致四處移動記錄，並且會影響工具保留的權杖以供日後參考。</span><span class="sxs-lookup"><span data-stu-id="842c7-118">This step typically results in moving records around, with the side effect that tokens retained by the tool for future reference are invalidated.</span></span> <span data-ttu-id="842c7-119">不過，中繼資料不會在第二次通過之前通知這些權杖變更的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="842c7-119">The metadata does not inform the caller of these token changes until after the second pass, however.</span></span> <span data-ttu-id="842c7-120">在第二個階段中，會執行各種優化，以減少中繼資料的整體大小，例如在 `mdTypeRef` `mdMemberRef` 參考至目前中繼資料範圍內所宣告的類型或成員時，將 (早期繫結) 和權杖優化。</span><span class="sxs-lookup"><span data-stu-id="842c7-120">In the second pass, various optimizations are performed that are intended to reduce the overall size of the metadata, such as optimizing away (early binding) `mdTypeRef` and `mdMemberRef` tokens when the reference is to a type or member that is declared in the current metadata scope.</span></span> <span data-ttu-id="842c7-121">在這個階段中，會發生另一輪 token 對應。</span><span class="sxs-lookup"><span data-stu-id="842c7-121">In this pass, another round of token mapping occurs.</span></span> <span data-ttu-id="842c7-122">經過這次傳遞之後，中繼資料引擎會透過其 `IMapToken` 介面，通知任何已變更權杖值的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="842c7-122">After this pass, the metadata engine notifies the caller, through its `IMapToken` interface, of any changed token values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="842c7-123">需求</span><span class="sxs-lookup"><span data-stu-id="842c7-123">Requirements</span></span>  

 <span data-ttu-id="842c7-124">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="842c7-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="842c7-125">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="842c7-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="842c7-126">連結 **庫：** 當做 MSCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="842c7-126">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="842c7-127">**.NET Framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="842c7-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="842c7-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="842c7-128">See also</span></span>

- [<span data-ttu-id="842c7-129">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="842c7-129">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="842c7-130">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="842c7-130">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
