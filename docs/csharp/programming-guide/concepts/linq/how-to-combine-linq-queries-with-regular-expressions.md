---
title: "如何：使用規則運算式合併 LINQ 查詢 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 6b003b65-20a4-4ca2-929e-2ee3f215aecc
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 51cce0d7ffd4806365600ee93d57806af96f08a8
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-combine-linq-queries-with-regular-expressions-c"></a>如何：使用規則運算式合併 LINQ 查詢 (C#)
本例示範如何使用 <xref:System.Text.RegularExpressions.Regex> 類別為文字字串中更複雜的比對建立規則運算式。 LINQ 查詢讓您輕鬆地準確篩選出您想要用規則運算式搜尋的檔案，並調整結果。  
  
## <a name="example"></a>範例  
  
```csharp  
class QueryWithRegEx  
{  
    public static void Main()  
    {  
        // Modify this path as necessary so that it accesses your version of Visual Studio.  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\";  
        // One of the following paths may be more appropriate on your computer.  
        //string startFolder = @"c:\program files (x86)\Microsoft Visual Studio 9.0\";  
        //string startFolder = @"c:\program files\Microsoft Visual Studio 10.0\";  
        //string startFolder = @"c:\program files (x86)\Microsoft Visual Studio 10.0\";  
  
        // Take a snapshot of the file system.  
        IEnumerable<System.IO.FileInfo> fileList = GetFiles(startFolder);  
  
        // Create the regular expression to find all things "Visual".  
        System.Text.RegularExpressions.Regex searchTerm =  
            new System.Text.RegularExpressions.Regex(@"Visual (Basic|C#|C\+\+|J#|SourceSafe|Studio)");  
  
        // Search the contents of each .htm file.  
        // Remove the where clause to find even more matchedValues!  
        // This query produces a list of files where a match  
        // was found, and a list of the matchedValues in that file.  
        // Note: Explicit typing of "Match" in select clause.  
        // This is required because MatchCollection is not a   
        // generic IEnumerable collection.  
        var queryMatchingFiles =  
            from file in fileList  
            where file.Extension == ".htm"  
            let fileText = System.IO.File.ReadAllText(file.FullName)  
            let matches = searchTerm.Matches(fileText)  
            where matches.Count > 0  
            select new  
            {  
                name = file.FullName,  
                matchedValues = from System.Text.RegularExpressions.Match match in matches  
                                select match.Value  
            };  
  
        // Execute the query.  
        Console.WriteLine("The term \"{0}\" was found in:", searchTerm.ToString());  
  
        foreach (var v in queryMatchingFiles)  
        {  
            // Trim the path a bit, then write   
            // the file name in which a match was found.  
            string s = v.name.Substring(startFolder.Length - 1);  
            Console.WriteLine(s);  
  
            // For this file, write out all the matching strings  
            foreach (var v2 in v.matchedValues)  
            {  
                Console.WriteLine("  " + v2);  
            }  
        }  
  
        // Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    // This method assumes that the application has discovery   
    // permissions for all folders under the specified path.  
    static IEnumerable<System.IO.FileInfo> GetFiles(string path)  
    {  
        if (!System.IO.Directory.Exists(path))  
            throw new System.IO.DirectoryNotFoundException();  
  
        string[] fileNames = null;  
        List<System.IO.FileInfo> files = new List<System.IO.FileInfo>();  
  
        fileNames = System.IO.Directory.GetFiles(path, "*.*", System.IO.SearchOption.AllDirectories);  
        foreach (string name in fileNames)  
        {  
            files.Add(new System.IO.FileInfo(name));  
        }  
        return files;  
    }  
}  
```  
  
 請注意，您也可以查詢 `RegEx` 搜尋傳回的 <xref:System.Text.RegularExpressions.MatchCollection> 物件。 在本例中，結果只會產生每個相符項目的值。 不過，它也可以使用 LINQ 對該集合執行所有種類的篩選、排序及群組。 因為 <xref:System.Text.RegularExpressions.MatchCollection> 是非泛型的 <xref:System.Collections.IEnumerable> 集合，所以您必須在查詢中明確指出範圍變數的類型。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 建立以 .NET Framework 3.5 版或更新版本為目標的專案，該專案包含 System.Core.dll 的參考，以及 System.Linq 和 System.IO 命名空間的 `using` 指示詞。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ 和字串 (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)   
 [LINQ 和檔案目錄 (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
