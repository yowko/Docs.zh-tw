---
title: HOW TO：填入物件集合，從多個來源 (LINQ) (Visual Basic)
ms.date: 06/22/2018
ms.assetid: 63062a22-e6a9-42c0-b357-c7c965f58f33
ms.openlocfilehash: 65c7e2c791ba8331416ee2eee292f1e8c4888712
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62024322"
---
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-visual-basic"></a><span data-ttu-id="36d11-102">HOW TO：填入物件集合，從多個來源 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36d11-102">How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="36d11-103">此範例示範如何將不同來源的資料合併成新的類型。</span><span class="sxs-lookup"><span data-stu-id="36d11-103">This example shows how to merge data from different sources into a sequence of new types.</span></span>

> [!NOTE]
> <span data-ttu-id="36d11-104">請勿嘗試將記憶體內部資料或檔案系統中的資料，與仍在資料庫中的資料聯結。</span><span class="sxs-lookup"><span data-stu-id="36d11-104">Don't try to join in-memory data or data in the file system with data that is still in a database.</span></span> <span data-ttu-id="36d11-105">這類跨定義域的聯結會產生未定義的結果，因為針對資料庫查詢和其他類型的來源定義聯結作業的方式可能不同。</span><span class="sxs-lookup"><span data-stu-id="36d11-105">Such cross-domain joins can yield undefined results because of different ways in which join operations might be defined for database queries and other types of sources.</span></span> <span data-ttu-id="36d11-106">此外，如果資料庫中的資料量太大，這類作業也可能會導致記憶體不足的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="36d11-106">Additionally, there is a risk that such an operation could cause an out-of-memory exception if the amount of data in the database is large enough.</span></span> <span data-ttu-id="36d11-107">若要將資料庫中的資料聯結至記憶體內部資料，請先在資料庫查詢中呼叫 `ToList` 或 `ToArray`，然後對傳回的集合執行聯結。</span><span class="sxs-lookup"><span data-stu-id="36d11-107">To join data from a database to in-memory data, first call `ToList` or `ToArray` on the database query, and then perform the join on the returned collection.</span></span>

## <a name="to-create-the-data-file"></a><span data-ttu-id="36d11-108">建立資料檔</span><span class="sxs-lookup"><span data-stu-id="36d11-108">To create the data file</span></span>

