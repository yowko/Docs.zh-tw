---
title: HOW TO：在 Visual Basic 中排序陣列
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: 3f4dbd6dce0957de3451b1f29c3a67ccd6791045
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838075"
---
# <a name="how-to-sort-an-array-in-visual-basic"></a>HOW TO：在 Visual Basic 中排序陣列
這個範例會宣告陣列`String`命名的物件`zooAnimals`，填入它，然後依字母順序排序。  
  
## <a name="example"></a>範例  
  
```  
Private Sub sortAnimals()  
    Dim zooAnimals(2) As String  
    zooAnimals(0) = "lion"  
    zooAnimals(1) = "turtle"  
    zooAnimals(2) = "ostrich"  
    Array.Sort(zooAnimals)  
End Sub  
```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   Mscorlib.dll 的存取和<xref:System>命名空間。  
  
## <a name="robust-programming"></a>穩固程式設計  
 以下條件可能會造成例外狀況：  
  
-   陣列是空的 (<xref:System.ArgumentNullException>類別)  
  
-   陣列是多維 (<xref:System.RankException>類別)  
  
-   陣列的一個或多個項目不會實作<xref:System.IComparable>介面 (<xref:System.InvalidOperationException>類別)  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [陣列的疑難排解](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
- [集合](../../concepts/collections.md)
- [For Each...Next 陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
