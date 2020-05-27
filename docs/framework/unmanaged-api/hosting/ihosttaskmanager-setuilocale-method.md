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
ms.openlocfilehash: e7e65c3b9bcafdf4c8b1185fcff1fc0740b2ef7c
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841424"
---
# <a name="ihosttaskmanagersetuilocale-method"></a><span data-ttu-id="1ea44-102">IHostTaskManager::SetUILocale 方法</span><span class="sxs-lookup"><span data-stu-id="1ea44-102">IHostTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="1ea44-103">通知主機 common language runtime （CLR）已變更目前正在執行之工作的使用者介面（UI）地區設定或文化特性。</span><span class="sxs-lookup"><span data-stu-id="1ea44-103">Notifies the host that the common language runtime (CLR) has changed the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ea44-104">語法</span><span class="sxs-lookup"><span data-stu-id="1ea44-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ea44-105">參數</span><span class="sxs-lookup"><span data-stu-id="1ea44-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="1ea44-106">在地區設定識別碼值，對應至新指派的地理文化特性和語言。</span><span class="sxs-lookup"><span data-stu-id="1ea44-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ea44-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="1ea44-107">Return Value</span></span>  
  
|<span data-ttu-id="1ea44-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1ea44-108">HRESULT</span></span>|<span data-ttu-id="1ea44-109">描述</span><span class="sxs-lookup"><span data-stu-id="1ea44-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1ea44-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1ea44-110">S_OK</span></span>|<span data-ttu-id="1ea44-111">`SetUILocale`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="1ea44-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="1ea44-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1ea44-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1ea44-113">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="1ea44-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1ea44-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1ea44-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1ea44-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="1ea44-115">The call timed out.</span></span>|  
|<span data-ttu-id="1ea44-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1ea44-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1ea44-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="1ea44-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1ea44-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1ea44-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1ea44-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="1ea44-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1ea44-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1ea44-120">E_FAIL</span></span>|<span data-ttu-id="1ea44-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="1ea44-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1ea44-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="1ea44-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1ea44-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="1ea44-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1ea44-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="1ea44-124">E_NOTIMPL</span></span>|<span data-ttu-id="1ea44-125">主機不允許受管理的使用者程式碼變更 UI 文化特性。</span><span class="sxs-lookup"><span data-stu-id="1ea44-125">The host does not allow managed user code to change the UI culture.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ea44-126">備註</span><span class="sxs-lookup"><span data-stu-id="1ea44-126">Remarks</span></span>  
 <span data-ttu-id="1ea44-127">`SetUILocale`當 managed 程式碼變更屬性的值時，執行時間 <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> 會呼叫。</span><span class="sxs-lookup"><span data-stu-id="1ea44-127">The runtime calls `SetUILocale` when the value of the <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="1ea44-128">這個方法可讓主機執行任何可能對地區設定同步處理的機制。</span><span class="sxs-lookup"><span data-stu-id="1ea44-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="1ea44-129">如果主機不允許從 managed 程式碼變更 UI 地區設定，或未執行同步處理地區設定的機制，則應該從這個方法傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="1ea44-129">If a host does not allow the UI locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ea44-130">規格需求</span><span class="sxs-lookup"><span data-stu-id="1ea44-130">Requirements</span></span>  
 <span data-ttu-id="1ea44-131">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1ea44-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ea44-132">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="1ea44-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1ea44-133">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1ea44-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1ea44-134">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ea44-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ea44-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ea44-135">See also</span></span>

- [<span data-ttu-id="1ea44-136">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="1ea44-136">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="1ea44-137">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="1ea44-137">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="1ea44-138">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="1ea44-138">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="1ea44-139">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="1ea44-139">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="1ea44-140">SetLocale 方法</span><span class="sxs-lookup"><span data-stu-id="1ea44-140">SetLocale Method</span></span>](ihosttaskmanager-setlocale-method.md)
