---
title: LINQ to XML 中的延後執行和延遲評估 (C#)
ms.date: 07/20/2015
ms.assetid: 8683d1b4-b7ec-407b-be12-906ebe958a09
ms.openlocfilehash: 83fdc73b583a2c8aba5383f4a5b3af11a1f6f9c4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709685"
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-c"></a><span data-ttu-id="de636-102">LINQ to XML 中的延後執行和延遲評估 (C#)</span><span class="sxs-lookup"><span data-stu-id="de636-102">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>
<span data-ttu-id="de636-103">若要使用延後執行，通常會實作查詢和座標軸運算。</span><span class="sxs-lookup"><span data-stu-id="de636-103">Query and axis operations are often implemented to use deferred execution.</span></span> <span data-ttu-id="de636-104">本主題說明延後執行的條件與優點以及一些實作考量。</span><span class="sxs-lookup"><span data-stu-id="de636-104">This topic explains the requirements and advantages of deferred execution, and some implementation considerations.</span></span>  
  
## <a name="deferred-execution"></a><span data-ttu-id="de636-105">延後執行</span><span class="sxs-lookup"><span data-stu-id="de636-105">Deferred Execution</span></span>  
 <span data-ttu-id="de636-106">延後執行是指延遲評估運算式，直到實際需要其「實現的」值為止。</span><span class="sxs-lookup"><span data-stu-id="de636-106">Deferred execution means that the evaluation of an expression is delayed until its *realized* value is actually required.</span></span> <span data-ttu-id="de636-107">當您必須管理大型資料集合，尤其是在包含一系列鏈結之查詢或管理的程式中時，延後執行會明顯改善效能。</span><span class="sxs-lookup"><span data-stu-id="de636-107">Deferred execution can greatly improve performance when you have to manipulate large data collections, especially in programs that contain a series of chained queries or manipulations.</span></span> <span data-ttu-id="de636-108">在最好的情況下，延後執行僅能單一逐一查看來源集合。</span><span class="sxs-lookup"><span data-stu-id="de636-108">In the best case, deferred execution enables only a single iteration through the source collection.</span></span>  
  
 <span data-ttu-id="de636-109">LINQ 技術可讓延後執行大量用於 <xref:System.Linq?displayProperty=nameWithType> 核心類別的成員以及各種 LINQ 命名空間中的擴充方法，例如，<xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="de636-109">The LINQ technologies make extensive use of deferred execution in both the members of core <xref:System.Linq?displayProperty=nameWithType> classes and in the extension methods in the various LINQ namespaces, such as <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="de636-110">在 Iterator 區塊中使用時，支援在 C# 語言中，透過 [yield](../../../../csharp/language-reference/keywords/yield.md) 關鍵字 (以 `yield-return` 陳述式的形式) 直接支援延後執行。</span><span class="sxs-lookup"><span data-stu-id="de636-110">Deferred execution is supported directly in the C# language by the [yield](../../../../csharp/language-reference/keywords/yield.md) keyword (in the form of the `yield-return` statement) when used within an iterator block.</span></span> <span data-ttu-id="de636-111">此類 Iterator 必須傳回型別 <xref:System.Collections.IEnumerator> 或 <xref:System.Collections.Generic.IEnumerator%601> (或衍生型別) 的集合。</span><span class="sxs-lookup"><span data-stu-id="de636-111">Such an iterator must return a collection of type <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> (or a derived type).</span></span>  
  
## <a name="eager-vs-lazy-evaluation"></a><span data-ttu-id="de636-112">急切評估與延遲評估之比較</span><span class="sxs-lookup"><span data-stu-id="de636-112">Eager vs. Lazy Evaluation</span></span>  
 <span data-ttu-id="de636-113">當您撰寫實作延後執行的方法時，您也必須決定要使用延遲評估或急切評估來實作方法。</span><span class="sxs-lookup"><span data-stu-id="de636-113">When you write a method that implements deferred execution, you also have to decide whether to implement the method using lazy evaluation or eager evaluation.</span></span>  
  
-   <span data-ttu-id="de636-114">若為「延遲評估」，來源集合的單一項目會在每次呼叫 Iterator 時進行處理。</span><span class="sxs-lookup"><span data-stu-id="de636-114">In *lazy evaluation*, a single element of the source collection is processed during each call to the iterator.</span></span> <span data-ttu-id="de636-115">這是實作 Iterator 的一般方式。</span><span class="sxs-lookup"><span data-stu-id="de636-115">This is the typical way in which iterators are implemented.</span></span>  
  
-   <span data-ttu-id="de636-116">若為「急切評估」，第一次呼叫 Iterator 時，就會處理整個集合。</span><span class="sxs-lookup"><span data-stu-id="de636-116">In *eager evaluation*, the first call to the iterator will result in the entire collection being processed.</span></span> <span data-ttu-id="de636-117">同時，可能也需要來源集合的暫存副本。</span><span class="sxs-lookup"><span data-stu-id="de636-117">A temporary copy of the source collection might also be required.</span></span> <span data-ttu-id="de636-118">例如，<xref:System.Linq.Enumerable.OrderBy%2A> 方法必須在傳回第一個項目前，排序整個集合。</span><span class="sxs-lookup"><span data-stu-id="de636-118">For example, the <xref:System.Linq.Enumerable.OrderBy%2A> method has to sort the entire collection before it returns the first element.</span></span>  
  
 <span data-ttu-id="de636-119">延遲評估通常會產生較好的效能，因為它會平均分散整個集合評估的負荷處理，並將暫存資料的使用率降到最低。</span><span class="sxs-lookup"><span data-stu-id="de636-119">Lazy evaluation usually yields better performance because it distributes overhead processing evenly throughout the evaluation of the collection and minimizes the use of temporary data.</span></span> <span data-ttu-id="de636-120">當然，對於某些運算而言，沒有具體化中繼結果之外的其他選擇。</span><span class="sxs-lookup"><span data-stu-id="de636-120">Of course, for some operations, there is no other option than to materialize intermediate results.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="de636-121">後續步驟</span><span class="sxs-lookup"><span data-stu-id="de636-121">Next Steps</span></span>  
 <span data-ttu-id="de636-122">此教學課程中的下一個主題說明延後執行：</span><span class="sxs-lookup"><span data-stu-id="de636-122">The next topic in this tutorial illustrates deferred execution:</span></span>  
  
-   [<span data-ttu-id="de636-123">延後執行範例 (C#)</span><span class="sxs-lookup"><span data-stu-id="de636-123">Deferred Execution Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-example.md)  
  
## <a name="see-also"></a><span data-ttu-id="de636-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de636-124">See also</span></span>

- [<span data-ttu-id="de636-125">教學課程：將查詢鏈結在一起 (C#)</span><span class="sxs-lookup"><span data-stu-id="de636-125">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
- [<span data-ttu-id="de636-126">概念和術語 (函數式轉換) (C#)</span><span class="sxs-lookup"><span data-stu-id="de636-126">Concepts and Terminology (Functional Transformation) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)
- [<span data-ttu-id="de636-127">彙總作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="de636-127">Aggregation Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/aggregation-operations.md)
- [<span data-ttu-id="de636-128">yield</span><span class="sxs-lookup"><span data-stu-id="de636-128">yield</span></span>](../../../../csharp/language-reference/keywords/yield.md)
