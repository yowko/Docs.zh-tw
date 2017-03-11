---
title: "Inheritance Basics (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "derived classes, inheritance"
  - "MyClass keyword, using"
  - "MyBase keyword, using"
  - "Inherits statement, inheritance"
  - "overriding, Overridable keyword"
  - "MustInherit keyword, using"
  - "Overrides keyword, using"
  - "inheritance"
  - "MustInherit classes"
  - "MustOverride keyword, using"
  - "classes [Visual Basic], derived"
  - "NotInheritable keyword, using"
  - "base classes, extending properties and methods"
  - "NotOverridable keyword, using"
  - "base classes, inheritance"
  - "abstract classes, inheritance"
  - "overriding, Overrides keyword"
ms.assetid: dfc8deba-f5b3-4d1d-a937-7cb826446fc5
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 23
---
# Inheritance Basics (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

`Inherits` 陳述式是以「*基底類別*」\(Base Class\) 的現有類別為基礎，宣告稱為「*衍生類別*」\(Derived Class\) 的新類別。  衍生類別可繼承並擴充在基底類別中定義的屬性、方法、事件、欄位及常數。  下列章節說明部分的繼承規則，以及您可用來變更類別繼承或被繼承方式的修飾詞：  
  
-   根據預設，除非以 `NotInheritable` 關鍵字標記該類別，否則所有類别都是可繼承的。  類別可繼承自您專案中的其他類別或繼承自專案參考的其他組件中的類別。  
  
-   不同於允許多重繼承的語言，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 只允許類別中的單一繼承，也就是說，衍生類別只能有一個基底類別。  雖然類別中不允許多重繼承，但類別可實作多重介面，一樣可以達到相同目的。  
  
-   為了防止顯露基底類別的設限項目，衍生類別的存取類型必須等於或高於其基底類別的限制。  例如 `Public` 類別不能繼承 `Friend` 或 `Private` 類別，而 `Friend` 類別不能繼承 `Private` 類別。  
  
## 繼承修飾詞  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會加入下列類別層級陳述式及修飾詞來支援繼承：  
  
-   `Inherits` 陳述式 \- 指定基底類別。  
  
-   `NotInheritable` 修飾詞 \- 防止程式設計人員使用類別做為基底類別  
  
