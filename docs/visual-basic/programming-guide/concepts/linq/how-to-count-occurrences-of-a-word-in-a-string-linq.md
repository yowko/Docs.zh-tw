---
title: "如何︰ 統計某個字在字串 (LINQ) (Visual Basic) 中的出現次數 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: bc367e46-f7cc-45f9-936f-754e661b7bb9
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 5697e52729287a09f1afe993c7b1c1d0c9a6507b
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-count-occurrences-of-a-word-in-a-string-linq-visual-basic"></a><span data-ttu-id="74e23-102">如何︰ 統計某個字在字串 (LINQ) (Visual Basic) 中的出現次數</span><span class="sxs-lookup"><span data-stu-id="74e23-102">How to: Count Occurrences of a Word in a String (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="74e23-103">這個範例示範如何使用 LINQ 查詢字串中指定單字的出現次數。</span><span class="sxs-lookup"><span data-stu-id="74e23-103">This example shows how to use a LINQ query to count the occurrences of a specified word in a string.</span></span> <span data-ttu-id="74e23-104">請注意，第一次執行計數，<xref:System.String.Split%2A>會呼叫方法來建立文字陣列。</xref:System.String.Split%2A></span><span class="sxs-lookup"><span data-stu-id="74e23-104">Note that to perform the count, first the <xref:System.String.Split%2A> method is called to create an array of words.</span></span> <span data-ttu-id="74e23-105">效能的費用<xref:System.String.Split%2A>方法。</xref:System.String.Split%2A></span><span class="sxs-lookup"><span data-stu-id="74e23-105">There is a performance cost to the <xref:System.String.Split%2A> method.</span></span> <span data-ttu-id="74e23-106">如果在字串上的唯一操作來統計字數，您應該考慮使用<xref:System.Text.RegularExpressions.Regex.Matches%2A>或<xref:System.String.IndexOf%2A>方法而。</xref:System.String.IndexOf%2A> </xref:System.Text.RegularExpressions.Regex.Matches%2A></span><span class="sxs-lookup"><span data-stu-id="74e23-106">If the only operation on the string is to count the words, you should consider using the <xref:System.Text.RegularExpressions.Regex.Matches%2A> or <xref:System.String.IndexOf%2A> methods instead.</span></span> <span data-ttu-id="74e23-107">不過，如果效能不是嚴重的問題，或您已經將句子分割才能對它執行其他類型的查詢，然後合理計算之單字或片語，以及使用 LINQ。</span><span class="sxs-lookup"><span data-stu-id="74e23-107">However, if performance is not a critical issue, or you have already split the sentence in order to perform other types of queries over it, then it makes sense to use LINQ to count the words or phrases as well.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74e23-108">範例</span><span class="sxs-lookup"><span data-stu-id="74e23-108">Example</span></span>  
  
```vb  
Class CountWords  
  
    Shared Sub Main()  
  
        Dim text As String = "Historically, the world of data and the world of objects" &   
                  " have not been well integrated. Programmers work in C# or Visual Basic" &   
                  " and also in SQL or XQuery. On the one side are concepts such as classes," &   
                  " objects, fields, inheritance, and .NET Framework APIs. On the other side" &   
                  " are tables, columns, rows, nodes, and separate languages for dealing with" &   
                  " them. Data types often require translation between the two worlds; there are" &   
                  " different standard functions. Because the object world has no notion of query, a" &   
                  " query can only be represented as a string without compile-time type checking or" &   
                  " IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to" &   
                  " objects in memory is often tedious and error-prone."  
  
        Dim searchTerm As String = "data"  
  
        ' Convert the string into an array of words.  
        Dim dataSource As String() = text.Split(New Char() {" ", ",", ".", ";", ":"},   
                                                 StringSplitOptions.RemoveEmptyEntries)  
  
        ' Create and execute the query. It executes immediately   
        ' because a singleton value is produced.  
        ' Use ToLower to match "data" and "Data"   
        Dim matchQuery = From word In dataSource   
                      Where word.ToLowerInvariant() = searchTerm.ToLowerInvariant()   
                      Select word  
  
        ' Count the matches.  
        Dim count As Integer = matchQuery.Count()  
        Console.WriteLine(count & " occurrence(s) of the search term """ &   
                          searchTerm & """ were found.")  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
End Class  
' Output:  
' 3 occurrence(s) of the search term "data" were found.  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="74e23-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="74e23-109">Compiling the Code</span></span>  
 <span data-ttu-id="74e23-110">建立以.NET Framework 3.5 版或以上版本，搭配 system.core.dll 的參考目標的專案和`Imports`System.Linq 命名空間陳述式。</span><span class="sxs-lookup"><span data-stu-id="74e23-110">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74e23-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74e23-111">See Also</span></span>  
 [<span data-ttu-id="74e23-112">LINQ 和字串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="74e23-112">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
