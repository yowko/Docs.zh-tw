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
ms.openlocfilehash: 3bfcb01e30b4cb33ec9276f1d3c6ac2f3bde4b58
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721760"
---
# <a name="iactiononclreventonevent-method"></a><span data-ttu-id="576df-102">IActionOnCLREvent::OnEvent 方法</span><span class="sxs-lookup"><span data-stu-id="576df-102">IActionOnCLREvent::OnEvent Method</span></span>

<span data-ttu-id="576df-103">針對已使用 [ICLROnEventManager：： RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) 方法呼叫註冊的事件，執行回呼。</span><span class="sxs-lookup"><span data-stu-id="576df-103">Performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="576df-104">語法</span><span class="sxs-lookup"><span data-stu-id="576df-104">Syntax</span></span>  
  
```cpp  
HRESULT OnEvent (  
    [in] EClrEvent event,  
    [in] PVOID     data  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="576df-105">參數</span><span class="sxs-lookup"><span data-stu-id="576df-105">Parameters</span></span>  

 `event`  
 <span data-ttu-id="576df-106">在其中一個 [EClrEvent](eclrevent-enumeration.md) 值，表示事件的類型。</span><span class="sxs-lookup"><span data-stu-id="576df-106">[in] One of the [EClrEvent](eclrevent-enumeration.md) values, which indicates the type of event.</span></span>  
  
 `data`  
 <span data-ttu-id="576df-107">在物件的指標，其中包含的詳細資料 `event` 。</span><span class="sxs-lookup"><span data-stu-id="576df-107">[in] A pointer to an object that contains details about `event`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="576df-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="576df-108">Return Value</span></span>  
  
|<span data-ttu-id="576df-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="576df-109">HRESULT</span></span>|<span data-ttu-id="576df-110">描述</span><span class="sxs-lookup"><span data-stu-id="576df-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="576df-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="576df-111">S_OK</span></span>|<span data-ttu-id="576df-112">`OnEvent` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="576df-112">`OnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="576df-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="576df-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="576df-114">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="576df-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="576df-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="576df-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="576df-116">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="576df-116">The call timed out.</span></span>|  
|<span data-ttu-id="576df-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="576df-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="576df-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="576df-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="576df-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="576df-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="576df-120">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="576df-120">An event was cancelled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="576df-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="576df-121">E_FAIL</span></span>|<span data-ttu-id="576df-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="576df-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="576df-123">如果方法傳回 E_FAIL，則 CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="576df-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="576df-124">對任何裝載方法的後續呼叫都會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="576df-124">Subsequent calls to any hosting method return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="576df-125">備註</span><span class="sxs-lookup"><span data-stu-id="576df-125">Remarks</span></span>  

 <span data-ttu-id="576df-126">`data`參數是未指定類型之物件的指標。</span><span class="sxs-lookup"><span data-stu-id="576df-126">The `data` parameter is a pointer to an object of unspecified type.</span></span> <span data-ttu-id="576df-127">如果 `event` 參數為 `Event_DomainUnload` ， `data` 則是已卸載之的數值識別碼 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="576df-127">If the `event` parameter is `Event_DomainUnload`, `data` is the numeric identifier for the <xref:System.AppDomain> that was unloaded.</span></span> <span data-ttu-id="576df-128">主機可以使用此識別碼作為索引鍵，以採取適當的動作。</span><span class="sxs-lookup"><span data-stu-id="576df-128">The host can take appropriate action using this identifier as a key.</span></span>  
  
 <span data-ttu-id="576df-129">如果 `event` 為 `Event_MDAFired` ， `data` 則是 [MDAInfo](mdainfo-structure.md) 實例的指標，其中包含 Managed 偵錯工具 (MDA) 的訊息輸出。</span><span class="sxs-lookup"><span data-stu-id="576df-129">If `event` is `Event_MDAFired`, `data` is a pointer to an [MDAInfo](mdainfo-structure.md) instance that contains the message output from a Managed Debugging Assistant (MDA).</span></span> <span data-ttu-id="576df-130">Mda 是 CLR 的一項功能，可協助開發人員進行偵錯工具，方法是產生有關其他難以捕捉之事件的 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="576df-130">MDAs are a feature of the CLR that help developers with debugging, by generating XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="576df-131">這類訊息在 managed 和非受控碼之間的轉換進行調試時特別有用。</span><span class="sxs-lookup"><span data-stu-id="576df-131">Such messages can be especially useful in debugging transitions between managed and unmanaged code.</span></span> <span data-ttu-id="576df-132">如需詳細資訊，請參閱 [診斷 Managed 偵錯工具的錯誤](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)。</span><span class="sxs-lookup"><span data-stu-id="576df-132">For more information, see [Diagnosing Errors with Managed Debugging Assistants](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="576df-133">需求</span><span class="sxs-lookup"><span data-stu-id="576df-133">Requirements</span></span>  

 <span data-ttu-id="576df-134">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="576df-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="576df-135">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="576df-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="576df-136">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="576df-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="576df-137">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="576df-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="576df-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="576df-138">See also</span></span>

- [<span data-ttu-id="576df-139">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="576df-139">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="576df-140">EClrEvent 列舉</span><span class="sxs-lookup"><span data-stu-id="576df-140">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="576df-141">IActionOnCLREvent 介面</span><span class="sxs-lookup"><span data-stu-id="576df-141">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="576df-142">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="576df-142">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="576df-143">ICLROnEventManager 介面</span><span class="sxs-lookup"><span data-stu-id="576df-143">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
- [<span data-ttu-id="576df-144">MDAInfo 結構</span><span class="sxs-lookup"><span data-stu-id="576df-144">MDAInfo Structure</span></span>](mdainfo-structure.md)
