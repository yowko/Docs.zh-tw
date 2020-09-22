---
title: Of 子句
ms.date: 07/20/2015
f1_keywords:
- Of
- vb.Of
- vb.of
helpviewer_keywords:
- Of keyword [Visual Basic]
- arguments [Visual Basic], data types
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
ms.assetid: 0db8f65c-65af-4089-ab7f-6fcfecb60444
ms.openlocfilehash: 0595356fb75fc0ac73a49622d71fe1d28fa7b648
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90865906"
---
# <a name="of-clause-visual-basic"></a>Of 子句 (Visual Basic)

引進 `Of` 子句，這個子句會識別*泛型*類別、結構、介面、委派或程式的*型別參數*。 如需泛型型別的詳細資訊，請參閱 [Visual Basic 中的泛型型別](../../programming-guide/language-features/data-types/generic-types.md)。  
  
## <a name="using-the-of-keyword"></a>使用 of 關鍵字  

 下列程式碼範例會使用 `Of` 關鍵字來定義採用兩個型別參數之類別的大綱。 它*constrains*會限制 `keyType` 介面的參數 <xref:System.IComparable> ，這表示使用程式碼必須提供實作為的型別引數 <xref:System.IComparable> 。 這是必要的，如此程式 `add` 才能呼叫 <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> 方法。 如需條件約束的詳細資訊，請參閱 [Type List](type-list.md)。  
  
```vb  
Public Class Dictionary(Of entryType, keyType As IComparable)  
    Public Sub add(ByVal e As entryType, ByVal k As keyType)  
        Dim dk As keyType  
        If k.CompareTo(dk) = 0 Then  
        End If  
    End Sub  
    Public Function find(ByVal k As keyType) As entryType  
    End Function  
End Class  
```  
  
 如果您完成上述類別定義，就可以 `dictionary` 從其建立各種類別。 您提供給的 `entryType` 型別， `keyType` 會決定類別保存的專案類型，以及它與每個專案相關聯的索引鍵類型。 由於條件約束的限制，您必須提供給實的 `keyType` 型別 <xref:System.IComparable> 。  
  
 下列程式碼範例會建立保存專案的物件 `String` ，並將索引 `Integer` 鍵與每一個索引鍵產生關聯。 `Integer`<xref:System.IComparable>在上執行，因此符合條件約束 `keyType` 。  
  
```vb  
Dim d As New dictionary(Of String, Integer)  
```  
  
 `Of` 關鍵字可用於以下內容：  
  
 [Class 陳述式](class-statement.md)  
  
 [Delegate 陳述式](delegate-statement.md)  
  
 [Function 陳述式](function-statement.md)  
  
 [Interface 陳述式](interface-statement.md)  
  
 [Structure 陳述式](structure-statement.md)  
  
 [Sub 陳述式](sub-statement.md)  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IComparable>
- [Type List](type-list.md)
- [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [位置](../modifiers/in-generic-modifier.md)
- [擴展](../modifiers/out-generic-modifier.md)
