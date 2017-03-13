---
title: "If...Then...Else Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.ElseIf"
  - "vb.Then"
  - "vb.If"
  - "vb.EndIf"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "ElseIf statement, If...Then...Else"
  - "Then statement, If...Then...Else"
  - "control flow, branching"
  - "execution, conditional"
  - "TypeOf...Is expression, and If...Then...Else statements"
  - "If...Then...Else statements"
  - "If statement, If...Then...Else"
  - "If statement"
  - "Is operator [Visual Basic], in If...Then...Else statements"
  - "If Operator [Visual Basic]"
  - "branching, conditional"
  - "IIf function, and If...Then...Else statements"
  - "Else statement [Visual Basic]"
ms.assetid: 790068a2-1307-4e28-8a72-be5ebda099e9
caps.latest.revision: 29
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 29
---
# If...Then...Else Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

根據運算式的值，有條件的執行陳述式群組。  
  
## 語法  
  
```  
' Multiple-line syntax:  
If condition [ Then ]  
    [ statements ]  
[ ElseIf elseifcondition [ Then ]  
    [ elseifstatements ] ]  
[ Else  
    [ elsestatements ] ]  
End If  
  
' Single-line syntax:  
If condition Then [ statements ] [ Else [ elsestatements ] ]  
```  
  
## 組件  
 `condition`  
 必要項。  運算式。  必須評估為 `True` 或 `False`，或評估為可以隱含轉換為 `Boolean` 的資料型別。  
  
 如果運算式是評估為 [Nothing](../../../visual-basic/language-reference/nothing.md)的 [可為 Null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)`Boolean` 變數，這種情況，視為運算式不 `True`，因此， `Else` 執行區塊。  
  
 `Then`  
 在單行語法中為必要項，在多行語法中為選擇項。  
  
 `statements`  
 選擇項。  接在 `If`...`Then` 之後，如果 `condition` 評估為 `True`，就會執行的一或多個陳述式。  
  
 `elseifcondition`  
 如果有 `ElseIf` 則為必要項。  運算式。  必須評估為 `True` 或 `False`，或評估為可以隱含轉換為 `Boolean` 的資料型別。  
  
 `elseifstatements`  
 選擇項。  接在 `ElseIf`...`Then` 之後，如果 `elseifcondition` 評估為 `True`，就會執行的一或多個陳述式。  
  
 `elsestatements`  
 選擇項。  如果先前無 `condition` 或 `elseifcondition` 運算式評估為 `True`，就會執行的一或多個陳述式。  
  
 `End If`  
 結束 `If`...`Then`...`Else` 區塊。  
  
## 備註  
  
## 多行語法  
 當遇到 `If`...`Then`...`Else` 陳述式時，就會測試 `condition`。  如果 `condition` 為 `True`，就會執行接在 `Then` 之後的陳述式。  如果 `condition` 為 `False`，則會依序評估每個 `ElseIf` 陳述式 \(如果有的話\)。  發現 `elseifcondition` 為 `True` 時，會執行緊接在相關 `ElseIf` 之後的陳述式。  如果沒有 `elseifcondition` 評估為 `True`，或是如果沒有 `ElseIf` 陳述式，就會執行接在 `Else` 之後的陳述式。  執行接在 `Then`、`ElseIf` 或 `Else` 之後的陳述式後，程式碼會繼續執行接在 `End If` 之後的陳述式。  
  
 `ElseIf` 和 `Else` 子句都是選擇項。  在 `If`...`Then`...`Else` 陳述式中可以有任意數目的 `ElseIf` 子句，但是任何 `ElseIf` 子句都不可以出現在 `Else` 子句之後。  `If`...`Then`...`Else` 陳述式可以相互套疊成巢狀。  
  
 在多行語法中，`If` 陳述式必須是第一行唯一的陳述式。  `ElseIf`、`Else` 和 `End If` 陳述式的前面只能出現行標籤。  `If`...`Then`...`Else` 區塊必須以 `End If` 陳述式結束。  
  
> [!TIP]
>  [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) 在評估具有多個可能值的單一運算式時，也許更能發揮作用。  
  
## 單行語法  
 您也可以用單行語法進行簡短的測試。  然而，多行語法提供更多的結構和彈性，而且通常較易閱讀、維護和偵錯。  
  
 接下來會檢查 `Then` 關鍵字後面跟隨的內容，判斷陳述式是否為單行的 `If`。  如果在 `Then` 之後同一行中出現的不是註解，則會將陳述式視為單行的 `If` 陳述式。  如果沒有出現 `Then`，則該陳述式必須是多行 `If`...`Then`...`Else` 的開頭。  
  
 由於 `If`...`Then` 的結果，您可以使用單行語法中執行多個陳述式。  所有陳述式都必須在同一行，並以冒號隔開。  
  
## 範例  
 下列範例說明 `If`...`Then`...`Else` 陳述式多行語法的使用方式。  
  
 [!code-vb[VbVbalrStatements#101](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_1.vb)]  
  
## 範例  
 下列範例包含巢狀的 `If`...`Then`...`Else` 陳述式。  
  
 [!code-vb[VbVbalrStatements#102](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_2.vb)]  
  
## 範例  
 下列範例說明單行語法的使用方式。  
  
 [!code-vb[VbVbalrStatements#103](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_3.vb)]  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Interaction.Choose%2A>   
 <xref:Microsoft.VisualBasic.Interaction.Switch%2A>   
 [\#If...Then...\#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md)   
 [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md)   
 [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [Decision Structures](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)   
 [Logical and Bitwise Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)   
 [If Operator](../../../visual-basic/language-reference/operators/if-operator.md)