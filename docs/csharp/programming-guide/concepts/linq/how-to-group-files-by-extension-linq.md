---
title: 如何：依副檔名分組檔案 (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 21a98320-a5a1-4981-82d8-6a637e7d9018
ms.openlocfilehash: 4b2200799a7623bf9d47540f922798f5161be1bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33319289"
---
# <a name="how-to-group-files-by-extension-linq-c"></a><span data-ttu-id="ea48d-102">如何：依副檔名分組檔案 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="ea48d-102">How to: Group Files by Extension (LINQ) (C#)</span></span>
<span data-ttu-id="ea48d-103">此範例示範如何使用 LINQ，對檔案或資料庫清單執行進階群組和排序作業。</span><span class="sxs-lookup"><span data-stu-id="ea48d-103">This example shows how LINQ can be used to perform advanced grouping and sorting operations on lists of files or folders.</span></span> <span data-ttu-id="ea48d-104">它也示範如何使用 <xref:System.Linq.Enumerable.Skip%2A> 和 <xref:System.Linq.Enumerable.Take%2A> 方法在主控台視窗中分頁輸出。</span><span class="sxs-lookup"><span data-stu-id="ea48d-104">It also shows how to page output in the console window by using the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea48d-105">範例</span><span class="sxs-lookup"><span data-stu-id="ea48d-105">Example</span></span>  
 <span data-ttu-id="ea48d-106">下列查詢示範如何依副檔名分組指定樹狀目錄的內容。</span><span class="sxs-lookup"><span data-stu-id="ea48d-106">The following query shows how to group the contents of a specified directory tree by the file name extension.</span></span>  
  
```csharp  
class GroupByExtension  
{  
    // This query will sort all the files under the specified folder  
    //  and subfolder into groups keyed by the file extension.  
    private static void Main()  
    {  
        // Take a snapshot of the file system.  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\Common7";  
  
        // Used in WriteLine to trim output lines.  
        int trimLength = startFolder.Length;  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        // Create the query.  
        var queryGroupByExt =  
            from file in fileList  
            group file by file.Extension.ToLower() into fileGroup  
            orderby fileGroup.Key  
            select fileGroup;  
  
        // Display one group at a time. If the number of   
        // entries is greater than the number of lines  
        // in the console window, then page the output.  
        PageOutput(trimLength, queryGroupByExt);  
    }  
  
    // This method specifically handles group queries of FileInfo objects with string keys.  
    // It can be modified to work for any long listings of data. Note that explicit typing  
    // must be used in method signatures. The groupbyExtList parameter is a query that produces  
    // groups of FileInfo objects with string keys.  
    private static void PageOutput(int rootLength,  
                                    IEnumerable<System.Linq.IGrouping<string, System.IO.FileInfo>> groupByExtList)  
    {  
        // Flag to break out of paging loop.  
        bool goAgain = true;  
  
        // "3" = 1 line for extension + 1 for "Press any key" + 1 for input cursor.  
        int numLines = Console.WindowHeight - 3;  
  
        // Iterate through the outer collection of groups.  
        foreach (var filegroup in groupByExtList)  
        {  
            // Start a new extension at the top of a page.  
            int currentLine = 0;  
  
            // Output only as many lines of the current group as will fit in the window.  
            do  
            {  
                Console.Clear();  
                Console.WriteLine(filegroup.Key == String.Empty ? "[none]" : filegroup.Key);  
  
                // Get 'numLines' number of items starting at number 'currentLine'.  
                var resultPage = filegroup.Skip(currentLine).Take(numLines);  
  
                //Execute the resultPage query  
                foreach (var f in resultPage)  
                {  
                    Console.WriteLine("\t{0}", f.FullName.Substring(rootLength));  
                }  
  
                // Increment the line counter.  
                currentLine += numLines;  
  
                // Give the user a chance to escape.  
                Console.WriteLine("Press any key to continue or the 'End' key to break...");  
                ConsoleKey key = Console.ReadKey().Key;  
                if (key == ConsoleKey.End)  
                {  
                    goAgain = false;  
                    break;  
                }  
            } while (currentLine < filegroup.Count());  
  
            if (goAgain == false)  
                break;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="ea48d-107">根據本機檔案系統的詳細資料及 `startFolder` 的設定，此程式的輸出可能很長。</span><span class="sxs-lookup"><span data-stu-id="ea48d-107">The output from this program can be long, depending on the details of the local file system and what the `startFolder` is set to.</span></span> <span data-ttu-id="ea48d-108">為了能夠檢視所有結果，此範例示範如何將結果分頁。</span><span class="sxs-lookup"><span data-stu-id="ea48d-108">To enable viewing of all results, this example shows how to page through results.</span></span> <span data-ttu-id="ea48d-109">您可以將相同的技術應用到 Windows 和 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ea48d-109">The same techniques can be applied to Windows and Web applications.</span></span> <span data-ttu-id="ea48d-110">請注意，因為程式碼會將群組中的項目分頁，所以需要使用巢狀 `foreach` 迴圈。</span><span class="sxs-lookup"><span data-stu-id="ea48d-110">Notice that because the code pages the items in a group, a nested `foreach` loop is required.</span></span> <span data-ttu-id="ea48d-111">此外還需要一些額外的邏輯來計算清單中目前的位置，以及讓使用者停止分頁並結束程式。</span><span class="sxs-lookup"><span data-stu-id="ea48d-111">There is also some additional logic to compute the current position in the list, and to enable the user to stop paging and exit the program.</span></span> <span data-ttu-id="ea48d-112">在這種特殊情況下，會對原始查詢的快取結果執行分頁查詢。</span><span class="sxs-lookup"><span data-stu-id="ea48d-112">In this particular case, the paging query is run against the cached results from the original query.</span></span> <span data-ttu-id="ea48d-113">在其他內容中 (例如 LINQ to SQL)，則不需要這類快取。</span><span class="sxs-lookup"><span data-stu-id="ea48d-113">In other contexts, such as LINQ to SQL, such caching is not required.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ea48d-114">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="ea48d-114">Compiling the Code</span></span>  
 <span data-ttu-id="ea48d-115">建立以 .NET Framework 3.5 版或更高版本為目標的專案，該專案包含 System.Core.dll 的參考，以及 System.Linq 和 System.IO 命名空間的 `using` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="ea48d-115">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to   System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea48d-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="ea48d-116">See Also</span></span>  
 [<span data-ttu-id="ea48d-117">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="ea48d-117">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
 [<span data-ttu-id="ea48d-118">LINQ 和檔案目錄 (C#)</span><span class="sxs-lookup"><span data-stu-id="ea48d-118">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
