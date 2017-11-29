---
title: "ICLRIoCompletionManager 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRIoCompletionManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRIoCompletionManager
helpviewer_keywords: ICLRIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c6c3ace6-e5e7-4450-8cc5-a9a48208c493
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dbff3c39da2a18ab45f0ea03d1e1588aa61c7c3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclriocompletionmanager-interface"></a><span data-ttu-id="572f3-102">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="572f3-102">ICLRIoCompletionManager Interface</span></span>
<span data-ttu-id="572f3-103">實作回呼方法，可讓以通知 common language runtime (CLR) 主機狀態的指定的 I/O 要求。</span><span class="sxs-lookup"><span data-stu-id="572f3-103">Implements a callback method that allows the host to notify the common language runtime (CLR) of the status of specified I/O requests.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="572f3-104">方法</span><span class="sxs-lookup"><span data-stu-id="572f3-104">Methods</span></span>  
  
|<span data-ttu-id="572f3-105">方法</span><span class="sxs-lookup"><span data-stu-id="572f3-105">Method</span></span>|<span data-ttu-id="572f3-106">說明</span><span class="sxs-lookup"><span data-stu-id="572f3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="572f3-107">OnComplete 方法</span><span class="sxs-lookup"><span data-stu-id="572f3-107">OnComplete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)|<span data-ttu-id="572f3-108">通知狀態的 I/O 要求所使用的呼叫 CLR [ihostiocompletionmanager:: Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="572f3-108">Notifies the CLR of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="572f3-109">備註</span><span class="sxs-lookup"><span data-stu-id="572f3-109">Remarks</span></span>  
 <span data-ttu-id="572f3-110">主應用程式使用實作 I/O 完成抽象[IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="572f3-110">The host implements the I/O completion abstraction by using the [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) interface.</span></span> <span data-ttu-id="572f3-111">CLR 會透過這個介面，I/O 要求，並主應用程式使用通知執行階段，這類要求的結果`ICLRIoCompletionManager`介面。</span><span class="sxs-lookup"><span data-stu-id="572f3-111">The CLR makes I/O requests through this interface, and the host notifies the runtime of the outcome of such requests by using the `ICLRIoCompletionManager` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="572f3-112">需求</span><span class="sxs-lookup"><span data-stu-id="572f3-112">Requirements</span></span>  
 <span data-ttu-id="572f3-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="572f3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="572f3-114">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="572f3-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="572f3-115">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="572f3-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="572f3-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="572f3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="572f3-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="572f3-117">See Also</span></span>  
 [<span data-ttu-id="572f3-118">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="572f3-118">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 [<span data-ttu-id="572f3-119">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="572f3-119">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 [<span data-ttu-id="572f3-120">裝載介面</span><span class="sxs-lookup"><span data-stu-id="572f3-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
