---
title: "How to: Control the Scope of a Variable (Visual Basic) | Microsoft Docs"
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
  - "variables [Visual Basic], scope"
  - "declared elements, scope"
  - "visibility, declared elements"
  - "variables [Visual Basic], visibility"
  - "scope, declared elements"
  - "scope, variables"
  - "scope, Visual Basic"
  - "declared elements, visibility"
  - "visibility, variables"
ms.assetid: 44b7f62a-cb5c-4d50-bce9-60ae68f87072
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# How to: Control the Scope of a Variable (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

一般而言，變數是位在宣告該變數之區域的「*範圍*」\(Scope\) 中，或是可見的以供參考。  在一些情況下，變數的「*存取層級*」\(Access Level\) 可能會影響它的範圍。  
  
 如需詳細資訊，請參閱 [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)。  
  
## 在區塊或程序層級設定範圍  
  
#### 若要只可在區塊內看到變數  
  
-   在區塊的初始和終止宣告陳述式 \(Declaration Statement\) 之間 \(例如 `For` 迴圈 \(Loop\) 的 `For` 和 `Next` 陳述式 \(Statement\) 之間\)，為變數放入 [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md)。  
  
     您只可在該區塊內參考此變數。  
  
#### 若要只可在程序內看到變數  
  
-   在程序內而在任意區塊外 \(例如 `With`...`End With` 區塊\)，為變數放入 `Dim` 陳述式。  
  
     您只可在該程序內 \(包括該程序所含的所有區塊內\) 參考此變數。  
  
## 在模組或命名空間層級設定範圍  
 為了方便起見，「*模組層級*」\(Module Level\) 這個詞彙也可套用在模組、類別和結構。  模組層級變數的存取層級可決定它的範圍。  包含模組、類別或結構的命名空間也會影響範圍。  
  
#### 若要在模組、類別或結構中都可看到變數  
  
1.  針對位在模組、類別或結構內而在任意程序外的變數放入 `Dim` 陳述式。  
  
2.  在 `Dim` 陳述式中加入 [Private](../../../../visual-basic/language-reference/modifiers/private.md) 關鍵字。  
  
3.  您可在模組、類別或結構內的任何位置參考此變數，而不是模組、類別或結構的外部。  
  
#### 若要在命名空間中看到變數  
  
1.  針對位在模組、類別或結構內而在任意程序外的變數放入 `Dim` 陳述式。  
  
2.  在 `Dim` 陳述式中包含 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) 或 [Public](../../../../visual-basic/language-reference/modifiers/public.md) 關鍵字。  
  
3.  您可在包含該模組、類別或結構之命名空間內的任何位置參考此變數。  
  
## 範例  
 下列範例在模組層級宣告變數，並將該變數的可視性限制成該模組內的程式碼。  
  
```  
Module demonstrateScope  
    Private strMsg As String  
    Sub initializePrivateVariable()  
        strMsg = "This variable cannot be used outside this module."  
    End Sub  
    Sub usePrivateVariable()  
        MsgBox(strMsg)  
    End Sub  
End Module  
```  
  
 在上個範例中，模組 `demonstrateScope` 中定義的所有程序都可參考 `String` 變數 `strMsg`。  呼叫 `usePrivateVariable` 程序時，會在對話方塊中顯示字串 \(String\) 變數 `strMsg` 的內容。  
  
 將上個範例做了如下修改後，在宣告字串變數 `strMsg` 的命名空間內之任意位置的程式碼就可參考該變數。  
  
```  
Public strMsg As String  
```  
  
## 穩固程式設計  
 變數的範圍愈小，意外參考到另一個同名變數的機會就會愈小。  同時您還可以減少因參考比對而發生的問題。  
  
## .NET Framework 安全性  
 變數的範圍愈小，惡意程式碼不適當使用此變數的機會就愈小。  
  
## 請參閱  
 [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)   
 [Lifetime in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)   
 [Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md)   
 [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md)