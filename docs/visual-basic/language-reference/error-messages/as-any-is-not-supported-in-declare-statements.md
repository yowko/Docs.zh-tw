---
title: "&#39;As Any&#39; is not supported in &#39;Declare&#39; statements | Microsoft Docs"
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
  - "bc30828"
  - "vbc30828"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30828"
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;As Any&#39; is not supported in &#39;Declare&#39; statements
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`Any` 資料型別是在 Visual Basic 6.0 \(含\) 較早版本中與 `Declare` 陳述式搭配使用，以允許使用包含任何資料型別的引數。  但由於 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 支援多載，因此使得 `Any` 資料型別已過時。  
  
 **錯誤 ID**：BC30828  
  
### 若要更正這個錯誤  
  
1.  請宣告您要使用的特定型別參數，例如：  
  
     [!code-vb[VbVbalrStatements#95](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_1.vb)]  
  
2.  如果呼叫的程序需要的是 `Void*`，請使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性 \(Attribute\) 指定 `As Any`。  
  
     [!code-vb[VbVbalrStatements#96](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_2.vb)]  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Walkthrough: Calling Windows APIs](../Topic/Walkthrough:%20Calling%20Windows%20APIs%20\(Visual%20Basic\).md)   
 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)   
 [在 Managed 程式碼中建立原型](../Topic/Creating%20Prototypes%20in%20Managed%20Code.md)