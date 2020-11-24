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
ms.openlocfilehash: db651e3fe51f90b84449874f2c60a12050b0350e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687108"
---
# <a name="iclrsyncmanagerdeleterwlockowneriterator-method"></a><span data-ttu-id="074ca-102">ICLRSyncManager::DeleteRWLockOwnerIterator 方法</span><span class="sxs-lookup"><span data-stu-id="074ca-102">ICLRSyncManager::DeleteRWLockOwnerIterator Method</span></span>

<span data-ttu-id="074ca-103">要求 common language runtime (CLR) 終結由呼叫 [ICLRSyncManager：： CreateRWLockOwnerIterator](iclrsyncmanager-createrwlockowneriterator-method.md)所建立的反覆運算器。</span><span class="sxs-lookup"><span data-stu-id="074ca-103">Requests that the common language runtime (CLR) destroy an iterator that was created by a call to [ICLRSyncManager::CreateRWLockOwnerIterator](iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="074ca-104">語法</span><span class="sxs-lookup"><span data-stu-id="074ca-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteRWLockOwnerIterator (  
    [in] SIZE_T  Iterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="074ca-105">參數</span><span class="sxs-lookup"><span data-stu-id="074ca-105">Parameters</span></span>  

 `Iterator`  
 <span data-ttu-id="074ca-106">在使用的呼叫所建立的反覆運算器 `CreateRWLockOwnerIterator` 。</span><span class="sxs-lookup"><span data-stu-id="074ca-106">[in] The iterator that was created by using a call to `CreateRWLockOwnerIterator`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="074ca-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="074ca-107">Return Value</span></span>  
  
|<span data-ttu-id="074ca-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="074ca-108">HRESULT</span></span>|<span data-ttu-id="074ca-109">描述</span><span class="sxs-lookup"><span data-stu-id="074ca-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="074ca-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="074ca-110">S_OK</span></span>|<span data-ttu-id="074ca-111">`DeleteRWLockOwnerIterator` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="074ca-111">`DeleteRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="074ca-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="074ca-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="074ca-113">CLR 尚未載入至進程，或處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="074ca-113">The CLR has not been loaded into a process, or is in a state in which it cannot run managed code or successfully process the call.</span></span>|  
|<span data-ttu-id="074ca-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="074ca-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="074ca-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="074ca-115">The call timed out.</span></span>|  
|<span data-ttu-id="074ca-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="074ca-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="074ca-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="074ca-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="074ca-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="074ca-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="074ca-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="074ca-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="074ca-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="074ca-120">E_FAIL</span></span>|<span data-ttu-id="074ca-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="074ca-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="074ca-122">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="074ca-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="074ca-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="074ca-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="074ca-124">備註</span><span class="sxs-lookup"><span data-stu-id="074ca-124">Remarks</span></span>  

 <span data-ttu-id="074ca-125">主機可以呼叫這個方法，並 `CreateRWLockOwnerIterator` 確保其執行緒執行保持同步。</span><span class="sxs-lookup"><span data-stu-id="074ca-125">The host can call this method and `CreateRWLockOwnerIterator` to ensure that its threading implementation remains synchronized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="074ca-126">需求</span><span class="sxs-lookup"><span data-stu-id="074ca-126">Requirements</span></span>  

 <span data-ttu-id="074ca-127">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="074ca-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="074ca-128">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="074ca-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="074ca-129">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="074ca-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="074ca-130">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="074ca-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="074ca-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="074ca-131">See also</span></span>

- [<span data-ttu-id="074ca-132">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="074ca-132">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="074ca-133">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="074ca-133">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
