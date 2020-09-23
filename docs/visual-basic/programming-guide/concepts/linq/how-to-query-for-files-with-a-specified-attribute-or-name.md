---
title: 作法：查詢具有指定屬性或名稱的檔案
ms.date: 07/20/2015
ms.assetid: b26026a3-3f43-448f-a582-259997af6be0
ms.openlocfilehash: eeacd94fb303a439e8034b84d285ab11b2333581
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059310"
---
# <a name="how-to-query-for-files-with-a-specified-attribute-or-name-visual-basic"></a><span data-ttu-id="a7607-102">如何：查詢具有指定屬性或名稱的檔案 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="a7607-102">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>

<span data-ttu-id="a7607-103">這個範例示範如何在指定的樹狀目錄中尋找所有具有指定副檔名 (例如 ".txt") 的檔案。</span><span class="sxs-lookup"><span data-stu-id="a7607-103">This example shows how to find all files that have a specified file name extension (for example ".txt") in a specified directory tree.</span></span> <span data-ttu-id="a7607-104">它也會示範如何根據建立時間來傳回樹狀結構中的最新或最舊檔案。</span><span class="sxs-lookup"><span data-stu-id="a7607-104">It also shows how to return either the newest or oldest file in the tree based on the creation time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7607-105">範例</span><span class="sxs-lookup"><span data-stu-id="a7607-105">Example</span></span>  
  
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
  
## <a name="compile-the-code"></a><span data-ttu-id="a7607-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="a7607-106">Compile the code</span></span>  

<span data-ttu-id="a7607-107">使用 `Imports` 適用于 system.string 命名空間的語句來建立 Visual Basic 主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="a7607-107">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a7607-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7607-108">See also</span></span>

- [<span data-ttu-id="a7607-109">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7607-109">LINQ to Objects (Visual Basic)</span></span>](linq-to-objects.md)
- [<span data-ttu-id="a7607-110">LINQ 與檔案目錄 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7607-110">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
