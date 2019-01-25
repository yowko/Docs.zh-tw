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
ms.openlocfilehash: cf29b906d524138fdd78b7a4f0286d1c59adc8eb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622116"
---
# <a name="ihostsecuritymanagersetthreadtoken-method"></a><span data-ttu-id="11953-102">IHostSecurityManager::SetThreadToken 方法</span><span class="sxs-lookup"><span data-stu-id="11953-102">IHostSecurityManager::SetThreadToken Method</span></span>
<span data-ttu-id="11953-103">設定目前執行中執行緒的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="11953-103">Sets a handle for the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11953-104">語法</span><span class="sxs-lookup"><span data-stu-id="11953-104">Syntax</span></span>  
  
```  
HRESULT SetThreadToken (  
    [in] HANDLE hToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="11953-105">參數</span><span class="sxs-lookup"><span data-stu-id="11953-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="11953-106">[in]若要設定的目前執行中執行緒的語彙基元控制代碼。</span><span class="sxs-lookup"><span data-stu-id="11953-106">[in] A handle to the token to set for the currently executing thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="11953-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="11953-107">Return Value</span></span>  
  
|<span data-ttu-id="11953-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="11953-108">HRESULT</span></span>|<span data-ttu-id="11953-109">描述</span><span class="sxs-lookup"><span data-stu-id="11953-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="11953-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="11953-110">S_OK</span></span>|<span data-ttu-id="11953-111">`SetThreadToken` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="11953-111">`SetThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="11953-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="11953-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="11953-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="11953-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="11953-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="11953-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="11953-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="11953-115">The call timed out.</span></span>|  
|<span data-ttu-id="11953-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="11953-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="11953-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="11953-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="11953-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="11953-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="11953-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="11953-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="11953-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="11953-120">E_FAIL</span></span>|<span data-ttu-id="11953-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="11953-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="11953-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="11953-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="11953-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="11953-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11953-124">備註</span><span class="sxs-lookup"><span data-stu-id="11953-124">Remarks</span></span>  
 <span data-ttu-id="11953-125">`IHostSecurityManager::SetThreadToken` 行為類似對應的 Win32 函式的名稱相同，不同之處在於 Win32 函式可讓呼叫者傳入任意的執行緒控制代碼，而`IHostSecurityManager::SetThreadToken`可以建立只與目前執行中執行緒關聯語彙基元。</span><span class="sxs-lookup"><span data-stu-id="11953-125">`IHostSecurityManager::SetThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::SetThreadToken` can associate a token only with the currently executing thread.</span></span>  
  
 <span data-ttu-id="11953-126">`HANDLE`類型不是 COM 相容; 也就是它的大小是特定的作業系統，它需要自訂封送處理。</span><span class="sxs-lookup"><span data-stu-id="11953-126">The `HANDLE` type is not COM-compliant; that is, its size is specific to an operating system and it requires custom marshaling.</span></span> <span data-ttu-id="11953-127">因此，此權杖是只在處理序中，CLR 和主機之間使用。</span><span class="sxs-lookup"><span data-stu-id="11953-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11953-128">需求</span><span class="sxs-lookup"><span data-stu-id="11953-128">Requirements</span></span>  
 <span data-ttu-id="11953-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="11953-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11953-130">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="11953-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="11953-131">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="11953-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="11953-132">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11953-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11953-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11953-133">See also</span></span>
- [<span data-ttu-id="11953-134">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="11953-134">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="11953-135">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="11953-135">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
