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
ms.openlocfilehash: 0d2975d6247cd9ecdb07b564d77518151404c7d0
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762453"
---
# <a name="iclrtaskgetmemstats-method"></a><span data-ttu-id="10ed0-102">ICLRTask::GetMemStats 方法</span><span class="sxs-lookup"><span data-stu-id="10ed0-102">ICLRTask::GetMemStats Method</span></span>
<span data-ttu-id="10ed0-103">取得與目前[ICLRTask](iclrtask-interface.md)實例所代表之工作相關的統計記憶體使用量資訊。</span><span class="sxs-lookup"><span data-stu-id="10ed0-103">Gets statistical memory usage information related to the task that the current [ICLRTask](iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10ed0-104">語法</span><span class="sxs-lookup"><span data-stu-id="10ed0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMemStats (  
    [out] COR_GC_THREAD_STATS *pMemUsage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10ed0-105">參數</span><span class="sxs-lookup"><span data-stu-id="10ed0-105">Parameters</span></span>  
 `pMemUsage`  
 <span data-ttu-id="10ed0-106">脫銷[COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md)實例的指標，其中包含工作之記憶體使用量的詳細資料，包括已配置的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="10ed0-106">[out] A pointer to a [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) instance that contains details about the memory usage of the task, including the number of bytes allocated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="10ed0-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="10ed0-107">Return Value</span></span>  
  
|<span data-ttu-id="10ed0-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="10ed0-108">HRESULT</span></span>|<span data-ttu-id="10ed0-109">Description</span><span class="sxs-lookup"><span data-stu-id="10ed0-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="10ed0-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="10ed0-110">S_OK</span></span>|<span data-ttu-id="10ed0-111">`GetMemStats`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="10ed0-111">`GetMemStats` returned successfully.</span></span>|  
|<span data-ttu-id="10ed0-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="10ed0-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="10ed0-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="10ed0-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="10ed0-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="10ed0-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="10ed0-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="10ed0-115">The call timed out.</span></span>|  
|<span data-ttu-id="10ed0-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="10ed0-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="10ed0-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="10ed0-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="10ed0-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="10ed0-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="10ed0-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="10ed0-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="10ed0-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="10ed0-120">E_FAIL</span></span>|<span data-ttu-id="10ed0-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="10ed0-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="10ed0-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="10ed0-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="10ed0-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="10ed0-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="10ed0-124">規格需求</span><span class="sxs-lookup"><span data-stu-id="10ed0-124">Requirements</span></span>  
 <span data-ttu-id="10ed0-125">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="10ed0-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10ed0-126">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="10ed0-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="10ed0-127">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="10ed0-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="10ed0-128">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10ed0-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10ed0-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10ed0-129">See also</span></span>

- [<span data-ttu-id="10ed0-130">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="10ed0-130">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="10ed0-131">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="10ed0-131">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="10ed0-132">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="10ed0-132">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="10ed0-133">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="10ed0-133">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
