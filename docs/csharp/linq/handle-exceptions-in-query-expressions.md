---
title: 處理查詢運算式中的例外狀況
description: 如何處理查詢運算式中的例外狀況。
ms.date: 12/1/2016
ms.assetid: 2bf0c397-13fb-4f68-bc2b-531c6c88a167
ms.openlocfilehash: 691373fabeb3934ecc454cbc3b36a5f7bf477bee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="handle-exceptions-in-query-expressions"></a><span data-ttu-id="ea316-103">處理查詢運算式中的例外狀況</span><span class="sxs-lookup"><span data-stu-id="ea316-103">Handle exceptions in query expressions</span></span>

<span data-ttu-id="ea316-104">您可在查詢運算式的內容中呼叫任何方法。</span><span class="sxs-lookup"><span data-stu-id="ea316-104">It is possible to call any method in the context of a query expression.</span></span> <span data-ttu-id="ea316-105">不過，我們建議您避免在查詢運算式中呼叫任何方法，因為它會產生副作用，例如修改資料來源的內容或擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ea316-105">However, we recommend that you avoid calling any method in a query expression that can create a side effect such as modifying the contents of the data source or throwing an exception.</span></span> <span data-ttu-id="ea316-106">本例顯示如何避免在查詢運算式中呼叫方法時引發例外狀況，卻不違反處理例外狀況的一般 .NET Framework 方針。</span><span class="sxs-lookup"><span data-stu-id="ea316-106">This example shows how to avoid raising exceptions when you call methods in a query expression without violating the general .NET Framework guidelines on exception handling.</span></span> <span data-ttu-id="ea316-107">這些方針指出，當您了解為何在指定內容中擲回時，可以接受攔截特定的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ea316-107">Those guidelines state that it is acceptable to catch a specific exception when you understand why it will be thrown in a given context.</span></span> <span data-ttu-id="ea316-108">如需詳細資訊，請參閱[例外狀況的最佳做法](../../standard/exceptions/best-practices-for-exceptions.md)。</span><span class="sxs-lookup"><span data-stu-id="ea316-108">For more information, see [Best Practices for Exceptions](../../standard/exceptions/best-practices-for-exceptions.md).</span></span>  
  
 <span data-ttu-id="ea316-109">最後一個範例顯示如何處理這種當您在查詢執行期間必須擲回例外狀況的情況。</span><span class="sxs-lookup"><span data-stu-id="ea316-109">The final example shows how to handle those cases when you must throw an exception during execution of a query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea316-110">範例</span><span class="sxs-lookup"><span data-stu-id="ea316-110">Example</span></span>  

 <span data-ttu-id="ea316-111">下例示範如何將例外狀況處理程式碼移到查詢運算式之外。</span><span class="sxs-lookup"><span data-stu-id="ea316-111">The following example shows how to move exception handling code outside a query expression.</span></span> <span data-ttu-id="ea316-112">只有當方法不依賴任何查詢區域變數時才可以。</span><span class="sxs-lookup"><span data-stu-id="ea316-112">This is only possible when the method does not depend on any variables local to the query.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#10](../../../samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="ea316-113">範例</span><span class="sxs-lookup"><span data-stu-id="ea316-113">Example</span></span> 

 <span data-ttu-id="ea316-114">在某些情況下，對從查詢中擲回的例外狀況的最佳回應，可能是立即停止執行查詢。</span><span class="sxs-lookup"><span data-stu-id="ea316-114">In some cases, the best response to an exception that is thrown from within a query might be to stop the query execution immediately.</span></span> <span data-ttu-id="ea316-115">下例示範如何處理可能從查詢主體內擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ea316-115">The following example shows how to handle exceptions that might be thrown from inside a query body.</span></span> <span data-ttu-id="ea316-116">假設 `SomeMethodThatMightThrow` 可能造成需要停止執行查詢的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ea316-116">Assume that `SomeMethodThatMightThrow` can potentially cause an exception that requires the query execution to stop.</span></span>  
  
 <span data-ttu-id="ea316-117">請注意，`try` 區塊會括住 `foreach` 迴圈，不是括住查詢本身。</span><span class="sxs-lookup"><span data-stu-id="ea316-117">Note that the `try` block encloses the `foreach` loop, and not the query itself.</span></span> <span data-ttu-id="ea316-118">這是因為 `foreach` 迴圈是查詢實際執行的點。</span><span class="sxs-lookup"><span data-stu-id="ea316-118">This is because the `foreach` loop is the point at which the query is actually executed.</span></span> <span data-ttu-id="ea316-119">如需詳細資訊，請參閱 [LINQ 查詢簡介](../programming-guide/concepts/linq/introduction-to-linq-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="ea316-119">For more information, see [Introduction to LINQ queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 [!code-csharp[csProgGuideLINQ#12](../../../samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_2.cs)]  
  

## <a name="see-also"></a><span data-ttu-id="ea316-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="ea316-120">See Also</span></span>  
 [<span data-ttu-id="ea316-121">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="ea316-121">LINQ query expressions</span></span>](index.md)
