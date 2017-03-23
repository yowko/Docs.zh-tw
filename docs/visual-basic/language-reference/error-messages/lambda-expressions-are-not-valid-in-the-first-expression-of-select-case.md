---
title: "Lambda expressions are not valid in the first expression of a &#39;Select Case&#39; statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc36635"
  - "vbc36635"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36635"
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
caps.latest.revision: 6
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 6
---
# Lambda expressions are not valid in the first expression of a &#39;Select Case&#39; statement
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

您無法在 `Select Case` 陳述式中，針對測試運算式使用 Lambda 運算式。  Lambda 運算式定義會傳回函式，而 `Select Case` 陳述式的測試運算式必須為基礎資料型別 \(Elementary Data Type\)。  
  
 下列程式碼會產生此錯誤：  
  
```vb#  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 **錯誤 ID**︰BC36635  
  
### 若要更正這個錯誤  
  
-   請檢查程式碼，判斷您是否可使用不同的條件建構，例如 `If...Then...Else` 陳述式。  
  
-   您可能想要呼叫此函式，如下列程式碼所示：  
  
    ```vb#  
    Dim num? As Integer  
    Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
        ' List of the cases  
    End Select  
    ```  
  
## 請參閱  
 [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [If...Then...Else Statement](../../../visual-basic/language-reference/statements/if-then-else-statement.md)   
 [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md)