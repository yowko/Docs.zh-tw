---
title: ICorConfiguration 介面
ms.date: 03/30/2017
api_name:
- ICorConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorConfiguration
helpviewer_keywords:
- ICorConfiguration interface [.NET Framework hosting]
ms.assetid: aaf96116-372b-4538-afb1-9e0fcdac1f98
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d7abd6b4ca97173cfecbabf1a8b90afcf3c48a1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54554175"
---
# <a name="icorconfiguration-interface"></a><span data-ttu-id="d8b39-102">ICorConfiguration 介面</span><span class="sxs-lookup"><span data-stu-id="d8b39-102">ICorConfiguration Interface</span></span>
<span data-ttu-id="d8b39-103">提供用於設定 common language runtime (CLR) 方法。</span><span class="sxs-lookup"><span data-stu-id="d8b39-103">Provides methods for configuring the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d8b39-104">方法</span><span class="sxs-lookup"><span data-stu-id="d8b39-104">Methods</span></span>  
  
|<span data-ttu-id="d8b39-105">方法</span><span class="sxs-lookup"><span data-stu-id="d8b39-105">Method</span></span>|<span data-ttu-id="d8b39-106">描述</span><span class="sxs-lookup"><span data-stu-id="d8b39-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d8b39-107">AddDebuggerSpecialThread 方法</span><span class="sxs-lookup"><span data-stu-id="d8b39-107">AddDebuggerSpecialThread Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-adddebuggerspecialthread-method.md)|<span data-ttu-id="d8b39-108">表示特定的執行緒都應該可以繼續執行，而偵錯工具已在 managed 或 unmanaged 偵錯的情況下停止應用程式執行偵錯服務。</span><span class="sxs-lookup"><span data-stu-id="d8b39-108">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>|  
|[<span data-ttu-id="d8b39-109">SetDebuggerThreadControl 方法</span><span class="sxs-lookup"><span data-stu-id="d8b39-109">SetDebuggerThreadControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setdebuggerthreadcontrol-method.md)|<span data-ttu-id="d8b39-110">設定偵錯的服務會針對偵錯呼叫封鎖及解除封鎖 CLR 執行緒時的回呼介面。</span><span class="sxs-lookup"><span data-stu-id="d8b39-110">Sets the callback interface that the debugging services will call as CLR threads are blocked and unblocked for debugging.</span></span>|  
|[<span data-ttu-id="d8b39-111">SetGCHostControl 方法</span><span class="sxs-lookup"><span data-stu-id="d8b39-111">SetGCHostControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgchostcontrol-method.md)|<span data-ttu-id="d8b39-112">設定要求的主機，若要變更虛擬記憶體的限制，記憶體回收行程所使用的回呼介面。</span><span class="sxs-lookup"><span data-stu-id="d8b39-112">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>|  
|[<span data-ttu-id="d8b39-113">SetGCThreadControl 方法</span><span class="sxs-lookup"><span data-stu-id="d8b39-113">SetGCThreadControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgcthreadcontrol-method.md)|<span data-ttu-id="d8b39-114">設定排程執行緒非執行階段工作，否則會封鎖記憶體回收的回呼介面。</span><span class="sxs-lookup"><span data-stu-id="d8b39-114">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d8b39-115">需求</span><span class="sxs-lookup"><span data-stu-id="d8b39-115">Requirements</span></span>  
 <span data-ttu-id="d8b39-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d8b39-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8b39-117">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d8b39-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d8b39-118">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d8b39-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d8b39-119">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8b39-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8b39-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8b39-120">See also</span></span>
- [<span data-ttu-id="d8b39-121">裝載介面</span><span class="sxs-lookup"><span data-stu-id="d8b39-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="d8b39-122">CorRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="d8b39-122">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
