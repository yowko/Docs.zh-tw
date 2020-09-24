---
title: '如何在字串中計算單字的出現次數 (LINQ)  (c # ) '
description: '此範例使用 c # 中的 LINQ 查詢來計算字串中指定單字的出現次數。 它會使用 Split 方法來建立單字陣列。'
ms.date: 07/20/2015
ms.assetid: f8e6f546-7c14-4aa1-8a75-e8d09f3b8ccd
ms.openlocfilehash: b354947c59747e49b5f3d099ebc3ea891fb4af90
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91159068"
---
# <a name="how-to-count-occurrences-of-a-word-in-a-string-linq-c"></a><span data-ttu-id="a25d0-104">如何在字串中計算單字的出現次數 (LINQ)  (c # ) </span><span class="sxs-lookup"><span data-stu-id="a25d0-104">How to count occurrences of a word in a string (LINQ) (C#)</span></span>

<span data-ttu-id="a25d0-105">本例示範如何使用 LINQ 查詢計算字串中指定單字的出現次數。</span><span class="sxs-lookup"><span data-stu-id="a25d0-105">This example shows how to use a LINQ query to count the occurrences of a specified word in a string.</span></span> <span data-ttu-id="a25d0-106">請注意，執行計數要先呼叫 <xref:System.String.Split%2A> 方法來建立文字陣列。</span><span class="sxs-lookup"><span data-stu-id="a25d0-106">Note that to perform the count, first the <xref:System.String.Split%2A> method is called to create an array of words.</span></span> <span data-ttu-id="a25d0-107"><xref:System.String.Split%2A> 方法有效能成本。</span><span class="sxs-lookup"><span data-stu-id="a25d0-107">There is a performance cost to the <xref:System.String.Split%2A> method.</span></span> <span data-ttu-id="a25d0-108">如果字串上唯一的作業是計算字數，您應該考慮改用 <xref:System.Text.RegularExpressions.Regex.Matches%2A> 或 <xref:System.String.IndexOf%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="a25d0-108">If the only operation on the string is to count the words, you should consider using the <xref:System.Text.RegularExpressions.Regex.Matches%2A> or <xref:System.String.IndexOf%2A> methods instead.</span></span> <span data-ttu-id="a25d0-109">不過，如果效能不是重要的問題，或您已分割句子對它執行其他類型的查詢，則使用 LINQ 計算單字或詞組才有意義。</span><span class="sxs-lookup"><span data-stu-id="a25d0-109">However, if performance is not a critical issue, or you have already split the sentence in order to perform other types of queries over it, then it makes sense to use LINQ to count the words or phrases as well.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a25d0-110">範例</span><span class="sxs-lookup"><span data-stu-id="a25d0-110">Example</span></span>  
  
```csharp  
class CountWords  
{  
    static void Main()  
    {  
        string text = @"Historically, the world of data and the world of objects" +  
          @" have not been well integrated. Programmers work in C# or Visual Basic" +  
          @" and also in SQL or XQuery. On the one side are concepts such as classes," +  
          @" objects, fields, inheritance, and .NET APIs. On the other side" +  
          @" are tables, columns, rows, nodes, and separate languages for dealing with" +  
          @" them. Data types often require translation between the two worlds; there are" +  
          @" different standard functions. Because the object world has no notion of query, a" +  
          @" query can only be represented as a string without compile-time type checking or" +  
          @" IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to" +  
          @" objects in memory is often tedious and error-prone.";  
  
        string searchTerm = "data";  
  
        //Convert the string into an array of words  
        string[] source = text.Split(new char[] { '.', '?', '!', ' ', ';', ':', ',' }, StringSplitOptions.RemoveEmptyEntries);  
  
        // Create the query.  Use ToLowerInvariant to match "data" and "Data"
        var matchQuery = from word in source  
                         where word.ToLowerInvariant() == searchTerm.ToLowerInvariant()  
                         select word;  
  
        // Count the matches, which executes the query.  
        int wordCount = matchQuery.Count();  
        Console.WriteLine("{0} occurrences(s) of the search term \"{1}\" were found.", wordCount, searchTerm);  
  
        // Keep console window open in debug mode  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
   3 occurrences(s) of the search term "data" were found.  
*/  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a25d0-111">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="a25d0-111">Compiling the Code</span></span>  

 <span data-ttu-id="a25d0-112">建立 C# 主控台應用程式專案，以及具有 `using` 指示詞的 System.Linq 和 System.IO 命名空間。</span><span class="sxs-lookup"><span data-stu-id="a25d0-112">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a25d0-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a25d0-113">See also</span></span>

- [<span data-ttu-id="a25d0-114">LINQ 和字串 (C#)</span><span class="sxs-lookup"><span data-stu-id="a25d0-114">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
