---
title: 宣告為 for 迴圈控制變數的陣列不能宣告它的初始大小
ms.date: 07/20/2015
f1_keywords:
- vbc32039
- bc32039
helpviewer_keywords:
- BC32039
ms.assetid: 1d8b6560-c9eb-4b71-a038-24c6f5a5ce46
ms.openlocfilehash: 9e8bb7b79b5a770c3c92e47d8e7c01c5b83d6061
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701215"
---
# <a name="array-declared-as-for-loop-control-variable-cannot-be-declared-with-an-initial-size"></a>宣告為 for 迴圈控制變數的陣列不能宣告它的初始大小
@No__t-0 迴圈使用陣列做為其*元素*反復專案變數，但會初始化該陣列。  
  
 下列語句會顯示如何產生此錯誤。  
  
```vb  
Dim arrayList As New List(Of Integer())  
For Each listElement() As Integer In arrayList  
For Each listElement(1) As Integer In arrayList  
```  
  
 第一個 `For Each` 語句是存取 `arrayList` 之元素的正確方式。 第二個 `For Each` 語句會產生此錯誤。  
  
 **錯誤識別碼：** BC32039  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 從*元素*反復專案變數的宣告中移除初始化。  
  
## <a name="see-also"></a>另請參閱

- [For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [集合](../../../standard/collections/index.md)
