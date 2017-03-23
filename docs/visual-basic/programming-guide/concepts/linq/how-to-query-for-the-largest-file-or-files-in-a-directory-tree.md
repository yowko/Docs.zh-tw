---
title: "如何︰ 查詢的最大檔案或目錄樹狀結構 (LINQ) (Visual Basic) 中的檔案 |Microsoft 文件"
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
ms.assetid: 8c1c9f0c-95dd-4222-9be2-9ec026a13e81
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
ms.openlocfilehash: 055cbdd5a5903417ab382d390e1215f0319c0b5a
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-visual-basic"></a>如何：查詢目錄樹狀中的最大檔案 (LINQ) (Visual Basic)
此範例顯示五個查詢相關的檔案大小 （位元組）︰  
  
-   如何擷取以位元組為單位的最大檔案大小。  
  
-   如何擷取以位元組為單位的最小的檔案大小。  
  
-   如何擷取<xref:System.IO.FileInfo>物件最大或最小檔案，從指定的根資料夾下的一個或多個資料夾。</xref:System.IO.FileInfo>  
  
-   如何擷取序列，例如 10 個最大的檔案。  
  
-   如何排成群組根據檔案大小 （位元組），略過小於指定大小的檔案。  
  
## <a name="example"></a>範例  
 下列範例包含五個不同的查詢顯示如何查詢及群組檔案，以位元組為單位的檔案大小而定。 您可以輕鬆地修改這些範例為基礎的一些其他屬性的查詢<xref:System.IO.FileInfo>物件。</xref:System.IO.FileInfo>  
  
```vb  
Module QueryBySize  
    Sub Main()  
  
        ' Change the drive\path if necessary  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0"  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(root)  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' Return the size of the largest file  
        Dim maxSize = Aggregate aFile In fileList Into Max(GetFileLength(aFile))  
  
        'Dim maxSize = fileLengths.Max  
        Console.WriteLine("The length of the largest file under {0} is {1}", _  
                          root, maxSize)  
  
        ' Return the FileInfo object of the largest file  
        ' by sorting and selecting from the beginning of the list  
        Dim filesByLengDesc = From file In fileList _  
                              Let filelength = GetFileLength(file) _  
                              Where filelength > 0 _  
                              Order By filelength Descending _  
                              Select file  
  
        Dim longestFile = filesByLengDesc.First  
  
        Console.WriteLine("The largest file under {0} is {1} with a length of {2} bytes", _  
                          root, longestFile.FullName, longestFile.Length)  
  
        Dim smallestFile = filesByLengDesc.Last  
  
        Console.WriteLine("The smallest file under {0} is {1} with a length of {2} bytes", _  
                                root, smallestFile.FullName, smallestFile.Length)  
  
        ' Return the FileInfos for the 10 largest files  
        ' Based on a previous query, but nothing is executed  
        ' until the For Each statement below.  
        Dim tenLargest = From file In filesByLengDesc Take 10  
  
        Console.WriteLine("The 10 largest files under {0} are:", root)  
  
        For Each fi As System.IO.FileInfo In tenLargest  
            Console.WriteLine("{0}: {1} bytes", fi.FullName, fi.Length)  
        Next  
  
        ' Group files according to their size,  
        ' leaving out the ones under 200K  
        Dim sizeGroups = From file As System.IO.FileInfo In fileList _  
                         Where file.Length > 0 _  
                         Let groupLength = file.Length / 100000 _  
                         Group file By groupLength Into fileGroup = Group _  
                         Where groupLength >= 2 _  
                         Order By groupLength Descending  
  
        For Each group In sizeGroups  
            Console.WriteLine(group.groupLength + "00000")  
  
            For Each item As System.IO.FileInfo In group.fileGroup  
                Console.WriteLine("   {0}: {1}", item.Name, item.Length)  
            Next  
        Next  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
  
    ' This method is used to catch the possible exception  
    ' that can be raised when accessing the FileInfo.Length property.  
    ' In this particular case, it is safe to ignore the exception.  
    Function GetFileLength(ByVal fi As System.IO.FileInfo) As Long  
        Dim retval As Long  
        Try  
            retval = fi.Length  
        Catch ex As FileNotFoundException  
            ' If a file is no longer present,  
            ' just return zero bytes.   
            retval = 0  
        End Try  
  
        Return retval  
    End Function  
End Module  
```  
  
 若要傳回一或多個完成<xref:System.IO.FileInfo>物件查詢首先必須檢查每個資料來源，然後再將它們排序其 Length 屬性的值。</xref:System.IO.FileInfo> 然後它會傳回單一物件或順序具有最大長度。 使用<xref:System.Linq.Enumerable.First%2A>傳回清單中的第一個項目。</xref:System.Linq.Enumerable.First%2A> 使用<xref:System.Linq.Enumerable.Take%2A>傳回的第 n 個項目。</xref:System.Linq.Enumerable.Take%2A> 指定遞減的排序順序，將最小項目清單的開頭。  
  
 查詢會呼叫另一個方法來取得檔案大小 （位元組），才能使用可能會在案例中，檔案已刪除另一個執行緒的時間週期之後引發的例外狀況<xref:System.IO.FileInfo>物件建立於呼叫`GetFiles`。</xref:System.IO.FileInfo> 即使透過<xref:System.IO.FileInfo>物件已建立，可能會發生例外狀況，因為<xref:System.IO.FileInfo>物件將會嘗試重新整理其<xref:System.IO.FileInfo.Length%2A>屬性，以位元組為單位的第一次存取該屬性時使用的最新的大小。</xref:System.IO.FileInfo.Length%2A> </xref:System.IO.FileInfo> </xref:System.IO.FileInfo> 將這項作業放在 try catch 區塊中的查詢之外，我們要遵循的規則，避免可能會造成副作用的查詢中的作業。 一般情況下，絕佳必須小心使用例外狀況時，以確定應用程式未處於未知狀態。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 建立以.NET Framework 3.5 版或以上版本，搭配 system.core.dll 的參考目標的專案和`Imports`System.Linq 命名空間陳述式。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)   
 [LINQ 和檔案目錄 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
