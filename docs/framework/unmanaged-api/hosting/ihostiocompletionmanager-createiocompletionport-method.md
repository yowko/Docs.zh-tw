---
title: IHostIoCompletionManager::CreateIoCompletionPort 方法
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.CreateIoCompletionPort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::CreateIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CreateIoCompletionPort method [.NET Framework hosting]
- CreateIoCompletionPort method [.NET Framework hosting]
ms.assetid: 907a2b43-68db-44a7-acac-89e792e7bb3c
topic_type:
- apiref
ms.openlocfilehash: c3fa8aeebe529564c0ecc4a970f586fffc97ee05
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133871"
---
# <a name="ihostiocompletionmanagercreateiocompletionport-method"></a><span data-ttu-id="eb38b-102">IHostIoCompletionManager::CreateIoCompletionPort 方法</span><span class="sxs-lookup"><span data-stu-id="eb38b-102">IHostIoCompletionManager::CreateIoCompletionPort Method</span></span>
<span data-ttu-id="eb38b-103">要求主機建立新的 i/o 完成埠。</span><span class="sxs-lookup"><span data-stu-id="eb38b-103">Requests that the host create a new I/O completion port.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb38b-104">語法</span><span class="sxs-lookup"><span data-stu-id="eb38b-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateIoCompletionPort (  
    [out] HANDLE *phPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb38b-105">參數</span><span class="sxs-lookup"><span data-stu-id="eb38b-105">Parameters</span></span>  
 `phPort`  
 <span data-ttu-id="eb38b-106">脫銷新建立的 i/o 完成埠的控制碼指標，如果無法建立埠，則為0（零）。</span><span class="sxs-lookup"><span data-stu-id="eb38b-106">[out] A pointer to a handle to the newly created I/O completion port, or 0 (zero), if the port could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eb38b-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="eb38b-107">Return Value</span></span>  
  
|<span data-ttu-id="eb38b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="eb38b-108">HRESULT</span></span>|<span data-ttu-id="eb38b-109">描述</span><span class="sxs-lookup"><span data-stu-id="eb38b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eb38b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="eb38b-110">S_OK</span></span>|<span data-ttu-id="eb38b-111">已成功傳回 `CreateIoCompletionPort`。</span><span class="sxs-lookup"><span data-stu-id="eb38b-111">`CreateIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="eb38b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="eb38b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="eb38b-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="eb38b-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="eb38b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="eb38b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="eb38b-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="eb38b-115">The call timed out.</span></span>|  
|<span data-ttu-id="eb38b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="eb38b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="eb38b-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="eb38b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="eb38b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="eb38b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="eb38b-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="eb38b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="eb38b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="eb38b-120">E_FAIL</span></span>|<span data-ttu-id="eb38b-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="eb38b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="eb38b-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="eb38b-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="eb38b-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="eb38b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="eb38b-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="eb38b-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="eb38b-125">沒有足夠的記憶體可用來配置要求的資源。</span><span class="sxs-lookup"><span data-stu-id="eb38b-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb38b-126">備註</span><span class="sxs-lookup"><span data-stu-id="eb38b-126">Remarks</span></span>  
 <span data-ttu-id="eb38b-127">CLR 會呼叫 `CreateIoCompletionPort` 方法，要求主機建立新的 i/o 完成埠。</span><span class="sxs-lookup"><span data-stu-id="eb38b-127">The CLR calls the `CreateIoCompletionPort` method to request that the host create a new I/O completion port.</span></span> <span data-ttu-id="eb38b-128">它會透過呼叫[IHostIoCompletionManager：： Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)方法，將 i/o 作業系結至這個埠。</span><span class="sxs-lookup"><span data-stu-id="eb38b-128">It binds I/O operations to this port through a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span> <span data-ttu-id="eb38b-129">主機會藉由呼叫[ICLRIoCompletionManager：： OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)，將狀態報表回 CLR。</span><span class="sxs-lookup"><span data-stu-id="eb38b-129">The host reports status back to the CLR by calling [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb38b-130">需求</span><span class="sxs-lookup"><span data-stu-id="eb38b-130">Requirements</span></span>  
 <span data-ttu-id="eb38b-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eb38b-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb38b-132">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="eb38b-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eb38b-133">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="eb38b-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eb38b-134">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb38b-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb38b-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="eb38b-135">See also</span></span>

- [<span data-ttu-id="eb38b-136">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="eb38b-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="eb38b-137">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="eb38b-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
