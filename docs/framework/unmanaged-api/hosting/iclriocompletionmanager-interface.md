---
title: ICLRIoCompletionManager 介面
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager
helpviewer_keywords:
- ICLRIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c6c3ace6-e5e7-4450-8cc5-a9a48208c493
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b71c177c7c0cb029fb7cfa734f54c87abf20b348
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557834"
---
# <a name="iclriocompletionmanager-interface"></a><span data-ttu-id="a1586-102">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="a1586-102">ICLRIoCompletionManager Interface</span></span>
<span data-ttu-id="a1586-103">實作回呼方法，讓以通知 common language runtime (CLR) 主機狀態的指定的 I/O 要求。</span><span class="sxs-lookup"><span data-stu-id="a1586-103">Implements a callback method that allows the host to notify the common language runtime (CLR) of the status of specified I/O requests.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a1586-104">方法</span><span class="sxs-lookup"><span data-stu-id="a1586-104">Methods</span></span>  
  
|<span data-ttu-id="a1586-105">方法</span><span class="sxs-lookup"><span data-stu-id="a1586-105">Method</span></span>|<span data-ttu-id="a1586-106">描述</span><span class="sxs-lookup"><span data-stu-id="a1586-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a1586-107">OnComplete 方法</span><span class="sxs-lookup"><span data-stu-id="a1586-107">OnComplete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)|<span data-ttu-id="a1586-108">通知狀態的 I/O 要求所使用的呼叫 CLR [ihostiocompletionmanager:: Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="a1586-108">Notifies the CLR of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1586-109">備註</span><span class="sxs-lookup"><span data-stu-id="a1586-109">Remarks</span></span>  
 <span data-ttu-id="a1586-110">主機實作的方式，使用 I/O 完成抽象[IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="a1586-110">The host implements the I/O completion abstraction by using the [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) interface.</span></span> <span data-ttu-id="a1586-111">透過這個介面，CLR 會提出的 I/O 要求和主應用程式通知執行階段的這類要求的結果使用`ICLRIoCompletionManager`介面。</span><span class="sxs-lookup"><span data-stu-id="a1586-111">The CLR makes I/O requests through this interface, and the host notifies the runtime of the outcome of such requests by using the `ICLRIoCompletionManager` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1586-112">需求</span><span class="sxs-lookup"><span data-stu-id="a1586-112">Requirements</span></span>  
 <span data-ttu-id="a1586-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a1586-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1586-114">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a1586-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a1586-115">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a1586-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a1586-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1586-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1586-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1586-117">See also</span></span>
- [<span data-ttu-id="a1586-118">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="a1586-118">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="a1586-119">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="a1586-119">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
- [<span data-ttu-id="a1586-120">裝載介面</span><span class="sxs-lookup"><span data-stu-id="a1586-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
