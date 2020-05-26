---
title: IHostTaskManager::SetCLRTaskManager 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetCLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetCLRTaskManager
helpviewer_keywords:
- IHostTaskManager::SetCLRTaskManager method [.NET Framework hosting]
- SetCLRTaskManager method [.NET Framework hosting]
ms.assetid: ec90ee83-bd4b-408b-9274-62a923ab86a1
topic_type:
- apiref
ms.openlocfilehash: 0e030a33a0a3368f35c82fad33f1ea2ce32446af
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841824"
---
# <a name="ihosttaskmanagersetclrtaskmanager-method"></a><span data-ttu-id="ad41f-102">IHostTaskManager::SetCLRTaskManager 方法</span><span class="sxs-lookup"><span data-stu-id="ad41f-102">IHostTaskManager::SetCLRTaskManager Method</span></span>
<span data-ttu-id="ad41f-103">提供具有由 common language runtime （CLR）所執行之[ICLRTaskManager](iclrtaskmanager-interface.md)實例介面指標的主機。</span><span class="sxs-lookup"><span data-stu-id="ad41f-103">Provides the host with an interface pointer to an [ICLRTaskManager](iclrtaskmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad41f-104">語法</span><span class="sxs-lookup"><span data-stu-id="ad41f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRTaskManager (  
    [in] ICLRTaskManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad41f-105">參數</span><span class="sxs-lookup"><span data-stu-id="ad41f-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="ad41f-106">在`ICLRTaskManager`由 common language runtime 所實作為實例的指標。</span><span class="sxs-lookup"><span data-stu-id="ad41f-106">[in] A pointer to an `ICLRTaskManager` instance implemented by the common language runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad41f-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="ad41f-107">Return Value</span></span>  
  
|<span data-ttu-id="ad41f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ad41f-108">HRESULT</span></span>|<span data-ttu-id="ad41f-109">描述</span><span class="sxs-lookup"><span data-stu-id="ad41f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ad41f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ad41f-110">S_OK</span></span>|<span data-ttu-id="ad41f-111">`SetCLRTaskManager`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="ad41f-111">`SetCLRTaskManager` returned successfully.</span></span>|  
|<span data-ttu-id="ad41f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ad41f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ad41f-113">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="ad41f-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ad41f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ad41f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ad41f-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="ad41f-115">The call timed out.</span></span>|  
|<span data-ttu-id="ad41f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ad41f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ad41f-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="ad41f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ad41f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ad41f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ad41f-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="ad41f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ad41f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ad41f-120">E_FAIL</span></span>|<span data-ttu-id="ad41f-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="ad41f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ad41f-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="ad41f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ad41f-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="ad41f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad41f-124">備註</span><span class="sxs-lookup"><span data-stu-id="ad41f-124">Remarks</span></span>  
 <span data-ttu-id="ad41f-125">執行時間會呼叫 `SetCLRTaskManager` ，以提供具有實例之介面指標的主機 `ICLRTaskManager` 。</span><span class="sxs-lookup"><span data-stu-id="ad41f-125">The runtime calls `SetCLRTaskManager` to provide the host with an interface pointer to an `ICLRTaskManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad41f-126">規格需求</span><span class="sxs-lookup"><span data-stu-id="ad41f-126">Requirements</span></span>  
 <span data-ttu-id="ad41f-127">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ad41f-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad41f-128">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="ad41f-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ad41f-129">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ad41f-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ad41f-130">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad41f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad41f-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad41f-131">See also</span></span>

- [<span data-ttu-id="ad41f-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="ad41f-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="ad41f-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="ad41f-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="ad41f-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="ad41f-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="ad41f-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="ad41f-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
