---
title: ICLRReferenceAssemblyEnum::Get 方法
ms.date: 03/30/2017
api_name:
- ICLRReferenceAssemblyEnum.Get
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRReferenceAssemblyEnum::Get
helpviewer_keywords:
- ICLRReferenceAssemblyEnum::Get method [.NET Framework hosting]
- Get method, ICLRReferenceAssemblyEnum interface [.NET Framework hosting]
ms.assetid: f21c1612-9c5d-4abc-a337-577086d29c17
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d8cfb2f18bcceed3a125ac7876122c02d2267698
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436451"
---
# <a name="iclrreferenceassemblyenumget-method"></a><span data-ttu-id="80969-102">ICLRReferenceAssemblyEnum::Get 方法</span><span class="sxs-lookup"><span data-stu-id="80969-102">ICLRReferenceAssemblyEnum::Get Method</span></span>
<span data-ttu-id="80969-103">在提供的索引取得組件識別。</span><span class="sxs-lookup"><span data-stu-id="80969-103">Gets the assembly identity at the supplied index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80969-104">語法</span><span class="sxs-lookup"><span data-stu-id="80969-104">Syntax</span></span>  
  
```  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="80969-105">參數</span><span class="sxs-lookup"><span data-stu-id="80969-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="80969-106">[in]要傳回之組件識別的以零為起始的索引。</span><span class="sxs-lookup"><span data-stu-id="80969-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="80969-107">[out]包含組件識別資料緩衝區。</span><span class="sxs-lookup"><span data-stu-id="80969-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="80969-108">[in、 out]大小`pwzBuffer`緩衝區。</span><span class="sxs-lookup"><span data-stu-id="80969-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="80969-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="80969-109">Return Value</span></span>  
  
|<span data-ttu-id="80969-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="80969-110">HRESULT</span></span>|<span data-ttu-id="80969-111">描述</span><span class="sxs-lookup"><span data-stu-id="80969-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="80969-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="80969-112">S_OK</span></span>|<span data-ttu-id="80969-113">`Get` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="80969-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="80969-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="80969-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="80969-115">`pwzBuffer` 為太小。</span><span class="sxs-lookup"><span data-stu-id="80969-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="80969-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="80969-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="80969-117">列舉包含的任何項目。</span><span class="sxs-lookup"><span data-stu-id="80969-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="80969-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="80969-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="80969-119">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="80969-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="80969-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="80969-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="80969-121">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="80969-121">The call timed out.</span></span>|  
|<span data-ttu-id="80969-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="80969-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="80969-123">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="80969-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="80969-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="80969-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="80969-125">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="80969-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="80969-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="80969-126">E_FAIL</span></span>|<span data-ttu-id="80969-127">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="80969-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="80969-128">若方法會傳回 E_FAIL，CLR 就不會再處理序內。</span><span class="sxs-lookup"><span data-stu-id="80969-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="80969-129">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="80969-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80969-130">備註</span><span class="sxs-lookup"><span data-stu-id="80969-130">Remarks</span></span>  
 <span data-ttu-id="80969-131">`Get` 通常會呼叫兩次。</span><span class="sxs-lookup"><span data-stu-id="80969-131">`Get` is typically called twice.</span></span> <span data-ttu-id="80969-132">第一次呼叫所提供的 null 值`pwzBuffer`，並設定`pcchBufferSize`大小適用於`pwzBuffer`。</span><span class="sxs-lookup"><span data-stu-id="80969-132">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="80969-133">第二個呼叫可提供適當大小`pwzBuffer`，而且包含在完成時的標準的組件識別資料。</span><span class="sxs-lookup"><span data-stu-id="80969-133">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80969-134">需求</span><span class="sxs-lookup"><span data-stu-id="80969-134">Requirements</span></span>  
 <span data-ttu-id="80969-135">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="80969-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80969-136">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="80969-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="80969-137">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="80969-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="80969-138">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80969-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80969-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80969-139">See Also</span></span>  
 [<span data-ttu-id="80969-140">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="80969-140">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="80969-141">ICLRReferenceAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="80969-141">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
