---
title: "如何︰ 查詢具有指定之的屬性或名稱 (Visual Basic) 的檔案 |Microsoft 文件"
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
ms.assetid: b26026a3-3f43-448f-a582-259997af6be0
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
ms.openlocfilehash: db0e3f415df80e8e4c551bd8493814cb3f4fe5ee
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-query-for-files-with-a-specified-attribute-or-name-visual-basic"></a>如何︰ 查詢具有指定之的屬性或名稱 (Visual Basic) 的檔案
這個範例會示範如何尋找具有指定的名稱的副檔名 (例如".txt") 的所有檔案中指定的目錄樹狀結構。 它也會示範如何傳回可能的最新或舊檔案的建立時間為基礎的樹狀目錄中。  
  
## <a name="example"></a>範例  
  
```vb  
Module FindFileByExtension  
    Sub Main()  
  
        ' Change the drive\path if necessary  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0"  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(root)  
  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' This query will produce the full path for all .txt files  
        ' under the specified folder including subfolders.  
        ' It orders the list according to the file name.  
        Dim fileQuery = From file In fileList _  
                        Where file.Extension = ".txt" _  
                        Order By file.Name _  
                        Select file  
  
        For Each file In fileQuery  
            Console.WriteLine(file.FullName)  
        Next  
  
        ' Create and execute a new query by using  
        ' the previous query as a starting point.  
        ' fileQuery is not executed again until the  
        ' call to Last  
        Dim fileQuery2 = From file In fileQuery _  
                         Order By file.CreationTime _  
                         Select file.Name, file.CreationTime  
  
        ' Execute the query  
        Dim newestFile = fileQuery2.Last  
  
        Console.WriteLine("\r\nThe newest .txt file is {0}. Creation time: {1}", _  
                newestFile.Name, newestFile.CreationTime)  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
End Module  
```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 建立以.NET Framework 3.5 版或以上版本，搭配 system.core.dll 的參考目標的專案和`Imports`System.Linq 命名空間陳述式。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)   
 [LINQ 和檔案目錄 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
