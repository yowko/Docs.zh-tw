---
title: ICLRTask::RudeAbort 方法
ms.date: 03/30/2017
api_name:
- ICLRTask.RudeAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::RudeAbort
helpviewer_keywords:
- RudeAbort method, ICLRTask interface [.NET Framework hosting]
- ICLRTask::RudeAbort method [.NET Framework hosting]
ms.assetid: b5785468-fcd7-4cc3-8a5d-8796337b53fc
topic_type:
- apiref
ms.openlocfilehash: 5d6e19fe307373c2920fd60b04bff482b238c5c4
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762951"
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="1e9c1-102">ICLRTask::RudeAbort 方法</span><span class="sxs-lookup"><span data-stu-id="1e9c1-102">ICLRTask::RudeAbort Method</span></span>
<span data-ttu-id="1e9c1-103">指示 common language runtime （CLR）立即且無條件地中止目前[ICLRTask 介面](iclrtask-interface.md)實例所代表的工作。</span><span class="sxs-lookup"><span data-stu-id="1e9c1-103">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e9c1-104">語法</span><span class="sxs-lookup"><span data-stu-id="1e9c1-104">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();
```  
  
## <a name="return-value"></a><span data-ttu-id="1e9c1-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="1e9c1-105">Return Value</span></span>  
  
|<span data-ttu-id="1e9c1-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1e9c1-106">HRESULT</span></span>|<span data-ttu-id="1e9c1-107">Description</span><span class="sxs-lookup"><span data-stu-id="1e9c1-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1e9c1-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="1e9c1-108">S_OK</span></span>|<span data-ttu-id="1e9c1-109">`RudeAbort`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="1e9c1-109">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="1e9c1-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1e9c1-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1e9c1-111">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="1e9c1-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1e9c1-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1e9c1-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1e9c1-113">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="1e9c1-113">The call timed out.</span></span>|  
|<span data-ttu-id="1e9c1-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1e9c1-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1e9c1-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="1e9c1-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1e9c1-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1e9c1-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1e9c1-117">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="1e9c1-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1e9c1-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1e9c1-118">E_FAIL</span></span>|<span data-ttu-id="1e9c1-119">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="1e9c1-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1e9c1-120">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="1e9c1-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1e9c1-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="1e9c1-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e9c1-122">備註</span><span class="sxs-lookup"><span data-stu-id="1e9c1-122">Remarks</span></span>  
 <span data-ttu-id="1e9c1-123">主機呼叫 `RudeAbort` 以立即中止工作。</span><span class="sxs-lookup"><span data-stu-id="1e9c1-123">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="1e9c1-124">不保證會執行完成項和例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="1e9c1-124">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e9c1-125">規格需求</span><span class="sxs-lookup"><span data-stu-id="1e9c1-125">Requirements</span></span>  
 <span data-ttu-id="1e9c1-126">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1e9c1-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e9c1-127">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="1e9c1-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1e9c1-128">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1e9c1-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1e9c1-129">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e9c1-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e9c1-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e9c1-130">See also</span></span>

- [<span data-ttu-id="1e9c1-131">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="1e9c1-131">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="1e9c1-132">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="1e9c1-132">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="1e9c1-133">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="1e9c1-133">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="1e9c1-134">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="1e9c1-134">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
