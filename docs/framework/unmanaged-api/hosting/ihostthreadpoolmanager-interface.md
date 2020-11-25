---
title: IHostThreadPoolManager 介面
ms.date: 03/30/2017
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
ms.openlocfilehash: b6625b0ef4dc3de4067514a0b39849c7a958d5c4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730756"
---
# <a name="ihostthreadpoolmanager-interface"></a><span data-ttu-id="04265-102">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="04265-102">IHostThreadPoolManager Interface</span></span>

<span data-ttu-id="04265-103">提供的方法，可讓 common language runtime (CLR) 設定執行緒集區，以及將工作專案加入執行緒集區。</span><span class="sxs-lookup"><span data-stu-id="04265-103">Provides methods that enable the common language runtime (CLR) to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="04265-104">方法</span><span class="sxs-lookup"><span data-stu-id="04265-104">Methods</span></span>  
  
|<span data-ttu-id="04265-105">方法</span><span class="sxs-lookup"><span data-stu-id="04265-105">Method</span></span>|<span data-ttu-id="04265-106">描述</span><span class="sxs-lookup"><span data-stu-id="04265-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="04265-107">GetAvailableThreads 方法</span><span class="sxs-lookup"><span data-stu-id="04265-107">GetAvailableThreads Method</span></span>](ihostthreadpoolmanager-getavailablethreads-method.md)|<span data-ttu-id="04265-108">取得執行緒集區中目前未處理工作專案的執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="04265-108">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>|  
|[<span data-ttu-id="04265-109">GetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="04265-109">GetMaxThreads Method</span></span>](ihostthreadpoolmanager-getmaxthreads-method.md)|<span data-ttu-id="04265-110">取得主機線上程集區中同時維護的執行緒數目上限。</span><span class="sxs-lookup"><span data-stu-id="04265-110">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>|  
|[<span data-ttu-id="04265-111">GetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="04265-111">GetMinThreads Method</span></span>](ihostthreadpoolmanager-getminthreads-method.md)|<span data-ttu-id="04265-112">取得主機在預期的要求中維持的最小閒置執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="04265-112">Gets the minimum number of idle threads that the host maintains in anticipation of requests.</span></span>|  
|[<span data-ttu-id="04265-113">QueueUserWorkItem 方法</span><span class="sxs-lookup"><span data-stu-id="04265-113">QueueUserWorkItem Method</span></span>](ihostthreadpoolmanager-queueuserworkitem-method.md)|<span data-ttu-id="04265-114">將函式排入佇列以便執行，並提供包含函式所要使用之資料的物件。</span><span class="sxs-lookup"><span data-stu-id="04265-114">Queues a function for execution, and provides an object containing data to be used by the function.</span></span>|  
|[<span data-ttu-id="04265-115">SetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="04265-115">SetMaxThreads Method</span></span>](ihostthreadpoolmanager-setmaxthreads-method.md)|<span data-ttu-id="04265-116">設定主機可以線上程集區中維護的執行緒數目上限。</span><span class="sxs-lookup"><span data-stu-id="04265-116">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>|  
|[<span data-ttu-id="04265-117">SetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="04265-117">SetMinThreads Method</span></span>](ihostthreadpoolmanager-setminthreads-method.md)|<span data-ttu-id="04265-118">設定主機必須在預期的要求中維持的最小閒置執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="04265-118">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04265-119">備註</span><span class="sxs-lookup"><span data-stu-id="04265-119">Remarks</span></span>  

 <span data-ttu-id="04265-120">使用和方法的呼叫中指定的值，不需要主控制項來設定執行緒集區 `SetMaxThreads` `SetMinThreads` 。</span><span class="sxs-lookup"><span data-stu-id="04265-120">The host is not required to configure the thread pool by using the values specified in calls to the `SetMaxThreads` and `SetMinThreads` methods.</span></span> <span data-ttu-id="04265-121">在此情況下，主機應該會從這些方法傳回 E_NOTIMPL 的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="04265-121">In this case, the host should return an HRESULT value of E_NOTIMPL from these methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04265-122">需求</span><span class="sxs-lookup"><span data-stu-id="04265-122">Requirements</span></span>  

 <span data-ttu-id="04265-123">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="04265-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04265-124">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="04265-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="04265-125">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="04265-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="04265-126">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04265-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04265-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04265-127">See also</span></span>

- <xref:System.Threading>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="04265-128">裝載介面</span><span class="sxs-lookup"><span data-stu-id="04265-128">Hosting Interfaces</span></span>](hosting-interfaces.md)
