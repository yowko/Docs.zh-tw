---
title: "IHostTaskManager::SetUILocale 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 099c3d4878e7dd83be9240e121777c71c2890c88
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanagersetuilocale-method"></a><span data-ttu-id="2aead-102">IHostTaskManager::SetUILocale 方法</span><span class="sxs-lookup"><span data-stu-id="2aead-102">IHostTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="2aead-103">通知主機 common language runtime (CLR) 已變更的使用者介面 (UI) 的地區設定或文化特性，在目前執行的工作。</span><span class="sxs-lookup"><span data-stu-id="2aead-103">Notifies the host that the common language runtime (CLR) has changed the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2aead-104">語法</span><span class="sxs-lookup"><span data-stu-id="2aead-104">Syntax</span></span>  
  
```  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2aead-105">參數</span><span class="sxs-lookup"><span data-stu-id="2aead-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="2aead-106">[in]可對應至新指派的地理文化特性和語言的地區設定識別碼值。</span><span class="sxs-lookup"><span data-stu-id="2aead-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2aead-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="2aead-107">Return Value</span></span>  
  
|<span data-ttu-id="2aead-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2aead-108">HRESULT</span></span>|<span data-ttu-id="2aead-109">描述</span><span class="sxs-lookup"><span data-stu-id="2aead-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2aead-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2aead-110">S_OK</span></span>|<span data-ttu-id="2aead-111">`SetUILocale`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="2aead-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="2aead-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2aead-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2aead-113">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="2aead-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2aead-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2aead-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2aead-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="2aead-115">The call timed out.</span></span>|  
|<span data-ttu-id="2aead-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2aead-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2aead-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="2aead-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2aead-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2aead-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2aead-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="2aead-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2aead-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2aead-120">E_FAIL</span></span>|<span data-ttu-id="2aead-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="2aead-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2aead-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="2aead-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2aead-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="2aead-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2aead-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="2aead-124">E_NOTIMPL</span></span>|<span data-ttu-id="2aead-125">主機不允許受管理的使用者程式碼變更的 UI 文化特性。</span><span class="sxs-lookup"><span data-stu-id="2aead-125">The host does not allow managed user code to change the UI culture.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2aead-126">備註</span><span class="sxs-lookup"><span data-stu-id="2aead-126">Remarks</span></span>  
 <span data-ttu-id="2aead-127">執行階段呼叫`SetUILocale`時的值<xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType>屬性變更的 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="2aead-127">The runtime calls `SetUILocale` when the value of the <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="2aead-128">這個方法會提供主機執行之同步處理的地區設定中可能會有任何機制的機會。</span><span class="sxs-lookup"><span data-stu-id="2aead-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="2aead-129">如果主機不允許從 managed 程式碼變更的 UI 地區設定，或未實作的機制，同步處理地區設定，則會傳回 E_NOTIMPL 從這個方法。</span><span class="sxs-lookup"><span data-stu-id="2aead-129">If a host does not allow the UI locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2aead-130">需求</span><span class="sxs-lookup"><span data-stu-id="2aead-130">Requirements</span></span>  
 <span data-ttu-id="2aead-131">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2aead-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2aead-132">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2aead-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2aead-133">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2aead-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2aead-134">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2aead-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2aead-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="2aead-135">See Also</span></span>  
 [<span data-ttu-id="2aead-136">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="2aead-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="2aead-137">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="2aead-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="2aead-138">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="2aead-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="2aead-139">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="2aead-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="2aead-140">SetLocale 方法</span><span class="sxs-lookup"><span data-stu-id="2aead-140">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)
