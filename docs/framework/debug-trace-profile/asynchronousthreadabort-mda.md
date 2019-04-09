---
title: asynchronousThreadAbort MDA
ms.date: 03/30/2017
helpviewer_keywords:
- asynchronous thread aborts
- AsynchronousThreadAbort MDA
- managed debugging assistants (MDAs), asynchronous thread aborts
- threading [.NET Framework], managed debugging assistants
- MDAs (managed debugging assistants), asynchronous thread aborts
ms.assetid: 9ebe40b2-d703-421e-8660-984acc42bfe0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 08f67ad363d0bd3efcc7a1eeedd1f48d3bae9407
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59114882"
---
# <a name="asynchronousthreadabort-mda"></a><span data-ttu-id="cfb9a-102">asynchronousThreadAbort MDA</span><span class="sxs-lookup"><span data-stu-id="cfb9a-102">asynchronousThreadAbort MDA</span></span>
<span data-ttu-id="cfb9a-103">當執行緒嘗試在另一個執行緒中在引入非同步中止時，就會啟用 `asynchronousThreadAbort` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="cfb9a-103">The `asynchronousThreadAbort` managed debugging assistant (MDA) is activated when a thread attempts to introduce an asynchronous abort into another thread.</span></span> <span data-ttu-id="cfb9a-104">同步執行緒中止不會啟動 `asynchronousThreadAbort` MDA。</span><span class="sxs-lookup"><span data-stu-id="cfb9a-104">Synchronous thread aborts do not activate the `asynchronousThreadAbort` MDA.</span></span>

## <a name="symptoms"></a><span data-ttu-id="cfb9a-105">徵兆</span><span class="sxs-lookup"><span data-stu-id="cfb9a-105">Symptoms</span></span>
 <span data-ttu-id="cfb9a-106">當主應用程式執行緒中止時，應用程式會當機，並出現未處理的 <xref:System.Threading.ThreadAbortException>。</span><span class="sxs-lookup"><span data-stu-id="cfb9a-106">An application crashes with an unhandled <xref:System.Threading.ThreadAbortException> when the main application thread is aborted.</span></span> <span data-ttu-id="cfb9a-107">如果繼續執行應用程式，可能會出現比應用程式當機更糟的結果，甚至還會造成資料損毀。</span><span class="sxs-lookup"><span data-stu-id="cfb9a-107">If the application were to continue to execute, the consequences might be worse than the application crashing, possibly resulting in further data corruption.</span></span>

 <span data-ttu-id="cfb9a-108">原本該自動進行的作業，很可能在部分完成後遭到中斷，使得應用程式資料處於無法預期的狀態。</span><span class="sxs-lookup"><span data-stu-id="cfb9a-108">Operations meant to be atomic have likely been interrupted after partial completion, leaving application data in an unpredictable state.</span></span> <span data-ttu-id="cfb9a-109"><xref:System.Threading.ThreadAbortException> 可以從程式碼執行中似乎是隨機點的位置產生，這些通常預期不會引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="cfb9a-109">A <xref:System.Threading.ThreadAbortException> can be generated from seemingly random points in the execution of code, often in places from which an exception is not expected to arise.</span></span> <span data-ttu-id="cfb9a-110">程式碼可能無法處理這類例外狀況，因而導致損毀狀態。</span><span class="sxs-lookup"><span data-stu-id="cfb9a-110">The code might not be capable of handling such an exception, resulting in a corrupt state.</span></span>

 <span data-ttu-id="cfb9a-111">由於這個問題原有的隨機性，徵兆可能會有很大的不同。</span><span class="sxs-lookup"><span data-stu-id="cfb9a-111">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>

## <a name="cause"></a><span data-ttu-id="cfb9a-112">原因</span><span class="sxs-lookup"><span data-stu-id="cfb9a-112">Cause</span></span>
 <span data-ttu-id="cfb9a-113">一個執行緒中的程式碼呼叫了目標執行緒上的 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 方法，以引入非同步執行緒中止。</span><span class="sxs-lookup"><span data-stu-id="cfb9a-113">Code in one thread called the <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method on a target thread to introduce an asynchronous thread abort.</span></span> <span data-ttu-id="cfb9a-114">由於對 <xref:System.Threading.Thread.Abort%2A> 發出呼叫的程式碼不是在中止作業目標的執行緒上執行；因此，執行緒中止為非同步。</span><span class="sxs-lookup"><span data-stu-id="cfb9a-114">The thread abort is asynchronous because the code that makes the call to <xref:System.Threading.Thread.Abort%2A> is running on a different thread than the target of the abort operation.</span></span> <span data-ttu-id="cfb9a-115">同步執行緒中止應該不會造成問題，因為執行 <xref:System.Threading.Thread.Abort%2A> 的執行緒應該只會在應用程式狀態一致的安全檢查點上完成。</span><span class="sxs-lookup"><span data-stu-id="cfb9a-115">Synchronous thread aborts should not cause a problem because the thread performing the <xref:System.Threading.Thread.Abort%2A> should have done so only at a safe checkpoint where application state is consistent.</span></span>

 <span data-ttu-id="cfb9a-116">由於非同步執行緒中止是在目標執行緒執行中的不可預期點進行處理，因而出現問題。</span><span class="sxs-lookup"><span data-stu-id="cfb9a-116">Asynchronous thread aborts present a problem because they are processed at unpredictable points in the target thread's execution.</span></span> <span data-ttu-id="cfb9a-117">若要避免發生這種情形，請撰寫程式碼，並在可能以這種方式中止的執行緒上執行該程式碼，以便在程式碼的幾乎每一行處理 <xref:System.Threading.ThreadAbortException>，讓應用程式資料能夠回到一致的狀態。</span><span class="sxs-lookup"><span data-stu-id="cfb9a-117">To avoid this, code written to run on a thread that might be aborted in this manner would need to handle a <xref:System.Threading.ThreadAbortException> at almost every line of code, taking care to put application data back into a consistent state.</span></span> <span data-ttu-id="cfb9a-118">期待在撰寫程式碼時已設想這個問題，或是撰寫出能夠預防各種可能情況的程式碼，都是不切實際的。</span><span class="sxs-lookup"><span data-stu-id="cfb9a-118">It is not realistic to expect code to be written with this problem in mind or to write code that protects against all possible circumstances.</span></span>

 <span data-ttu-id="cfb9a-119">呼叫進入 Unmanaged 程式碼和 `finally` 區塊，並不會非同步地中止，而是會立即從這些分類的其中一個分類中結束。</span><span class="sxs-lookup"><span data-stu-id="cfb9a-119">Calls into unmanaged code and `finally` blocks will not be aborted asynchronously but immediately upon exit from one of these categories.</span></span>

 <span data-ttu-id="cfb9a-120">由於本問題原有的隨機性，可能會難以判定原因。</span><span class="sxs-lookup"><span data-stu-id="cfb9a-120">The cause might be difficult to determine due to the randomness inherent to the problem.</span></span>

