---
title: "Anonymous type member name can be inferred only from a simple or qualified name with no arguments | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc36556"
  - "bc36556"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36556"
ms.assetid: e3ba1f33-3a71-4f03-9b04-ed5ec17de17c
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Anonymous type member name can be inferred only from a simple or qualified name with no arguments
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

您無法從複雜運算式推斷匿名型別成員名稱。  
  
```vb#  
Dim numbers() As Integer = {1, 2, 3, 4, 5}  
' Not valid.  
' Dim instanceName1 = New With {numbers(3)}  
```  
  
 如需可以推斷和無法推斷成員名稱和型別的匿名型別來源的詳細資訊，請參閱 [如何：在匿名類型宣告中推斷屬性名稱和類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)。  
  
 **錯誤 ID**：BC36556  
  
### 若要更正這個錯誤  
  
-   將運算式指派給成員名稱，如下列程式碼所示：  
  
    ```  
    Dim instanceName2 = New With {.number = numbers(3)}  
    ```  
  
## 請參閱  
 [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [如何：在匿名類型宣告中推斷屬性名稱和類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)