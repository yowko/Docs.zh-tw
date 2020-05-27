---
title: IHostAutoEvent::Wait 方法
ms.date: 03/30/2017
api_name:
- IHostAutoEvent.Wait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent::Wait
helpviewer_keywords:
- Wait method, IHostAutoEvent interface [.NET Framework hosting]
- IHostAutoEvent::Wait method [.NET Framework hosting]
ms.assetid: 535d51c5-9112-401b-8c36-85f35d7ee609
topic_type:
- apiref
ms.openlocfilehash: 7baabafc61e14d127ff3f0cdb7453be6f1a2abeb
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804964"
---
# <a name="ihostautoeventwait-method"></a><span data-ttu-id="510ff-102">IHostAutoEvent::Wait 方法</span><span class="sxs-lookup"><span data-stu-id="510ff-102">IHostAutoEvent::Wait Method</span></span>
<span data-ttu-id="510ff-103">導致目前的[IHostAutoEvent](ihostautoevent-interface.md)實例等到其擁有或指定的時間量經過之後，才會等候。</span><span class="sxs-lookup"><span data-stu-id="510ff-103">Causes the current [IHostAutoEvent](ihostautoevent-interface.md) instance to wait until it is owned or a specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="510ff-104">語法</span><span class="sxs-lookup"><span data-stu-id="510ff-104">Syntax</span></span>  
  
```cpp  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="510ff-105">參數</span><span class="sxs-lookup"><span data-stu-id="510ff-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="510ff-106">在目前實例在傳回 `IHostAutoEvent` 之前應等候的毫秒數（如果沒有任何執行緒或光纖取得擁有權）。</span><span class="sxs-lookup"><span data-stu-id="510ff-106">[in] The number of milliseconds the current `IHostAutoEvent` instance should wait before returning, if no thread or fiber takes ownership.</span></span>  
  
 `option`  
 <span data-ttu-id="510ff-107">在其中一個[WAIT_OPTION](wait-option-enumeration.md)值，指定當此作業封鎖時，主機應採取的動作。</span><span class="sxs-lookup"><span data-stu-id="510ff-107">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, specifying the action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="510ff-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="510ff-108">Return Value</span></span>  
  
|<span data-ttu-id="510ff-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="510ff-109">HRESULT</span></span>|<span data-ttu-id="510ff-110">描述</span><span class="sxs-lookup"><span data-stu-id="510ff-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="510ff-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="510ff-111">S_OK</span></span>|<span data-ttu-id="510ff-112">`Wait`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="510ff-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="510ff-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="510ff-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="510ff-114">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="510ff-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="510ff-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="510ff-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="510ff-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="510ff-116">The call timed out.</span></span>|  
|<span data-ttu-id="510ff-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="510ff-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="510ff-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="510ff-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="510ff-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="510ff-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="510ff-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="510ff-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="510ff-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="510ff-121">E_FAIL</span></span>|<span data-ttu-id="510ff-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="510ff-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="510ff-123">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="510ff-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="510ff-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="510ff-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="510ff-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="510ff-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="510ff-126">主機在等候間隔期間偵測到鎖死，並選擇目前實例所代表的事件 `IHostAutoEvent` 做為鎖死犧牲者。</span><span class="sxs-lookup"><span data-stu-id="510ff-126">The host detected a deadlock during the wait interval, and chose the event represented by the current `IHostAutoEvent` instance as the deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="510ff-127">規格需求</span><span class="sxs-lookup"><span data-stu-id="510ff-127">Requirements</span></span>  
 <span data-ttu-id="510ff-128">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="510ff-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="510ff-129">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="510ff-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="510ff-130">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="510ff-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="510ff-131">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="510ff-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="510ff-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="510ff-132">See also</span></span>

- [<span data-ttu-id="510ff-133">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="510ff-133">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="510ff-134">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="510ff-134">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="510ff-135">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="510ff-135">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="510ff-136">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="510ff-136">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
