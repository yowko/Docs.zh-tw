---
title: "Cannot convert anonymous type to expression tree because it contains a field that is used in the initialization of another field | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc36548"
  - "vbc36548"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36548"
ms.assetid: 27de068f-080e-4160-86bf-1ec23fd1925a
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Cannot convert anonymous type to expression tree because it contains a field that is used in the initialization of another field
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

當某個匿名型別的屬性用於初始化其他匿名型別的屬性時，編譯器不接受匿名轉換至運算式樹狀結構。  例如在下列程式碼中，會在初始設定清單中宣告 `Prop1`，然後當做 `Prop2` 的初始值使用。  
  
```vb#  
Module M2  
  
    Sub ExpressionExample(Of T)(ByVal x As Expressions.Expression(Of Func(Of T)))  
    End Sub  
  
    Sub Main()  
        ' The following line causes the error.  
        ' ExpressionExample(Function() New With {.Prop1 = 2, .Prop2 = .Prop1})  
  
    End Sub  
End Module  
```  
  
 **錯誤 ID**：BC36548  
  
### 若要更正這個錯誤  
  
-   將 `Prop1` 的初始值指派給區域變數。  將該變數同時指派給 `Prop1` 和 `Prop2`，如下列程式碼所示。  
  
    ```  
    Sub Main()  
  
        Dim temp = 2  
        ExpressionExample(Function() New With {.Prop1 = temp, .Prop2 = temp})  
  
    End Sub  
    ```  
  
## 請參閱  
 [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [運算式樹狀架構](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)   
 [如何：使用運算式樹狀架構建置動態查詢](../Topic/How%20to:%20Use%20Expression%20Trees%20to%20Build%20Dynamic%20Queries%20\(C%23%20and%20Visual%20Basic\).md)