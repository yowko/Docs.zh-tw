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
ms.openlocfilehash: e41fcf2f03b024c1b4ae0032c0ff025d6e2aa1c3
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842500"
---
# <a name="ihosttaskgetpriority-method"></a><span data-ttu-id="107b5-102">IHostTask::GetPriority 方法</span><span class="sxs-lookup"><span data-stu-id="107b5-102">IHostTask::GetPriority Method</span></span>
<span data-ttu-id="107b5-103">取得目前[IHostTask](ihosttask-interface.md)實例所代表之工作的執行緒優先權層級。</span><span class="sxs-lookup"><span data-stu-id="107b5-103">Gets the thread priority level of the task represented by the current [IHostTask](ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="107b5-104">語法</span><span class="sxs-lookup"><span data-stu-id="107b5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPriority (  
    [out] int *pPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="107b5-105">參數</span><span class="sxs-lookup"><span data-stu-id="107b5-105">Parameters</span></span>  
 `pPriority`  
 <span data-ttu-id="107b5-106">脫銷整數的指標，表示目前實例所代表之工作的執行緒優先權層級 `IHostTask` 。</span><span class="sxs-lookup"><span data-stu-id="107b5-106">[out] A pointer to an integer that indicates the thread priority level of the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="107b5-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="107b5-107">Return Value</span></span>  
  
|<span data-ttu-id="107b5-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="107b5-108">HRESULT</span></span>|<span data-ttu-id="107b5-109">描述</span><span class="sxs-lookup"><span data-stu-id="107b5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="107b5-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="107b5-110">S_OK</span></span>|<span data-ttu-id="107b5-111">`GetPriority`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="107b5-111">`GetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="107b5-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="107b5-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="107b5-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="107b5-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="107b5-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="107b5-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="107b5-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="107b5-115">The call timed out.</span></span>|  
|<span data-ttu-id="107b5-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="107b5-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="107b5-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="107b5-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="107b5-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="107b5-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="107b5-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="107b5-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="107b5-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="107b5-120">E_FAIL</span></span>|<span data-ttu-id="107b5-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="107b5-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="107b5-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="107b5-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="107b5-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="107b5-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="107b5-124">備註</span><span class="sxs-lookup"><span data-stu-id="107b5-124">Remarks</span></span>  
 <span data-ttu-id="107b5-125">執行緒優先權層級的值是由 Win32 `SetThreadPriority` 函數所定義。</span><span class="sxs-lookup"><span data-stu-id="107b5-125">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="107b5-126">規格需求</span><span class="sxs-lookup"><span data-stu-id="107b5-126">Requirements</span></span>  
 <span data-ttu-id="107b5-127">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="107b5-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="107b5-128">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="107b5-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="107b5-129">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="107b5-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="107b5-130">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="107b5-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="107b5-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="107b5-131">See also</span></span>

- [<span data-ttu-id="107b5-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="107b5-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="107b5-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="107b5-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="107b5-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="107b5-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="107b5-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="107b5-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
