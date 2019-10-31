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
ms.openlocfilehash: 96bb3a530bf4c63c3662ecfa635a929381fc0de6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121528"
---
# <a name="ihostsecuritycontextcapture-method"></a><span data-ttu-id="1f051-102">IHostSecurityContext::Capture 方法</span><span class="sxs-lookup"><span data-stu-id="1f051-102">IHostSecurityContext::Capture Method</span></span>
<span data-ttu-id="1f051-103">取得從[IHostSecurityManager：： GetSecurityCoNtext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)的呼叫所傳回的[IHostSecurityCoNtext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)實例複本。</span><span class="sxs-lookup"><span data-stu-id="1f051-103">Gets a clone of the [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) instance returned from a call to [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f051-104">語法</span><span class="sxs-lookup"><span data-stu-id="1f051-104">Syntax</span></span>  
  
```cpp
HRESULT Capture (  
    [out] IHostSecurityContext** ppClonedContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f051-105">參數</span><span class="sxs-lookup"><span data-stu-id="1f051-105">Parameters</span></span>  
 `ppClonedContext`  
 <span data-ttu-id="1f051-106">脫銷要捕捉的 `IHostSecurityContext` 物件之複本位址的指標。</span><span class="sxs-lookup"><span data-stu-id="1f051-106">[out] A pointer to the address of a clone of the `IHostSecurityContext` object to be captured.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f051-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="1f051-107">Return Value</span></span>  
  
|<span data-ttu-id="1f051-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1f051-108">HRESULT</span></span>|<span data-ttu-id="1f051-109">描述</span><span class="sxs-lookup"><span data-stu-id="1f051-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1f051-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1f051-110">S_OK</span></span>|<span data-ttu-id="1f051-111">已成功傳回 `Capture`。</span><span class="sxs-lookup"><span data-stu-id="1f051-111">`Capture` returned successfully.</span></span>|  
|<span data-ttu-id="1f051-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1f051-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1f051-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="1f051-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1f051-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1f051-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1f051-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="1f051-115">The call timed out.</span></span>|  
|<span data-ttu-id="1f051-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1f051-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1f051-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="1f051-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1f051-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1f051-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1f051-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="1f051-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1f051-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1f051-120">E_FAIL</span></span>|<span data-ttu-id="1f051-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="1f051-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1f051-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="1f051-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1f051-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="1f051-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f051-124">備註</span><span class="sxs-lookup"><span data-stu-id="1f051-124">Remarks</span></span>  
 <span data-ttu-id="1f051-125">從 `Capture` 傳回的介面指標是已捕捉內容的複本。</span><span class="sxs-lookup"><span data-stu-id="1f051-125">The interface pointer returned from `Capture` is a clone of the captured context.</span></span> <span data-ttu-id="1f051-126">當這項資訊在非同步程式碼點上移動時，其存留期會與進行呼叫的指標分開。</span><span class="sxs-lookup"><span data-stu-id="1f051-126">When this information is moved across an asynchronous code point, its lifetime is separated from that of the pointer against which the call was made.</span></span> <span data-ttu-id="1f051-127">因此，可以釋放原始指標。</span><span class="sxs-lookup"><span data-stu-id="1f051-127">The original pointer can therefore be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f051-128">需求</span><span class="sxs-lookup"><span data-stu-id="1f051-128">Requirements</span></span>  
 <span data-ttu-id="1f051-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1f051-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f051-130">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="1f051-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1f051-131">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1f051-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1f051-132">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f051-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f051-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="1f051-133">See also</span></span>

- [<span data-ttu-id="1f051-134">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="1f051-134">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="1f051-135">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="1f051-135">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
