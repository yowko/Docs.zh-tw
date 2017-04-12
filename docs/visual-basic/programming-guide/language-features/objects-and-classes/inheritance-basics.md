---
title: "繼承基本概念 (Visual Basic) |Microsoft 文件"
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
- derived classes, inheritance
- MyClass keyword, using
- MyBase keyword, using
- Inherits statement, inheritance
- overriding, Overridable keyword
- MustInherit keyword, using
- Overrides keyword, using
- inheritance
- MustInherit classes
- MustOverride keyword, using
- classes [Visual Basic], derived
- NotInheritable keyword, using
- base classes, extending properties and methods
- NotOverridable keyword, using
- base classes, inheritance
- abstract classes, inheritance
- overriding, Overrides keyword
ms.assetid: dfc8deba-f5b3-4d1d-a937-7cb826446fc5
caps.latest.revision: 23
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
ms.openlocfilehash: 58aee9f8c348eb06daec2b8c9e332f3f2775bcb6
ms.lasthandoff: 03/13/2017

---
# <a name="inheritance-basics-visual-basic"></a>繼承基本概念 (Visual Basic)
`Inherits`陳述式用來宣告新的類別，稱為*衍生的類別*、 根據現有的類別，稱為*基底類別*。 在衍生的類別繼承，並擴充屬性、 方法、 事件、 欄位和基底類別中定義的常數。 下節說明一些繼承的規則和修飾詞可用來變更方式類別繼承，或是會繼承︰  
  
-   根據預設，所有類別都都會繼承除非標`NotInheritable`關鍵字。 類別可以繼承自其他類別，在您的專案，或從您的專案參考其他組件中的類別。  
  
-   不同於語言可讓多重繼承，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]允許只有單一繼承類別; 也就是說，衍生的類別可以有只有一個基底類別。 雖然類別中不允許多重繼承，類別可以實作多個介面，可以達到相同目的。  
  
-   若要避免公開受限制的項目與基底類別，衍生類別的存取類型必須相等或更具限制性其基底類別。 例如，`Public`類別無法繼承`Friend`或`Private`類別，和`Friend`類別無法繼承`Private`類別。  
  
## <a name="inheritance-modifiers"></a>繼承修飾詞  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]導入了下列類別層級的陳述式和修飾詞來支援繼承︰  
  
-   `Inherits`陳述式，指定基底類別。  
  
-   `NotInheritable`修飾詞，可讓程式設計人員使用類別當做基底類別。  
  
