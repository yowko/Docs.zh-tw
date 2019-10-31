---
title: ICLRTask::GetMemStats 方法
ms.date: 03/30/2017
api_name:
- ICLRTask.GetMemStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::GetMemStats
helpviewer_keywords:
- ICLRTask::GetMemStats method [.NET Framework hosting]
- GetMemStats method [.NET Framework hosting]
ms.assetid: c9e07657-1682-4c30-a336-f8658ff1a125
topic_type:
- apiref
ms.openlocfilehash: 0bf8b6f393806e590be8f97dbfe2d01d5746c339
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139699"
---
# <a name="iclrtaskgetmemstats-method"></a><span data-ttu-id="343c9-102">ICLRTask::GetMemStats 方法</span><span class="sxs-lookup"><span data-stu-id="343c9-102">ICLRTask::GetMemStats Method</span></span>
<span data-ttu-id="343c9-103">取得與目前[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)實例所代表之工作相關的統計記憶體使用量資訊。</span><span class="sxs-lookup"><span data-stu-id="343c9-103">Gets statistical memory usage information related to the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="343c9-104">語法</span><span class="sxs-lookup"><span data-stu-id="343c9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMemStats (  
    [out] COR_GC_THREAD_STATS *pMemUsage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="343c9-105">參數</span><span class="sxs-lookup"><span data-stu-id="343c9-105">Parameters</span></span>  
 `pMemUsage`  
 <span data-ttu-id="343c9-106">脫銷[COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md)實例的指標，其中包含工作之記憶體使用量的詳細資料，包括已配置的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="343c9-106">[out] A pointer to a [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) instance that contains details about the memory usage of the task, including the number of bytes allocated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="343c9-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="343c9-107">Return Value</span></span>  
  
|<span data-ttu-id="343c9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="343c9-108">HRESULT</span></span>|<span data-ttu-id="343c9-109">描述</span><span class="sxs-lookup"><span data-stu-id="343c9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="343c9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="343c9-110">S_OK</span></span>|<span data-ttu-id="343c9-111">已成功傳回 `GetMemStats`。</span><span class="sxs-lookup"><span data-stu-id="343c9-111">`GetMemStats` returned successfully.</span></span>|  
|<span data-ttu-id="343c9-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="343c9-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="343c9-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="343c9-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="343c9-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="343c9-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="343c9-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="343c9-115">The call timed out.</span></span>|  
|<span data-ttu-id="343c9-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="343c9-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="343c9-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="343c9-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="343c9-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="343c9-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="343c9-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="343c9-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="343c9-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="343c9-120">E_FAIL</span></span>|<span data-ttu-id="343c9-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="343c9-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="343c9-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="343c9-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="343c9-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="343c9-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="343c9-124">需求</span><span class="sxs-lookup"><span data-stu-id="343c9-124">Requirements</span></span>  
 <span data-ttu-id="343c9-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="343c9-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="343c9-126">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="343c9-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="343c9-127">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="343c9-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="343c9-128">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="343c9-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="343c9-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="343c9-129">See also</span></span>

- [<span data-ttu-id="343c9-130">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="343c9-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="343c9-131">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="343c9-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="343c9-132">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="343c9-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="343c9-133">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="343c9-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
