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
ms.openlocfilehash: 051bd5cb846eb4e6e3390e17b3011a1c5b50bc45
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127868"
---
# <a name="iclrtaskmanagersetuilocale-method"></a><span data-ttu-id="31859-102">ICLRTaskManager::SetUILocale 方法</span><span class="sxs-lookup"><span data-stu-id="31859-102">ICLRTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="31859-103">通知 common language runtime （CLR），主控制項已修改目前正在執行之工作的使用者介面（UI）地區設定或文化特性。</span><span class="sxs-lookup"><span data-stu-id="31859-103">Notifies the common language runtime (CLR) that the host has modified the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31859-104">語法</span><span class="sxs-lookup"><span data-stu-id="31859-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31859-105">參數</span><span class="sxs-lookup"><span data-stu-id="31859-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="31859-106">在地區設定識別碼值，對應至新指派的地理文化特性和使用者介面的語言。</span><span class="sxs-lookup"><span data-stu-id="31859-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language for the user interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="31859-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="31859-107">Return Value</span></span>  
  
|<span data-ttu-id="31859-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="31859-108">HRESULT</span></span>|<span data-ttu-id="31859-109">描述</span><span class="sxs-lookup"><span data-stu-id="31859-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="31859-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="31859-110">S_OK</span></span>|<span data-ttu-id="31859-111">已成功傳回 `SetUILocale`。</span><span class="sxs-lookup"><span data-stu-id="31859-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="31859-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="31859-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="31859-113">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="31859-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="31859-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="31859-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="31859-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="31859-115">The call timed out.</span></span>|  
|<span data-ttu-id="31859-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="31859-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="31859-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="31859-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="31859-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="31859-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="31859-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="31859-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="31859-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="31859-120">E_FAIL</span></span>|<span data-ttu-id="31859-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="31859-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="31859-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="31859-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="31859-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="31859-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31859-124">備註</span><span class="sxs-lookup"><span data-stu-id="31859-124">Remarks</span></span>  
 <span data-ttu-id="31859-125">`SetUILocale` 提供機會讓主機針對地區設定的同步處理執行任何可能的機制。</span><span class="sxs-lookup"><span data-stu-id="31859-125">`SetUILocale` provides an opportunity for the host to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31859-126">需求</span><span class="sxs-lookup"><span data-stu-id="31859-126">Requirements</span></span>  
 <span data-ttu-id="31859-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="31859-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31859-128">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="31859-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="31859-129">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="31859-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="31859-130">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31859-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31859-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="31859-131">See also</span></span>

- [<span data-ttu-id="31859-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="31859-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="31859-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="31859-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="31859-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="31859-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="31859-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="31859-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
