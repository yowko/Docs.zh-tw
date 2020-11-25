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
ms.openlocfilehash: 5231db8de6129ed593e4e0d508b312b7034c01f0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733902"
---
# <a name="ihostiocompletionmanagerbind-method"></a><span data-ttu-id="cc4a4-102">IHostIoCompletionManager::Bind 方法</span><span class="sxs-lookup"><span data-stu-id="cc4a4-102">IHostIoCompletionManager::Bind Method</span></span>

<span data-ttu-id="cc4a4-103">將指定的控制碼系結至先前呼叫 [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md)所建立的 i/o 完成通訊埠。</span><span class="sxs-lookup"><span data-stu-id="cc4a4-103">Binds the specified handle to an I/O completion port that has been created by an earlier call to [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc4a4-104">語法</span><span class="sxs-lookup"><span data-stu-id="cc4a4-104">Syntax</span></span>  
  
```cpp  
HRESULT Bind (  
    [in] HANDLE hPort,  
    [in] HANDLE hHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc4a4-105">參數</span><span class="sxs-lookup"><span data-stu-id="cc4a4-105">Parameters</span></span>  

 `hPort`  
 <span data-ttu-id="cc4a4-106">在要系結的 i/o 完成通訊埠 `hHandle` 。</span><span class="sxs-lookup"><span data-stu-id="cc4a4-106">[in] The I/O completion port to which to bind `hHandle`.</span></span> <span data-ttu-id="cc4a4-107">如果的值 `hPort` 是 null， `hHandle` 就會系結至預設的 i/o 完成通訊埠。</span><span class="sxs-lookup"><span data-stu-id="cc4a4-107">If the value of `hPort` is null, `hHandle` is bound to the default I/O completion port.</span></span>  
  
 `hHandle`  
 <span data-ttu-id="cc4a4-108">在要系結的作業系統控制碼 `hPort` 。</span><span class="sxs-lookup"><span data-stu-id="cc4a4-108">[in] The operating system handle to bind to `hPort`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cc4a4-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="cc4a4-109">Return Value</span></span>  
  
|<span data-ttu-id="cc4a4-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cc4a4-110">HRESULT</span></span>|<span data-ttu-id="cc4a4-111">描述</span><span class="sxs-lookup"><span data-stu-id="cc4a4-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cc4a4-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="cc4a4-112">S_OK</span></span>|<span data-ttu-id="cc4a4-113">`Bind` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="cc4a4-113">`Bind` returned successfully.</span></span>|  
|<span data-ttu-id="cc4a4-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cc4a4-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cc4a4-115">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="cc4a4-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cc4a4-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cc4a4-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cc4a4-117">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="cc4a4-117">The call timed out.</span></span>|  
|<span data-ttu-id="cc4a4-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cc4a4-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cc4a4-119">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="cc4a4-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cc4a4-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cc4a4-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cc4a4-121">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="cc4a4-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cc4a4-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cc4a4-122">E_FAIL</span></span>|<span data-ttu-id="cc4a4-123">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="cc4a4-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cc4a4-124">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="cc4a4-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cc4a4-125">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="cc4a4-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc4a4-126">備註</span><span class="sxs-lookup"><span data-stu-id="cc4a4-126">Remarks</span></span>  

 <span data-ttu-id="cc4a4-127">I/o 完成通訊埠是使用的呼叫所建立 `CreateIoCompletionPort` 。</span><span class="sxs-lookup"><span data-stu-id="cc4a4-127">An I/O completion port is created by using a call to `CreateIoCompletionPort`.</span></span> <span data-ttu-id="cc4a4-128">CLR 會呼叫 `Bind` 以將控制碼系結至該埠。</span><span class="sxs-lookup"><span data-stu-id="cc4a4-128">The CLR calls `Bind` to bind a handle to that port.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cc4a4-129">當 i/o 要求完成時，主機必須呼叫 [ICLRIoCompletionManager：： OnComplete](iclriocompletionmanager-oncomplete-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="cc4a4-129">When an I/O request completes, the host must call the [ICLRIoCompletionManager::OnComplete](iclriocompletionmanager-oncomplete-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc4a4-130">需求</span><span class="sxs-lookup"><span data-stu-id="cc4a4-130">Requirements</span></span>  

 <span data-ttu-id="cc4a4-131">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cc4a4-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc4a4-132">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="cc4a4-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cc4a4-133">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="cc4a4-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cc4a4-134">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc4a4-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc4a4-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc4a4-135">See also</span></span>

- [<span data-ttu-id="cc4a4-136">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="cc4a4-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
