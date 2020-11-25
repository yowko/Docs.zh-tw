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
ms.openlocfilehash: 5f799c140705a5279c996b6bec90ab1f29bd42ef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732429"
---
# <a name="iclrtaskmanagersetlocale-method"></a><span data-ttu-id="76289-102">ICLRTaskManager::SetLocale 方法</span><span class="sxs-lookup"><span data-stu-id="76289-102">ICLRTaskManager::SetLocale Method</span></span>

<span data-ttu-id="76289-103">通知 common language runtime (CLR) 主控制項已修改地區設定識別碼的值， (對應到目前執行中工作的地理文化特性和語言) 。</span><span class="sxs-lookup"><span data-stu-id="76289-103">Notifies the common language runtime (CLR) that the host has modified the value of the locale identifier (which maps to the geographical culture and language) on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76289-104">語法</span><span class="sxs-lookup"><span data-stu-id="76289-104">Syntax</span></span>  
  
```cpp  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76289-105">參數</span><span class="sxs-lookup"><span data-stu-id="76289-105">Parameters</span></span>  

 `lcid`  
 <span data-ttu-id="76289-106">在對應到新指派之地理文化特性和語言的地區設定識別碼值。</span><span class="sxs-lookup"><span data-stu-id="76289-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="76289-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="76289-107">Return Value</span></span>  
  
|<span data-ttu-id="76289-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="76289-108">HRESULT</span></span>|<span data-ttu-id="76289-109">描述</span><span class="sxs-lookup"><span data-stu-id="76289-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="76289-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="76289-110">S_OK</span></span>|<span data-ttu-id="76289-111">此方法已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="76289-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="76289-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="76289-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="76289-113">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="76289-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="76289-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="76289-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="76289-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="76289-115">The call timed out.</span></span>|  
|<span data-ttu-id="76289-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="76289-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="76289-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="76289-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="76289-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="76289-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="76289-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="76289-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="76289-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="76289-120">E_FAIL</span></span>|<span data-ttu-id="76289-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="76289-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="76289-122">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="76289-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="76289-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="76289-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76289-124">備註</span><span class="sxs-lookup"><span data-stu-id="76289-124">Remarks</span></span>  

 <span data-ttu-id="76289-125">`SetLocale` 讓主機有機會執行任何可能對地區設定進行同步處理的機制。</span><span class="sxs-lookup"><span data-stu-id="76289-125">`SetLocale` gives the host an opportunity to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76289-126">需求</span><span class="sxs-lookup"><span data-stu-id="76289-126">Requirements</span></span>  

 <span data-ttu-id="76289-127">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="76289-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76289-128">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="76289-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="76289-129">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="76289-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="76289-130">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76289-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76289-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76289-131">See also</span></span>

- [<span data-ttu-id="76289-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="76289-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="76289-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="76289-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="76289-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="76289-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="76289-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="76289-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
