---
title: HOW TO：填入物件集合，從多個來源 (LINQ) (Visual Basic)
ms.date: 06/22/2018
ms.assetid: 63062a22-e6a9-42c0-b357-c7c965f58f33
ms.openlocfilehash: 0228d152539abe3bf0db5a8e5bf4581eaf957b31
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638817"
---
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-visual-basic"></a>HOW TO：填入物件集合，從多個來源 (LINQ) (Visual Basic)

此範例示範如何將不同來源的資料合併成新的類型。

> [!NOTE]
> 請勿嘗試將記憶體內部資料或檔案系統中的資料，與仍在資料庫中的資料聯結。 這類跨定義域的聯結會產生未定義的結果，因為針對資料庫查詢和其他類型的來源定義聯結作業的方式可能不同。 此外，如果資料庫中的資料量太大，這類作業也可能會導致記憶體不足的例外狀況。 若要將資料庫中的資料聯結至記憶體內部資料，請先在資料庫查詢中呼叫 `ToList` 或 `ToArray`，然後對傳回的集合執行聯結。

## <a name="to-create-the-data-file"></a>建立資料檔

- 中所述，將 names.csv 和 scores.csv 檔案複製到專案資料夾， [How to:聯結從不同的檔案 (LINQ) (Visual Basic) 的內容](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md)。

## <a name="example"></a>範例

下列範例示範如何使用具名類型 `Student`，來儲存將兩個記憶體內部字串集合合併得來的資料，這些字串模擬 .csv 格式的試算表資料。 第一個字串集合代表學生姓名和學號，第二個集合代表學生學號 (第一欄) 和四個測驗分數。 學號會作為外部索引鍵使用。

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
                               .FirstName = splitName(0), .LastName = splitName(1), .ID = splitName(2),
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
' The average score of Omelchenko Svetlana is 82.5
' The average score of O'Donnell Claire is 72.25
' The average score of Mortensen Sven is 84.5
' The average score of Garcia Cesar is 88.25
' The average score of Garcia Debra is 67
' The average score of Fakhouri Fadi is 92.25
' The average score of Feng Hanying is 88
' The average score of Garcia Hugo is 85.75
' The average score of Tucker Lance is 81.75
' The average score of Adams Terry is 85.25
' The average score of Zabokritski Eugene is 83
' The average score of Tucker Michael is 92
```

在  [Select 子句](../../../../visual-basic/language-reference/queries/select-clause.md)子句，物件初始設定式來具現化每個新`Student`物件所使用的兩個來源的資料。

如果您不需要儲存查詢的結果，則匿名型別會比具名類型更方便使用。 如果要在執行查詢的方法外傳遞查詢結果，則必須使用具名類型。 下列範例會執行與上述範例相同的工作，但使用匿名型別而不是具名類型：

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

## <a name="compiling-the-code"></a>編譯程式碼

建立並編譯專案，以下列選項之一為目標：

- .NET Framework 3.5 版與對 System.Core.dll 的參考。
- NET Framework 4.0 或更高版本。
- NET Core 1.0 或更高版本。

## <a name="see-also"></a>另請參閱

- [LINQ 和字串 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
