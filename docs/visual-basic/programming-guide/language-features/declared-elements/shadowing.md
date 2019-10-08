---
title: Visual Basic 中的遮蔽功能
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
ms.openlocfilehash: 30c02cf367c461c3896a01538d03380627de294f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004862"
---
# <a name="shadowing-in-visual-basic"></a>Visual Basic 中的遮蔽功能
當兩個程式設計項目共用相同名稱時，其中一個專案可以隱藏或*遮蔽*另一個。 在這種情況下，陰影元素無法供參考;相反地，當您的程式碼使用元素名稱時，Visual Basic 編譯器會將它解析成遮蔽專案。  
  
## <a name="purpose"></a>用途  
 遮蔽的主要目的是保護類別成員的定義。 基類可能會進行一項變更，以建立一個與您已定義的專案名稱相同的元素。 如果發生這種情況，`Shadows` 修飾詞會強制透過類別的參考解析成您所定義的成員，而不是新的基類元素。  
  
## <a name="types-of-shadowing"></a>遮蔽的類型  
 元素可以用兩種不同的方式來遮蔽另一個專案。 遮蔽專案可以在包含陰影專案之區域的子領域內宣告，在此情況下，遮蔽會*透過範圍*來完成。 或者，衍生類別可以重新定義基類的成員，在這種情況下，會*透過繼承*來完成遮蔽。  
  
### <a name="shadowing-through-scope"></a>透過範圍遮蔽  
 相同模組、類別或結構中的程式設計專案可能具有相同的名稱，但範圍不同。 當以這種方式宣告兩個專案，且程式碼參考其共用的名稱時，具有較窄範圍的元素會遮蔽另一個元素（區塊範圍是最小的）。  
  
 例如，模組可以定義名為 `temp` 的 @no__t 0 變數，而模組內的程式可以宣告名為 `temp` 的本機變數。 從程式內對 `temp` 的參考會存取本機變數，而從程式外部對 `temp` 的參考則會存取 `Public` 變數。 在此情況下，程式變數 `temp` 會將模組變數遮蔽 `temp`。  
  
 下圖顯示兩個名為 `temp` 的變數。 本機變數 `temp` 會在從本身的程式中存取時，將成員變數從 `temp` 遮蔽 `p`。 不過，`MyClass` 關鍵字會略過遮蔽並存取成員變數。  
  
 ![顯示透過範圍遮蔽的圖形。](./media/shadowing/shadow-scope-diagram.gif)
  
 如需透過範圍進行遮蔽的範例，請參閱 [How 至：隱藏名稱與變數 @ no__t-0 相同的變數。  
  
### <a name="shadowing-through-inheritance"></a>透過繼承進行遮蔽  
 如果衍生類別重新定義繼承自基類的程式設計專案，重新定義元素會遮蔽原始專案。 您可以使用任何其他類型來遮蔽任何類型的已宣告元素或多載專案集。 例如，@no__t 0 變數可以遮蔽 @no__t 1 程式。 如果您使用另一個程式來遮蔽程式，則可以使用不同的參數清單和不同的傳回型別。  
  
 下圖顯示基類 `b`，以及繼承自 `b` 的衍生類別 `d`。 基類會定義名為 `proc` 的程式，而衍生的類別會使用相同名稱的另一個程式來遮蔽它。 第一個 `Call` 語句會存取衍生類別中的遮蔽 `proc`。 不過，`MyBase` 關鍵字會略過遮蔽，並存取基類中的陰影程式。  
  
 ![透過繼承遮蔽示意圖](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 如需透過繼承進行遮蔽的範例，請參閱 [How to：隱藏與您的變數 @ no__t-0 相同的變數，並 @no__t 1How 至：隱藏繼承的變數 @ no__t-0。  
  
#### <a name="shadowing-and-access-level"></a>遮蔽和存取層級  
 使用衍生類別時，程式碼不一定可以存取遮蔽元素。 例如，它可能會宣告 `Private`。 在這種情況下，遮蔽會失效，而編譯器會解析任何對相同專案的參考（如果沒有任何遮蔽）。 此元素是可存取的元素，這是從遮蔽類別回溯的最少 derivational 步驟。 如果遮蔽的專案是程式，則解決方式會是具有相同名稱、參數清單和傳回類型的最接近可存取版本。  
  
 下列範例顯示三個類別的繼承階層架構。 每個類別都會定義 `Sub` 程式 `display`，而每個衍生類別都會將 @no__t 2 程式遮蔽在其基類中。  
  
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
  
 在上述範例中，衍生類別 `secondClass` 陰影 `display` 與 @no__t 2 程式。 當模組 `callDisplay` 在 `secondClass` 中呼叫 `display` 時，呼叫端程式碼會超出 `secondClass`，因此無法存取私用的 `display` 程式。 遮蔽會失效，而編譯器會解析基類的參考 `display` 程式。  
  
 不過，進一步衍生的類別 `thirdClass` 會將 `display` 宣告為 `Public`，讓 `callDisplay` 中的程式碼可以存取它。  
  
## <a name="shadowing-and-overriding"></a>遮蔽和覆寫  
 請勿將遮蔽與覆寫混淆。 當衍生類別繼承自基類時，會使用這兩個專案，而且這兩個專案都是以另一個宣告的元素重新定義。 但是兩者之間有顯著的差異。 如需比較，請參閱[遮蔽和覆寫之間的差異](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)。  
  
## <a name="shadowing-and-overloading"></a>遮蔽和多載  
 如果您在衍生類別中遮蔽具有多個專案的相同基類元素，則遮蔽專案會變成該元素的多載版本。 如需詳細資訊，請參閱 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)。  
  
## <a name="accessing-a-shadowed-element"></a>存取陰影元素  
 當您從衍生類別存取專案時，通常會透過使用 `Me` 關鍵字來限定專案名稱，藉此在該衍生類別的目前實例中執行此動作。 如果您的衍生類別會遮蔽基類中的專案，您可以使用 `MyBase` 關鍵字來限定基類專案，藉以存取該元素。  
  
 如需存取遮蔽專案的範例，請參閱 [How to：存取衍生類別 @ no__t-0 所隱藏的變數。  
  
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
  
 在上述範例中，`basObj` 的變數會宣告為基類。 將 @no__t 0 物件指派給它會構成擴輾轉換，因此是有效的。 不過，基類無法存取衍生類別中變數 `z` 的遮蔽版本，因此編譯器會將 `basObj.z` 解析為原始的基類值。  
  
## <a name="see-also"></a>另請參閱

- [對已宣告項目的參考](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic 中的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [擴展和縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me、My、MyBase 和 MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [繼承的基本概念](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
