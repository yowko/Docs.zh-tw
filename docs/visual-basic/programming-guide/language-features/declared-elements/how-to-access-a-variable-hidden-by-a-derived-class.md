---
title: "How to: Access a Variable Hidden by a Derived Class (Visual Basic) | Microsoft Docs"
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
  - "qualification, of element names"
  - "base classes, accessing elements"
  - "element names, qualification"
  - "references, declared elements"
  - "declared elements, referencing"
  - "variables [Visual Basic], accessing hidden"
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# How to: Access a Variable Hidden by a Derived Class (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

當衍生類別中的程式碼存取變數時，編譯器 \(Compiler\) 通常會將參考解析為最接近的可存取版本，也就是說，從正在存取的類別 \(Class\) 反推回去時，所需衍生步驟最少的可存取版本。  如果衍生類別中已經定義變數，則程式碼通常就會存取該定義。  
  
 如果衍生類別變數會遮蔽基底類別中的變數，則會隱藏基底類別版本。  不過，只要使用 `MyBase` 關鍵字來限定基底類別變數，即可存取這個變數。  
  
### 存取衍生類別所隱藏的基底類別變數  
  
-   在運算式或指派陳述式 \(Assignment Statement\) 中，於變數名稱之前加上 `MyBase` 關鍵字和句號 \(`.`\)。  
  
     編譯器會將參考解析為變數的基底類別版本。  
  
     下列範例示範如何透過繼承遮蔽。  這個範例會建立兩個參考，一個參考會存取主導遮蔽變數，另一個參考則會略過遮蔽。  
  
    ```  
    Public Class shadowBaseClass  
        Public shadowString As String = "This is the base class string."  
    End Class  
    Public Class shadowDerivedClass  
        Inherits shadowBaseClass  
        Public Shadows shadowString As String = "This is the derived class string."  
        Public Sub showStrings()  
            Dim s As String = "Unqualified shadowString: " & shadowString &  
                vbCrLf & "MyBase.shadowString: " & MyBase.shadowString  
            MsgBox(s)  
        End Sub  
    End Class  
    ```  
  
     前面的範例在基底類別中宣告變數 `shadowString`，並且在衍生類別中遮蔽這個變數。  當名稱 `shadowString` 不限制時，在衍生類別中的 `showStrings` 程序會顯示字串的主導遮蔽版本。  接著當 `shadowString` 符合 `MyBase`  關鍵字資格時，會顯示遮蔽的版本。  
  
## 穩固程式設計  
 若要降低參考到錯誤版本的受遮蔽變數的風險，您可以對受遮蔽變數的所有參考進行完整限定。  遮蔽會使用相同名稱引入多個變數版本。  當程式碼陳述式參考變數名稱時，編譯器 \(Compiler\) 所解析出的版本，取決於例如程式碼陳述式位置和限定字串的存在與否等因素。  這樣會提高參考到錯誤版本的變數的風險。  
  
## 請參閱  
 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Shadowing in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)   
 [Differences Between Shadowing and Overriding](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)   
 [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)   
 [How to: Hide an Inherited Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)   
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)   
 [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)   
 [Me, My, MyBase, and MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)   
 [Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)