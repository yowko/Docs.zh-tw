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
ms.openlocfilehash: 51d79c398c94ec355528140325da2c25422cbad9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133853"
---
# <a name="ihostiocompletionmanager-interface"></a><span data-ttu-id="c44c6-102">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="c44c6-102">IHostIoCompletionManager Interface</span></span>
<span data-ttu-id="c44c6-103">提供的方法可讓 common language runtime （CLR）與主機所提供的 i/o 完成通訊埠互動。</span><span class="sxs-lookup"><span data-stu-id="c44c6-103">Provides methods that allow the common language runtime (CLR) to interact with I/O completion ports provided by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c44c6-104">方法</span><span class="sxs-lookup"><span data-stu-id="c44c6-104">Methods</span></span>  
  
|<span data-ttu-id="c44c6-105">方法</span><span class="sxs-lookup"><span data-stu-id="c44c6-105">Method</span></span>|<span data-ttu-id="c44c6-106">描述</span><span class="sxs-lookup"><span data-stu-id="c44c6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c44c6-107">Bind 方法</span><span class="sxs-lookup"><span data-stu-id="c44c6-107">Bind Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)|<span data-ttu-id="c44c6-108">將控制碼系結到 i/o 完成通訊埠。</span><span class="sxs-lookup"><span data-stu-id="c44c6-108">Binds a handle to an I/O completion port.</span></span>|  
|[<span data-ttu-id="c44c6-109">CloseIoCompletionPort 方法</span><span class="sxs-lookup"><span data-stu-id="c44c6-109">CloseIoCompletionPort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-closeiocompletionport-method.md)|<span data-ttu-id="c44c6-110">關閉透過先前的 `CreateIoCompletionPort`呼叫所建立的埠。</span><span class="sxs-lookup"><span data-stu-id="c44c6-110">Closes a port that was created through an earlier call to `CreateIoCompletionPort`.</span></span>|  
|[<span data-ttu-id="c44c6-111">CreateIoCompletionPort 方法</span><span class="sxs-lookup"><span data-stu-id="c44c6-111">CreateIoCompletionPort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)|<span data-ttu-id="c44c6-112">要求主機建立新的 i/o 完成埠。</span><span class="sxs-lookup"><span data-stu-id="c44c6-112">Requests that the host create a new I/O completion port.</span></span>|  
|[<span data-ttu-id="c44c6-113">GetAvailableThreads 方法</span><span class="sxs-lookup"><span data-stu-id="c44c6-113">GetAvailableThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getavailablethreads-method.md)|<span data-ttu-id="c44c6-114">取得目前未處理要求的 i/o 完成執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="c44c6-114">Gets the number of I/O completion threads that are not currently processing requests.</span></span>|  
|[<span data-ttu-id="c44c6-115">GetHostOverlappedSize 方法</span><span class="sxs-lookup"><span data-stu-id="c44c6-115">GetHostOverlappedSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)|<span data-ttu-id="c44c6-116">取得主機打算附加到 i/o 要求的任何自訂資料大小。</span><span class="sxs-lookup"><span data-stu-id="c44c6-116">Gets the size of any custom data the host intends to append to I/O requests.</span></span>|  
|[<span data-ttu-id="c44c6-117">GetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="c44c6-117">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getmaxthreads-method.md)|<span data-ttu-id="c44c6-118">取得主機可以為服務 i/o 要求所分配的執行緒數目上限。</span><span class="sxs-lookup"><span data-stu-id="c44c6-118">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>|  
|[<span data-ttu-id="c44c6-119">GetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="c44c6-119">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getminthreads-method.md)|<span data-ttu-id="c44c6-120">取得主機提供給服務 i/o 要求的執行緒數目下限。</span><span class="sxs-lookup"><span data-stu-id="c44c6-120">Gets the minimum number of threads that the host provides to service I/O requests.</span></span>|  
|[<span data-ttu-id="c44c6-121">InitializeHostOverlapped 方法</span><span class="sxs-lookup"><span data-stu-id="c44c6-121">InitializeHostOverlapped Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)|<span data-ttu-id="c44c6-122">提供主機初始化 i/o 要求之任何自訂資料的機會。</span><span class="sxs-lookup"><span data-stu-id="c44c6-122">Provides the host with an opportunity to initialize any custom data about an I/O request.</span></span>|  
|[<span data-ttu-id="c44c6-123">SetCLRIoCompletionManager 方法</span><span class="sxs-lookup"><span data-stu-id="c44c6-123">SetCLRIoCompletionManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setclriocompletionmanager-method.md)|<span data-ttu-id="c44c6-124">提供具有 CLR 所實[ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)實例之介面指標的主機。</span><span class="sxs-lookup"><span data-stu-id="c44c6-124">Provides the host with an interface pointer to an [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implemented by the CLR.</span></span>|  
|[<span data-ttu-id="c44c6-125">SetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="c44c6-125">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)|<span data-ttu-id="c44c6-126">設定主機 allots 至服務 i/o 要求的執行緒數目上限。</span><span class="sxs-lookup"><span data-stu-id="c44c6-126">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>|  
|[<span data-ttu-id="c44c6-127">SetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="c44c6-127">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setminthreads-method.md)|<span data-ttu-id="c44c6-128">設定主機應該為 i/o 完成所配置的執行緒數目下限。</span><span class="sxs-lookup"><span data-stu-id="c44c6-128">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c44c6-129">備註</span><span class="sxs-lookup"><span data-stu-id="c44c6-129">Remarks</span></span>  
 <span data-ttu-id="c44c6-130">`IHostIoCompletionManager` 對應至 CLR 所實的 `ICLRIoCompletionManager` 介面。</span><span class="sxs-lookup"><span data-stu-id="c44c6-130">`IHostIoCompletionManager` corresponds to the `ICLRIoCompletionManager` interface implemented by the CLR.</span></span> <span data-ttu-id="c44c6-131">CLR 會呼叫 `IHostIoCompletionManager` 的方法，將控制碼系結至主機提供的埠，而主機則會呼叫 `ICLRIoCompletionManager` 的方法，以報告 i/o 要求的完成。</span><span class="sxs-lookup"><span data-stu-id="c44c6-131">The CLR calls the methods of `IHostIoCompletionManager` to bind handles to the ports that the host provides, and the host calls the methods of `ICLRIoCompletionManager` to report the completion of I/O requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c44c6-132">需求</span><span class="sxs-lookup"><span data-stu-id="c44c6-132">Requirements</span></span>  
 <span data-ttu-id="c44c6-133">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c44c6-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c44c6-134">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="c44c6-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c44c6-135">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c44c6-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c44c6-136">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c44c6-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c44c6-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="c44c6-137">See also</span></span>

- [<span data-ttu-id="c44c6-138">裝載介面</span><span class="sxs-lookup"><span data-stu-id="c44c6-138">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
