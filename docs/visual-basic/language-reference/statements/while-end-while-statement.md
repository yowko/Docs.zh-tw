---
title: "While...End While Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.While"
  - "vb.While...EndWhile"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "While statement, While...End While"
  - "While statement"
  - "While...End While statements"
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# While...End While Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

只要給定的條件是 `True`，便會執行一系列的陳述式。  
  
## 語法  
  
```  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`condition`|必要項。  `Boolean` 運算式。  如果 `condition` 是 `Nothing`，Visual Basic 會將它視為 `False`。|  
|`statements`|選擇項。  `While` 後面的一或多個陳述式，每次 `condition` 是 `True` 時就會執行該陳述式。|  
|`Continue While`|選擇項。  為 `While` 區塊的下一個反覆項目控制權。|  
|`Exit While`|選擇項。  從 `While` 區塊當中傳出控制權。|  
|`End While`|必要項。  結束 `While` 區塊的定義。|  
  
## 備註  
 只要條件仍是 `True`，在您想要重複一組陳述式不定次數時，請使用 `While...End While` 結構。  如果想要在何處測試條件，或測試何種結果方面更具彈性，您可能會慣用 [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md)。  如果您想要重複陳述式特定次數，[For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md) 通常是較好的選擇。  
  
> [!NOTE]
>  `While` 關鍵字也可以用於 [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md)、[Skip While Clause](../../../visual-basic/language-reference/queries/skip-while-clause.md) 和 [Take While Clause](../../../visual-basic/language-reference/queries/take-while-clause.md)。  
  
 如果 `condition` 為 `True`，則會執行所有 `statements`，直到遇到 `End While` 陳述式為止。  控制項就會返回到 `While` 陳述式，然後， `condition` 再被檢查。  如果 `condition` 仍為 `True`，則會重複這項處理。  如果是 `False`，控制項會將 `End While` 至接在陳述式之後的陳述式。  
  
 ，在開始迴圈前， `While` 陳述式永遠檢查這個條件。  只要條件維持為 `True`，迴圈就會繼續。  如果 `condition` 是 `False` ，初次進入迴圈時，它也不會執行一次。  
  
 `condition` 通常來自於兩個值的比較，不過，可以是任何評估為 [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) 值的任何運算式\(`True` 或 `False`\)。  這個運算式可以包含其他資料型別的值，例如數字型別\(Numeric Type\)，已轉換成 `Boolean`。  
  
 您可以將一個迴圈置於另一個迴圈內，以便巢狀化 `While` 迴圈。  您可以將不同類型的控制結構以巢狀結構互置。  如需詳細資訊，請參閱 [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)。  
  
## 結束時，  
 [結束時，](../../../visual-basic/language-reference/statements/exit-statement.md) 陳述式可能會提供另一種 `While` 結束迴圈。  直接`Exit While``End While` 至接在陳述式之後的陳述式控制權。  
  
 您通常會使用 `Exit While` ，在特定條件評估之後\(例如，在 `If...Then...Else` 結構\)。  如果偵測到一個條件 \(例如錯誤值或終止要求\)，而該條件會使迴圈不需要或不可能繼續重複執行，則您可能會想要結束迴圈。  您可以使用 `Exit While` ，同時對測試會造成*無限迴圈*，是迴圈無限次數條件時。  您可以使用 `Exit While` 逸出此迴圈。  
  
 您可以將任意數目的 `Exit While` 陳述式放在 `While` 中的任何位置。  
  
 用於巢狀的 `While` 迴圈內時，`Exit While` 會將控制權轉移到最內層迴圈的外部，再轉入下一個較高的巢狀層次。  
  
 為迴圈的下一個反覆項目的直接 `Continue While` 陳述式傳送控制項。  如需詳細資訊，請參閱 [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md)。  
  
## 範例  
 在下列範例中，迴圈中的陳述式會繼續執行，直到 `index` 變數大小 10 為止。  
  
 [!code-vb[VbVbalrStatements#171](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_1.vb)]  
  
## 範例  
 下列範例說明 `Continue While` 和 `Exit While` 陳述式的用法。  
  
 [!code-vb[VbVbalrStatements#172](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_2.vb)]  
  
## 範例  
 下列範例會讀取文字檔中的所有文字行。  <xref:System.IO.File.OpenText%2A> 方法會開啟檔案，並傳回讀取字元的 <xref:System.IO.StreamReader>。  在 `While` 情況， `StreamReader` 的 <xref:System.IO.StreamReader.Peek%2A> 方法判斷檔案是否包含其他字元。  
  
 [!code-vb[VbVbalrStatements#173](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_3.vb)]  
  
## 請參閱  
 [Loop Structures](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md)   
 [For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md)   
 [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)   
 [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md)