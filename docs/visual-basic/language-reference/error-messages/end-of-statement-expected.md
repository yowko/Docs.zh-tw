---
title: "必須有陳述式結尾 | Microsoft Docs"
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
  - "bc30205"
  - "vbc30205"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30205"
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 必須有陳述式結尾
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

陳述式已有完整的語法，但是在完成陳述式的項目之後還有額外的程式設計項目。  在每個陳述式的結尾需要一個行結束字元。  
  
 行結束字元分割 Visual Basic 原始程式檔的字元定義為一行。  行結束字元的範例為 Unicode 歸位字元 \(&HD\)， Unicode 換行字元 \(&HA\) 和 Unicode 新行字元的 Unicode 歸位字元 \(Carriage Return\)。  如需行結束字元的詳細資訊，請參閱 [Visual Basic Language Specification](../../../visual-basic/reference/language-specification.md)。  
  
 **錯誤 ID︰**BC30205  
  
### 若要更正這個錯誤  
  
1.  檢查在同一行裡是否有不同的陳述式。  
  
2.  在完成陳述式的項目之後插入一個行結束字元。  
  
## 請參閱  
 [如何：在程式碼中中斷和合併陳述式](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)   
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)