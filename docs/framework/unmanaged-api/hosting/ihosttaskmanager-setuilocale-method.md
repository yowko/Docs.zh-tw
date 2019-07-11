---
title: IHostTaskManager::SetUILocale 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetUILocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetUILocale
helpviewer_keywords:
- SetUILocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetUILocale method [.NET Framework hosting]
ms.assetid: d0c87a9c-ea81-4237-a16b-c22b36ec9dc8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 173eda2882ca9172c840d0d4fa65ef972fd779da
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749332"
---
# <a name="ihosttaskmanagersetuilocale-method"></a><span data-ttu-id="fc91e-102">IHostTaskManager::SetUILocale 方法</span><span class="sxs-lookup"><span data-stu-id="fc91e-102">IHostTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="fc91e-103">Common language runtime (CLR) 已變更的使用者介面 (UI) 的地區設定或在目前執行之工作的文化特性，會告知主應用程式。</span><span class="sxs-lookup"><span data-stu-id="fc91e-103">Notifies the host that the common language runtime (CLR) has changed the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc91e-104">語法</span><span class="sxs-lookup"><span data-stu-id="fc91e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc91e-105">參數</span><span class="sxs-lookup"><span data-stu-id="fc91e-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="fc91e-106">[in]可對應到新指派的地理文化特性和語言的地區設定識別碼值。</span><span class="sxs-lookup"><span data-stu-id="fc91e-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc91e-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="fc91e-107">Return Value</span></span>  
  
|<span data-ttu-id="fc91e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fc91e-108">HRESULT</span></span>|<span data-ttu-id="fc91e-109">描述</span><span class="sxs-lookup"><span data-stu-id="fc91e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fc91e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fc91e-110">S_OK</span></span>|<span data-ttu-id="fc91e-111">`SetUILocale` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="fc91e-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="fc91e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fc91e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fc91e-113">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="fc91e-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fc91e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fc91e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fc91e-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="fc91e-115">The call timed out.</span></span>|  
|<span data-ttu-id="fc91e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fc91e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fc91e-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="fc91e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fc91e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fc91e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fc91e-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="fc91e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fc91e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fc91e-120">E_FAIL</span></span>|<span data-ttu-id="fc91e-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="fc91e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fc91e-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="fc91e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fc91e-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="fc91e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fc91e-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="fc91e-124">E_NOTIMPL</span></span>|<span data-ttu-id="fc91e-125">主機不允許受管理的使用者程式碼變更的 UI 文化特性。</span><span class="sxs-lookup"><span data-stu-id="fc91e-125">The host does not allow managed user code to change the UI culture.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc91e-126">備註</span><span class="sxs-lookup"><span data-stu-id="fc91e-126">Remarks</span></span>  
 <span data-ttu-id="fc91e-127">執行階段會呼叫`SetUILocale`時的值<xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType>屬性變更時，managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="fc91e-127">The runtime calls `SetUILocale` when the value of the <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="fc91e-128">這個方法便有機會執行同步處理的地區設定中可能會有任何機制主機。</span><span class="sxs-lookup"><span data-stu-id="fc91e-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="fc91e-129">若主機不允許從 managed 程式碼變更的 UI 地區設定，或未實作的機制來同步處理地區設定，應從這個方法會傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="fc91e-129">If a host does not allow the UI locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc91e-130">需求</span><span class="sxs-lookup"><span data-stu-id="fc91e-130">Requirements</span></span>  
 <span data-ttu-id="fc91e-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fc91e-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc91e-132">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fc91e-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fc91e-133">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="fc91e-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fc91e-134">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc91e-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc91e-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc91e-135">See also</span></span>

- [<span data-ttu-id="fc91e-136">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="fc91e-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="fc91e-137">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="fc91e-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="fc91e-138">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="fc91e-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="fc91e-139">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="fc91e-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="fc91e-140">SetLocale 方法</span><span class="sxs-lookup"><span data-stu-id="fc91e-140">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)
