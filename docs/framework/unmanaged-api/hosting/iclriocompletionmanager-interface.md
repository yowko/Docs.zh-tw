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
ms.openlocfilehash: e23675351e1fd0de510243c9ee8b3a6dd6f29cec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714116"
---
# <a name="iclriocompletionmanager-interface"></a><span data-ttu-id="799d0-102">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="799d0-102">ICLRIoCompletionManager Interface</span></span>

<span data-ttu-id="799d0-103">執行回呼方法，這個方法可讓主機通知 common language runtime (CLR) 指定的 i/o 要求的狀態。</span><span class="sxs-lookup"><span data-stu-id="799d0-103">Implements a callback method that allows the host to notify the common language runtime (CLR) of the status of specified I/O requests.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="799d0-104">方法</span><span class="sxs-lookup"><span data-stu-id="799d0-104">Methods</span></span>  
  
|<span data-ttu-id="799d0-105">方法</span><span class="sxs-lookup"><span data-stu-id="799d0-105">Method</span></span>|<span data-ttu-id="799d0-106">描述</span><span class="sxs-lookup"><span data-stu-id="799d0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="799d0-107">OnComplete 方法</span><span class="sxs-lookup"><span data-stu-id="799d0-107">OnComplete Method</span></span>](iclriocompletionmanager-oncomplete-method.md)|<span data-ttu-id="799d0-108">使用 [IHostIoCompletionManager：： Bind](ihostiocompletionmanager-bind-method.md) 方法的呼叫，將發出的 i/o 要求狀態通知 CLR。</span><span class="sxs-lookup"><span data-stu-id="799d0-108">Notifies the CLR of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](ihostiocompletionmanager-bind-method.md) method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="799d0-109">備註</span><span class="sxs-lookup"><span data-stu-id="799d0-109">Remarks</span></span>  

 <span data-ttu-id="799d0-110">主機會使用 [IHostIoCompletionManager](ihostiocompletionmanager-interface.md) 介面來執行 i/o 完成抽象概念。</span><span class="sxs-lookup"><span data-stu-id="799d0-110">The host implements the I/O completion abstraction by using the [IHostIoCompletionManager](ihostiocompletionmanager-interface.md) interface.</span></span> <span data-ttu-id="799d0-111">CLR 會透過這個介面提出 i/o 要求，且主機會使用介面，通知執行時間結果這類要求的結果 `ICLRIoCompletionManager` 。</span><span class="sxs-lookup"><span data-stu-id="799d0-111">The CLR makes I/O requests through this interface, and the host notifies the runtime of the outcome of such requests by using the `ICLRIoCompletionManager` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="799d0-112">需求</span><span class="sxs-lookup"><span data-stu-id="799d0-112">Requirements</span></span>  

 <span data-ttu-id="799d0-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="799d0-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="799d0-114">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="799d0-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="799d0-115">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="799d0-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="799d0-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="799d0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="799d0-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="799d0-117">See also</span></span>

- [<span data-ttu-id="799d0-118">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="799d0-118">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="799d0-119">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="799d0-119">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
- [<span data-ttu-id="799d0-120">裝載介面</span><span class="sxs-lookup"><span data-stu-id="799d0-120">Hosting Interfaces</span></span>](hosting-interfaces.md)