- <span data-ttu-id="36d11-109">將 names.csv 和 scores.csv 檔案複製到您的專案資料夾中，如[如何：聯結從不同的檔案 (LINQ) (Visual Basic) 的內容](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="36d11-109">Copy the names.csv and scores.csv files into your project folder, as described in [How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md).</span></span>

## <a name="example"></a><span data-ttu-id="36d11-110">範例</span><span class="sxs-lookup"><span data-stu-id="36d11-110">Example</span></span>

<span data-ttu-id="36d11-111">下列範例示範如何使用具名類型 `Student`，來儲存將兩個記憶體內部字串集合合併得來的資料，這些字串模擬 .csv 格式的試算表資料。</span><span class="sxs-lookup"><span data-stu-id="36d11-111">The following example shows how to use a named type `Student` to store merged data from two in-memory collections of strings that simulate spreadsheet data in .csv format.</span></span> <span data-ttu-id="36d11-112">第一個字串集合代表學生姓名和學號，第二個集合代表學生學號 (第一欄) 和四個測驗分數。</span><span class="sxs-lookup"><span data-stu-id="36d11-112">The first collection of strings represents the student names and IDs, and the second collection represents the student ID (in the first column) and four exam scores.</span></span> <span data-ttu-id="36d11-113">學號會作為外部索引鍵使用。</span><span class="sxs-lookup"><span data-stu-id="36d11-113">The ID is used as the foreign key.</span></span>

```vb
Imports System.Collections.Generic
Imports System.Linq

Class Student
    Public FirstName As String
    Public LastName As String
    Public ID As Integer
    Public ExamScores As List(Of Integer)
End Class

Class PopulateCollection

    Shared Sub Main()

        ' Merge content from spreadsheets into a list of Student objects.

        ' These data files are defined in How to: Join Content from
        ' Dissimilar Files (LINQ).

        ' Each line of names.csv consists of a last name, a first name, and an
        ' ID number, separated by commas. For example, Omelchenko,Svetlana,111
        Dim names As String() = System.IO.File.ReadAllLines("../../../names.csv")

        ' Each line of scores.csv consists of an ID number and four test
        ' scores, separated by commas. For example, 111, 97, 92, 81, 60
        Dim scores As String() = System.IO.File.ReadAllLines("../../../scores.csv")

        ' The following query merges the content of two dissimilar spreadsheets
        ' based on common ID values.
        ' Multiple From clauses are used instead of a Join clause
        ' in order to store the results of scoreLine.Split.
        ' Note the dynamic creation of a list of integers for the
        ' ExamScores member. The first item is skipped in the split string
        ' because it is the student ID, not an exam score.
        Dim queryNamesScores = From nameLine In names
                          Let splitName = nameLine.Split(New Char() {","})
                          From scoreLine In scores
                          Let splitScoreLine = scoreLine.Split(New Char() {","})
                          Where Convert.ToInt32(splitName(2)) = Convert.ToInt32(splitScoreLine(0))
                          Select New Student() With {
                               .FirstName = splitName(1), .LastName = splitName(0), .ID = splitName(2),
                               .ExamScores = (From scoreAsText In splitScoreLine Skip 1
                                             Select Convert.ToInt32(scoreAsText)).ToList()}

        ' Optional. Store the query results for faster access in future
        ' queries. This could be useful with very large data files.
        Dim students As List(Of Student) = queryNamesScores.ToList()

        ' Display each student's name and exam score average.
        For Each s In students
            Console.WriteLine("The average score of " & s.FirstName & " " &
                              s.LastName & " is " & s.ExamScores.Average())
        Next

        ' Keep console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()
    End Sub
End Class

' Output:
' The average score of Svetlana Omelchenko is 82.5
' The average score of Claire O'Donnell is 72.25
' The average score of Sven Mortensen is 84.5
' The average score of Cesar Garcia is 88.25
' The average score of Debra Garcia is 67
' The average score of Fadi Fakhouri is 92.25
' The average score of Hanying Feng is 88
' The average score of Hugo Garcia is 85.75
' The average score of Lance Tucker is 81.75
' The average score of Terry Adams is 85.25
' The average score of Eugene Zabokritski is 83
' The average score of Michael Tucker is 92
```

<span data-ttu-id="36d11-114">在  [Select 子句](../../../../visual-basic/language-reference/queries/select-clause.md)子句，物件初始設定式來具現化每個新`Student`物件所使用的兩個來源的資料。</span><span class="sxs-lookup"><span data-stu-id="36d11-114">In the [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md) clause, an object initializer is used to instantiate each new `Student` object by using the data from the two sources.</span></span>

<span data-ttu-id="36d11-115">如果您不需要儲存查詢的結果，則匿名型別會比具名類型更方便使用。</span><span class="sxs-lookup"><span data-stu-id="36d11-115">If you don't have to store the results of a query, anonymous types can be more convenient than named types.</span></span> <span data-ttu-id="36d11-116">如果要在執行查詢的方法外傳遞查詢結果，則必須使用具名類型。</span><span class="sxs-lookup"><span data-stu-id="36d11-116">Named types are required if you pass the query results outside the method in which the query is executed.</span></span> <span data-ttu-id="36d11-117">下列範例會執行與上述範例相同的工作，但使用匿名型別而不是具名類型：</span><span class="sxs-lookup"><span data-stu-id="36d11-117">The following example performs the same task as the previous example, but uses anonymous types instead of named types:</span></span>

```vb
' Merge the data by using an anonymous type.
' Note the dynamic creation of a list of integers for the
' ExamScores member. We skip 1 because the first string
' in the array is the student ID, not an exam score.
Dim queryNamesScores2 =
    From nameLine In names
    Let splitName = nameLine.Split(New Char() {","})
    From scoreLine In scores
    Let splitScoreLine = scoreLine.Split(New Char() {","})
    Where Convert.ToInt32(splitName(2)) = Convert.ToInt32(splitScoreLine(0))
    Select New With
           {.Last = splitName(0),
            .First = splitName(1),
            .ExamScores = (From scoreAsText In splitScoreLine Skip 1
                           Select Convert.ToInt32(scoreAsText)).ToList()}

' Display each student's name and exam score average.
For Each s In queryNamesScores2
    Console.WriteLine("The average score of " & s.First & " " &
                      s.Last & " is " & s.ExamScores.Average())
Next
```

## <a name="compiling-the-code"></a><span data-ttu-id="36d11-118">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="36d11-118">Compiling the code</span></span>

<span data-ttu-id="36d11-119">建立並編譯專案，以下列選項之一為目標：</span><span class="sxs-lookup"><span data-stu-id="36d11-119">Create and compile a project that targets one of the following options:</span></span>

- <span data-ttu-id="36d11-120">.NET Framework 3.5 版與對 System.Core.dll 的參考。</span><span class="sxs-lookup"><span data-stu-id="36d11-120">.NET Framework version 3.5 with a reference to System.Core.dll.</span></span>
- <span data-ttu-id="36d11-121">NET Framework 4.0 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="36d11-121">.NET Framework version 4.0 or higher.</span></span>
- <span data-ttu-id="36d11-122">NET Core 1.0 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="36d11-122">.NET Core version 1.0 or higher.</span></span>

## <a name="see-also"></a><span data-ttu-id="36d11-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36d11-123">See also</span></span>

- [<span data-ttu-id="36d11-124">LINQ 和字串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36d11-124">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
