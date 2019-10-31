---
title: IGCThreadControl 介面
ms.date: 03/30/2017
api_name:
- IGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCThreadControl
helpviewer_keywords:
- IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 3ff04d75-85ac-4df9-886d-dbaa037c0552
topic_type:
- apiref
ms.openlocfilehash: 3aba31f60af25144b9f01aa9ca8cc633d4c1a438
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134806"
---
# <a name="igcthreadcontrol-interface"></a><span data-ttu-id="4d4d5-102">IGCThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="4d4d5-102">IGCThreadControl Interface</span></span>
<span data-ttu-id="4d4d5-103">提供方法來參與執行緒的排程，否則會封鎖垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="4d4d5-103">Provides methods for participating in the scheduling of threads that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4d4d5-104">方法</span><span class="sxs-lookup"><span data-stu-id="4d4d5-104">Methods</span></span>  
  
|<span data-ttu-id="4d4d5-105">方法</span><span class="sxs-lookup"><span data-stu-id="4d4d5-105">Method</span></span>|<span data-ttu-id="4d4d5-106">描述</span><span class="sxs-lookup"><span data-stu-id="4d4d5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4d4d5-107">SuspensionEnding 方法</span><span class="sxs-lookup"><span data-stu-id="4d4d5-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionending-method.md)|<span data-ttu-id="4d4d5-108">通知主機執行時間在垃圾收集或其他暫停之後繼續執行緒。</span><span class="sxs-lookup"><span data-stu-id="4d4d5-108">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="4d4d5-109">SuspensionStarting 方法</span><span class="sxs-lookup"><span data-stu-id="4d4d5-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionstarting-method.md)|<span data-ttu-id="4d4d5-110">通知主機執行時間正在中止垃圾收集或其他暫停的執行緒。</span><span class="sxs-lookup"><span data-stu-id="4d4d5-110">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="4d4d5-111">ThreadIsBlockingForSuspension 方法</span><span class="sxs-lookup"><span data-stu-id="4d4d5-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md)|<span data-ttu-id="4d4d5-112">通知主機發出呼叫的執行緒即將封鎖，可能是因為垃圾收集或其他暫停。</span><span class="sxs-lookup"><span data-stu-id="4d4d5-112">Notifies the host that the thread making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4d4d5-113">需求</span><span class="sxs-lookup"><span data-stu-id="4d4d5-113">Requirements</span></span>  
 <span data-ttu-id="4d4d5-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4d5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d4d5-115">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="4d4d5-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4d4d5-116">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4d4d5-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4d4d5-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d4d5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d4d5-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="4d4d5-118">See also</span></span>

- [<span data-ttu-id="4d4d5-119">裝載介面</span><span class="sxs-lookup"><span data-stu-id="4d4d5-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
