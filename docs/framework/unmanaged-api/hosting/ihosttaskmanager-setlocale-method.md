---
title: IHostTaskManager::SetLocale 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: 747ee407-ee8c-484d-9583-25089236d2d1
topic_type:
- apiref
ms.openlocfilehash: 7730c2dddaca98e4cb06cdb381e8a46ff23c97f9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699192"
---
# <a name="ihosttaskmanagersetlocale-method"></a><span data-ttu-id="b21cb-102">IHostTaskManager::SetLocale 方法</span><span class="sxs-lookup"><span data-stu-id="b21cb-102">IHostTaskManager::SetLocale Method</span></span>

<span data-ttu-id="b21cb-103">通知主機 common language runtime (CLR) 已變更目前正在執行之工作的地區設定或文化特性。</span><span class="sxs-lookup"><span data-stu-id="b21cb-103">Notifies the host that the common language runtime (CLR) has changed the locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b21cb-104">語法</span><span class="sxs-lookup"><span data-stu-id="b21cb-104">Syntax</span></span>  
  
```cpp  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b21cb-105">參數</span><span class="sxs-lookup"><span data-stu-id="b21cb-105">Parameters</span></span>  

 `lcid`  
 <span data-ttu-id="b21cb-106">在對應到新指派之地理文化特性和語言的地區設定識別碼值。</span><span class="sxs-lookup"><span data-stu-id="b21cb-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b21cb-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="b21cb-107">Return Value</span></span>  
  
|<span data-ttu-id="b21cb-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b21cb-108">HRESULT</span></span>|<span data-ttu-id="b21cb-109">描述</span><span class="sxs-lookup"><span data-stu-id="b21cb-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b21cb-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b21cb-110">S_OK</span></span>|<span data-ttu-id="b21cb-111">`SetLocale` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="b21cb-111">`SetLocale` returned successfully.</span></span>|  
|<span data-ttu-id="b21cb-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b21cb-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b21cb-113">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="b21cb-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b21cb-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b21cb-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b21cb-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="b21cb-115">The call timed out.</span></span>|  
|<span data-ttu-id="b21cb-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b21cb-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b21cb-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="b21cb-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b21cb-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b21cb-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b21cb-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="b21cb-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b21cb-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b21cb-120">E_FAIL</span></span>|<span data-ttu-id="b21cb-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="b21cb-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b21cb-122">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="b21cb-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b21cb-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="b21cb-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b21cb-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="b21cb-124">E_NOTIMPL</span></span>|<span data-ttu-id="b21cb-125">主機不允許受管理的使用者程式碼修改地區設定。</span><span class="sxs-lookup"><span data-stu-id="b21cb-125">The host does not allow managed user code to modify the locale.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b21cb-126">備註</span><span class="sxs-lookup"><span data-stu-id="b21cb-126">Remarks</span></span>  

 <span data-ttu-id="b21cb-127">`SetLocale`當 <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> managed 程式碼變更屬性的值時，執行時間會呼叫。</span><span class="sxs-lookup"><span data-stu-id="b21cb-127">The runtime calls `SetLocale` when the value of the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="b21cb-128">此方法可讓主機執行任何可能對地區設定進行同步處理的機制。</span><span class="sxs-lookup"><span data-stu-id="b21cb-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="b21cb-129">如果主機不允許從 managed 程式碼變更地區設定，或未執行同步處理地區設定的機制，則應該從此方法傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="b21cb-129">If a host does not allow the locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b21cb-130">需求</span><span class="sxs-lookup"><span data-stu-id="b21cb-130">Requirements</span></span>  

 <span data-ttu-id="b21cb-131">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b21cb-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b21cb-132">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="b21cb-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b21cb-133">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="b21cb-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b21cb-134">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b21cb-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b21cb-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b21cb-135">See also</span></span>

- [<span data-ttu-id="b21cb-136">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="b21cb-136">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="b21cb-137">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="b21cb-137">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="b21cb-138">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="b21cb-138">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="b21cb-139">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="b21cb-139">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="b21cb-140">SetUILocale 方法</span><span class="sxs-lookup"><span data-stu-id="b21cb-140">SetUILocale Method</span></span>](ihosttaskmanager-setuilocale-method.md)
