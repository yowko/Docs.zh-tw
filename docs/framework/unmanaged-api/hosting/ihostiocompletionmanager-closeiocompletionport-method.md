---
title: IHostIoCompletionManager::CloseIoCompletionPort 方法
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.CloseIoCompletionPort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort method [.NET Framework hosting]
- CloseIoCompletionPort method [.NET Framework hosting]
ms.assetid: e86ad7be-3758-498a-a972-5522d69dfbb3
topic_type:
- apiref
ms.openlocfilehash: 254254af705f93793b030882e0ac79d0372ca55f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133884"
---
# <a name="ihostiocompletionmanagercloseiocompletionport-method"></a><span data-ttu-id="8894e-102">IHostIoCompletionManager::CloseIoCompletionPort 方法</span><span class="sxs-lookup"><span data-stu-id="8894e-102">IHostIoCompletionManager::CloseIoCompletionPort Method</span></span>
<span data-ttu-id="8894e-103">要求主機關閉透過先前呼叫[CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)所開啟的埠。</span><span class="sxs-lookup"><span data-stu-id="8894e-103">Requests that the host close a port that was opened through an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8894e-104">語法</span><span class="sxs-lookup"><span data-stu-id="8894e-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseIoCompletionPort (  
    [in] HANDLE hPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8894e-105">參數</span><span class="sxs-lookup"><span data-stu-id="8894e-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="8894e-106">在要關閉之埠的控制碼。</span><span class="sxs-lookup"><span data-stu-id="8894e-106">[in] The handle of the port to close.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8894e-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="8894e-107">Return Value</span></span>  
  
|<span data-ttu-id="8894e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8894e-108">HRESULT</span></span>|<span data-ttu-id="8894e-109">描述</span><span class="sxs-lookup"><span data-stu-id="8894e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8894e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8894e-110">S_OK</span></span>|<span data-ttu-id="8894e-111">已成功傳回 `CloseIoCompletionPort`。</span><span class="sxs-lookup"><span data-stu-id="8894e-111">`CloseIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="8894e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8894e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8894e-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="8894e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8894e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8894e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8894e-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="8894e-115">The call timed out.</span></span>|  
|<span data-ttu-id="8894e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8894e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8894e-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="8894e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8894e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8894e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8894e-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="8894e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8894e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8894e-120">E_FAIL</span></span>|<span data-ttu-id="8894e-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="8894e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8894e-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="8894e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8894e-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="8894e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8894e-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8894e-124">E_INVALIDARG</span></span>|<span data-ttu-id="8894e-125">傳遞了不正確埠控制碼。</span><span class="sxs-lookup"><span data-stu-id="8894e-125">An invalid port handle was passed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8894e-126">備註</span><span class="sxs-lookup"><span data-stu-id="8894e-126">Remarks</span></span>  
 <span data-ttu-id="8894e-127">`hPort` 必須是先前呼叫 `CreateIoCompletionPort`所建立之埠的控制碼。</span><span class="sxs-lookup"><span data-stu-id="8894e-127">`hPort` must be a handle to a port that was created by an earlier call to `CreateIoCompletionPort`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8894e-128">需求</span><span class="sxs-lookup"><span data-stu-id="8894e-128">Requirements</span></span>  
 <span data-ttu-id="8894e-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8894e-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8894e-130">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="8894e-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8894e-131">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8894e-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8894e-132">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8894e-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8894e-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="8894e-133">See also</span></span>

- [<span data-ttu-id="8894e-134">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="8894e-134">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="8894e-135">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="8894e-135">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
