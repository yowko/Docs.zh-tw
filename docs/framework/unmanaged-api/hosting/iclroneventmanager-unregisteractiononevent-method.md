---
title: ICLROnEventManager::UnregisterActionOnEvent 方法
ms.date: 03/30/2017
api_name:
- ICLROnEventManager.UnregisterActionOnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager::UnregisterActionOnEvent
helpviewer_keywords:
- UnRegisterActionOnEvent method [.NET Framework hosting]
- ICLROnEventManager::UnRegisterActionOnEvent method [.NET Framework hosting]
ms.assetid: 4c02ec37-cdf0-46b2-890e-235092741236
topic_type:
- apiref
ms.openlocfilehash: ca3c7fe813f22d3beab3087414100b3d8e5814ac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725595"
---
# <a name="iclroneventmanagerunregisteractiononevent-method"></a><span data-ttu-id="8cc98-102">ICLROnEventManager::UnregisterActionOnEvent 方法</span><span class="sxs-lookup"><span data-stu-id="8cc98-102">ICLROnEventManager::UnregisterActionOnEvent Method</span></span>

<span data-ttu-id="8cc98-103">針對指定的事件，取消註冊先前註冊的回呼指標。</span><span class="sxs-lookup"><span data-stu-id="8cc98-103">Unregisters a previously registered callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cc98-104">語法</span><span class="sxs-lookup"><span data-stu-id="8cc98-104">Syntax</span></span>  
  
```cpp  
HRESULT UnregisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8cc98-105">參數</span><span class="sxs-lookup"><span data-stu-id="8cc98-105">Parameters</span></span>  

 `event`  
 <span data-ttu-id="8cc98-106">在其中一個 [EClrEvent](eclrevent-enumeration.md) 值，表示要取消註冊所描述之回呼指標的事件 `pAction` 。</span><span class="sxs-lookup"><span data-stu-id="8cc98-106">[in] One of the [EClrEvent](eclrevent-enumeration.md) values, indicating the event for which to unregister the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="8cc98-107">在 [IActionOnCLREvent](iactiononclrevent-interface.md) 物件的指標，該物件會以參數形式傳遞給 [RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="8cc98-107">[in] A pointer to an [IActionOnCLREvent](iactiononclrevent-interface.md) object that was passed as a parameter to the [RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8cc98-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="8cc98-108">Return Value</span></span>  
  
|<span data-ttu-id="8cc98-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8cc98-109">HRESULT</span></span>|<span data-ttu-id="8cc98-110">描述</span><span class="sxs-lookup"><span data-stu-id="8cc98-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8cc98-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8cc98-111">S_OK</span></span>|<span data-ttu-id="8cc98-112">`UnregisterActionOnEvent` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="8cc98-112">`UnregisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="8cc98-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8cc98-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8cc98-114">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="8cc98-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8cc98-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8cc98-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8cc98-116">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="8cc98-116">The call timed out.</span></span>|  
|<span data-ttu-id="8cc98-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8cc98-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8cc98-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="8cc98-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8cc98-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8cc98-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8cc98-120">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="8cc98-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8cc98-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8cc98-121">E_FAIL</span></span>|<span data-ttu-id="8cc98-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="8cc98-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8cc98-123">在方法傳回 E_FAIL 之後，就無法在進程中使用 CLR。</span><span class="sxs-lookup"><span data-stu-id="8cc98-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8cc98-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="8cc98-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8cc98-125">需求</span><span class="sxs-lookup"><span data-stu-id="8cc98-125">Requirements</span></span>  

 <span data-ttu-id="8cc98-126">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8cc98-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cc98-127">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="8cc98-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8cc98-128">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="8cc98-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8cc98-129">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cc98-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cc98-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8cc98-130">See also</span></span>

- [<span data-ttu-id="8cc98-131">EClrEvent 列舉</span><span class="sxs-lookup"><span data-stu-id="8cc98-131">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="8cc98-132">IActionOnCLREvent 介面</span><span class="sxs-lookup"><span data-stu-id="8cc98-132">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="8cc98-133">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="8cc98-133">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="8cc98-134">ICLROnEventManager 介面</span><span class="sxs-lookup"><span data-stu-id="8cc98-134">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
