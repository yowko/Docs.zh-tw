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
ms.openlocfilehash: 7760e178984798fac5cde2e8c0143a9c8716a212
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672753"
---
# <a name="ihostsecuritycontextcapture-method"></a><span data-ttu-id="25ca5-102">IHostSecurityContext::Capture 方法</span><span class="sxs-lookup"><span data-stu-id="25ca5-102">IHostSecurityContext::Capture Method</span></span>

<span data-ttu-id="25ca5-103">取得從呼叫[IHostSecurityManager：： GetSecurityCoNtext](ihostsecuritymanager-getsecuritycontext-method.md)傳回之[IHostSecurityCoNtext](ihostsecuritycontext-interface.md)實例的複製。</span><span class="sxs-lookup"><span data-stu-id="25ca5-103">Gets a clone of the [IHostSecurityContext](ihostsecuritycontext-interface.md) instance returned from a call to [IHostSecurityManager::GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25ca5-104">語法</span><span class="sxs-lookup"><span data-stu-id="25ca5-104">Syntax</span></span>  
  
```cpp
HRESULT Capture (  
    [out] IHostSecurityContext** ppClonedContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25ca5-105">參數</span><span class="sxs-lookup"><span data-stu-id="25ca5-105">Parameters</span></span>  

 `ppClonedContext`  
 <span data-ttu-id="25ca5-106">擴展要捕捉之物件的複本位址指標 `IHostSecurityContext` 。</span><span class="sxs-lookup"><span data-stu-id="25ca5-106">[out] A pointer to the address of a clone of the `IHostSecurityContext` object to be captured.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25ca5-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="25ca5-107">Return Value</span></span>  
  
|<span data-ttu-id="25ca5-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="25ca5-108">HRESULT</span></span>|<span data-ttu-id="25ca5-109">描述</span><span class="sxs-lookup"><span data-stu-id="25ca5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="25ca5-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="25ca5-110">S_OK</span></span>|<span data-ttu-id="25ca5-111">`Capture` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="25ca5-111">`Capture` returned successfully.</span></span>|  
|<span data-ttu-id="25ca5-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="25ca5-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="25ca5-113">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="25ca5-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="25ca5-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="25ca5-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="25ca5-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="25ca5-115">The call timed out.</span></span>|  
|<span data-ttu-id="25ca5-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="25ca5-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="25ca5-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="25ca5-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="25ca5-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="25ca5-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="25ca5-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="25ca5-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="25ca5-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="25ca5-120">E_FAIL</span></span>|<span data-ttu-id="25ca5-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="25ca5-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="25ca5-122">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="25ca5-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="25ca5-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="25ca5-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25ca5-124">備註</span><span class="sxs-lookup"><span data-stu-id="25ca5-124">Remarks</span></span>  

 <span data-ttu-id="25ca5-125">從傳回的介面指標 `Capture` 是所捕獲內容的複本。</span><span class="sxs-lookup"><span data-stu-id="25ca5-125">The interface pointer returned from `Capture` is a clone of the captured context.</span></span> <span data-ttu-id="25ca5-126">當這項資訊跨非同步程式碼點移動時，其存留期會與進行呼叫的指標分隔開來。</span><span class="sxs-lookup"><span data-stu-id="25ca5-126">When this information is moved across an asynchronous code point, its lifetime is separated from that of the pointer against which the call was made.</span></span> <span data-ttu-id="25ca5-127">因此，可以釋放原始指標。</span><span class="sxs-lookup"><span data-stu-id="25ca5-127">The original pointer can therefore be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25ca5-128">需求</span><span class="sxs-lookup"><span data-stu-id="25ca5-128">Requirements</span></span>  

 <span data-ttu-id="25ca5-129">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="25ca5-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25ca5-130">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="25ca5-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="25ca5-131">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="25ca5-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="25ca5-132">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25ca5-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25ca5-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25ca5-133">See also</span></span>

- [<span data-ttu-id="25ca5-134">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="25ca5-134">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="25ca5-135">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="25ca5-135">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
