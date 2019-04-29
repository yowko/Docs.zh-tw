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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 702992ab4edfea3f0b699efefedb195cd87586ea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789567"
---
# <a name="ihosttaskgetpriority-method"></a><span data-ttu-id="d7edc-102">IHostTask::GetPriority 方法</span><span class="sxs-lookup"><span data-stu-id="d7edc-102">IHostTask::GetPriority Method</span></span>
<span data-ttu-id="d7edc-103">取得表示目前的工作的執行緒優先權層級[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)執行個體。</span><span class="sxs-lookup"><span data-stu-id="d7edc-103">Gets the thread priority level of the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7edc-104">語法</span><span class="sxs-lookup"><span data-stu-id="d7edc-104">Syntax</span></span>  
  
```  
HRESULT GetPriority (  
    [out] int *pPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7edc-105">參數</span><span class="sxs-lookup"><span data-stu-id="d7edc-105">Parameters</span></span>  
 `pPriority`  
 <span data-ttu-id="d7edc-106">[out]整數，表示由目前工作的執行緒優先權層級指標`IHostTask`執行個體。</span><span class="sxs-lookup"><span data-stu-id="d7edc-106">[out] A pointer to an integer that indicates the thread priority level of the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d7edc-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="d7edc-107">Return Value</span></span>  
  
|<span data-ttu-id="d7edc-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d7edc-108">HRESULT</span></span>|<span data-ttu-id="d7edc-109">描述</span><span class="sxs-lookup"><span data-stu-id="d7edc-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d7edc-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d7edc-110">S_OK</span></span>|<span data-ttu-id="d7edc-111">`GetPriority` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="d7edc-111">`GetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="d7edc-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d7edc-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d7edc-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="d7edc-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d7edc-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d7edc-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d7edc-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="d7edc-115">The call timed out.</span></span>|  
|<span data-ttu-id="d7edc-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d7edc-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d7edc-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="d7edc-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d7edc-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d7edc-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d7edc-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="d7edc-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d7edc-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d7edc-120">E_FAIL</span></span>|<span data-ttu-id="d7edc-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="d7edc-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d7edc-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="d7edc-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d7edc-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="d7edc-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7edc-124">備註</span><span class="sxs-lookup"><span data-stu-id="d7edc-124">Remarks</span></span>  
 <span data-ttu-id="d7edc-125">定義 win32 執行緒優先權層級值`SetThreadPriority`函式。</span><span class="sxs-lookup"><span data-stu-id="d7edc-125">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7edc-126">需求</span><span class="sxs-lookup"><span data-stu-id="d7edc-126">Requirements</span></span>  
 <span data-ttu-id="d7edc-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d7edc-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7edc-128">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d7edc-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d7edc-129">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d7edc-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d7edc-130">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7edc-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7edc-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7edc-131">See also</span></span>

- [<span data-ttu-id="d7edc-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="d7edc-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="d7edc-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="d7edc-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="d7edc-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="d7edc-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="d7edc-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="d7edc-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