-   `MustInherit`修飾詞，指定類別，適用於做為基底類別。 執行個體`MustInherit`類別不能直接建立; 他們只能建立為基底的類別執行個體的衍生類別。 (其他程式設計語言，例如 c + + 和 C# 中，使用詞彙*抽象類別*來說明這類的類別。)  
  
## <a name="overriding-properties-and-methods-in-derived-classes"></a>屬性和方法在衍生類別中的覆寫  
 根據預設，在衍生的類別會從其基底類別繼承屬性和方法。 在衍生類別中有不同的行為繼承的屬性或方法有很*覆寫*。 也就是說，您可以定義新的實作方法的衍生類別中。 下列修飾詞是用來控制如何覆寫屬性及方法：  
  
-   `Overridable`— 可讓衍生類別中覆寫類別中的屬性或方法。  
  
-   `Overrides`-覆寫`Overridable`屬性或方法的基底類別中定義。  
  
-   `NotOverridable`可防止遭到覆寫繼承的類別中的屬性或方法。 根據預設，`Public`方法都是`NotOverridable`。  
  
-   `MustOverride`-需要在衍生的類別覆寫屬性或方法。 當`MustOverride`關鍵字時，方法定義都包含只`Sub`， `Function`，或`Property`陳述式。 允許其他陳述式，以及特別是沒有任何`End Sub`或`End Function`陳述式。 `MustOverride`方法必須宣告中`MustInherit`類別。  
  
 假設您想要定義類別處理薪資。 您可以定義泛型`Payroll`類別，其中包含`RunPayroll`計算薪資典型的一週的方法。 您接著可以使用`Payroll`更特殊的基底類別為`BonusPayroll`分配員工加分時可用的類別。  
  
 `BonusPayroll`類別可以繼承，並覆寫，`PayEmployee`定義基底方法`Payroll`類別。  
  
 下列範例會定義基底類別，`Payroll,`和衍生的類別， `BonusPayroll`，因而覆寫繼承的方法， `PayEmployee`。 程序， `RunPayroll`、 建立和傳送`Payroll`物件和`BonusPayroll`函式物件`Pay`，執行`PayEmployee`兩個物件的方法。  
  
 [!code-vb[VbVbalrOOP #&28;](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_1.vb)]  
  
## <a name="the-mybase-keyword"></a>MyBase 關鍵字  
 `MyBase`關鍵字的行為就像指的是類別的目前執行個體的基底類別的物件變數。 `MyBase`經常用來存取基底類別成員會覆寫或遮蔽衍生類別中。 特別是，`MyBase.New`用來明確地從衍生的類別建構函式呼叫基底類別建構函式。  
  
 例如，假設您正在設計衍生的類別中覆寫繼承自基底類別的方法。 覆寫的方法可以呼叫基底類別中的方法，並修改的傳回值，如下列程式碼片段所示︰  
  
 [!code-vb[VbVbalrOOP #&109;](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_2.vb)]  
  
 下列清單說明限制使用`MyBase`:  
  
-   `MyBase`是指直接基底類別和繼承的成員。 它不能用來存取`Private`類別中的成員。  
  
-   `MyBase`是關鍵字，而不是真正的物件。 `MyBase`無法指派給變數，傳遞至程序，或用於`Is`比較。  
  
-   此方法，`MyBase`限定並沒有定義中直接基底類別; 它可能會改為在間接繼承的基底類別中定義。 為了讓所限定的參考`MyBase`才能正確編譯，某些基底類別必須包含符合的名稱和類型的參數，會出現在呼叫方法。  
  
-   您不能使用`MyBase`呼叫`MustOverride`基底類別方法。  
  
-   `MyBase`不能用來限定本身。 因此，下列程式碼不正確︰  
  
     `MyBase.MyBase.BtnOK_Click()`  
  
-   `MyBase`不能在模組中。  
  
-   `MyBase`無法用來存取基底類別成員標記為`Friend`基底類別位於不同的組件中。  
  
 如需詳細資訊和另一個範例，請參閱[How to︰ 存取衍生類別所變數隱藏](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)。  
  
## <a name="the-myclass-keyword"></a>MyClass 關鍵字  
 `MyClass`關鍵字的行為就像適用於目前的執行個體的類別，為原始實作的物件變數。 `MyClass`類似於`Me`，但每個方法和屬性上呼叫`MyClass`一樣的方法或屬性會被視為[NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md)。 因此，不會影響方法或屬性藉由衍生類別中覆寫。  
  
-   `MyClass`是關鍵字，而不是真正的物件。 `MyClass`無法指派給變數，傳遞至程序，或用於`Is`比較。  
  
-   `MyClass`是指包含類別和繼承的成員。  
  
-   `MyClass`可用來當做限定詞`Shared`成員。  
  
-   `MyClass`不在內部使用`Shared`方法，但可以在執行個體方法內用來存取共用的成員的類別。  
  
-   `MyClass`不能在標準模組。  
  
-   `MyClass`可用來限定基底類別中定義，而該類別中所提供的方法沒有實作的方法。 這類的參考具有相同的意義`MyBase.`*方法*。  
  
 下列範例會比較`Me`和`MyClass`。  
  
```  
Class baseClass  
    Public Overridable Sub testMethod()  
        MsgBox("Base class string")  
    End Sub  
    Public Sub useMe()  
        ' The following call uses the calling class's method, even if   
        ' that method is an override.  
        Me.testMethod()  
    End Sub  
    Public Sub useMyClass()  
        ' The following call uses this instance's method and not any  
        ' override.  
        MyClass.testMethod()  
    End Sub  
End Class  
Class derivedClass : Inherits baseClass  
    Public Overrides Sub testMethod()  
        MsgBox("Derived class string")  
    End Sub  
End Class  
Class testClasses  
    Sub startHere()  
        Dim testObj As derivedClass = New derivedClass()  
        ' The following call displays "Derived class string".  
        testObj.useMe()  
        ' The following call displays "Base class string".  
        testObj.useMyClass()  
    End Sub  
End Class  
```  
  
 即使`derivedClass`覆寫`testMethod`、`MyClass`關鍵字`useMyClass`nullifies 的覆寫和編譯器解析效果的基底類別版本來呼叫`testMethod`。  
  
## <a name="see-also"></a>另請參閱  
 [Inherits 陳述式](../../../../visual-basic/language-reference/statements/inherits-statement.md)   
 [Me、My、MyBase 和 MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
