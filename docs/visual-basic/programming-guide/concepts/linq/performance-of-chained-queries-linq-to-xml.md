---
title: 已鏈結之查詢 (LINQ to XML) 的效能 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 589f2adc-69f9-404d-b9d6-4c28dabea7f7
ms.openlocfilehash: 8634ca224f5892918721996114649c392a5080a0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665867"
---
# <a name="performance-of-chained-queries-linq-to-xml-visual-basic"></a><span data-ttu-id="8834f-102">已鏈結之查詢 (LINQ to XML) 的效能 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8834f-102">Performance of Chained Queries (LINQ to XML) (Visual Basic)</span></span>

<span data-ttu-id="8834f-103">LINQ (和 LINQ to XML) 其中一個最重要的優點在於，鏈結查詢的執行效能就如同單一較大且更複雜的查詢。</span><span class="sxs-lookup"><span data-stu-id="8834f-103">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single larger, more complicated query.</span></span>

<span data-ttu-id="8834f-104">鏈結查詢是指使用其他查詢當做其來源的查詢。</span><span class="sxs-lookup"><span data-stu-id="8834f-104">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="8834f-105">例如，在下列簡單程式碼中，`query2` 具有 `query1` 當做其來源：</span><span class="sxs-lookup"><span data-stu-id="8834f-105">For example, in the following simple code, `query2` has `query1` as its source:</span></span>

```vb
Dim root As New XElement("Root", New XElement("Child", 1), New XElement("Child", 2), New XElement("Child", 3), New XElement("Child", 4))

Dim query1 = From x In root.Elements("Child") Where CInt(x) >= 3x

Dim query2 = From e In query1 Where CInt(e) Mod 2 = 0e

For Each i As var In query2
    Console.WriteLine("{0}", CInt(i))
Next
```

<span data-ttu-id="8834f-106">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="8834f-106">This example produces the following output:</span></span>

```
4
```

<span data-ttu-id="8834f-107">這個鏈結查詢會與逐一查看連結串列 (Linked List) 提供相同的效能設定檔。</span><span class="sxs-lookup"><span data-stu-id="8834f-107">This chained query provides the same performance profile as iterating through a linked list.</span></span>

- <span data-ttu-id="8834f-108"><xref:System.Xml.Linq.XContainer.Elements%2A> 軸基本上與逐一查看連結串列具有相同的效能。</span><span class="sxs-lookup"><span data-stu-id="8834f-108">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="8834f-109"><xref:System.Xml.Linq.XContainer.Elements%2A> 會實作成延後執行的 Iterator。</span><span class="sxs-lookup"><span data-stu-id="8834f-109"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="8834f-110">這表示，除了逐一查看連結串列以外，它會執行一些工作，例如配置 Iterator 物件和追蹤執行狀態。</span><span class="sxs-lookup"><span data-stu-id="8834f-110">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="8834f-111">這項工作可分成兩個分類：在設定 Iterator 時完成的工作，以及在每次反覆運算期間完成的工作。</span><span class="sxs-lookup"><span data-stu-id="8834f-111">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="8834f-112">設定工作是小型且固定的工作量，而在每次反覆運算期間完成的工作則與來源集合中的項目數成正比。</span><span class="sxs-lookup"><span data-stu-id="8834f-112">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>

- <span data-ttu-id="8834f-113">在 `query1` 中，`Where` 子句會讓查詢呼叫 <xref:System.Linq.Enumerable.Where%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="8834f-113">In `query1`, the `Where` clause causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="8834f-114">這個方法也會實作成 Iterator。</span><span class="sxs-lookup"><span data-stu-id="8834f-114">This method is also implemented as an iterator.</span></span> <span data-ttu-id="8834f-115">設定工作包含具現化將參考 Lambda 運算式的委派 (Delegate)，以及進行 Iterator 的一般設定。</span><span class="sxs-lookup"><span data-stu-id="8834f-115">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="8834f-116">進行每次反覆運算時，系統會呼叫此委派來執行述詞 (Predicate)。</span><span class="sxs-lookup"><span data-stu-id="8834f-116">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="8834f-117">設定工作以及在每次反覆運算期間完成的工作與逐一查看軸時完成的工作很相似。</span><span class="sxs-lookup"><span data-stu-id="8834f-117">The setup work and the work done during each iteration is the similar to the work done while iterating through the axis.</span></span>

- <span data-ttu-id="8834f-118">在 `query1` 中，select 子句會讓查詢呼叫 <xref:System.Linq.Enumerable.Select%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="8834f-118">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="8834f-119">這個方法與 <xref:System.Linq.Enumerable.Where%2A> 方法具有相同的效能設定檔。</span><span class="sxs-lookup"><span data-stu-id="8834f-119">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>

- <span data-ttu-id="8834f-120">在 `query2` 中，`Where` 子句和 `Select` 子句都具有相同的效能設定檔，如同 `query1`。</span><span class="sxs-lookup"><span data-stu-id="8834f-120">In `query2`, both the `Where` clause and the `Select` clause have the same performance profile as in `query1`.</span></span>

 <span data-ttu-id="8834f-121">因此，逐一查看 `query2` 的作業會直接與第一個查詢之來源中的項目數成正比 (亦即，線性時間)。</span><span class="sxs-lookup"><span data-stu-id="8834f-121">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span>

## <a name="see-also"></a><span data-ttu-id="8834f-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8834f-122">See also</span></span>

- [<span data-ttu-id="8834f-123">效能 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8834f-123">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
