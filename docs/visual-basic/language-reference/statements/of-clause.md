---
title: Of 子句 (Visual Basic)
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
ms.openlocfilehash: 9ace0ad55d9eb1618dbdafb0d49d1ff4b169a877
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="of-clause-visual-basic"></a>Of 子句 (Visual Basic)
導入了`Of`子句，用來識別*型別參數*上*泛型*類別、 結構、 介面、 委派或程序。 在泛型類型上的資訊，請參閱[Visual Basic 中的泛型類型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)。  
  
## <a name="using-the-of-keyword"></a>使用的關鍵字  
 下列程式碼範例使用`Of`關鍵字來定義外框的可接受兩個類型參數的類別。 它*限制*`keyType`參數<xref:System.IComparable>介面，這表示使用的程式碼必須提供實作的型別引數<xref:System.IComparable>。 這是必要的讓`add`程序可以呼叫<xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType>方法。 如需有關條件約束的詳細資訊，請參閱[型別清單](../../../visual-basic/language-reference/statements/type-list.md)。  
  
```  
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
  
 如果您完成上述類別定義，您可以建構各種`dictionary`從它的類別。 您提供給型別`entryType`和`keyType`判斷何種類型的項目類別保存，而且它將與每個項目索引鍵的類型。 由於條件約束，您必須提供給`keyType`實作的型別<xref:System.IComparable>。  
  
 下列程式碼範例會建立物件以保留`String`項目並將相關聯`Integer`每個索引鍵。 `Integer` 實作<xref:System.IComparable>並因此滿足條件約束上`keyType`。  
  
```  
Dim d As New dictionary(Of String, Integer)  
```  
  
 `Of` 關鍵字可用於以下內容：  
  
 [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Delegate 陳述式](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Structure 陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IComparable>  
 [類型清單](../../../visual-basic/language-reference/statements/type-list.md)  
 [Visual Basic 中的泛型型別](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
