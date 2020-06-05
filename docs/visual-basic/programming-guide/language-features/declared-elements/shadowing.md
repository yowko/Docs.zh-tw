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
ms.openlocfilehash: 7d76e2e7398c2f954ff4274f77ffa350efbd3617
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410743"
---
# <a name="shadowing-in-visual-basic"></a>Visual Basic 中的遮蔽功能
當兩個程式設計項目共用相同名稱時，其中一個專案可以隱藏或*遮蔽*另一個。 在這種情況下，陰影元素無法供參考;相反地，當您的程式碼使用元素名稱時，Visual Basic 編譯器會將它解析成遮蔽專案。  
  
## <a name="purpose"></a>目的  
 遮蔽的主要目的是保護類別成員的定義。 基類可能會進行一項變更，以建立一個與您已定義的專案名稱相同的元素。 如果發生這種情況， `Shadows` 修飾詞會強制透過類別的參考解析成您所定義的成員，而不是新的基類元素。  
  
## <a name="types-of-shadowing"></a>遮蔽的類型  
 元素可以用兩種不同的方式來遮蔽另一個專案。 遮蔽專案可以在包含陰影專案之區域的子領域內宣告，在此情況下，遮蔽會*透過範圍*來完成。 或者，衍生類別可以重新定義基類的成員，在這種情況下，會*透過繼承*來完成遮蔽。  
  
### <a name="shadowing-through-scope"></a>透過範圍遮蔽  
 相同模組、類別或結構中的程式設計專案可能具有相同的名稱，但範圍不同。 當以這種方式宣告兩個專案，且程式碼參考其共用的名稱時，具有較窄範圍的元素會遮蔽另一個元素（區塊範圍是最小的）。  
  
 例如，模組可以定義 `Public` 名為的變數 `temp` ，而模組內的程式可以宣告一個也名為的本機變數 `temp` 。 從程式內對的參考會 `temp` 存取區域變數，而從程式外部的參考 `temp` 則會存取 `Public` 變數。 在此情況下，程式變數會 `temp` 遮蔽模組變數 `temp` 。  
  
 下圖顯示兩個名為的變數 `temp` 。 本機變數會在 `temp` `temp` 從其本身的程式中存取時，遮蔽成員變數 `p` 。 不過， `MyClass` 關鍵字會略過遮蔽並存取成員變數。  
  
 ![顯示透過範圍遮蔽的圖形。](./media/shadowing/shadow-scope-diagram.gif)
  
 如需透過範圍進行遮蔽的範例，請參閱[如何：隱藏與您的變數名稱相同的變數](how-to-hide-a-variable-with-the-same-name-as-your-variable.md)。  
  
### <a name="shadowing-through-inheritance"></a>透過繼承進行遮蔽  
 如果衍生類別重新定義繼承自基類的程式設計專案，重新定義元素會遮蔽原始專案。 您可以使用任何其他類型來遮蔽任何類型的已宣告元素或多載專案集。 例如， `Integer` 變數可以遮蔽程式 `Function` 。 如果您使用另一個程式來遮蔽程式，則可以使用不同的參數清單和不同的傳回型別。  
  
 下圖顯示基類 `b` ，以及繼承自的衍生類別 `d` `b` 。 基類會定義名為的程式 `proc` ，而衍生的類別會使用相同名稱的另一個程式來遮蔽該程式。 第一個 `Call` 語句會存取 `proc` 衍生類別中的陰影。 不過， `MyBase` 關鍵字會略過遮蔽，並存取基類中的陰影程式。  
  
 ![透過繼承遮蔽示意圖](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 如需透過繼承進行遮蔽的範例，請參閱[如何：隱藏與您的變數名稱相同的變數](how-to-hide-a-variable-with-the-same-name-as-your-variable.md)和[如何：隱藏繼承的變數](how-to-hide-an-inherited-variable.md)。  
  
#### <a name="shadowing-and-access-level"></a>遮蔽和存取層級  
 使用衍生類別時，程式碼不一定可以存取遮蔽元素。 例如，它可能會宣告 `Private` 。 在這種情況下，遮蔽會失效，而編譯器會解析任何對相同專案的參考（如果沒有任何遮蔽）。 此元素是可存取的元素，這是從遮蔽類別回溯的最少 derivational 步驟。 如果遮蔽的專案是程式，則解決方式會是具有相同名稱、參數清單和傳回類型的最接近可存取版本。  
  
 下列範例顯示三個類別的繼承階層架構。 每個類別都會定義一個程式 `Sub` `display` ，而每個衍生類別都會 `display` 在其基類中遮蔽程式。  
  
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
  
 在上述範例中，衍生類別會加上程式的 `secondClass` 陰影 `display` `Private` 。 當模組 `callDisplay` 呼叫 `display` 中 `secondClass` 的時，呼叫程式碼會在外， `secondClass` 因此無法存取私 `display` 用程式。 遮蔽會失效，而編譯器會解析基類程式的參考 `display` 。  
  
 不過，進一步的衍生類別 `thirdClass` 會將宣告 `display` 為 `Public` ，因此中的程式碼 `callDisplay` 可以存取它。  
  
## <a name="shadowing-and-overriding"></a>遮蔽和覆寫  
 請勿將遮蔽與覆寫混淆。 當衍生類別繼承自基類時，會使用這兩個專案，而且這兩個專案都是以另一個宣告的元素重新定義。 但是兩者之間有顯著的差異。 如需比較，請參閱[遮蔽和覆寫之間的差異](differences-between-shadowing-and-overriding.md)。  
  
## <a name="shadowing-and-overloading"></a>遮蔽和多載  
 如果您在衍生類別中遮蔽具有多個專案的相同基類元素，則遮蔽專案會變成該元素的多載版本。 如需詳細資訊，請參閱 [Procedure Overloading](../procedures/procedure-overloading.md)。  
  
## <a name="accessing-a-shadowed-element"></a>存取陰影元素  
 當您從衍生類別存取專案時，通常會透過使用關鍵字來限定專案名稱，藉此在該衍生類別的目前實例中執行此動作 `Me` 。 如果您的衍生類別會遮蔽基類中的專案，您可以使用關鍵字來限定基類專案，藉以存取該元素 `MyBase` 。  
  
 如需存取陰影元素的範例，請參閱[如何：存取衍生類別所隱藏的變數](how-to-access-a-variable-hidden-by-a-derived-class.md)。  
  
### <a name="declaration-of-the-object-variable"></a>物件變數的宣告  
 您建立物件變數的方式也會影響衍生類別是要存取遮蔽專案還是陰影元素。 下列範例會從衍生類別建立兩個物件，但是一個物件宣告為基類，另一個則做為衍生類別。  
  
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
  
 在上述範例中，變數 `basObj` 會宣告為基類。 指派 `dervCls` 物件給它會構成擴輾轉換，因此是有效的。 不過，基類無法存取衍生類別中變數的遮蔽版本 `z` ，因此編譯器會解析 `basObj.z` 為原始的基類值。  
  
## <a name="see-also"></a>另請參閱

- [References to Declared Elements](references-to-declared-elements.md)
- [Visual Basic 中的範圍](scope.md)
- [Widening and Narrowing Conversions](../data-types/widening-and-narrowing-conversions.md)
- [Shadows](../../../language-reference/modifiers/shadows.md)
- [覆寫](../../../language-reference/modifiers/overrides.md)
- [Me、My、MyBase 及 MyClass](../../program-structure/me-my-mybase-and-myclass.md)
- [繼承基本概念](../objects-and-classes/inheritance-basics.md)
