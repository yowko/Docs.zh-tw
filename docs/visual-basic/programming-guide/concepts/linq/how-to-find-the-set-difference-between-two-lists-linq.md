---
title: 作法：尋找兩份清單之間的集合差異 (LINQ)
ms.date: 07/20/2015
ms.assetid: b5b25474-10a8-4df6-aab5-75621bb6b68e
ms.openlocfilehash: f533b63b40325b34c5881c1e2f14aa4e576191c7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396593"
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-visual-basic"></a><span data-ttu-id="be334-102">如何：尋找兩個清單之間的集合差異（LINQ）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="be334-102">How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="be334-103">此範例示範如何使用 LINQ 比較兩份字串清單，然後輸出在 names1.txt 但不在 names2.txt 中的字串行。</span><span class="sxs-lookup"><span data-stu-id="be334-103">This example shows how to use LINQ to compare two lists of strings and output those lines that are in names1.txt but not in names2.txt.</span></span>  
  
### <a name="to-create-the-data-files"></a><span data-ttu-id="be334-104">建立資料檔</span><span class="sxs-lookup"><span data-stu-id="be334-104">To create the data files</span></span>  
  
1. <span data-ttu-id="be334-105">將 names1.txt 和 names2.txt 複製到您的方案資料夾，如[如何：合併和比較字串集合（LINQ）（Visual Basic）](how-to-combine-and-compare-string-collections-linq.md)中所示。</span><span class="sxs-lookup"><span data-stu-id="be334-105">Copy names1.txt and names2.txt to your solution folder as shown in [How to: Combine and Compare String Collections (LINQ) (Visual Basic)](how-to-combine-and-compare-string-collections-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="be334-106">範例</span><span class="sxs-lookup"><span data-stu-id="be334-106">Example</span></span>  
  
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
  
 <span data-ttu-id="be334-107">Visual Basic 中某些類型的查詢作業，例如 <xref:System.Linq.Enumerable.Except%2A> 、、 <xref:System.Linq.Enumerable.Distinct%2A> <xref:System.Linq.Enumerable.Union%2A> 和 <xref:System.Linq.Enumerable.Concat%2A> ，只能以以方法為基礎的語法來表示。</span><span class="sxs-lookup"><span data-stu-id="be334-107">Some types of query operations in Visual Basic, such as <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A>, and <xref:System.Linq.Enumerable.Concat%2A>, can only be expressed in method-based syntax.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="be334-108">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="be334-108">Compile the code</span></span>  
<span data-ttu-id="be334-109">建立 Visual Basic 的主控台應用程式專案，其中包含 `Imports` System. Linq 命名空間的語句。</span><span class="sxs-lookup"><span data-stu-id="be334-109">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="be334-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be334-110">See also</span></span>

- [<span data-ttu-id="be334-111">LINQ 與字串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="be334-111">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
