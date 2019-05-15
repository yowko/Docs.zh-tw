---
title: 作法：處理 PLINQ 查詢中的例外狀況
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to handle exceptions
ms.assetid: 8d56ff9b-a571-4d31-b41f-80c0b51b70a5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ef107ae0dceb7ee937b21d65cba92cbcf6a9a96c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64628991"
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a><span data-ttu-id="55ab1-102">作法：處理 PLINQ 查詢中的例外狀況</span><span class="sxs-lookup"><span data-stu-id="55ab1-102">How to: Handle Exceptions in a PLINQ Query</span></span>
<span data-ttu-id="55ab1-103">此主題中的第一個範例顯示如何處理當執行 PLINQ 查詢時可從它擲回的 <xref:System.AggregateException?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="55ab1-103">The first example in this topic shows how to handle the <xref:System.AggregateException?displayProperty=nameWithType> that can be thrown from a PLINQ query when it executes.</span></span> <span data-ttu-id="55ab1-104">第二個範例顯示如何將 try-catch 區塊放在委派內，且盡可能地接近將擲回例外狀況的位置。</span><span class="sxs-lookup"><span data-stu-id="55ab1-104">The second example shows how to put try-catch blocks within delegates, as close as possible to where the exception will be thrown.</span></span> <span data-ttu-id="55ab1-105">如此一來，您可以在發生例外狀況時立即攔截它們，並可能繼續執行查詢。</span><span class="sxs-lookup"><span data-stu-id="55ab1-105">In this way, you can catch them as soon as they occur and possibly continue query execution.</span></span> <span data-ttu-id="55ab1-106">當系統允許例外狀況反昇至聯結的執行緒時，查詢可能就可以在引發例外狀況之後，繼續處理某些項目。</span><span class="sxs-lookup"><span data-stu-id="55ab1-106">When exceptions are allowed to bubble up back to the joining thread, then it is possible that a query may continue to process some items after the exception is raised.</span></span>  
  
 <span data-ttu-id="55ab1-107">在某些 PLINQ 回復為循序執行且發生例外狀況的情況中，例外狀況可能會直接傳播，而不會包裝在 <xref:System.AggregateException> 中。</span><span class="sxs-lookup"><span data-stu-id="55ab1-107">In some cases when PLINQ falls back to sequential execution, and an exception occurs, the exception may be propagated directly, and not wrapped in an <xref:System.AggregateException>.</span></span> <span data-ttu-id="55ab1-108">此外，<xref:System.Threading.ThreadAbortException> 一律會直接傳播。</span><span class="sxs-lookup"><span data-stu-id="55ab1-108">Also, <xref:System.Threading.ThreadAbortException>s are always propagated directly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55ab1-109">啟用 [Just My Code] 時，Visual Studio 會在擲回例外狀況的字行上中斷，並顯示錯誤訊息，指出「使用者程式碼未處理例外狀況」。</span><span class="sxs-lookup"><span data-stu-id="55ab1-109">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="55ab1-110">這個錯誤是良性的。</span><span class="sxs-lookup"><span data-stu-id="55ab1-110">This error is benign.</span></span> <span data-ttu-id="55ab1-111">您可以按 F5 鍵繼續，並查看下面範例中示範的例外狀況處理行為。</span><span class="sxs-lookup"><span data-stu-id="55ab1-111">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="55ab1-112">若要防止 Visual Studio 在遇到第一個錯誤時就中斷，只要取消核取 [工具]、[選項]、[偵錯]、[一般] 下的 [Just My Code] 核取方塊即可。</span><span class="sxs-lookup"><span data-stu-id="55ab1-112">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
>   
>  <span data-ttu-id="55ab1-113">這個範例是為了示範用法，執行速度可能比不上對應的循序 LINQ to Objects 查詢。</span><span class="sxs-lookup"><span data-stu-id="55ab1-113">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="55ab1-114">如需加速的詳細資訊，請參閱[認識 PLINQ 中的加速](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。</span><span class="sxs-lookup"><span data-stu-id="55ab1-114">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="55ab1-115">範例</span><span class="sxs-lookup"><span data-stu-id="55ab1-115">Example</span></span>  
 <span data-ttu-id="55ab1-116">此範例會示範如何在執行查詢的程式碼周圍放置 try-catch 區塊，以攔截任何擲回的 <xref:System.AggregateException?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="55ab1-116">This example shows how to put the try-catch blocks around the code that executes the query to catch any <xref:System.AggregateException?displayProperty=nameWithType>s that are thrown.</span></span>  
  
 [!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
 [!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]  
  
 <span data-ttu-id="55ab1-117">在此範例中，擲回例外狀況之後查詢無法繼續。</span><span class="sxs-lookup"><span data-stu-id="55ab1-117">In this example, the query cannot continue after the exception is thrown.</span></span> <span data-ttu-id="55ab1-118">應用程式程式碼攔截到例外狀況時，PLINQ 已經停止所有執行緒上的查詢。</span><span class="sxs-lookup"><span data-stu-id="55ab1-118">By the time your application code catches the exception, PLINQ has already stopped the query on all threads.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55ab1-119">範例</span><span class="sxs-lookup"><span data-stu-id="55ab1-119">Example</span></span>  
 <span data-ttu-id="55ab1-120">下列範例會示範如何將 try-catch 區塊放在委派中，以使其可攔截例外狀況並繼續執行查詢。</span><span class="sxs-lookup"><span data-stu-id="55ab1-120">The following example shows how to put a try-catch block in a delegate to make it possible to catch an exception and continue with the query execution.</span></span>  
  
 [!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
 [!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="55ab1-121">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="55ab1-121">Compiling the Code</span></span>  
  
- <span data-ttu-id="55ab1-122">若要編譯並執行這些範例，請將它們複製到 [PLINQ 資料範] 範例中，並從 Main 呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="55ab1-122">To compile and run these examples, copy them into the PLINQ Data Sample example and call the method from Main.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="55ab1-123">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="55ab1-123">Robust Programming</span></span>  
 <span data-ttu-id="55ab1-124">除非您知道如何處理，否則請勿攔截例外狀況，這樣您才不會損毀您的程式狀態。</span><span class="sxs-lookup"><span data-stu-id="55ab1-124">Do not catch an exception unless you know how to handle it so that you do not corrupt the state of your program.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55ab1-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55ab1-125">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="55ab1-126">平行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="55ab1-126">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