-   `MustInherit` 修飾詞 \- 指定預定只做為基底類別使用的類別。  無法直接建立 `MustInherit` 類別的執行個體；只能將這些類別建立成衍生類別的基底類別執行個體   \(如 C\+\+ 和 C\# 的其他程式設計語言使用「*抽象類別*」\(Abstract Class\) 一詞來描述這種類別\)。  
  
## 覆寫衍生類別中的屬性及方法  
 根據預設，衍生類別會從其基底類別繼承屬性和方法。  如果繼承的屬性或方法必須在衍生的類別中具有不同的行為，即可予以「*覆寫*」\(Overridden\)。  也就是說，您可以在衍生的類別中定義方法的新實作。  下列修飾詞是用來控制如何覆寫屬性及方法：  
  
-   `Overridable` \- 允許在衍生類別中覆寫類別中的屬性或方法。  
  
-   `Overrides` \- 覆寫在基底類別中定義的 `Overridable` 屬性或方法。  
  
-   `NotOverridable` \- 防止屬性或方法在繼承的類別中被覆寫。  根據預設，`Public` 方法是 `NotOverridable`。  
  
-   `MustOverride` \- 要求衍生類別覆寫屬性或方法。  當使用 `MustOverride` 關鍵字時，方法定義就只能包含 `Sub`、`Function` 或 `Property` 陳述式。  不允許其他陳述式，特別是不允許 `End Sub` 或 `End Function` 陳述式。  `MustOverride` 方法必須在 `MustInherit` 類別中宣告。  
  
 假定您要定義用來處理薪水帳冊的類別。  您可以定義泛型 `Payroll` 類別，這個類別包含 `RunPayroll` 方法，可以計算一般週薪。  然後，您可針對更特定的 `BonusPayroll` 類別，使用 `Payroll` 做為基底類別，於分發員工獎金時使用。  
  
 `BonusPayroll` 類別可繼承和覆寫在基底類別 `Payroll` 中定義的 `PayEmployee` 方法。  
  
 下列範例定義基底類別 `Payroll`，以及衍生類別 `BonusPayroll`，用以覆寫 `PayEmployee` 繼承方法。  程序 `RunPayroll` 會建立 `Payroll` 物件和 `BonusPayroll` 物件，並將它們傳遞至函式 `Pay`，該函式會執行這兩個物件的 `PayEmployee` 方法。  
  
 [!code-vb[VbVbalrOOP#28](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#28)]  
  
## MyBase 關鍵字  
 `MyBase` 關鍵字的行為就像參考類別目前執行個體之基底類別的物件變數。  `MyBase` 經常用於存取衍生類別中所覆寫或遮蔽的基底類別成員。  特別是，`MyBase.New` 用於從衍生類別建構函式 \(Constructor\) 明確地呼叫基底類別建構函式。  
  
 例如，假設您正在設計要覆寫繼承自基底類別方法的衍生類別。  覆寫方法可呼叫基底類別中的方法並且修改傳回值，下列程式碼片段顯示此項作業：  
  
 [!code-vb[VbVbalrOOP#109](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#109)]  
  
 下列清單說明有關使用 `MyBase` 的限制：  
  
-   `MyBase` 指的是即時基底類別及其繼承成員。  您不能使用該關鍵字來存取類別中的 `Private` 成員。  
  
-   `MyBase` 是關鍵字，而不是實質的物件。  您不能將 `MyBase` 指派到變數、傳遞到程序或在 `Is` 比較中使用。  
  
-   `MyBase` 限定的方法不需要在即時基底類別中定義，而是必須在間接繼承基底類別中定義。  為了正確編譯 `MyBase` 所限定的參考，某些基底類別必須包含符合呼叫中所出現之參數名稱和型別的方法。  
  
-   您不能使用 `MyBase` 來呼叫 `MustOverride` 基底類別方法。  
  
-   無法使用 `MyBase` 來限定自己。  因此下列程式碼是無效的：  
  
     `MyBase.MyBase.BtnOK_Click()`  
  
-   無法在模組中使用 `MyBase`。  
  
-   如果基底類別在不同的組件中時，就無法使用 `MyBase` 來存取標記為 `Friend` 的基底類別成員。  
  
 如需詳細資訊與其他範例，請參閱 [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)。  
  
## MyClass 關鍵字  
 `MyClass` 關鍵字的行為就像參考原先實作之類別目前執行個體的物件變數。  `MyClass` 與 `Me` 類似，但會將 `MyClass` 上的每個方法和屬性呼叫都視同方法或屬性為 [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md)。  因此，方法或屬性不受衍生類別中的覆寫所影響。  
  
-   `MyClass` 是關鍵字，而不是實質的物件。  您不能將 `MyClass` 指派到變數、傳遞到程序或在 `Is` 比較中使用。  
  
-   `MyClass` 指的是包含類別及其繼承成員。  
  
-   `MyClass` 可用來做為 `Shared` 成員的限定詞。  
  
-   `MyClass` 不能用在 `Shared` 方法內部，但可用於執行個體方法中，用以存取類別的共用成員。  
  
-   無法在標準模組中使用 `MyClass`。  
  
-   可使用 `MyClass` 來限定基底類別中所定義的方法，而該類別中沒有提供方法的實作。  這類參考的意義與 `MyBase.`*Method* 的意義相同。  
  
 下列範例將比較 `Me` 和 `MyClass`。  
  
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
  
 即使 `derivedClass` 覆寫 `testMethod`，在 `useMyClass` 中的 `MyClass` 關鍵字會使覆寫的效果無效，而且編譯器會解析對 `testMethod` 基底類別 \(Base Class\) 版本的呼叫。  
  
## 請參閱  
 [Inherits Statement](../../../../visual-basic/language-reference/statements/inherits-statement.md)   
 [Me, My, MyBase, and MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)