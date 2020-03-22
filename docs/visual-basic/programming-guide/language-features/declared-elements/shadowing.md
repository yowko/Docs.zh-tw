---
title: 遮蔽
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], shadowing
- overriding, and shadowing
- shadowing
- duplicate names [Visual Basic]
- shadowing, by inheritance
- declared elements [Visual Basic], referencing
- shadowing, by scope
- declared elements [Visual Basic], hiding
- naming conflicts, shadowing
- declared elements [Visual Basic], shadowing
- shadowing, and overriding
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic], about
- objects [Visual Basic], names
- names [Visual Basic], shadowing
ms.assetid: 54bb4c25-12c4-4181-b4a0-93546053964e
ms.openlocfilehash: 20a33478f622fca6d3183772f53dcb3e72f79409
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266881"
---
# <a name="shadowing-in-visual-basic"></a>Visual Basic 中的遮蔽功能
當兩個程式設計元素共用相同的名稱時，其中一個元素可以隱藏或*隱藏*另一個。 在這種情況下，陰影元素不能供參考;相反，當代碼使用元素名稱時，Visual Basic 編譯器會將其解析為隱藏元素。  
  
## <a name="purpose"></a>目的  
 陰影的主要目的是保護類成員的定義。 基類可能會經歷一個更改，該更改創建與已定義的元素同名的元素。 如果發生這種情況，`Shadows`修改器將強制通過類的引用解析為您定義的成員，而不是新的基類元素。  
  
## <a name="types-of-shadowing"></a>陰影類型  
 元素可以通過兩種不同的方式隱藏另一個元素。 陰影元素可以在包含陰影元素的區域的次區域內聲明，在這種情況下，陰影*是通過作用域*完成的。 或者派生類可以重新定義基類的成員，在這種情況下，陰影*是通過繼承*來完成的。  
  
### <a name="shadowing-through-scope"></a>陰影範圍  
 同一模組、類或結構中的程式設計元素可以具有相同的名稱但範圍不同。 以這種方式聲明兩個元素並且代碼引用它們共用的名稱時，具有較窄範圍的元素會陰影另一個元素（塊作用域是最窄的）。  
  
 例如，模組可以定義名為 的`Public``temp`變數，模組中的過程可以聲明也命名為 的`temp`區域變數。 從過程`temp`內部對的引用訪問區域變數，而從過程外部`temp`的引用訪問`Public`該變數。 在這種情況下，過程變數`temp`對模組變數`temp`進行陰影。  
  
 下圖顯示了兩個變數，這兩個變數`temp`都命名為 。 當從其`temp`自己的過程中`p`訪問成員`temp`變數時，區域變數將隱藏成員變數。 但是，`MyClass`關鍵字繞過陰影並訪問成員變數。  
  
 ![顯示陰影範圍的圖形。](./media/shadowing/shadow-scope-diagram.gif)
  
 有關在作用域中隱藏的示例，請參閱[如何：隱藏與變數同名的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)。  
  
