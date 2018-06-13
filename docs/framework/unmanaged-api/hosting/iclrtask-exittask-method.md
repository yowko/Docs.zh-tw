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
ms.openlocfilehash: 3391ed2be03c965807a1c6cad89579cea4015693
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434560"
---
# <a name="iclrtaskexittask-method"></a><span data-ttu-id="e146c-102">ICLRTask::ExitTask 方法</span><span class="sxs-lookup"><span data-stu-id="e146c-102">ICLRTask::ExitTask Method</span></span>
<span data-ttu-id="e146c-103">會告知 common language runtime (CLR)，代表目前的工作[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)執行個體即將結束，並嘗試依正常程序關閉的工作。</span><span class="sxs-lookup"><span data-stu-id="e146c-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance is ending, and attempts to shut the task down gracefully.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e146c-104">語法</span><span class="sxs-lookup"><span data-stu-id="e146c-104">Syntax</span></span>  
  
```  
HRESULT ExitTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e146c-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="e146c-105">Return Value</span></span>  
  
|<span data-ttu-id="e146c-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e146c-106">HRESULT</span></span>|<span data-ttu-id="e146c-107">描述</span><span class="sxs-lookup"><span data-stu-id="e146c-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e146c-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="e146c-108">S_OK</span></span>|<span data-ttu-id="e146c-109">`ExitTask` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="e146c-109">`ExitTask` returned successfully.</span></span>|  
|<span data-ttu-id="e146c-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e146c-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e146c-111">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="e146c-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e146c-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e146c-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e146c-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="e146c-113">The call timed out.</span></span>|  
|<span data-ttu-id="e146c-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e146c-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e146c-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="e146c-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e146c-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e146c-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e146c-117">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="e146c-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e146c-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e146c-118">E_FAIL</span></span>|<span data-ttu-id="e146c-119">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="e146c-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e146c-120">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="e146c-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e146c-121">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="e146c-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e146c-122">備註</span><span class="sxs-lookup"><span data-stu-id="e146c-122">Remarks</span></span>  
 <span data-ttu-id="e146c-123">`ExitTask` 嘗試正常關機狀態的工作，類似於中斷執行緒從 unmanaged 的類型程式庫的方式。</span><span class="sxs-lookup"><span data-stu-id="e146c-123">`ExitTask` attempts a clean shutdown of a task, in a manner analogous to detaching a thread from an unmanaged type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e146c-124">需求</span><span class="sxs-lookup"><span data-stu-id="e146c-124">Requirements</span></span>  
 <span data-ttu-id="e146c-125">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e146c-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e146c-126">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e146c-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e146c-127">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e146c-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e146c-128">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e146c-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e146c-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e146c-129">See Also</span></span>  
 [<span data-ttu-id="e146c-130">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="e146c-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="e146c-131">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="e146c-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="e146c-132">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="e146c-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="e146c-133">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="e146c-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
