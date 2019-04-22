---
title: HOW TO：查詢字串 (LINQ) (Visual Basic) 中的字元
ms.date: 07/20/2015
ms.assetid: 499ebbe0-746c-4235-9dba-ce722c12b50e
ms.openlocfilehash: 3f460f635c581eef5655c5707e3dd356e7986d74
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819485"
---
# <a name="how-to-query-for-characters-in-a-string-linq-visual-basic"></a><span data-ttu-id="43c82-102">HOW TO：查詢字串 (LINQ) (Visual Basic) 中的字元</span><span class="sxs-lookup"><span data-stu-id="43c82-102">How to: Query for Characters in a String (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="43c82-103">因為 <xref:System.String> 類別會實作泛型 <xref:System.Collections.Generic.IEnumerable%601> 介面，所以可以用字元序列的形式查詢任何字串。</span><span class="sxs-lookup"><span data-stu-id="43c82-103">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="43c82-104">不過，這不是常見的 LINQ 用法。</span><span class="sxs-lookup"><span data-stu-id="43c82-104">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="43c82-105">對於複雜的模式比對作業，使用 <xref:System.Text.RegularExpressions.Regex> 類別。</span><span class="sxs-lookup"><span data-stu-id="43c82-105">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43c82-106">範例</span><span class="sxs-lookup"><span data-stu-id="43c82-106">Example</span></span>  
 <span data-ttu-id="43c82-107">下列範例會查詢字串，以判斷它所包含的數字位數。</span><span class="sxs-lookup"><span data-stu-id="43c82-107">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="43c82-108">請注意，查詢會在第一次執行之後「重複使用」。</span><span class="sxs-lookup"><span data-stu-id="43c82-108">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="43c82-109">這可能是因為查詢本身不會儲存任何實際結果。</span><span class="sxs-lookup"><span data-stu-id="43c82-109">This is possible because the query itself does not store any actual results.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="43c82-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="43c82-110">Compiling the Code</span></span>  
 <span data-ttu-id="43c82-111">建立以 .NET Framework 3.5 版或更新版本為目標的專案，其中包含對 System.Core.dll 的參考，以及 System.Linq 命名空間的 `Imports` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="43c82-111">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43c82-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43c82-112">See also</span></span>

- [<span data-ttu-id="43c82-113">LINQ 和字串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43c82-113">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
- [<span data-ttu-id="43c82-114">如何：合併 LINQ 查詢與規則運算式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43c82-114">How to: Combine LINQ Queries with Regular Expressions (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)
