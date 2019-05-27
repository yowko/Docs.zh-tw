---
title: 中繼具體化 (C#)
ms.date: 07/20/2015
ms.assetid: 7922d38f-5044-41cf-8e17-7173d6553a5e
ms.openlocfilehash: fa1e11c6b4cacff3b5a5a7ca1cc311f5fabda6c7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64596609"
---
# <a name="intermediate-materialization-c"></a><span data-ttu-id="a83b1-102">中繼具體化 (C#)</span><span class="sxs-lookup"><span data-stu-id="a83b1-102">Intermediate Materialization (C#)</span></span>
<span data-ttu-id="a83b1-103">如果不小心，在某些情況下，造成查詢中的集合過早具體化，可能會徹底改變應用程式的記憶體與效能設定檔。</span><span class="sxs-lookup"><span data-stu-id="a83b1-103">If you are not careful, in some situations you can drastically alter the memory and performance profile of your application by causing premature materialization of collections in your queries.</span></span> <span data-ttu-id="a83b1-104">有些標準查詢運算子會在產生單一項目前，造成其來源集合具體化。</span><span class="sxs-lookup"><span data-stu-id="a83b1-104">Some standard query operators cause materialization of their source collection before yielding a single element.</span></span> <span data-ttu-id="a83b1-105">例如，<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> 會先逐一查看其完整的來源集合，然後排序所有的項目，最後產生第一個項目。</span><span class="sxs-lookup"><span data-stu-id="a83b1-105">For example, <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> first iterates through its entire source collection, then sorts all items, and then finally yields the first item.</span></span> <span data-ttu-id="a83b1-106">也就是說，取得順序集合的第一個項目會高度耗費資源；之後每個項目則不會高度耗費資源。</span><span class="sxs-lookup"><span data-stu-id="a83b1-106">This means that it is expensive to get the first item of an ordered collection; each item thereafter is not expensive.</span></span> <span data-ttu-id="a83b1-107">這很合理：該查詢運算子不可能以其他方式執行。</span><span class="sxs-lookup"><span data-stu-id="a83b1-107">This makes sense: It would be impossible for that query operator to do otherwise.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a83b1-108">範例</span><span class="sxs-lookup"><span data-stu-id="a83b1-108">Example</span></span>  
 <span data-ttu-id="a83b1-109">此範例會改變先前的範例。</span><span class="sxs-lookup"><span data-stu-id="a83b1-109">This example alters the previous example.</span></span> <span data-ttu-id="a83b1-110">`AppendString` 方法會先呼叫 <xref:System.Linq.Enumerable.ToList%2A>，然後再逐一查看來源。</span><span class="sxs-lookup"><span data-stu-id="a83b1-110">The `AppendString` method calls <xref:System.Linq.Enumerable.ToList%2A> before iterating through the source.</span></span> <span data-ttu-id="a83b1-111">這會導致具體化。</span><span class="sxs-lookup"><span data-stu-id="a83b1-111">This causes materialization.</span></span>  
  
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
  
 <span data-ttu-id="a83b1-112">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="a83b1-112">This example produces the following output:</span></span>  
  
```  
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
  
 <span data-ttu-id="a83b1-113">在此範例中，您可以了解呼叫 <xref:System.Linq.Enumerable.ToList%2A> 會造成 `AppendString` 列舉其完整來源，然後再產生第一個項目。</span><span class="sxs-lookup"><span data-stu-id="a83b1-113">In this example, you can see that the call to <xref:System.Linq.Enumerable.ToList%2A> causes `AppendString` to enumerate its entire source before yielding the first item.</span></span> <span data-ttu-id="a83b1-114">如果來源是大型陣列，這會明顯改變應用程式的記憶體設定檔。</span><span class="sxs-lookup"><span data-stu-id="a83b1-114">If the source were a large array, this would significantly alter the memory profile of the application.</span></span>  
  
 <span data-ttu-id="a83b1-115">標準的查詢運算子也可以鏈結在一起。</span><span class="sxs-lookup"><span data-stu-id="a83b1-115">Standard query operators can also be chained together.</span></span> <span data-ttu-id="a83b1-116">此教學課程中的最後一個主題有加以說明。</span><span class="sxs-lookup"><span data-stu-id="a83b1-116">The final topic in this tutorial illustrates this.</span></span>  
  
- [<span data-ttu-id="a83b1-117">將標準查詢運算子鏈結在一起 (C#)</span><span class="sxs-lookup"><span data-stu-id="a83b1-117">Chaining Standard Query Operators Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-standard-query-operators-together.md)  
  
## <a name="see-also"></a><span data-ttu-id="a83b1-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a83b1-118">See also</span></span>

- [<span data-ttu-id="a83b1-119">教學課程：將查詢鏈結在一起 (C#)</span><span class="sxs-lookup"><span data-stu-id="a83b1-119">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
