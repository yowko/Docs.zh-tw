---
title: 作法：尋找兩個清單 (LINQ) (Visual Basic) 之間的集合差異
ms.date: 07/20/2015
ms.assetid: b5b25474-10a8-4df6-aab5-75621bb6b68e
ms.openlocfilehash: a5c08e270059cd4ab127051d091deff221091fbc
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593472"
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-visual-basic"></a><span data-ttu-id="99f97-102">作法：尋找兩個清單 (LINQ) (Visual Basic) 之間的集合差異</span><span class="sxs-lookup"><span data-stu-id="99f97-102">How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="99f97-103">此範例示範如何使用 LINQ 比較兩份字串清單，然後輸出在 names1.txt 但不在 names2.txt 中的字串行。</span><span class="sxs-lookup"><span data-stu-id="99f97-103">This example shows how to use LINQ to compare two lists of strings and output those lines that are in names1.txt but not in names2.txt.</span></span>  
  
### <a name="to-create-the-data-files"></a><span data-ttu-id="99f97-104">建立資料檔</span><span class="sxs-lookup"><span data-stu-id="99f97-104">To create the data files</span></span>  
  
1. <span data-ttu-id="99f97-105">將 names1.txt 和 names2.txt 複製到您的方案資料夾，如[如何：合併和比較字串集合 (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="99f97-105">Copy names1.txt and names2.txt to your solution folder as shown in [How to: Combine and Compare String Collections (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="99f97-106">範例</span><span class="sxs-lookup"><span data-stu-id="99f97-106">Example</span></span>  
  
```vb  
Class CompareLists  
  
    Shared Sub Main()  
  
        ' Create the IEnumerable data sources.  
        Dim names1 As String() = System.IO.File.ReadAllLines("../../../names1.txt")  
        Dim names2 As String() = System.IO.File.ReadAllLines("../../../names2.txt")  
  
        ' Create the query. Note that method syntax must be used here.  
        Dim differenceQuery = names1.Except(names2)  
        Console.WriteLine("The following lines are in names1.txt but not names2.txt")  
  
        ' Execute the query.  
        For Each name As String In differenceQuery  
            Console.WriteLine(name)  
        Next  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
End Class  
' Output:  
' The following lines are in names1.txt but not names2.txt  
' Potra, Cristina  
' Noriega, Fabricio  
' Aw, Kam Foo  
' Toyoshima, Tim  
' Guy, Wey Yuan  
' Garcia, Debra  
```  
  
 <span data-ttu-id="99f97-107">某些類型的查詢在 Visual Basic 中的作業，例如<xref:System.Linq.Enumerable.Except%2A>， <xref:System.Linq.Enumerable.Distinct%2A>， <xref:System.Linq.Enumerable.Union%2A>，和<xref:System.Linq.Enumerable.Concat%2A>，只能在以方法為基礎的語法中表示。</span><span class="sxs-lookup"><span data-stu-id="99f97-107">Some types of query operations in Visual Basic, such as <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A>, and <xref:System.Linq.Enumerable.Concat%2A>, can only be expressed in method-based syntax.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="99f97-108">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="99f97-108">Compiling the Code</span></span>  
<span data-ttu-id="99f97-109">建立 VB.NET 的主控台應用程式專案，使用`Imports`System.Linq 命名空間陳述式。</span><span class="sxs-lookup"><span data-stu-id="99f97-109">Create a VB.NET console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="99f97-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99f97-110">See also</span></span>

- [<span data-ttu-id="99f97-111">LINQ 和字串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99f97-111">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
