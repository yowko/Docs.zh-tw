---
title: "不會推斷變數 &#39;&lt;variablename&gt;&#39; 的類型，因為它繫結至封閉範圍中的欄位。 | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc42110"
  - "bc42110"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42110"
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
caps.latest.revision: 33
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 33
---
# 不會推斷變數 &#39;&lt;variablename&gt;&#39; 的類型，因為它繫結至封閉範圍中的欄位。
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

不會推斷變數 '\<variablename\>' 的類型，因為它繫結至封閉範圍中的欄位。請變更 '\<variablename\>' 名稱，或使用完整名稱 \(例如 'Me.variablename' 或 'MyBase.variablename'\)。  
  
 程式碼中的迴圈控制變數與類別或其他封閉範圍的欄位具有相同的名稱。  由於使用控制變數時不需包含 `As` 子句，因此變數將會繫結至封閉範圍中的欄位，而且編譯器不會為其建立新的變數，或是推斷其型別。  
  
 在下列範例中，`For` 陳述式中的控制變數 `Index` 會繫結至 `Customer` 類別中的 `Index` 欄位。  編譯器不會為控制變數 `Index` 建立新的變數，或是推斷其型別。  
  
```  
Class Customer  
  
    ' The class has a field named Index.  
    Private Index As Integer  
  
    Sub Main()  
  
    ' The following line will raise this warning.  
        For Index = 1 To 10  
            ' ...  
        Next  
  
    End Sub  
End Class  
  
```  
  
 根據預設，這是一個警告訊息。  如需如何隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](/visual-studio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID**︰BC42110  
  
### 若要解決這個警告  
  
-   將迴圈控制變數的名稱變更為某個識別項 \(其名稱不是類別欄位的名稱\)，即可使該變數成為區域變數。  
  
    ```  
    For I = 1 To 10  
    ```  
  
-   使用 `Me.` 做為變數名稱的前置詞，即可釐清迴圈控制變數繫結至類別欄位的情況。  
  
    ```  
    For Me.Index = 1 To 10  
    ```  
  
-   請不要依賴邏輯型別推斷，而是使用 `As` 子句來指定迴圈控制變數的型別。  
  
    ```  
    For Index As Integer = 1 To 10  
    ```  
  
## 範例  
 下列程式碼以第一項修正方法示範先前的範例。  
  
```  
Class Customer  
  
    ' The class has a field named Index.  
    Private Index As Integer  
  
    Sub Main()  
  
        For I = 1 To 10  
            ' ...  
        Next  
  
    End Sub  
End Class  
```  
  
## 請參閱  
 [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md)   
 [For Each...Next 陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)   
 [For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [How to: Refer to the Current Instance of an Object](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)   
 [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Me, My, MyBase, and MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)