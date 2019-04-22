---
title: 延後的執行和延遲評估，在 LINQ to XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 31998eed-b95e-47fb-a865-9de1f337d1fb
ms.openlocfilehash: b5c3e2a484aa16df22742ddf77d6438ec2a699bb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58839029"
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-visual-basic"></a><span data-ttu-id="7b720-102">延後的執行和延遲評估，在 LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b720-102">Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)</span></span>
<span data-ttu-id="7b720-103">若要使用延後執行，通常會實作查詢和座標軸運算。</span><span class="sxs-lookup"><span data-stu-id="7b720-103">Query and axis operations are often implemented to use deferred execution.</span></span> <span data-ttu-id="7b720-104">本主題說明延後執行的條件與優點以及一些實作考量。</span><span class="sxs-lookup"><span data-stu-id="7b720-104">This topic explains the requirements and advantages of deferred execution, and some implementation considerations.</span></span>  
  
## <a name="deferred-execution"></a><span data-ttu-id="7b720-105">延後執行</span><span class="sxs-lookup"><span data-stu-id="7b720-105">Deferred Execution</span></span>  
 <span data-ttu-id="7b720-106">延後執行是指延遲評估運算式，直到實際需要其「實現的」值為止。</span><span class="sxs-lookup"><span data-stu-id="7b720-106">Deferred execution means that the evaluation of an expression is delayed until its *realized* value is actually required.</span></span> <span data-ttu-id="7b720-107">當您必須管理大型資料集合，尤其是在包含一系列鏈結之查詢或管理的程式中時，延後執行會明顯改善效能。</span><span class="sxs-lookup"><span data-stu-id="7b720-107">Deferred execution can greatly improve performance when you have to manipulate large data collections, especially in programs that contain a series of chained queries or manipulations.</span></span> <span data-ttu-id="7b720-108">在最好的情況下，延後執行僅能單一逐一查看來源集合。</span><span class="sxs-lookup"><span data-stu-id="7b720-108">In the best case, deferred execution enables only a single iteration through the source collection.</span></span>  
  
 <span data-ttu-id="7b720-109">LINQ 技術可讓延後執行大量用於 <xref:System.Linq?displayProperty=nameWithType> 核心類別的成員以及各種 LINQ 命名空間中的擴充方法，例如，<xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="7b720-109">The LINQ technologies make extensive use of deferred execution in both the members of core <xref:System.Linq?displayProperty=nameWithType> classes and in the extension methods in the various LINQ namespaces, such as <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.</span></span>  
  
## <a name="eager-vs-lazy-evaluation"></a><span data-ttu-id="7b720-110">急切評估與延遲評估之比較</span><span class="sxs-lookup"><span data-stu-id="7b720-110">Eager vs. Lazy Evaluation</span></span>  
 <span data-ttu-id="7b720-111">當您撰寫實作延後執行的方法時，您也必須決定要使用延遲評估或急切評估來實作方法。</span><span class="sxs-lookup"><span data-stu-id="7b720-111">When you write a method that implements deferred execution, you also have to decide whether to implement the method using lazy evaluation or eager evaluation.</span></span>  
  
-   <span data-ttu-id="7b720-112">若為「延遲評估」，來源集合的單一項目會在每次呼叫 Iterator 時進行處理。</span><span class="sxs-lookup"><span data-stu-id="7b720-112">In *lazy evaluation*, a single element of the source collection is processed during each call to the iterator.</span></span> <span data-ttu-id="7b720-113">這是實作 Iterator 的一般方式。</span><span class="sxs-lookup"><span data-stu-id="7b720-113">This is the typical way in which iterators are implemented.</span></span>  
  
-   <span data-ttu-id="7b720-114">若為「急切評估」，第一次呼叫 Iterator 時，就會處理整個集合。</span><span class="sxs-lookup"><span data-stu-id="7b720-114">In *eager evaluation*, the first call to the iterator will result in the entire collection being processed.</span></span> <span data-ttu-id="7b720-115">同時，可能也需要來源集合的暫存副本。</span><span class="sxs-lookup"><span data-stu-id="7b720-115">A temporary copy of the source collection might also be required.</span></span> <span data-ttu-id="7b720-116">例如，<xref:System.Linq.Enumerable.OrderBy%2A> 方法必須在傳回第一個項目前，排序整個集合。</span><span class="sxs-lookup"><span data-stu-id="7b720-116">For example, the <xref:System.Linq.Enumerable.OrderBy%2A> method has to sort the entire collection before it returns the first element.</span></span>  
  
 <span data-ttu-id="7b720-117">延遲評估通常會產生較好的效能，因為它會平均分散整個集合評估的負荷處理，並將暫存資料的使用率降到最低。</span><span class="sxs-lookup"><span data-stu-id="7b720-117">Lazy evaluation usually yields better performance because it distributes overhead processing evenly throughout the evaluation of the collection and minimizes the use of temporary data.</span></span> <span data-ttu-id="7b720-118">當然，對於某些運算而言，沒有具體化中繼結果之外的其他選擇。</span><span class="sxs-lookup"><span data-stu-id="7b720-118">Of course, for some operations, there is no other option than to materialize intermediate results.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="7b720-119">後續步驟</span><span class="sxs-lookup"><span data-stu-id="7b720-119">Next Steps</span></span>  
 <span data-ttu-id="7b720-120">此教學課程中的下一個主題說明延後執行：</span><span class="sxs-lookup"><span data-stu-id="7b720-120">The next topic in this tutorial illustrates deferred execution:</span></span>  
  
-   [<span data-ttu-id="7b720-121">延後的執行範例 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b720-121">Deferred Execution Example (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-example.md)  
  
## <a name="see-also"></a><span data-ttu-id="7b720-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b720-122">See also</span></span>

- [<span data-ttu-id="7b720-123">教學課程：延後的執行 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b720-123">Tutorial: Deferred Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
- [<span data-ttu-id="7b720-124">概念和術語 （函數式轉換） (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b720-124">Concepts and Terminology (Functional Transformation) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)
- [<span data-ttu-id="7b720-125">彙總作業 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b720-125">Aggregation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)
