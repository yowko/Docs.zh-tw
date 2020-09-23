---
title: 作法：尋找兩份清單之間的集合差異 (LINQ)
ms.date: 07/20/2015
ms.assetid: b5b25474-10a8-4df6-aab5-75621bb6b68e
ms.openlocfilehash: 1671cd32c0c0b8a3ff7fa6be87bd43dde9750776
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91100213"
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-visual-basic"></a>如何：尋找兩個清單之間的集合差異 (LINQ)  (Visual Basic) 

此範例示範如何使用 LINQ 比較兩份字串清單，然後輸出在 names1.txt 但不在 names2.txt 中的字串行。  
  
### <a name="to-create-the-data-files"></a>建立資料檔  
  
1. 將 names1.txt 和 names2.txt 複製到您的方案資料夾，如 [如何：合併和比較字串集合 (LINQ)  (](how-to-combine-and-compare-string-collections-linq.md)Visual Basic) 中所示。  
  
## <a name="example"></a>範例  
  
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
  
 Visual Basic 中的某些查詢作業類型（例如 <xref:System.Linq.Enumerable.Except%2A> 、 <xref:System.Linq.Enumerable.Distinct%2A> 、 <xref:System.Linq.Enumerable.Union%2A> 和 <xref:System.Linq.Enumerable.Concat%2A> ）只能以以方法為基礎的語法來表示。  
  
## <a name="compile-the-code"></a>編譯程式碼  

使用 `Imports` 適用于 system.string 命名空間的語句來建立 Visual Basic 主控台應用程式專案。
  
## <a name="see-also"></a>另請參閱

- [LINQ 與字串 (Visual Basic)](linq-and-strings.md)
