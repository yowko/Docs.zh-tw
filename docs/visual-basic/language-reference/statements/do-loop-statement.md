---
title: "Do...Loop Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Do"
  - "vb.Loop"
  - "vb.Until"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "conditional statements, Do…Loop"
  - "while statement, Do...Loop"
  - "execution, conditional"
  - "Do loops"
  - "Until keyword, Do...Loop statement"
  - "Do...Loop statement"
  - "instructions, repeating"
  - "Do statement"
  - "Exit statement, in Do...Loop statements"
  - "loop structures, Do…Loop statements"
  - "do-while statements"
  - "loops, exiting"
  - "Loop keyword, Do...Loop statement"
ms.assetid: 892f9096-b3e2-4aee-834d-83bc4e2c379d
caps.latest.revision: 37
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 37
---
# Do...Loop Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

當 `Boolean` 條件為 `True` 時重複陳述式區塊，或是重複陳述式區塊直到條件變成 `True` 為止。  
  
## 語法  
  
```  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
-or-  
Do  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop { While | Until } condition  
```  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`Do`|必要項。  開始 `Do` 迴圈的定義。|  
|`While`|除非使用 `Until`，否則為必要項。  重複迴圈直到 `condition` 為 `False` 為止。|  
|`Until`|除非使用 `While`，否則為必要項。  重複迴圈直到 `condition` 為 `True` 為止。|  
|`condition`|選擇項。  `Boolean` 運算式。  如果 `condition` 是 `Nothing`，Visual Basic 會將它視為 `False`。|  
|`statements`|選擇項。  當 \(或直到\) `condition` 為 `True` 時，一或數個被重複的陳述式。|  
|`Continue Do`|選擇項。  為 `Do` 迴圈的下一個反覆項目控制權。|  
|`Exit Do`|選擇項。  從 `Do` 迴圈當中傳出控制權。|  
|`Loop`|必要項。  結束 `Do` 迴圈的定義。|  
  
## 備註  
 當您想不定次數重複一組陳述式時，請使用 `Do...Loop` 結構，直到滿足條件為止。  如果您想重複陳述式特定數次時，[For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)通常是較好的選擇。  
  
 可以使用 `While` 或 `Until` 指定 `condition`，但不能同時使用兩者做指定。  
  
 您只可以在迴圈的開頭或結尾處，測試 `condition` 一次。  如果您在迴圈開頭處測試 `condition` \(在 `Do` 陳述式中\)，則迴圈可能一次都不會執行。  如果您在迴圈結尾處進行測試 \(在 `Loop` 陳述式中\)，則迴圈永遠至少執行一次。  
  
 條件通常來自於兩個值的比較，它也可以是任何評估為 [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) 值 \(`True` 或 `False`\) 的運算式。  其中包含其他資料型別的值，例如已轉換為 `Boolean` 的數字型別 \(Numeric Type\)。  
  
 您可以將一個迴圈置於另一個迴圈內，使 `Do` 迴圈套疊成巢狀。  您可以將不同類型的控制結構相互套疊成巢狀。  如需詳細資訊，請參閱 [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)。  
  
> [!NOTE]
>  `Do...Loop` 結構會提供給您比 [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) 還多的彈性，因為它允許您在 `condition` 不是 `True` 時或當它先成為 `True` 時，決定是否結束迴圈。  它還允許您在迴圈開頭或結尾處測試 `condition`。  
  
## Exit Do  
 [Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md) 陳述式可以提供結束 `Do…Loop` 的替代方式。  `Exit Do` 會立即將控制權轉移至 `Loop` 陳述式隨後的陳述式。  
  
 `Exit Do` 通常會在評估一些條件之後使用，例如 `If...Then...Else` 結構。  如果偵測到一個條件 \(例如錯誤值或終止要求\)，而該條件會使迴圈不需要或不可能繼續重複執行，則您可能會想要結束迴圈。  `Exit Do` 的其中一個用處是可以測試會造成「*無止盡迴圈*」\(Endless Loop\) 的條件，無止盡迴圈就是會執行極多次，甚至無數次的迴圈。  您可以使用 `Exit Do` 離開迴圈。  
  
 您可以將任意數目的 `Exit Do` 陳述式包含在 `Do…Loop` 中的任何位置。  
  
 用於巢狀的 `Do` 迴圈內時，`Exit Do` 會將控制權轉移到最內層迴圈的外部，再轉入下一個較高的巢狀層次。  
  
## 範例  
 在下列範例中，迴圈中的陳述式會繼續執行，直到 `index` 變數大小 10 為止。  `Until` 子句是在迴圈的結尾。  
  
 [!code-vb[VbVbalrStatements#131](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_1.vb)]  
  
## 範例  
 下列範例會使用 `While` 子句而不使用 `Until` 子句，並且會在迴圈的開始處而不是結尾處測試 `condition`。  
  
 [!code-vb[VbVbalrStatements#132](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_2.vb)]  
  
## 範例  
 在下列範例中，當 `index` 變數大於 100 時，`condition` 就會停止迴圈。  但是當索引變數大於 10 時，迴圈中的 `If` 陳述式會導致 `Exit Do` 陳述式停止迴圈。  
  
 [!code-vb[VbVbalrStatements#133](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_3.vb)]  
  
## 範例  
 下列範例會讀取文字檔中的所有文字行。  <xref:System.IO.File.OpenText%2A> 方法會開啟檔案，並傳回讀取字元的 <xref:System.IO.StreamReader>。  在 `Do...Loop` 的情況下，`StreamReader` 的 <xref:System.IO.StreamReader.Peek%2A> 方法會判斷是否存在任何額外的字元。  
  
 [!code-vb[VbVbalrStatements#134](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_4.vb)]  
  
## 請參閱  
 [Loop Structures](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md)   
 [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)   
 [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md)