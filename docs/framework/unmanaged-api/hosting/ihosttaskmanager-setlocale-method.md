---
title: IHostTaskManager::SetLocale 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: 747ee407-ee8c-484d-9583-25089236d2d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 77f0196e667e2d7bb148c07218a7e39f52a37809
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474311"
---
# <a name="ihosttaskmanagersetlocale-method"></a><span data-ttu-id="4054f-102">IHostTaskManager::SetLocale 方法</span><span class="sxs-lookup"><span data-stu-id="4054f-102">IHostTaskManager::SetLocale Method</span></span>
<span data-ttu-id="4054f-103">Common language runtime (CLR) 已變更的地區設定或在目前執行之工作的文化特性，會告知主應用程式。</span><span class="sxs-lookup"><span data-stu-id="4054f-103">Notifies the host that the common language runtime (CLR) has changed the locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4054f-104">語法</span><span class="sxs-lookup"><span data-stu-id="4054f-104">Syntax</span></span>  
  
```  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4054f-105">參數</span><span class="sxs-lookup"><span data-stu-id="4054f-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="4054f-106">[in]可對應到新指派的地理文化特性和語言的地區設定識別碼值。</span><span class="sxs-lookup"><span data-stu-id="4054f-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4054f-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="4054f-107">Return Value</span></span>  
  
|<span data-ttu-id="4054f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4054f-108">HRESULT</span></span>|<span data-ttu-id="4054f-109">描述</span><span class="sxs-lookup"><span data-stu-id="4054f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4054f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4054f-110">S_OK</span></span>|<span data-ttu-id="4054f-111">`SetLocale` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="4054f-111">`SetLocale` returned successfully.</span></span>|  
|<span data-ttu-id="4054f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4054f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4054f-113">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="4054f-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4054f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4054f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4054f-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="4054f-115">The call timed out.</span></span>|  
|<span data-ttu-id="4054f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4054f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4054f-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="4054f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4054f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4054f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4054f-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="4054f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4054f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4054f-120">E_FAIL</span></span>|<span data-ttu-id="4054f-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="4054f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4054f-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="4054f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4054f-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="4054f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4054f-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="4054f-124">E_NOTIMPL</span></span>|<span data-ttu-id="4054f-125">主機不允許受管理的使用者程式碼，以修改的地區設定。</span><span class="sxs-lookup"><span data-stu-id="4054f-125">The host does not allow managed user code to modify the locale.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4054f-126">備註</span><span class="sxs-lookup"><span data-stu-id="4054f-126">Remarks</span></span>  
 <span data-ttu-id="4054f-127">執行階段會呼叫`SetLocale`時的值<xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType>屬性變更時，managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="4054f-127">The runtime calls `SetLocale` when the value of the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="4054f-128">這個方法便有機會執行同步處理的地區設定中可能會有任何機制主機。</span><span class="sxs-lookup"><span data-stu-id="4054f-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="4054f-129">若主機不允許從 managed 程式碼變更的地區設定，或未實作的機制來同步處理地區設定，應從這個方法會傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="4054f-129">If a host does not allow the locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4054f-130">需求</span><span class="sxs-lookup"><span data-stu-id="4054f-130">Requirements</span></span>  
 <span data-ttu-id="4054f-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4054f-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4054f-132">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4054f-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4054f-133">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4054f-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4054f-134">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4054f-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4054f-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4054f-135">See also</span></span>
- [<span data-ttu-id="4054f-136">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="4054f-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="4054f-137">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="4054f-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="4054f-138">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="4054f-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="4054f-139">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="4054f-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="4054f-140">SetUILocale 方法</span><span class="sxs-lookup"><span data-stu-id="4054f-140">SetUILocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)
