---
title: HOW TO：查詢的一組資料夾 (LINQ) (Visual Basic) 中的位元組總數
ms.date: 07/20/2015
ms.assetid: bfe85ed2-44dc-4ef1-aac7-241622b80a69
ms.openlocfilehash: 9aa098ddca2e3ad300913b207c9db5a4976eded7
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831666"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-visual-basic"></a><span data-ttu-id="fc97e-102">HOW TO：查詢的一組資料夾 (LINQ) (Visual Basic) 中的位元組總數</span><span class="sxs-lookup"><span data-stu-id="fc97e-102">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="fc97e-103">此範例示範如何擷取所指定資料夾及其所有子資料夾中之所有檔案使用的位元組總數。</span><span class="sxs-lookup"><span data-stu-id="fc97e-103">This example shows how to retrieve the total number of bytes used by all the files in a specified folder and all its subfolders.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc97e-104">範例</span><span class="sxs-lookup"><span data-stu-id="fc97e-104">Example</span></span>  
 <span data-ttu-id="fc97e-105"><xref:System.Linq.Enumerable.Sum%2A> 方法會新增 `select` 子句中選取之所有項目的值。</span><span class="sxs-lookup"><span data-stu-id="fc97e-105">The <xref:System.Linq.Enumerable.Sum%2A> method adds the values of all the items selected in the `select` clause.</span></span> <span data-ttu-id="fc97e-106">您可以輕鬆地修改此查詢以擷取指定目錄樹狀結構中的最大或最小檔案，方法是呼叫 <xref:System.Linq.Enumerable.Min%2A> 或 <xref:System.Linq.Enumerable.Max%2A> 方法，而非 <xref:System.Linq.Enumerable.Sum%2A>。</span><span class="sxs-lookup"><span data-stu-id="fc97e-106">You can easily modify this query to retrieve the biggest or smallest file in the specified directory tree by calling the <xref:System.Linq.Enumerable.Min%2A> or <xref:System.Linq.Enumerable.Max%2A> method instead of <xref:System.Linq.Enumerable.Sum%2A>.</span></span>  
  
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
  
 <span data-ttu-id="fc97e-107">如果您只需要計算所指定樹狀目錄中的位元組數，則可以用更有效率的方式進行這項作業，而不需要建立 LINQ 查詢，原因是這種查詢需要多花時間來建立清單集合作為資料來源。</span><span class="sxs-lookup"><span data-stu-id="fc97e-107">If you only have to count the number of bytes in a specified directory tree, you can do this more efficiently without creating a LINQ query, which incurs the overhead of creating the list collection as a data source.</span></span> <span data-ttu-id="fc97e-108">當查詢越複雜，或需要對相同資料來源執行多個查詢時，LINQ 方式就越有用。</span><span class="sxs-lookup"><span data-stu-id="fc97e-108">The usefulness of the LINQ approach increases as the query becomes more complex, or when you have to run multiple queries against the same data source.</span></span>  
  
 <span data-ttu-id="fc97e-109">查詢會呼叫外面另一個方法來取得檔案長度。</span><span class="sxs-lookup"><span data-stu-id="fc97e-109">The query calls out to a separate method to obtain the file length.</span></span> <span data-ttu-id="fc97e-110">這麼做是要解決可能會因下列狀況引發的例外狀況：自呼叫 `GetFiles` 而建立 <xref:System.IO.FileInfo> 物件後，有另一個執行緒刪除了檔案。</span><span class="sxs-lookup"><span data-stu-id="fc97e-110">It does this in order to consume the possible exception that will be raised if the file was deleted on another thread after the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="fc97e-111">即使已建立 <xref:System.IO.FileInfo> 物件，還是可能會發生這個例外狀況，原因是 <xref:System.IO.FileInfo> 物件會在它的 <xref:System.IO.FileInfo.Length%2A> 屬性第一次受到存取時，嘗試用目前最新的長度來重新整理這個屬性。</span><span class="sxs-lookup"><span data-stu-id="fc97e-111">Even though the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property with the most current length the first time the property is accessed.</span></span> <span data-ttu-id="fc97e-112">讓這個作業進入查詢外部的 try-catch 區塊，程式碼就會遵循規則，以避免查詢中會造成副作業的作業。</span><span class="sxs-lookup"><span data-stu-id="fc97e-112">By putting this operation in a try-catch block outside the query, the code follows the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="fc97e-113">一般而言，處理例外狀況時需要十分小心，以確定應用程式不是處於未知狀態。</span><span class="sxs-lookup"><span data-stu-id="fc97e-113">In general, great care must be taken when you consume exceptions to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fc97e-114">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="fc97e-114">Compiling the Code</span></span>  
 <span data-ttu-id="fc97e-115">建立專案的目標.NET Framework 3.5 版或更高版本 system.core.dll 的參考和`Imports`System.Linq 命名空間陳述式。</span><span class="sxs-lookup"><span data-stu-id="fc97e-115">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a   `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc97e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc97e-116">See also</span></span>

- [<span data-ttu-id="fc97e-117">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc97e-117">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="fc97e-118">LINQ 與檔案目錄 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc97e-118">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
