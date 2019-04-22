---
title: 宣告為 for 迴圈控制變數的陣列不能宣告它的初始大小
ms.date: 07/20/2015
f1_keywords:
- vbc32039
- bc32039
helpviewer_keywords:
- BC32039
ms.assetid: 1d8b6560-c9eb-4b71-a038-24c6f5a5ce46
ms.openlocfilehash: bee3bcd3701945f5cf77f6761defc8be77acf49f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58843574"
---
# <a name="array-declared-as-for-loop-control-variable-cannot-be-declared-with-an-initial-size"></a>宣告為 for 迴圈控制變數的陣列不能宣告它的初始大小
A`For Each`迴圈會使用陣列做為其*項目*反覆運算變數但初始化該陣列。  
  
 下列陳述式會顯示可以產生此錯誤的方式。  
  
```  
Dim arrayList As New List(Of Integer())  
For Each listElement() As Integer In arrayList  
For Each listElement(1) As Integer In arrayList  
```  
  
 第一個`For Each`陳述式是正確的方式來存取元素的`arrayList`。 第二個`For Each`陳述式會產生這個錯誤。  
  
 **錯誤 ID:** BC32039  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   從宣告中移除初始化*項目*反覆運算變數。  
  
## <a name="see-also"></a>另請參閱

- [For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [集合](../../../standard/collections/index.md)
