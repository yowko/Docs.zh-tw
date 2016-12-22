---
title: "How to: Hide an Inherited Variable (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "qualification, of element names"
  - "element names, qualification"
  - "references, declared elements"
  - "declaration statements, declared elements"
  - "referencing declared elements"
  - "declared elements, referencing"
  - "declared elements, about declared elements"
  - "variables [Visual Basic], hiding inherited"
ms.assetid: 765728d9-7351-4a30-999d-b5f34f024412
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Hide an Inherited Variable (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

衍生類別 \(Derived Class\) 會繼承其基底類別的所有定義。  如果您想要使用和基底類別中的某個項目相同的名稱來定義變數，則可以在衍生類別中定義變數時，隱藏或「*遮蔽*」\(Shadow\) 該基底類別項目。  如果這樣做，則除非衍生類別中的程式碼明確略過主導遮蔽機制，否則程式碼就會存取您的變數。  
  
 另一個可能會讓您想要隱藏繼承的變數的原因是，這樣可以保護基底類別免於遭到修訂。  基底類別可能會遭到變更，而繼承的項目也隨之改變。  如果發生這種情況，則 `Shadows` 修飾詞 \(Modifier\) 會強制將衍生類別的參考解析為您的變數，而不是基底類別項目。  
  
### 隱藏繼承的變數  
  
1.  確定您想要隱藏的變數是在類別 \(Class\) 層級 \(不在任何程序內\) 宣告。  否則您就不需要隱藏它。  
  
2.  在您的衍生類別內，撰寫 [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) 來宣告變數。  使用和繼承的變數相同的名稱。  
  
3.  在宣告中加入 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) 關鍵字。  
  
     當衍生類別中的程式碼參考變數名稱時，編譯器就會解析對變數的參考。  
  
     下列範例說明遮蔽繼承變數的方法。  
  
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
  
     前面的範例在基底類別中宣告變數 `shadowString`，並且在衍生類別中遮蔽這個變數。  當名稱 `shadowString` 不限制時，在衍生類別中的 `showStrings` 程序會顯示字串的主導遮蔽版本。  接著當 `shadowString` 以 `MyBase` 關鍵字加以限制時，會顯示遮蔽的版本。  
  
## 穩固程式設計  
 遮蔽會使用相同名稱引入多個變數版本。  當程式碼陳述式參考變數名稱時，編譯器 \(Compiler\) 所解析出的版本，取決於例如程式碼陳述式位置和限定字串的存在與否等因素。  這有可能會增加參考到遮蔽變數不必要版本的風險。  您可全面限定遮蔽變數的所有參考，以降低風險。  
  
## 請參閱  
 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Shadowing in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)   
 [Differences Between Shadowing and Overriding](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)   
 [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)   
 [How to: Access a Variable Hidden by a Derived Class](../Topic/How%20to:%20Access%20a%20Variable%20Hidden%20by%20a%20Derived%20Class%20\(Visual%20Basic\).md)   
 [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)   
 [Me, My, MyBase, and MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)   
 [Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)