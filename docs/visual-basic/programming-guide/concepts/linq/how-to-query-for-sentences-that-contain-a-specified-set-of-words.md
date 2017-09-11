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
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 6da15fca0044c1b519d9de9e3785977cda344f06
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-visual-basic"></a><span data-ttu-id="18023-102">如何：查詢包含指定字組的句子 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18023-102">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="18023-103">這個範例示範如何在包含一組指定的文字相符的文字檔案中找到的句子。</span><span class="sxs-lookup"><span data-stu-id="18023-103">This example shows how to find sentences in a text file that contain matches for each of a specified set of words.</span></span> <span data-ttu-id="18023-104">雖然搜尋詞彙的陣列是硬式編碼在此範例中，它可能也會填入以動態方式在執行階段。</span><span class="sxs-lookup"><span data-stu-id="18023-104">Although the array of search terms is hard-coded in this example, it could also be populated dynamically at runtime.</span></span> <span data-ttu-id="18023-105">在此範例中，查詢會傳回 「 過去 」，包含文字的句子 「 資料 」 和 「 整合式 」。</span><span class="sxs-lookup"><span data-stu-id="18023-105">In this example, the query returns the sentences that contain the words "Historically," "data," and "integrated."</span></span>  
  
## <a name="example"></a><span data-ttu-id="18023-106">範例</span><span class="sxs-lookup"><span data-stu-id="18023-106">Example</span></span>  
  
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
  
 <span data-ttu-id="18023-107">查詢的運作方式是先將文字分割成句子，並接著將句子分割成保留每個字的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="18023-107">The query works by first splitting the text into sentences, and then splitting the sentences into an array of strings that hold each word.</span></span> <span data-ttu-id="18023-108">陣列，每個<xref:System.Linq.Enumerable.Distinct%2A>方法會移除所有重複的文字，並接著執行查詢<xref:System.Linq.Enumerable.Intersect%2A>word 陣列上的作業和`wordsToMatch`陣列。</xref:System.Linq.Enumerable.Intersect%2A> </xref:System.Linq.Enumerable.Distinct%2A></span><span class="sxs-lookup"><span data-stu-id="18023-108">For each of these arrays, the <xref:System.Linq.Enumerable.Distinct%2A> method removes all duplicate words, and then the query performs an <xref:System.Linq.Enumerable.Intersect%2A> operation on the word array and the `wordsToMatch` array.</span></span> <span data-ttu-id="18023-109">如果交集的計數會的計數相同`wordsToMatch`陣列，文字中找不到的所有文字，並傳回原始的句子。</span><span class="sxs-lookup"><span data-stu-id="18023-109">If the count of the intersection is the same as the count of the `wordsToMatch` array, all words were found in the words and the original sentence is returned.</span></span>  
  
 <span data-ttu-id="18023-110">在呼叫<xref:System.String.Split%2A>，才能移除字串做為分隔符號使用標點符號。</xref:System.String.Split%2A></span><span class="sxs-lookup"><span data-stu-id="18023-110">In the call to <xref:System.String.Split%2A>, the punctuation marks are used as separators in order to remove them from the string.</span></span> <span data-ttu-id="18023-111">如果您沒有這麼做，您可以有字串 「 過去 」 的範例，就不符合 「 過去 」 在`wordsToMatch`陣列。</span><span class="sxs-lookup"><span data-stu-id="18023-111">If you did not do this, for example you could have a string "Historically," that would not match "Historically" in the `wordsToMatch` array.</span></span> <span data-ttu-id="18023-112">您可能要使用其他分隔符號，根據之原始程式文字中找到的標點符號的類型。</span><span class="sxs-lookup"><span data-stu-id="18023-112">You may have to use additional separators, depending on the types of punctuation found in the source text.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="18023-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="18023-113">Compiling the Code</span></span>  
 <span data-ttu-id="18023-114">建立以.NET Framework 3.5 版或以上版本，搭配 system.core.dll 的參考目標的專案和`Imports`System.Linq 命名空間陳述式。</span><span class="sxs-lookup"><span data-stu-id="18023-114">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18023-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18023-115">See Also</span></span>  
 [<span data-ttu-id="18023-116">LINQ 和字串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18023-116">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
