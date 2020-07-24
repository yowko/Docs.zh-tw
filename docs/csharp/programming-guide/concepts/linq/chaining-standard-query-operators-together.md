---
title: 將標準查詢運算子鏈結在一起 (C#)
description: '這個範例會示範如何在 c # 中將標準查詢運算子連結在一起。 查詢不會具體化中繼結果。'
ms.date: 07/20/2015
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: 41a7e4c7910c783d07181fe16254b0cac6902794
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104070"
---
# <a name="chaining-standard-query-operators-together-c"></a><span data-ttu-id="a2564-104">將標準查詢運算子鏈結在一起 (C#)</span><span class="sxs-lookup"><span data-stu-id="a2564-104">Chaining Standard Query Operators Together (C#)</span></span>
<span data-ttu-id="a2564-105">這是[教學課程：將查詢鏈結在一起 (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md) 教學課程中的最後一個主題。</span><span class="sxs-lookup"><span data-stu-id="a2564-105">This is the final topic in the [Tutorial: Chaining Queries Together (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md) tutorial.</span></span>  
  
 <span data-ttu-id="a2564-106">標準的查詢運算子也可以鏈結在一起。</span><span class="sxs-lookup"><span data-stu-id="a2564-106">The standard query operators can also be chained together.</span></span> <span data-ttu-id="a2564-107">例如，您可以插入 <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> 運算子，也可以用延遲的方式操作。</span><span class="sxs-lookup"><span data-stu-id="a2564-107">For example, you can interject the <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operator, and it also operates in a lazy fashion.</span></span> <span data-ttu-id="a2564-108">但該運算子不會具體化任何中繼結果。</span><span class="sxs-lookup"><span data-stu-id="a2564-108">No intermediate results are materialized by it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2564-109">範例</span><span class="sxs-lookup"><span data-stu-id="a2564-109">Example</span></span>  
 <span data-ttu-id="a2564-110">在此範例中，呼叫 <xref:System.Linq.Enumerable.Where%2A> 前，會先呼叫 `ConvertCollectionToUpperCase` 方法。</span><span class="sxs-lookup"><span data-stu-id="a2564-110">In this example, the <xref:System.Linq.Enumerable.Where%2A> method is called before calling `ConvertCollectionToUpperCase`.</span></span> <span data-ttu-id="a2564-111"><xref:System.Linq.Enumerable.Where%2A> 方法會使用與本教學課程之前範例、`ConvertCollectionToUpperCase` 和 `AppendString` 中所使用之延遲方法幾乎完全相同的方式操作。</span><span class="sxs-lookup"><span data-stu-id="a2564-111">The <xref:System.Linq.Enumerable.Where%2A> method operates in almost exactly the same way as the lazy methods used in previous examples in this tutorial, `ConvertCollectionToUpperCase` and `AppendString`.</span></span>  
  
 <span data-ttu-id="a2564-112">其中一種差異是，在這種情況下，<xref:System.Linq.Enumerable.Where%2A> 方法會逐一查看其來源集合、判斷第一個項目沒有傳遞述詞，然後取得下一個有傳遞的項目。</span><span class="sxs-lookup"><span data-stu-id="a2564-112">One difference is that in this case, the <xref:System.Linq.Enumerable.Where%2A> method iterates through its source collection, determines that the first item does not pass the predicate, and then gets the next item, which does pass.</span></span> <span data-ttu-id="a2564-113">它接著會產生第二個項目。</span><span class="sxs-lookup"><span data-stu-id="a2564-113">It then yields the second item.</span></span>  
  
 <span data-ttu-id="a2564-114">不過，基本概念是一樣的：除非必要，否則系統不會具體化中繼集合。</span><span class="sxs-lookup"><span data-stu-id="a2564-114">However, the basic idea is the same: Intermediate collections are not materialized unless they have to be.</span></span>  
  
 <span data-ttu-id="a2564-115">使用查詢運算式時，會將這些運算式轉換為標準查詢運算子的呼叫，因此適用相同的原則。</span><span class="sxs-lookup"><span data-stu-id="a2564-115">When query expressions are used, they are converted to calls to the standard query operators, and the same principles apply.</span></span>  
  
 <span data-ttu-id="a2564-116">本節中，查詢 Office Open XML 文件的所有範例都使用相同的原則。</span><span class="sxs-lookup"><span data-stu-id="a2564-116">All of the examples in this section that are querying Office Open XML documents use the same principle.</span></span> <span data-ttu-id="a2564-117">延後執行與延遲評估是您必須了解的部分基礎概念，才能有效使用 LINQ (和 LINQ to XML)。</span><span class="sxs-lookup"><span data-stu-id="a2564-117">Deferred execution and lazy evaluation are some of the fundamental concepts that you must understand  to use LINQ (and LINQ to XML) effectively.</span></span>  
  
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
  
 <span data-ttu-id="a2564-118">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="a2564-118">This example produces the following output:</span></span>  
  
```output  
ToUpper: source >abc<  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
