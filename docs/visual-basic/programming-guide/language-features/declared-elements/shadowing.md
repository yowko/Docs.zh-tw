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
ms.openlocfilehash: fde6259b67a8d963ed8c30b87c94029fb2658664
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656067"
---
# <a name="shadowing-in-visual-basic"></a>Visual Basic 中的遮蔽功能
當兩個的程式設計項目共用相同的名稱時，可以隱藏其中一個，或*陰影*，另一個。 在這種情況下，加上陰影的項目不是可參考。相反地，當您的程式碼使用的項目名稱時，Visual Basic 編譯器解析遮蔽的項目。  
  
## <a name="purpose"></a>用途  
 遮蔽的主要目的是要保護的定義類別成員。 基底類別可能進行的變更，建立名稱與您已定義的名稱相同的項目。 如果發生這種情況，`Shadows`修飾詞強制參考您要解析為成員的類別透過您定義的而不是新的基底類別項目。  
  
## <a name="types-of-shadowing"></a>遮蔽的型別  
 項目可遮蔽另一個項目以兩個不同的方式。 遮蔽的項目可以包含陰影的項目，遮蔽的案例來達成區域的子區域內宣告*透過範圍*。 衍生的類別可以重新定義基底類別，是案例遮蔽的成員或者*透過繼承*。  
  
### <a name="shadowing-through-scope"></a>透過範圍遮蔽  
 它是讓程式設計中相同的模組、 類別或結構有相同名稱但不同範圍的項目。 當以這種方式宣告兩個項目，程式碼參照到它們共用的名稱具有較小範圍的項目會遮蔽另一個項目 （區塊範圍最小）。  
  
 例如，可以定義模組`Public`名為變數`temp`，而且在模組中的程序可以宣告本機變數，也稱為`temp`。 若要參考`temp`從程序存取的本機變數的參考時`temp`從外部程序存取`Public`變數。 在此情況下，程序變數`temp`遮蔽模組變數`temp`。  
  
 下圖顯示兩個變數，名為`temp`。 本機變數`temp`遮蔽的成員變數`temp`時從自己的程序內存取`p`。 不過，`MyClass`關鍵字略過遮蔽和存取的成員變數。  
  
 ![透過範圍遮蔽示意圖](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowscope.gif "ShadowScope")  
透過範圍遮蔽  
  
 如需透過範圍遮蔽的範例，請參閱[如何： 隱藏與您變數同名的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)。  
  
### <a name="shadowing-through-inheritance"></a>透過繼承遮蔽  
 如果在衍生的類別重新定義繼承自基底類別的程式設計項目，則重新定義的項目會遮蔽原始項目。 您可以使用任何其他類型遮蔽任何一種宣告的項目或集合的多載的項目。 例如，`Integer`變數可以遮蔽`Function`程序。 如果您要遮蔽另一個程序的程序，您可以使用不同的參數清單和傳回類型不同。  
  
 下圖顯示基底類別`b`和衍生的類別`d`繼承自`b`。 基底類別會定義名為程序`proc`，並在衍生的類別可遮蔽它具有相同名稱的另一個程序。 第一個`Call`陳述式可讓您存取遮蔽`proc`衍生類別中。 不過，`MyBase`關鍵字略過遮蔽和存取基底類別中加上陰影的程序。  
  
 ![透過繼承遮蔽示意圖](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowinherit.gif "ShadowInherit")  
透過繼承遮蔽  
  
 如需透過繼承遮蔽的範例，請參閱[如何： 隱藏與您變數同名的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)和[如何： 隱藏繼承的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)。  
  
#### <a name="shadowing-and-access-level"></a>遮蔽和存取層級  
 遮蔽的項目不一定可從使用衍生的類別的程式碼存取。 例如，可能會宣告`Private`。 在這種情況下，若要遮蔽會失敗，則編譯器會解析就會相同項目的任何參考如果有任何遮蔽。 此元素為可以存取最少衍生步驟向後從遮蔽類別的項目。 如果加上陰影的項目為程序，解析為最接近的可存取版本具有相同名稱，也就是參數清單和傳回型別。  
  
 下列範例示範三個類別的繼承階層架構。 每個類別會定義`Sub`程序`display`，以及每個衍生類別陰影`display`其基底類別中的程序。  
  
```  
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
  
 在上述範例中，在衍生類別中`secondClass`陰影`display`與`Private`程序。 當模組`callDisplay`呼叫`display`中`secondClass`，呼叫程式碼超出`secondClass`因此無法存取私用`display`程序。 遮蔽會失敗，並編譯器解析參考的基底類別`display`程序。  
  
 不過，進一步衍生類別`thirdClass`宣告`display`為`Public`，因此中的程式碼`callDisplay`可以存取它。  
  
## <a name="shadowing-and-overriding"></a>遮蔽和覆寫  
 請勿混淆遮蔽和覆寫。 在衍生的類別繼承自基底類別，並同時重新定義與另一個宣告的項目時，會使用這兩項目。 但有兩個重大差異。 如需比較，請參閱[差異之間遮蔽和覆](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)。  
  
## <a name="shadowing-and-overloading"></a>遮蔽和多載化  
 如果您在衍生類別中遮蔽具有多個項目相同的基底類別項目，遮蔽的項目會變成該元素的多載的版本。 如需詳細資訊，請參閱[程序多載](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)。  
  
## <a name="accessing-a-shadowed-element"></a>存取遮蔽的項目  
 當您從衍生類別中存取項目時，您通常要透過目前的執行個體的衍生類別，來限定項目名稱與`Me`關鍵字。 如果您在衍生的類別會遮蔽基底類別中的項目，您可以存取的基底類別項目來限定它與`MyBase`關鍵字。  
  
 如需的存取遮蔽的項目範例，請參閱[如何： 存取衍生類別所變數隱藏](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)。  
  
### <a name="declaration-of-the-object-variable"></a>物件變數的宣告  
 在衍生的類別存取遮蔽項目或遮蔽的項目是否也會影響您建立的物件變數的方式。 下列範例會建立兩個物件從衍生類別，但一個物件宣告為基底類別和另一個則為衍生的類別。  
  
```  
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
  
 在上述範例中，變數`basObj`宣告的基底類別。 指派`dervCls`物件傳送給它構成擴展轉換，因此無效。 不過，基底類別無法存取遮蔽版本的變數`z`在衍生類別中，因此編譯器會解析`basObj.z`原始基底類別值。  
  
## <a name="see-also"></a>另請參閱  
 [對已宣告項目的參考](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [在 Visual Basic 中的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [擴展和縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Me、My、MyBase 和 MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [繼承的基本概念](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
