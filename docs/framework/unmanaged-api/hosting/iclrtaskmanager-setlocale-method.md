---
title: ICLRTaskManager::SetLocale 方法
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: ed16bb7f-4206-43a8-b9e9-c5737b69e3af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae097320ad7cd6e7c840122bf3f315812e9b2acd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763343"
---
# <a name="iclrtaskmanagersetlocale-method"></a><span data-ttu-id="d9e62-102">ICLRTaskManager::SetLocale 方法</span><span class="sxs-lookup"><span data-stu-id="d9e62-102">ICLRTaskManager::SetLocale Method</span></span>
<span data-ttu-id="d9e62-103">主應用程式已修改地區設定識別碼 （這會對應到地理的文化特性和語言） 上目前執行之工作的值會告知 common language runtime (CLR)。</span><span class="sxs-lookup"><span data-stu-id="d9e62-103">Notifies the common language runtime (CLR) that the host has modified the value of the locale identifier (which maps to the geographical culture and language) on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9e62-104">語法</span><span class="sxs-lookup"><span data-stu-id="d9e62-104">Syntax</span></span>  
  
```  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9e62-105">參數</span><span class="sxs-lookup"><span data-stu-id="d9e62-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="d9e62-106">[in]可對應到新指派的地理文化特性和語言的地區設定識別碼值。</span><span class="sxs-lookup"><span data-stu-id="d9e62-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9e62-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="d9e62-107">Return Value</span></span>  
  
|<span data-ttu-id="d9e62-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d9e62-108">HRESULT</span></span>|<span data-ttu-id="d9e62-109">描述</span><span class="sxs-lookup"><span data-stu-id="d9e62-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d9e62-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d9e62-110">S_OK</span></span>|<span data-ttu-id="d9e62-111">此方法傳回成功。</span><span class="sxs-lookup"><span data-stu-id="d9e62-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="d9e62-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d9e62-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d9e62-113">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="d9e62-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d9e62-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d9e62-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d9e62-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="d9e62-115">The call timed out.</span></span>|  
|<span data-ttu-id="d9e62-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d9e62-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d9e62-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="d9e62-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d9e62-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d9e62-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d9e62-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="d9e62-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d9e62-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d9e62-120">E_FAIL</span></span>|<span data-ttu-id="d9e62-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="d9e62-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d9e62-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="d9e62-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d9e62-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="d9e62-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9e62-124">備註</span><span class="sxs-lookup"><span data-stu-id="d9e62-124">Remarks</span></span>  
 <span data-ttu-id="d9e62-125">`SetLocale` 可讓主應用程式有機會執行它可能會有任何機制，地區設定的同步處理。</span><span class="sxs-lookup"><span data-stu-id="d9e62-125">`SetLocale` gives the host an opportunity to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9e62-126">需求</span><span class="sxs-lookup"><span data-stu-id="d9e62-126">Requirements</span></span>  
 <span data-ttu-id="d9e62-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d9e62-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9e62-128">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d9e62-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d9e62-129">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d9e62-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9e62-130">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9e62-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9e62-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9e62-131">See also</span></span>

- [<span data-ttu-id="d9e62-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="d9e62-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="d9e62-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="d9e62-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="d9e62-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="d9e62-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="d9e62-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="d9e62-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
