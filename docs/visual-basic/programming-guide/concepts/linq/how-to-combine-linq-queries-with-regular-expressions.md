---
title: How to combine LINQ queries with regular expressions
ms.date: 07/20/2015
ms.assetid: 3da1bd10-b0d8-4d5b-a637-966891c13592
ms.openlocfilehash: 27fc46056ad78567339ca0c5818aef38d0fbb9a6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348424"
---
# <a name="how-to-combine-linq-queries-with-regular-expressions-visual-basic"></a><span data-ttu-id="6fa67-102">How to combine LINQ queries with regular expressions (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6fa67-102">How to combine LINQ queries with regular expressions (Visual Basic)</span></span>

<span data-ttu-id="6fa67-103">此範例會示範如何使用 <xref:System.Text.RegularExpressions.Regex> 類別來建立規則運算式，以在文字字串中進行更複雜的比對。</span><span class="sxs-lookup"><span data-stu-id="6fa67-103">This example shows how to use the <xref:System.Text.RegularExpressions.Regex> class to create a regular expression for more complex matching in text strings.</span></span> <span data-ttu-id="6fa67-104">LINQ 查詢讓您輕鬆地準確篩選出您想要用規則運算式搜尋的檔案，並調整結果。</span><span class="sxs-lookup"><span data-stu-id="6fa67-104">The LINQ query makes it easy to filter on exactly the files that you want to search with the regular expression, and to shape the results.</span></span>

## <a name="example"></a><span data-ttu-id="6fa67-105">範例</span><span class="sxs-lookup"><span data-stu-id="6fa67-105">Example</span></span>

```vb
Imports System.IO
Imports System.Text.RegularExpressions

Class LinqRegExVB

    Shared Sub Main()

        ' Root folder to query, along with all subfolders.
        ' Modify this path as necessary so that it accesses your Visual Studio folder.
        Dim startFolder As String = "C:\Program Files (x86)\Microsoft Visual Studio 14.0\"
        ' One of the following paths may be more appropriate on your computer.
        'Dim startFolder As String = "C:\Program Files (x86)\Microsoft Visual Studio\2017\"

        ' Take a snapshot of the file system.
        Dim fileList As IEnumerable(Of FileInfo) = GetFiles(startFolder)

        ' Create a regular expression to find all things "Visual".
        Dim searchTerm As New Regex("Visual (Basic|C#|C\+\+|Studio)")

        ' Search the contents of each .htm file.
        ' Remove the where clause to find even more matches!
        ' This query produces a list of files where a match
        ' was found, and a list of the matches in that file.
        ' Note: Explicit typing of "Match" in select clause.
        ' This is required because MatchCollection is not a
        ' generic IEnumerable collection.
        Dim queryMatchingFiles = From afile In fileList
                                Where afile.Extension = ".htm"
                                Let fileText = File.ReadAllText(afile.FullName)
                                Let matches = searchTerm.Matches(fileText)
                                Where (matches.Count > 0)
                                Select Name = afile.FullName,
                                       Matches = From match As Match In matches
                                                 Select match.Value

        ' Execute the query.
        Console.WriteLine("The term " & searchTerm.ToString() & " was found in:")

        For Each fileMatches In queryMatchingFiles
            ' Trim the path a bit, then write
            ' the file name in which a match was found.
            Dim s = fileMatches.Name.Substring(startFolder.Length - 1)
            Console.WriteLine(s)

            ' For this file, write out all the matching strings
            For Each match In fileMatches.Matches
                Console.WriteLine("  " + match)
            Next
        Next

        ' Keep the console window open in debug mode
        Console.WriteLine("Press any key to exit")
        Console.ReadKey()
    End Sub

    ' Function to retrieve a list of files. Note that this is a copy
    ' of the file information.
    Shared Function GetFiles(root As String) As IEnumerable(Of FileInfo)
        Return From file In My.Computer.FileSystem.GetFiles(
                   root, FileIO.SearchOption.SearchAllSubDirectories, "*.*")
               Select New FileInfo(file)
    End Function

End Class
```

<span data-ttu-id="6fa67-106">請注意，您也可以對由 `RegEx` 搜尋所傳回的 <xref:System.Text.RegularExpressions.MatchCollection> 物件進行查詢。</span><span class="sxs-lookup"><span data-stu-id="6fa67-106">Note that you can also query the <xref:System.Text.RegularExpressions.MatchCollection> object that is returned by a `RegEx` search.</span></span> <span data-ttu-id="6fa67-107">在本例中，結果只會產生每個相符項目的值。</span><span class="sxs-lookup"><span data-stu-id="6fa67-107">In this example only the value of each match is produced in the results.</span></span> <span data-ttu-id="6fa67-108">不過，它也可以使用 LINQ 對該集合執行所有種類的篩選、排序及群組。</span><span class="sxs-lookup"><span data-stu-id="6fa67-108">However, it is also possible to use LINQ to perform all kinds of filtering, sorting, and grouping on that collection.</span></span> <span data-ttu-id="6fa67-109">因為 <xref:System.Text.RegularExpressions.MatchCollection> 為非泛型 <xref:System.Collections.IEnumerable> 集合，所以您必須在查詢中明確地陳述範圍變數的類型。</span><span class="sxs-lookup"><span data-stu-id="6fa67-109">Because <xref:System.Text.RegularExpressions.MatchCollection> is a non-generic <xref:System.Collections.IEnumerable> collection, you have to explicitly state the type of the range variable in the query.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="6fa67-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="6fa67-110">Compiling the code</span></span>

<span data-ttu-id="6fa67-111">Create a VB.NET console application project, copy and paste the code sample, and adjust the Startup object value in the project properties.</span><span class="sxs-lookup"><span data-stu-id="6fa67-111">Create a VB.NET console application project, copy and paste the code sample, and adjust the Startup object value in the project properties.</span></span>

## <a name="see-also"></a><span data-ttu-id="6fa67-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="6fa67-112">See also</span></span>

- [<span data-ttu-id="6fa67-113">LINQ and Strings (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6fa67-113">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
- [<span data-ttu-id="6fa67-114">LINQ 與檔案目錄 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6fa67-114">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
