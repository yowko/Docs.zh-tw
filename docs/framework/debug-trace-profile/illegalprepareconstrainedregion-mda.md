---
title: illegalPrepareConstrainedRegion MDA
description: 檢查 illegalPrepareConstrainedRegion managed 偵錯工具，這是在 PrepareConstrainedRegions 呼叫後面沒有 try 語句時叫用的。
ms.date: 03/30/2017
helpviewer_keywords:
- PrepareConstrainedRegions method
- managed debugging assistants (MDAs), illegal PrepareConstrainedRegions
- try/catch exception handling, managed debugging assistants
- IllegalPrepareConstrainedRegions MDA
- MDAs (managed debugging assistants), illegal PrepareConstrainedRegions
ms.assetid: 2f9b5031-f910-4e01-a196-f89eab313eaf
ms.openlocfilehash: 7cbf04e8605ccf18e89882dd09b96cc7c59330c9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272783"
---
# <a name="illegalprepareconstrainedregion-mda"></a><span data-ttu-id="bc487-103">illegalPrepareConstrainedRegion MDA</span><span class="sxs-lookup"><span data-stu-id="bc487-103">illegalPrepareConstrainedRegion MDA</span></span>

<span data-ttu-id="bc487-104"><xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> 方法呼叫並未緊接在例外狀況處理常式的 `try` 陳述式前面時，`illegalPrepareConstrainedRegion` Managed 偵錯助理 (MDA) 就會啟動。</span><span class="sxs-lookup"><span data-stu-id="bc487-104">The `illegalPrepareConstrainedRegion` managed debugging assistant (MDA) is activated when a <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> method call does not immediately precede the `try` statement of the exception handler.</span></span> <span data-ttu-id="bc487-105">這項限制屬於 MSIL 層級，因此可允許在呼叫和 `try` 之間具有不產生程式碼的來源，例如註解。</span><span class="sxs-lookup"><span data-stu-id="bc487-105">This restriction is at the MSIL level, so it is permissible to have non-code-generating source between the call and the `try`, such as comments.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="bc487-106">徵狀</span><span class="sxs-lookup"><span data-stu-id="bc487-106">Symptoms</span></span>  

 <span data-ttu-id="bc487-107">限制的執行區域 (CER) 永遠不會被視為這類執行區執，而是當成簡單的例外狀況處理區塊 (`finally` 或`catch`)。</span><span class="sxs-lookup"><span data-stu-id="bc487-107">A constrained execution region (CER) that is never treated as such, but as a simple exception handling block (`finally` or `catch`).</span></span> <span data-ttu-id="bc487-108">因此，這個區域不會在發生記憶體不足狀況或執行緒中止的情況下執行。</span><span class="sxs-lookup"><span data-stu-id="bc487-108">As a consequence, the region does not run in the event of an out-of-memory condition or a thread abort.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="bc487-109">原因</span><span class="sxs-lookup"><span data-stu-id="bc487-109">Cause</span></span>  

 <span data-ttu-id="bc487-110">未正確地遵循 CER 的準備模式。</span><span class="sxs-lookup"><span data-stu-id="bc487-110">The preparation pattern for a CER is not followed correctly.</span></span>  <span data-ttu-id="bc487-111">這是一個錯誤事件。</span><span class="sxs-lookup"><span data-stu-id="bc487-111">This is an error event.</span></span> <span data-ttu-id="bc487-112"><xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>用來標記例外狀況處理常式的方法呼叫， `catch` / `finally` / `fault` / `filter` 必須緊接在語句之前使用 `try` 。</span><span class="sxs-lookup"><span data-stu-id="bc487-112">The <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method call used to mark exception handlers as introducing a CER in their `catch`/`finally`/`fault`/`filter` blocks must be used immediately before the `try` statement.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="bc487-113">解決方法</span><span class="sxs-lookup"><span data-stu-id="bc487-113">Resolution</span></span>  

 <span data-ttu-id="bc487-114">請確定對 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> 的呼叫緊接在 `try` 陳述式前面。</span><span class="sxs-lookup"><span data-stu-id="bc487-114">Ensure that the call to <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> happens immediately before the `try` statement.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="bc487-115">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="bc487-115">Effect on the Runtime</span></span>  

 <span data-ttu-id="bc487-116">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="bc487-116">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="bc487-117">輸出</span><span class="sxs-lookup"><span data-stu-id="bc487-117">Output</span></span>  

 <span data-ttu-id="bc487-118">MDA 會顯示呼叫 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> 方法的方法名稱、MSIL 位移，以及指出呼叫並未緊接在 try 區塊開頭前面的訊息。</span><span class="sxs-lookup"><span data-stu-id="bc487-118">The MDA displays the name of the method calling the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method, the MSIL offset, and a message indicating the call does not immediately precede the beginning of the try block.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="bc487-119">設定</span><span class="sxs-lookup"><span data-stu-id="bc487-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="bc487-120">範例</span><span class="sxs-lookup"><span data-stu-id="bc487-120">Example</span></span>  

 <span data-ttu-id="bc487-121">下列程式碼範例示範會導致此 MDA 啟動的模式。</span><span class="sxs-lookup"><span data-stu-id="bc487-121">The following code example demonstrates the pattern that causes this MDA to be activated.</span></span>  
  
```csharp
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
  
## <a name="see-also"></a><span data-ttu-id="bc487-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc487-122">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>
- [<span data-ttu-id="bc487-123">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="bc487-123">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="bc487-124">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="bc487-124">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
