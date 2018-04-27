---
title: 繼承基本概念 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- derived classes [Visual Basic], inheritance
- MyClass keyword [Visual Basic], using
- MyBase keyword [Visual Basic], using
- Inherits statement [Visual Basic], inheritance
- overriding, Overridable keyword
- MustInherit keyword [Visual Basic], using
- Overrides keyword [Visual Basic], using
- inheritance
- MustInherit classes [Visual Basic]
- MustOverride keyword [Visual Basic], using
- classes [Visual Basic], derived
- NotInheritable keyword [Visual Basic], using
- base classes [Visual Basic], extending properties and methods [Visual Basic]
- NotOverridable keyword [Visual Basic], using
- base classes [Visual Basic], inheritance
- abstract classes [Visual Basic], inheritance
- overriding, Overrides keyword
ms.assetid: dfc8deba-f5b3-4d1d-a937-7cb826446fc5
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e37dabefcbda48144af910298dd4d82c13b7042
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="inheritance-basics-visual-basic"></a>繼承基本概念 (Visual Basic)
`Inherits`陳述式用來宣告新類別，稱為*衍生的類別*、 根據現有的類別，又稱為*基底類別*。 在衍生的類別繼承，並擴充屬性、 方法、 事件、 欄位和基底類別中定義的常數。 下節將說明一些繼承規則，以及變更的方式類別，您可以使用的修飾詞繼承或繼承：  
  
-   根據預設，除非標記為可繼承的所有類別都都會`NotInheritable`關鍵字。 類別可以繼承自其他類別，在您的專案，或從您的專案參考其他組件中的類別。  
  
-   不同於允許多個繼承的語言，Visual Basic，請允許類別; 中的只能使用單一繼承也就是在衍生的類別可以有只有一個基底類別。 雖然在類別中不允許多重繼承，類別可以實作多個介面，可以達到相同的端點。  
  
-   若要避免公開受限制的項目中的基底類別，衍生類別的存取類型必須是等於或更具限制性其基底類別。 例如，`Public`類別不可繼承`Friend`或`Private`類別，和`Friend`類別不可繼承`Private`類別。  
  
## <a name="inheritance-modifiers"></a>繼承修飾詞  
 下列類別層級的陳述式和修飾詞，以支援繼承，導入了 Visual Basic:  
  
-   `Inherits` 陳述式，指定基底類別。  
  
-   `NotInheritable` 修飾詞，可讓程式設計人員使用類別的基底類別。  
  
