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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f78785b4da3ae3b362603eea34d81207ed48a657
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-group-files-by-extension-linq-visual-basic"></a>如何︰ 依副檔名 (LINQ) (Visual Basic) 的檔案群組
此範例顯示如何使用 LINQ，若要執行進階的分組和排序作業清單上的檔案或資料夾。 它也示範如何使用網頁在主控台視窗輸出<xref:System.Linq.Enumerable.Skip%2A>和<xref:System.Linq.Enumerable.Take%2A>方法。</xref:System.Linq.Enumerable.Take%2A> </xref:System.Linq.Enumerable.Skip%2A>  
  
## <a name="example"></a>範例  
 下列查詢會示範如何依副檔名分組指定的目錄樹狀結構的內容。  
  
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
  
 此程式的輸出可以很長的根據本機檔案系統，以及詳細資料`startFolder`設為。 若要啟用 檢視所有結果，此範例會示範如何將結果分頁。 相同的技巧可以套用至 Windows 和 Web 應用程式中。 請注意，因為字碼頁的巢狀群組中的項目`For Each`迴圈是必要。 另外還有一些額外的邏輯來計算目前的位置，在清單中，並讓使用者停止分頁並結束程式。 在此案例中，分頁查詢針對快取的結果從執行原始查詢。 在其他內容，例如 LINQ to SQL，這類不需要快取。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 建立以.NET Framework 3.5 版或以上版本，搭配 system.core.dll 的參考目標的專案和`Imports`System.Linq 命名空間陳述式。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)   
 [LINQ 和檔案目錄 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
