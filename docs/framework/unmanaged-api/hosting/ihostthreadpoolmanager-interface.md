---
title: "IHostThreadPoolManager 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostThreadPoolManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager
helpviewer_keywords:
- IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: c3a2cd90-7c4e-4374-bb87-b41befb8344f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1cd58c53deec0a895ae6f67cccf26d2c8c2530be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihostthreadpoolmanager-interface"></a><span data-ttu-id="baadb-102">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="baadb-102">IHostThreadPoolManager Interface</span></span>
<span data-ttu-id="baadb-103">提供方法讓 common language runtime (CLR) 來設定執行緒集區，以及佇列的執行緒集區的工作項目。</span><span class="sxs-lookup"><span data-stu-id="baadb-103">Provides methods that enable the common language runtime (CLR) to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="baadb-104">方法</span><span class="sxs-lookup"><span data-stu-id="baadb-104">Methods</span></span>  
  
|<span data-ttu-id="baadb-105">方法</span><span class="sxs-lookup"><span data-stu-id="baadb-105">Method</span></span>|<span data-ttu-id="baadb-106">描述</span><span class="sxs-lookup"><span data-stu-id="baadb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="baadb-107">GetAvailableThreads 方法</span><span class="sxs-lookup"><span data-stu-id="baadb-107">GetAvailableThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md)|<span data-ttu-id="baadb-108">取得目前未處理的工作項目之執行緒集區中的執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="baadb-108">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>|  
|[<span data-ttu-id="baadb-109">GetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="baadb-109">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)|<span data-ttu-id="baadb-110">執行緒集區中，同時取得主機維護執行緒的數目上限。</span><span class="sxs-lookup"><span data-stu-id="baadb-110">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>|  
|[<span data-ttu-id="baadb-111">GetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="baadb-111">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)|<span data-ttu-id="baadb-112">取得主機維護的閒置執行緒數目最小要求的頁數。</span><span class="sxs-lookup"><span data-stu-id="baadb-112">Gets the minimum number of idle threads that the host maintains in anticipation of requests.</span></span>|  
|[<span data-ttu-id="baadb-113">QueueUserWorkItem 方法</span><span class="sxs-lookup"><span data-stu-id="baadb-113">QueueUserWorkItem Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)|<span data-ttu-id="baadb-114">對於執行，函式，並提供物件，其中包含要由函式使用的資料。</span><span class="sxs-lookup"><span data-stu-id="baadb-114">Queues a function for execution, and provides an object containing data to be used by the function.</span></span>|  
|[<span data-ttu-id="baadb-115">SetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="baadb-115">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)|<span data-ttu-id="baadb-116">設定主應用程式可以維護執行緒集區中的執行緒的數目上限。</span><span class="sxs-lookup"><span data-stu-id="baadb-116">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>|  
|[<span data-ttu-id="baadb-117">SetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="baadb-117">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)|<span data-ttu-id="baadb-118">預期的要求中設定主應用程式必須維護的閒置執行緒的最小數目。</span><span class="sxs-lookup"><span data-stu-id="baadb-118">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="baadb-119">備註</span><span class="sxs-lookup"><span data-stu-id="baadb-119">Remarks</span></span>  
 <span data-ttu-id="baadb-120">主機不需要使用的呼叫中指定的值，設定執行緒集區`SetMaxThreads`和`SetMinThreads`方法。</span><span class="sxs-lookup"><span data-stu-id="baadb-120">The host is not required to configure the thread pool by using the values specified in calls to the `SetMaxThreads` and `SetMinThreads` methods.</span></span> <span data-ttu-id="baadb-121">在此情況下，主應用程式應該傳回 E_NOTIMPL 的 HRESULT 值，這些方法。</span><span class="sxs-lookup"><span data-stu-id="baadb-121">In this case, the host should return an HRESULT value of E_NOTIMPL from these methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="baadb-122">需求</span><span class="sxs-lookup"><span data-stu-id="baadb-122">Requirements</span></span>  
 <span data-ttu-id="baadb-123">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="baadb-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="baadb-124">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="baadb-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="baadb-125">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="baadb-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="baadb-126">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="baadb-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baadb-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="baadb-127">See Also</span></span>  
 <xref:System.Threading>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="baadb-128">裝載介面</span><span class="sxs-lookup"><span data-stu-id="baadb-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
