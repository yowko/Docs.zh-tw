---
title: IHostSecurityManager::SetThreadToken 方法
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.SetThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::SetThreadToken
helpviewer_keywords:
- SetThreadToken method [.NET Framework hosting]
- IHostSecurityManager::SetThreadToken method [.NET Framework hosting]
ms.assetid: e951c345-8a86-4587-911b-a1a57bc6428a
topic_type:
- apiref
ms.openlocfilehash: 5a2b2e5560c292598f0110de9445eb66ba794997
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683104"
---
# <a name="ihostsecuritymanagersetthreadtoken-method"></a><span data-ttu-id="ebbfa-102">IHostSecurityManager::SetThreadToken 方法</span><span class="sxs-lookup"><span data-stu-id="ebbfa-102">IHostSecurityManager::SetThreadToken Method</span></span>

<span data-ttu-id="ebbfa-103">設定目前執行中線程的控制碼。</span><span class="sxs-lookup"><span data-stu-id="ebbfa-103">Sets a handle for the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebbfa-104">語法</span><span class="sxs-lookup"><span data-stu-id="ebbfa-104">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadToken (  
    [in] HANDLE hToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ebbfa-105">參數</span><span class="sxs-lookup"><span data-stu-id="ebbfa-105">Parameters</span></span>  

 `hToken`  
 <span data-ttu-id="ebbfa-106">在要為目前執行中的執行緒設定的權杖控制碼。</span><span class="sxs-lookup"><span data-stu-id="ebbfa-106">[in] A handle to the token to set for the currently executing thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ebbfa-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="ebbfa-107">Return Value</span></span>  
  
|<span data-ttu-id="ebbfa-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ebbfa-108">HRESULT</span></span>|<span data-ttu-id="ebbfa-109">描述</span><span class="sxs-lookup"><span data-stu-id="ebbfa-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ebbfa-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ebbfa-110">S_OK</span></span>|<span data-ttu-id="ebbfa-111">`SetThreadToken` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="ebbfa-111">`SetThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="ebbfa-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ebbfa-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ebbfa-113">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="ebbfa-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ebbfa-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ebbfa-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ebbfa-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="ebbfa-115">The call timed out.</span></span>|  
|<span data-ttu-id="ebbfa-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ebbfa-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ebbfa-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="ebbfa-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ebbfa-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ebbfa-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ebbfa-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="ebbfa-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ebbfa-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ebbfa-120">E_FAIL</span></span>|<span data-ttu-id="ebbfa-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="ebbfa-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ebbfa-122">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="ebbfa-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ebbfa-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="ebbfa-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ebbfa-124">備註</span><span class="sxs-lookup"><span data-stu-id="ebbfa-124">Remarks</span></span>  

 <span data-ttu-id="ebbfa-125">`IHostSecurityManager::SetThreadToken` 與相同名稱的對應 Win32 函數類似，不同之處在于 Win32 函數可讓呼叫端傳入任意執行緒的控制碼，而 `IHostSecurityManager::SetThreadToken` 只可將權杖與目前執行中的執行緒產生關聯。</span><span class="sxs-lookup"><span data-stu-id="ebbfa-125">`IHostSecurityManager::SetThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::SetThreadToken` can associate a token only with the currently executing thread.</span></span>  
  
 <span data-ttu-id="ebbfa-126">此 `HANDLE` 類型與 COM 不相容; 也就是說，它的大小是作業系統專用的，且需要自訂封送處理。</span><span class="sxs-lookup"><span data-stu-id="ebbfa-126">The `HANDLE` type is not COM-compliant; that is, its size is specific to an operating system and it requires custom marshaling.</span></span> <span data-ttu-id="ebbfa-127">因此，此權杖僅適用于在 CLR 與主機之間的進程內。</span><span class="sxs-lookup"><span data-stu-id="ebbfa-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebbfa-128">需求</span><span class="sxs-lookup"><span data-stu-id="ebbfa-128">Requirements</span></span>  

 <span data-ttu-id="ebbfa-129">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ebbfa-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebbfa-130">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="ebbfa-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ebbfa-131">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="ebbfa-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ebbfa-132">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebbfa-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebbfa-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ebbfa-133">See also</span></span>

- [<span data-ttu-id="ebbfa-134">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="ebbfa-134">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="ebbfa-135">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="ebbfa-135">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
