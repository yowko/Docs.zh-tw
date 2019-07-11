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
ms.openlocfilehash: a69e32d418478071f9b99a391e6bef9095d6f4ad
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749915"
---
# <a name="iclrreferenceassemblyenumget-method"></a><span data-ttu-id="7bd3c-102">ICLRReferenceAssemblyEnum::Get 方法</span><span class="sxs-lookup"><span data-stu-id="7bd3c-102">ICLRReferenceAssemblyEnum::Get Method</span></span>
<span data-ttu-id="7bd3c-103">提供的索引處取得組件識別。</span><span class="sxs-lookup"><span data-stu-id="7bd3c-103">Gets the assembly identity at the supplied index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bd3c-104">語法</span><span class="sxs-lookup"><span data-stu-id="7bd3c-104">Syntax</span></span>  
  
```cpp  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7bd3c-105">參數</span><span class="sxs-lookup"><span data-stu-id="7bd3c-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="7bd3c-106">[in]要傳回的組件身分識別以零為起始的索引。</span><span class="sxs-lookup"><span data-stu-id="7bd3c-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="7bd3c-107">[out]包含組件身分識別資料的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="7bd3c-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="7bd3c-108">[in、 out]大小`pwzBuffer`緩衝區。</span><span class="sxs-lookup"><span data-stu-id="7bd3c-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7bd3c-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="7bd3c-109">Return Value</span></span>  
  
|<span data-ttu-id="7bd3c-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7bd3c-110">HRESULT</span></span>|<span data-ttu-id="7bd3c-111">描述</span><span class="sxs-lookup"><span data-stu-id="7bd3c-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7bd3c-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="7bd3c-112">S_OK</span></span>|<span data-ttu-id="7bd3c-113">`Get` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="7bd3c-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="7bd3c-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="7bd3c-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="7bd3c-115">`pwzBuffer` 為太小。</span><span class="sxs-lookup"><span data-stu-id="7bd3c-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="7bd3c-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="7bd3c-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="7bd3c-117">列舉包含的任何其他項目。</span><span class="sxs-lookup"><span data-stu-id="7bd3c-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="7bd3c-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7bd3c-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7bd3c-119">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="7bd3c-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7bd3c-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7bd3c-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7bd3c-121">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="7bd3c-121">The call timed out.</span></span>|  
|<span data-ttu-id="7bd3c-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7bd3c-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7bd3c-123">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="7bd3c-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7bd3c-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7bd3c-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7bd3c-125">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="7bd3c-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7bd3c-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7bd3c-126">E_FAIL</span></span>|<span data-ttu-id="7bd3c-127">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="7bd3c-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7bd3c-128">如果方法會傳回 E_FAIL，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="7bd3c-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7bd3c-129">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="7bd3c-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7bd3c-130">備註</span><span class="sxs-lookup"><span data-stu-id="7bd3c-130">Remarks</span></span>  
 <span data-ttu-id="7bd3c-131">`Get` 通常會呼叫兩次。</span><span class="sxs-lookup"><span data-stu-id="7bd3c-131">`Get` is typically called twice.</span></span> <span data-ttu-id="7bd3c-132">第一次呼叫提供 null 值`pwzBuffer`，並設定`pcchBufferSize`適用於大小`pwzBuffer`。</span><span class="sxs-lookup"><span data-stu-id="7bd3c-132">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="7bd3c-133">第二個呼叫提供適當大小`pwzBuffer`，而且包含完成時的標準組件身分識別資料。</span><span class="sxs-lookup"><span data-stu-id="7bd3c-133">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bd3c-134">需求</span><span class="sxs-lookup"><span data-stu-id="7bd3c-134">Requirements</span></span>  
 <span data-ttu-id="7bd3c-135">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7bd3c-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bd3c-136">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7bd3c-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7bd3c-137">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7bd3c-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7bd3c-138">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bd3c-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bd3c-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7bd3c-139">See also</span></span>

- [<span data-ttu-id="7bd3c-140">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="7bd3c-140">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="7bd3c-141">ICLRReferenceAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="7bd3c-141">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
