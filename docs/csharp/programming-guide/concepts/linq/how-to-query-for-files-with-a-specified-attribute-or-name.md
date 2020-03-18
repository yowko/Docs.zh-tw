---
title: 如何查詢具有指定屬性或名稱 （C#） 的檔
ms.date: 07/20/2015
ms.assetid: 560e3879-b0b3-4549-ad02-0a53aff2f83c
ms.openlocfilehash: fc6456f159887b7ad109e8ad48f0f79999d53e09
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168865"
---
# <a name="how-to-query-for-files-with-a-specified-attribute-or-name-c"></a>如何查詢具有指定屬性或名稱 （C#） 的檔
這個範例示範如何在指定的樹狀目錄中尋找所有具有指定副檔名 (例如 ".txt") 的檔案。 它也會示範如何根據建立時間來傳回樹狀結構中的最新或最舊檔案。  
  
## <a name="example"></a>範例  
  
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
  
## <a name="compiling-the-code"></a>編譯程式碼  
  建立 C# 主控台應用程式專案，以及具有 `using` 指示詞的 System.Linq 和 System.IO 命名空間。
  
## <a name="see-also"></a>另請參閱

- [LINQ to Objects (C#)](./linq-to-objects.md)
- [LINQ 和檔案目錄 (C#)](./linq-and-file-directories.md)
