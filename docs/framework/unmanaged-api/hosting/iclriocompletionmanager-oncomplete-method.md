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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f0d9d4336b79b60e69f980b6d5931e2994732f30
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61792687"
---
# <a name="iclriocompletionmanageroncomplete-method"></a><span data-ttu-id="bb353-102">ICLRIoCompletionManager::OnComplete 方法</span><span class="sxs-lookup"><span data-stu-id="bb353-102">ICLRIoCompletionManager::OnComplete Method</span></span>
<span data-ttu-id="bb353-103">狀態的 I/O 要求所使用的呼叫會告知 common language runtime (CLR) [ihostiocompletionmanager:: Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="bb353-103">Notifies the common language runtime (CLR) of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb353-104">語法</span><span class="sxs-lookup"><span data-stu-id="bb353-104">Syntax</span></span>  
  
```  
HRESULT OnComplete (  
    [in] DWORD dwErrorCode,  
    [in] DWORD NumberOfBytesTransferred,  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb353-105">參數</span><span class="sxs-lookup"><span data-stu-id="bb353-105">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="bb353-106">[in]HRESULT 值，指出繫結作業的狀態。</span><span class="sxs-lookup"><span data-stu-id="bb353-106">[in] An HRESULT value that indicates the status of the bind operation.</span></span>  
  
- <span data-ttu-id="bb353-107">S_OK 表示作業已順利完成。</span><span class="sxs-lookup"><span data-stu-id="bb353-107">S_OK indicates that the operation completed successfully.</span></span>  
  
- <span data-ttu-id="bb353-108">HOST_E_INTERRUPTED 指出呼叫結束之前完成。</span><span class="sxs-lookup"><span data-stu-id="bb353-108">HOST_E_INTERRUPTED indicates that the call terminated before completion.</span></span>  
  
- <span data-ttu-id="bb353-109">E_FAIL 表示未知，無法復原，災難性的失敗發生。</span><span class="sxs-lookup"><span data-stu-id="bb353-109">E_FAIL indicates that an unknown, unrecoverable, catastrophic failure occurred.</span></span>  
  
 `NumberOfBytesTransferred`  
 <span data-ttu-id="bb353-110">[in]I/O 要求處理期間，傳輸的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="bb353-110">[in] The number of bytes transferred during the processing of the I/O request.</span></span>  
  
 `pvOverlapped`  
 <span data-ttu-id="bb353-111">[in]指標`OVERLAPPED`傳遞至呼叫的結構`IHostIoCompletionManager::Bind`方法。</span><span class="sxs-lookup"><span data-stu-id="bb353-111">[in] A pointer to the `OVERLAPPED` structure that was passed to the call to the `IHostIoCompletionManager::Bind` method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bb353-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="bb353-112">Return Value</span></span>  
  
|<span data-ttu-id="bb353-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bb353-113">HRESULT</span></span>|<span data-ttu-id="bb353-114">描述</span><span class="sxs-lookup"><span data-stu-id="bb353-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bb353-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="bb353-115">S_OK</span></span>|<span data-ttu-id="bb353-116">`OnComplete` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="bb353-116">`OnComplete` returned successfully.</span></span>|  
|<span data-ttu-id="bb353-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bb353-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bb353-118">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="bb353-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bb353-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bb353-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bb353-120">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="bb353-120">The call timed out.</span></span>|  
|<span data-ttu-id="bb353-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bb353-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bb353-122">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="bb353-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bb353-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bb353-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bb353-124">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="bb353-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bb353-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bb353-125">E_FAIL</span></span>|<span data-ttu-id="bb353-126">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="bb353-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bb353-127">方法會傳回 E_FAIL 之後，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="bb353-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bb353-128">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="bb353-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb353-129">備註</span><span class="sxs-lookup"><span data-stu-id="bb353-129">Remarks</span></span>  
 <span data-ttu-id="bb353-130">如果主應用程式實作的 I/O 完成抽象概念，CLR 會透過主機的 I/O 要求使用的方法[IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="bb353-130">If the host implements an I/O completion abstraction, the CLR makes I/O requests through the host by using methods of [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md).</span></span> <span data-ttu-id="bb353-131">主應用程式接著會呼叫`OnComplete`方法來通知執行階段的這類要求的結果。</span><span class="sxs-lookup"><span data-stu-id="bb353-131">The host then calls the `OnComplete` method to notify the runtime of the outcome of such requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb353-132">需求</span><span class="sxs-lookup"><span data-stu-id="bb353-132">Requirements</span></span>  
 <span data-ttu-id="bb353-133">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bb353-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb353-134">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bb353-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bb353-135">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="bb353-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bb353-136">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb353-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb353-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb353-137">See also</span></span>

- [<span data-ttu-id="bb353-138">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="bb353-138">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="bb353-139">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="bb353-139">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="bb353-140">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="bb353-140">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
