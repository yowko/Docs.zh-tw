---
title: IHostSecurityContext::Capture 方法
ms.date: 03/30/2017
api_name:
- IHostSecurityContext.Capture
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityContext::Capture
helpviewer_keywords:
- Capture method [.NET Framework hosting]
- IHostSecurityContext::Capture method [.NET Framework hosting]
ms.assetid: ae0836d0-1170-4494-bac5-d0e809df51a2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01d8821cdcb27ed44491db41da22309147da8a36
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706731"
---
# <a name="ihostsecuritycontextcapture-method"></a><span data-ttu-id="41614-102">IHostSecurityContext::Capture 方法</span><span class="sxs-lookup"><span data-stu-id="41614-102">IHostSecurityContext::Capture Method</span></span>
<span data-ttu-id="41614-103">取得的複製品[IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)呼叫所傳回的執行個體[ihostsecuritymanager:: Getsecuritycontext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)。</span><span class="sxs-lookup"><span data-stu-id="41614-103">Gets a clone of the [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) instance returned from a call to [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41614-104">語法</span><span class="sxs-lookup"><span data-stu-id="41614-104">Syntax</span></span>  
  
```  
HRESULT Capture (  
    [out] IHostSecurityContext** ppClonedContext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="41614-105">參數</span><span class="sxs-lookup"><span data-stu-id="41614-105">Parameters</span></span>  
 `ppClonedContext`  
 <span data-ttu-id="41614-106">[out]建立複製的位址指標`IHostSecurityContext`来擷取的物件。</span><span class="sxs-lookup"><span data-stu-id="41614-106">[out] A pointer to the address of a clone of the `IHostSecurityContext` object to be captured.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="41614-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="41614-107">Return Value</span></span>  
  
|<span data-ttu-id="41614-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="41614-108">HRESULT</span></span>|<span data-ttu-id="41614-109">描述</span><span class="sxs-lookup"><span data-stu-id="41614-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="41614-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="41614-110">S_OK</span></span>|<span data-ttu-id="41614-111">`Capture` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="41614-111">`Capture` returned successfully.</span></span>|  
|<span data-ttu-id="41614-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="41614-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="41614-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="41614-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="41614-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="41614-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="41614-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="41614-115">The call timed out.</span></span>|  
|<span data-ttu-id="41614-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="41614-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="41614-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="41614-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="41614-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="41614-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="41614-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="41614-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="41614-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="41614-120">E_FAIL</span></span>|<span data-ttu-id="41614-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="41614-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="41614-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="41614-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="41614-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="41614-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41614-124">備註</span><span class="sxs-lookup"><span data-stu-id="41614-124">Remarks</span></span>  
 <span data-ttu-id="41614-125">從傳回的介面指標`Capture`是擷取的內容的複製。</span><span class="sxs-lookup"><span data-stu-id="41614-125">The interface pointer returned from `Capture` is a clone of the captured context.</span></span> <span data-ttu-id="41614-126">當這項資訊移動非同步程式碼點時，其存留期的指標，對其進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="41614-126">When this information is moved across an asynchronous code point, its lifetime is separated from that of the pointer against which the call was made.</span></span> <span data-ttu-id="41614-127">因此可以釋放原始指標。</span><span class="sxs-lookup"><span data-stu-id="41614-127">The original pointer can therefore be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41614-128">需求</span><span class="sxs-lookup"><span data-stu-id="41614-128">Requirements</span></span>  
 <span data-ttu-id="41614-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="41614-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41614-130">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="41614-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="41614-131">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="41614-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="41614-132">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41614-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41614-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41614-133">See also</span></span>
- [<span data-ttu-id="41614-134">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="41614-134">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="41614-135">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="41614-135">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
