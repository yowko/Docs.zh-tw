---
title: HOW TO：查詢樹狀目錄中的最大檔案 (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 20c8a917-0552-4514-b489-0b8b6a4c3b4c
ms.openlocfilehash: 20453c754c792d4f5c59fde481e1fec56dcd0e09
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564119"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-c"></a><span data-ttu-id="b6912-102">HOW TO：查詢樹狀目錄中的最大檔案 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="b6912-102">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (C#)</span></span>
<span data-ttu-id="b6912-103">此範例顯示五個與檔案位元組大小相關的查詢：</span><span class="sxs-lookup"><span data-stu-id="b6912-103">This example shows five queries related to file size in bytes:</span></span>  
  
-   <span data-ttu-id="b6912-104">如何擷取最大檔案的位元組大小。</span><span class="sxs-lookup"><span data-stu-id="b6912-104">How to retrieve the size in bytes of the largest file.</span></span>  
  
-   <span data-ttu-id="b6912-105">如何擷取最小檔案的位元組大小。</span><span class="sxs-lookup"><span data-stu-id="b6912-105">How to retrieve the size in bytes of the smallest file.</span></span>  
  
-   <span data-ttu-id="b6912-106">如何從所指定根資料夾下的一或多個資料夾中，擷取最大或最小檔案的 <xref:System.IO.FileInfo> 物件。</span><span class="sxs-lookup"><span data-stu-id="b6912-106">How to retrieve the <xref:System.IO.FileInfo> object largest or smallest file from one or more folders under a specified root folder.</span></span>  
  
-   <span data-ttu-id="b6912-107">如何擷取序列，例如 10 個最大檔案。</span><span class="sxs-lookup"><span data-stu-id="b6912-107">How to retrieve a sequence such as the 10 largest files.</span></span>  
  
-   <span data-ttu-id="b6912-108">如何根據檔案位元組大小將檔案分組排序，並略過小於指定大小的檔案。</span><span class="sxs-lookup"><span data-stu-id="b6912-108">How to order files into groups based on their file size in bytes, ignoring files that are less than a specified size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6912-109">範例</span><span class="sxs-lookup"><span data-stu-id="b6912-109">Example</span></span>  
 <span data-ttu-id="b6912-110">下列範例包含五個不同的查詢，以示範如何根據檔案位元組大小來查詢和分組檔案。</span><span class="sxs-lookup"><span data-stu-id="b6912-110">The following example contains five separate queries that show how to query and group files, depending on their file size in bytes.</span></span> <span data-ttu-id="b6912-111">您可以輕鬆修改這些範例，使查詢根據 <xref:System.IO.FileInfo> 物件的其他某個屬性。</span><span class="sxs-lookup"><span data-stu-id="b6912-111">You can easily modify these examples to base the query on some other property of the <xref:System.IO.FileInfo> object.</span></span>  
  
```csharp  
class QueryBySize  
{  
    static void Main(string[] args)  
    {  
        QueryFilesBySize();  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    private static void QueryFilesBySize()  
    {  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\";  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        //Return the size of the largest file  
        long maxSize =  
            (from file in fileList  
             let len = GetFileLength(file)  
             select len)  
             .Max();  
  
        Console.WriteLine("The length of the largest file under {0} is {1}",  
            startFolder, maxSize);  
  
        // Return the FileInfo object for the largest file  
        // by sorting and selecting from beginning of list  
        System.IO.FileInfo longestFile =  
            (from file in fileList  
             let len = GetFileLength(file)  
             where len > 0  
             orderby len descending  
             select file)  
            .First();  
  
        Console.WriteLine("The largest file under {0} is {1} with a length of {2} bytes",  
                            startFolder, longestFile.FullName, longestFile.Length);  
  
        //Return the FileInfo of the smallest file  
        System.IO.FileInfo smallestFile =  
            (from file in fileList  
             let len = GetFileLength(file)  
             where len > 0  
             orderby len ascending  
             select file).First();  
  
        Console.WriteLine("The smallest file under {0} is {1} with a length of {2} bytes",  
                            startFolder, smallestFile.FullName, smallestFile.Length);  
  
        //Return the FileInfos for the 10 largest files  
        // queryTenLargest is an IEnumerable<System.IO.FileInfo>  
        var queryTenLargest =  
            (from file in fileList  
             let len = GetFileLength(file)  
             orderby len descending  
             select file).Take(10);  
  
        Console.WriteLine("The 10 largest files under {0} are:", startFolder);  
  
        foreach (var v in queryTenLargest)  
        {  
            Console.WriteLine("{0}: {1} bytes", v.FullName, v.Length);  
        }  
  
        // Group the files according to their size, leaving out  
        // files that are less than 200000 bytes.   
        var querySizeGroups =  
            from file in fileList  
            let len = GetFileLength(file)  
            where len > 0  
            group file by (len / 100000) into fileGroup  
            where fileGroup.Key >= 2  
            orderby fileGroup.Key descending  
            select fileGroup;  
  
        foreach (var filegroup in querySizeGroups)  
        {  
            Console.WriteLine(filegroup.Key.ToString() + "00000");  
            foreach (var item in filegroup)  
            {  
                Console.WriteLine("\t{0}: {1}", item.Name, item.Length);  
            }  
        }  
    }  
  
    // This method is used to swallow the possible exception  
    // that can be raised when accessing the FileInfo.Length property.  
    // In this particular case, it is safe to swallow the exception.  
    static long GetFileLength(System.IO.FileInfo fi)  
    {  
        long retval;  
        try  
        {  
            retval = fi.Length;  
        }  
        catch (System.IO.FileNotFoundException)  
        {  
            // If a file is no longer present,  
            // just add zero bytes to the total.  
            retval = 0;  
        }  
        return retval;  
    }  
  
}  
```  
  
 <span data-ttu-id="b6912-112">若要傳回一或多個完整的 <xref:System.IO.FileInfo> 物件，查詢必須先檢查資料來源中的每個物件，再根據其 Length 屬性值進行排序。</span><span class="sxs-lookup"><span data-stu-id="b6912-112">To return one or more complete <xref:System.IO.FileInfo> objects, the query first must examine each one in the data source, and then sort them by the value of their Length property.</span></span> <span data-ttu-id="b6912-113">然後，它會傳回具有最大長度的單一物件或物件序列。</span><span class="sxs-lookup"><span data-stu-id="b6912-113">Then it can return the single one or the sequence with the greatest lengths.</span></span> <span data-ttu-id="b6912-114">使用 <xref:System.Linq.Enumerable.First%2A> 可傳回清單中的第一個項目。</span><span class="sxs-lookup"><span data-stu-id="b6912-114">Use <xref:System.Linq.Enumerable.First%2A> to return the first element in a list.</span></span> <span data-ttu-id="b6912-115">使用 <xref:System.Linq.Enumerable.Take%2A> 則傳回前 n 個項目。</span><span class="sxs-lookup"><span data-stu-id="b6912-115">Use <xref:System.Linq.Enumerable.Take%2A> to return the first n number of elements.</span></span> <span data-ttu-id="b6912-116">指定遞減排序次序，則會將最小的項目放在清單的開頭。</span><span class="sxs-lookup"><span data-stu-id="b6912-116">Specify a descending sort order to put the smallest elements at the start of the list.</span></span>  
  
 <span data-ttu-id="b6912-117">查詢會呼叫外面另一個取得檔案位元組大小的方法，以解決可能會因下列狀況引發的例外狀況：自呼叫 `GetFiles` 而建立 <xref:System.IO.FileInfo> 物件以來的這段期間，有另一個執行緒刪除了檔案。</span><span class="sxs-lookup"><span data-stu-id="b6912-117">The query calls out to a separate method to obtain the file size in bytes in order to consume the possible exception that will be raised in the case where a file was deleted on another thread in the time period since the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="b6912-118">即使已建立 <xref:System.IO.FileInfo> 物件，還是可能會發生這個例外狀況，原因是 <xref:System.IO.FileInfo> 物件會在它的 <xref:System.IO.FileInfo.Length%2A> 屬性第一次受到存取時，嘗試使用目前最新的位元組大小來重新整理這個屬性。</span><span class="sxs-lookup"><span data-stu-id="b6912-118">Even through the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property by using the most current size in bytes the first time the property is accessed.</span></span> <span data-ttu-id="b6912-119">讓這個作業進入查詢外部的 try-catch 區塊，就會遵循規則，以避免查詢中會造成副作業的作業。</span><span class="sxs-lookup"><span data-stu-id="b6912-119">By putting this operation in a try-catch block outside the query, we follow the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="b6912-120">一般而言，處理例外狀況時需要十分小心，以確定應用程式不是處於未知狀態。</span><span class="sxs-lookup"><span data-stu-id="b6912-120">In general, great care must be taken when consuming exceptions, to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b6912-121">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="b6912-121">Compiling the Code</span></span>  
 <span data-ttu-id="b6912-122">建立以 .NET Framework 3.5 版或更新版本為目標的專案，該專案包含 System.Core.dll 的參考，以及 System.Linq 和 System.IO 命名空間的 `using` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="b6912-122">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6912-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6912-123">See also</span></span>

- [<span data-ttu-id="b6912-124">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="b6912-124">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="b6912-125">LINQ 和檔案目錄 (C#)</span><span class="sxs-lookup"><span data-stu-id="b6912-125">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
