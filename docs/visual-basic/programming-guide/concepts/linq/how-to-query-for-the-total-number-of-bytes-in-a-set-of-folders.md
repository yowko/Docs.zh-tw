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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: bda25acd3065898eeb61dce83d46d7526e825add
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-visual-basic"></a><span data-ttu-id="faee9-102">如何︰ 查詢一組資料夾 (LINQ) (Visual Basic) 中的位元組總數</span><span class="sxs-lookup"><span data-stu-id="faee9-102">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="faee9-103">這個範例示範如何擷取指定的資料夾中的所有檔案和所有子資料夾所使用的位元組總數。</span><span class="sxs-lookup"><span data-stu-id="faee9-103">This example shows how to retrieve the total number of bytes used by all the files in a specified folder and all its subfolders.</span></span>  
  
## <a name="example"></a><span data-ttu-id="faee9-104">範例</span><span class="sxs-lookup"><span data-stu-id="faee9-104">Example</span></span>  
 <span data-ttu-id="faee9-105"><xref:System.Linq.Enumerable.Sum%2A>方法會將選取的所有項目的值`select`子句。</xref:System.Linq.Enumerable.Sum%2A></span><span class="sxs-lookup"><span data-stu-id="faee9-105">The <xref:System.Linq.Enumerable.Sum%2A> method adds the values of all the items selected in the `select` clause.</span></span> <span data-ttu-id="faee9-106">您可以輕鬆地修改此查詢以擷取指定的目錄樹狀結構中的最大或最小檔案，藉由呼叫的<xref:System.Linq.Enumerable.Min%2A><xref:System.Linq.Enumerable.Max%2A>方法而不是<xref:System.Linq.Enumerable.Sum%2A>.</xref:System.Linq.Enumerable.Sum%2A></xref:System.Linq.Enumerable.Max%2A>或</xref:System.Linq.Enumerable.Min%2A></span><span class="sxs-lookup"><span data-stu-id="faee9-106">You can easily modify this query to retrieve the biggest or smallest file in the specified directory tree by calling the <xref:System.Linq.Enumerable.Min%2A> or <xref:System.Linq.Enumerable.Max%2A> method instead of <xref:System.Linq.Enumerable.Sum%2A>.</span></span>  
  
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
  
 <span data-ttu-id="faee9-107">如果您只有指定的目錄樹狀結構中的位元組計數，您可以更有效率而不需建立 LINQ 查詢，產生建立做為資料來源的清單集合的負荷。</span><span class="sxs-lookup"><span data-stu-id="faee9-107">If you only have to count the number of bytes in a specified directory tree, you can do this more efficiently without creating a LINQ query, which incurs the overhead of creating the list collection as a data source.</span></span> <span data-ttu-id="faee9-108">查詢會變得更複雜，或當您需要針對相同的資料來源執行多個查詢時，會增加 LINQ 方法的用處。</span><span class="sxs-lookup"><span data-stu-id="faee9-108">The usefulness of the LINQ approach increases as the query becomes more complex, or when you have to run multiple queries against the same data source.</span></span>  
  
 <span data-ttu-id="faee9-109">查詢呼叫另一個方法來取得檔案的長度。</span><span class="sxs-lookup"><span data-stu-id="faee9-109">The query calls out to a separate method to obtain the file length.</span></span> <span data-ttu-id="faee9-110">這麼做是為了使用可能的例外狀況，若檔案已刪除之後的另一個執行緒上將會產生<xref:System.IO.FileInfo>物件建立於呼叫`GetFiles`。</xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="faee9-110">It does this in order to consume the possible exception that will be raised if the file was deleted on another thread after the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="faee9-111">即使<xref:System.IO.FileInfo>物件已建立，可能會發生例外狀況，因為<xref:System.IO.FileInfo>物件將會嘗試重新整理其<xref:System.IO.FileInfo.Length%2A>屬性與最新的第一次存取屬性的長度。</xref:System.IO.FileInfo.Length%2A> </xref:System.IO.FileInfo> </xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="faee9-111">Even though the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property with the most current length the first time the property is accessed.</span></span> <span data-ttu-id="faee9-112">將這項作業放在 try catch 區塊中的查詢之外，此程式碼會遵循的規則，避免可能會造成副作用的查詢中的作業。</span><span class="sxs-lookup"><span data-stu-id="faee9-112">By putting this operation in a try-catch block outside the query, the code follows the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="faee9-113">一般情況下，取用以確定應用程式未處於不明狀態的例外狀況時，必須採取小心。</span><span class="sxs-lookup"><span data-stu-id="faee9-113">In general, great care must be taken when you consume exceptions to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="faee9-114">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="faee9-114">Compiling the Code</span></span>  
 <span data-ttu-id="faee9-115">建立以.NET Framework 3.5 版或以上版本，搭配 system.core.dll 的參考目標的專案和`Imports`System.Linq 命名空間陳述式。</span><span class="sxs-lookup"><span data-stu-id="faee9-115">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a   `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faee9-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="faee9-116">See Also</span></span>  
 <span data-ttu-id="faee9-117">[LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md) </span><span class="sxs-lookup"><span data-stu-id="faee9-117">[LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md) </span></span>  
<span data-ttu-id="faee9-118"> [LINQ 和檔案目錄 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)</span><span class="sxs-lookup"><span data-stu-id="faee9-118"> [LINQ and File Directories (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)</span></span>
