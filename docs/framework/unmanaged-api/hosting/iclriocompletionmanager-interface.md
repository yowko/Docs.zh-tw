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
ms.openlocfilehash: 822b51531b7afc1c824c74b9580d9208e347e13b
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703560"
---
# <a name="iclriocompletionmanager-interface"></a><span data-ttu-id="5ac50-102">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="5ac50-102">ICLRIoCompletionManager Interface</span></span>
<span data-ttu-id="5ac50-103">會執行回呼方法，讓主機能夠通知 common language runtime （CLR）所指定 i/o 要求的狀態。</span><span class="sxs-lookup"><span data-stu-id="5ac50-103">Implements a callback method that allows the host to notify the common language runtime (CLR) of the status of specified I/O requests.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5ac50-104">方法</span><span class="sxs-lookup"><span data-stu-id="5ac50-104">Methods</span></span>  
  
|<span data-ttu-id="5ac50-105">方法</span><span class="sxs-lookup"><span data-stu-id="5ac50-105">Method</span></span>|<span data-ttu-id="5ac50-106">描述</span><span class="sxs-lookup"><span data-stu-id="5ac50-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5ac50-107">OnComplete 方法</span><span class="sxs-lookup"><span data-stu-id="5ac50-107">OnComplete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)|<span data-ttu-id="5ac50-108">通知 CLR，這是使用[IHostIoCompletionManager：： Bind](ihostiocompletionmanager-bind-method.md)方法呼叫所提出的 i/o 要求狀態。</span><span class="sxs-lookup"><span data-stu-id="5ac50-108">Notifies the CLR of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](ihostiocompletionmanager-bind-method.md) method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ac50-109">備註</span><span class="sxs-lookup"><span data-stu-id="5ac50-109">Remarks</span></span>  
 <span data-ttu-id="5ac50-110">主機會使用[IHostIoCompletionManager](ihostiocompletionmanager-interface.md)介面來執行 i/o 完成抽象概念。</span><span class="sxs-lookup"><span data-stu-id="5ac50-110">The host implements the I/O completion abstraction by using the [IHostIoCompletionManager](ihostiocompletionmanager-interface.md) interface.</span></span> <span data-ttu-id="5ac50-111">CLR 會透過這個介面提出 i/o 要求，而主機會使用介面來通知執行時間此類要求的結果 `ICLRIoCompletionManager` 。</span><span class="sxs-lookup"><span data-stu-id="5ac50-111">The CLR makes I/O requests through this interface, and the host notifies the runtime of the outcome of such requests by using the `ICLRIoCompletionManager` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ac50-112">需求</span><span class="sxs-lookup"><span data-stu-id="5ac50-112">Requirements</span></span>  
 <span data-ttu-id="5ac50-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5ac50-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ac50-114">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="5ac50-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5ac50-115">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5ac50-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5ac50-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ac50-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ac50-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ac50-117">See also</span></span>

- [<span data-ttu-id="5ac50-118">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="5ac50-118">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="5ac50-119">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="5ac50-119">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
- [<span data-ttu-id="5ac50-120">裝載介面</span><span class="sxs-lookup"><span data-stu-id="5ac50-120">Hosting Interfaces</span></span>](hosting-interfaces.md)
