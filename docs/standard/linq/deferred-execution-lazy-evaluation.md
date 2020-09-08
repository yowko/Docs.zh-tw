---
title: 延後執行和延遲評估-LINQ to XML
description: 瞭解延後執行的優點和需求，以及如何使用查詢和軸作業來實現。
ms.date: 07/20/2015
ms.assetid: 8683d1b4-b7ec-407b-be12-906ebe958a09
ms.openlocfilehash: 21b1c7b7d54e7f787919f1e1601fc36bc8c1caff
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552106"
---
# <a name="deferred-execution-and-lazy-evaluation-linq-to-xml"></a><span data-ttu-id="77143-103">延後執行和延遲評估 (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="77143-103">Deferred execution and lazy evaluation (LINQ to XML)</span></span>

<span data-ttu-id="77143-104">若要使用延後執行，通常會實作查詢和座標軸運算。</span><span class="sxs-lookup"><span data-stu-id="77143-104">Query and axis operations are often implemented to use deferred execution.</span></span> <span data-ttu-id="77143-105">本文說明延後執行的需求和優點，以及一些執行考慮。</span><span class="sxs-lookup"><span data-stu-id="77143-105">This article explains the requirements and advantages of deferred execution, and some implementation considerations.</span></span>

## <a name="deferred-execution"></a><span data-ttu-id="77143-106">延後執行</span><span class="sxs-lookup"><span data-stu-id="77143-106">Deferred execution</span></span>

<span data-ttu-id="77143-107">延後執行是指延遲評估運算式，直到實際需要其「實現的」\*\* 值為止。</span><span class="sxs-lookup"><span data-stu-id="77143-107">Deferred execution means that the evaluation of an expression is delayed until its *realized* value is actually required.</span></span> <span data-ttu-id="77143-108">當您必須管理大型資料集合，尤其是在包含一系列鏈結之查詢或管理的程式中時，延後執行會明顯改善效能。</span><span class="sxs-lookup"><span data-stu-id="77143-108">Deferred execution can greatly improve performance when you have to manipulate large data collections, especially in programs that contain a series of chained queries or manipulations.</span></span> <span data-ttu-id="77143-109">在最好的情況下，延後執行僅能單一逐一查看來源集合。</span><span class="sxs-lookup"><span data-stu-id="77143-109">In the best case, deferred execution enables only a single iteration through the source collection.</span></span>

