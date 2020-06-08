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
ms.openlocfilehash: a3018d8477d5abd7d03ad8675503624d2e44e8f4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504130"
---
# <a name="iclroneventmanagerunregisteractiononevent-method"></a><span data-ttu-id="2ca70-102">ICLROnEventManager::UnregisterActionOnEvent 方法</span><span class="sxs-lookup"><span data-stu-id="2ca70-102">ICLROnEventManager::UnregisterActionOnEvent Method</span></span>
<span data-ttu-id="2ca70-103">將先前註冊的回呼指標取消註冊到指定的事件。</span><span class="sxs-lookup"><span data-stu-id="2ca70-103">Unregisters a previously registered callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ca70-104">語法</span><span class="sxs-lookup"><span data-stu-id="2ca70-104">Syntax</span></span>  
  
```cpp  
HRESULT UnregisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ca70-105">參數</span><span class="sxs-lookup"><span data-stu-id="2ca70-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="2ca70-106">在其中一個[EClrEvent](eclrevent-enumeration.md)值，表示要取消註冊所描述之回呼指標的事件 `pAction` 。</span><span class="sxs-lookup"><span data-stu-id="2ca70-106">[in] One of the [EClrEvent](eclrevent-enumeration.md) values, indicating the event for which to unregister the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="2ca70-107">在當做參數傳遞至[RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md)方法的[IActionOnCLREvent](iactiononclrevent-interface.md)物件指標。</span><span class="sxs-lookup"><span data-stu-id="2ca70-107">[in] A pointer to an [IActionOnCLREvent](iactiononclrevent-interface.md) object that was passed as a parameter to the [RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2ca70-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="2ca70-108">Return Value</span></span>  
  
|<span data-ttu-id="2ca70-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2ca70-109">HRESULT</span></span>|<span data-ttu-id="2ca70-110">說明</span><span class="sxs-lookup"><span data-stu-id="2ca70-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2ca70-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2ca70-111">S_OK</span></span>|<span data-ttu-id="2ca70-112">`UnregisterActionOnEvent`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="2ca70-112">`UnregisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="2ca70-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2ca70-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2ca70-114">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="2ca70-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2ca70-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2ca70-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2ca70-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="2ca70-116">The call timed out.</span></span>|  
|<span data-ttu-id="2ca70-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2ca70-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2ca70-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="2ca70-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2ca70-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2ca70-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2ca70-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="2ca70-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2ca70-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2ca70-121">E_FAIL</span></span>|<span data-ttu-id="2ca70-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="2ca70-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2ca70-123">在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="2ca70-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2ca70-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="2ca70-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2ca70-125">規格需求</span><span class="sxs-lookup"><span data-stu-id="2ca70-125">Requirements</span></span>  
 <span data-ttu-id="2ca70-126">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2ca70-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ca70-127">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="2ca70-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2ca70-128">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2ca70-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2ca70-129">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ca70-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ca70-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ca70-130">See also</span></span>

- [<span data-ttu-id="2ca70-131">EClrEvent 列舉</span><span class="sxs-lookup"><span data-stu-id="2ca70-131">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="2ca70-132">IActionOnCLREvent 介面</span><span class="sxs-lookup"><span data-stu-id="2ca70-132">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="2ca70-133">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="2ca70-133">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="2ca70-134">ICLROnEventManager 介面</span><span class="sxs-lookup"><span data-stu-id="2ca70-134">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
