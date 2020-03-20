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
ms.openlocfilehash: aacf9de36dc39b63ed36b672e31f40704413d608
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176327"
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="f0b4e-102">ICLRTask::RudeAbort 方法</span><span class="sxs-lookup"><span data-stu-id="f0b4e-102">ICLRTask::RudeAbort Method</span></span>
<span data-ttu-id="f0b4e-103">指示通用語言運行時 （CLR） 立即無條件中止由當前[ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)實例表示的任務。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-103">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0b4e-104">語法</span><span class="sxs-lookup"><span data-stu-id="f0b4e-104">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();
```  
  
## <a name="return-value"></a><span data-ttu-id="f0b4e-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="f0b4e-105">Return Value</span></span>  
  
|<span data-ttu-id="f0b4e-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f0b4e-106">HRESULT</span></span>|<span data-ttu-id="f0b4e-107">描述</span><span class="sxs-lookup"><span data-stu-id="f0b4e-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f0b4e-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="f0b4e-108">S_OK</span></span>|<span data-ttu-id="f0b4e-109">`RudeAbort`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-109">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="f0b4e-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f0b4e-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f0b4e-111">CLR 尚未載入到進程中，或者 CLR 處於無法成功運行託管代碼或成功處理調用的狀態。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f0b4e-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f0b4e-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f0b4e-113">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-113">The call timed out.</span></span>|  
|<span data-ttu-id="f0b4e-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f0b4e-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f0b4e-115">調用方不擁有鎖。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f0b4e-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f0b4e-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f0b4e-117">當阻塞的執行緒或光纖等待事件時，事件已被取消。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f0b4e-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f0b4e-118">E_FAIL</span></span>|<span data-ttu-id="f0b4e-119">發生了未知的災難性故障。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f0b4e-120">當方法返回E_FAIL時，CLR 在進程中不再可用。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f0b4e-121">對託管方法的後續調用返回HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0b4e-122">備註</span><span class="sxs-lookup"><span data-stu-id="f0b4e-122">Remarks</span></span>  
 <span data-ttu-id="f0b4e-123">主機調用`RudeAbort`以立即中止任務。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-123">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="f0b4e-124">不保證執行終結者和異常處理常式。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-124">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0b4e-125">需求</span><span class="sxs-lookup"><span data-stu-id="f0b4e-125">Requirements</span></span>  
 <span data-ttu-id="f0b4e-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0b4e-127">**標題：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f0b4e-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f0b4e-128">**庫：** 作為資源包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="f0b4e-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f0b4e-129">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0b4e-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0b4e-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0b4e-130">See also</span></span>

- [<span data-ttu-id="f0b4e-131">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="f0b4e-131">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="f0b4e-132">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="f0b4e-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="f0b4e-133">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="f0b4e-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="f0b4e-134">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="f0b4e-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
