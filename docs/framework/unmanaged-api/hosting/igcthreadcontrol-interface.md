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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5c00f401bedc1a2810c4e9b3046a45e53a79f1ea
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134260"
---
# <a name="igcthreadcontrol-interface"></a><span data-ttu-id="98245-102">IGCThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="98245-102">IGCThreadControl Interface</span></span>
<span data-ttu-id="98245-103">提供方法來參與，否則記憶體回收會封鎖執行緒的排程。</span><span class="sxs-lookup"><span data-stu-id="98245-103">Provides methods for participating in the scheduling of threads that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="98245-104">方法</span><span class="sxs-lookup"><span data-stu-id="98245-104">Methods</span></span>  
  
|<span data-ttu-id="98245-105">方法</span><span class="sxs-lookup"><span data-stu-id="98245-105">Method</span></span>|<span data-ttu-id="98245-106">描述</span><span class="sxs-lookup"><span data-stu-id="98245-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="98245-107">SuspensionEnding 方法</span><span class="sxs-lookup"><span data-stu-id="98245-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionending-method.md)|<span data-ttu-id="98245-108">主應用程式執行階段會進行記憶體回收或其他暫止後繼續處理執行緒。</span><span class="sxs-lookup"><span data-stu-id="98245-108">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="98245-109">SuspensionStarting 方法</span><span class="sxs-lookup"><span data-stu-id="98245-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionstarting-method.md)|<span data-ttu-id="98245-110">通知記憶體回收執行緒暫止或其他暫停，正在開始執行階段主應用程式。</span><span class="sxs-lookup"><span data-stu-id="98245-110">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="98245-111">ThreadIsBlockingForSuspension 方法</span><span class="sxs-lookup"><span data-stu-id="98245-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md)|<span data-ttu-id="98245-112">主應用程式進行呼叫的執行緒即將封鎖，可能是記憶體回收或其他暫止。</span><span class="sxs-lookup"><span data-stu-id="98245-112">Notifies the host that the thread making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="98245-113">需求</span><span class="sxs-lookup"><span data-stu-id="98245-113">Requirements</span></span>  
 <span data-ttu-id="98245-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="98245-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98245-115">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="98245-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="98245-116">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="98245-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="98245-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98245-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98245-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98245-118">See also</span></span>

- [<span data-ttu-id="98245-119">裝載介面</span><span class="sxs-lookup"><span data-stu-id="98245-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
