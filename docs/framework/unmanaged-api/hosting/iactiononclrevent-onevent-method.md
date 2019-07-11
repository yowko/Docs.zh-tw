---
title: IActionOnCLREvent::OnEvent 方法
ms.date: 03/30/2017
api_name:
- IActionOnCLREvent.OnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IActionOnCLREvent::OnEvent
helpviewer_keywords:
- OnEvent method [.NET Framework hosting]
- IActionOnCLREvent::OnEvent method [.NET Framework hosting]
ms.assetid: 0970f10c-4304-4c12-91c0-83e51455afb4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 777cf1084f77587b83ff63a02ba84d474be0f87c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757844"
---
# <a name="iactiononclreventonevent-method"></a><span data-ttu-id="c3a87-102">IActionOnCLREvent::OnEvent 方法</span><span class="sxs-lookup"><span data-stu-id="c3a87-102">IActionOnCLREvent::OnEvent Method</span></span>
<span data-ttu-id="c3a87-103">對事件所使用的呼叫已註冊的回呼[iclroneventmanager:: Registeractiononevent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="c3a87-103">Performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3a87-104">語法</span><span class="sxs-lookup"><span data-stu-id="c3a87-104">Syntax</span></span>  
  
```cpp  
HRESULT OnEvent (  
    [in] EClrEvent event,  
    [in] PVOID     data  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3a87-105">參數</span><span class="sxs-lookup"><span data-stu-id="c3a87-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="c3a87-106">[in]其中一個[EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)值，指出事件的型別。</span><span class="sxs-lookup"><span data-stu-id="c3a87-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, which indicates the type of event.</span></span>  
  
 `data`  
 <span data-ttu-id="c3a87-107">[in]包含有關的詳細資料物件的指標`event`。</span><span class="sxs-lookup"><span data-stu-id="c3a87-107">[in] A pointer to an object that contains details about `event`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3a87-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="c3a87-108">Return Value</span></span>  
  
|<span data-ttu-id="c3a87-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c3a87-109">HRESULT</span></span>|<span data-ttu-id="c3a87-110">說明</span><span class="sxs-lookup"><span data-stu-id="c3a87-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c3a87-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c3a87-111">S_OK</span></span>|<span data-ttu-id="c3a87-112">`OnEvent` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="c3a87-112">`OnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="c3a87-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c3a87-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c3a87-114">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="c3a87-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c3a87-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c3a87-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c3a87-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="c3a87-116">The call timed out.</span></span>|  
|<span data-ttu-id="c3a87-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c3a87-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c3a87-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="c3a87-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c3a87-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c3a87-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c3a87-120">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="c3a87-120">An event was cancelled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c3a87-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c3a87-121">E_FAIL</span></span>|<span data-ttu-id="c3a87-122">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="c3a87-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c3a87-123">如果方法會傳回 E_FAIL，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="c3a87-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c3a87-124">任何裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="c3a87-124">Subsequent calls to any hosting method return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3a87-125">備註</span><span class="sxs-lookup"><span data-stu-id="c3a87-125">Remarks</span></span>  
 <span data-ttu-id="c3a87-126">`data`參數是未指定類型之物件的指標。</span><span class="sxs-lookup"><span data-stu-id="c3a87-126">The `data` parameter is a pointer to an object of unspecified type.</span></span> <span data-ttu-id="c3a87-127">如果`event`參數是`Event_DomainUnload`，`data`的數值識別碼<xref:System.AppDomain>，已經卸載。</span><span class="sxs-lookup"><span data-stu-id="c3a87-127">If the `event` parameter is `Event_DomainUnload`, `data` is the numeric identifier for the <xref:System.AppDomain> that was unloaded.</span></span> <span data-ttu-id="c3a87-128">主機可以採取適當的動作，使用這個識別碼做為索引鍵。</span><span class="sxs-lookup"><span data-stu-id="c3a87-128">The host can take appropriate action using this identifier as a key.</span></span>  
  
 <span data-ttu-id="c3a87-129">如果`event`已`Event_MDAFired`，`data`是一個指向[MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)執行個體，包含的訊息輸出從 Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="c3a87-129">If `event` is `Event_MDAFired`, `data` is a pointer to an [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance that contains the message output from a Managed Debugging Assistant (MDA).</span></span> <span data-ttu-id="c3a87-130">Mda 是協助開發人員偵錯，藉由產生 XML 訊息的相關事件，否則很難攔截的 clr 功能。</span><span class="sxs-lookup"><span data-stu-id="c3a87-130">MDAs are a feature of the CLR that help developers with debugging, by generating XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="c3a87-131">這類訊息可以是特別適用於偵錯 managed 和 unmanaged 程式碼之間的轉換。</span><span class="sxs-lookup"><span data-stu-id="c3a87-131">Such messages can be especially useful in debugging transitions between managed and unmanaged code.</span></span> <span data-ttu-id="c3a87-132">如需詳細資訊，請參閱 < [Managed 偵錯助理診斷錯誤](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)。</span><span class="sxs-lookup"><span data-stu-id="c3a87-132">For more information, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3a87-133">需求</span><span class="sxs-lookup"><span data-stu-id="c3a87-133">Requirements</span></span>  
 <span data-ttu-id="c3a87-134">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c3a87-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3a87-135">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c3a87-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c3a87-136">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c3a87-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c3a87-137">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3a87-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3a87-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3a87-138">See also</span></span>

- [<span data-ttu-id="c3a87-139">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="c3a87-139">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="c3a87-140">EClrEvent 列舉</span><span class="sxs-lookup"><span data-stu-id="c3a87-140">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="c3a87-141">IActionOnCLREvent 介面</span><span class="sxs-lookup"><span data-stu-id="c3a87-141">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="c3a87-142">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="c3a87-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="c3a87-143">ICLROnEventManager 介面</span><span class="sxs-lookup"><span data-stu-id="c3a87-143">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
- [<span data-ttu-id="c3a87-144">MDAInfo 結構</span><span class="sxs-lookup"><span data-stu-id="c3a87-144">MDAInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)
