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
ms.openlocfilehash: c3abb3e80226da909a0c7eb8e4bf54959557dcbf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436263"
---
# <a name="iclriocompletionmanager-interface"></a><span data-ttu-id="d521c-102">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="d521c-102">ICLRIoCompletionManager Interface</span></span>
<span data-ttu-id="d521c-103">實作回呼方法，可讓以通知 common language runtime (CLR) 主機狀態的指定的 I/O 要求。</span><span class="sxs-lookup"><span data-stu-id="d521c-103">Implements a callback method that allows the host to notify the common language runtime (CLR) of the status of specified I/O requests.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d521c-104">方法</span><span class="sxs-lookup"><span data-stu-id="d521c-104">Methods</span></span>  
  
|<span data-ttu-id="d521c-105">方法</span><span class="sxs-lookup"><span data-stu-id="d521c-105">Method</span></span>|<span data-ttu-id="d521c-106">描述</span><span class="sxs-lookup"><span data-stu-id="d521c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d521c-107">OnComplete 方法</span><span class="sxs-lookup"><span data-stu-id="d521c-107">OnComplete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)|<span data-ttu-id="d521c-108">通知狀態的 I/O 要求所使用的呼叫 CLR [ihostiocompletionmanager:: Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="d521c-108">Notifies the CLR of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d521c-109">備註</span><span class="sxs-lookup"><span data-stu-id="d521c-109">Remarks</span></span>  
 <span data-ttu-id="d521c-110">主應用程式使用實作 I/O 完成抽象[IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="d521c-110">The host implements the I/O completion abstraction by using the [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) interface.</span></span> <span data-ttu-id="d521c-111">CLR 會透過這個介面，I/O 要求，並主應用程式使用通知執行階段，這類要求的結果`ICLRIoCompletionManager`介面。</span><span class="sxs-lookup"><span data-stu-id="d521c-111">The CLR makes I/O requests through this interface, and the host notifies the runtime of the outcome of such requests by using the `ICLRIoCompletionManager` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d521c-112">需求</span><span class="sxs-lookup"><span data-stu-id="d521c-112">Requirements</span></span>  
 <span data-ttu-id="d521c-113">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d521c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d521c-114">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d521c-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d521c-115">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d521c-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d521c-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d521c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d521c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d521c-117">See Also</span></span>  
 [<span data-ttu-id="d521c-118">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="d521c-118">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 [<span data-ttu-id="d521c-119">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="d521c-119">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 [<span data-ttu-id="d521c-120">裝載介面</span><span class="sxs-lookup"><span data-stu-id="d521c-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
