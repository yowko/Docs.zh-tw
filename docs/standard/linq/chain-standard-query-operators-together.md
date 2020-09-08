---
title: '將標準查詢運算子一起 (c # ) -LINQ to XML'
description: 瞭解如何將查詢運算子串聯在一起。
ms.date: 07/20/2015
dev_langs:
- csharp
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: ed3ca44c853ebbeee690cb31232a13e35b383d1b
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552101"
---
# <a name="chain-standard-query-operators-together-c-linq-to-xml"></a><span data-ttu-id="7c324-103">將標準查詢運算子一起 (c # )  (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="7c324-103">Chain standard query operators together (C#) (LINQ to XML)</span></span>

<span data-ttu-id="7c324-104">標準查詢運算子可以連結在一起。</span><span class="sxs-lookup"><span data-stu-id="7c324-104">The standard query operators can be chained together.</span></span> <span data-ttu-id="7c324-105">例如，您可以插入子句所叫 <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> 用的運算子 (`where`) ，它會以延遲的方式運作，也就是說，它不會具體化中繼結果。</span><span class="sxs-lookup"><span data-stu-id="7c324-105">For example, you can interject the <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operator (invoked by the `where` clause), and it operates in a lazy fashion; that is, no intermediate results are materialized by it.</span></span>

## <a name="example-interject-a-where-clause"></a><span data-ttu-id="7c324-106">範例：插入 where 子句</span><span class="sxs-lookup"><span data-stu-id="7c324-106">Example: Interject a where clause</span></span>

<span data-ttu-id="7c324-107">在此範例中，呼叫 <xref:System.Linq.Enumerable.Where%2A> 前，會先呼叫 `ConvertCollectionToUpperCase` 方法。</span><span class="sxs-lookup"><span data-stu-id="7c324-107">In this example, the <xref:System.Linq.Enumerable.Where%2A> method is called before calling `ConvertCollectionToUpperCase`.</span></span> <span data-ttu-id="7c324-108"><xref:System.Linq.Enumerable.Where%2A> 方法會使用與本教學課程之前範例、`ConvertCollectionToUpperCase` 和 `AppendString` 中所使用之延遲方法幾乎完全相同的方式操作。</span><span class="sxs-lookup"><span data-stu-id="7c324-108">The <xref:System.Linq.Enumerable.Where%2A> method operates in almost exactly the same way as the lazy methods used in previous examples in this tutorial, `ConvertCollectionToUpperCase` and `AppendString`.</span></span>

<span data-ttu-id="7c324-109">其中一個差異是，在此情況下， <xref:System.Linq.Enumerable.Where%2A> 方法會逐一查看其來源集合，判斷第一個專案不會通過述詞，然後取得下一個專案，而該專案會通過。</span><span class="sxs-lookup"><span data-stu-id="7c324-109">One difference is that in this case, the <xref:System.Linq.Enumerable.Where%2A> method iterates through its source collection, determines that the first item doesn't pass the predicate, and then gets the next item, which does pass.</span></span> <span data-ttu-id="7c324-110">它接著會產生第二個項目。</span><span class="sxs-lookup"><span data-stu-id="7c324-110">It then yields the second item.</span></span>

<span data-ttu-id="7c324-111">不過，基本概念是相同的：不會具體化中繼集合，除非它們必須是。</span><span class="sxs-lookup"><span data-stu-id="7c324-111">However, the basic idea is the same: intermediate collections aren't materialized unless they have to be.</span></span>

<span data-ttu-id="7c324-112">使用查詢運算式時，會將它們轉換為對標準查詢運算子的呼叫，並套用相同的原則。</span><span class="sxs-lookup"><span data-stu-id="7c324-112">When query expressions are used, they're converted to calls to the standard query operators, and the same principles apply.</span></span>

<span data-ttu-id="7c324-113">本節中，查詢 Office Open XML 文件的所有範例都使用相同的原則。</span><span class="sxs-lookup"><span data-stu-id="7c324-113">All of the examples in this section that are querying Office Open XML documents use the same principle.</span></span> <span data-ttu-id="7c324-114">延後執行和延遲評估是一些基本概念，您必須瞭解這些概念才能使用 LINQ，並有效 LINQ to XML。</span><span class="sxs-lookup"><span data-stu-id="7c324-114">Deferred execution and lazy evaluation are some of the fundamental concepts that you must understand to use LINQ, and LINQ to XML, effectively.</span></span>

```csharp
public static class LocalExtensions
{
    public static IEnumerable<string>
      ConvertCollectionToUpperCase(this IEnumerable<string> source)
    {
        foreach (string str in source)
        {
            Console.WriteLine("ToUpper: source >{0}<", str);
            yield return str.ToUpper();
        }
    }

    public static IEnumerable<string>
      AppendString(this IEnumerable<string> source, string stringToAppend)
    {
        foreach (string str in source)
        {
            Console.WriteLine("AppendString: source >{0}<", str);
            yield return str + stringToAppend;
        }
    }
}

class Program
{
    static void Main(string[] args)
    {
        string[] stringArray = { "abc", "def", "ghi" };

        IEnumerable<string> q1 =
            from s in stringArray.ConvertCollectionToUpperCase()
            where s.CompareTo("D") >= 0
            select s;

        IEnumerable<string> q2 =
            from s in q1.AppendString("!!!")
            select s;

        foreach (string str in q2)
        {
            Console.WriteLine("Main: str >{0}<", str);
            Console.WriteLine();
        }
    }
}
```

<span data-ttu-id="7c324-115">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="7c324-115">This example produces the following output:</span></span>

```output
ToUpper: source >abc<
ToUpper: source >def<
AppendString: source >DEF<
Main: str >DEF!!!<

ToUpper: source >ghi<
AppendString: source >GHI<
Main: str >GHI!!!<
```

<span data-ttu-id="7c324-116">這是本教學課程中的最後一篇文章 [： (c # ) ](chain-queries-example.md) 教學課程將查詢連結在一起。</span><span class="sxs-lookup"><span data-stu-id="7c324-116">This is the final article in the [Tutorial: Chaining Queries Together (C#)](chain-queries-example.md) tutorial.</span></span>
