---
title: "ICLROnEventManager::UnregisterActionOnEvent 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLROnEventManager.UnregisterActionOnEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLROnEventManager::UnregisterActionOnEvent
helpviewer_keywords:
- UnRegisterActionOnEvent method [.NET Framework hosting]
- ICLROnEventManager::UnRegisterActionOnEvent method [.NET Framework hosting]
ms.assetid: 4c02ec37-cdf0-46b2-890e-235092741236
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5e8f922207ff347bb6570ede417fdeda71f92d0f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclroneventmanagerunregisteractiononevent-method"></a><span data-ttu-id="b7475-102">ICLROnEventManager::UnregisterActionOnEvent 方法</span><span class="sxs-lookup"><span data-stu-id="b7475-102">ICLROnEventManager::UnregisterActionOnEvent Method</span></span>
<span data-ttu-id="b7475-103">取消註冊先前註冊的回呼指標為指定的事件。</span><span class="sxs-lookup"><span data-stu-id="b7475-103">Unregisters a previously registered callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7475-104">語法</span><span class="sxs-lookup"><span data-stu-id="b7475-104">Syntax</span></span>  
  
```  
HRESULT UnregisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b7475-105">參數</span><span class="sxs-lookup"><span data-stu-id="b7475-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="b7475-106">[in]其中一個[EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)值，表示要取消註冊回呼指標所描述的事件`pAction`。</span><span class="sxs-lookup"><span data-stu-id="b7475-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, indicating the event for which to unregister the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="b7475-107">[in]指標[IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)物件當做參數傳遞[RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="b7475-107">[in] A pointer to an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) object that was passed as a parameter to the [RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b7475-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="b7475-108">Return Value</span></span>  
  
|<span data-ttu-id="b7475-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b7475-109">HRESULT</span></span>|<span data-ttu-id="b7475-110">描述</span><span class="sxs-lookup"><span data-stu-id="b7475-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b7475-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b7475-111">S_OK</span></span>|<span data-ttu-id="b7475-112">`UnregisterActionOnEvent`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="b7475-112">`UnregisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="b7475-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b7475-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b7475-114">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="b7475-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b7475-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b7475-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b7475-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="b7475-116">The call timed out.</span></span>|  
|<span data-ttu-id="b7475-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b7475-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b7475-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="b7475-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b7475-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b7475-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b7475-120">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="b7475-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b7475-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b7475-121">E_FAIL</span></span>|<span data-ttu-id="b7475-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="b7475-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b7475-123">方法會傳回 E_FAIL 之後，CLR 就不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="b7475-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b7475-124">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="b7475-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b7475-125">需求</span><span class="sxs-lookup"><span data-stu-id="b7475-125">Requirements</span></span>  
 <span data-ttu-id="b7475-126">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b7475-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7475-127">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b7475-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b7475-128">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b7475-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b7475-129">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7475-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7475-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7475-130">See Also</span></span>  
 [<span data-ttu-id="b7475-131">EClrEvent 列舉</span><span class="sxs-lookup"><span data-stu-id="b7475-131">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [<span data-ttu-id="b7475-132">IActionOnCLREvent 介面</span><span class="sxs-lookup"><span data-stu-id="b7475-132">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [<span data-ttu-id="b7475-133">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="b7475-133">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="b7475-134">ICLROnEventManager 介面</span><span class="sxs-lookup"><span data-stu-id="b7475-134">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
