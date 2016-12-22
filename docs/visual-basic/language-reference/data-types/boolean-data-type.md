---
title: "Boolean Data Type (Visual Basic) | Microsoft Docs"
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
  - "vb.FALSE"
  - "vb.TRUE"
  - "vb.Boolean"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Boolean data type"
  - "Boolean values, False keyword"
  - "False keyword [Visual Basic]"
  - "True keyword [Visual Basic]"
  - "Boolean values, True keyword"
ms.assetid: 4858e630-4813-4216-a55e-f4d0feb884e4
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Boolean Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

保留只可為 `True` 或 `False` 的值。  關鍵字 `True` 和 `False` 對應到 `Boolean` 變數的兩個狀態。  
  
## 備註  
 使用 [Boolean Data Type \(Visual Basic\)](../../../visual-basic/language-reference/data-types/boolean-data-type.md) 以包含兩個狀態的值 \(例如 true\/false、yes\/no 或 on\/off\)。  
  
 `Boolean` 的預設值為 `False`。  
  
 `Boolean` 值不會儲存為數字，且儲存值也不會等於數字。  您不需撰寫程式碼，藉以取得 `True` 和 `False` 的相等數值。  盡可能地將 `Boolean` 變數的使用方式限制為所設計的邏輯值。  
  
## 型別轉換  
 當 Visual Basic 將數字資料型別轉換成 `Boolean` 時，0 會變成 `False`，而其他所有值都會變成 `True`。  當 Visual Basic 將 `Boolean` 值轉換成數字型別時，`False` 會變成 0，而 `True` 會變成 \-1。  
  
 在 `Boolean` 值與數字資料型別間進行轉換時，請記住 .NET Framework 轉換方法並不一定會產生與 Visual Basic 轉換關鍵字相同的結果。  這是因為 Visual Basic 轉換保有與舊版相容的行為。  如需詳細資訊，請參閱[Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)中無法將布林值型別正確轉換成數字型別的說明。  
  
## 程式設計提示  
  
-   **負數**：`Boolean` 不是數字型別且不可代表負值。  無論如何，您都不應該使用 `Boolean` 來存放數值。  
  
-   **型別字元**：`Boolean` 沒有常值型別字元或識別項型別字元。  
  
-   **架構型別。** 在 .NET Framework 中對應的型別為 <xref:System.Boolean?displayProperty=fullName> 結構。  
  
## 範例  
 在下列範例中，`runningVB` 是 `Boolean` 變數，儲存簡單的是\/否設定。  
  
```  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## 請參閱  
 <xref:System.Boolean?displayProperty=fullName>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)   
 [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [CType 函式](../../../visual-basic/language-reference/functions/ctype-function.md)