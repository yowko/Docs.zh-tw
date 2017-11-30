---
title: "IHostIoCompletionManager::CreateIoCompletionPort 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.CreateIoCompletionPort
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::CreateIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CreateIoCompletionPort method [.NET Framework hosting]
- CreateIoCompletionPort method [.NET Framework hosting]
ms.assetid: 907a2b43-68db-44a7-acac-89e792e7bb3c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c1942c34b0807b76bbe25aedc60b7b1c6fecc87e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ihostiocompletionmanagercreateiocompletionport-method"></a><span data-ttu-id="51023-102">IHostIoCompletionManager::CreateIoCompletionPort 方法</span><span class="sxs-lookup"><span data-stu-id="51023-102">IHostIoCompletionManager::CreateIoCompletionPort Method</span></span>
<span data-ttu-id="51023-103">主應用程式建立新的 I/O 完成通訊埠的要求。</span><span class="sxs-lookup"><span data-stu-id="51023-103">Requests that the host create a new I/O completion port.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51023-104">語法</span><span class="sxs-lookup"><span data-stu-id="51023-104">Syntax</span></span>  
  
```  
HRESULT CreateIoCompletionPort (  
    [out] HANDLE *phPort  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="51023-105">參數</span><span class="sxs-lookup"><span data-stu-id="51023-105">Parameters</span></span>  
 `phPort`  
 <span data-ttu-id="51023-106">[out]指標，新建的 I/O 完成通訊埠或 0 （零），如果無法建立連接埠控制代碼。</span><span class="sxs-lookup"><span data-stu-id="51023-106">[out] A pointer to a handle to the newly created I/O completion port, or 0 (zero), if the port could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="51023-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="51023-107">Return Value</span></span>  
  
|<span data-ttu-id="51023-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="51023-108">HRESULT</span></span>|<span data-ttu-id="51023-109">描述</span><span class="sxs-lookup"><span data-stu-id="51023-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="51023-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="51023-110">S_OK</span></span>|<span data-ttu-id="51023-111">`CreateIoCompletionPort`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="51023-111">`CreateIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="51023-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="51023-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="51023-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="51023-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="51023-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="51023-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="51023-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="51023-115">The call timed out.</span></span>|  
|<span data-ttu-id="51023-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="51023-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="51023-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="51023-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="51023-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="51023-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="51023-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="51023-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="51023-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="51023-120">E_FAIL</span></span>|<span data-ttu-id="51023-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="51023-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="51023-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="51023-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="51023-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="51023-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="51023-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="51023-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="51023-125">記憶體不足，無法配置所要求的資源。</span><span class="sxs-lookup"><span data-stu-id="51023-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51023-126">備註</span><span class="sxs-lookup"><span data-stu-id="51023-126">Remarks</span></span>  
 <span data-ttu-id="51023-127">CLR 會呼叫`CreateIoCompletionPort`方法，以要求主機建立新的 I/O 完成通訊埠。</span><span class="sxs-lookup"><span data-stu-id="51023-127">The CLR calls the `CreateIoCompletionPort` method to request that the host create a new I/O completion port.</span></span> <span data-ttu-id="51023-128">它會透過呼叫這個連接埠繫結 I/O 作業[ihostiocompletionmanager:: Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="51023-128">It binds I/O operations to this port through a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span> <span data-ttu-id="51023-129">主應用程式回報狀態至 CLR 藉由呼叫[iclriocompletionmanager:: Oncomplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)。</span><span class="sxs-lookup"><span data-stu-id="51023-129">The host reports status back to the CLR by calling [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51023-130">需求</span><span class="sxs-lookup"><span data-stu-id="51023-130">Requirements</span></span>  
 <span data-ttu-id="51023-131">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="51023-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51023-132">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="51023-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="51023-133">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="51023-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="51023-134">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51023-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51023-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51023-135">See Also</span></span>  
 [<span data-ttu-id="51023-136">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="51023-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="51023-137">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="51023-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
