---
title: "How to: Hide a Variable with the Same Name as Your Variable (Visual Basic) | Microsoft Docs"
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
  - "declarations, elements"
  - "element names, qualification"
  - "references, declared elements"
  - "declaration statements, declared elements"
  - "declaring elements"
  - "referencing declared elements"
  - "declared elements, referencing"
  - "declared elements, about declared elements"
ms.assetid: e39c0752-f19f-4d2e-a453-00df1b5fc7ee
caps.latest.revision: 25
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 25
---
# How to: Hide a Variable with the Same Name as Your Variable (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

您可以利用「*遮蔽*」\(Shadow\) 變數的方式來隱藏變數，即使用相同名稱的變數來重新定義變數。  使用兩種方法來遮蔽要隱藏的變數：  
  
-   **透過範圍遮蔽。** 若某個區域包含要隱藏的變數，您可在該區域的子區域中重新宣告變數，即可透過範圍來遮蔽變數。  
  
-   **透過繼承遮蔽。** 如果要隱藏的變數是在類別層級定義的，則可以在衍生類別中使用 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) 關鍵字重新宣告變數，然後透過繼承來遮蔽變數。  
  
## 隱藏變數的兩種方法  
  
#### 若要透過範圍來遮蔽變數以隱藏變數  
  
1.  判斷定義要隱藏的變數所在區域，及判斷以您的變數重新定義該變數的子區域。  
  
    |變數的區域|允許重新定義的子區域|  
    |-----------|----------------|  
    |模組|模組中的類別|  
    |類別|類別中的子類別<br /><br /> 類別中的程序|  
  
     您不能在程序的區塊中重新定義程序變數，例如在 `If`...`End If` 結構或 `For` 迴圈中。  
  
2.  如果子區域不存在，請予以建立。  
  
3.  在子區域中，寫入 [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) 來宣告主導遮蔽的變數。  
  
     當子區域中的程式碼參考變數名稱時，編譯器就會解析對主導遮蔽變數的參考。  
  
     下列範例示範如何透過範圍遮蔽和略過遮蔽的參考。  
  
    ```  
    Module shadowByScope  
        ' The following statement declares num as a module-level variable.  
        Public num As Integer  
        Sub show()  
            ' The following statement declares num as a local variable.  
            Dim num As Integer  
            ' The following statement sets the value of the local variable.  
            num = 2  
            ' The following statement displays the module-level variable.  
            MsgBox(CStr(shadowByScope.num))  
        End Sub  
        Sub useModuleLevelNum()  
            ' The following statement sets the value of the module-level variable.  
            num = 1  
            show()  
        End Sub  
    End Module  
    ```  
  
     前面的範例同時在模組層級和程序層級 \(在程序 `show` 中\) 宣告變數 `num`。  區域變數 `num` 會遮蔽在 `show` 中的模組層級變數 `num`，所以區域變數會設定為 2。  不過，並沒有區域變數遮蔽 `useModuleLevelNum` 程序中的 `num`。  因此，`useModuleLevelNum` 會將模組層級變數的值設定為 1。  
  
     限定具有模組名稱的 `num`，會使 `show` 中的 `MsgBox` 呼叫略過遮蔽機制。  因此，顯示的會是模組層級變數而非區域變數。  
  
#### 若要透過繼承來遮蔽變數以隱藏變數  
  
1.  確定要隱藏的變數是在類別內，而且是在類別層級 \(即在任何程序以外\) 宣告。  否則您無法透過繼承來遮蔽變數。  
  
2.  如果衍生自變數類別的類別不存在，請予以定義。  
  
3.  在衍生類別中寫入 `Dim` 陳述式來宣告您的變數。  在宣告中加入 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) 關鍵字。  
  
     當衍生類別中的程式碼參考變數名稱時，編譯器就會解析對變數的參考。  
  
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
  
     前面的範例在基底類別中宣告變數 `shadowString`，並且在衍生類別中遮蔽這個變數。  當名稱 `shadowString` 不限制時，在衍生類別中的 `showStrings` 程序會顯示字串的主導遮蔽版本。  接著當 `shadowString` 符合 `MyBase`關鍵字資格時，會顯示遮蔽的版本。  
  
## 穩固程式設計  
 遮蔽會使用相同名稱引入多個變數版本。  當程式碼陳述式參考變數名稱時，編譯器 \(Compiler\) 所解析出的版本，取決於例如程式碼陳述式位置和限定字串的存在與否等因素。  這有可能會增加參考到遮蔽變數不必要版本的風險。  您可全面限定遮蔽變數的所有參考，以降低風險。  
  
## 請參閱  
 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Shadowing in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)   
 [Differences Between Shadowing and Overriding](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)   
 [How to: Hide an Inherited Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)   
 [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)   
 [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)   
 [Me, My, MyBase, and MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)   
 [Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)