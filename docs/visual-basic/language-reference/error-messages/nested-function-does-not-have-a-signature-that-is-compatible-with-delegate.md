---
title: "Nested function does not have a signature that is compatible with delegate &#39;&lt;delegatename&gt;&#39; | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc36532"
  - "bc36532"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36532"
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
caps.latest.revision: 5
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 5
---
# Nested function does not have a signature that is compatible with delegate &#39;&lt;delegatename&gt;&#39;
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Lambda 運算式已指派給具有不相容簽章的委派。  例如，在下列程式碼中，委派 `Del` 有兩個整數參數。  
  
```vb#  
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer  
```  
  
 如果具有一個引數的 Lambda 運算式已宣告為型別 `Del`，則會引發錯誤：  
  
```vb#  
' Neither of these is valid.   
' Dim lambda1 As Del = Function(n As Integer) n + 1  
' Dim lambda2 As Del = Function(n) n + 1  
```  
  
 **錯誤 ID**：BC36532  
  
### 若要更正這個錯誤  
  
-   調整委派定義或所指派的 Lambda 運算式，讓簽章可相容。  
  
## 請參閱  
 [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)   
 [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)