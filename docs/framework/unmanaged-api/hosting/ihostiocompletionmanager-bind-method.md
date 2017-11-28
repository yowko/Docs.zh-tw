---
title: "IHostIoCompletionManager::Bind 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.Bind
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::Bind
helpviewer_keywords:
- IHostIoCompletionManager::Bind method [.NET Framework hosting]
- Bind method [.NET Framework hosting]
ms.assetid: acd74cb5-7e22-4a07-83c3-82288e1abd9f
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d5eba258065c5ddbbf6fad474aed700065b155a4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ihostiocompletionmanagerbind-method"></a><span data-ttu-id="ad8f4-102">IHostIoCompletionManager::Bind 方法</span><span class="sxs-lookup"><span data-stu-id="ad8f4-102">IHostIoCompletionManager::Bind Method</span></span>
<span data-ttu-id="ad8f4-103">將指定的控制代碼繫結至已建立之前呼叫 I/O 完成通訊埠[CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)。</span><span class="sxs-lookup"><span data-stu-id="ad8f4-103">Binds the specified handle to an I/O completion port that has been created by an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad8f4-104">語法</span><span class="sxs-lookup"><span data-stu-id="ad8f4-104">Syntax</span></span>  
  
```  
HRESULT Bind (  
    [in] HANDLE hPort,  
    [in] HANDLE hHandle  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ad8f4-105">參數</span><span class="sxs-lookup"><span data-stu-id="ad8f4-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="ad8f4-106">[in]I/O 完成通訊埠的繫結`hHandle`。</span><span class="sxs-lookup"><span data-stu-id="ad8f4-106">[in] The I/O completion port to which to bind `hHandle`.</span></span> <span data-ttu-id="ad8f4-107">如果值`hPort`為 null，`hHandle`繫結至預設 I/O 完成通訊埠。</span><span class="sxs-lookup"><span data-stu-id="ad8f4-107">If the value of `hPort` is null, `hHandle` is bound to the default I/O completion port.</span></span>  
  
 `hHandle`  
 <span data-ttu-id="ad8f4-108">[in]要繫結的作業系統控制代碼`hPort`。</span><span class="sxs-lookup"><span data-stu-id="ad8f4-108">[in] The operating system handle to bind to `hPort`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad8f4-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="ad8f4-109">Return Value</span></span>  
  
|<span data-ttu-id="ad8f4-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ad8f4-110">HRESULT</span></span>|<span data-ttu-id="ad8f4-111">描述</span><span class="sxs-lookup"><span data-stu-id="ad8f4-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ad8f4-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="ad8f4-112">S_OK</span></span>|<span data-ttu-id="ad8f4-113">`Bind`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="ad8f4-113">`Bind` returned successfully.</span></span>|  
|<span data-ttu-id="ad8f4-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ad8f4-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ad8f4-115">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="ad8f4-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ad8f4-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ad8f4-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ad8f4-117">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="ad8f4-117">The call timed out.</span></span>|  
|<span data-ttu-id="ad8f4-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ad8f4-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ad8f4-119">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="ad8f4-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ad8f4-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ad8f4-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ad8f4-121">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="ad8f4-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ad8f4-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ad8f4-122">E_FAIL</span></span>|<span data-ttu-id="ad8f4-123">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="ad8f4-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ad8f4-124">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="ad8f4-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ad8f4-125">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="ad8f4-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad8f4-126">備註</span><span class="sxs-lookup"><span data-stu-id="ad8f4-126">Remarks</span></span>  
 <span data-ttu-id="ad8f4-127">I/O 完成連接埠由透過呼叫`CreateIoCompletionPort`。</span><span class="sxs-lookup"><span data-stu-id="ad8f4-127">An I/O completion port is created by using a call to `CreateIoCompletionPort`.</span></span> <span data-ttu-id="ad8f4-128">CLR 會呼叫`Bind`繫結該連接埠控制代碼。</span><span class="sxs-lookup"><span data-stu-id="ad8f4-128">The CLR calls `Bind` to bind a handle to that port.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ad8f4-129">I/O 要求完成時，主機必須呼叫[iclriocompletionmanager:: Oncomplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="ad8f4-129">When an I/O request completes, the host must call the [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad8f4-130">需求</span><span class="sxs-lookup"><span data-stu-id="ad8f4-130">Requirements</span></span>  
 <span data-ttu-id="ad8f4-131">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ad8f4-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad8f4-132">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ad8f4-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ad8f4-133">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ad8f4-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ad8f4-134">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad8f4-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad8f4-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad8f4-135">See Also</span></span>  
 [<span data-ttu-id="ad8f4-136">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="ad8f4-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
