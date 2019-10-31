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
ms.openlocfilehash: 8aef78c7cf70e6b2d97af9c47d57908b86729ff7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122076"
---
# <a name="ihostthreadpoolmanager-interface"></a><span data-ttu-id="1dc88-102">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="1dc88-102">IHostThreadPoolManager Interface</span></span>
<span data-ttu-id="1dc88-103">提供的方法可讓 common language runtime （CLR）設定執行緒集區，並將工作專案排入執行緒集區佇列。</span><span class="sxs-lookup"><span data-stu-id="1dc88-103">Provides methods that enable the common language runtime (CLR) to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1dc88-104">方法</span><span class="sxs-lookup"><span data-stu-id="1dc88-104">Methods</span></span>  
  
|<span data-ttu-id="1dc88-105">方法</span><span class="sxs-lookup"><span data-stu-id="1dc88-105">Method</span></span>|<span data-ttu-id="1dc88-106">描述</span><span class="sxs-lookup"><span data-stu-id="1dc88-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1dc88-107">GetAvailableThreads 方法</span><span class="sxs-lookup"><span data-stu-id="1dc88-107">GetAvailableThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md)|<span data-ttu-id="1dc88-108">取得執行緒集區中目前未處理工作專案的執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="1dc88-108">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>|  
|[<span data-ttu-id="1dc88-109">GetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="1dc88-109">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)|<span data-ttu-id="1dc88-110">取得主機線上程集區中同時維護的執行緒數目上限。</span><span class="sxs-lookup"><span data-stu-id="1dc88-110">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>|  
|[<span data-ttu-id="1dc88-111">GetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="1dc88-111">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)|<span data-ttu-id="1dc88-112">取得主機在預期要求中維持的最小閒置執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="1dc88-112">Gets the minimum number of idle threads that the host maintains in anticipation of requests.</span></span>|  
|[<span data-ttu-id="1dc88-113">QueueUserWorkItem 方法</span><span class="sxs-lookup"><span data-stu-id="1dc88-113">QueueUserWorkItem Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)|<span data-ttu-id="1dc88-114">將函式排入佇列以便執行，並提供包含函數所要使用之資料的物件。</span><span class="sxs-lookup"><span data-stu-id="1dc88-114">Queues a function for execution, and provides an object containing data to be used by the function.</span></span>|  
|[<span data-ttu-id="1dc88-115">SetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="1dc88-115">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)|<span data-ttu-id="1dc88-116">設定主機可以線上程集區中維護的執行緒數目上限。</span><span class="sxs-lookup"><span data-stu-id="1dc88-116">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>|  
|[<span data-ttu-id="1dc88-117">SetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="1dc88-117">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)|<span data-ttu-id="1dc88-118">設定主機必須在要求中維持的最小閒置執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="1dc88-118">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1dc88-119">備註</span><span class="sxs-lookup"><span data-stu-id="1dc88-119">Remarks</span></span>  
 <span data-ttu-id="1dc88-120">主機不需要使用對 `SetMaxThreads` 和 `SetMinThreads` 方法的呼叫中指定的值來設定執行緒集區。</span><span class="sxs-lookup"><span data-stu-id="1dc88-120">The host is not required to configure the thread pool by using the values specified in calls to the `SetMaxThreads` and `SetMinThreads` methods.</span></span> <span data-ttu-id="1dc88-121">在此情況下，主機應該會從這些方法傳回 E_NOTIMPL 的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="1dc88-121">In this case, the host should return an HRESULT value of E_NOTIMPL from these methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dc88-122">需求</span><span class="sxs-lookup"><span data-stu-id="1dc88-122">Requirements</span></span>  
 <span data-ttu-id="1dc88-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1dc88-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dc88-124">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="1dc88-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1dc88-125">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1dc88-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1dc88-126">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dc88-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dc88-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="1dc88-127">See also</span></span>

- <xref:System.Threading>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="1dc88-128">裝載介面</span><span class="sxs-lookup"><span data-stu-id="1dc88-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
