---
title: 如何：處理平行迴圈中的例外狀況
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to handle exceptions
ms.assetid: 512f0d5a-4636-4875-b766-88f20044f143
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 11ba240d71287be91bd0b4b40a2cb69f6e2808d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580545"
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a><span data-ttu-id="1535a-102">如何：處理平行迴圈中的例外狀況</span><span class="sxs-lookup"><span data-stu-id="1535a-102">How to: Handle Exceptions in Parallel Loops</span></span>
<span data-ttu-id="1535a-103"><xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 多載沒有任何特殊機制可用來處理可能擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1535a-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> overloads do not have any special mechanism to handle exceptions that might be thrown.</span></span> <span data-ttu-id="1535a-104">它們在這一方面類似於一般 `for` 和 `foreach` 迴圈 (在 Visual Basic 中為 `For` 和 `For Each`)；未處理的例外狀況會導致此迴圈立即終止。</span><span class="sxs-lookup"><span data-stu-id="1535a-104">In this respect, they resemble regular `for` and `foreach` loops (`For` and `For Each` in Visual Basic); an unhandled exception causes the loop to terminate immediately.</span></span>  
  
 <span data-ttu-id="1535a-105">當您將自己的例外狀況處理邏輯加入平行迴圈時，請處理多個執行緒上可能同時擲回類似例外狀況的情況，以及某個執行緒上擲回的例外狀況導致在另一個執行緒上擲回另一個例外狀況的情況。</span><span class="sxs-lookup"><span data-stu-id="1535a-105">When you add your own exception-handling logic to parallel loops, handle the case in which similar exceptions might be thrown on multiple threads concurrently, and the case in which an exception thrown on one thread causes another exception to be thrown on another thread.</span></span> <span data-ttu-id="1535a-106">您可以來自此迴圈的所有例外狀況包裝在 <xref:System.AggregateException?displayProperty=nameWithType> 中，同時處理這兩種情況。</span><span class="sxs-lookup"><span data-stu-id="1535a-106">You can handle both cases by wrapping all exceptions from the loop in a <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1535a-107">下列範例會示範一種可能的方式。</span><span class="sxs-lookup"><span data-stu-id="1535a-107">The following example shows one possible approach.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1535a-108">啟用 [Just My Code] 時，Visual Studio 在某些情況下會在擲回例外狀況的字行上中斷，並顯示錯誤訊息，指出「使用者程式碼未處理例外狀況」。</span><span class="sxs-lookup"><span data-stu-id="1535a-108">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="1535a-109">這個錯誤是良性的。</span><span class="sxs-lookup"><span data-stu-id="1535a-109">This error is benign.</span></span> <span data-ttu-id="1535a-110">您可以按 F5 從中斷的地方繼續，並查看下面範例中示範的例外處理行為。</span><span class="sxs-lookup"><span data-stu-id="1535a-110">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the example below.</span></span> <span data-ttu-id="1535a-111">若要防止 Visual Studio 在遇到第一個錯誤時就中斷，只要取消核取 [工具]、[選項]、[偵錯]、[一般] 下的 [Just My Code] 核取方塊即可。</span><span class="sxs-lookup"><span data-stu-id="1535a-111">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1535a-112">範例</span><span class="sxs-lookup"><span data-stu-id="1535a-112">Example</span></span>  
 <span data-ttu-id="1535a-113">在此範例中，會攔截所有例外狀況，然後包裝於擲回的 <xref:System.AggregateException?displayProperty=nameWithType> 之中。</span><span class="sxs-lookup"><span data-stu-id="1535a-113">In this example, all exceptions are caught and then wrapped in an <xref:System.AggregateException?displayProperty=nameWithType> which is thrown.</span></span> <span data-ttu-id="1535a-114">呼叫端可決定要處理哪一個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1535a-114">The caller can decide which exceptions to handle.</span></span>  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="1535a-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="1535a-115">See Also</span></span>  
 [<span data-ttu-id="1535a-116">資料平行處理原則</span><span class="sxs-lookup"><span data-stu-id="1535a-116">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [<span data-ttu-id="1535a-117">PLINQ 和 TPL 中的 Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="1535a-117">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
