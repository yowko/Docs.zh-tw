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
ms.openlocfilehash: 8d18e6c1dca7f52b17c19f4638410a08866905f7
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804803"
---
# <a name="ihostiocompletionmanagerbind-method"></a><span data-ttu-id="d2740-102">IHostIoCompletionManager::Bind 方法</span><span class="sxs-lookup"><span data-stu-id="d2740-102">IHostIoCompletionManager::Bind Method</span></span>
<span data-ttu-id="d2740-103">將指定的控制碼系結至先前呼叫[CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md)所建立的 i/o 完成埠。</span><span class="sxs-lookup"><span data-stu-id="d2740-103">Binds the specified handle to an I/O completion port that has been created by an earlier call to [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2740-104">語法</span><span class="sxs-lookup"><span data-stu-id="d2740-104">Syntax</span></span>  
  
```cpp  
HRESULT Bind (  
    [in] HANDLE hPort,  
    [in] HANDLE hHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2740-105">參數</span><span class="sxs-lookup"><span data-stu-id="d2740-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="d2740-106">在要系結的 i/o 完成通訊埠 `hHandle` 。</span><span class="sxs-lookup"><span data-stu-id="d2740-106">[in] The I/O completion port to which to bind `hHandle`.</span></span> <span data-ttu-id="d2740-107">如果的值 `hPort` 是 null，會系結 `hHandle` 至預設的 i/o 完成埠。</span><span class="sxs-lookup"><span data-stu-id="d2740-107">If the value of `hPort` is null, `hHandle` is bound to the default I/O completion port.</span></span>  
  
 `hHandle`  
 <span data-ttu-id="d2740-108">在要系結的作業系統控制碼 `hPort` 。</span><span class="sxs-lookup"><span data-stu-id="d2740-108">[in] The operating system handle to bind to `hPort`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d2740-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="d2740-109">Return Value</span></span>  
  
|<span data-ttu-id="d2740-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d2740-110">HRESULT</span></span>|<span data-ttu-id="d2740-111">描述</span><span class="sxs-lookup"><span data-stu-id="d2740-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d2740-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="d2740-112">S_OK</span></span>|<span data-ttu-id="d2740-113">`Bind`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="d2740-113">`Bind` returned successfully.</span></span>|  
|<span data-ttu-id="d2740-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d2740-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d2740-115">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="d2740-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d2740-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d2740-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d2740-117">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="d2740-117">The call timed out.</span></span>|  
|<span data-ttu-id="d2740-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d2740-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d2740-119">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="d2740-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d2740-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d2740-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d2740-121">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="d2740-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d2740-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d2740-122">E_FAIL</span></span>|<span data-ttu-id="d2740-123">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="d2740-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d2740-124">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="d2740-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d2740-125">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="d2740-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2740-126">備註</span><span class="sxs-lookup"><span data-stu-id="d2740-126">Remarks</span></span>  
 <span data-ttu-id="d2740-127">I/o 完成通訊埠是使用的呼叫所建立 `CreateIoCompletionPort` 。</span><span class="sxs-lookup"><span data-stu-id="d2740-127">An I/O completion port is created by using a call to `CreateIoCompletionPort`.</span></span> <span data-ttu-id="d2740-128">CLR 會呼叫 `Bind` 來系結該埠的控制碼。</span><span class="sxs-lookup"><span data-stu-id="d2740-128">The CLR calls `Bind` to bind a handle to that port.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d2740-129">當 i/o 要求完成時，主機必須呼叫[ICLRIoCompletionManager：： OnComplete](iclriocompletionmanager-oncomplete-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="d2740-129">When an I/O request completes, the host must call the [ICLRIoCompletionManager::OnComplete](iclriocompletionmanager-oncomplete-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2740-130">規格需求</span><span class="sxs-lookup"><span data-stu-id="d2740-130">Requirements</span></span>  
 <span data-ttu-id="d2740-131">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d2740-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2740-132">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="d2740-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d2740-133">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d2740-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d2740-134">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2740-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2740-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2740-135">See also</span></span>

- [<span data-ttu-id="d2740-136">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="d2740-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
