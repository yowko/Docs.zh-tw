---
title: "ICLRTaskManager::SetLocale 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTaskManager.SetLocale
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: ed16bb7f-4206-43a8-b9e9-c5737b69e3af
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 736e2ef5490aa9185654a6cdf677579b5f30c1e3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtaskmanagersetlocale-method"></a><span data-ttu-id="4dfdd-102">ICLRTaskManager::SetLocale 方法</span><span class="sxs-lookup"><span data-stu-id="4dfdd-102">ICLRTaskManager::SetLocale Method</span></span>
<span data-ttu-id="4dfdd-103">通知主機已修改的地區設定識別碼 （這會對應至地理文化特性和語言） 目前正在執行的工作上值的 common language runtime (CLR)。</span><span class="sxs-lookup"><span data-stu-id="4dfdd-103">Notifies the common language runtime (CLR) that the host has modified the value of the locale identifier (which maps to the geographical culture and language) on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dfdd-104">語法</span><span class="sxs-lookup"><span data-stu-id="4dfdd-104">Syntax</span></span>  
  
```  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4dfdd-105">參數</span><span class="sxs-lookup"><span data-stu-id="4dfdd-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="4dfdd-106">[in]可對應至新指派的地理文化特性和語言的地區設定識別碼值。</span><span class="sxs-lookup"><span data-stu-id="4dfdd-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4dfdd-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="4dfdd-107">Return Value</span></span>  
  
|<span data-ttu-id="4dfdd-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4dfdd-108">HRESULT</span></span>|<span data-ttu-id="4dfdd-109">描述</span><span class="sxs-lookup"><span data-stu-id="4dfdd-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4dfdd-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4dfdd-110">S_OK</span></span>|<span data-ttu-id="4dfdd-111">方法成功傳回。</span><span class="sxs-lookup"><span data-stu-id="4dfdd-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="4dfdd-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4dfdd-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4dfdd-113">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="4dfdd-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4dfdd-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4dfdd-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4dfdd-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="4dfdd-115">The call timed out.</span></span>|  
|<span data-ttu-id="4dfdd-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4dfdd-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4dfdd-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="4dfdd-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4dfdd-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4dfdd-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4dfdd-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="4dfdd-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4dfdd-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4dfdd-120">E_FAIL</span></span>|<span data-ttu-id="4dfdd-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="4dfdd-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4dfdd-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="4dfdd-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4dfdd-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="4dfdd-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4dfdd-124">備註</span><span class="sxs-lookup"><span data-stu-id="4dfdd-124">Remarks</span></span>  
 <span data-ttu-id="4dfdd-125">`SetLocale`可讓主應用程式執行的地區設定同步處理可能會有任何機制。</span><span class="sxs-lookup"><span data-stu-id="4dfdd-125">`SetLocale` gives the host an opportunity to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4dfdd-126">需求</span><span class="sxs-lookup"><span data-stu-id="4dfdd-126">Requirements</span></span>  
 <span data-ttu-id="4dfdd-127">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4dfdd-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4dfdd-128">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4dfdd-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4dfdd-129">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4dfdd-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4dfdd-130">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4dfdd-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dfdd-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4dfdd-131">See Also</span></span>  
 [<span data-ttu-id="4dfdd-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="4dfdd-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="4dfdd-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="4dfdd-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="4dfdd-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="4dfdd-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="4dfdd-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="4dfdd-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
