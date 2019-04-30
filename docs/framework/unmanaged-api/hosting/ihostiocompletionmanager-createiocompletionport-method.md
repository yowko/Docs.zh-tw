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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cf7978af4081b84a361e0a96a6c9da7180cb217
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61951719"
---
# <a name="ihostiocompletionmanagercreateiocompletionport-method"></a><span data-ttu-id="cd66e-102">IHostIoCompletionManager::CreateIoCompletionPort 方法</span><span class="sxs-lookup"><span data-stu-id="cd66e-102">IHostIoCompletionManager::CreateIoCompletionPort Method</span></span>
<span data-ttu-id="cd66e-103">主應用程式建立新的 I/O 完成連接埠的要求。</span><span class="sxs-lookup"><span data-stu-id="cd66e-103">Requests that the host create a new I/O completion port.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd66e-104">語法</span><span class="sxs-lookup"><span data-stu-id="cd66e-104">Syntax</span></span>  
  
```  
HRESULT CreateIoCompletionPort (  
    [out] HANDLE *phPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd66e-105">參數</span><span class="sxs-lookup"><span data-stu-id="cd66e-105">Parameters</span></span>  
 `phPort`  
 <span data-ttu-id="cd66e-106">[out]新建立的 I/O 完成通訊埠或 0 （零），如果無法建立連接埠的控制代碼指標。</span><span class="sxs-lookup"><span data-stu-id="cd66e-106">[out] A pointer to a handle to the newly created I/O completion port, or 0 (zero), if the port could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cd66e-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="cd66e-107">Return Value</span></span>  
  
|<span data-ttu-id="cd66e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cd66e-108">HRESULT</span></span>|<span data-ttu-id="cd66e-109">描述</span><span class="sxs-lookup"><span data-stu-id="cd66e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cd66e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="cd66e-110">S_OK</span></span>|<span data-ttu-id="cd66e-111">`CreateIoCompletionPort` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="cd66e-111">`CreateIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="cd66e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cd66e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cd66e-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="cd66e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cd66e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cd66e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cd66e-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="cd66e-115">The call timed out.</span></span>|  
|<span data-ttu-id="cd66e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cd66e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cd66e-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="cd66e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cd66e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cd66e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cd66e-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="cd66e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cd66e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cd66e-120">E_FAIL</span></span>|<span data-ttu-id="cd66e-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="cd66e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cd66e-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="cd66e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cd66e-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="cd66e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="cd66e-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="cd66e-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="cd66e-125">記憶體不足，無法配置所要求的資源。</span><span class="sxs-lookup"><span data-stu-id="cd66e-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd66e-126">備註</span><span class="sxs-lookup"><span data-stu-id="cd66e-126">Remarks</span></span>  
 <span data-ttu-id="cd66e-127">CLR 會呼叫`CreateIoCompletionPort`方法，以要求主機建立新的 I/O 完成連接埠。</span><span class="sxs-lookup"><span data-stu-id="cd66e-127">The CLR calls the `CreateIoCompletionPort` method to request that the host create a new I/O completion port.</span></span> <span data-ttu-id="cd66e-128">它會在將 I/O 作業透過呼叫此連接埠繫結[ihostiocompletionmanager:: Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="cd66e-128">It binds I/O operations to this port through a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span> <span data-ttu-id="cd66e-129">主應用程式回報狀態至 CLR 藉由呼叫[iclriocompletionmanager:: Oncomplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)。</span><span class="sxs-lookup"><span data-stu-id="cd66e-129">The host reports status back to the CLR by calling [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd66e-130">需求</span><span class="sxs-lookup"><span data-stu-id="cd66e-130">Requirements</span></span>  
 <span data-ttu-id="cd66e-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cd66e-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd66e-132">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cd66e-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cd66e-133">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="cd66e-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cd66e-134">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd66e-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd66e-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd66e-135">See also</span></span>

- [<span data-ttu-id="cd66e-136">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="cd66e-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="cd66e-137">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="cd66e-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
