---
title: "IHostTaskManager::SetLocale 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.SetLocale
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: 747ee407-ee8c-484d-9583-25089236d2d1
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 885dd41a3bc5afb156d1f338fb3564731d5a742a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagersetlocale-method"></a><span data-ttu-id="11fc8-102">IHostTaskManager::SetLocale 方法</span><span class="sxs-lookup"><span data-stu-id="11fc8-102">IHostTaskManager::SetLocale Method</span></span>
<span data-ttu-id="11fc8-103">通知主機 common language runtime (CLR) 已變更地區設定或文化特性，在目前執行的工作。</span><span class="sxs-lookup"><span data-stu-id="11fc8-103">Notifies the host that the common language runtime (CLR) has changed the locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11fc8-104">語法</span><span class="sxs-lookup"><span data-stu-id="11fc8-104">Syntax</span></span>  
  
```  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="11fc8-105">參數</span><span class="sxs-lookup"><span data-stu-id="11fc8-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="11fc8-106">[in]可對應至新指派的地理文化特性和語言的地區設定識別碼值。</span><span class="sxs-lookup"><span data-stu-id="11fc8-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="11fc8-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="11fc8-107">Return Value</span></span>  
  
|<span data-ttu-id="11fc8-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="11fc8-108">HRESULT</span></span>|<span data-ttu-id="11fc8-109">描述</span><span class="sxs-lookup"><span data-stu-id="11fc8-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="11fc8-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="11fc8-110">S_OK</span></span>|<span data-ttu-id="11fc8-111">`SetLocale`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="11fc8-111">`SetLocale` returned successfully.</span></span>|  
|<span data-ttu-id="11fc8-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="11fc8-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="11fc8-113">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="11fc8-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="11fc8-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="11fc8-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="11fc8-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="11fc8-115">The call timed out.</span></span>|  
|<span data-ttu-id="11fc8-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="11fc8-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="11fc8-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="11fc8-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="11fc8-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="11fc8-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="11fc8-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="11fc8-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="11fc8-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="11fc8-120">E_FAIL</span></span>|<span data-ttu-id="11fc8-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="11fc8-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="11fc8-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="11fc8-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="11fc8-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="11fc8-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="11fc8-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="11fc8-124">E_NOTIMPL</span></span>|<span data-ttu-id="11fc8-125">主機不允許修改的地區設定的受管理的使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="11fc8-125">The host does not allow managed user code to modify the locale.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11fc8-126">備註</span><span class="sxs-lookup"><span data-stu-id="11fc8-126">Remarks</span></span>  
 <span data-ttu-id="11fc8-127">執行階段呼叫`SetLocale`時的值<xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType>屬性變更的 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="11fc8-127">The runtime calls `SetLocale` when the value of the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="11fc8-128">這個方法會提供主機執行之同步處理的地區設定中可能會有任何機制的機會。</span><span class="sxs-lookup"><span data-stu-id="11fc8-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="11fc8-129">如果主機不允許從 managed 程式碼中變更地區設定，或未實作的機制，同步處理地區設定，則會傳回 E_NOTIMPL 從這個方法。</span><span class="sxs-lookup"><span data-stu-id="11fc8-129">If a host does not allow the locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11fc8-130">需求</span><span class="sxs-lookup"><span data-stu-id="11fc8-130">Requirements</span></span>  
 <span data-ttu-id="11fc8-131">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="11fc8-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11fc8-132">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="11fc8-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="11fc8-133">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="11fc8-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="11fc8-134">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11fc8-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11fc8-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11fc8-135">See Also</span></span>  
 [<span data-ttu-id="11fc8-136">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="11fc8-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="11fc8-137">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="11fc8-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="11fc8-138">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="11fc8-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="11fc8-139">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="11fc8-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="11fc8-140">SetUILocale 方法</span><span class="sxs-lookup"><span data-stu-id="11fc8-140">SetUILocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)
