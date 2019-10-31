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
ms.openlocfilehash: 84fc99f6a5feb7ec73ee16942ba2794fc082dc89
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133906"
---
# <a name="ihostiocompletionmanagerbind-method"></a><span data-ttu-id="8993d-102">IHostIoCompletionManager::Bind 方法</span><span class="sxs-lookup"><span data-stu-id="8993d-102">IHostIoCompletionManager::Bind Method</span></span>
<span data-ttu-id="8993d-103">將指定的控制碼系結至先前呼叫[CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)所建立的 i/o 完成埠。</span><span class="sxs-lookup"><span data-stu-id="8993d-103">Binds the specified handle to an I/O completion port that has been created by an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8993d-104">語法</span><span class="sxs-lookup"><span data-stu-id="8993d-104">Syntax</span></span>  
  
```cpp  
HRESULT Bind (  
    [in] HANDLE hPort,  
    [in] HANDLE hHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8993d-105">參數</span><span class="sxs-lookup"><span data-stu-id="8993d-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="8993d-106">在要系結 `hHandle`的 i/o 完成埠。</span><span class="sxs-lookup"><span data-stu-id="8993d-106">[in] The I/O completion port to which to bind `hHandle`.</span></span> <span data-ttu-id="8993d-107">如果 `hPort` 的值為 null，`hHandle` 會系結至預設的 i/o 完成埠。</span><span class="sxs-lookup"><span data-stu-id="8993d-107">If the value of `hPort` is null, `hHandle` is bound to the default I/O completion port.</span></span>  
  
 `hHandle`  
 <span data-ttu-id="8993d-108">在要系結至 `hPort`的作業系統控制碼。</span><span class="sxs-lookup"><span data-stu-id="8993d-108">[in] The operating system handle to bind to `hPort`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8993d-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="8993d-109">Return Value</span></span>  
  
|<span data-ttu-id="8993d-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8993d-110">HRESULT</span></span>|<span data-ttu-id="8993d-111">描述</span><span class="sxs-lookup"><span data-stu-id="8993d-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8993d-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="8993d-112">S_OK</span></span>|<span data-ttu-id="8993d-113">已成功傳回 `Bind`。</span><span class="sxs-lookup"><span data-stu-id="8993d-113">`Bind` returned successfully.</span></span>|  
|<span data-ttu-id="8993d-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8993d-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8993d-115">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="8993d-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8993d-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8993d-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8993d-117">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="8993d-117">The call timed out.</span></span>|  
|<span data-ttu-id="8993d-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8993d-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8993d-119">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="8993d-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8993d-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8993d-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8993d-121">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="8993d-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8993d-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8993d-122">E_FAIL</span></span>|<span data-ttu-id="8993d-123">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="8993d-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8993d-124">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="8993d-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8993d-125">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="8993d-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8993d-126">備註</span><span class="sxs-lookup"><span data-stu-id="8993d-126">Remarks</span></span>  
 <span data-ttu-id="8993d-127">I/o 完成通訊埠是使用 `CreateIoCompletionPort`的呼叫所建立。</span><span class="sxs-lookup"><span data-stu-id="8993d-127">An I/O completion port is created by using a call to `CreateIoCompletionPort`.</span></span> <span data-ttu-id="8993d-128">CLR 會呼叫 `Bind` 來系結該埠的控制碼。</span><span class="sxs-lookup"><span data-stu-id="8993d-128">The CLR calls `Bind` to bind a handle to that port.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8993d-129">當 i/o 要求完成時，主機必須呼叫[ICLRIoCompletionManager：： OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="8993d-129">When an I/O request completes, the host must call the [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8993d-130">需求</span><span class="sxs-lookup"><span data-stu-id="8993d-130">Requirements</span></span>  
 <span data-ttu-id="8993d-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8993d-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8993d-132">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="8993d-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8993d-133">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8993d-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8993d-134">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8993d-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8993d-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="8993d-135">See also</span></span>

- [<span data-ttu-id="8993d-136">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="8993d-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
