---
title: "在 Visual Basic 中，以遮蔽 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- inheritance, shadowing
- overriding, and shadowing
- shadowing
- duplicate names
- shadowing, by inheritance
- declared elements, referencing
- shadowing, by scope
- declared elements, hiding
- naming conflicts, shadowing
- declared elements, shadowing
- shadowing, and overriding
- scope, shadowing
- Shadows keyword, about
- objects [Visual Basic], names
- names, shadowing
ms.assetid: 54bb4c25-12c4-4181-b4a0-93546053964e
caps.latest.revision: 24
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 5f4053de05f0a7a42fccdade1714e08f8eb172e6
ms.lasthandoff: 03/13/2017

---
# <a name="shadowing-in-visual-basic"></a>Visual Basic 中的遮蔽功能
當兩個程式設計項目共用相同的名稱時，其中可以隱藏它，或*陰影*，另一個。 在這種情況下，遮蔽的項目不是可供參考。相反地，當您的程式碼使用的項目名稱，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器解析遮蔽的項目。  
  
## <a name="purpose"></a>用途  
 遮蔽的主要目的是要保護的類別成員定義。 基底類別可能進行的變更，建立名稱與您已定義的名稱相同的項目。 如果發生這種情況，`Shadows`修飾詞強制參考到您的類別成員解析您定義的而不是新的基底類別項目。  
  
## <a name="types-of-shadowing"></a>遮蔽的型別  
 項目可以在兩種不同方式遮蔽另一個項目。 遮蔽的項目可以在區域包含遮蔽的項目，並須遮蔽的情況下的子區域內宣告*範圍*。 在衍生類別可以重新定義的基底類別，是大小寫，以遮蔽成員或者*透過繼承*。  
  
### <a name="shadowing-through-scope"></a>透過範圍遮蔽  
 它有可能的程式設計項目在相同的模組、 類別或結構有相同名稱但不同的範圍。 當以這種方式宣告兩個項目，程式碼會參考它們共用的名稱具有較小範圍的項目會遮蔽其他項目 （區塊範圍最小）。  
  
 例如，可以定義模組`Public`名為變數`temp`，同時在模組中的程序可以宣告區域變數也稱為`temp`。 參考`temp`中的程序存取的本機變數的參考時`temp`從外部程序存取`Public`變數。 在此情況下，程序變數`temp`遮蔽模組變數`temp`。  
  
 下圖顯示兩個變數，名為`temp`。 本機變數`temp`遮蔽成員變數`temp`時從自己的程序內存取`p`。 不過，`MyClass`關鍵字略過遮蔽和存取的成員變數。  
  
 ![透過範圍遮蔽示意圖](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowscope.gif "ShadowScope")  
透過範圍遮蔽  
  
 如需透過範圍遮蔽的範例，請參閱[如何︰ 隱藏與您的變數名稱的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)。  
  
### <a name="shadowing-through-inheritance"></a>透過繼承遮蔽  
 如果衍生的類別重新定義繼承自基底類別的程式設計項目，重新定義的項目會遮蔽原始項目。 您可以使用任何其他類型遮蔽任何類型的宣告的項目或集合的多載的項目。 例如，`Integer`變數都可以遮蔽`Function`程序。 如果您遮蔽另一個程序的程序，您可以使用不同的參數清單和不同的傳回型別。  
  
 下圖顯示基底類別`b`和衍生的類別`d`繼承自`b`。 基底類別會定義名為程序`proc`，和在衍生的類別遮蔽它具有相同名稱的另一個程序。 第一個`Call`陳述式會存取遮蔽`proc`衍生類別中。 不過，`MyBase`關鍵字略過遮蔽和存取的基底類別中的遮蔽程序。  
  
 ![透過繼承遮蔽示意圖](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowinherit.gif "ShadowInherit")  
透過繼承遮蔽  
  
 如需透過繼承遮蔽的範例，請參閱[如何︰ 隱藏與您的變數名稱的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)和[如何︰ 隱藏繼承的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)。  
  
#### <a name="shadowing-and-access-level"></a>遮蔽和存取層級  
 遮蔽的項目不一定可從使用衍生的類別的程式碼存取。 例如，可能會宣告`Private`。 在這種情況下，若要遮蔽會失敗，編譯器會解析任何參考的相同項目，就會如果有任何遮蔽。 此元素是最少衍生向後步驟從遮蔽類別可存取的項目。 如果遮蔽的項目為程序，解決方式是最接近的可存取版本具有相同名稱，也就是參數清單和傳回型別。  
  
 下列範例顯示三個類別的繼承階層架構。 每個類別定義`Sub`程序`display`，以及每個衍生類別陰影`display`其基底類別中的程序。  
  
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
  
 在上述範例中，衍生類別中`secondClass`陰影`display`與`Private`程序。 當模組`callDisplay`呼叫`display`中`secondClass`，呼叫程式碼超出`secondClass`，因此無法存取私用`display`程序。 遮蔽會失敗，，編譯器會解析基底類別的參考`display`程序。  
  
 不過，進一步衍生類別`thirdClass`宣告`display`為`Public`，因此中的程式碼`callDisplay`可以存取它。  
  
## <a name="shadowing-and-overriding"></a>遮蔽和覆寫  
 請勿混淆遮蔽和覆寫。 在衍生的類別繼承自基底類別，並同時重新定義與另一個宣告的項目時，會使用這兩項目。 但是有兩個明顯的差異。 如需比較，請參閱[差異之間遮蔽和覆](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)。  
  
## <a name="shadowing-and-overloading"></a>遮蔽和多載化  
 如果您在衍生類別中遮蔽具有多個項目相同的基底類別項目，遮蔽的項目會成為該元素的多載的版本。 如需詳細資訊，請參閱[程序多載](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)。  
  
## <a name="accessing-a-shadowed-element"></a>存取遮蔽的項目  
 當您從衍生類別中存取項目時，您通常要透過目前的執行個體的衍生類別，來限定項目名稱與`Me`關鍵字。 如果您的衍生的類別遮蔽基底類別中的項目，您可以存取的基底類別的項目來限定它與`MyBase`關鍵字。  
  
 如需存取遮蔽的項目，請參閱[如何︰ 存取衍生類別所變數隱藏](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)。  
  
### <a name="declaration-of-the-object-variable"></a>物件變數宣告  
 物件變數的建立方式，也會影響在衍生的類別存取遮蔽的項目或遮蔽的項目。 下列範例會從衍生類別中，建立兩個物件，但一個物件宣告為基底類別，而另一個則做為衍生的類別。  
  
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
  
 在上述範例中，變數`basObj`宣告為基底類別。 指派`dervCls`物件傳送給它構成擴展的轉換，因此是有效。 不過，基底類別無法存取變數的遮蔽版本`z`在衍生類別中，因此編譯器會解析`basObj.z`原始基底類別值。  
  
## <a name="see-also"></a>另請參閱  
 [宣告項目參考](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [在 Visual Basic 中的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)   
 [擴展和縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [陰影](../../../../visual-basic/language-reference/modifiers/shadows.md)   
 [覆寫](../../../../visual-basic/language-reference/modifiers/overrides.md)   
 [Me、 My、 MyBase 和 MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)   
 [繼承的基本概念](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
