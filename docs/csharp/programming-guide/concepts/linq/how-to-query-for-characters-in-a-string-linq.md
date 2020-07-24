---
title: '如何查詢字串中的字元（LINQ）（c #）'
description: '您可以使用 LINQ 中的字元序列來查詢字串。 這個 c # 範例會查詢字串，以判斷它所包含的數位位數。'
ms.date: 07/20/2015
ms.assetid: 727a1be7-dbec-4ab8-b414-bc2d56feb6ff
ms.openlocfilehash: 3512be7c30843fcd8e881eab59761706a84a3ac8
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104558"
---
# <a name="how-to-query-for-characters-in-a-string-linq-c"></a><span data-ttu-id="dc1e5-104">如何查詢字串中的字元（LINQ）（c #）</span><span class="sxs-lookup"><span data-stu-id="dc1e5-104">How to query for characters in a string (LINQ) (C#)</span></span>
<span data-ttu-id="dc1e5-105">因為 <xref:System.String> 類別會實作泛型 <xref:System.Collections.Generic.IEnumerable%601> 介面，所以可以用字元序列的形式查詢任何字串。</span><span class="sxs-lookup"><span data-stu-id="dc1e5-105">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="dc1e5-106">不過，這不是常見的 LINQ 用法。</span><span class="sxs-lookup"><span data-stu-id="dc1e5-106">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="dc1e5-107">對於複雜的模式比對作業，使用 <xref:System.Text.RegularExpressions.Regex> 類別。</span><span class="sxs-lookup"><span data-stu-id="dc1e5-107">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc1e5-108">範例</span><span class="sxs-lookup"><span data-stu-id="dc1e5-108">Example</span></span>  
 <span data-ttu-id="dc1e5-109">下列範例會查詢字串，以判斷它所包含的數字位數。</span><span class="sxs-lookup"><span data-stu-id="dc1e5-109">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="dc1e5-110">請注意，查詢會在第一次執行之後「重複使用」。</span><span class="sxs-lookup"><span data-stu-id="dc1e5-110">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="dc1e5-111">這可能是因為查詢本身不會儲存任何實際結果。</span><span class="sxs-lookup"><span data-stu-id="dc1e5-111">This is possible because the query itself does not store any actual results.</span></span>  
  
```csharp  
class QueryAString  
{  
    static void Main()  
    {  
        string aString = "ABCDE99F-J74-12-89A";  
  
        // Select only those characters that are numbers  
        IEnumerable<char> stringQuery =  
          from ch in aString  
          where Char.IsDigit(ch)  
          select ch;  
  
        // Execute the query  
        foreach (char c in stringQuery)  
            Console.Write(c + " ");  
  
        // Call the Count method on the existing query.  
        int count = stringQuery.Count();  
        Console.WriteLine("Count = {0}", count);  
  
        // Select all characters before the first '-'  
        IEnumerable<char> stringQuery2 = aString.TakeWhile(c => c != '-');  
  
        // Execute the second query  
        foreach (char c in stringQuery2)  
            Console.Write(c);  
  
        Console.WriteLine(System.Environment.NewLine + "Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
  Output: 9 9 7 4 1 2 8 9  
  Count = 8  
  ABCDE99F  
*/  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="dc1e5-112">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="dc1e5-112">Compiling the Code</span></span>  
 <span data-ttu-id="dc1e5-113">建立 C# 主控台應用程式專案，以及具有 `using` 指示詞的 System.Linq 和 System.IO 命名空間。</span><span class="sxs-lookup"><span data-stu-id="dc1e5-113">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc1e5-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="dc1e5-114">See also</span></span>

- [<span data-ttu-id="dc1e5-115">LINQ 和字串 (C#)</span><span class="sxs-lookup"><span data-stu-id="dc1e5-115">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="dc1e5-116">如何結合 LINQ 查詢與正則運算式（c #）</span><span class="sxs-lookup"><span data-stu-id="dc1e5-116">How to combine LINQ queries with regular expressions (C#)</span></span>](./how-to-combine-linq-queries-with-regular-expressions.md)