<span data-ttu-id="77143-110">LINQ 技術可讓延後執行大量用於 <xref:System.Linq?displayProperty=nameWithType> 核心類別的成員以及各種 LINQ 命名空間中的擴充方法，例如，<xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="77143-110">The LINQ technologies make extensive use of deferred execution in both the members of core <xref:System.Linq?displayProperty=nameWithType> classes and in the extension methods in the various LINQ namespaces, such as <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="77143-111">在 iterator 區塊中使用時，使用語句) 形式的 [yield (c # 參考) ](../../csharp/language-reference/keywords/yield.md) 關鍵字 (，直接在 c # 語言中支援延後執行 `yield-return` 。</span><span class="sxs-lookup"><span data-stu-id="77143-111">Deferred execution is supported directly in the C# language by the [yield (C# Reference)](../../csharp/language-reference/keywords/yield.md) keyword (in the form of the `yield-return` statement) when used within an iterator block.</span></span> <span data-ttu-id="77143-112">此類 Iterator 必須傳回型別 <xref:System.Collections.IEnumerator> 或 <xref:System.Collections.Generic.IEnumerator%601> (或衍生型別) 的集合。</span><span class="sxs-lookup"><span data-stu-id="77143-112">Such an iterator must return a collection of type <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> (or a derived type).</span></span>

## <a name="eager-vs-lazy-evaluation"></a><span data-ttu-id="77143-113">積極與延遲評估</span><span class="sxs-lookup"><span data-stu-id="77143-113">Eager vs. lazy evaluation</span></span>

<span data-ttu-id="77143-114">當您撰寫實作延後執行的方法時，您也必須決定要使用延遲評估或急切評估來實作方法。</span><span class="sxs-lookup"><span data-stu-id="77143-114">When you write a method that implements deferred execution, you also have to decide whether to implement the method using lazy evaluation or eager evaluation.</span></span>

- <span data-ttu-id="77143-115">若為「延遲評估」\*\*，來源集合的單一項目會在每次呼叫 Iterator 時進行處理。</span><span class="sxs-lookup"><span data-stu-id="77143-115">In *lazy evaluation*, a single element of the source collection is processed during each call to the iterator.</span></span> <span data-ttu-id="77143-116">這是實作 Iterator 的一般方式。</span><span class="sxs-lookup"><span data-stu-id="77143-116">This is the typical way in which iterators are implemented.</span></span>
- <span data-ttu-id="77143-117">若為「急切評估」\*\*，第一次呼叫 Iterator 時，就會處理整個集合。</span><span class="sxs-lookup"><span data-stu-id="77143-117">In *eager evaluation*, the first call to the iterator will result in the entire collection being processed.</span></span> <span data-ttu-id="77143-118">同時，可能也需要來源集合的暫存副本。</span><span class="sxs-lookup"><span data-stu-id="77143-118">A temporary copy of the source collection might also be required.</span></span> <span data-ttu-id="77143-119">例如，<xref:System.Linq.Enumerable.OrderBy%2A> 方法必須在傳回第一個項目前，排序整個集合。</span><span class="sxs-lookup"><span data-stu-id="77143-119">For example, the <xref:System.Linq.Enumerable.OrderBy%2A> method has to sort the entire collection before it returns the first element.</span></span>

<span data-ttu-id="77143-120">延遲評估通常會產生較好的效能，因為它會平均分散整個集合評估的負荷處理，並將暫存資料的使用率降到最低。</span><span class="sxs-lookup"><span data-stu-id="77143-120">Lazy evaluation usually yields better performance because it distributes overhead processing evenly throughout the evaluation of the collection and minimizes the use of temporary data.</span></span> <span data-ttu-id="77143-121">當然，對於某些運算而言，沒有具體化中繼結果之外的其他選擇。</span><span class="sxs-lookup"><span data-stu-id="77143-121">Of course, for some operations, there is no other option than to materialize intermediate results.</span></span>

<span data-ttu-id="77143-122">如需在 c # 和 Visual Basic 中進行程式設計延後執行的範例，請參閱 [延後執行範例](deferred-execution-example.md) 。</span><span class="sxs-lookup"><span data-stu-id="77143-122">See [Deferred execution example](deferred-execution-example.md) for an example of programming deferred execution in C# and Visual Basic.</span></span>

## <a name="see-also"></a><span data-ttu-id="77143-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77143-123">See also</span></span>

- [<span data-ttu-id="77143-124">教學課程：在 C 中一起連結查詢#</span><span class="sxs-lookup"><span data-stu-id="77143-124">Tutorial: Chain Queries Together in C#</span></span>](chain-queries-example.md)
- [<span data-ttu-id="77143-125">概念和術語 (功能性轉換) </span><span class="sxs-lookup"><span data-stu-id="77143-125">Concepts and terminology (functional transformation)</span></span>](concepts-terminology-functional-transformation.md)
- [<span data-ttu-id="77143-126">彙總作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="77143-126">Aggregation Operations (C#)</span></span>](../../csharp/programming-guide/concepts/linq/aggregation-operations.md)
- [<span data-ttu-id="77143-127"> (Visual Basic) 的匯總作業 </span><span class="sxs-lookup"><span data-stu-id="77143-127">Aggregation Operations (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)
- [<span data-ttu-id="77143-128">yield (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="77143-128">yield (C# Reference)</span></span>](../../csharp/language-reference/keywords/yield.md)
