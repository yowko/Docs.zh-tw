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
ms.openlocfilehash: 5d57bc742ebcba00f9fbe569a4be27b82a5f8055
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726505"
---
# <a name="iclrtaskgetmemstats-method"></a><span data-ttu-id="bda9b-102">ICLRTask::GetMemStats 方法</span><span class="sxs-lookup"><span data-stu-id="bda9b-102">ICLRTask::GetMemStats Method</span></span>

<span data-ttu-id="bda9b-103">取得與目前 [ICLRTask](iclrtask-interface.md) 實例所代表之工作相關的統計記憶體使用量資訊。</span><span class="sxs-lookup"><span data-stu-id="bda9b-103">Gets statistical memory usage information related to the task that the current [ICLRTask](iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bda9b-104">語法</span><span class="sxs-lookup"><span data-stu-id="bda9b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMemStats (  
    [out] COR_GC_THREAD_STATS *pMemUsage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bda9b-105">參數</span><span class="sxs-lookup"><span data-stu-id="bda9b-105">Parameters</span></span>  

 `pMemUsage`  
 <span data-ttu-id="bda9b-106">擴展 [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) 實例的指標，其中包含工作的記憶體使用量詳細資料，包括配置的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="bda9b-106">[out] A pointer to a [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) instance that contains details about the memory usage of the task, including the number of bytes allocated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bda9b-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="bda9b-107">Return Value</span></span>  
  
|<span data-ttu-id="bda9b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bda9b-108">HRESULT</span></span>|<span data-ttu-id="bda9b-109">描述</span><span class="sxs-lookup"><span data-stu-id="bda9b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bda9b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="bda9b-110">S_OK</span></span>|<span data-ttu-id="bda9b-111">`GetMemStats` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="bda9b-111">`GetMemStats` returned successfully.</span></span>|  
|<span data-ttu-id="bda9b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bda9b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bda9b-113">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="bda9b-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bda9b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bda9b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bda9b-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="bda9b-115">The call timed out.</span></span>|  
|<span data-ttu-id="bda9b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bda9b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bda9b-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="bda9b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bda9b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bda9b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bda9b-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="bda9b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bda9b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bda9b-120">E_FAIL</span></span>|<span data-ttu-id="bda9b-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="bda9b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bda9b-122">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="bda9b-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bda9b-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="bda9b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bda9b-124">需求</span><span class="sxs-lookup"><span data-stu-id="bda9b-124">Requirements</span></span>  

 <span data-ttu-id="bda9b-125">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bda9b-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bda9b-126">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="bda9b-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bda9b-127">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="bda9b-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bda9b-128">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bda9b-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bda9b-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bda9b-129">See also</span></span>

- [<span data-ttu-id="bda9b-130">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="bda9b-130">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="bda9b-131">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="bda9b-131">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="bda9b-132">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="bda9b-132">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="bda9b-133">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="bda9b-133">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
