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
ms.openlocfilehash: 39c9752912e88b04455516c0e9bed43610ba8aa0
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703822"
---
# <a name="iclriocompletionmanageroncomplete-method"></a><span data-ttu-id="eb124-102">ICLRIoCompletionManager::OnComplete 方法</span><span class="sxs-lookup"><span data-stu-id="eb124-102">ICLRIoCompletionManager::OnComplete Method</span></span>
<span data-ttu-id="eb124-103">使用對[IHostIoCompletionManager：： Bind](ihostiocompletionmanager-bind-method.md)方法的呼叫，通知 common language RUNTIME （CLR）所發出的 i/o 要求狀態。</span><span class="sxs-lookup"><span data-stu-id="eb124-103">Notifies the common language runtime (CLR) of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](ihostiocompletionmanager-bind-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb124-104">語法</span><span class="sxs-lookup"><span data-stu-id="eb124-104">Syntax</span></span>  
  
```cpp  
HRESULT OnComplete (  
    [in] DWORD dwErrorCode,  
    [in] DWORD NumberOfBytesTransferred,  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb124-105">參數</span><span class="sxs-lookup"><span data-stu-id="eb124-105">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="eb124-106">在HRESULT 值，指出系結作業的狀態。</span><span class="sxs-lookup"><span data-stu-id="eb124-106">[in] An HRESULT value that indicates the status of the bind operation.</span></span>  
  
- <span data-ttu-id="eb124-107">S_OK 表示作業已成功完成。</span><span class="sxs-lookup"><span data-stu-id="eb124-107">S_OK indicates that the operation completed successfully.</span></span>  
  
- <span data-ttu-id="eb124-108">HOST_E_INTERRUPTED 表示呼叫在完成前終止。</span><span class="sxs-lookup"><span data-stu-id="eb124-108">HOST_E_INTERRUPTED indicates that the call terminated before completion.</span></span>  
  
- <span data-ttu-id="eb124-109">E_FAIL 表示發生未知、無法復原、嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="eb124-109">E_FAIL indicates that an unknown, unrecoverable, catastrophic failure occurred.</span></span>  
  
 `NumberOfBytesTransferred`  
 <span data-ttu-id="eb124-110">在處理 i/o 要求期間所傳輸的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="eb124-110">[in] The number of bytes transferred during the processing of the I/O request.</span></span>  
  
 `pvOverlapped`  
 <span data-ttu-id="eb124-111">在`OVERLAPPED`傳遞至方法之呼叫的結構指標 `IHostIoCompletionManager::Bind` 。</span><span class="sxs-lookup"><span data-stu-id="eb124-111">[in] A pointer to the `OVERLAPPED` structure that was passed to the call to the `IHostIoCompletionManager::Bind` method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eb124-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="eb124-112">Return Value</span></span>  
  
|<span data-ttu-id="eb124-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="eb124-113">HRESULT</span></span>|<span data-ttu-id="eb124-114">說明</span><span class="sxs-lookup"><span data-stu-id="eb124-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eb124-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="eb124-115">S_OK</span></span>|<span data-ttu-id="eb124-116">`OnComplete`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="eb124-116">`OnComplete` returned successfully.</span></span>|  
|<span data-ttu-id="eb124-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="eb124-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="eb124-118">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="eb124-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="eb124-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="eb124-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="eb124-120">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="eb124-120">The call timed out.</span></span>|  
|<span data-ttu-id="eb124-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="eb124-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="eb124-122">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="eb124-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="eb124-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="eb124-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="eb124-124">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="eb124-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="eb124-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="eb124-125">E_FAIL</span></span>|<span data-ttu-id="eb124-126">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="eb124-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="eb124-127">在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="eb124-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="eb124-128">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="eb124-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb124-129">備註</span><span class="sxs-lookup"><span data-stu-id="eb124-129">Remarks</span></span>  
 <span data-ttu-id="eb124-130">如果主機執行 i/o 完成抽象概念，CLR 會使用[IHostIoCompletionManager](ihostiocompletionmanager-interface.md)的方法，透過主機進行 i/o 要求。</span><span class="sxs-lookup"><span data-stu-id="eb124-130">If the host implements an I/O completion abstraction, the CLR makes I/O requests through the host by using methods of [IHostIoCompletionManager](ihostiocompletionmanager-interface.md).</span></span> <span data-ttu-id="eb124-131">然後，主機會呼叫 `OnComplete` 方法，以通知執行時間此類要求的結果。</span><span class="sxs-lookup"><span data-stu-id="eb124-131">The host then calls the `OnComplete` method to notify the runtime of the outcome of such requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb124-132">需求</span><span class="sxs-lookup"><span data-stu-id="eb124-132">Requirements</span></span>  
 <span data-ttu-id="eb124-133">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eb124-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb124-134">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="eb124-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eb124-135">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="eb124-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eb124-136">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb124-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb124-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb124-137">See also</span></span>

- [<span data-ttu-id="eb124-138">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="eb124-138">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="eb124-139">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="eb124-139">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="eb124-140">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="eb124-140">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
