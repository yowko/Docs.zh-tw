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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71f5cdfaf47c55107980edf089f8964c5936fb23
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440982"
---
# <a name="ihostsecuritymanagersetthreadtoken-method"></a><span data-ttu-id="dc160-102">IHostSecurityManager::SetThreadToken 方法</span><span class="sxs-lookup"><span data-stu-id="dc160-102">IHostSecurityManager::SetThreadToken Method</span></span>
<span data-ttu-id="dc160-103">設定目前執行中執行緒的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="dc160-103">Sets a handle for the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc160-104">語法</span><span class="sxs-lookup"><span data-stu-id="dc160-104">Syntax</span></span>  
  
```  
HRESULT SetThreadToken (  
    [in] HANDLE hToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dc160-105">參數</span><span class="sxs-lookup"><span data-stu-id="dc160-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="dc160-106">[in]若要設定的目前執行中執行緒語彙基元控制代碼。</span><span class="sxs-lookup"><span data-stu-id="dc160-106">[in] A handle to the token to set for the currently executing thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dc160-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="dc160-107">Return Value</span></span>  
  
|<span data-ttu-id="dc160-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dc160-108">HRESULT</span></span>|<span data-ttu-id="dc160-109">描述</span><span class="sxs-lookup"><span data-stu-id="dc160-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dc160-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="dc160-110">S_OK</span></span>|<span data-ttu-id="dc160-111">`SetThreadToken` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="dc160-111">`SetThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="dc160-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dc160-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dc160-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="dc160-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dc160-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dc160-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dc160-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="dc160-115">The call timed out.</span></span>|  
|<span data-ttu-id="dc160-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dc160-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dc160-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="dc160-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dc160-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dc160-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dc160-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="dc160-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dc160-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dc160-120">E_FAIL</span></span>|<span data-ttu-id="dc160-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="dc160-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dc160-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="dc160-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dc160-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="dc160-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc160-124">備註</span><span class="sxs-lookup"><span data-stu-id="dc160-124">Remarks</span></span>  
 <span data-ttu-id="dc160-125">`IHostSecurityManager::SetThreadToken` 行為類似對應的 Win32 函式的名稱相同，不同之處在於 Win32 函式可讓呼叫端来傳入任意的執行緒控制代碼，而`IHostSecurityManager::SetThreadToken`可以建立只與目前執行中執行緒關聯語彙基元。</span><span class="sxs-lookup"><span data-stu-id="dc160-125">`IHostSecurityManager::SetThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::SetThreadToken` can associate a token only with the currently executing thread.</span></span>  
  
 <span data-ttu-id="dc160-126">`HANDLE`類型不是 COM 相容; 也就是它的大小是特定的作業系統，它需要自訂封送處理。</span><span class="sxs-lookup"><span data-stu-id="dc160-126">The `HANDLE` type is not COM-compliant; that is, its size is specific to an operating system and it requires custom marshaling.</span></span> <span data-ttu-id="dc160-127">因此，這個語彙基元是僅供處理程序，則 CLR 與主機之間。</span><span class="sxs-lookup"><span data-stu-id="dc160-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc160-128">需求</span><span class="sxs-lookup"><span data-stu-id="dc160-128">Requirements</span></span>  
 <span data-ttu-id="dc160-129">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dc160-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc160-130">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dc160-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dc160-131">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="dc160-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dc160-132">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc160-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc160-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc160-133">See Also</span></span>  
 [<span data-ttu-id="dc160-134">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="dc160-134">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="dc160-135">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="dc160-135">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
