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
ms.openlocfilehash: a45f8ab6372776bece09e408bc9887bfaddb0955
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727363"
---
# <a name="ihostiocompletionmanagercloseiocompletionport-method"></a><span data-ttu-id="c02d2-102">IHostIoCompletionManager::CloseIoCompletionPort 方法</span><span class="sxs-lookup"><span data-stu-id="c02d2-102">IHostIoCompletionManager::CloseIoCompletionPort Method</span></span>

<span data-ttu-id="c02d2-103">要求主機關閉透過先前呼叫 [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md)開啟的埠。</span><span class="sxs-lookup"><span data-stu-id="c02d2-103">Requests that the host close a port that was opened through an earlier call to [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c02d2-104">語法</span><span class="sxs-lookup"><span data-stu-id="c02d2-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseIoCompletionPort (  
    [in] HANDLE hPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c02d2-105">參數</span><span class="sxs-lookup"><span data-stu-id="c02d2-105">Parameters</span></span>  

 `hPort`  
 <span data-ttu-id="c02d2-106">在要關閉之埠的控制碼。</span><span class="sxs-lookup"><span data-stu-id="c02d2-106">[in] The handle of the port to close.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c02d2-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="c02d2-107">Return Value</span></span>  
  
|<span data-ttu-id="c02d2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c02d2-108">HRESULT</span></span>|<span data-ttu-id="c02d2-109">描述</span><span class="sxs-lookup"><span data-stu-id="c02d2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c02d2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c02d2-110">S_OK</span></span>|<span data-ttu-id="c02d2-111">`CloseIoCompletionPort` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="c02d2-111">`CloseIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="c02d2-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c02d2-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c02d2-113">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="c02d2-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c02d2-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c02d2-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c02d2-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="c02d2-115">The call timed out.</span></span>|  
|<span data-ttu-id="c02d2-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c02d2-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c02d2-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="c02d2-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c02d2-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c02d2-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c02d2-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="c02d2-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c02d2-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c02d2-120">E_FAIL</span></span>|<span data-ttu-id="c02d2-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="c02d2-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c02d2-122">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="c02d2-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c02d2-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="c02d2-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c02d2-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c02d2-124">E_INVALIDARG</span></span>|<span data-ttu-id="c02d2-125">傳遞的埠控制碼無效。</span><span class="sxs-lookup"><span data-stu-id="c02d2-125">An invalid port handle was passed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c02d2-126">備註</span><span class="sxs-lookup"><span data-stu-id="c02d2-126">Remarks</span></span>  

 <span data-ttu-id="c02d2-127">`hPort` 必須是先前呼叫所建立之埠的控制碼 `CreateIoCompletionPort` 。</span><span class="sxs-lookup"><span data-stu-id="c02d2-127">`hPort` must be a handle to a port that was created by an earlier call to `CreateIoCompletionPort`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c02d2-128">需求</span><span class="sxs-lookup"><span data-stu-id="c02d2-128">Requirements</span></span>  

 <span data-ttu-id="c02d2-129">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c02d2-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c02d2-130">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="c02d2-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c02d2-131">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="c02d2-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c02d2-132">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c02d2-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c02d2-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c02d2-133">See also</span></span>

- [<span data-ttu-id="c02d2-134">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="c02d2-134">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="c02d2-135">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="c02d2-135">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
