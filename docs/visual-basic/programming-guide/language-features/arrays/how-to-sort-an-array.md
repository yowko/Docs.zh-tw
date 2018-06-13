---
title: 如何：在 Visual Basic 中排序陣列
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: a067c40e1dd0e881516cbc7769cb9afb879d1b9d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646292"
---
# <a name="how-to-sort-an-array-in-visual-basic"></a>如何：在 Visual Basic 中排序陣列
這個範例會宣告陣列`String`物件命名`zooAnimals`，會填入它，然後再依字母順序排序。  
  
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
  
-   存取 Mscorlib.dll 和<xref:System>命名空間。  
  
## <a name="robust-programming"></a>穩固程式設計  
 以下條件可能會造成例外狀況：  
  
-   陣列是空的 (<xref:System.ArgumentNullException>類別)  
  
-   陣列是多維 (<xref:System.RankException>類別)  
  
-   不會實作一個或多個陣列項目的<xref:System.IComparable>介面 (<xref:System.InvalidOperationException>類別)  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Array.Sort%2A?displayProperty=nameWithType>  
 [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [陣列的疑難排解](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)  
 [集合](../../concepts/collections.md)  
 [For Each...Next 陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
