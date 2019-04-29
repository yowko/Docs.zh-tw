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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e7976740a79efda8e5ab569f2efb55444012c5d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796554"
---
# <a name="ihostthreadpoolmanager-interface"></a><span data-ttu-id="a3422-102">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="a3422-102">IHostThreadPoolManager Interface</span></span>
<span data-ttu-id="a3422-103">提供方法，啟用 common language runtime (CLR) 來設定執行緒集區，以及執行緒集區的工作項目佇列。</span><span class="sxs-lookup"><span data-stu-id="a3422-103">Provides methods that enable the common language runtime (CLR) to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a3422-104">方法</span><span class="sxs-lookup"><span data-stu-id="a3422-104">Methods</span></span>  
  
|<span data-ttu-id="a3422-105">方法</span><span class="sxs-lookup"><span data-stu-id="a3422-105">Method</span></span>|<span data-ttu-id="a3422-106">描述</span><span class="sxs-lookup"><span data-stu-id="a3422-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a3422-107">GetAvailableThreads 方法</span><span class="sxs-lookup"><span data-stu-id="a3422-107">GetAvailableThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md)|<span data-ttu-id="a3422-108">取得目前未處理的工作項目之執行緒集區中的執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="a3422-108">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>|  
|[<span data-ttu-id="a3422-109">GetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="a3422-109">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)|<span data-ttu-id="a3422-110">執行緒集區中，同時取得主機維護執行緒的數目上限。</span><span class="sxs-lookup"><span data-stu-id="a3422-110">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>|  
|[<span data-ttu-id="a3422-111">GetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="a3422-111">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)|<span data-ttu-id="a3422-112">預期的要求中取得主控件保留的閒置執行緒的數目下限。</span><span class="sxs-lookup"><span data-stu-id="a3422-112">Gets the minimum number of idle threads that the host maintains in anticipation of requests.</span></span>|  
|[<span data-ttu-id="a3422-113">QueueUserWorkItem 方法</span><span class="sxs-lookup"><span data-stu-id="a3422-113">QueueUserWorkItem Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)|<span data-ttu-id="a3422-114">函式，以執行排入佇列，並提供包含要使用的函式資料的物件。</span><span class="sxs-lookup"><span data-stu-id="a3422-114">Queues a function for execution, and provides an object containing data to be used by the function.</span></span>|  
|[<span data-ttu-id="a3422-115">SetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="a3422-115">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)|<span data-ttu-id="a3422-116">設定主應用程式可以維護執行緒集區中的執行緒最大數目。</span><span class="sxs-lookup"><span data-stu-id="a3422-116">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>|  
|[<span data-ttu-id="a3422-117">SetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="a3422-117">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)|<span data-ttu-id="a3422-118">預期的要求中設定主應用程式必須維護的閒置執行緒的數目下限。</span><span class="sxs-lookup"><span data-stu-id="a3422-118">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3422-119">備註</span><span class="sxs-lookup"><span data-stu-id="a3422-119">Remarks</span></span>  
 <span data-ttu-id="a3422-120">主應用程式不需要使用的呼叫中指定的值，設定執行緒集區`SetMaxThreads`和`SetMinThreads`方法。</span><span class="sxs-lookup"><span data-stu-id="a3422-120">The host is not required to configure the thread pool by using the values specified in calls to the `SetMaxThreads` and `SetMinThreads` methods.</span></span> <span data-ttu-id="a3422-121">在此情況下，主應用程式應該從這些方法會傳回 E_NOTIMPL HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="a3422-121">In this case, the host should return an HRESULT value of E_NOTIMPL from these methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3422-122">需求</span><span class="sxs-lookup"><span data-stu-id="a3422-122">Requirements</span></span>  
 <span data-ttu-id="a3422-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a3422-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3422-124">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a3422-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a3422-125">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a3422-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a3422-126">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3422-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3422-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3422-127">See also</span></span>

- <xref:System.Threading>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="a3422-128">裝載介面</span><span class="sxs-lookup"><span data-stu-id="a3422-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
