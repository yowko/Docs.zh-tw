---
title: "如何：在程式碼中中斷和合併陳述式 (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb._"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "冒號 (:)"
  - "行接續符號"
  - "_ 行接續字元"
  - ": 行分隔符號字元"
  - "Visual Basic 程式碼，分行符號"
  - "Visual Basic 程式碼，分行符號"
  - "Visual Basic 程式碼，行接續符號"
  - "長的程式碼"
  - "行終端符號"
  - "行接續序列"
  - "底線，程式碼中的"
  - "陳述式 [Visual Basic]，行接續符號"
  - "分行符號，程式碼"
  - "行接續字元"
  - "Visual Basic 程式碼，行接續符號"
  - "陳述式 [Visual Basic]，分行符號"
ms.assetid: dea01dad-a8ac-484a-bb3a-8c45a1b1eccc
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# 如何：在程式碼中中斷和合併陳述式 (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

撰寫程式碼時，您有時也許會在程式碼編輯器中建立冗長的陳述式，而需要水平捲動才能完全看見。  雖然這不會影響您的程式碼，以便讓難以將您或其他人可以讀取程式碼，則會出現在監視器。  在這種情況，您應該考慮將較長的陳述式分為數行。  
  
### 若要將單一陳述式分為數行  
  
-   在您要斷行的哪一點，使用行接續字元 \(Line\-Continuation Character\)，也就是底線 \(`_`\)。  必須緊接在空格和行結束字元緊接在底線 \(歸位字元 \(Carriage Return\)。  
  
    > [!NOTE]
    >  在某些情況下，因此，如果您省略行接續字元 \(Line\-Continuation Character\)， Visual Basic 編譯器會在下一行程式碼會隱含地 continue 陳述式。  如需可省略行接續字元的語法項目清單，請參閱 \<隱含行接續\> [Statements](../../../visual-basic/programming-guide/language-features/statements.md)。  
  
     在下列範例中，陳述式分成 4 行，除了最後一行外，其餘行都以行接續字元結束。  
  
     [!code-vb[VbVbcnConventions#20](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/how-to-break-and-combine_1.vb)]  
  
     使用這個序列能讓您的程式碼易於閱讀，不論是在線上或者列印出來。  
  
     行接續字元必須是該行的最後一個字元。  您無法在後面加上另一個在同一行。  
  
     某些條件存在。您可以使用行接續字元的位置;例如，您無法在引數清單中使用它。  您可以利用行接續字元中斷一個引數清單，但是引數個別的名稱則必須保持完整。  
  
     使用行接續字元，您將無法繼續註解。  編譯器不會檢查在註解的字元特殊的意義。  如需加入多行註解，請重複在每一行中加入註解符號 \(`'`\)。  
  
 雖然將每個陳述式位於不同行是建議的方法， [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會在同一行也允許您將數個陳述式。  
  
### 若要將數個陳述式置於同一行  
  
-   以冒號 \(`:`\) 將陳述式分隔，如下列範例所示。  
  
     [!code-vb[VbVbcnConventions#10](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/how-to-break-and-combine_2.vb)]  
  
## 請參閱  
 [程式結構和程式碼慣例](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)   
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)