---
title: "如何： 計算的文字字串 (LINQ) (Visual Basic) 中的出現次數"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc367e46-f7cc-45f9-936f-754e661b7bb9
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 82b40e11a72d26858cc2b0b5c0c759517f5b5ee3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-count-occurrences-of-a-word-in-a-string-linq-visual-basic"></a>如何： 計算的文字字串 (LINQ) (Visual Basic) 中的出現次數
本例示範如何使用 LINQ 查詢計算字串中指定單字的出現次數。 請注意，執行計數要先呼叫 <xref:System.String.Split%2A> 方法來建立文字陣列。 <xref:System.String.Split%2A> 方法有效能成本。 如果字串上唯一的作業是計算字數，您應該考慮改用 <xref:System.Text.RegularExpressions.Regex.Matches%2A> 或 <xref:System.String.IndexOf%2A> 方法。 不過，如果效能不是重要的問題，或您已分割句子對它執行其他類型的查詢，則使用 LINQ 計算單字或詞組才有意義。  
  
## <a name="example"></a>範例  
  
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
  
## <a name="compiling-the-code"></a>編譯程式碼  
 建立以 .NET Framework 3.5 版或更新版本為目標的專案，其中包含對 System.Core.dll 的參考，以及 System.Linq 命名空間的 `Imports` 陳述式。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ 和字串 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
