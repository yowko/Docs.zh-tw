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
ms.openlocfilehash: 02facbb0ff1c0f8978d4f4f720ab370f70f07fe2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721682"
---
# <a name="igcthreadcontrol-interface"></a><span data-ttu-id="986d7-102">IGCThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="986d7-102">IGCThreadControl Interface</span></span>

<span data-ttu-id="986d7-103">提供方法來參與執行緒的排程，而這些執行緒會被封鎖，以進行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="986d7-103">Provides methods for participating in the scheduling of threads that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="986d7-104">方法</span><span class="sxs-lookup"><span data-stu-id="986d7-104">Methods</span></span>  
  
|<span data-ttu-id="986d7-105">方法</span><span class="sxs-lookup"><span data-stu-id="986d7-105">Method</span></span>|<span data-ttu-id="986d7-106">描述</span><span class="sxs-lookup"><span data-stu-id="986d7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="986d7-107">SuspensionEnding 方法</span><span class="sxs-lookup"><span data-stu-id="986d7-107">SuspensionEnding Method</span></span>](igcthreadcontrol-suspensionending-method.md)|<span data-ttu-id="986d7-108">通知主機執行時間在垃圾收集或其他暫停之後繼續執行緒。</span><span class="sxs-lookup"><span data-stu-id="986d7-108">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="986d7-109">SuspensionStarting 方法</span><span class="sxs-lookup"><span data-stu-id="986d7-109">SuspensionStarting Method</span></span>](igcthreadcontrol-suspensionstarting-method.md)|<span data-ttu-id="986d7-110">通知主機執行時間正在等待垃圾收集或其他暫止的執行緒暫停。</span><span class="sxs-lookup"><span data-stu-id="986d7-110">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="986d7-111">ThreadIsBlockingForSuspension 方法</span><span class="sxs-lookup"><span data-stu-id="986d7-111">ThreadIsBlockingForSuspension Method</span></span>](igcthreadcontrol-threadisblockingforsuspension-method.md)|<span data-ttu-id="986d7-112">通知主機發出呼叫的執行緒即將封鎖，或許是針對垃圾收集或其他擱置。</span><span class="sxs-lookup"><span data-stu-id="986d7-112">Notifies the host that the thread making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="986d7-113">需求</span><span class="sxs-lookup"><span data-stu-id="986d7-113">Requirements</span></span>  

 <span data-ttu-id="986d7-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="986d7-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="986d7-115">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="986d7-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="986d7-116">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="986d7-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="986d7-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="986d7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="986d7-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="986d7-118">See also</span></span>

- [<span data-ttu-id="986d7-119">裝載介面</span><span class="sxs-lookup"><span data-stu-id="986d7-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
