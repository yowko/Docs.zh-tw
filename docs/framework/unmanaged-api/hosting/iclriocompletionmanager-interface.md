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
ms.openlocfilehash: 7864bb81c3b457bf8ec07cd194d24b29a42bd441
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61767464"
---
# <a name="iclriocompletionmanager-interface"></a><span data-ttu-id="808e4-102">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="808e4-102">ICLRIoCompletionManager Interface</span></span>
<span data-ttu-id="808e4-103">實作回呼方法，讓以通知 common language runtime (CLR) 主機狀態的指定的 I/O 要求。</span><span class="sxs-lookup"><span data-stu-id="808e4-103">Implements a callback method that allows the host to notify the common language runtime (CLR) of the status of specified I/O requests.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="808e4-104">方法</span><span class="sxs-lookup"><span data-stu-id="808e4-104">Methods</span></span>  
  
|<span data-ttu-id="808e4-105">方法</span><span class="sxs-lookup"><span data-stu-id="808e4-105">Method</span></span>|<span data-ttu-id="808e4-106">描述</span><span class="sxs-lookup"><span data-stu-id="808e4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="808e4-107">OnComplete 方法</span><span class="sxs-lookup"><span data-stu-id="808e4-107">OnComplete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)|<span data-ttu-id="808e4-108">通知狀態的 I/O 要求所使用的呼叫 CLR [ihostiocompletionmanager:: Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="808e4-108">Notifies the CLR of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="808e4-109">備註</span><span class="sxs-lookup"><span data-stu-id="808e4-109">Remarks</span></span>  
 <span data-ttu-id="808e4-110">主機實作的方式，使用 I/O 完成抽象[IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="808e4-110">The host implements the I/O completion abstraction by using the [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) interface.</span></span> <span data-ttu-id="808e4-111">透過這個介面，CLR 會提出的 I/O 要求和主應用程式通知執行階段的這類要求的結果使用`ICLRIoCompletionManager`介面。</span><span class="sxs-lookup"><span data-stu-id="808e4-111">The CLR makes I/O requests through this interface, and the host notifies the runtime of the outcome of such requests by using the `ICLRIoCompletionManager` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="808e4-112">需求</span><span class="sxs-lookup"><span data-stu-id="808e4-112">Requirements</span></span>  
 <span data-ttu-id="808e4-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="808e4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="808e4-114">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="808e4-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="808e4-115">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="808e4-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="808e4-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="808e4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="808e4-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="808e4-117">See also</span></span>

- [<span data-ttu-id="808e4-118">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="808e4-118">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="808e4-119">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="808e4-119">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
- [<span data-ttu-id="808e4-120">裝載介面</span><span class="sxs-lookup"><span data-stu-id="808e4-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
