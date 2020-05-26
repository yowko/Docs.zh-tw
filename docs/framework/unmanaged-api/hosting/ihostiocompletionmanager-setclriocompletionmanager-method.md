---
title: IHostIoCompletionManager::SetCLRIoCompletionManager 方法
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetCLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager method [.NET Framework hosting]
- SetCLRIoCompletionManager method [.NET Framework hosting]
ms.assetid: 4254bb01-3a14-4f34-a3be-60ff1f5072b5
topic_type:
- apiref
ms.openlocfilehash: a76e807e6b316fc4b904e3f085a17b00d6a11c73
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804703"
---
# <a name="ihostiocompletionmanagersetclriocompletionmanager-method"></a><span data-ttu-id="28cfb-102">IHostIoCompletionManager::SetCLRIoCompletionManager 方法</span><span class="sxs-lookup"><span data-stu-id="28cfb-102">IHostIoCompletionManager::SetCLRIoCompletionManager Method</span></span>
<span data-ttu-id="28cfb-103">提供具有 common language runtime （CLR）所實[ICLRIoCompletionManager](iclriocompletionmanager-interface.md)實例之介面指標的主機。</span><span class="sxs-lookup"><span data-stu-id="28cfb-103">Provides the host with an interface pointer to the [ICLRIoCompletionManager](iclriocompletionmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28cfb-104">語法</span><span class="sxs-lookup"><span data-stu-id="28cfb-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRIoCompletionManager (  
    [in] ICLRIoCompletionManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28cfb-105">參數</span><span class="sxs-lookup"><span data-stu-id="28cfb-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="28cfb-106">在CLR 提供之實例的介面指標 `ICLRIoCompletionManager` 。</span><span class="sxs-lookup"><span data-stu-id="28cfb-106">[in] An interface pointer to an `ICLRIoCompletionManager` instance provided by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28cfb-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="28cfb-107">Return Value</span></span>  
  
|<span data-ttu-id="28cfb-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="28cfb-108">HRESULT</span></span>|<span data-ttu-id="28cfb-109">描述</span><span class="sxs-lookup"><span data-stu-id="28cfb-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="28cfb-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="28cfb-110">S_OK</span></span>|<span data-ttu-id="28cfb-111">`SetCLRIoCompletionManager`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="28cfb-111">`SetCLRIoCompletionManager` returned successfully.</span></span>|  
|<span data-ttu-id="28cfb-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="28cfb-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="28cfb-113">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="28cfb-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="28cfb-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="28cfb-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="28cfb-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="28cfb-115">The call timed out.</span></span>|  
|<span data-ttu-id="28cfb-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="28cfb-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="28cfb-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="28cfb-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="28cfb-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="28cfb-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="28cfb-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="28cfb-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="28cfb-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="28cfb-120">E_FAIL</span></span>|<span data-ttu-id="28cfb-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="28cfb-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="28cfb-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="28cfb-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="28cfb-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="28cfb-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28cfb-124">備註</span><span class="sxs-lookup"><span data-stu-id="28cfb-124">Remarks</span></span>  
 <span data-ttu-id="28cfb-125">在 CLR 已呼叫之後 `SetCLRIoCompletionManager` ，主機必須呼叫[ICLRIoCompletionManager：： OnComplete](iclriocompletionmanager-oncomplete-method.md) ，以便在 i/o 要求完成時通知 CLR。</span><span class="sxs-lookup"><span data-stu-id="28cfb-125">After the CLR has called `SetCLRIoCompletionManager`, the host must call [ICLRIoCompletionManager::OnComplete](iclriocompletionmanager-oncomplete-method.md) to notify the CLR when an I/O request has been completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28cfb-126">規格需求</span><span class="sxs-lookup"><span data-stu-id="28cfb-126">Requirements</span></span>  
 <span data-ttu-id="28cfb-127">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="28cfb-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28cfb-128">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="28cfb-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="28cfb-129">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="28cfb-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="28cfb-130">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28cfb-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28cfb-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28cfb-131">See also</span></span>

- [<span data-ttu-id="28cfb-132">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="28cfb-132">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="28cfb-133">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="28cfb-133">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
