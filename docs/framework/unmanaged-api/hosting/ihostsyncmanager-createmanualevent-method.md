---
title: IHostSyncManager::CreateManualEvent 方法
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateManualEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateManualEvent
helpviewer_keywords:
- CreateManualEvent method [.NET Framework hosting]
- IHostSyncManager::CreateManualEvent method [.NET Framework hosting]
ms.assetid: 68661fbd-09cf-46dc-890b-e694f8a3880a
topic_type:
- apiref
ms.openlocfilehash: 334520df749ba428e6480188cd0655bb734725a6
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803300"
---
# <a name="ihostsyncmanagercreatemanualevent-method"></a><span data-ttu-id="9c4b4-102">IHostSyncManager::CreateManualEvent 方法</span><span class="sxs-lookup"><span data-stu-id="9c4b4-102">IHostSyncManager::CreateManualEvent Method</span></span>
<span data-ttu-id="9c4b4-103">建立手動重設事件物件。</span><span class="sxs-lookup"><span data-stu-id="9c4b4-103">Creates a manual-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c4b4-104">語法</span><span class="sxs-lookup"><span data-stu-id="9c4b4-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateManualEvent (  
    [in]  BOOL bInitialState,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c4b4-105">參數</span><span class="sxs-lookup"><span data-stu-id="9c4b4-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="9c4b4-106">[in] `true` ，如果物件已收到信號，則為，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="9c4b4-106">[in] `true`, if the object is signaled; otherwise, `false`.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="9c4b4-107">脫銷[IHostManualEvent](ihostmanualevent-interface.md)實例位址的指標，如果無法建立事件則為 null。</span><span class="sxs-lookup"><span data-stu-id="9c4b4-107">[out] A pointer to the address of an [IHostManualEvent](ihostmanualevent-interface.md) instance, or null if the event could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9c4b4-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="9c4b4-108">Return Value</span></span>  
  
|<span data-ttu-id="9c4b4-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9c4b4-109">HRESULT</span></span>|<span data-ttu-id="9c4b4-110">描述</span><span class="sxs-lookup"><span data-stu-id="9c4b4-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9c4b4-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9c4b4-111">S_OK</span></span>|<span data-ttu-id="9c4b4-112">`CreateManualEvent`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="9c4b4-112">`CreateManualEvent` returned successfully.</span></span>|  
|<span data-ttu-id="9c4b4-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9c4b4-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9c4b4-114">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="9c4b4-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9c4b4-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9c4b4-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9c4b4-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="9c4b4-116">The call timed out.</span></span>|  
|<span data-ttu-id="9c4b4-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9c4b4-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9c4b4-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="9c4b4-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9c4b4-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9c4b4-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9c4b4-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="9c4b4-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9c4b4-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9c4b4-121">E_FAIL</span></span>|<span data-ttu-id="9c4b4-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="9c4b4-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9c4b4-123">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="9c4b4-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9c4b4-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="9c4b4-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9c4b4-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="9c4b4-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="9c4b4-126">沒有足夠的記憶體可用來建立要求的事件物件。</span><span class="sxs-lookup"><span data-stu-id="9c4b4-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c4b4-127">備註</span><span class="sxs-lookup"><span data-stu-id="9c4b4-127">Remarks</span></span>  
 <span data-ttu-id="9c4b4-128">`CreateManualEvent`建立 `IHostManualEvent` ，這是手動重設的事件物件，需要呼叫[IHostManualEvent：： reset](ihostmanualevent-reset-method.md)方法，才能將它設定為非信號狀態。</span><span class="sxs-lookup"><span data-stu-id="9c4b4-128">`CreateManualEvent` creates an `IHostManualEvent`, a manual-reset event object that requires a call to the [IHostManualEvent::Reset](ihostmanualevent-reset-method.md) method to set it to a non-signaled state.</span></span> <span data-ttu-id="9c4b4-129">`CreateManualEvent``CreateEvent`使用 `true` 針對參數所指定的值來鏡像 Win32 函數 `bManualReset` 。</span><span class="sxs-lookup"><span data-stu-id="9c4b4-129">`CreateManualEvent` mirrors the Win32 `CreateEvent` function with a value of `true` specified for the `bManualReset` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c4b4-130">規格需求</span><span class="sxs-lookup"><span data-stu-id="9c4b4-130">Requirements</span></span>  
 <span data-ttu-id="9c4b4-131">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9c4b4-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c4b4-132">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="9c4b4-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9c4b4-133">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9c4b4-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9c4b4-134">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c4b4-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c4b4-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c4b4-135">See also</span></span>

- [<span data-ttu-id="9c4b4-136">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="9c4b4-136">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="9c4b4-137">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="9c4b4-137">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="9c4b4-138">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="9c4b4-138">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
