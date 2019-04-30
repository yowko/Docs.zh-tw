---
title: IHostIoCompletionManager::Bind 方法
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.Bind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::Bind
helpviewer_keywords:
- IHostIoCompletionManager::Bind method [.NET Framework hosting]
- Bind method [.NET Framework hosting]
ms.assetid: acd74cb5-7e22-4a07-83c3-82288e1abd9f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3fa87026e0d4c93da782be15bef98afa9a0e4dfd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984356"
---
# <a name="ihostiocompletionmanagerbind-method"></a><span data-ttu-id="d3f78-102">IHostIoCompletionManager::Bind 方法</span><span class="sxs-lookup"><span data-stu-id="d3f78-102">IHostIoCompletionManager::Bind Method</span></span>
<span data-ttu-id="d3f78-103">將指定的控制代碼繫結至已經由先前呼叫建立 I/O 完成通訊埠[CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)。</span><span class="sxs-lookup"><span data-stu-id="d3f78-103">Binds the specified handle to an I/O completion port that has been created by an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3f78-104">語法</span><span class="sxs-lookup"><span data-stu-id="d3f78-104">Syntax</span></span>  
  
```  
HRESULT Bind (  
    [in] HANDLE hPort,  
    [in] HANDLE hHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3f78-105">參數</span><span class="sxs-lookup"><span data-stu-id="d3f78-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="d3f78-106">[in]I/O 完成連接埠要繫結至`hHandle`。</span><span class="sxs-lookup"><span data-stu-id="d3f78-106">[in] The I/O completion port to which to bind `hHandle`.</span></span> <span data-ttu-id="d3f78-107">如果值`hPort`為 null，`hHandle`繫結至預設 I/O 完成連接埠。</span><span class="sxs-lookup"><span data-stu-id="d3f78-107">If the value of `hPort` is null, `hHandle` is bound to the default I/O completion port.</span></span>  
  
 `hHandle`  
 <span data-ttu-id="d3f78-108">[in]要繫結作業系統控制代碼`hPort`。</span><span class="sxs-lookup"><span data-stu-id="d3f78-108">[in] The operating system handle to bind to `hPort`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d3f78-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="d3f78-109">Return Value</span></span>  
  
|<span data-ttu-id="d3f78-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d3f78-110">HRESULT</span></span>|<span data-ttu-id="d3f78-111">描述</span><span class="sxs-lookup"><span data-stu-id="d3f78-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d3f78-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="d3f78-112">S_OK</span></span>|<span data-ttu-id="d3f78-113">`Bind` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="d3f78-113">`Bind` returned successfully.</span></span>|  
|<span data-ttu-id="d3f78-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d3f78-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d3f78-115">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="d3f78-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d3f78-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d3f78-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d3f78-117">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="d3f78-117">The call timed out.</span></span>|  
|<span data-ttu-id="d3f78-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d3f78-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d3f78-119">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="d3f78-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d3f78-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d3f78-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d3f78-121">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="d3f78-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d3f78-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d3f78-122">E_FAIL</span></span>|<span data-ttu-id="d3f78-123">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="d3f78-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d3f78-124">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="d3f78-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d3f78-125">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="d3f78-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3f78-126">備註</span><span class="sxs-lookup"><span data-stu-id="d3f78-126">Remarks</span></span>  
 <span data-ttu-id="d3f78-127">I/O 完成連接埠由使用呼叫`CreateIoCompletionPort`。</span><span class="sxs-lookup"><span data-stu-id="d3f78-127">An I/O completion port is created by using a call to `CreateIoCompletionPort`.</span></span> <span data-ttu-id="d3f78-128">CLR 會呼叫`Bind`繫結到該連接埠的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="d3f78-128">The CLR calls `Bind` to bind a handle to that port.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3f78-129">I/O 要求完成時，主機必須呼叫[iclriocompletionmanager:: Oncomplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="d3f78-129">When an I/O request completes, the host must call the [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3f78-130">需求</span><span class="sxs-lookup"><span data-stu-id="d3f78-130">Requirements</span></span>  
 <span data-ttu-id="d3f78-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d3f78-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3f78-132">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d3f78-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d3f78-133">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d3f78-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d3f78-134">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3f78-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3f78-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3f78-135">See also</span></span>

- [<span data-ttu-id="d3f78-136">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="d3f78-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
