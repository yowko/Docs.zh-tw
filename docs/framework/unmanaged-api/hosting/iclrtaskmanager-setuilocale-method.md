---
title: ICLRTaskManager::SetUILocale 方法
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.SetUILocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::SetUILocale
helpviewer_keywords:
- ICLRTaskManager::SetUILocale method [.NET Framework hosting]
- SetUILocale method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 03adaa9a-2beb-49b3-b2c4-6b4fc3f10715
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03c5c9d04567832951062fe1512a292f9b32a94b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59155671"
---
# <a name="iclrtaskmanagersetuilocale-method"></a><span data-ttu-id="0221a-102">ICLRTaskManager::SetUILocale 方法</span><span class="sxs-lookup"><span data-stu-id="0221a-102">ICLRTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="0221a-103">目前正在執行的工作上會告知 common language runtime (CLR) 主機已修改的使用者介面 (UI) 的地區設定或文化特性。</span><span class="sxs-lookup"><span data-stu-id="0221a-103">Notifies the common language runtime (CLR) that the host has modified the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0221a-104">語法</span><span class="sxs-lookup"><span data-stu-id="0221a-104">Syntax</span></span>  
  
```  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0221a-105">參數</span><span class="sxs-lookup"><span data-stu-id="0221a-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="0221a-106">[in]對應到新指派的地理文化特性和使用者介面的語言地區設定識別碼值。</span><span class="sxs-lookup"><span data-stu-id="0221a-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language for the user interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0221a-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="0221a-107">Return Value</span></span>  
  
|<span data-ttu-id="0221a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0221a-108">HRESULT</span></span>|<span data-ttu-id="0221a-109">描述</span><span class="sxs-lookup"><span data-stu-id="0221a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0221a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0221a-110">S_OK</span></span>|<span data-ttu-id="0221a-111">`SetUILocale` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="0221a-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="0221a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0221a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0221a-113">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="0221a-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0221a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0221a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0221a-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="0221a-115">The call timed out.</span></span>|  
|<span data-ttu-id="0221a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0221a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0221a-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="0221a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0221a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0221a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0221a-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="0221a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0221a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0221a-120">E_FAIL</span></span>|<span data-ttu-id="0221a-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="0221a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0221a-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="0221a-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0221a-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="0221a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0221a-124">備註</span><span class="sxs-lookup"><span data-stu-id="0221a-124">Remarks</span></span>  
 <span data-ttu-id="0221a-125">`SetUILocale` 提供的主應用程式執行任何機制，它可能會有的地區設定的同步處理的機會。</span><span class="sxs-lookup"><span data-stu-id="0221a-125">`SetUILocale` provides an opportunity for the host to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0221a-126">需求</span><span class="sxs-lookup"><span data-stu-id="0221a-126">Requirements</span></span>  
 <span data-ttu-id="0221a-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0221a-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0221a-128">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0221a-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0221a-129">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0221a-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0221a-130">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0221a-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0221a-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0221a-131">See also</span></span>

- [<span data-ttu-id="0221a-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="0221a-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="0221a-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="0221a-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="0221a-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="0221a-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="0221a-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="0221a-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
