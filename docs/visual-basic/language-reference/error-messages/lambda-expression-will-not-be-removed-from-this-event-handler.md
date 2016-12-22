---
title: "Lambda expression will not be removed from this event handler | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc42326"
  - "vbc42326"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42326"
ms.assetid: 63214dc6-0112-4245-8ebf-7c9e8f5a5782
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Lambda expression will not be removed from this event handler
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Lambda 運算式將不會從這個事件處理常式中移除。請指派 Lambda 運算式給變數，然後使用變數來加入並移除該事件。  
  
 當 Lambda 運算式和事件處理常式一起使用時，您可能看不到預期的行為。  編譯器會為每個 Lambda 運算式定義產生新方法，即使它們完全相同也一樣。  因此，下列程式碼會顯示 `False`。  
  
```vb#  
Module Module1  
  
    Sub Main()  
        Dim fun1 As ChangeInteger = Function(p As Integer) p + 1  
        Dim fun2 As ChangeInteger = Function(p As Integer) p + 1  
        Console.WriteLine(fun1 = fun2)  
    End Sub  
  
    Delegate Function ChangeInteger(ByVal x As Integer) As Integer  
  
End Module  
```  
  
 當 Lambda 運算式和事件處理常式一起使用時，可能會導致未預期的結果。  在下列範例中，`RemoveHandler` 陳述式不會移除由 `AddHandler` 加入的 Lambda 運算式。  
  
```vb#  
Module Module1  
  
    Event ProcessInteger(ByVal x As Integer)  
  
    Sub Main()  
  
        ' The following line adds one listener to the event.  
        AddHandler ProcessInteger, Function(m As Integer) m  
  
        ' The following statement searches the current listeners   
        ' for a match to remove. However, this lambda is not the same  
        ' as the previous one, so nothing is removed.  
        RemoveHandler ProcessInteger, Function(m As Integer) m  
  
    End Sub  
End Module  
```  
  
 根據預設，這是一個警告訊息。  如需如何隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](/visual-studio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID**：BC42326  
  
### 若要更正這個錯誤  
  
-   若要避免警告並移除 Lambda 運算式，請將 Lambda 運算式指派給變數，然後同時在 `AddHandler` 和 `RemoveHandler` 陳述式中使用該變數，如下列範例所示。  
  
    ```vb#  
    Module Module1  
  
        Event ProcessInteger(ByVal x As Integer)  
  
        Dim PrintHandler As ProcessIntegerEventHandler  
  
        Sub Main()  
  
            ' Assign the lambda expression to a variable.  
            PrintHandler = Function(m As Integer) m  
  
            ' Use the variable to add the listener.  
            AddHandler ProcessInteger, PrintHandler  
  
            ' Use the variable again when you want to remove the listener.  
            RemoveHandler ProcessInteger, PrintHandler  
  
        End Sub  
    End Module  
    ```  
  
## 請參閱  
 [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)   
 [Events](../../../visual-basic/programming-guide/language-features/events/events.md)