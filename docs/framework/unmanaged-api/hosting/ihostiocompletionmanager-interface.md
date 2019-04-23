---
title: IHostIoCompletionManager 介面
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c28d1983-83f7-46e2-990f-dbb9dc07c818
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3c3bebe8eabd4d5fd5faec21e0b0efc408353bc2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197265"
---
# <a name="ihostiocompletionmanager-interface"></a><span data-ttu-id="b3e93-102">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="b3e93-102">IHostIoCompletionManager Interface</span></span>
<span data-ttu-id="b3e93-103">提供方法，可讓 common language runtime (CLR) 與主應用程式所提供的 I/O 完成連接埠進行互動。</span><span class="sxs-lookup"><span data-stu-id="b3e93-103">Provides methods that allow the common language runtime (CLR) to interact with I/O completion ports provided by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b3e93-104">方法</span><span class="sxs-lookup"><span data-stu-id="b3e93-104">Methods</span></span>  
  
|<span data-ttu-id="b3e93-105">方法</span><span class="sxs-lookup"><span data-stu-id="b3e93-105">Method</span></span>|<span data-ttu-id="b3e93-106">描述</span><span class="sxs-lookup"><span data-stu-id="b3e93-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b3e93-107">Bind 方法</span><span class="sxs-lookup"><span data-stu-id="b3e93-107">Bind Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)|<span data-ttu-id="b3e93-108">將控制代碼繫結至 I/O 完成連接埠。</span><span class="sxs-lookup"><span data-stu-id="b3e93-108">Binds a handle to an I/O completion port.</span></span>|  
|[<span data-ttu-id="b3e93-109">CloseIoCompletionPort 方法</span><span class="sxs-lookup"><span data-stu-id="b3e93-109">CloseIoCompletionPort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-closeiocompletionport-method.md)|<span data-ttu-id="b3e93-110">關閉透過先前呼叫所建立的連接埠`CreateIoCompletionPort`。</span><span class="sxs-lookup"><span data-stu-id="b3e93-110">Closes a port that was created through an earlier call to `CreateIoCompletionPort`.</span></span>|  
|[<span data-ttu-id="b3e93-111">CreateIoCompletionPort 方法</span><span class="sxs-lookup"><span data-stu-id="b3e93-111">CreateIoCompletionPort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)|<span data-ttu-id="b3e93-112">主應用程式建立新的 I/O 完成連接埠的要求。</span><span class="sxs-lookup"><span data-stu-id="b3e93-112">Requests that the host create a new I/O completion port.</span></span>|  
|[<span data-ttu-id="b3e93-113">GetAvailableThreads 方法</span><span class="sxs-lookup"><span data-stu-id="b3e93-113">GetAvailableThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getavailablethreads-method.md)|<span data-ttu-id="b3e93-114">取得目前未處理要求的 I/O 完成執行緒的數目。</span><span class="sxs-lookup"><span data-stu-id="b3e93-114">Gets the number of I/O completion threads that are not currently processing requests.</span></span>|  
|[<span data-ttu-id="b3e93-115">GetHostOverlappedSize 方法</span><span class="sxs-lookup"><span data-stu-id="b3e93-115">GetHostOverlappedSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)|<span data-ttu-id="b3e93-116">取得主應用程式想要附加至 I/O 要求的任何自訂資料的大小。</span><span class="sxs-lookup"><span data-stu-id="b3e93-116">Gets the size of any custom data the host intends to append to I/O requests.</span></span>|  
|[<span data-ttu-id="b3e93-117">GetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="b3e93-117">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getmaxthreads-method.md)|<span data-ttu-id="b3e93-118">取得服務 I/O 要求的主機可以配置的執行緒數目上限。</span><span class="sxs-lookup"><span data-stu-id="b3e93-118">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>|  
|[<span data-ttu-id="b3e93-119">GetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="b3e93-119">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getminthreads-method.md)|<span data-ttu-id="b3e93-120">取得服務 I/O 要求的主機提供的執行緒最小數目。</span><span class="sxs-lookup"><span data-stu-id="b3e93-120">Gets the minimum number of threads that the host provides to service I/O requests.</span></span>|  
|[<span data-ttu-id="b3e93-121">InitializeHostOverlapped 方法</span><span class="sxs-lookup"><span data-stu-id="b3e93-121">InitializeHostOverlapped Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)|<span data-ttu-id="b3e93-122">提供有機會初始化的 I/O 要求相關的任何自訂資料中的主應用程式。</span><span class="sxs-lookup"><span data-stu-id="b3e93-122">Provides the host with an opportunity to initialize any custom data about an I/O request.</span></span>|  
|[<span data-ttu-id="b3e93-123">SetCLRIoCompletionManager 方法</span><span class="sxs-lookup"><span data-stu-id="b3e93-123">SetCLRIoCompletionManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setclriocompletionmanager-method.md)|<span data-ttu-id="b3e93-124">主應用程式提供的介面指標[ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) ，CLR 所實作的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b3e93-124">Provides the host with an interface pointer to an [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implemented by the CLR.</span></span>|  
|[<span data-ttu-id="b3e93-125">SetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="b3e93-125">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)|<span data-ttu-id="b3e93-126">I/O 要求提供服務設定主應用程式指派的執行緒的數目上限。</span><span class="sxs-lookup"><span data-stu-id="b3e93-126">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>|  
|[<span data-ttu-id="b3e93-127">SetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="b3e93-127">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setminthreads-method.md)|<span data-ttu-id="b3e93-128">I/O 完成設定主應用程式應該配置的執行緒最小數目。</span><span class="sxs-lookup"><span data-stu-id="b3e93-128">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3e93-129">備註</span><span class="sxs-lookup"><span data-stu-id="b3e93-129">Remarks</span></span>  
 <span data-ttu-id="b3e93-130">`IHostIoCompletionManager` 對應至`ICLRIoCompletionManager`，CLR 所實作的介面。</span><span class="sxs-lookup"><span data-stu-id="b3e93-130">`IHostIoCompletionManager` corresponds to the `ICLRIoCompletionManager` interface implemented by the CLR.</span></span> <span data-ttu-id="b3e93-131">CLR 會呼叫的方法`IHostIoCompletionManager`若要將控制代碼繫結至主應用程式提供，且主機會呼叫方法的連接埠`ICLRIoCompletionManager`報告的 I/O 要求完成。</span><span class="sxs-lookup"><span data-stu-id="b3e93-131">The CLR calls the methods of `IHostIoCompletionManager` to bind handles to the ports that the host provides, and the host calls the methods of `ICLRIoCompletionManager` to report the completion of I/O requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3e93-132">需求</span><span class="sxs-lookup"><span data-stu-id="b3e93-132">Requirements</span></span>  
 <span data-ttu-id="b3e93-133">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b3e93-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3e93-134">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b3e93-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b3e93-135">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b3e93-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b3e93-136">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3e93-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3e93-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3e93-137">See also</span></span>

- [<span data-ttu-id="b3e93-138">裝載介面</span><span class="sxs-lookup"><span data-stu-id="b3e93-138">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
