---
title: 如何：依任何字或欄位排序或篩選文字資料 (LINQ) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9df137fe-335b-46e0-aecf-ea8a9eddd4e3
ms.openlocfilehash: 0e27a72fcb5789ac9a067091aeb150d33f646708
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-sort-or-filter-text-data-by-any-word-or-field-linq-visual-basic"></a>如何：依任何字或欄位排序或篩選文字資料 (LINQ) (Visual Basic)
下列範例示範如何依行中的任一欄位，來排序多行結構化文字 (例如逗號分隔值)。 此欄位可能會在執行階段以動態方式指定。 假設 scores.csv 中的欄位各代表學生的學號和四個測驗分數。  
  
### <a name="to-create-a-file-that-contains-data"></a>建立內含資料的檔案  
  
1.  複製主題 scores.csv 資料[How to： 將內容從不同的檔案 (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md)並將它儲存到您的方案資料夾。  
  
## <a name="example"></a>範例  
  
```vb  
Class SortLines  
  
    Shared Sub Main()  
        Dim scores As String() = System.IO.File.ReadAllLines("../../../scores.csv")  
  
        ' Change this to any value from 0 to 4  
        Dim sortField As Integer = 1  
  
        Console.WriteLine("Sorted highest to lowest by field " & sortField)  
  
        ' Demonstrates how to return query from a method.  
        ' The query is executed here.  
        For Each str As String In SortQuery(scores, sortField)  
            Console.WriteLine(str)  
        Next  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
  
    Shared Function SortQuery(  
        ByVal source As IEnumerable(Of String),   
        ByVal num As Integer) As IEnumerable(Of String)  
  
        Dim scoreQuery = From line In source   
                         Let fields = line.Split(New Char() {","})   
                         Order By fields(num) Descending   
                         Select line  
  
        Return scoreQuery  
    End Function  
End Class  
' Output:  
' Sorted highest to lowest by field 1  
' 116, 99, 86, 90, 94  
' 120, 99, 82, 81, 79  
' 111, 97, 92, 81, 60  
' 114, 97, 89, 85, 82  
' 121, 96, 85, 91, 60  
' 122, 94, 92, 91, 91  
' 117, 93, 92, 80, 87  
' 118, 92, 90, 83, 78  
' 113, 88, 94, 65, 91  
' 112, 75, 84, 91, 39  
' 119, 68, 79, 88, 92  
' 115, 35, 72, 91, 70  
```  
  
 此範例也示範如何從函式傳回的查詢變數。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 建立以 .NET Framework 3.5 版或更新版本為目標的專案，其中包含對 System.Core.dll 的參考，以及 System.Linq 命名空間的 `Imports` 陳述式。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ 和字串 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
