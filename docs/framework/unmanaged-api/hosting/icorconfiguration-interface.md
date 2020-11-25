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
ms.openlocfilehash: fa8d15bc8e504a57d5cc87c170a3a5b022798add
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715780"
---
# <a name="icorconfiguration-interface"></a><span data-ttu-id="90e15-102">ICorConfiguration 介面</span><span class="sxs-lookup"><span data-stu-id="90e15-102">ICorConfiguration Interface</span></span>

<span data-ttu-id="90e15-103">提供 (CLR) 設定 common language runtime 的方法。</span><span class="sxs-lookup"><span data-stu-id="90e15-103">Provides methods for configuring the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="90e15-104">方法</span><span class="sxs-lookup"><span data-stu-id="90e15-104">Methods</span></span>  
  
|<span data-ttu-id="90e15-105">方法</span><span class="sxs-lookup"><span data-stu-id="90e15-105">Method</span></span>|<span data-ttu-id="90e15-106">描述</span><span class="sxs-lookup"><span data-stu-id="90e15-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="90e15-107">AddDebuggerSpecialThread 方法</span><span class="sxs-lookup"><span data-stu-id="90e15-107">AddDebuggerSpecialThread Method</span></span>](icorconfiguration-adddebuggerspecialthread-method.md)|<span data-ttu-id="90e15-108">向偵錯工具表示，當偵錯工具在 managed 或非受控的偵測情節中停止應用程式時，應該允許特定執行緒繼續執行。</span><span class="sxs-lookup"><span data-stu-id="90e15-108">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>|  
|[<span data-ttu-id="90e15-109">SetDebuggerThreadControl 方法</span><span class="sxs-lookup"><span data-stu-id="90e15-109">SetDebuggerThreadControl Method</span></span>](icorconfiguration-setdebuggerthreadcontrol-method.md)|<span data-ttu-id="90e15-110">設定偵錯工具將呼叫的回呼介面，因為 CLR 執行緒會被封鎖和解除封鎖以進行偵測。</span><span class="sxs-lookup"><span data-stu-id="90e15-110">Sets the callback interface that the debugging services will call as CLR threads are blocked and unblocked for debugging.</span></span>|  
|[<span data-ttu-id="90e15-111">SetGCHostControl 方法</span><span class="sxs-lookup"><span data-stu-id="90e15-111">SetGCHostControl Method</span></span>](icorconfiguration-setgchostcontrol-method.md)|<span data-ttu-id="90e15-112">設定要由垃圾收集行程用來要求主控制項變更虛擬記憶體限制的回呼介面。</span><span class="sxs-lookup"><span data-stu-id="90e15-112">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>|  
|[<span data-ttu-id="90e15-113">SetGCThreadControl 方法</span><span class="sxs-lookup"><span data-stu-id="90e15-113">SetGCThreadControl Method</span></span>](icorconfiguration-setgcthreadcontrol-method.md)|<span data-ttu-id="90e15-114">設定回呼介面，以排程非執行時間工作的執行緒，否則將會遭到封鎖，以進行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="90e15-114">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="90e15-115">需求</span><span class="sxs-lookup"><span data-stu-id="90e15-115">Requirements</span></span>  

 <span data-ttu-id="90e15-116">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="90e15-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90e15-117">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="90e15-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="90e15-118">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="90e15-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="90e15-119">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90e15-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90e15-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90e15-120">See also</span></span>

- [<span data-ttu-id="90e15-121">裝載介面</span><span class="sxs-lookup"><span data-stu-id="90e15-121">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="90e15-122">CorRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="90e15-122">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
