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
ms.openlocfilehash: c0cfbb5109d5b49f995028944e735c96440c9ab2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583513"
---
# <a name="of-clause-visual-basic"></a>Of 子句 (Visual Basic)
引進了一個 `Of` 子句，它會識別*泛型*類別、結構、介面、委派或程式上的*型別參數*。 如需泛型型別的詳細資訊，請參閱[Visual Basic 中的泛型型別](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)。  
  
## <a name="using-the-of-keyword"></a>使用 of 關鍵字  
 下列程式碼範例會使用 `Of` 關鍵字來定義接受兩個型別參數之類別的外框。 它會*限制*<xref:System.IComparable> 介面的 `keyType` 參數，這表示取用的程式碼必須提供實作為 <xref:System.IComparable> 的型別引數。 這是必要的，因此 `add` 程式可以呼叫 <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> 方法。 如需條件約束的詳細資訊，請參閱 [Type List](../../../visual-basic/language-reference/statements/type-list.md)。  
  
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
  
 如果您完成上述類別定義，您可以從它建立各種不同的 `dictionary` 類別。 您提供給 `entryType` 的型別，`keyType` 會決定類別所保存的專案類型，以及與每個專案相關聯的索引鍵類型。 由於條件約束的原因，您必須提供來 `keyType` 可執行 <xref:System.IComparable> 的類型。  
  
 下列程式碼範例會建立一個物件，它會保存 `String` 專案，並將 `Integer` 索引鍵與每一個金鑰相關聯。 `Integer` 會執行 <xref:System.IComparable>，因此滿足 `keyType` 上的條件約束。  
  
```vb  
Dim d As New dictionary(Of String, Integer)  
```  
  
 `Of` 關鍵字可用於以下內容：  
  
 [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Delegate 陳述式](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Structure 陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>請參閱

- <xref:System.IComparable>
- [類型清單](../../../visual-basic/language-reference/statements/type-list.md)
- [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
