---
title: "如何︰ 依副檔名 (LINQ) (Visual Basic) 分組檔案 |Microsoft 文件"
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
ms.assetid: 904dc6d7-7162-4655-a7f4-5785d669bc5a
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
ms.openlocfilehash: 8b78cbaf8b0f20c6b7ab14640dffd61e9657dc9b
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-group-files-by-extension-linq-visual-basic"></a><span data-ttu-id="378b8-102">如何︰ 依副檔名 (LINQ) (Visual Basic) 的檔案群組</span><span class="sxs-lookup"><span data-stu-id="378b8-102">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="378b8-103">此範例顯示如何使用 LINQ，若要執行進階的分組和排序作業清單上的檔案或資料夾。</span><span class="sxs-lookup"><span data-stu-id="378b8-103">This example shows how LINQ can be used to perform advanced grouping and sorting operations on lists of files or folders.</span></span> <span data-ttu-id="378b8-104">它也示範如何使用網頁在主控台視窗輸出<xref:System.Linq.Enumerable.Skip%2A>和<xref:System.Linq.Enumerable.Take%2A>方法。</xref:System.Linq.Enumerable.Take%2A> </xref:System.Linq.Enumerable.Skip%2A></span><span class="sxs-lookup"><span data-stu-id="378b8-104">It also shows how to page output in the console window by using the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="378b8-105">範例</span><span class="sxs-lookup"><span data-stu-id="378b8-105">Example</span></span>  
 <span data-ttu-id="378b8-106">下列查詢會示範如何依副檔名分組指定的目錄樹狀結構的內容。</span><span class="sxs-lookup"><span data-stu-id="378b8-106">The following query shows how to group the contents of a specified directory tree by the file name extension.</span></span>  
  
```vb  
Module GroupByExtension  
    Public Sub Main()  
  
        ' Root folder to query, along with all subfolders.  
        Dim startFolder As String = "C:\program files\Microsoft Visual Studio 9.0\VB\"  
  
        ' Used in WriteLine() to skip over startfolder in output lines.  
        Dim rootLength As Integer = startFolder.Length  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(startFolder)  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' Create the query.  
        Dim queryGroupByExt = From file In fileList _  
                          Group By file.Extension.ToLower() Into fileGroup = Group _  
                          Order By ToLower _  
                          Select fileGroup  
  
        ' Execute the query. By storing the result we can  
        ' page the display with good performance.  
        Dim groupByExtList = queryGroupByExt.ToList()  
  
        ' Display one group at a time. If the number of   
        ' entries is greater than the number of lines  
        ' in the console window, then page the output.  
        Dim trimLength = startFolder.Length  
        PageOutput(groupByExtList, trimLength)  
  
    End Sub  
  
    ' Pages console diplay for large query results. No more than one group per page.  
    ' This sub specifically works with group queries of FileInfo objects  
    ' but can be modified for any type.  
    Sub PageOutput(ByVal groupQuery, ByVal charsToSkip)  
  
        ' "3" = 1 line for extension key + 1 for "Press any key" + 1 for input cursor.  
        Dim numLines As Integer = Console.WindowHeight - 3  
        ' Flag to indicate whether there are more results to diplay  
        Dim goAgain As Boolean = True  
  
        For Each fg As IEnumerable(Of System.IO.FileInfo) In groupQuery  
            ' Start a new extension at the top of a page.  
            Dim currentLine As Integer = 0  
  
            Do While (currentLine < fg.Count())  
                Console.Clear()  
                Console.WriteLine(fg(0).Extension)  
  
                ' Get the next page of results  
                ' No more than one filename per page  
                Dim resultPage = From file In fg _  
                                Skip currentLine Take numLines  
  
                ' Execute the query. Trim the display output.  
                For Each line In resultPage  
                    Console.WriteLine(vbTab & line.FullName.Substring(charsToSkip))  
                Next  
  
                ' Advance the current position  
                currentLine = numLines + currentLine  
  
                ' Give the user a chance to break out of the loop  
                Console.WriteLine("Press any key for next page or the 'End' key to exit.")  
                Dim key As ConsoleKey = Console.ReadKey().Key  
                If key = ConsoleKey.End Then  
                    goAgain = False  
                    Exit For  
                End If  
            Loop  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="378b8-107">此程式的輸出可以很長的根據本機檔案系統，以及詳細資料`startFolder`設為。</span><span class="sxs-lookup"><span data-stu-id="378b8-107">The output from this program can be long, depending on the details of the local file system and what the `startFolder` is set to.</span></span> <span data-ttu-id="378b8-108">若要啟用 檢視所有結果，此範例會示範如何將結果分頁。</span><span class="sxs-lookup"><span data-stu-id="378b8-108">To enable viewing of all results, this example shows how to page through results.</span></span> <span data-ttu-id="378b8-109">相同的技巧可以套用至 Windows 和 Web 應用程式中。</span><span class="sxs-lookup"><span data-stu-id="378b8-109">The same techniques can be applied to Windows and Web applications.</span></span> <span data-ttu-id="378b8-110">請注意，因為字碼頁的巢狀群組中的項目`For Each`迴圈是必要。</span><span class="sxs-lookup"><span data-stu-id="378b8-110">Notice that because the code pages the items in a group, a nested `For Each` loop is required.</span></span> <span data-ttu-id="378b8-111">另外還有一些額外的邏輯來計算目前的位置，在清單中，並讓使用者停止分頁並結束程式。</span><span class="sxs-lookup"><span data-stu-id="378b8-111">There is also some additional logic to compute the current position in the list, and to enable the user to stop paging and exit the program.</span></span> <span data-ttu-id="378b8-112">在此案例中，分頁查詢針對快取的結果從執行原始查詢。</span><span class="sxs-lookup"><span data-stu-id="378b8-112">In this particular case, the paging query is run against the cached results from the original query.</span></span> <span data-ttu-id="378b8-113">在其他內容，例如 LINQ to SQL，這類不需要快取。</span><span class="sxs-lookup"><span data-stu-id="378b8-113">In other contexts, such as LINQ to SQL, such caching is not required.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="378b8-114">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="378b8-114">Compiling the Code</span></span>  
 <span data-ttu-id="378b8-115">建立以.NET Framework 3.5 版或以上版本，搭配 system.core.dll 的參考目標的專案和`Imports`System.Linq 命名空間陳述式。</span><span class="sxs-lookup"><span data-stu-id="378b8-115">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a   `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="378b8-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="378b8-116">See Also</span></span>  
 <span data-ttu-id="378b8-117">[LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md) </span><span class="sxs-lookup"><span data-stu-id="378b8-117">[LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md) </span></span>  
<span data-ttu-id="378b8-118"> [LINQ 和檔案目錄 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)</span><span class="sxs-lookup"><span data-stu-id="378b8-118"> [LINQ and File Directories (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)</span></span>
