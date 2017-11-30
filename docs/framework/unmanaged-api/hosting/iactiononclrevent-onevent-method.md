---
title: "IActionOnCLREvent::OnEvent 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IActionOnCLREvent.OnEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IActionOnCLREvent::OnEvent
helpviewer_keywords:
- OnEvent method [.NET Framework hosting]
- IActionOnCLREvent::OnEvent method [.NET Framework hosting]
ms.assetid: 0970f10c-4304-4c12-91c0-83e51455afb4
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b2f609969ccf67f07701d20578225f1618293968
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iactiononclreventonevent-method"></a><span data-ttu-id="2633e-102">IActionOnCLREvent::OnEvent 方法</span><span class="sxs-lookup"><span data-stu-id="2633e-102">IActionOnCLREvent::OnEvent Method</span></span>
<span data-ttu-id="2633e-103">執行所使用的呼叫已註冊的事件回呼[iclroneventmanager:: Registeractiononevent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="2633e-103">Performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2633e-104">語法</span><span class="sxs-lookup"><span data-stu-id="2633e-104">Syntax</span></span>  
  
```  
HRESULT OnEvent (  
    [in] EClrEvent event,  
    [in] PVOID     data  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2633e-105">參數</span><span class="sxs-lookup"><span data-stu-id="2633e-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="2633e-106">[in]其中一個[EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)值，指出事件類型。</span><span class="sxs-lookup"><span data-stu-id="2633e-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, which indicates the type of event.</span></span>  
  
 `data`  
 <span data-ttu-id="2633e-107">[in]包含有關的詳細資料物件的指標`event`。</span><span class="sxs-lookup"><span data-stu-id="2633e-107">[in] A pointer to an object that contains details about `event`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2633e-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="2633e-108">Return Value</span></span>  
  
|<span data-ttu-id="2633e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2633e-109">HRESULT</span></span>|<span data-ttu-id="2633e-110">描述</span><span class="sxs-lookup"><span data-stu-id="2633e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2633e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2633e-111">S_OK</span></span>|<span data-ttu-id="2633e-112">`OnEvent`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="2633e-112">`OnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="2633e-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2633e-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2633e-114">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="2633e-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2633e-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2633e-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2633e-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="2633e-116">The call timed out.</span></span>|  
|<span data-ttu-id="2633e-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2633e-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2633e-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="2633e-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2633e-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2633e-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2633e-120">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="2633e-120">An event was cancelled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2633e-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2633e-121">E_FAIL</span></span>|<span data-ttu-id="2633e-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="2633e-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2633e-123">若方法會傳回 E_FAIL，CLR 就不會再處理序內。</span><span class="sxs-lookup"><span data-stu-id="2633e-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2633e-124">任何裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="2633e-124">Subsequent calls to any hosting method return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2633e-125">備註</span><span class="sxs-lookup"><span data-stu-id="2633e-125">Remarks</span></span>  
 <span data-ttu-id="2633e-126">`data`參數是未指定類型的物件的指標。</span><span class="sxs-lookup"><span data-stu-id="2633e-126">The `data` parameter is a pointer to an object of unspecified type.</span></span> <span data-ttu-id="2633e-127">如果`event`參數是`Event_DomainUnload`，`data`的數值識別碼<xref:System.AppDomain>，已經卸載。</span><span class="sxs-lookup"><span data-stu-id="2633e-127">If the `event` parameter is `Event_DomainUnload`, `data` is the numeric identifier for the <xref:System.AppDomain> that was unloaded.</span></span> <span data-ttu-id="2633e-128">主機可以採取適當的動作，使用這個識別碼做為索引鍵。</span><span class="sxs-lookup"><span data-stu-id="2633e-128">The host can take appropriate action using this identifier as a key.</span></span>  
  
 <span data-ttu-id="2633e-129">如果`event`是`Event_MDAFired`，`data`是指向[MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)包含的訊息輸出從 Managed 偵錯助理 (MDA) 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2633e-129">If `event` is `Event_MDAFired`, `data` is a pointer to an [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance that contains the message output from a Managed Debugging Assistant (MDA).</span></span> <span data-ttu-id="2633e-130">Mda 是協助開發人員偵錯，所產生 XML 訊息，否則很難設陷事件有關的 clr 功能。</span><span class="sxs-lookup"><span data-stu-id="2633e-130">MDAs are a feature of the CLR that help developers with debugging, by generating XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="2633e-131">此類訊息可以是特別適用於偵錯 managed 和 unmanaged 程式碼之間的轉換。</span><span class="sxs-lookup"><span data-stu-id="2633e-131">Such messages can be especially useful in debugging transitions between managed and unmanaged code.</span></span> <span data-ttu-id="2633e-132">如需詳細資訊，請參閱[診斷 Managed 偵錯助理的錯誤](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)。</span><span class="sxs-lookup"><span data-stu-id="2633e-132">For more information, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2633e-133">需求</span><span class="sxs-lookup"><span data-stu-id="2633e-133">Requirements</span></span>  
 <span data-ttu-id="2633e-134">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2633e-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2633e-135">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2633e-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2633e-136">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2633e-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2633e-137">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2633e-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2633e-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2633e-138">See Also</span></span>  
 [<span data-ttu-id="2633e-139">使用 Managed 偵錯助理診斷錯誤</span><span class="sxs-lookup"><span data-stu-id="2633e-139">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="2633e-140">EClrEvent 列舉</span><span class="sxs-lookup"><span data-stu-id="2633e-140">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [<span data-ttu-id="2633e-141">IActionOnCLREvent 介面</span><span class="sxs-lookup"><span data-stu-id="2633e-141">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [<span data-ttu-id="2633e-142">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="2633e-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="2633e-143">ICLROnEventManager 介面</span><span class="sxs-lookup"><span data-stu-id="2633e-143">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 [<span data-ttu-id="2633e-144">MDAInfo 結構</span><span class="sxs-lookup"><span data-stu-id="2633e-144">MDAInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)
