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
ms.openlocfilehash: 3b8c9421dea4040a9f183b886f1ad8575cace780
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762421"
---
# <a name="icorconfiguration-interface"></a><span data-ttu-id="ad1e0-102">ICorConfiguration 介面</span><span class="sxs-lookup"><span data-stu-id="ad1e0-102">ICorConfiguration Interface</span></span>
<span data-ttu-id="ad1e0-103">提供設定 common language runtime （CLR）的方法。</span><span class="sxs-lookup"><span data-stu-id="ad1e0-103">Provides methods for configuring the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ad1e0-104">方法</span><span class="sxs-lookup"><span data-stu-id="ad1e0-104">Methods</span></span>  
  
|<span data-ttu-id="ad1e0-105">方法</span><span class="sxs-lookup"><span data-stu-id="ad1e0-105">Method</span></span>|<span data-ttu-id="ad1e0-106">描述</span><span class="sxs-lookup"><span data-stu-id="ad1e0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ad1e0-107">AddDebuggerSpecialThread 方法</span><span class="sxs-lookup"><span data-stu-id="ad1e0-107">AddDebuggerSpecialThread Method</span></span>](icorconfiguration-adddebuggerspecialthread-method.md)|<span data-ttu-id="ad1e0-108">向偵錯工具表示，當偵錯工具在 managed 或非受控的偵測案例中停止時，應該允許特定執行緒繼續執行。</span><span class="sxs-lookup"><span data-stu-id="ad1e0-108">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>|  
|[<span data-ttu-id="ad1e0-109">SetDebuggerThreadControl 方法</span><span class="sxs-lookup"><span data-stu-id="ad1e0-109">SetDebuggerThreadControl Method</span></span>](icorconfiguration-setdebuggerthreadcontrol-method.md)|<span data-ttu-id="ad1e0-110">設定偵錯工具將會呼叫的回呼介面，因為 CLR 執行緒會被封鎖並解除封鎖以進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="ad1e0-110">Sets the callback interface that the debugging services will call as CLR threads are blocked and unblocked for debugging.</span></span>|  
|[<span data-ttu-id="ad1e0-111">SetGCHostControl 方法</span><span class="sxs-lookup"><span data-stu-id="ad1e0-111">SetGCHostControl Method</span></span>](icorconfiguration-setgchostcontrol-method.md)|<span data-ttu-id="ad1e0-112">設定要由垃圾收集行程用來要求主控制項變更虛擬記憶體限制的回呼介面。</span><span class="sxs-lookup"><span data-stu-id="ad1e0-112">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>|  
|[<span data-ttu-id="ad1e0-113">SetGCThreadControl 方法</span><span class="sxs-lookup"><span data-stu-id="ad1e0-113">SetGCThreadControl Method</span></span>](icorconfiguration-setgcthreadcontrol-method.md)|<span data-ttu-id="ad1e0-114">設定回呼介面，用於針對非執行時間工作排程執行緒，否則會封鎖垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="ad1e0-114">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ad1e0-115">規格需求</span><span class="sxs-lookup"><span data-stu-id="ad1e0-115">Requirements</span></span>  
 <span data-ttu-id="ad1e0-116">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ad1e0-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad1e0-117">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="ad1e0-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ad1e0-118">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ad1e0-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ad1e0-119">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad1e0-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad1e0-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad1e0-120">See also</span></span>

- [<span data-ttu-id="ad1e0-121">裝載介面</span><span class="sxs-lookup"><span data-stu-id="ad1e0-121">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="ad1e0-122">CorRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="ad1e0-122">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
