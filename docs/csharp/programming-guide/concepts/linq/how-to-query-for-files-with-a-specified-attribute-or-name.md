---
title: 如何：查詢具有指定之屬性或名稱的檔案 (C#)
ms.date: 07/20/2015
ms.assetid: 560e3879-b0b3-4549-ad02-0a53aff2f83c
ms.openlocfilehash: ee366f551eb73059196cb4dcd61c1ca42bf55fda
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-query-for-files-with-a-specified-attribute-or-name-c"></a><span data-ttu-id="90142-102">如何：查詢具有指定之屬性或名稱的檔案 (C#)</span><span class="sxs-lookup"><span data-stu-id="90142-102">How to: Query for Files with a Specified Attribute or Name (C#)</span></span>
<span data-ttu-id="90142-103">這個範例示範如何在指定的樹狀目錄中尋找所有具有指定副檔名 (例如 ".txt") 的檔案。</span><span class="sxs-lookup"><span data-stu-id="90142-103">This example shows how to find all files that have a specified file name extension (for example ".txt") in a specified directory tree.</span></span> <span data-ttu-id="90142-104">它也會示範如何根據建立時間來傳回樹狀結構中的最新或最舊檔案。</span><span class="sxs-lookup"><span data-stu-id="90142-104">It also shows how to return either the newest or oldest file in the tree based on the creation time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90142-105">範例</span><span class="sxs-lookup"><span data-stu-id="90142-105">Example</span></span>  
  
```csharp  
class FindFileByExtension  
{  
    // This query will produce the full path for all .txt files  
    // under the specified folder including subfolders.  
    // It orders the list according to the file name.  
    static void Main()  
    {  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\";  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        //Create the query  
        IEnumerable<System.IO.FileInfo> fileQuery =  
            from file in fileList  
            where file.Extension == ".txt"  
            orderby file.Name  
            select file;  
  
        //Execute the query. This might write out a lot of files!  
        foreach (System.IO.FileInfo fi in fileQuery)  
        {  
            Console.WriteLine(fi.FullName);  
        }  
  
        // Create and execute a new query by using the previous   
        // query as a starting point. fileQuery is not   
        // executed again until the call to Last()  
        var newestFile =  
            (from file in fileQuery  
             orderby file.CreationTime  
             select new { file.FullName, file.CreationTime })  
            .Last();  
  
        Console.WriteLine("\r\nThe newest .txt file is {0}. Creation time: {1}",  
            newestFile.FullName, newestFile.CreationTime);  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="90142-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="90142-106">Compiling the Code</span></span>  
 <span data-ttu-id="90142-107">建立以 .NET Framework 3.5 版或更高版本為目標的專案，該專案包含 System.Core.dll 的參考，以及 System.Linq 和 System.IO 命名空間的 `using` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="90142-107">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to   System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90142-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="90142-108">See Also</span></span>  
 [<span data-ttu-id="90142-109">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="90142-109">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
 [<span data-ttu-id="90142-110">LINQ 和檔案目錄 (C#)</span><span class="sxs-lookup"><span data-stu-id="90142-110">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