## <a name="resolution"></a><span data-ttu-id="cfb9a-121">解決方式</span><span class="sxs-lookup"><span data-stu-id="cfb9a-121">Resolution</span></span>
 <span data-ttu-id="cfb9a-122">避免需要使用非同步執行緒中止的程式碼設計。</span><span class="sxs-lookup"><span data-stu-id="cfb9a-122">Avoid code design that requires the use of asynchronous thread aborts.</span></span> <span data-ttu-id="cfb9a-123">有數種方法更適合用來中斷不需要呼叫 <xref:System.Threading.Thread.Abort%2A> 的目標執行緒。</span><span class="sxs-lookup"><span data-stu-id="cfb9a-123">There are several approaches more appropriate for interruption of a target thread that do not require a call to <xref:System.Threading.Thread.Abort%2A>.</span></span> <span data-ttu-id="cfb9a-124">最安全的方法就是採用一種機制，例如通用的屬性，對目標執行緒發出信號以要求中斷。</span><span class="sxs-lookup"><span data-stu-id="cfb9a-124">The safest is to introduce a mechanism, such as a common property, that signals the target thread to request an interrupt.</span></span> <span data-ttu-id="cfb9a-125">目標執行緒會在特定的安全檢查點上檢查信號。</span><span class="sxs-lookup"><span data-stu-id="cfb9a-125">The target thread checks the signal at certain safe checkpoints.</span></span> <span data-ttu-id="cfb9a-126">如果注意到已經要求中斷，目標執行緒就會順利地關閉。</span><span class="sxs-lookup"><span data-stu-id="cfb9a-126">If it notices that an interrupt has been requested, it can shut down gracefully.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="cfb9a-127">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="cfb9a-127">Effect on the Runtime</span></span>
 <span data-ttu-id="cfb9a-128">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="cfb9a-128">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="cfb9a-129">它只會報告有關非同步執行緒中止的資料。</span><span class="sxs-lookup"><span data-stu-id="cfb9a-129">It only reports data about asynchronous thread aborts.</span></span>

## <a name="output"></a><span data-ttu-id="cfb9a-130">Output</span><span class="sxs-lookup"><span data-stu-id="cfb9a-130">Output</span></span>
 <span data-ttu-id="cfb9a-131">此 MDA 會報告執行中止之執行緒的 ID，以及作為中止目標之執行緒的 ID。</span><span class="sxs-lookup"><span data-stu-id="cfb9a-131">The MDA reports the ID of the thread performing the abort and the ID of the thread that is the target of the abort.</span></span> <span data-ttu-id="cfb9a-132">由於僅限於非同步中止，因此這兩者絕對不會相同。</span><span class="sxs-lookup"><span data-stu-id="cfb9a-132">These will never be the same because this is limited to asynchronous aborts.</span></span>

## <a name="configuration"></a><span data-ttu-id="cfb9a-133">組態</span><span class="sxs-lookup"><span data-stu-id="cfb9a-133">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <asynchronousThreadAbort />
  </assistants>
</mdaConfig>
```

## <a name="example"></a><span data-ttu-id="cfb9a-134">範例</span><span class="sxs-lookup"><span data-stu-id="cfb9a-134">Example</span></span>
 <span data-ttu-id="cfb9a-135">若要啟用 `asynchronousThreadAbort` MDA ，只需要在個別執行的執行緒上呼叫 <xref:System.Threading.Thread.Abort%2A>。</span><span class="sxs-lookup"><span data-stu-id="cfb9a-135">Activating the `asynchronousThreadAbort` MDA requires only a call to <xref:System.Threading.Thread.Abort%2A> on a separate running thread.</span></span> <span data-ttu-id="cfb9a-136">請考慮如果執行緒啟動函式的內容是一組更為複雜的作業，而那些作業可能會在任意一點因為中止而中斷的後果。</span><span class="sxs-lookup"><span data-stu-id="cfb9a-136">Consider the consequences if the contents of the thread start function were a set of more complex operations which might be interrupted at any arbitrary point by the abort.</span></span>

```csharp
using System.Threading;
void FireMda()
{
    Thread t = new Thread(delegate() { Thread.Sleep(1000); });
    t.Start();
    // The following line activates the MDA.
    t.Abort();
    t.Join();
}
```

## <a name="see-also"></a><span data-ttu-id="cfb9a-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cfb9a-137">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="cfb9a-138">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="cfb9a-138">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
