---
title: "如何︰ 查詢包含一組指定的文字 (LINQ) (Visual Basic) 的句子 |Microsoft 文件"
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
ms.assetid: a5ae8ced-61fe-4c10-bb8a-95630e50f603
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 31561d586c9c05f502002efdfc455acb55159fed
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-visual-basic"></a>如何：查詢包含指定字組的句子 (LINQ) (Visual Basic)
這個範例示範如何在包含一組指定的文字相符的文字檔案中找到的句子。 雖然搜尋詞彙的陣列是硬式編碼在此範例中，它可能也會填入以動態方式在執行階段。 在此範例中，查詢會傳回 「 過去 」，包含文字的句子 「 資料 」 和 「 整合式 」。  
  
## <a name="example"></a>範例  
  
```vb  
Class FindSentences  
  
    Shared Sub Main()  
        Dim text As String = "Historically, the world of data and the world of objects " &   
        "have not been well integrated. Programmers work in C# or Visual Basic " &   
        "and also in SQL or XQuery. On the one side are concepts such as classes, " &   
        "objects, fields, inheritance, and .NET Framework APIs. On the other side " &   
        "are tables, columns, rows, nodes, and separate languages for dealing with " &   
        "them. Data types often require translation between the two worlds; there are " &   
        "different standard functions. Because the object world has no notion of query, a " &   
        "query can only be represented as a string without compile-time type checking or " &   
        "IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to " &   
        "objects in memory is often tedious and error-prone."  
  
        ' Split the text block into an array of sentences.  
        Dim sentences As String() = text.Split(New Char() {".", "?", "!"})  
  
        ' Define the search terms. This list could also be dynamically populated at runtime  
        Dim wordsToMatch As String() = {"Historically", "data", "integrated"}  
  
        ' Find sentences that contain all the terms in the wordsToMatch array  
        ' Note that the number of terms to match is not specified at compile time  
        Dim sentenceQuery = From sentence In sentences   
                            Let w = sentence.Split(New Char() {" ", ",", ".", ";", ":"},   
                                                   StringSplitOptions.RemoveEmptyEntries)   
                            Where w.Distinct().Intersect(wordsToMatch).Count = wordsToMatch.Count()   
                            Select sentence  
  
        ' Execute the query  
        For Each str As String In sentenceQuery  
            Console.WriteLine(str)  
        Next  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
End Class  
' Output:  
' Historically, the world of data and the world of objects have not been well integrated  
```  
  
 查詢的運作方式是先將文字分割成句子，並接著將句子分割成保留每個字的字串陣列。 陣列，每個<xref:System.Linq.Enumerable.Distinct%2A>方法會移除所有重複的文字，並接著執行查詢<xref:System.Linq.Enumerable.Intersect%2A>word 陣列上的作業和`wordsToMatch`陣列。</xref:System.Linq.Enumerable.Intersect%2A> </xref:System.Linq.Enumerable.Distinct%2A> 如果交集的計數會的計數相同`wordsToMatch`陣列，文字中找不到的所有文字，並傳回原始的句子。  
  
 在呼叫<xref:System.String.Split%2A>，才能移除字串做為分隔符號使用標點符號。</xref:System.String.Split%2A> 如果您沒有這麼做，您可以有字串 「 過去 」 的範例，就不符合 「 過去 」 在`wordsToMatch`陣列。 您可能要使用其他分隔符號，根據之原始程式文字中找到的標點符號的類型。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 建立以.NET Framework 3.5 版或以上版本，搭配 system.core.dll 的參考目標的專案和`Imports`System.Linq 命名空間陳述式。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ 和字串 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
