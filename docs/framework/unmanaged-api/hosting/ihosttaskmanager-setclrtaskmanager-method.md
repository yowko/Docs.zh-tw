---
title: IHostTaskManager::SetCLRTaskManager 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetCLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetCLRTaskManager
helpviewer_keywords:
- IHostTaskManager::SetCLRTaskManager method [.NET Framework hosting]
- SetCLRTaskManager method [.NET Framework hosting]
ms.assetid: ec90ee83-bd4b-408b-9274-62a923ab86a1
topic_type:
- apiref
ms.openlocfilehash: c674cc43065bf8ea102bec1c5134757380454913
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141236"
---
# <a name="ihosttaskmanagersetclrtaskmanager-method"></a><span data-ttu-id="6929e-102">IHostTaskManager::SetCLRTaskManager 方法</span><span class="sxs-lookup"><span data-stu-id="6929e-102">IHostTaskManager::SetCLRTaskManager Method</span></span>
<span data-ttu-id="6929e-103">提供具有由 common language runtime （CLR）所執行之[ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)實例介面指標的主機。</span><span class="sxs-lookup"><span data-stu-id="6929e-103">Provides the host with an interface pointer to an [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6929e-104">語法</span><span class="sxs-lookup"><span data-stu-id="6929e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRTaskManager (  
    [in] ICLRTaskManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6929e-105">參數</span><span class="sxs-lookup"><span data-stu-id="6929e-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="6929e-106">在通用語言執行平臺所實 `ICLRTaskManager` 實例的指標。</span><span class="sxs-lookup"><span data-stu-id="6929e-106">[in] A pointer to an `ICLRTaskManager` instance implemented by the common language runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6929e-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="6929e-107">Return Value</span></span>  
  
|<span data-ttu-id="6929e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6929e-108">HRESULT</span></span>|<span data-ttu-id="6929e-109">描述</span><span class="sxs-lookup"><span data-stu-id="6929e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6929e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6929e-110">S_OK</span></span>|<span data-ttu-id="6929e-111">已成功傳回 `SetCLRTaskManager`。</span><span class="sxs-lookup"><span data-stu-id="6929e-111">`SetCLRTaskManager` returned successfully.</span></span>|  
|<span data-ttu-id="6929e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6929e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6929e-113">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="6929e-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6929e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6929e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6929e-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="6929e-115">The call timed out.</span></span>|  
|<span data-ttu-id="6929e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6929e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6929e-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="6929e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6929e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6929e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6929e-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="6929e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6929e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6929e-120">E_FAIL</span></span>|<span data-ttu-id="6929e-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="6929e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6929e-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="6929e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6929e-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="6929e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6929e-124">備註</span><span class="sxs-lookup"><span data-stu-id="6929e-124">Remarks</span></span>  
 <span data-ttu-id="6929e-125">執行時間會呼叫 `SetCLRTaskManager`，以提供具有 `ICLRTaskManager` 實例之介面指標的主機。</span><span class="sxs-lookup"><span data-stu-id="6929e-125">The runtime calls `SetCLRTaskManager` to provide the host with an interface pointer to an `ICLRTaskManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6929e-126">需求</span><span class="sxs-lookup"><span data-stu-id="6929e-126">Requirements</span></span>  
 <span data-ttu-id="6929e-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6929e-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6929e-128">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="6929e-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6929e-129">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6929e-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6929e-130">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6929e-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6929e-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="6929e-131">See also</span></span>

- [<span data-ttu-id="6929e-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="6929e-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="6929e-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="6929e-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="6929e-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="6929e-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="6929e-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="6929e-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
