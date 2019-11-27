---
title: 如何：查詢字串中的字元 (LINQ)
ms.date: 07/20/2015
ms.assetid: 499ebbe0-746c-4235-9dba-ce722c12b50e
ms.openlocfilehash: 9da6d5abd6155a7af5ec59e17693e8acae7e7b73
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347713"
---
# <a name="how-to-query-for-characters-in-a-string-linq-visual-basic"></a><span data-ttu-id="37b83-102">如何：查詢字串中的字元（LINQ）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="37b83-102">How to: Query for Characters in a String (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="37b83-103">因為 <xref:System.String> 類別會實作泛型 <xref:System.Collections.Generic.IEnumerable%601> 介面，所以可以用字元序列的形式查詢任何字串。</span><span class="sxs-lookup"><span data-stu-id="37b83-103">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="37b83-104">不過，這不是常見的 LINQ 用法。</span><span class="sxs-lookup"><span data-stu-id="37b83-104">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="37b83-105">對於複雜的模式比對作業，使用 <xref:System.Text.RegularExpressions.Regex> 類別。</span><span class="sxs-lookup"><span data-stu-id="37b83-105">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>

## <a name="example"></a><span data-ttu-id="37b83-106">範例</span><span class="sxs-lookup"><span data-stu-id="37b83-106">Example</span></span>

<span data-ttu-id="37b83-107">下列範例會查詢字串，以判斷它所包含的數字位數。</span><span class="sxs-lookup"><span data-stu-id="37b83-107">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="37b83-108">請注意，查詢會在第一次執行之後「重複使用」。</span><span class="sxs-lookup"><span data-stu-id="37b83-108">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="37b83-109">這可能是因為查詢本身不會儲存任何實際結果。</span><span class="sxs-lookup"><span data-stu-id="37b83-109">This is possible because the query itself does not store any actual results.</span></span>

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

## <a name="compiling-the-code"></a><span data-ttu-id="37b83-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="37b83-110">Compiling the Code</span></span>

<span data-ttu-id="37b83-111">建立 VB.NET 主控台應用程式專案，其中包含 System. Linq 命名空間的 `Imports` 語句。</span><span class="sxs-lookup"><span data-stu-id="37b83-111">Create a VB.NET console application project, with an `Imports` statement for the System.Linq namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="37b83-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="37b83-112">See also</span></span>

- [<span data-ttu-id="37b83-113">LINQ 和字串（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="37b83-113">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
- [<span data-ttu-id="37b83-114">如何結合 LINQ 查詢與正則運算式（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="37b83-114">How to combine LINQ queries with regular expressions (Visual Basic)</span></span>](how-to-combine-linq-queries-with-regular-expressions.md)
