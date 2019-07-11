---
title: ICLRProbingAssemblyEnum::Get 方法
ms.date: 03/30/2017
api_name:
- ICLRProbingAssemblyEnum.Get
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRProbingAssemblyEnum::Get
helpviewer_keywords:
- Get method, ICLRProbingAssemblyEnum interface [.NET Framework hosting]
- ICLRProbingAssemblyEnum::Get method [.NET Framework hosting]
ms.assetid: fdb67a77-782f-44cf-a8a1-b75999b0f3c8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3225e42df44e719ecde31c26fae70f26731fa157
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761579"
---
# <a name="iclrprobingassemblyenumget-method"></a><span data-ttu-id="5f59f-102">ICLRProbingAssemblyEnum::Get 方法</span><span class="sxs-lookup"><span data-stu-id="5f59f-102">ICLRProbingAssemblyEnum::Get Method</span></span>
<span data-ttu-id="5f59f-103">取得組件識別的指定索引處。</span><span class="sxs-lookup"><span data-stu-id="5f59f-103">Gets the assembly identity at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f59f-104">語法</span><span class="sxs-lookup"><span data-stu-id="5f59f-104">Syntax</span></span>  
  
```cpp  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f59f-105">參數</span><span class="sxs-lookup"><span data-stu-id="5f59f-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="5f59f-106">[in]要傳回的組件身分識別以零為起始的索引。</span><span class="sxs-lookup"><span data-stu-id="5f59f-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="5f59f-107">[out]包含組件身分識別資料的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="5f59f-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="5f59f-108">[in、 out]大小`pwzBuffer`緩衝區。</span><span class="sxs-lookup"><span data-stu-id="5f59f-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5f59f-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="5f59f-109">Return Value</span></span>  
  
|<span data-ttu-id="5f59f-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5f59f-110">HRESULT</span></span>|<span data-ttu-id="5f59f-111">說明</span><span class="sxs-lookup"><span data-stu-id="5f59f-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5f59f-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="5f59f-112">S_OK</span></span>|<span data-ttu-id="5f59f-113">`Get` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="5f59f-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="5f59f-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="5f59f-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="5f59f-115">`pwzBuffer` 為太小。</span><span class="sxs-lookup"><span data-stu-id="5f59f-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="5f59f-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="5f59f-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="5f59f-117">列舉包含的任何其他項目。</span><span class="sxs-lookup"><span data-stu-id="5f59f-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="5f59f-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5f59f-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5f59f-119">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="5f59f-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5f59f-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5f59f-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5f59f-121">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="5f59f-121">The call timed out.</span></span>|  
|<span data-ttu-id="5f59f-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5f59f-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5f59f-123">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="5f59f-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5f59f-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5f59f-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5f59f-125">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="5f59f-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5f59f-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5f59f-126">E_FAIL</span></span>|<span data-ttu-id="5f59f-127">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="5f59f-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5f59f-128">如果方法會傳回 E_FAIL，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="5f59f-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5f59f-129">任何裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="5f59f-129">Subsequent calls to any hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f59f-130">備註</span><span class="sxs-lookup"><span data-stu-id="5f59f-130">Remarks</span></span>  
 <span data-ttu-id="5f59f-131">位於索引 0 的身分識別是特有的處理器架構的識別。</span><span class="sxs-lookup"><span data-stu-id="5f59f-131">The identity at index 0 is the identity specific to the processor architecture.</span></span> <span data-ttu-id="5f59f-132">位於索引 1 的身分識別是 Microsoft intermediate language (MSIL) 的架構中性組件。</span><span class="sxs-lookup"><span data-stu-id="5f59f-132">The identity at index 1 is the architecture-neutral assembly for Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="5f59f-133">位於索引 2 的身分識別不包含架構資訊。</span><span class="sxs-lookup"><span data-stu-id="5f59f-133">The identity at index 2 contains no architecture information.</span></span>  
  
 <span data-ttu-id="5f59f-134">`Get` 通常會呼叫兩次。</span><span class="sxs-lookup"><span data-stu-id="5f59f-134">`Get` is typically called twice.</span></span> <span data-ttu-id="5f59f-135">第一次呼叫提供 null 值`pwzBuffer`，並設定`pcchBufferSize`適用於大小`pwzBuffer`。</span><span class="sxs-lookup"><span data-stu-id="5f59f-135">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="5f59f-136">第二個呼叫提供適當大小`pwzBuffer`，而且包含完成時的標準組件身分識別資料。</span><span class="sxs-lookup"><span data-stu-id="5f59f-136">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f59f-137">需求</span><span class="sxs-lookup"><span data-stu-id="5f59f-137">Requirements</span></span>  
 <span data-ttu-id="5f59f-138">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5f59f-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f59f-139">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5f59f-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5f59f-140">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5f59f-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5f59f-141">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f59f-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f59f-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f59f-142">See also</span></span>

- [<span data-ttu-id="5f59f-143">ICLRProbingAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="5f59f-143">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
- [<span data-ttu-id="5f59f-144">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="5f59f-144">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
