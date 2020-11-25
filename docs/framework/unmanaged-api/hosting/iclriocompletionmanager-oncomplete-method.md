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
ms.openlocfilehash: 15119974acf74b49669e5ffbee59fbff9e5c84c9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714090"
---
# <a name="iclriocompletionmanageroncomplete-method"></a><span data-ttu-id="0e706-102">ICLRIoCompletionManager::OnComplete 方法</span><span class="sxs-lookup"><span data-stu-id="0e706-102">ICLRIoCompletionManager::OnComplete Method</span></span>

<span data-ttu-id="0e706-103">通知 common language runtime (CLR) 使用 [IHostIoCompletionManager：： Bind](ihostiocompletionmanager-bind-method.md) 方法的呼叫所提出之 i/o 要求的狀態。</span><span class="sxs-lookup"><span data-stu-id="0e706-103">Notifies the common language runtime (CLR) of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](ihostiocompletionmanager-bind-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e706-104">語法</span><span class="sxs-lookup"><span data-stu-id="0e706-104">Syntax</span></span>  
  
```cpp  
HRESULT OnComplete (  
    [in] DWORD dwErrorCode,  
    [in] DWORD NumberOfBytesTransferred,  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e706-105">參數</span><span class="sxs-lookup"><span data-stu-id="0e706-105">Parameters</span></span>  

 `dwErrorCode`  
 <span data-ttu-id="0e706-106">在HRESULT 值，指出系結作業的狀態。</span><span class="sxs-lookup"><span data-stu-id="0e706-106">[in] An HRESULT value that indicates the status of the bind operation.</span></span>  
  
- <span data-ttu-id="0e706-107">S_OK 表示作業已順利完成。</span><span class="sxs-lookup"><span data-stu-id="0e706-107">S_OK indicates that the operation completed successfully.</span></span>  
  
- <span data-ttu-id="0e706-108">HOST_E_INTERRUPTED 表示呼叫會在完成前終止。</span><span class="sxs-lookup"><span data-stu-id="0e706-108">HOST_E_INTERRUPTED indicates that the call terminated before completion.</span></span>  
  
- <span data-ttu-id="0e706-109">E_FAIL 表示發生未知、無法復原的災難性失敗。</span><span class="sxs-lookup"><span data-stu-id="0e706-109">E_FAIL indicates that an unknown, unrecoverable, catastrophic failure occurred.</span></span>  
  
 `NumberOfBytesTransferred`  
 <span data-ttu-id="0e706-110">在處理 i/o 要求期間傳送的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="0e706-110">[in] The number of bytes transferred during the processing of the I/O request.</span></span>  
  
 `pvOverlapped`  
 <span data-ttu-id="0e706-111">在 `OVERLAPPED` 傳遞給方法之呼叫的結構指標 `IHostIoCompletionManager::Bind` 。</span><span class="sxs-lookup"><span data-stu-id="0e706-111">[in] A pointer to the `OVERLAPPED` structure that was passed to the call to the `IHostIoCompletionManager::Bind` method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0e706-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="0e706-112">Return Value</span></span>  
  
|<span data-ttu-id="0e706-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0e706-113">HRESULT</span></span>|<span data-ttu-id="0e706-114">描述</span><span class="sxs-lookup"><span data-stu-id="0e706-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0e706-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="0e706-115">S_OK</span></span>|<span data-ttu-id="0e706-116">`OnComplete` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="0e706-116">`OnComplete` returned successfully.</span></span>|  
|<span data-ttu-id="0e706-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0e706-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0e706-118">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="0e706-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0e706-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0e706-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0e706-120">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="0e706-120">The call timed out.</span></span>|  
|<span data-ttu-id="0e706-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0e706-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0e706-122">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="0e706-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0e706-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0e706-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0e706-124">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="0e706-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0e706-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0e706-125">E_FAIL</span></span>|<span data-ttu-id="0e706-126">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="0e706-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0e706-127">在方法傳回 E_FAIL 之後，就無法在進程中使用 CLR。</span><span class="sxs-lookup"><span data-stu-id="0e706-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0e706-128">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="0e706-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e706-129">備註</span><span class="sxs-lookup"><span data-stu-id="0e706-129">Remarks</span></span>  

 <span data-ttu-id="0e706-130">如果主機執行 i/o 完成抽象概念，則 CLR 會使用 [IHostIoCompletionManager](ihostiocompletionmanager-interface.md)的方法，透過主控制項發出 i/o 要求。</span><span class="sxs-lookup"><span data-stu-id="0e706-130">If the host implements an I/O completion abstraction, the CLR makes I/O requests through the host by using methods of [IHostIoCompletionManager](ihostiocompletionmanager-interface.md).</span></span> <span data-ttu-id="0e706-131">然後，主機會呼叫 `OnComplete` 方法，以通知執行時間產生這類要求的結果。</span><span class="sxs-lookup"><span data-stu-id="0e706-131">The host then calls the `OnComplete` method to notify the runtime of the outcome of such requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e706-132">需求</span><span class="sxs-lookup"><span data-stu-id="0e706-132">Requirements</span></span>  

 <span data-ttu-id="0e706-133">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0e706-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e706-134">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="0e706-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0e706-135">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="0e706-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0e706-136">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e706-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e706-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e706-137">See also</span></span>

- [<span data-ttu-id="0e706-138">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="0e706-138">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="0e706-139">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="0e706-139">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="0e706-140">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="0e706-140">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
