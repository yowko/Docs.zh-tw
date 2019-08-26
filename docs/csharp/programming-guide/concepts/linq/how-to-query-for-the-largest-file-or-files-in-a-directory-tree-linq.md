---
title: 作法：查詢樹狀目錄中的最大檔案 (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 20c8a917-0552-4514-b489-0b8b6a4c3b4c
ms.openlocfilehash: 966138795dca53db99a0752b9bb7b85cc4601ee3
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592763"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-c"></a>作法：查詢樹狀目錄中的最大檔案 (LINQ) (C#)
此範例顯示五個與檔案位元組大小相關的查詢：  
  
- 如何擷取最大檔案的位元組大小。  
  
- 如何擷取最小檔案的位元組大小。  
  
- 如何從所指定根資料夾下的一或多個資料夾中，擷取最大或最小檔案的 <xref:System.IO.FileInfo> 物件。  
  
- 如何擷取序列，例如 10 個最大檔案。  
  
- 如何根據檔案位元組大小將檔案分組排序，並略過小於指定大小的檔案。  
  
## <a name="example"></a>範例  
 下列範例包含五個不同的查詢，以示範如何根據檔案位元組大小來查詢和分組檔案。 您可以輕鬆修改這些範例，使查詢根據 <xref:System.IO.FileInfo> 物件的其他某個屬性。  
  
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
  
 若要傳回一或多個完整的 <xref:System.IO.FileInfo> 物件，查詢必須先檢查資料來源中的每個物件，再根據其 Length 屬性值進行排序。 然後，它會傳回具有最大長度的單一物件或物件序列。 使用 <xref:System.Linq.Enumerable.First%2A> 可傳回清單中的第一個項目。 使用 <xref:System.Linq.Enumerable.Take%2A> 則傳回前 n 個項目。 指定遞減排序次序，則會將最小的項目放在清單的開頭。  
  
 查詢會呼叫外面另一個取得檔案位元組大小的方法，以解決可能會因下列狀況引發的例外狀況：自呼叫 `GetFiles` 而建立 <xref:System.IO.FileInfo> 物件以來的這段期間，有另一個執行緒刪除了檔案。 即使已建立 <xref:System.IO.FileInfo> 物件，還是可能會發生這個例外狀況，原因是 <xref:System.IO.FileInfo> 物件會在它的 <xref:System.IO.FileInfo.Length%2A> 屬性第一次受到存取時，嘗試使用目前最新的位元組大小來重新整理這個屬性。 讓這個作業進入查詢外部的 try-catch 區塊，就會遵循規則，以避免查詢中會造成副作業的作業。 一般而言，處理例外狀況時需要十分小心，以確定應用程式不是處於未知狀態。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
建立 C# 主控台應用程式專案，以及具有 `using` 指示詞的 System.Linq 和 System.IO 命名空間。
 
## <a name="see-also"></a>另請參閱

- [LINQ to Objects (C#)](./linq-to-objects.md)
- [LINQ 和檔案目錄 (C#)](./linq-and-file-directories.md)
