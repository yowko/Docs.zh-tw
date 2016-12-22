---
title: "Visual Basic Limitations | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "limits"
  - "limitations, Visual Basic"
  - "limitations"
  - "limits, Visual Basic code"
  - "Visual Basic code, limitations"
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Visual Basic Limitations
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

舊版的 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 會在程式碼中強制界限，例如變數名稱的長度、模組中允許的變數個數，以及模組大小。  在 [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] 中，已放寬這些限制，因此讓您能更自由地撰寫和排列程式碼。  
  
 實體限制會更依賴於執行階段記憶體，而不是編譯時期考量。  如果您使用審慎的程式設計作法，並將大型應用程式分成多個類別和模組，則幾乎沒有什麼機會遇到內部 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 限制。  
  
 下列是您在非常情況下可能會遇到的一些限制：  
  
-   **名稱長度** ：每一個宣告的程式設計項目名稱都有字元數上限。  如果項目名稱合格的話，這個上限就會套用至整個限定性條件字串。  請參閱[Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
-   **行長度** ：原始程式碼的實體行最多可有 65535 個字元。  如果您使用行接續字元 \(Line Continuation Character\)，則邏輯原始程式碼行就可以更長。  請參閱 [如何：在程式碼中中斷和合併陳述式](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)。  
  
-   **陣列維度** ：您可以對陣列宣告的維度數會有上限。  這會限制您可以使用多少個索引指定陣列元素。  請參閱 [Array Dimensions in Visual Basic](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)。  
  
-   **字串長度** ：您可以在單一字串中儲存的 Unicode 字元數會有上限。  請參閱[String Data Type](../../../visual-basic/language-reference/data-types/string-data-type.md)。  
  
-   **環境字串長度** ：任何做為命令列引數的環境字串最多可有 32768 個字元。  這項限制適用於所有平台。  
  
## 請參閱  
 [程式結構和程式碼慣例](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)   
 [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)