### <a name="shadowing-through-inheritance"></a>通過繼承進行陰影  
 如果派生類重新定義從基類繼承的程式設計元素，則重新定義元素將隱藏原始元素。 可以使用任何其他類型隱藏任何類型的聲明元素或一組重載元素。 例如，`Integer`變數可以隱藏`Function`過程。 如果使用另一個過程對過程進行陰影，則可以使用不同的參數清單和不同的返回類型。  
  
 下圖顯示了從`b``b`繼承的基類和派生類`d`。 基類定義名為 的過程`proc`，派生類使用另一個同名過程來隱藏它。 第一`Call`個語句訪問派生類中的`proc`陰影。 但是，`MyBase`關鍵字繞過陰影並訪問基類中的隱藏過程。  
  
 ![透過繼承遮蔽示意圖](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 有關通過繼承進行陰影的示例，請參閱[如何：隱藏與變數同名的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)以及如何[：隱藏繼承變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)。  
  
#### <a name="shadowing-and-access-level"></a>陰影和存取層級  
 使用派生類的代碼並不總是可以訪問陰影元素。 例如，它可能聲明`Private`。 在這種情況下，陰影將失敗，編譯器解析對如果沒有陰影時的相同元素的任何引用。 此元素是從陰影類向後派生最少的可訪問元素。 如果隱藏元素是過程，則解析度是最接近的可訪問版本，具有相同的名稱、參數清單和返回類型。  
  
 下面的示例顯示了三個類的繼承層次結構。 每個類定義一個`Sub`過程`display`，每個派生類在其基類`display`中隱藏該過程。  
  
```vb  
Public Class firstClass  
    Public Sub display()  
        MsgBox("This is firstClass")  
    End Sub  
End Class  
Public Class secondClass  
    Inherits firstClass  
    Private Shadows Sub display()  
        MsgBox("This is secondClass")  
    End Sub  
End Class  
Public Class thirdClass  
    Inherits secondClass  
    Public Shadows Sub display()  
        MsgBox("This is thirdClass")  
    End Sub  
End Class  
Module callDisplay  
    Dim first As New firstClass  
    Dim second As New secondClass  
    Dim third As New thirdClass  
    Public Sub callDisplayProcedures()  
        ' The following statement displays "This is firstClass".  
        first.display()  
        ' The following statement displays "This is firstClass".  
        second.display()  
        ' The following statement displays "This is thirdClass".  
        third.display()  
    End Sub  
End Module  
```  
  
 在前面的示例中，派生類`secondClass`陰影`display`帶有一個`Private`過程。 當模組`callDisplay`調用`display``secondClass`時，調用代碼位於外部`secondClass`，因此無法訪問私有`display`過程。 隱藏將失敗，編譯器解析對基類`display`過程的引用。  
  
 但是，進一步的派生`thirdClass`類聲明`display`為`Public`，因此 中`callDisplay`的代碼可以訪問它。  
  
## <a name="shadowing-and-overriding"></a>陰影和覆蓋  
 不要混淆陰影和重寫。 當派生類從基類繼承時，兩者都使用，並且都與另一個類重新定義一個聲明的元素。 但兩者之間存在顯著差異。 有關比較，請參閱[陰影和覆蓋之間的差異](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)。  
  
## <a name="shadowing-and-overloading"></a>陰影和重載  
 如果對派生類中具有多個元素的同一基類元素進行陰影，則陰影元素將成為該元素的重載版本。 如需詳細資訊，請參閱 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)。  
  
## <a name="accessing-a-shadowed-element"></a>訪問隱藏元素  
 當您從派生類訪問元素時，通常通過派生類的當前實例，通過`Me`用 關鍵字限定元素名稱來執行此操作。 如果派生類對基類中的元素造成陰影，則可以通過使用`MyBase`關鍵字限定基類元素來訪問該元素元素。  
  
 有關訪問隱藏元素的示例，請參閱[如何：訪問派生類隱藏的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)。  
  
### <a name="declaration-of-the-object-variable"></a>物件變數的聲明  
 創建物件變數的方式還可以影響派生類是訪問陰影元素還是隱影元素。 下面的示例從派生類創建兩個物件，但一個物件聲明為基類，另一個物件聲明為派生類。  
  
```vb  
Public Class baseCls  
    ' The following statement declares the element that is to be shadowed.  
    Public z As Integer = 100  
End Class  
Public Class dervCls  
    Inherits baseCls  
    ' The following statement declares the shadowing element.  
    Public Shadows z As String = "*"  
End Class  
Public Class useClasses  
    ' The following statement creates the object declared as the base class.  
    Dim basObj As baseCls = New dervCls()  
    ' Note that dervCls widens to its base class baseCls.  
    ' The following statement creates the object declared as the derived class.  
    Dim derObj As dervCls = New dervCls()  
    Public Sub showZ()
    ' The following statement outputs 100 (the shadowed element).  
        MsgBox("Accessed through base class: " & basObj.z)  
    ' The following statement outputs "*" (the shadowing element).  
        MsgBox("Accessed through derived class: " & derObj.z)  
    End Sub  
End Class  
```  
  
 在前面的示例中，變數`basObj`聲明為基類。 向其分配`dervCls`物件構成擴大轉換，因此有效。 但是，基類無法訪問派生類中變數`z`的隱藏版本，因此編譯器解析`basObj.z`為原始基類值。  
  
## <a name="see-also"></a>另請參閱

- [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic 中的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [重寫](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me、My、MyBase 和 MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [繼承基本概念](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
