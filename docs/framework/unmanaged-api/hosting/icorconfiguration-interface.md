---
title: "ICorConfiguration 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorConfiguration
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorConfiguration
helpviewer_keywords: ICorConfiguration interface [.NET Framework hosting]
ms.assetid: aaf96116-372b-4538-afb1-9e0fcdac1f98
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6bc66abf28e90d858d993bd62e9c67f840af137b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorconfiguration-interface"></a><span data-ttu-id="10d6b-102">ICorConfiguration 介面</span><span class="sxs-lookup"><span data-stu-id="10d6b-102">ICorConfiguration Interface</span></span>
<span data-ttu-id="10d6b-103">提供方法來設定 common language runtime (CLR)。</span><span class="sxs-lookup"><span data-stu-id="10d6b-103">Provides methods for configuring the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="10d6b-104">方法</span><span class="sxs-lookup"><span data-stu-id="10d6b-104">Methods</span></span>  
  
|<span data-ttu-id="10d6b-105">方法</span><span class="sxs-lookup"><span data-stu-id="10d6b-105">Method</span></span>|<span data-ttu-id="10d6b-106">說明</span><span class="sxs-lookup"><span data-stu-id="10d6b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="10d6b-107">AddDebuggerSpecialThread 方法</span><span class="sxs-lookup"><span data-stu-id="10d6b-107">AddDebuggerSpecialThread Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-adddebuggerspecialthread-method.md)|<span data-ttu-id="10d6b-108">表示特定執行緒應該可以繼續執行，而偵錯工具有 managed 或 unmanaged 偵錯案例期間停止一個應用程式執行偵錯服務。</span><span class="sxs-lookup"><span data-stu-id="10d6b-108">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>|  
|[<span data-ttu-id="10d6b-109">SetDebuggerThreadControl 方法</span><span class="sxs-lookup"><span data-stu-id="10d6b-109">SetDebuggerThreadControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setdebuggerthreadcontrol-method.md)|<span data-ttu-id="10d6b-110">設定偵錯服務會針對偵錯呼叫封鎖及解除封鎖 CLR 執行緒時的回呼介面。</span><span class="sxs-lookup"><span data-stu-id="10d6b-110">Sets the callback interface that the debugging services will call as CLR threads are blocked and unblocked for debugging.</span></span>|  
|[<span data-ttu-id="10d6b-111">SetGCHostControl 方法</span><span class="sxs-lookup"><span data-stu-id="10d6b-111">SetGCHostControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgchostcontrol-method.md)|<span data-ttu-id="10d6b-112">設定用於記憶體回收行程所要求的主機，若要變更的虛擬記憶體限制的回呼介面。</span><span class="sxs-lookup"><span data-stu-id="10d6b-112">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>|  
|[<span data-ttu-id="10d6b-113">SetGCThreadControl 方法</span><span class="sxs-lookup"><span data-stu-id="10d6b-113">SetGCThreadControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgcthreadcontrol-method.md)|<span data-ttu-id="10d6b-114">設定排程執行緒非執行階段工作，否則會封鎖記憶體回收的回呼介面。</span><span class="sxs-lookup"><span data-stu-id="10d6b-114">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="10d6b-115">需求</span><span class="sxs-lookup"><span data-stu-id="10d6b-115">Requirements</span></span>  
 <span data-ttu-id="10d6b-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="10d6b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10d6b-117">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="10d6b-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="10d6b-118">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="10d6b-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="10d6b-119">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10d6b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10d6b-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10d6b-120">See Also</span></span>  
 [<span data-ttu-id="10d6b-121">裝載介面</span><span class="sxs-lookup"><span data-stu-id="10d6b-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="10d6b-122">CorRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="10d6b-122">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
