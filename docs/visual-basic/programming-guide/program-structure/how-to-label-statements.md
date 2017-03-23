---
title: "How to: Label Statements (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "colons (:)"
  - "statements [Visual Basic], labels"
  - ": separator character"
  - "Visual Basic code, labeling statements"
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# How to: Label Statements (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

陳述式組塊是由以冒號分隔的程式碼行所構成。  程式碼行的前面若加上識別字串或整數，就稱為已加註「*標記*」\(Label\)。  陳述式標記是用來標記程式碼行，以表示與陳述式 \(如 `On Error Goto`\) 一起使用。  
  
 標籤可以是任何有效的Visual Basic識別項，例如所識別的程式設計項目 — 或整數常值。   標籤必須出現在原始程式碼行的開頭，且不論同一行程式碼後面是否緊跟著陳述式，標籤後面都必須加上一個冒號。  
  
 編譯器辨識標籤的方法，是檢查程式碼行的開頭是否符合任何已定義的識別項。  如果不符合，編譯器則認定為標籤。  
  
 標籤具有專屬的宣告空間，不會干擾其他的識別項。  標籤的範圍就是方法的主體。  在任何模稜兩可的狀況中，標籤宣告具有優先權。  
  
> [!NOTE]
>  標記只能用於方法內的可執行陳述式。  
  
### 若要標記一行程式碼  
  
-   在原始程式碼行的開頭置入識別項，後面加上冒號。  
  
     例如，以下程式碼行分別標記了 `Jump` 和 `120`：  
  
     [!code-vb[VbVbalrStatements#708](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/how-to-label-statements_1.vb)]  
  
## 請參閱  
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)   
 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [程式結構和程式碼慣例](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)