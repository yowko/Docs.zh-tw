---
title: 如何：依任何字或欄位排序或篩選文字資料 (LINQ)
ms.date: 07/20/2015
ms.assetid: 9df137fe-335b-46e0-aecf-ea8a9eddd4e3
ms.openlocfilehash: 15e7666a5fcb5a16628216354c18599f87c7d905
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341521"
---
# <a name="how-to-sort-or-filter-text-data-by-any-word-or-field-linq-visual-basic"></a><span data-ttu-id="416aa-102">如何：依任何字或欄位排序或篩選文字資料 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="416aa-102">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="416aa-103">下列範例示範如何依行中的任一欄位，來排序多行結構化文字 (例如逗號分隔值)。</span><span class="sxs-lookup"><span data-stu-id="416aa-103">The following example shows how to sort lines of structured text, such as comma-separated values, by any field in the line.</span></span> <span data-ttu-id="416aa-104">此欄位可能會在執行階段以動態方式指定。</span><span class="sxs-lookup"><span data-stu-id="416aa-104">The field may be dynamically specified at runtime.</span></span> <span data-ttu-id="416aa-105">假設 scores.csv 中的欄位各代表學生的學號和四個測驗分數。</span><span class="sxs-lookup"><span data-stu-id="416aa-105">Assume that the fields in scores.csv represent a student's ID number, followed by a series of four test scores.</span></span>

### <a name="to-create-a-file-that-contains-data"></a><span data-ttu-id="416aa-106">建立內含資料的檔案</span><span class="sxs-lookup"><span data-stu-id="416aa-106">To create a file that contains data</span></span>

<span data-ttu-id="416aa-107">Copy the scores.csv data from the topic [How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) and save it to your solution folder.</span><span class="sxs-lookup"><span data-stu-id="416aa-107">Copy the scores.csv data from the topic [How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) and save it to your solution folder.</span></span>

## <a name="example"></a><span data-ttu-id="416aa-108">範例</span><span class="sxs-lookup"><span data-stu-id="416aa-108">Example</span></span>

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

<span data-ttu-id="416aa-109">This example also demonstrates how to return a query variable from a Function.</span><span class="sxs-lookup"><span data-stu-id="416aa-109">This example also demonstrates how to return a query variable from a Function.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="416aa-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="416aa-110">Compiling the Code</span></span>

<span data-ttu-id="416aa-111">Create a VB.NET console application project, with an `Imports` statement for the System.Linq namespace.</span><span class="sxs-lookup"><span data-stu-id="416aa-111">Create a VB.NET console application project, with an `Imports` statement for the System.Linq namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="416aa-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="416aa-112">See also</span></span>

- [<span data-ttu-id="416aa-113">LINQ and Strings (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="416aa-113">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
