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
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 95c5197b2cb66745201ceac89b78fe67b95ecb75
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-visual-basic"></a><span data-ttu-id="dc472-102">如何：查詢目錄樹狀中的最大檔案 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc472-102">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="dc472-103">此範例顯示五個查詢相關的檔案大小 （位元組）︰</span><span class="sxs-lookup"><span data-stu-id="dc472-103">This example shows five queries related to file size in bytes:</span></span>  
  
-   <span data-ttu-id="dc472-104">如何擷取以位元組為單位的最大檔案大小。</span><span class="sxs-lookup"><span data-stu-id="dc472-104">How to retrieve the size in bytes of the largest file.</span></span>  
  
-   <span data-ttu-id="dc472-105">如何擷取以位元組為單位的最小的檔案大小。</span><span class="sxs-lookup"><span data-stu-id="dc472-105">How to retrieve the size in bytes of the smallest file.</span></span>  
  
-   <span data-ttu-id="dc472-106">如何擷取<xref:System.IO.FileInfo>物件最大或最小檔案，從指定的根資料夾下的一個或多個資料夾。</xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="dc472-106">How to retrieve the <xref:System.IO.FileInfo> object largest or smallest file from one or more folders under a specified root folder.</span></span>  
  
-   <span data-ttu-id="dc472-107">如何擷取序列，例如 10 個最大的檔案。</span><span class="sxs-lookup"><span data-stu-id="dc472-107">How to retrieve a sequence such as the 10 largest files.</span></span>  
  
-   <span data-ttu-id="dc472-108">如何排成群組根據檔案大小 （位元組），略過小於指定大小的檔案。</span><span class="sxs-lookup"><span data-stu-id="dc472-108">How to order files into groups based on their file size in bytes, ignoring files that are less than a specified size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc472-109">範例</span><span class="sxs-lookup"><span data-stu-id="dc472-109">Example</span></span>  
 <span data-ttu-id="dc472-110">下列範例包含五個不同的查詢顯示如何查詢及群組檔案，以位元組為單位的檔案大小而定。</span><span class="sxs-lookup"><span data-stu-id="dc472-110">The following example contains five separate queries that show how to query and group files, depending on their file size in bytes.</span></span> <span data-ttu-id="dc472-111">您可以輕鬆地修改這些範例為基礎的一些其他屬性的查詢<xref:System.IO.FileInfo>物件。</xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="dc472-111">You can easily modify these examples to base the query on some other property of the <xref:System.IO.FileInfo> object.</span></span>  
  
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
  
 <span data-ttu-id="dc472-112">若要傳回一或多個完成<xref:System.IO.FileInfo>物件查詢首先必須檢查每個資料來源，然後再將它們排序其 Length 屬性的值。</xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="dc472-112">To return one or more complete <xref:System.IO.FileInfo> objects, the query first must examine each one in the data source, and then sort them by the value of their Length property.</span></span> <span data-ttu-id="dc472-113">然後它會傳回單一物件或順序具有最大長度。</span><span class="sxs-lookup"><span data-stu-id="dc472-113">Then it can return the single one or the sequence with the greatest lengths.</span></span> <span data-ttu-id="dc472-114">使用<xref:System.Linq.Enumerable.First%2A>傳回清單中的第一個項目。</xref:System.Linq.Enumerable.First%2A></span><span class="sxs-lookup"><span data-stu-id="dc472-114">Use <xref:System.Linq.Enumerable.First%2A> to return the first element in a list.</span></span> <span data-ttu-id="dc472-115">使用<xref:System.Linq.Enumerable.Take%2A>傳回的第 n 個項目。</xref:System.Linq.Enumerable.Take%2A></span><span class="sxs-lookup"><span data-stu-id="dc472-115">Use <xref:System.Linq.Enumerable.Take%2A> to return the first n number of elements.</span></span> <span data-ttu-id="dc472-116">指定遞減的排序順序，將最小項目清單的開頭。</span><span class="sxs-lookup"><span data-stu-id="dc472-116">Specify a descending sort order to put the smallest elements at the start of the list.</span></span>  
  
 <span data-ttu-id="dc472-117">查詢會呼叫另一個方法來取得檔案大小 （位元組），才能使用可能會在案例中，檔案已刪除另一個執行緒的時間週期之後引發的例外狀況<xref:System.IO.FileInfo>物件建立於呼叫`GetFiles`。</xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="dc472-117">The query calls out to a separate method to obtain the file size in bytes in order to consume the possible exception that will be raised in the case where a file was deleted on another thread in the time period since the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="dc472-118">即使透過<xref:System.IO.FileInfo>物件已建立，可能會發生例外狀況，因為<xref:System.IO.FileInfo>物件將會嘗試重新整理其<xref:System.IO.FileInfo.Length%2A>屬性，以位元組為單位的第一次存取該屬性時使用的最新的大小。</xref:System.IO.FileInfo.Length%2A> </xref:System.IO.FileInfo> </xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="dc472-118">Even through the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property by using the most current size in bytes the first time the property is accessed.</span></span> <span data-ttu-id="dc472-119">將這項作業放在 try catch 區塊中的查詢之外，我們要遵循的規則，避免可能會造成副作用的查詢中的作業。</span><span class="sxs-lookup"><span data-stu-id="dc472-119">By putting this operation in a try-catch block outside the query, we follow the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="dc472-120">一般情況下，絕佳必須小心使用例外狀況時，以確定應用程式未處於未知狀態。</span><span class="sxs-lookup"><span data-stu-id="dc472-120">In general, great care must be taken when consuming exceptions, to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="dc472-121">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="dc472-121">Compiling the Code</span></span>  
 <span data-ttu-id="dc472-122">建立以.NET Framework 3.5 版或以上版本，搭配 system.core.dll 的參考目標的專案和`Imports`System.Linq 命名空間陳述式。</span><span class="sxs-lookup"><span data-stu-id="dc472-122">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc472-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc472-123">See Also</span></span>  
 <span data-ttu-id="dc472-124">[LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md) </span><span class="sxs-lookup"><span data-stu-id="dc472-124">[LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md) </span></span>  
<span data-ttu-id="dc472-125"> [LINQ 和檔案目錄 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)</span><span class="sxs-lookup"><span data-stu-id="dc472-125"> [LINQ and File Directories (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)</span></span>
