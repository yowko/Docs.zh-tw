---
title: "IGCThreadControl 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCThreadControl
api_location: mscoree.dll
api_type: COM
f1_keywords: IGCThreadControl
helpviewer_keywords: IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 3ff04d75-85ac-4df9-886d-dbaa037c0552
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: def6ae3c8bf8eea9cb135529e2b6e672b180e68c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="igcthreadcontrol-interface"></a><span data-ttu-id="9db6d-102">IGCThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="9db6d-102">IGCThreadControl Interface</span></span>
<span data-ttu-id="9db6d-103">提供方法來參與，否則記憶體回收會封鎖執行緒的排程。</span><span class="sxs-lookup"><span data-stu-id="9db6d-103">Provides methods for participating in the scheduling of threads that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9db6d-104">方法</span><span class="sxs-lookup"><span data-stu-id="9db6d-104">Methods</span></span>  
  
|<span data-ttu-id="9db6d-105">方法</span><span class="sxs-lookup"><span data-stu-id="9db6d-105">Method</span></span>|<span data-ttu-id="9db6d-106">描述</span><span class="sxs-lookup"><span data-stu-id="9db6d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9db6d-107">SuspensionEnding 方法</span><span class="sxs-lookup"><span data-stu-id="9db6d-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionending-method.md)|<span data-ttu-id="9db6d-108">通知主機執行階段會在記憶體回收或其他暫止後繼續處理執行緒。</span><span class="sxs-lookup"><span data-stu-id="9db6d-108">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="9db6d-109">SuspensionStarting 方法</span><span class="sxs-lookup"><span data-stu-id="9db6d-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionstarting-method.md)|<span data-ttu-id="9db6d-110">通知記憶體回收執行緒暫止或其他暫停，正在開始執行階段主應用程式。</span><span class="sxs-lookup"><span data-stu-id="9db6d-110">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="9db6d-111">ThreadIsBlockingForSuspension 方法</span><span class="sxs-lookup"><span data-stu-id="9db6d-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md)|<span data-ttu-id="9db6d-112">通知主機進行呼叫的執行緒即將封鎖，可能是記憶體回收集合或其他暫止。</span><span class="sxs-lookup"><span data-stu-id="9db6d-112">Notifies the host that the thread making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9db6d-113">需求</span><span class="sxs-lookup"><span data-stu-id="9db6d-113">Requirements</span></span>  
 <span data-ttu-id="9db6d-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9db6d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9db6d-115">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9db6d-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9db6d-116">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9db6d-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9db6d-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9db6d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9db6d-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="9db6d-118">See Also</span></span>  
 [<span data-ttu-id="9db6d-119">裝載介面</span><span class="sxs-lookup"><span data-stu-id="9db6d-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
