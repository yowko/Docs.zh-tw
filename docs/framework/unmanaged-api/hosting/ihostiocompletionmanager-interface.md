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
ms.openlocfilehash: 75ad8670008242008aa344835143ff9b2add0a6c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719589"
---
# <a name="ihostiocompletionmanager-interface"></a><span data-ttu-id="9963b-102">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="9963b-102">IHostIoCompletionManager Interface</span></span>

<span data-ttu-id="9963b-103">提供方法，讓 common language runtime (CLR) 與主機所提供的 i/o 完成埠互動。</span><span class="sxs-lookup"><span data-stu-id="9963b-103">Provides methods that allow the common language runtime (CLR) to interact with I/O completion ports provided by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9963b-104">方法</span><span class="sxs-lookup"><span data-stu-id="9963b-104">Methods</span></span>  
  
|<span data-ttu-id="9963b-105">方法</span><span class="sxs-lookup"><span data-stu-id="9963b-105">Method</span></span>|<span data-ttu-id="9963b-106">描述</span><span class="sxs-lookup"><span data-stu-id="9963b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9963b-107">Bind 方法</span><span class="sxs-lookup"><span data-stu-id="9963b-107">Bind Method</span></span>](ihostiocompletionmanager-bind-method.md)|<span data-ttu-id="9963b-108">將控制碼系結至 i/o 完成通訊埠。</span><span class="sxs-lookup"><span data-stu-id="9963b-108">Binds a handle to an I/O completion port.</span></span>|  
|[<span data-ttu-id="9963b-109">CloseIoCompletionPort 方法</span><span class="sxs-lookup"><span data-stu-id="9963b-109">CloseIoCompletionPort Method</span></span>](ihostiocompletionmanager-closeiocompletionport-method.md)|<span data-ttu-id="9963b-110">關閉透過先前的呼叫所建立的埠 `CreateIoCompletionPort` 。</span><span class="sxs-lookup"><span data-stu-id="9963b-110">Closes a port that was created through an earlier call to `CreateIoCompletionPort`.</span></span>|  
|[<span data-ttu-id="9963b-111">CreateIoCompletionPort 方法</span><span class="sxs-lookup"><span data-stu-id="9963b-111">CreateIoCompletionPort Method</span></span>](ihostiocompletionmanager-createiocompletionport-method.md)|<span data-ttu-id="9963b-112">要求主機建立新的 i/o 完成通訊埠。</span><span class="sxs-lookup"><span data-stu-id="9963b-112">Requests that the host create a new I/O completion port.</span></span>|  
|[<span data-ttu-id="9963b-113">GetAvailableThreads 方法</span><span class="sxs-lookup"><span data-stu-id="9963b-113">GetAvailableThreads Method</span></span>](ihostiocompletionmanager-getavailablethreads-method.md)|<span data-ttu-id="9963b-114">取得目前未處理要求的 i/o 完成執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="9963b-114">Gets the number of I/O completion threads that are not currently processing requests.</span></span>|  
|[<span data-ttu-id="9963b-115">GetHostOverlappedSize 方法</span><span class="sxs-lookup"><span data-stu-id="9963b-115">GetHostOverlappedSize Method</span></span>](ihostiocompletionmanager-gethostoverlappedsize-method.md)|<span data-ttu-id="9963b-116">取得主機打算附加至 i/o 要求的任何自訂資料大小。</span><span class="sxs-lookup"><span data-stu-id="9963b-116">Gets the size of any custom data the host intends to append to I/O requests.</span></span>|  
|[<span data-ttu-id="9963b-117">GetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="9963b-117">GetMaxThreads Method</span></span>](ihostiocompletionmanager-getmaxthreads-method.md)|<span data-ttu-id="9963b-118">取得主機可為服務 i/o 要求所分配的最大執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="9963b-118">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>|  
|[<span data-ttu-id="9963b-119">GetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="9963b-119">GetMinThreads Method</span></span>](ihostiocompletionmanager-getminthreads-method.md)|<span data-ttu-id="9963b-120">取得主機提供給服務 i/o 要求的執行緒數目下限。</span><span class="sxs-lookup"><span data-stu-id="9963b-120">Gets the minimum number of threads that the host provides to service I/O requests.</span></span>|  
|[<span data-ttu-id="9963b-121">InitializeHostOverlapped 方法</span><span class="sxs-lookup"><span data-stu-id="9963b-121">InitializeHostOverlapped Method</span></span>](ihostiocompletionmanager-initializehostoverlapped-method.md)|<span data-ttu-id="9963b-122">提供主機有機會初始化任何有關 i/o 要求的自訂資料。</span><span class="sxs-lookup"><span data-stu-id="9963b-122">Provides the host with an opportunity to initialize any custom data about an I/O request.</span></span>|  
|[<span data-ttu-id="9963b-123">SetCLRIoCompletionManager 方法</span><span class="sxs-lookup"><span data-stu-id="9963b-123">SetCLRIoCompletionManager Method</span></span>](ihostiocompletionmanager-setclriocompletionmanager-method.md)|<span data-ttu-id="9963b-124">為主機提供由 CLR 所執行之 [ICLRIoCompletionManager](iclriocompletionmanager-interface.md) 實例的介面指標。</span><span class="sxs-lookup"><span data-stu-id="9963b-124">Provides the host with an interface pointer to an [ICLRIoCompletionManager](iclriocompletionmanager-interface.md) instance implemented by the CLR.</span></span>|  
|[<span data-ttu-id="9963b-125">SetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="9963b-125">SetMaxThreads Method</span></span>](ihostiocompletionmanager-setmaxthreads-method.md)|<span data-ttu-id="9963b-126">設定主機 allots 至服務 i/o 要求的最大執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="9963b-126">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>|  
|[<span data-ttu-id="9963b-127">SetMinThreads 方法</span><span class="sxs-lookup"><span data-stu-id="9963b-127">SetMinThreads Method</span></span>](ihostiocompletionmanager-setminthreads-method.md)|<span data-ttu-id="9963b-128">設定主機應該為 i/o 完成配置的執行緒數目下限。</span><span class="sxs-lookup"><span data-stu-id="9963b-128">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9963b-129">備註</span><span class="sxs-lookup"><span data-stu-id="9963b-129">Remarks</span></span>  

 <span data-ttu-id="9963b-130">`IHostIoCompletionManager` 對應至 `ICLRIoCompletionManager` CLR 所執行的介面。</span><span class="sxs-lookup"><span data-stu-id="9963b-130">`IHostIoCompletionManager` corresponds to the `ICLRIoCompletionManager` interface implemented by the CLR.</span></span> <span data-ttu-id="9963b-131">CLR 會呼叫的方法 `IHostIoCompletionManager` ，將控制碼系結至主機提供的埠，而主機會呼叫的方法， `ICLRIoCompletionManager` 以報告 i/o 要求的完成。</span><span class="sxs-lookup"><span data-stu-id="9963b-131">The CLR calls the methods of `IHostIoCompletionManager` to bind handles to the ports that the host provides, and the host calls the methods of `ICLRIoCompletionManager` to report the completion of I/O requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9963b-132">需求</span><span class="sxs-lookup"><span data-stu-id="9963b-132">Requirements</span></span>  

 <span data-ttu-id="9963b-133">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9963b-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9963b-134">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="9963b-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9963b-135">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="9963b-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9963b-136">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9963b-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9963b-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9963b-137">See also</span></span>

- [<span data-ttu-id="9963b-138">裝載介面</span><span class="sxs-lookup"><span data-stu-id="9963b-138">Hosting Interfaces</span></span>](hosting-interfaces.md)
