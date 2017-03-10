---
title: "Widening (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.widening"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "conversions, type"
  - "type conversion"
  - "conversions, data type"
  - "Widening keyword"
  - "data type conversion"
ms.assetid: 646ae263-94d3-40a2-b0cc-64f619292f56
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# Widening (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

表示轉換運算子 \(`CType`\) 會將類別或結構轉換成可保留所有可能原始類別或結構值的型別。  
  
## 使用 Widening 關鍵字進行轉換  
 除了 `Widening` 之外，轉換程序還必須指定 `Public Shared`。  
  
 在執行階段中進行的擴展轉換一定會成功，且決不會造成資料遺漏。  範例是 `Single` 轉換成 `Double`、`Char` 轉換成 `String`，以及將衍生型別 \(Derived Type\) 轉換成其基底型別 \(Base Type\)。  因為衍生型別包含基底型別的所有成員，因此是基底型別的執行個體，所以會擴展這個最後一個轉換。  
  
 即使 `Option Strict` 是 `On`，使用程式碼也不必使用 `CType` 來擴展轉換。  
  
 `Widening` 關鍵字可用於以下內容中：  
  
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 如需擴大和縮小轉換運算子的範例定義，請參閱 [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)。  
  
## 請參閱  
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)   
 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [How to: Define an Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)   
 [CType 函式](../../../visual-basic/language-reference/functions/ctype-function.md)   
 [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)