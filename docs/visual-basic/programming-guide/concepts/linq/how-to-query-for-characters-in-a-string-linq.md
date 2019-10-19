---
title: 如何：查詢字串中的字元（LINQ）（Visual Basic）
ms.date: 07/20/2015
ms.assetid: 499ebbe0-746c-4235-9dba-ce722c12b50e
ms.openlocfilehash: f2102a8cb149fa9c7886826e509bf254fad5eb95
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582718"
---
# <a name="how-to-query-for-characters-in-a-string-linq-visual-basic"></a>如何：查詢字串中的字元（LINQ）（Visual Basic）

因為 <xref:System.String> 類別會實作泛型 <xref:System.Collections.Generic.IEnumerable%601> 介面，所以可以用字元序列的形式查詢任何字串。 不過，這不是常見的 LINQ 用法。 對於複雜的模式比對作業，使用 <xref:System.Text.RegularExpressions.Regex> 類別。

## <a name="example"></a>範例

下列範例會查詢字串，以判斷它所包含的數字位數。 請注意，查詢會在第一次執行之後「重複使用」。 這可能是因為查詢本身不會儲存任何實際結果。

```vb
Class QueryAString

    Shared Sub Main()

        ' A string is an IEnumerable data source.
        Dim aString As String = "ABCDE99F-J74-12-89A"

        ' Select only those characters that are numbers
        Dim stringQuery = From ch In aString
                          Where Char.IsDigit(ch)
                          Select ch
        ' Execute the query
        For Each c As Char In stringQuery
            Console.Write(c & " ")
        Next

        ' Call the Count method on the existing query.
        Dim count As Integer = stringQuery.Count()
        Console.WriteLine(System.Environment.NewLine & "Count = " & count)

        ' Select all characters before the first '-'
        Dim stringQuery2 = aString.TakeWhile(Function(c) c <> "-")

        ' Execute the second query
        For Each ch In stringQuery2
            Console.Write(ch)
        Next

        Console.WriteLine(System.Environment.NewLine & "Press any key to exit")
        Console.ReadKey()
    End Sub
End Class
' Output:
' 9 9 7 4 1 2 8 9
' Count = 8
' ABCDE99F
```

## <a name="compiling-the-code"></a>編譯程式碼

建立 VB.NET 主控台應用程式專案，其中包含 System. Linq 命名空間的 `Imports` 語句。

## <a name="see-also"></a>請參閱

- [LINQ 和字串（Visual Basic）](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
- [如何：使用正則運算式合併 LINQ 查詢（Visual Basic）](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)