-   `MustInherit` 修飾詞，指定此類別僅供做為基底類別。 執行個體`MustInherit`類別不能直接建立; 它們只能建立為基底的類別執行個體的衍生類別。 (其他程式設計語言，例如 c + + 和 C# 中，使用詞彙*抽象類別*來描述這種類別。)  
  
## <a name="overriding-properties-and-methods-in-derived-classes"></a>屬性和方法在衍生類別中的覆寫  
 根據預設，在衍生的類別會從其基底類別繼承屬性和方法。 在衍生類別中有不同的行為的繼承的屬性或方法具有可*覆寫*。 也就是說，您可以定義新的實作方法的衍生類別中。 下列修飾詞是用來控制如何覆寫屬性及方法：  
  
-   `Overridable` — 可讓衍生類別中覆寫類別中的屬性或方法。  
  
-   `Overrides` -覆寫`Overridable`屬性或方法的基底類別中定義。  
  
-   `NotOverridable` 可防止遭到覆寫繼承的類別中的屬性或方法。 根據預設，`Public`方法`NotOverridable`。  
  
-   `MustOverride` — 需要在衍生的類別覆寫屬性或方法。 當`MustOverride`使用關鍵字、 方法定義組成只`Sub`， `Function`，或`Property`陳述式。 不允許任何其他陳述式，以及特別是沒有任何`End Sub`或`End Function`陳述式。 `MustOverride` 方法必須宣告在`MustInherit`類別。  
  
 假設您想要定義類別處理薪資。 您可以定義為泛型`Payroll`類別，其中包含`RunPayroll`薪資計算一般一週的方法。 您接著可以使用`Payroll`更具特製化的基底類別為`BonusPayroll`類別，將員工加分時無法使用。  
  
 `BonusPayroll`類別可以繼承，並覆寫，`PayEmployee`方法定義於基底`Payroll`類別。  
  
 下列範例會定義基底類別，`Payroll,`和衍生的類別， `BonusPayroll`，因而覆寫繼承的方法， `PayEmployee`。 程序，`RunPayroll`建立，然後將傳遞`Payroll`物件和`BonusPayroll`函式物件`Pay`，執行`PayEmployee`這兩個物件的方法。  
  
 [!code-vb[VbVbalrOOP#28](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_1.vb)]  
  
## <a name="the-mybase-keyword"></a>MyBase 關鍵字  
 `MyBase`關鍵字的行為就像指的是類別的目前執行個體的基底類別的物件變數。 `MyBase` 經常用來存取基底類別成員會覆寫或遮蔽衍生類別中。 特別是，`MyBase.New`用來明確地從衍生的類別建構函式呼叫的基底類別建構函式。  
  
 例如，假設您要設計衍生的類別中覆寫繼承自基底類別的方法。 覆寫的方法可以呼叫基底類別中的方法，並修改的傳回值，如下列程式碼片段所示：  
  
 [!code-vb[VbVbalrOOP#109](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_2.vb)]  
  
 下列清單描述限制使用`MyBase`:  
  
-   `MyBase` 是指直接基底類別和繼承的成員。 它不能用來存取`Private`類別中的成員。  
  
-   `MyBase` 是關鍵字，而不是真正的物件。 `MyBase` 無法指派給變數，傳遞至程序，或用於`Is`比較。  
  
-   方法的`MyBase`限定不必定義在直接基底類別; 它可能會改為在間接繼承的基底類別中定義。 為了讓所限定的參考`MyBase`才能正確編譯時，某些基底類別必須包含比對的名稱和顯示呼叫中的參數類型的方法。  
  
-   您無法使用`MyBase`呼叫`MustOverride`基底類別方法。  
  
-   `MyBase` 不能用來限定本身。 因此，下列程式碼不是有效的：  
  
     `MyBase.MyBase.BtnOK_Click()`  
  
-   `MyBase` 不能在模組中。  
  
-   `MyBase` 無法用來存取基底類別成員標記為`Friend`如果基底類別在不同的組件。  
  
 如需詳細資訊，以及另一個範例，請參閱[如何： 存取衍生類別所變數隱藏](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)。  
  
## <a name="the-myclass-keyword"></a>MyClass 關鍵字  
 `MyClass`關鍵字的行為就像指的是以原始實作類別的目前執行個體的物件變數。 `MyClass` 類似於`Me`，但每個方法和屬性上呼叫`MyClass`好像方法或屬性會被視為[NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md)。 因此，此方法或屬性不會影響在衍生類別中覆寫。  
  
-   `MyClass` 是關鍵字，而不是真正的物件。 `MyClass` 無法指派給變數，傳遞至程序，或用於`Is`比較。  
  
-   `MyClass` 是指包含類別和繼承的成員。  
  
-   `MyClass` 可用來當作限定詞`Shared`成員。  
  
-   `MyClass` 不在內部使用`Shared`方法，但是可以在執行個體方法內用來存取共用的成員的類別。  
  
-   `MyClass` 不能在標準模組。  
  
-   `MyClass` 可用來限定，它定義於基底類別，而該類別中提供的方法沒有實作的方法。 這類的參考具有相同的意義`MyBase.`*方法*。  
  
 下列範例會比較`Me`和`MyClass`。  
  
```vb
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
  
 即使`derivedClass`會覆寫`testMethod`、`MyClass`關鍵字`useMyClass`nullifies 覆寫時，和編譯器解析的效果，呼叫的基底類別版本`testMethod`。  
  
## <a name="see-also"></a>另請參閱  
 [Inherits 陳述式](../../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [Me、My、MyBase 和 MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
