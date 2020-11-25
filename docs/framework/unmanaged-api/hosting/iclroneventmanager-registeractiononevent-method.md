---
title: ICLROnEventManager::RegisterActionOnEvent 方法
ms.date: 03/30/2017
api_name:
- ICLROnEventManager.RegisterActionOnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager::RegisterActionOnEvent
helpviewer_keywords:
- ICLROnEventManager::RegisterActionOnEvent method [.NET Framework hosting]
- RegisterActionOnEvent method [.NET Framework hosting]
ms.assetid: b944cf49-918d-4c4e-993b-77d097a52550
topic_type:
- apiref
ms.openlocfilehash: 7f0770585e977f5299a40517c28dfb776b2ab898
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725608"
---
# <a name="iclroneventmanagerregisteractiononevent-method"></a><span data-ttu-id="05beb-102">ICLROnEventManager::RegisterActionOnEvent 方法</span><span class="sxs-lookup"><span data-stu-id="05beb-102">ICLROnEventManager::RegisterActionOnEvent Method</span></span>

<span data-ttu-id="05beb-103">註冊指定事件的回呼指標。</span><span class="sxs-lookup"><span data-stu-id="05beb-103">Registers a callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05beb-104">語法</span><span class="sxs-lookup"><span data-stu-id="05beb-104">Syntax</span></span>  
  
```cpp  
HRESULT RegisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05beb-105">參數</span><span class="sxs-lookup"><span data-stu-id="05beb-105">Parameters</span></span>  

 `event`  
 <span data-ttu-id="05beb-106">在其中一個 [EClrEvent](eclrevent-enumeration.md) 值，表示要註冊其所描述之回呼指標的事件 `pAction` 。</span><span class="sxs-lookup"><span data-stu-id="05beb-106">[in] One of the [EClrEvent](eclrevent-enumeration.md) values, indicating the event for which to register the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="05beb-107">在 [IActionOnCLREvent](iactiononclrevent-interface.md) 物件的指標，該物件會在已註冊的事件引發時呼叫。</span><span class="sxs-lookup"><span data-stu-id="05beb-107">[in] A pointer to an [IActionOnCLREvent](iactiononclrevent-interface.md) object that is called when the registered event fires.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="05beb-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="05beb-108">Return Value</span></span>  
  
|<span data-ttu-id="05beb-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="05beb-109">HRESULT</span></span>|<span data-ttu-id="05beb-110">描述</span><span class="sxs-lookup"><span data-stu-id="05beb-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="05beb-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="05beb-111">S_OK</span></span>|<span data-ttu-id="05beb-112">`RegisterActionOnEvent` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="05beb-112">`RegisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="05beb-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="05beb-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="05beb-114">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="05beb-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="05beb-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="05beb-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="05beb-116">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="05beb-116">The call timed out.</span></span>|  
|<span data-ttu-id="05beb-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="05beb-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="05beb-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="05beb-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="05beb-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="05beb-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="05beb-120">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="05beb-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="05beb-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="05beb-121">E_FAIL</span></span>|<span data-ttu-id="05beb-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="05beb-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="05beb-123">在方法傳回 E_FAIL 之後，就無法在進程中使用 CLR。</span><span class="sxs-lookup"><span data-stu-id="05beb-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="05beb-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="05beb-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05beb-125">備註</span><span class="sxs-lookup"><span data-stu-id="05beb-125">Remarks</span></span>  

 <span data-ttu-id="05beb-126">主機可以為所描述的兩個事件種類的任一個或兩個註冊回呼 `EClrEvent` 。</span><span class="sxs-lookup"><span data-stu-id="05beb-126">The host can register callbacks for either or both of the two event types described by `EClrEvent`.</span></span> <span data-ttu-id="05beb-127">主機會藉 `ICLROnEventManager` 由呼叫 [ICLRControl：： GetCLRManager](iclrcontrol-getclrmanager-method.md) 方法來取得介面。</span><span class="sxs-lookup"><span data-stu-id="05beb-127">The host gets the `ICLROnEventManager` interface by calling the [ICLRControl::GetCLRManager](iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="05beb-128">註冊的事件 `RegisterActionOnEvent` 可以從不同的執行緒中引發一次以上，以表示卸載或停用 CLR。</span><span class="sxs-lookup"><span data-stu-id="05beb-128">The events that `RegisterActionOnEvent` registers can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05beb-129">需求</span><span class="sxs-lookup"><span data-stu-id="05beb-129">Requirements</span></span>  

 <span data-ttu-id="05beb-130">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="05beb-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05beb-131">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="05beb-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="05beb-132">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="05beb-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="05beb-133">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05beb-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05beb-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05beb-134">See also</span></span>

- [<span data-ttu-id="05beb-135">EClrEvent 列舉</span><span class="sxs-lookup"><span data-stu-id="05beb-135">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="05beb-136">IActionOnCLREvent 介面</span><span class="sxs-lookup"><span data-stu-id="05beb-136">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="05beb-137">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="05beb-137">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="05beb-138">ICLROnEventManager 介面</span><span class="sxs-lookup"><span data-stu-id="05beb-138">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
