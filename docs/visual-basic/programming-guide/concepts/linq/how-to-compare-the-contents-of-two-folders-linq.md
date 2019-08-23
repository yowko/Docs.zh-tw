---
title: HOW TO：比較兩個資料夾的內容 (LINQ) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 903c7e9a-f48d-4a07-a8a8-5450d2646efa
ms.openlocfilehash: 5db73b57cfa21de4f1d14299ed7956a322876898
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940668"
---
# <a name="how-to-compare-the-contents-of-two-folders-linq-visual-basic"></a><span data-ttu-id="5f55f-102">HOW TO：比較兩個資料夾的內容 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f55f-102">How to: Compare the Contents of Two Folders (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="5f55f-103">本例示範三種比較兩個檔案清單的方式︰</span><span class="sxs-lookup"><span data-stu-id="5f55f-103">This example demonstrates three ways to compare two file listings:</span></span>  
  
- <span data-ttu-id="5f55f-104">查詢指定兩個檔案清單是否完全相同的布林值。</span><span class="sxs-lookup"><span data-stu-id="5f55f-104">By querying for a Boolean value that specifies whether the two file lists are identical.</span></span>  
  
- <span data-ttu-id="5f55f-105">查詢交集，以擷取這兩個資料夾都有的檔案。</span><span class="sxs-lookup"><span data-stu-id="5f55f-105">By querying for the intersection to retrieve the files that are in both folders.</span></span>  
  
- <span data-ttu-id="5f55f-106">查詢集合差異，以擷取一個資料夾中有而另一個沒有的檔案。</span><span class="sxs-lookup"><span data-stu-id="5f55f-106">By querying for the set difference to retrieve the files that are in one folder but not the other.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5f55f-107">這裡顯示的技巧可用於比較任何類型的物件序列。</span><span class="sxs-lookup"><span data-stu-id="5f55f-107">The techniques shown here can be adapted to compare sequences of objects of any type.</span></span>  
  
 <span data-ttu-id="5f55f-108">這裡顯示的 `FileComparer` 類別會示範如何一起使用自訂比較子類別和標準查詢運算子。</span><span class="sxs-lookup"><span data-stu-id="5f55f-108">The `FileComparer` class shown here demonstrates how to use a custom comparer class together with the Standard Query Operators.</span></span> <span data-ttu-id="5f55f-109">此類別不適用於實際案例。</span><span class="sxs-lookup"><span data-stu-id="5f55f-109">The class is not intended for use in real-world scenarios.</span></span> <span data-ttu-id="5f55f-110">它僅使用每個檔案以位元組計的名稱和長度，來判斷每個資料夾的內容是否相同。</span><span class="sxs-lookup"><span data-stu-id="5f55f-110">It just uses the name and length in bytes of each file to determine whether the contents of each folder are identical or not.</span></span> <span data-ttu-id="5f55f-111">在實際案例中，您應該修改此比較子以執行更嚴格的相等檢查。</span><span class="sxs-lookup"><span data-stu-id="5f55f-111">In a real-world scenario, you should modify this comparer to perform a more rigorous equality check.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f55f-112">範例</span><span class="sxs-lookup"><span data-stu-id="5f55f-112">Example</span></span>  
  
```vb  
Module CompareDirs  
    Public Sub Main()  
  
        ' Create two identical or different temporary folders   
        ' on a local drive and add files to them.  
        ' Then set these file paths accordingly.  
        Dim pathA As String = "C:\TestDir"  
        Dim pathB As String = "C:\TestDir2"  
  
        ' Take a snapshot of the file system.   
        Dim dir1 As New System.IO.DirectoryInfo(pathA)  
        Dim dir2 As New System.IO.DirectoryInfo(pathB)  
  
        Dim list1 = dir1.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
        Dim list2 = dir2.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' Create the FileCompare object we'll use in each query  
        Dim myFileCompare As New FileCompare  
  
        ' This query determines whether the two folders contain  
        ' identical file lists, based on the custom file comparer  
        ' that is defined in the FileCompare class.  
        ' The query executes immediately because it returns a bool.  
        Dim areIdentical As Boolean = list1.SequenceEqual(list2, myFileCompare)  
        If areIdentical = True Then  
            Console.WriteLine("The two folders are the same.")  
        Else  
            Console.WriteLine("The two folders are not the same.")  
        End If  
  
        ' Find common files in both folders. It produces a sequence and doesn't execute  
        ' until the foreach statement.  
        Dim queryCommonFiles = list1.Intersect(list2, myFileCompare)  
  
        If queryCommonFiles.Count() > 0 Then  
  
            Console.WriteLine("The following files are in both folders:")  
            For Each fi As System.IO.FileInfo In queryCommonFiles  
                Console.WriteLine(fi.FullName)  
            Next  
        Else  
            Console.WriteLine("There are no common files in the two folders.")  
        End If  
  
        ' Find the set difference between the two folders.  
        ' For this example we only check one way.  
        Dim queryDirAOnly = list1.Except(list2, myFileCompare)  
        Console.WriteLine("The following files are in dirA but not dirB:")  
        For Each fi As System.IO.FileInfo In queryDirAOnly  
            Console.WriteLine(fi.FullName)  
        Next  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
    ' This implementation defines a very simple comparison  
    ' between two FileInfo objects. It only compares the name  
    ' of the files being compared and their length in bytes.  
    Public Class FileCompare  
        Implements System.Collections.Generic.IEqualityComparer(Of System.IO.FileInfo)  
  
        Public Function Equals1(ByVal x As System.IO.FileInfo, ByVal y As System.IO.FileInfo) _  
            As Boolean Implements System.Collections.Generic.IEqualityComparer(Of System.IO.FileInfo).Equals  
  
            If (x.Name = y.Name) And (x.Length = y.Length) Then  
                Return True  
            Else  
                Return False  
            End If  
        End Function  
  
        ' Return a hash that reflects the comparison criteria. According to the   
        ' rules for IEqualityComparer(Of T), if Equals is true, then the hash codes must  
        ' also be equal. Because equality as defined here is a simple value equality, not  
        ' reference identity, it is possible that two or more objects will produce the same  
        ' hash code.  
        Public Function GetHashCode1(ByVal fi As System.IO.FileInfo) _  
            As Integer Implements System.Collections.Generic.IEqualityComparer(Of System.IO.FileInfo).GetHashCode  
            Dim s As String = fi.Name & fi.Length  
            Return s.GetHashCode()  
        End Function  
    End Class  
End Module  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5f55f-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="5f55f-113">Compiling the Code</span></span>  
 <span data-ttu-id="5f55f-114">建立 VB.NET 主控台應用程式專案, 其中包含`Imports` System. Linq 命名空間的語句。</span><span class="sxs-lookup"><span data-stu-id="5f55f-114">Create a VB.NET console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
 
## <a name="see-also"></a><span data-ttu-id="5f55f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f55f-115">See also</span></span>

- [<span data-ttu-id="5f55f-116">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f55f-116">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="5f55f-117">LINQ 與檔案目錄 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f55f-117">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
