---
title: ICLRGCManager::Collect 方法
ms.date: 03/30/2017
api_name:
- ICLRGCManager.Collect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::Collect
helpviewer_keywords:
- ICLRGCManager::Collect method [.NET Framework hosting]
- Collect method, ICLRGCManager interface [.NET Framework hosting]
ms.assetid: 0c6cbbea-c27c-4695-bda3-17c1910d8ddb
topic_type:
- apiref
ms.openlocfilehash: 90ce4e888ddb3a10dd0dfd7e68463311db86742f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677761"
---
# <a name="iclrgcmanagercollect-method"></a><span data-ttu-id="6ea9a-102">ICLRGCManager::Collect 方法</span><span class="sxs-lookup"><span data-stu-id="6ea9a-102">ICLRGCManager::Collect Method</span></span>

<span data-ttu-id="6ea9a-103">針對指定的層級強制進行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="6ea9a-103">Forces a garbage collection for the specified generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ea9a-104">語法</span><span class="sxs-lookup"><span data-stu-id="6ea9a-104">Syntax</span></span>  
  
```cpp  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ea9a-105">參數</span><span class="sxs-lookup"><span data-stu-id="6ea9a-105">Parameters</span></span>  

 `Generation`  
 <span data-ttu-id="6ea9a-106">在要收集的世代。</span><span class="sxs-lookup"><span data-stu-id="6ea9a-106">[in] The generation to collect.</span></span> <span data-ttu-id="6ea9a-107">值-1 會強制所有層代的集合。</span><span class="sxs-lookup"><span data-stu-id="6ea9a-107">A value of -1 forces a collection of all generations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ea9a-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="6ea9a-108">Return Value</span></span>  
  
|<span data-ttu-id="6ea9a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6ea9a-109">HRESULT</span></span>|<span data-ttu-id="6ea9a-110">描述</span><span class="sxs-lookup"><span data-stu-id="6ea9a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6ea9a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6ea9a-111">S_OK</span></span>|<span data-ttu-id="6ea9a-112">`Collect` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="6ea9a-112">`Collect` returned successfully.</span></span>|  
|<span data-ttu-id="6ea9a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6ea9a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6ea9a-114">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="6ea9a-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6ea9a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6ea9a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6ea9a-116">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="6ea9a-116">The call timed out.</span></span>|  
|<span data-ttu-id="6ea9a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6ea9a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6ea9a-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="6ea9a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6ea9a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6ea9a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6ea9a-120">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="6ea9a-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6ea9a-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6ea9a-121">E_FAIL</span></span>|<span data-ttu-id="6ea9a-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="6ea9a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6ea9a-123">在方法傳回 E_FAIL 之後，就無法在進程中使用 CLR。</span><span class="sxs-lookup"><span data-stu-id="6ea9a-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6ea9a-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="6ea9a-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ea9a-125">備註</span><span class="sxs-lookup"><span data-stu-id="6ea9a-125">Remarks</span></span>  

 <span data-ttu-id="6ea9a-126">`Collect`無論目前的狀態為何，方法都會強制 CLR 的垃圾收集行程執行集合。</span><span class="sxs-lookup"><span data-stu-id="6ea9a-126">The `Collect` method forces the CLR's garbage collector to perform a collection regardless of its current state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ea9a-127">需求</span><span class="sxs-lookup"><span data-stu-id="6ea9a-127">Requirements</span></span>  

 <span data-ttu-id="6ea9a-128">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6ea9a-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ea9a-129">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="6ea9a-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6ea9a-130">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="6ea9a-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6ea9a-131">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ea9a-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ea9a-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ea9a-132">See also</span></span>

- [<span data-ttu-id="6ea9a-133">自動記憶體管理</span><span class="sxs-lookup"><span data-stu-id="6ea9a-133">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="6ea9a-134">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="6ea9a-134">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="6ea9a-135">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="6ea9a-135">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="6ea9a-136">ICLRGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="6ea9a-136">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
- [<span data-ttu-id="6ea9a-137">CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="6ea9a-137">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="6ea9a-138">裝載介面</span><span class="sxs-lookup"><span data-stu-id="6ea9a-138">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="6ea9a-139">裝載</span><span class="sxs-lookup"><span data-stu-id="6ea9a-139">Hosting</span></span>](index.md)
