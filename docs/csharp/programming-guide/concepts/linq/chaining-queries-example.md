---
title: 鏈結查詢範例 (C#)
description: '這個範例顯示當您將兩個在 c # 中使用延後執行和延遲評估的查詢鏈在一起時，會發生什麼情況。'
ms.date: 07/20/2015
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
ms.openlocfilehash: 0cfcfe1c8f537778fd1ef909277d95d83991af51
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105542"
---
# <a name="chaining-queries-example-c"></a><span data-ttu-id="25e8a-103">鏈結查詢範例 (C#)</span><span class="sxs-lookup"><span data-stu-id="25e8a-103">Chaining Queries Example (C#)</span></span>
<span data-ttu-id="25e8a-104">這個範例會在先前的範例上建置，然後在將同時使用延後執行與延遲評估的兩個查詢鏈結在一起時，顯示發生什麼狀況。</span><span class="sxs-lookup"><span data-stu-id="25e8a-104">This example builds on the previous example and shows what happens when you chain together two queries that both use deferred execution and lazy evaluation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25e8a-105">範例</span><span class="sxs-lookup"><span data-stu-id="25e8a-105">Example</span></span>  
 <span data-ttu-id="25e8a-106">在此範例中，會介紹另一個擴充方法 `AppendString`，這個擴充方法會將指定的字串附加到來源集合中的每個字串，然後產生新的字串。</span><span class="sxs-lookup"><span data-stu-id="25e8a-106">In this example, another extension method is introduced, `AppendString`, which appends a specified string onto every string in the source collection, and then yields the new strings.</span></span>  
  
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
  
 <span data-ttu-id="25e8a-107">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="25e8a-107">This example produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="25e8a-108">在此範例中，您可以看到每個擴充方法會針對來源集合中的每個項目，一次運算一個。</span><span class="sxs-lookup"><span data-stu-id="25e8a-108">In this example, you can see that each extension method operates one at a time for each item in the source collection.</span></span>  
  
 <span data-ttu-id="25e8a-109">從這個範例應該清楚知道的是，即使我們已經將產生集合的查詢鏈結在一起，還是不會具體化任何中繼集合。</span><span class="sxs-lookup"><span data-stu-id="25e8a-109">What should be clear from this example is that even though we have chained together queries that yield collections, no intermediate collections are materialized.</span></span> <span data-ttu-id="25e8a-110">但是，每個項目都會從一個延遲方法傳遞到下一個延遲方法。</span><span class="sxs-lookup"><span data-stu-id="25e8a-110">Instead, each item is passed from one lazy method to the next.</span></span> <span data-ttu-id="25e8a-111">這會使記憶體使用量比先取得一個字串陣列，然後建立已經轉換為大寫的另一個字串陣列，最後建立每個字串都已經附加驚嘆號的第三個字串陣列這種方法小很多。</span><span class="sxs-lookup"><span data-stu-id="25e8a-111">This results in a much smaller memory footprint than an approach that would first take one array of strings, then create a second array of strings that have been converted to uppercase, and finally create a third array of strings where each string has the exclamation points appended to it.</span></span>  
  
 <span data-ttu-id="25e8a-112">本教學課程中的下一個主題說明中繼具體化：</span><span class="sxs-lookup"><span data-stu-id="25e8a-112">The next topic in this tutorial illustrates intermediate materialization:</span></span>  
  
- [<span data-ttu-id="25e8a-113">中繼具體化 (C#)</span><span class="sxs-lookup"><span data-stu-id="25e8a-113">Intermediate Materialization (C#)</span></span>](./intermediate-materialization.md)  
  
## <a name="see-also"></a><span data-ttu-id="25e8a-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="25e8a-114">See also</span></span>

- [<span data-ttu-id="25e8a-115">教學課程：將查詢鏈結在一起 (C#)</span><span class="sxs-lookup"><span data-stu-id="25e8a-115">Tutorial: Chaining Queries Together (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
