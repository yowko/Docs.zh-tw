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
ms.openlocfilehash: 69e3ecfc82985d52bd5b14e9faf2566e395b622b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124648"
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="49891-102">ICLRTask::RudeAbort 方法</span><span class="sxs-lookup"><span data-stu-id="49891-102">ICLRTask::RudeAbort Method</span></span>
<span data-ttu-id="49891-103">指示 common language runtime （CLR）立即且無條件地中止目前[ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)實例所代表的工作。</span><span class="sxs-lookup"><span data-stu-id="49891-103">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49891-104">語法</span><span class="sxs-lookup"><span data-stu-id="49891-104">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();   
```  
  
## <a name="return-value"></a><span data-ttu-id="49891-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="49891-105">Return Value</span></span>  
  
|<span data-ttu-id="49891-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="49891-106">HRESULT</span></span>|<span data-ttu-id="49891-107">描述</span><span class="sxs-lookup"><span data-stu-id="49891-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="49891-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="49891-108">S_OK</span></span>|<span data-ttu-id="49891-109">已成功傳回 `RudeAbort`。</span><span class="sxs-lookup"><span data-stu-id="49891-109">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="49891-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="49891-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="49891-111">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="49891-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="49891-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="49891-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="49891-113">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="49891-113">The call timed out.</span></span>|  
|<span data-ttu-id="49891-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="49891-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="49891-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="49891-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="49891-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="49891-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="49891-117">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="49891-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="49891-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="49891-118">E_FAIL</span></span>|<span data-ttu-id="49891-119">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="49891-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="49891-120">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="49891-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="49891-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="49891-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49891-122">備註</span><span class="sxs-lookup"><span data-stu-id="49891-122">Remarks</span></span>  
 <span data-ttu-id="49891-123">主機會呼叫 `RudeAbort` 以立即中止工作。</span><span class="sxs-lookup"><span data-stu-id="49891-123">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="49891-124">不保證會執行完成項和例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="49891-124">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49891-125">需求</span><span class="sxs-lookup"><span data-stu-id="49891-125">Requirements</span></span>  
 <span data-ttu-id="49891-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="49891-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49891-127">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="49891-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="49891-128">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="49891-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="49891-129">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49891-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49891-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="49891-130">See also</span></span>

- [<span data-ttu-id="49891-131">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="49891-131">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="49891-132">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="49891-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="49891-133">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="49891-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="49891-134">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="49891-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
