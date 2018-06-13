---
title: 如何： 查詢資料夾 (LINQ) (Visual Basic) 中的檔案的內容
ms.date: 07/20/2015
ms.assetid: edacbcd3-f3e4-4429-a8be-28a58dc0dd70
ms.openlocfilehash: e0f5e07065ebe210a927491a3f55f891f9934e60
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643035"
---
# <a name="how-to-query-the-contents-of-files-in-a-folder-linq-visual-basic"></a><span data-ttu-id="bb53c-102">如何： 查詢資料夾 (LINQ) (Visual Basic) 中的檔案的內容</span><span class="sxs-lookup"><span data-stu-id="bb53c-102">How to: Query the Contents of Files in a Folder (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="bb53c-103">此範例示範如何查詢所指定樹狀目錄中的所有檔案、開啟每個檔案，然後檢查檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="bb53c-103">This example shows how to query over all the files in a specified directory tree, open each file, and inspect its contents.</span></span> <span data-ttu-id="bb53c-104">這類技巧可以用來建立索引，或將樹狀目錄內容的索引反轉。</span><span class="sxs-lookup"><span data-stu-id="bb53c-104">This type of technique could be used to create indexes or reverse indexes of the contents of a directory tree.</span></span> <span data-ttu-id="bb53c-105">在此範例中，執行的是簡單字串搜尋。</span><span class="sxs-lookup"><span data-stu-id="bb53c-105">A simple string search is performed in this example.</span></span> <span data-ttu-id="bb53c-106">不過，您可以使用規則運算式執行更複雜的模式比對類型。</span><span class="sxs-lookup"><span data-stu-id="bb53c-106">However, more complex types of pattern matching can be performed with a regular expression.</span></span> <span data-ttu-id="bb53c-107">如需詳細資訊，請參閱[How to： 使用規則運算式 (Visual Basic) 結合的 LINQ 查詢](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="bb53c-107">For more information, see [How to: Combine LINQ Queries with Regular Expressions (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb53c-108">範例</span><span class="sxs-lookup"><span data-stu-id="bb53c-108">Example</span></span>  
  
```vb  
Module Module1  
    'QueryContents  
    Public Sub Main()  
  
        ' Modify this path as necessary.  
        Dim startFolder = "c:\program files\Microsoft Visual Studio 9.0\VB\"  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(startFolder)  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        Dim searchTerm = "Visual Studio"  
  
        ' Search the contents of each file.  
        ' A regular expression created with the RegEx class  
        ' could be used instead of the Contains method.  
        Dim queryMatchingFiles = From file In fileList _  
                                 Where file.Extension = ".htm" _  
                                 Let fileText = GetFileText(file.FullName) _  
                                 Where fileText.Contains(searchTerm) _  
                                 Select file.FullName  
  
        Console.WriteLine("The term " & searchTerm & " was found in:")  
  
        ' Execute the query.  
        For Each filename In queryMatchingFiles  
            Console.WriteLine(filename)  
        Next  
  
        ' Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit")  
        Console.ReadKey()  
  
    End Sub  
  
    ' Read the contents of the file. This is done in a separate  
    ' function in order to handle potential file system errors.  
    Function GetFileText(ByVal name As String) As String  
  
        ' If the file has been deleted, the right thing  
        ' to do in this case is return an empty string.  
        Dim fileContents = String.Empty  
  
        ' If the file has been deleted since we took   
        ' the snapshot, ignore it and return the empty string.  
        If System.IO.File.Exists(name) Then  
            fileContents = System.IO.File.ReadAllText(name)  
        End If  
  
        Return fileContents  
  
    End Function  
End Module  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bb53c-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="bb53c-109">Compiling the Code</span></span>  
 <span data-ttu-id="bb53c-110">建立以 .NET Framework 3.5 版或更新版本為目標的專案，其中包含對 System.Core.dll 的參考，以及 System.Linq 命名空間的 `Imports` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="bb53c-110">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb53c-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb53c-111">See Also</span></span>  
 [<span data-ttu-id="bb53c-112">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb53c-112">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
 [<span data-ttu-id="bb53c-113">LINQ 與檔案目錄 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb53c-113">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
