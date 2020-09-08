---
title: " (c # ) 的連鎖查詢範例-LINQ to XML"
description: 瞭解當您將兩個同時使用延後執行和延遲評估的查詢串聯在一起時，會發生什麼事。
ms.date: 07/20/2015
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
ms.openlocfilehash: c0bbab9061b98eda15523f8a8e64e997bde8b307
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552271"
---
# <a name="chain-queries-example-c-linq-to-xml"></a><span data-ttu-id="289eb-103"> (c # )  (LINQ to XML 的連鎖查詢範例) </span><span class="sxs-lookup"><span data-stu-id="289eb-103">Chain queries example (C#) (LINQ to XML)</span></span>

<span data-ttu-id="289eb-104">此範例以 [延後執行範例](deferred-execution-example.md) 中的範例為基礎，並顯示當您將兩個同時使用延後執行和延遲評估的查詢串連在一起時，會發生什麼事。</span><span class="sxs-lookup"><span data-stu-id="289eb-104">This example builds on the example in [Deferred execution example](deferred-execution-example.md) and shows what happens when you chain together two queries that both use deferred execution and lazy evaluation.</span></span>

## <a name="example-add-a-second-extension-method-that-uses-yield-return-to-defer-execution"></a><span data-ttu-id="289eb-105">範例：新增第二個使用的擴充方法 `yield return` 來順延強制</span><span class="sxs-lookup"><span data-stu-id="289eb-105">Example: Add a second extension method that uses `yield return` to defer execution</span></span>

<span data-ttu-id="289eb-106">在此範例中，會引進另一個擴充方法，此方法會將 `AppendString` 指定的字串附加至來源集合中的每個字串，然後產生已變更的字串。</span><span class="sxs-lookup"><span data-stu-id="289eb-106">In this example, another extension method is introduced, `AppendString`, which appends a specified string onto every string in the source collection, and then yields the changed string.</span></span>

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

 <span data-ttu-id="289eb-107">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="289eb-107">This example produces the following output:</span></span>

```output
ToUpper: source >abc<
AppendString: source >ABC<
Main: str >ABC!!!<

ToUpper: source >def<
AppendString: source >DEF<
Main: str >DEF!!!<

ToUpper: source >ghi<
AppendString: source >GHI<
Main: str >GHI!!!<
```

<span data-ttu-id="289eb-108">在此範例中，您可以看到每個擴充方法會針對來源集合中的每個項目，一次運算一個。</span><span class="sxs-lookup"><span data-stu-id="289eb-108">In this example, you can see that each extension method operates one at a time for each item in the source collection.</span></span>

<span data-ttu-id="289eb-109">從這個範例應該清楚知道的是，即使我們已經將產生集合的查詢鏈結在一起，還是不會具體化任何中繼集合。</span><span class="sxs-lookup"><span data-stu-id="289eb-109">What should be clear from this example is that even though we have chained together queries that yield collections, no intermediate collections are materialized.</span></span> <span data-ttu-id="289eb-110">但是，每個項目都會從一個延遲方法傳遞到下一個延遲方法。</span><span class="sxs-lookup"><span data-stu-id="289eb-110">Instead, each item is passed from one lazy method to the next.</span></span> <span data-ttu-id="289eb-111">這會使記憶體使用量比先取得一個字串陣列，然後建立已經轉換為大寫的另一個字串陣列，最後建立每個字串都已經附加驚嘆號的第三個字串陣列這種方法小很多。</span><span class="sxs-lookup"><span data-stu-id="289eb-111">This results in a much smaller memory footprint than an approach that would first take one array of strings, then create a second array of strings that have been converted to uppercase, and finally create a third array of strings where each string has the exclamation points appended to it.</span></span>

<span data-ttu-id="289eb-112">本教學課程的下一篇文章說明中繼具體化：</span><span class="sxs-lookup"><span data-stu-id="289eb-112">The next article in this tutorial illustrates intermediate materialization:</span></span>

- [<span data-ttu-id="289eb-113">中繼具體化 (c # ) </span><span class="sxs-lookup"><span data-stu-id="289eb-113">Intermediate materialization (C#)</span></span>](intermediate-materialization.md)

## <a name="see-also"></a><span data-ttu-id="289eb-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="289eb-114">See also</span></span>

- [<span data-ttu-id="289eb-115">延後執行和延遲評估</span><span class="sxs-lookup"><span data-stu-id="289eb-115">Deferred execution and lazy evaluation</span></span>](deferred-execution-lazy-evaluation.md)
