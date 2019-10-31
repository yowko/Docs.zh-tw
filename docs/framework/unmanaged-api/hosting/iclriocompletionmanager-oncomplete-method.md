---
title: ICLRIoCompletionManager::OnComplete 方法
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager.OnComplete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager::OnComplete
helpviewer_keywords:
- OnComplete method [.NET Framework hosting]
- ICLRIoCompletionManager::OnComplete method [.NET Framework hosting]
ms.assetid: 003f6974-9727-4322-bed5-e330d1224d0b
topic_type:
- apiref
ms.openlocfilehash: b44a71137e39130bb0fe4c303fdff62c76d38cbd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141019"
---
# <a name="iclriocompletionmanageroncomplete-method"></a><span data-ttu-id="3a2bf-102">ICLRIoCompletionManager::OnComplete 方法</span><span class="sxs-lookup"><span data-stu-id="3a2bf-102">ICLRIoCompletionManager::OnComplete Method</span></span>
<span data-ttu-id="3a2bf-103">使用對[IHostIoCompletionManager：： Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)方法的呼叫，通知 common language RUNTIME （CLR）所發出的 i/o 要求狀態。</span><span class="sxs-lookup"><span data-stu-id="3a2bf-103">Notifies the common language runtime (CLR) of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a2bf-104">語法</span><span class="sxs-lookup"><span data-stu-id="3a2bf-104">Syntax</span></span>  
  
```cpp  
HRESULT OnComplete (  
    [in] DWORD dwErrorCode,  
    [in] DWORD NumberOfBytesTransferred,  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a2bf-105">參數</span><span class="sxs-lookup"><span data-stu-id="3a2bf-105">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="3a2bf-106">在HRESULT 值，指出系結作業的狀態。</span><span class="sxs-lookup"><span data-stu-id="3a2bf-106">[in] An HRESULT value that indicates the status of the bind operation.</span></span>  
  
- <span data-ttu-id="3a2bf-107">S_OK 表示作業已成功完成。</span><span class="sxs-lookup"><span data-stu-id="3a2bf-107">S_OK indicates that the operation completed successfully.</span></span>  
  
- <span data-ttu-id="3a2bf-108">HOST_E_INTERRUPTED 表示呼叫在完成前終止。</span><span class="sxs-lookup"><span data-stu-id="3a2bf-108">HOST_E_INTERRUPTED indicates that the call terminated before completion.</span></span>  
  
- <span data-ttu-id="3a2bf-109">E_FAIL 表示發生未知、無法復原、嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="3a2bf-109">E_FAIL indicates that an unknown, unrecoverable, catastrophic failure occurred.</span></span>  
  
 `NumberOfBytesTransferred`  
 <span data-ttu-id="3a2bf-110">在處理 i/o 要求期間所傳輸的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="3a2bf-110">[in] The number of bytes transferred during the processing of the I/O request.</span></span>  
  
 `pvOverlapped`  
 <span data-ttu-id="3a2bf-111">在傳遞至呼叫 `IHostIoCompletionManager::Bind` 方法之 `OVERLAPPED` 結構的指標。</span><span class="sxs-lookup"><span data-stu-id="3a2bf-111">[in] A pointer to the `OVERLAPPED` structure that was passed to the call to the `IHostIoCompletionManager::Bind` method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3a2bf-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="3a2bf-112">Return Value</span></span>  
  
|<span data-ttu-id="3a2bf-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3a2bf-113">HRESULT</span></span>|<span data-ttu-id="3a2bf-114">描述</span><span class="sxs-lookup"><span data-stu-id="3a2bf-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3a2bf-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="3a2bf-115">S_OK</span></span>|<span data-ttu-id="3a2bf-116">已成功傳回 `OnComplete`。</span><span class="sxs-lookup"><span data-stu-id="3a2bf-116">`OnComplete` returned successfully.</span></span>|  
|<span data-ttu-id="3a2bf-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3a2bf-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3a2bf-118">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="3a2bf-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3a2bf-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3a2bf-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3a2bf-120">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="3a2bf-120">The call timed out.</span></span>|  
|<span data-ttu-id="3a2bf-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3a2bf-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3a2bf-122">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="3a2bf-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3a2bf-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3a2bf-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3a2bf-124">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="3a2bf-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3a2bf-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3a2bf-125">E_FAIL</span></span>|<span data-ttu-id="3a2bf-126">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="3a2bf-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3a2bf-127">在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="3a2bf-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3a2bf-128">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="3a2bf-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a2bf-129">備註</span><span class="sxs-lookup"><span data-stu-id="3a2bf-129">Remarks</span></span>  
 <span data-ttu-id="3a2bf-130">如果主機執行 i/o 完成抽象概念，CLR 會使用[IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)的方法，透過主機進行 i/o 要求。</span><span class="sxs-lookup"><span data-stu-id="3a2bf-130">If the host implements an I/O completion abstraction, the CLR makes I/O requests through the host by using methods of [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md).</span></span> <span data-ttu-id="3a2bf-131">然後，主機會呼叫 `OnComplete` 方法，以通知執行時間此類要求的結果。</span><span class="sxs-lookup"><span data-stu-id="3a2bf-131">The host then calls the `OnComplete` method to notify the runtime of the outcome of such requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a2bf-132">需求</span><span class="sxs-lookup"><span data-stu-id="3a2bf-132">Requirements</span></span>  
 <span data-ttu-id="3a2bf-133">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3a2bf-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a2bf-134">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="3a2bf-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3a2bf-135">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3a2bf-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3a2bf-136">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a2bf-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a2bf-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="3a2bf-137">See also</span></span>

- [<span data-ttu-id="3a2bf-138">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="3a2bf-138">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="3a2bf-139">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="3a2bf-139">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="3a2bf-140">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="3a2bf-140">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
