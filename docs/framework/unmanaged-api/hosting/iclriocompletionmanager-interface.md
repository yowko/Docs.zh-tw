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
ms.openlocfilehash: b63d4269a8d48ee49016a4c51d63bf81bdba8da2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141025"
---
# <a name="iclriocompletionmanager-interface"></a><span data-ttu-id="2f234-102">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="2f234-102">ICLRIoCompletionManager Interface</span></span>
<span data-ttu-id="2f234-103">會執行回呼方法，讓主機能夠通知 common language runtime （CLR）所指定 i/o 要求的狀態。</span><span class="sxs-lookup"><span data-stu-id="2f234-103">Implements a callback method that allows the host to notify the common language runtime (CLR) of the status of specified I/O requests.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2f234-104">方法</span><span class="sxs-lookup"><span data-stu-id="2f234-104">Methods</span></span>  
  
|<span data-ttu-id="2f234-105">方法</span><span class="sxs-lookup"><span data-stu-id="2f234-105">Method</span></span>|<span data-ttu-id="2f234-106">描述</span><span class="sxs-lookup"><span data-stu-id="2f234-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2f234-107">OnComplete 方法</span><span class="sxs-lookup"><span data-stu-id="2f234-107">OnComplete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)|<span data-ttu-id="2f234-108">通知 CLR，這是使用[IHostIoCompletionManager：： Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)方法呼叫所提出的 i/o 要求狀態。</span><span class="sxs-lookup"><span data-stu-id="2f234-108">Notifies the CLR of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f234-109">備註</span><span class="sxs-lookup"><span data-stu-id="2f234-109">Remarks</span></span>  
 <span data-ttu-id="2f234-110">主機會使用[IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)介面來執行 i/o 完成抽象概念。</span><span class="sxs-lookup"><span data-stu-id="2f234-110">The host implements the I/O completion abstraction by using the [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) interface.</span></span> <span data-ttu-id="2f234-111">CLR 會透過這個介面提出 i/o 要求，而主機會使用 `ICLRIoCompletionManager` 介面來通知執行時間此類要求的結果。</span><span class="sxs-lookup"><span data-stu-id="2f234-111">The CLR makes I/O requests through this interface, and the host notifies the runtime of the outcome of such requests by using the `ICLRIoCompletionManager` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f234-112">需求</span><span class="sxs-lookup"><span data-stu-id="2f234-112">Requirements</span></span>  
 <span data-ttu-id="2f234-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2f234-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f234-114">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="2f234-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2f234-115">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2f234-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2f234-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f234-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f234-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="2f234-117">See also</span></span>

- [<span data-ttu-id="2f234-118">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="2f234-118">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="2f234-119">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="2f234-119">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
- [<span data-ttu-id="2f234-120">裝載介面</span><span class="sxs-lookup"><span data-stu-id="2f234-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
