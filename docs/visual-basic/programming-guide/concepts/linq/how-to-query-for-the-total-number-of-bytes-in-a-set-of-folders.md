---
title: "如何︰ 查詢一組資料夾 (LINQ) (Visual Basic) 中的位元組總數 |Microsoft 文件"
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
ms.assetid: bfe85ed2-44dc-4ef1-aac7-241622b80a69
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 668a8a4d89f7b81c3aef9b4e1a46ad749c4a8341
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-visual-basic"></a>如何︰ 查詢一組資料夾 (LINQ) (Visual Basic) 中的位元組總數
這個範例示範如何擷取指定的資料夾中的所有檔案和所有子資料夾所使用的位元組總數。  
  
## <a name="example"></a>範例  
 <xref:System.Linq.Enumerable.Sum%2A>方法會將選取的所有項目的值`select`子句。</xref:System.Linq.Enumerable.Sum%2A> 您可以輕鬆地修改此查詢以擷取指定的目錄樹狀結構中的最大或最小檔案，藉由呼叫的<xref:System.Linq.Enumerable.Min%2A><xref:System.Linq.Enumerable.Max%2A>方法而不是<xref:System.Linq.Enumerable.Sum%2A>.</xref:System.Linq.Enumerable.Sum%2A></xref:System.Linq.Enumerable.Max%2A>或</xref:System.Linq.Enumerable.Min%2A>  
  
```vb  
Module QueryTotalBytes  
    Sub Main()  
  
        ' Change the drive\path if necessary.  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0\VB"  
  
        'Take a snapshot of the folder contents.  
        ' This method assumes that the application has discovery permissions  
        ' for all folders under the specified path.  
        Dim fileList = My.Computer.FileSystem.GetFiles _  
                  (root, FileIO.SearchOption.SearchAllSubDirectories, "*.*")  
  
        Dim fileQuery = From file In fileList _  
                        Select GetFileLength(file)  
  
        ' Force execution and cache the results to avoid multiple trips to the file system.  
        Dim fileLengths = fileQuery.ToArray()  
  
        ' Find the largest file  
        Dim maxSize = Aggregate aFile In fileLengths Into Max()  
  
        ' Find the total number of bytes  
        Dim totalBytes = Aggregate aFile In fileLengths Into Sum()  
  
        Console.WriteLine("The largest file is " & maxSize & " bytes")  
        Console.WriteLine("There are " & totalBytes & " total bytes in " & _  
                          fileList.Count & " files under " & root)  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
    ' This method is used to catch the possible exception  
    ' that can be raised when accessing the FileInfo.Length property.  
    Function GetFileLength(ByVal filename As String) As Long  
        Dim retval As Long  
        Try  
            Dim fi As New System.IO.FileInfo(filename)  
            retval = fi.Length  
        Catch ex As System.IO.FileNotFoundException  
            ' If a file is no longer present,  
            ' just return zero bytes.   
            retval = 0  
        End Try  
  
        Return retval  
    End Function  
End Module  
```  
  
 如果您只有指定的目錄樹狀結構中的位元組計數，您可以更有效率而不需建立 LINQ 查詢，產生建立做為資料來源的清單集合的負荷。 查詢會變得更複雜，或當您需要針對相同的資料來源執行多個查詢時，會增加 LINQ 方法的用處。  
  
 查詢呼叫另一個方法來取得檔案的長度。 這麼做是為了使用可能的例外狀況，若檔案已刪除之後的另一個執行緒上將會產生<xref:System.IO.FileInfo>物件建立於呼叫`GetFiles`。</xref:System.IO.FileInfo> 即使<xref:System.IO.FileInfo>物件已建立，可能會發生例外狀況，因為<xref:System.IO.FileInfo>物件將會嘗試重新整理其<xref:System.IO.FileInfo.Length%2A>屬性與最新的第一次存取屬性的長度。</xref:System.IO.FileInfo.Length%2A> </xref:System.IO.FileInfo> </xref:System.IO.FileInfo> 將這項作業放在 try catch 區塊中的查詢之外，此程式碼會遵循的規則，避免可能會造成副作用的查詢中的作業。 一般情況下，取用以確定應用程式未處於不明狀態的例外狀況時，必須採取小心。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 建立以.NET Framework 3.5 版或以上版本，搭配 system.core.dll 的參考目標的專案和`Imports`System.Linq 命名空間陳述式。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)   
 [LINQ 和檔案目錄 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
