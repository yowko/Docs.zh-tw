---
title: "IHostSecurityContext::Capture 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityContext.Capture
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityContext::Capture
helpviewer_keywords:
- Capture method [.NET Framework hosting]
- IHostSecurityContext::Capture method [.NET Framework hosting]
ms.assetid: ae0836d0-1170-4494-bac5-d0e809df51a2
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: def431dd40c6dd7aa6688a638971d3676bbd1ffb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsecuritycontextcapture-method"></a><span data-ttu-id="83ddd-102">IHostSecurityContext::Capture 方法</span><span class="sxs-lookup"><span data-stu-id="83ddd-102">IHostSecurityContext::Capture Method</span></span>
<span data-ttu-id="83ddd-103">取得的複製品[IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)從呼叫傳回的執行個體[ihostsecuritymanager:: Getsecuritycontext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)。</span><span class="sxs-lookup"><span data-stu-id="83ddd-103">Gets a clone of the [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) instance returned from a call to [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83ddd-104">語法</span><span class="sxs-lookup"><span data-stu-id="83ddd-104">Syntax</span></span>  
  
```  
HRESULT Capture (  
    [out] IHostSecurityContext** ppClonedContext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="83ddd-105">參數</span><span class="sxs-lookup"><span data-stu-id="83ddd-105">Parameters</span></span>  
 `ppClonedContext`  
 <span data-ttu-id="83ddd-106">[out]複製品的位址指標`IHostSecurityContext`来擷取的物件。</span><span class="sxs-lookup"><span data-stu-id="83ddd-106">[out] A pointer to the address of a clone of the `IHostSecurityContext` object to be captured.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83ddd-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="83ddd-107">Return Value</span></span>  
  
|<span data-ttu-id="83ddd-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="83ddd-108">HRESULT</span></span>|<span data-ttu-id="83ddd-109">描述</span><span class="sxs-lookup"><span data-stu-id="83ddd-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="83ddd-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="83ddd-110">S_OK</span></span>|<span data-ttu-id="83ddd-111">`Capture`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="83ddd-111">`Capture` returned successfully.</span></span>|  
|<span data-ttu-id="83ddd-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="83ddd-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="83ddd-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="83ddd-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="83ddd-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="83ddd-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="83ddd-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="83ddd-115">The call timed out.</span></span>|  
|<span data-ttu-id="83ddd-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="83ddd-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="83ddd-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="83ddd-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="83ddd-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="83ddd-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="83ddd-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="83ddd-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="83ddd-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="83ddd-120">E_FAIL</span></span>|<span data-ttu-id="83ddd-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="83ddd-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="83ddd-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="83ddd-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="83ddd-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="83ddd-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83ddd-124">備註</span><span class="sxs-lookup"><span data-stu-id="83ddd-124">Remarks</span></span>  
 <span data-ttu-id="83ddd-125">從傳回的介面指標`Capture`是擷取內容的複製。</span><span class="sxs-lookup"><span data-stu-id="83ddd-125">The interface pointer returned from `Capture` is a clone of the captured context.</span></span> <span data-ttu-id="83ddd-126">當這項資訊的非同步程式碼的點之間移動時，其存留期的呼叫時的指標。</span><span class="sxs-lookup"><span data-stu-id="83ddd-126">When this information is moved across an asynchronous code point, its lifetime is separated from that of the pointer against which the call was made.</span></span> <span data-ttu-id="83ddd-127">因此可以釋出原始指標。</span><span class="sxs-lookup"><span data-stu-id="83ddd-127">The original pointer can therefore be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83ddd-128">需求</span><span class="sxs-lookup"><span data-stu-id="83ddd-128">Requirements</span></span>  
 <span data-ttu-id="83ddd-129">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="83ddd-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83ddd-130">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="83ddd-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="83ddd-131">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="83ddd-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="83ddd-132">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83ddd-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83ddd-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="83ddd-133">See Also</span></span>  
 [<span data-ttu-id="83ddd-134">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="83ddd-134">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="83ddd-135">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="83ddd-135">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
