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
ms.openlocfilehash: aa17f637ef71373697db5ce66e4a6540c5cc5fbd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139489"
---
# <a name="ihostsecuritymanagersetthreadtoken-method"></a><span data-ttu-id="f9575-102">IHostSecurityManager::SetThreadToken 方法</span><span class="sxs-lookup"><span data-stu-id="f9575-102">IHostSecurityManager::SetThreadToken Method</span></span>
<span data-ttu-id="f9575-103">設定目前執行中線程的控制碼。</span><span class="sxs-lookup"><span data-stu-id="f9575-103">Sets a handle for the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9575-104">語法</span><span class="sxs-lookup"><span data-stu-id="f9575-104">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadToken (  
    [in] HANDLE hToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9575-105">參數</span><span class="sxs-lookup"><span data-stu-id="f9575-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="f9575-106">在要為目前執行的執行緒設定之標記的控制碼。</span><span class="sxs-lookup"><span data-stu-id="f9575-106">[in] A handle to the token to set for the currently executing thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9575-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="f9575-107">Return Value</span></span>  
  
|<span data-ttu-id="f9575-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f9575-108">HRESULT</span></span>|<span data-ttu-id="f9575-109">描述</span><span class="sxs-lookup"><span data-stu-id="f9575-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f9575-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f9575-110">S_OK</span></span>|<span data-ttu-id="f9575-111">已成功傳回 `SetThreadToken`。</span><span class="sxs-lookup"><span data-stu-id="f9575-111">`SetThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="f9575-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f9575-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f9575-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="f9575-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f9575-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f9575-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f9575-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="f9575-115">The call timed out.</span></span>|  
|<span data-ttu-id="f9575-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f9575-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f9575-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="f9575-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f9575-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f9575-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f9575-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="f9575-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f9575-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f9575-120">E_FAIL</span></span>|<span data-ttu-id="f9575-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="f9575-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f9575-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="f9575-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f9575-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="f9575-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9575-124">備註</span><span class="sxs-lookup"><span data-stu-id="f9575-124">Remarks</span></span>  
 <span data-ttu-id="f9575-125">`IHostSecurityManager::SetThreadToken` 的行為類似于相同名稱的對應 Win32 函式，不同之處在于 Win32 函式允許呼叫端將控制碼傳入任意執行緒，而 `IHostSecurityManager::SetThreadToken` 只能將權杖與目前執行中的執行緒產生關聯。</span><span class="sxs-lookup"><span data-stu-id="f9575-125">`IHostSecurityManager::SetThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::SetThreadToken` can associate a token only with the currently executing thread.</span></span>  
  
 <span data-ttu-id="f9575-126">`HANDLE` 類型不符合 COM 規範;也就是說，它的大小是作業系統特有的，而且需要自訂封送處理。</span><span class="sxs-lookup"><span data-stu-id="f9575-126">The `HANDLE` type is not COM-compliant; that is, its size is specific to an operating system and it requires custom marshaling.</span></span> <span data-ttu-id="f9575-127">因此，此權杖僅適用于在進程內的 CLR 與主控制項之間使用。</span><span class="sxs-lookup"><span data-stu-id="f9575-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9575-128">需求</span><span class="sxs-lookup"><span data-stu-id="f9575-128">Requirements</span></span>  
 <span data-ttu-id="f9575-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f9575-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9575-130">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="f9575-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f9575-131">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f9575-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f9575-132">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9575-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9575-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="f9575-133">See also</span></span>

- [<span data-ttu-id="f9575-134">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="f9575-134">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="f9575-135">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="f9575-135">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
