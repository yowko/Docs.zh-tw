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
ms.openlocfilehash: c8b4d4c7edec47ab4acaae2a5cd93ad474612063
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855534"
---
# <a name="ihostsecuritycontextcapture-method"></a><span data-ttu-id="7cbf1-102">IHostSecurityContext::Capture 方法</span><span class="sxs-lookup"><span data-stu-id="7cbf1-102">IHostSecurityContext::Capture Method</span></span>
<span data-ttu-id="7cbf1-103">取得從[IHostSecurityManager：： GetSecurityCoNtext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)的呼叫所傳回的[IHostSecurityCoNtext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)實例複本。</span><span class="sxs-lookup"><span data-stu-id="7cbf1-103">Gets a clone of the [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) instance returned from a call to [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cbf1-104">語法</span><span class="sxs-lookup"><span data-stu-id="7cbf1-104">Syntax</span></span>  
  
```cpp
HRESULT Capture (  
    [out] IHostSecurityContext** ppClonedContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7cbf1-105">參數</span><span class="sxs-lookup"><span data-stu-id="7cbf1-105">Parameters</span></span>  
 `ppClonedContext`  
 <span data-ttu-id="7cbf1-106">脫銷要捕捉之`IHostSecurityContext`物件的複本位址指標。</span><span class="sxs-lookup"><span data-stu-id="7cbf1-106">[out] A pointer to the address of a clone of the `IHostSecurityContext` object to be captured.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7cbf1-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="7cbf1-107">Return Value</span></span>  
  
|<span data-ttu-id="7cbf1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7cbf1-108">HRESULT</span></span>|<span data-ttu-id="7cbf1-109">描述</span><span class="sxs-lookup"><span data-stu-id="7cbf1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7cbf1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7cbf1-110">S_OK</span></span>|<span data-ttu-id="7cbf1-111">`Capture`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="7cbf1-111">`Capture` returned successfully.</span></span>|  
|<span data-ttu-id="7cbf1-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7cbf1-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7cbf1-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="7cbf1-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7cbf1-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7cbf1-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7cbf1-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="7cbf1-115">The call timed out.</span></span>|  
|<span data-ttu-id="7cbf1-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7cbf1-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7cbf1-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="7cbf1-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7cbf1-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7cbf1-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7cbf1-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="7cbf1-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7cbf1-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7cbf1-120">E_FAIL</span></span>|<span data-ttu-id="7cbf1-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="7cbf1-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7cbf1-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="7cbf1-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7cbf1-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="7cbf1-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7cbf1-124">備註</span><span class="sxs-lookup"><span data-stu-id="7cbf1-124">Remarks</span></span>  
 <span data-ttu-id="7cbf1-125">從`Capture`傳回的介面指標是已捕捉內容的複本。</span><span class="sxs-lookup"><span data-stu-id="7cbf1-125">The interface pointer returned from `Capture` is a clone of the captured context.</span></span> <span data-ttu-id="7cbf1-126">當這項資訊在非同步程式碼點上移動時，其存留期會與進行呼叫的指標分開。</span><span class="sxs-lookup"><span data-stu-id="7cbf1-126">When this information is moved across an asynchronous code point, its lifetime is separated from that of the pointer against which the call was made.</span></span> <span data-ttu-id="7cbf1-127">因此，可以釋放原始指標。</span><span class="sxs-lookup"><span data-stu-id="7cbf1-127">The original pointer can therefore be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cbf1-128">需求</span><span class="sxs-lookup"><span data-stu-id="7cbf1-128">Requirements</span></span>  
 <span data-ttu-id="7cbf1-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7cbf1-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cbf1-130">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7cbf1-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7cbf1-131">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7cbf1-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7cbf1-132">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cbf1-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cbf1-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7cbf1-133">See also</span></span>

- [<span data-ttu-id="7cbf1-134">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="7cbf1-134">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="7cbf1-135">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="7cbf1-135">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
