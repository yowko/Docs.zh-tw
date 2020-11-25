---
title: IHostTask::GetPriority 方法
ms.date: 03/30/2017
api_name:
- IHostTask.GetPriority
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::GetPriority
helpviewer_keywords:
- GetPriority method [.NET Framework hosting]
- IHostTask::GetPriority method [.NET Framework hosting]
ms.assetid: 4b463cd6-77c1-4f9a-8518-346ad8fc4b70
topic_type:
- apiref
ms.openlocfilehash: d30dcbe4e7c289c23c5af00e4bdadedc186809b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714766"
---
# <a name="ihosttaskgetpriority-method"></a><span data-ttu-id="ffe70-102">IHostTask::GetPriority 方法</span><span class="sxs-lookup"><span data-stu-id="ffe70-102">IHostTask::GetPriority Method</span></span>

<span data-ttu-id="ffe70-103">取得目前 [IHostTask](ihosttask-interface.md) 實例所代表之工作的執行緒優先權層級。</span><span class="sxs-lookup"><span data-stu-id="ffe70-103">Gets the thread priority level of the task represented by the current [IHostTask](ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffe70-104">語法</span><span class="sxs-lookup"><span data-stu-id="ffe70-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPriority (  
    [out] int *pPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ffe70-105">參數</span><span class="sxs-lookup"><span data-stu-id="ffe70-105">Parameters</span></span>  

 `pPriority`  
 <span data-ttu-id="ffe70-106">擴展整數的指標，指出目前實例所代表之工作的執行緒優先權層級 `IHostTask` 。</span><span class="sxs-lookup"><span data-stu-id="ffe70-106">[out] A pointer to an integer that indicates the thread priority level of the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ffe70-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="ffe70-107">Return Value</span></span>  
  
|<span data-ttu-id="ffe70-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ffe70-108">HRESULT</span></span>|<span data-ttu-id="ffe70-109">描述</span><span class="sxs-lookup"><span data-stu-id="ffe70-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ffe70-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ffe70-110">S_OK</span></span>|<span data-ttu-id="ffe70-111">`GetPriority` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="ffe70-111">`GetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="ffe70-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ffe70-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ffe70-113">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="ffe70-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ffe70-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ffe70-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ffe70-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="ffe70-115">The call timed out.</span></span>|  
|<span data-ttu-id="ffe70-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ffe70-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ffe70-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="ffe70-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ffe70-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ffe70-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ffe70-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="ffe70-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ffe70-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ffe70-120">E_FAIL</span></span>|<span data-ttu-id="ffe70-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="ffe70-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ffe70-122">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="ffe70-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ffe70-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="ffe70-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ffe70-124">備註</span><span class="sxs-lookup"><span data-stu-id="ffe70-124">Remarks</span></span>  

 <span data-ttu-id="ffe70-125">執行緒優先權層級值是由 Win32 `SetThreadPriority` 函式定義。</span><span class="sxs-lookup"><span data-stu-id="ffe70-125">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffe70-126">需求</span><span class="sxs-lookup"><span data-stu-id="ffe70-126">Requirements</span></span>  

 <span data-ttu-id="ffe70-127">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ffe70-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffe70-128">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="ffe70-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ffe70-129">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="ffe70-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ffe70-130">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffe70-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffe70-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ffe70-131">See also</span></span>

- [<span data-ttu-id="ffe70-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="ffe70-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="ffe70-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="ffe70-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="ffe70-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="ffe70-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="ffe70-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="ffe70-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
