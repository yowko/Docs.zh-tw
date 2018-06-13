---
title: 如何：查詢字串中的字元 (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 727a1be7-dbec-4ab8-b414-bc2d56feb6ff
ms.openlocfilehash: db535f55822fa40d8589ddf95f9f78adfa1b6f1e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323075"
---
# <a name="how-to-query-for-characters-in-a-string-linq-c"></a><span data-ttu-id="e8120-102">如何：查詢字串中的字元 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="e8120-102">How to: Query for Characters in a String (LINQ) (C#)</span></span>
<span data-ttu-id="e8120-103">因為 <xref:System.String> 類別會實作泛型 <xref:System.Collections.Generic.IEnumerable%601> 介面，所以可以用字元序列的形式查詢任何字串。</span><span class="sxs-lookup"><span data-stu-id="e8120-103">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="e8120-104">不過，這不是常見的 LINQ 用法。</span><span class="sxs-lookup"><span data-stu-id="e8120-104">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="e8120-105">對於複雜的模式比對作業，使用 <xref:System.Text.RegularExpressions.Regex> 類別。</span><span class="sxs-lookup"><span data-stu-id="e8120-105">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8120-106">範例</span><span class="sxs-lookup"><span data-stu-id="e8120-106">Example</span></span>  
 <span data-ttu-id="e8120-107">下列範例會查詢字串，以判斷它所包含的數字位數。</span><span class="sxs-lookup"><span data-stu-id="e8120-107">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="e8120-108">請注意，查詢會在第一次執行之後「重複使用」。</span><span class="sxs-lookup"><span data-stu-id="e8120-108">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="e8120-109">這可能是因為查詢本身不會儲存任何實際結果。</span><span class="sxs-lookup"><span data-stu-id="e8120-109">This is possible because the query itself does not store any actual results.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="e8120-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="e8120-110">Compiling the Code</span></span>  
 <span data-ttu-id="e8120-111">建立以 .NET Framework 3.5 版或更新版本為目標的專案，該專案包含 System.Core.dll 的參考，以及 System.Linq 和 System.IO 命名空間的 `using` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="e8120-111">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8120-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="e8120-112">See Also</span></span>  
 [<span data-ttu-id="e8120-113">LINQ 和字串 (C#)</span><span class="sxs-lookup"><span data-stu-id="e8120-113">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)  
 [<span data-ttu-id="e8120-114">如何：使用規則運算式合併 LINQ 查詢 (C#)</span><span class="sxs-lookup"><span data-stu-id="e8120-114">How to: Combine LINQ Queries with Regular Expressions (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)
