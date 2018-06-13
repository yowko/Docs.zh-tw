---
title: illegalPrepareConstrainedRegion MDA
ms.date: 03/30/2017
helpviewer_keywords:
- PrepareConstrainedRegions method
- managed debugging assistants (MDAs), illegal PrepareConstrainedRegions
- try/catch exception handling, managed debugging assistants
- IllegalPrepareConstrainedRegions MDA
- MDAs (managed debugging assistants), illegal PrepareConstrainedRegions
ms.assetid: 2f9b5031-f910-4e01-a196-f89eab313eaf
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 59a2b7f7ed855cd6b7d363ea5d4723c7d7b8d629
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33386349"
---
# <a name="illegalprepareconstrainedregion-mda"></a><span data-ttu-id="4c7d2-102">illegalPrepareConstrainedRegion MDA</span><span class="sxs-lookup"><span data-stu-id="4c7d2-102">illegalPrepareConstrainedRegion MDA</span></span>
<span data-ttu-id="4c7d2-103"><xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> 方法呼叫並未緊接在例外狀況處理常式的 `try` 陳述式前面時，`illegalPrepareConstrainedRegion` Managed 偵錯助理 (MDA) 就會啟動。</span><span class="sxs-lookup"><span data-stu-id="4c7d2-103">The `illegalPrepareConstrainedRegion` managed debugging assistant (MDA) is activated when a <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> method call does not immediately precede the `try` statement of the exception handler.</span></span> <span data-ttu-id="4c7d2-104">這項限制屬於 MSIL 層級，因此可允許在呼叫和 `try` 之間具有不產生程式碼的來源，例如註解。</span><span class="sxs-lookup"><span data-stu-id="4c7d2-104">This restriction is at the MSIL level, so it is permissible to have non-code-generating source between the call and the `try`, such as comments.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="4c7d2-105">徵兆</span><span class="sxs-lookup"><span data-stu-id="4c7d2-105">Symptoms</span></span>  
 <span data-ttu-id="4c7d2-106">限制的執行區域 (CER) 永遠不會被視為這類執行區執，而是當成簡單的例外狀況處理區塊 (`finally` 或`catch`)。</span><span class="sxs-lookup"><span data-stu-id="4c7d2-106">A constrained execution region (CER) that is never treated as such, but as a simple exception handling block (`finally` or `catch`).</span></span> <span data-ttu-id="4c7d2-107">因此，這個區域不會在發生記憶體不足狀況或執行緒中止的情況下執行。</span><span class="sxs-lookup"><span data-stu-id="4c7d2-107">As a consequence, the region does not run in the event of an out-of-memory condition or a thread abort.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="4c7d2-108">原因</span><span class="sxs-lookup"><span data-stu-id="4c7d2-108">Cause</span></span>  
 <span data-ttu-id="4c7d2-109">未正確地遵循 CER 的準備模式。</span><span class="sxs-lookup"><span data-stu-id="4c7d2-109">The preparation pattern for a CER is not followed correctly.</span></span>  <span data-ttu-id="4c7d2-110">這是一個錯誤事件。</span><span class="sxs-lookup"><span data-stu-id="4c7d2-110">This is an error event.</span></span> <span data-ttu-id="4c7d2-111"><xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>用來將標示為引入 CER 中的例外狀況處理常式的方法呼叫其`catch` / `finally` / `fault` / `filter`區塊必須緊接地用於前面`try`陳述式。</span><span class="sxs-lookup"><span data-stu-id="4c7d2-111">The <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method call used to mark exception handlers as introducing a CER in their `catch`/`finally`/`fault`/`filter` blocks must be used immediately before the `try` statement.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="4c7d2-112">解決方式</span><span class="sxs-lookup"><span data-stu-id="4c7d2-112">Resolution</span></span>  
 <span data-ttu-id="4c7d2-113">請確定對 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> 的呼叫緊接在 `try` 陳述式前面。</span><span class="sxs-lookup"><span data-stu-id="4c7d2-113">Ensure that the call to <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> happens immediately before the `try` statement.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="4c7d2-114">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="4c7d2-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="4c7d2-115">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="4c7d2-115">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="4c7d2-116">輸出</span><span class="sxs-lookup"><span data-stu-id="4c7d2-116">Output</span></span>  
 <span data-ttu-id="4c7d2-117">MDA 會顯示呼叫 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> 方法的方法名稱、MSIL 位移，以及指出呼叫並未緊接在 try 區塊開頭前面的訊息。</span><span class="sxs-lookup"><span data-stu-id="4c7d2-117">The MDA displays the name of the method calling the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method, the MSIL offset, and a message indicating the call does not immediately precede the beginning of the try block.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="4c7d2-118">組態</span><span class="sxs-lookup"><span data-stu-id="4c7d2-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="4c7d2-119">範例</span><span class="sxs-lookup"><span data-stu-id="4c7d2-119">Example</span></span>  
 <span data-ttu-id="4c7d2-120">下列程式碼範例示範會導致此 MDA 啟動的模式。</span><span class="sxs-lookup"><span data-stu-id="4c7d2-120">The following code example demonstrates the pattern that causes this MDA to be activated.</span></span>  
  
```  
void MethodWithInvalidPCR()  
{  
    RuntimeHelpers.PrepareConstrainedRegions();  
    Object o = new Object();  
    try  
    {  
        …  
    }  
    finally  
    {  
        …  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="4c7d2-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c7d2-121">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>  
 [<span data-ttu-id="4c7d2-122">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="4c7d2-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="4c7d2-123">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="4c7d2-123">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
