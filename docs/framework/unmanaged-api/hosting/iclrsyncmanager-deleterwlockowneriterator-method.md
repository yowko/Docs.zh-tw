---
title: ICLRSyncManager::DeleteRWLockOwnerIterator 方法
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.DeleteRWLockOwnerIterator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator method [.NET Framework hosting]
- DeleteRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: fcfd340a-b7d6-44e4-8167-2c05b789d483
topic_type:
- apiref
ms.openlocfilehash: a4094a64d27072ce257341398bb49419bef9b8bb
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763146"
---
# <a name="iclrsyncmanagerdeleterwlockowneriterator-method"></a><span data-ttu-id="73959-102">ICLRSyncManager::DeleteRWLockOwnerIterator 方法</span><span class="sxs-lookup"><span data-stu-id="73959-102">ICLRSyncManager::DeleteRWLockOwnerIterator Method</span></span>
<span data-ttu-id="73959-103">要求 common language runtime （CLR）終結由呼叫[ICLRSyncManager：： CreateRWLockOwnerIterator](iclrsyncmanager-createrwlockowneriterator-method.md)所建立的反覆運算器。</span><span class="sxs-lookup"><span data-stu-id="73959-103">Requests that the common language runtime (CLR) destroy an iterator that was created by a call to [ICLRSyncManager::CreateRWLockOwnerIterator](iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73959-104">語法</span><span class="sxs-lookup"><span data-stu-id="73959-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteRWLockOwnerIterator (  
    [in] SIZE_T  Iterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73959-105">參數</span><span class="sxs-lookup"><span data-stu-id="73959-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="73959-106">在使用的呼叫所建立的反覆運算器 `CreateRWLockOwnerIterator` 。</span><span class="sxs-lookup"><span data-stu-id="73959-106">[in] The iterator that was created by using a call to `CreateRWLockOwnerIterator`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73959-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="73959-107">Return Value</span></span>  
  
|<span data-ttu-id="73959-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="73959-108">HRESULT</span></span>|<span data-ttu-id="73959-109">Description</span><span class="sxs-lookup"><span data-stu-id="73959-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="73959-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="73959-110">S_OK</span></span>|<span data-ttu-id="73959-111">`DeleteRWLockOwnerIterator`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="73959-111">`DeleteRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="73959-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="73959-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="73959-113">CLR 尚未載入進程中，或處於無法執行 managed 程式碼或無法成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="73959-113">The CLR has not been loaded into a process, or is in a state in which it cannot run managed code or successfully process the call.</span></span>|  
|<span data-ttu-id="73959-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="73959-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="73959-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="73959-115">The call timed out.</span></span>|  
|<span data-ttu-id="73959-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="73959-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="73959-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="73959-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="73959-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="73959-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="73959-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="73959-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="73959-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="73959-120">E_FAIL</span></span>|<span data-ttu-id="73959-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="73959-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="73959-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="73959-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="73959-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="73959-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73959-124">備註</span><span class="sxs-lookup"><span data-stu-id="73959-124">Remarks</span></span>  
 <span data-ttu-id="73959-125">主機可以呼叫這個方法， `CreateRWLockOwnerIterator` 以確保其執行緒的執行保持同步。</span><span class="sxs-lookup"><span data-stu-id="73959-125">The host can call this method and `CreateRWLockOwnerIterator` to ensure that its threading implementation remains synchronized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73959-126">規格需求</span><span class="sxs-lookup"><span data-stu-id="73959-126">Requirements</span></span>  
 <span data-ttu-id="73959-127">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="73959-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73959-128">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="73959-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="73959-129">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="73959-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="73959-130">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73959-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73959-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73959-131">See also</span></span>

- [<span data-ttu-id="73959-132">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="73959-132">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="73959-133">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="73959-133">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
