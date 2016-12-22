---
title: "Implicit conversion from &#39;&lt;typename1&gt;&#39; to &#39;&lt;typename2&gt;&#39; in copying the value of &#39;ByRef&#39; parameter &#39;&lt;parametername&gt;&#39; back to the matching argument. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc41999"
  - "bc41999"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC41999"
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Implicit conversion from &#39;&lt;typename1&gt;&#39; to &#39;&lt;typename2&gt;&#39; in copying the value of &#39;ByRef&#39; parameter &#39;&lt;parametername&gt;&#39; back to the matching argument.
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

程序是以 [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) 引數呼叫的，但此引數的型別與對應之參數的型別不同。  
  
 如果您傳遞引數 `ByRef`，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 有時會將引數值複製到程序中的區域變數，而不是傳遞參考。  在這種狀況下，當程序傳回時，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 必須接著將區域變數值複製回呼叫程式碼中的引數。  
  
 如果 `ByRef` 引數值已複製到程序，並且引數和參數屬於相同型別，便不需要轉換。  但是，如果型別不同，則 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 必須以兩個方向轉換。  因為您無法在程序引數或參數上使用 `CType` 或任何其他轉換關鍵字，因此這類轉換一律是隱含轉換。  
  
 根據預設，這是一個警告訊息。  如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](/visual-studio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID：**BC41999  
  
### 若要更正這個錯誤  
  
-   請盡可能使用與程序參數相同型別的呼叫引數，這樣 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 便不需要執行任何轉換。  
  
-   如果您需要以不同於參數型別的引數型別呼叫程序，但不需要傳回值至此呼叫引數，則參數必須定義為 [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) 而不是 `ByRef`。  
  
## 請參閱  
 [Procedures](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Passing Arguments by Value and by Reference](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)