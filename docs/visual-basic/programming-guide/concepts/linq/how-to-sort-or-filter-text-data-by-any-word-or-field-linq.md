---
title: "如何︰ 排序或篩選文字資料，依任何字或欄位 (LINQ) (Visual Basic) |Microsoft 文件"
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
ms.assetid: 9df137fe-335b-46e0-aecf-ea8a9eddd4e3
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
ms.openlocfilehash: e13cdc32b40f1c16d4c8fa27f3c3af15a80c33d7
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-sort-or-filter-text-data-by-any-word-or-field-linq-visual-basic"></a><span data-ttu-id="55f07-102">如何：依任何字或欄位排序或篩選文字資料 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55f07-102">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="55f07-103">下列範例顯示如何排序的結構化文字行，例如以逗號分隔的值，任何列中的欄位。</span><span class="sxs-lookup"><span data-stu-id="55f07-103">The following example shows how to sort lines of structured text, such as comma-separated values, by any field in the line.</span></span> <span data-ttu-id="55f07-104">欄位可能會在執行階段以動態方式指定。</span><span class="sxs-lookup"><span data-stu-id="55f07-104">The field may be dynamically specified at runtime.</span></span> <span data-ttu-id="55f07-105">假設在 scores.csv 欄位代表後面接著一系列的四個測驗分數的學生識別碼編號。</span><span class="sxs-lookup"><span data-stu-id="55f07-105">Assume that the fields in scores.csv represent a student's ID number, followed by a series of four test scores.</span></span>  
  
### <a name="to-create-a-file-that-contains-data"></a><span data-ttu-id="55f07-106">若要建立包含資料的檔案</span><span class="sxs-lookup"><span data-stu-id="55f07-106">To create a file that contains data</span></span>  
  
1.  <span data-ttu-id="55f07-107">從主題中複製 scores.csv 資料[How to︰ 將內容從不同的檔案 (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md)並將它儲存到您的方案資料夾。</span><span class="sxs-lookup"><span data-stu-id="55f07-107">Copy the scores.csv data from the topic [How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) and save it to your solution folder.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55f07-108">範例</span><span class="sxs-lookup"><span data-stu-id="55f07-108">Example</span></span>  
  
```vb  
Class SortLines  
  
    Shared Sub Main()  
        Dim scores As String() = System.IO.File.ReadAllLines("../../../scores.csv")  
  
        ' Change this to any value from 0 to 4  
        Dim sortField As Integer = 1  
  
        Console.WriteLine("Sorted highest to lowest by field " & sortField)  
  
        ' Demonstrates how to return query from a method.  
        ' The query is executed here.  
        For Each str As String In SortQuery(scores, sortField)  
            Console.WriteLine(str)  
        Next  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
  
    Shared Function SortQuery(  
        ByVal source As IEnumerable(Of String),   
        ByVal num As Integer) As IEnumerable(Of String)  
  
        Dim scoreQuery = From line In source   
                         Let fields = line.Split(New Char() {","})   
                         Order By fields(num) Descending   
                         Select line  
  
        Return scoreQuery  
    End Function  
End Class  
' Output:  
' Sorted highest to lowest by field 1  
' 116, 99, 86, 90, 94  
' 120, 99, 82, 81, 79  
' 111, 97, 92, 81, 60  
' 114, 97, 89, 85, 82  
' 121, 96, 85, 91, 60  
' 122, 94, 92, 91, 91  
' 117, 93, 92, 80, 87  
' 118, 92, 90, 83, 78  
' 113, 88, 94, 65, 91  
' 112, 75, 84, 91, 39  
' 119, 68, 79, 88, 92  
' 115, 35, 72, 91, 70  
```  
  
 <span data-ttu-id="55f07-109">這個範例也示範如何從函式傳回的查詢變數。</span><span class="sxs-lookup"><span data-stu-id="55f07-109">This example also demonstrates how to return a query variable from a Function.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="55f07-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="55f07-110">Compiling the Code</span></span>  
 <span data-ttu-id="55f07-111">建立以.NET Framework 3.5 版或以上版本，搭配 system.core.dll 的參考目標的專案和`Imports`System.Linq 命名空間陳述式。</span><span class="sxs-lookup"><span data-stu-id="55f07-111">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55f07-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55f07-112">See Also</span></span>  
 [<span data-ttu-id="55f07-113">LINQ 和字串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55f07-113">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
