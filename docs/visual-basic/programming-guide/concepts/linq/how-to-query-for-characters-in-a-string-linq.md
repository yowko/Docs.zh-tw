---
title: 如何：查詢字串中的字元 (LINQ)
ms.date: 07/20/2015
ms.assetid: 499ebbe0-746c-4235-9dba-ce722c12b50e
ms.openlocfilehash: 2f306a488610aaa5775210eba3d7312b092545a7
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345516"
---
# <a name="how-to-query-for-characters-in-a-string-linq-visual-basic"></a><span data-ttu-id="1311e-102">如何：查詢字串中的字元（LINQ）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="1311e-102">How to: Query for Characters in a String (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="1311e-103">因為 <xref:System.String> 類別會實作泛型 <xref:System.Collections.Generic.IEnumerable%601> 介面，所以可以用字元序列的形式查詢任何字串。</span><span class="sxs-lookup"><span data-stu-id="1311e-103">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="1311e-104">不過，這不是常見的 LINQ 用法。</span><span class="sxs-lookup"><span data-stu-id="1311e-104">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="1311e-105">對於複雜的模式比對作業，使用 <xref:System.Text.RegularExpressions.Regex> 類別。</span><span class="sxs-lookup"><span data-stu-id="1311e-105">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>

## <a name="example"></a><span data-ttu-id="1311e-106">範例</span><span class="sxs-lookup"><span data-stu-id="1311e-106">Example</span></span>

<span data-ttu-id="1311e-107">下列範例會查詢字串，以判斷它所包含的數字位數。</span><span class="sxs-lookup"><span data-stu-id="1311e-107">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="1311e-108">請注意，查詢會在第一次執行之後「重複使用」。</span><span class="sxs-lookup"><span data-stu-id="1311e-108">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="1311e-109">這可能是因為查詢本身不會儲存任何實際結果。</span><span class="sxs-lookup"><span data-stu-id="1311e-109">This is possible because the query itself does not store any actual results.</span></span>

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

## <a name="compile-the-code"></a><span data-ttu-id="1311e-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="1311e-110">Compile the code</span></span>

<span data-ttu-id="1311e-111">建立 Visual Basic 的主控台應用程式專案，其中包含 System. Linq 命名空間的 `Imports` 語句。</span><span class="sxs-lookup"><span data-stu-id="1311e-111">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="1311e-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="1311e-112">See also</span></span>

- [<span data-ttu-id="1311e-113">LINQ 和字串（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="1311e-113">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
- [<span data-ttu-id="1311e-114">如何結合 LINQ 查詢與正則運算式（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="1311e-114">How to combine LINQ queries with regular expressions (Visual Basic)</span></span>](how-to-combine-linq-queries-with-regular-expressions.md)
