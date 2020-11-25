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
ms.openlocfilehash: 0c74e073d55ab7dc98620052a0cfd68c294f7a1c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724269"
---
# <a name="ihostiocompletionmanagercreateiocompletionport-method"></a><span data-ttu-id="a4890-102">IHostIoCompletionManager::CreateIoCompletionPort 方法</span><span class="sxs-lookup"><span data-stu-id="a4890-102">IHostIoCompletionManager::CreateIoCompletionPort Method</span></span>

<span data-ttu-id="a4890-103">要求主機建立新的 i/o 完成通訊埠。</span><span class="sxs-lookup"><span data-stu-id="a4890-103">Requests that the host create a new I/O completion port.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4890-104">語法</span><span class="sxs-lookup"><span data-stu-id="a4890-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateIoCompletionPort (  
    [out] HANDLE *phPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4890-105">參數</span><span class="sxs-lookup"><span data-stu-id="a4890-105">Parameters</span></span>  

 `phPort`  
 <span data-ttu-id="a4890-106">擴展新建立的 i/o 完成埠之控制碼的指標，如果無法建立埠，則為 0 (零) 。</span><span class="sxs-lookup"><span data-stu-id="a4890-106">[out] A pointer to a handle to the newly created I/O completion port, or 0 (zero), if the port could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4890-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="a4890-107">Return Value</span></span>  
  
|<span data-ttu-id="a4890-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a4890-108">HRESULT</span></span>|<span data-ttu-id="a4890-109">描述</span><span class="sxs-lookup"><span data-stu-id="a4890-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a4890-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a4890-110">S_OK</span></span>|<span data-ttu-id="a4890-111">`CreateIoCompletionPort` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="a4890-111">`CreateIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="a4890-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a4890-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a4890-113">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="a4890-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a4890-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a4890-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a4890-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="a4890-115">The call timed out.</span></span>|  
|<span data-ttu-id="a4890-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a4890-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a4890-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="a4890-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a4890-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a4890-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a4890-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="a4890-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a4890-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a4890-120">E_FAIL</span></span>|<span data-ttu-id="a4890-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="a4890-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a4890-122">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="a4890-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a4890-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="a4890-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a4890-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="a4890-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="a4890-125">可用的記憶體不足，無法配置要求的資源。</span><span class="sxs-lookup"><span data-stu-id="a4890-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4890-126">備註</span><span class="sxs-lookup"><span data-stu-id="a4890-126">Remarks</span></span>  

 <span data-ttu-id="a4890-127">CLR `CreateIoCompletionPort` 會呼叫方法來要求主機建立新的 i/o 完成通訊埠。</span><span class="sxs-lookup"><span data-stu-id="a4890-127">The CLR calls the `CreateIoCompletionPort` method to request that the host create a new I/O completion port.</span></span> <span data-ttu-id="a4890-128">它會透過呼叫 [IHostIoCompletionManager：： Bind](ihostiocompletionmanager-bind-method.md) 方法，將 i/o 作業系結至此埠。</span><span class="sxs-lookup"><span data-stu-id="a4890-128">It binds I/O operations to this port through a call to the [IHostIoCompletionManager::Bind](ihostiocompletionmanager-bind-method.md) method.</span></span> <span data-ttu-id="a4890-129">主機會藉由呼叫 [ICLRIoCompletionManager：： OnComplete](iclriocompletionmanager-oncomplete-method.md)，將狀態報表回 CLR。</span><span class="sxs-lookup"><span data-stu-id="a4890-129">The host reports status back to the CLR by calling [ICLRIoCompletionManager::OnComplete](iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4890-130">需求</span><span class="sxs-lookup"><span data-stu-id="a4890-130">Requirements</span></span>  

 <span data-ttu-id="a4890-131">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a4890-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4890-132">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a4890-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a4890-133">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="a4890-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a4890-134">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4890-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4890-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4890-135">See also</span></span>

- [<span data-ttu-id="a4890-136">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="a4890-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="a4890-137">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="a4890-137">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
