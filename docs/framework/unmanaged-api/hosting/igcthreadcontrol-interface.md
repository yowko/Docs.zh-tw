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
ms.openlocfilehash: 78e667acf1573769a1a67b4c964d7801f11838fe
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805120"
---
# <a name="igcthreadcontrol-interface"></a><span data-ttu-id="a2a11-102">IGCThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="a2a11-102">IGCThreadControl Interface</span></span>
<span data-ttu-id="a2a11-103">提供方法來參與執行緒的排程，否則會封鎖垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="a2a11-103">Provides methods for participating in the scheduling of threads that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a2a11-104">方法</span><span class="sxs-lookup"><span data-stu-id="a2a11-104">Methods</span></span>  
  
|<span data-ttu-id="a2a11-105">方法</span><span class="sxs-lookup"><span data-stu-id="a2a11-105">Method</span></span>|<span data-ttu-id="a2a11-106">描述</span><span class="sxs-lookup"><span data-stu-id="a2a11-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a2a11-107">SuspensionEnding 方法</span><span class="sxs-lookup"><span data-stu-id="a2a11-107">SuspensionEnding Method</span></span>](igcthreadcontrol-suspensionending-method.md)|<span data-ttu-id="a2a11-108">通知主機執行時間在垃圾收集或其他暫停之後繼續執行緒。</span><span class="sxs-lookup"><span data-stu-id="a2a11-108">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="a2a11-109">SuspensionStarting 方法</span><span class="sxs-lookup"><span data-stu-id="a2a11-109">SuspensionStarting Method</span></span>](igcthreadcontrol-suspensionstarting-method.md)|<span data-ttu-id="a2a11-110">通知主機執行時間正在中止垃圾收集或其他暫停的執行緒。</span><span class="sxs-lookup"><span data-stu-id="a2a11-110">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="a2a11-111">ThreadIsBlockingForSuspension 方法</span><span class="sxs-lookup"><span data-stu-id="a2a11-111">ThreadIsBlockingForSuspension Method</span></span>](igcthreadcontrol-threadisblockingforsuspension-method.md)|<span data-ttu-id="a2a11-112">通知主機發出呼叫的執行緒即將封鎖，可能是因為垃圾收集或其他暫停。</span><span class="sxs-lookup"><span data-stu-id="a2a11-112">Notifies the host that the thread making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a2a11-113">規格需求</span><span class="sxs-lookup"><span data-stu-id="a2a11-113">Requirements</span></span>  
 <span data-ttu-id="a2a11-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a2a11-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2a11-115">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="a2a11-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a2a11-116">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a2a11-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a2a11-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2a11-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2a11-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2a11-118">See also</span></span>

- [<span data-ttu-id="a2a11-119">裝載介面</span><span class="sxs-lookup"><span data-stu-id="a2a11-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
