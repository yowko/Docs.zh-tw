---
title: ICLRTask::ExitTask 方法
ms.date: 03/30/2017
api_name:
- ICLRTask.ExitTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::ExitTask
helpviewer_keywords:
- ExitTask method [.NET Framework hosting]
- ICLRTask::ExitTask method [.NET Framework hosting]
ms.assetid: 746c85a6-4b33-4f72-a2e9-379fdf2e96af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 81afc2aa738c719456091c3f28f3ca33682776e4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759017"
---
# <a name="iclrtaskexittask-method"></a><span data-ttu-id="d4feb-102">ICLRTask::ExitTask 方法</span><span class="sxs-lookup"><span data-stu-id="d4feb-102">ICLRTask::ExitTask Method</span></span>
<span data-ttu-id="d4feb-103">會告知 common language runtime (CLR)，代表目前的工作[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)執行個體即將結束，並會嘗試依正常程序關閉工作。</span><span class="sxs-lookup"><span data-stu-id="d4feb-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance is ending, and attempts to shut the task down gracefully.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4feb-104">語法</span><span class="sxs-lookup"><span data-stu-id="d4feb-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d4feb-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="d4feb-105">Return Value</span></span>  
  
|<span data-ttu-id="d4feb-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d4feb-106">HRESULT</span></span>|<span data-ttu-id="d4feb-107">描述</span><span class="sxs-lookup"><span data-stu-id="d4feb-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d4feb-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="d4feb-108">S_OK</span></span>|<span data-ttu-id="d4feb-109">`ExitTask` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="d4feb-109">`ExitTask` returned successfully.</span></span>|  
|<span data-ttu-id="d4feb-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d4feb-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d4feb-111">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="d4feb-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d4feb-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d4feb-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d4feb-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="d4feb-113">The call timed out.</span></span>|  
|<span data-ttu-id="d4feb-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d4feb-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d4feb-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="d4feb-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d4feb-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d4feb-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d4feb-117">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="d4feb-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d4feb-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d4feb-118">E_FAIL</span></span>|<span data-ttu-id="d4feb-119">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="d4feb-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d4feb-120">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="d4feb-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d4feb-121">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="d4feb-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4feb-122">備註</span><span class="sxs-lookup"><span data-stu-id="d4feb-122">Remarks</span></span>  
 <span data-ttu-id="d4feb-123">`ExitTask` 嘗試正常關機狀態的一項工作，類似於從 unmanaged 型別程式庫卸離執行緒的方式。</span><span class="sxs-lookup"><span data-stu-id="d4feb-123">`ExitTask` attempts a clean shutdown of a task, in a manner analogous to detaching a thread from an unmanaged type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4feb-124">需求</span><span class="sxs-lookup"><span data-stu-id="d4feb-124">Requirements</span></span>  
 <span data-ttu-id="d4feb-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d4feb-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4feb-126">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d4feb-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d4feb-127">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d4feb-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d4feb-128">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4feb-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4feb-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4feb-129">See also</span></span>

- [<span data-ttu-id="d4feb-130">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="d4feb-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="d4feb-131">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="d4feb-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="d4feb-132">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="d4feb-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="d4feb-133">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="d4feb-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
