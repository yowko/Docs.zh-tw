---
title: '中繼具體化 (c # ) '
description: 瞭解如何使用一些標準的查詢運算子，會導致查詢中的集合具體化，並大幅改變應用程式的記憶體和效能設定檔。
ms.date: 07/20/2015
ms.assetid: 7922d38f-5044-41cf-8e17-7173d6553a5e
ms.openlocfilehash: 8dca4bb29886973762351049d06bcf5d3ba352db
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552120"
---
# <a name="intermediate-materialization-c"></a><span data-ttu-id="41eb2-103">中繼具體化 (c # ) </span><span class="sxs-lookup"><span data-stu-id="41eb2-103">Intermediate materialization (C#)</span></span>

<span data-ttu-id="41eb2-104">如果您不小心，在某些情況下，會導致查詢中的集合過早具體化，以大幅改變應用程式的記憶體和效能設定檔。</span><span class="sxs-lookup"><span data-stu-id="41eb2-104">If you're not careful you can, in some situations, drastically alter the memory and performance profile of your application by causing premature materialization of collections in your queries.</span></span> <span data-ttu-id="41eb2-105">有些標準查詢運算子會在產生單一項目前，造成其來源集合具體化。</span><span class="sxs-lookup"><span data-stu-id="41eb2-105">Some standard query operators cause materialization of their source collection before yielding a single element.</span></span> <span data-ttu-id="41eb2-106">例如，<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> 會先逐一查看其完整的來源集合，然後排序所有的項目，最後產生第一個項目。</span><span class="sxs-lookup"><span data-stu-id="41eb2-106">For example, <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> first iterates through its entire source collection, then sorts all items, and then finally yields the first item.</span></span> <span data-ttu-id="41eb2-107">這表示取得已排序集合的第一個專案是很昂貴的。之後的每個專案都不耗費資源。</span><span class="sxs-lookup"><span data-stu-id="41eb2-107">This means that it's expensive to get the first item of an ordered collection; each item thereafter isn't expensive.</span></span> <span data-ttu-id="41eb2-108">這很合理：否則，該查詢運算子不可能這麼做。</span><span class="sxs-lookup"><span data-stu-id="41eb2-108">This makes sense: It would be impossible for that query operator to do otherwise.</span></span>

## <a name="example-add-a-method-that-calls-tolist-causing-materialization"></a><span data-ttu-id="41eb2-109">範例：加入呼叫的方法 `ToList` ，造成具體化</span><span class="sxs-lookup"><span data-stu-id="41eb2-109">Example: Add a method that calls `ToList`, causing materialization</span></span>

<span data-ttu-id="41eb2-110">此範例會改變 [ (c # ) 的鏈查詢範例 ](chain-queries-example.md)中的範例： `AppendString` 方法會在 <xref:System.Linq.Enumerable.ToList%2A> 反覆運算來源之前變更為呼叫，這會造成具體化。</span><span class="sxs-lookup"><span data-stu-id="41eb2-110">This example alters the example in [Chain queries example (C#)](chain-queries-example.md): the `AppendString` method is changed to call <xref:System.Linq.Enumerable.ToList%2A> before iterating through the source, which causes materialization.</span></span>

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
        // the following statement materializes the source collection in a List<T>
        // before iterating through it
        foreach (string str in source.ToList())
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

 <span data-ttu-id="41eb2-111">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="41eb2-111">This example produces the following output:</span></span>

```output
ToUpper: source >abc<
ToUpper: source >def<
ToUpper: source >ghi<
AppendString: source >ABC<
Main: str >ABC!!!<

AppendString: source >DEF<
Main: str >DEF!!!<

AppendString: source >GHI<
Main: str >GHI!!!<
```

<span data-ttu-id="41eb2-112">在此範例中，您可以了解呼叫 <xref:System.Linq.Enumerable.ToList%2A> 會造成 `AppendString` 列舉其完整來源，然後再產生第一個項目。</span><span class="sxs-lookup"><span data-stu-id="41eb2-112">In this example, you can see that the call to <xref:System.Linq.Enumerable.ToList%2A> causes `AppendString` to enumerate its entire source before yielding the first item.</span></span> <span data-ttu-id="41eb2-113">如果來源是大型陣列，這會明顯改變應用程式的記憶體設定檔。</span><span class="sxs-lookup"><span data-stu-id="41eb2-113">If the source were a large array, this would significantly alter the memory profile of the application.</span></span>

<span data-ttu-id="41eb2-114">標準查詢運算子也可以連結在一起，如本教學課程的最後一篇文章所示：</span><span class="sxs-lookup"><span data-stu-id="41eb2-114">Standard query operators can also be chained together as shown in the final article in this tutorial:</span></span>

- [<span data-ttu-id="41eb2-115">將標準查詢運算子一起 (c # ) </span><span class="sxs-lookup"><span data-stu-id="41eb2-115">Chain standard query operators together (C#)</span></span>](chain-standard-query-operators-together.md)

## <a name="see-also"></a><span data-ttu-id="41eb2-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41eb2-116">See also</span></span>

- [<span data-ttu-id="41eb2-117">延後執行和延遲評估</span><span class="sxs-lookup"><span data-stu-id="41eb2-117">Deferred execution and lazy evaluation</span></span>](deferred-execution-lazy-evaluation.md)
