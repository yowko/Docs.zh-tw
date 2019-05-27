---
title: 作法：查詢資料夾中的文字檔內容 (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: f5b4dce7-1a34-4eb4-9bf1-60d5bdda264c
ms.openlocfilehash: 1be896f257395cb1e70718ac55e3199da09d8961
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65585849"
---
# <a name="how-to-query-the-contents-of-text-files-in-a-folder-linq-c"></a><span data-ttu-id="a0aa6-102">作法：查詢資料夾中的文字檔內容 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a0aa6-102">How to: Query the Contents of Text Files in a Folder (LINQ) (C#)</span></span>
<span data-ttu-id="a0aa6-103">此範例示範如何查詢所指定樹狀目錄中的所有檔案、開啟每個檔案，然後檢查檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="a0aa6-103">This example shows how to query over all the files in a specified directory tree, open each file, and inspect its contents.</span></span> <span data-ttu-id="a0aa6-104">這類技巧可以用來建立索引，或將樹狀目錄內容的索引反轉。</span><span class="sxs-lookup"><span data-stu-id="a0aa6-104">This type of technique could be used to create indexes or reverse indexes of the contents of a directory tree.</span></span> <span data-ttu-id="a0aa6-105">在此範例中，執行的是簡單字串搜尋。</span><span class="sxs-lookup"><span data-stu-id="a0aa6-105">A simple string search is performed in this example.</span></span> <span data-ttu-id="a0aa6-106">不過，您可以使用規則運算式執行更複雜的模式比對類型。</span><span class="sxs-lookup"><span data-stu-id="a0aa6-106">However, more complex types of pattern matching can be performed with a regular expression.</span></span> <span data-ttu-id="a0aa6-107">如需詳細資訊，請參閱[如何：使用規則運算式合併 LINQ 查詢 (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="a0aa6-107">For more information, see [How to: Combine LINQ Queries with Regular Expressions (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0aa6-108">範例</span><span class="sxs-lookup"><span data-stu-id="a0aa6-108">Example</span></span>  
  
```csharp  
class QueryContents  
{  
    public static void Main()  
    {  
        // Modify this path as necessary.  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\";  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        string searchTerm = @"Visual Studio";  
  
        // Search the contents of each file.  
        // A regular expression created with the RegEx class  
        // could be used instead of the Contains method.  
        // queryMatchingFiles is an IEnumerable<string>.  
        var queryMatchingFiles =  
            from file in fileList  
            where file.Extension == ".htm"  
            let fileText = GetFileText(file.FullName)  
            where fileText.Contains(searchTerm)  
            select file.FullName;  
  
        // Execute the query.  
        Console.WriteLine("The term \"{0}\" was found in:", searchTerm);  
        foreach (string filename in queryMatchingFiles)  
        {  
            Console.WriteLine(filename);  
        }  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    // Read the contents of the file.  
    static string GetFileText(string name)  
    {  
        string fileContents = String.Empty;  
  
        // If the file has been deleted since we took   
        // the snapshot, ignore it and return the empty string.  
        if (System.IO.File.Exists(name))  
        {  
            fileContents = System.IO.File.ReadAllText(name);  
        }  
        return fileContents;  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a0aa6-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="a0aa6-109">Compiling the Code</span></span>  
<span data-ttu-id="a0aa6-110">建立 C# 主控台應用程式專案，以及具有 `using` 指示詞的 System.Linq 和 System.IO 命名空間。</span><span class="sxs-lookup"><span data-stu-id="a0aa6-110">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a0aa6-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0aa6-111">See also</span></span>

- [<span data-ttu-id="a0aa6-112">LINQ 和檔案目錄 (C#)</span><span class="sxs-lookup"><span data-stu-id="a0aa6-112">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
- [<span data-ttu-id="a0aa6-113">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="a0aa6-113">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
