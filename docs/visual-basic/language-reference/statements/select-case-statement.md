---
title: "Select...Case Statement (Visual Basic) | Microsoft Docs"
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
  - "vb.Select"
  - "vb.Case"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Select statement"
  - "Case statement"
  - "Select...Case statements"
  - "conditional statements, Select Case"
  - "control flow, branching"
  - "Else keyword [Visual Basic], in Select...Case statements"
  - "execution, conditional"
  - "To keyword, in Select...Case statements"
  - "Select Case statement, Select...Case"
  - "Select statement, Select...Case"
  - "Is operator [Visual Basic], in Select...Case statements"
  - "branching, conditional"
  - "Case Else statement, Select...Case"
  - "End keyword, Select Case statements"
  - "Case statement, Select...Case"
ms.assetid: 68877b65-5419-4bf0-a465-20cd0e4c7d44
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Select...Case Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

依據運算式的值，執行數個陳述式群組的其中一組。  
  
## 語法  
  
```  
Select [ Case ] testexpression  
    [ Case expressionlist  
        [ statements ] ]  
    [ Case Else  
        [ elsestatements ] ]  
End Select  
```  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`testexpression`|必要項。  運算式。  必須評估為其中一個基礎資料型別 \(`Boolean`、`Byte`、`Char`、`Date`、`Double`、`Decimal`、`Integer`、`Long`、`Object`、`SByte`、`Short`、`Single`、`String`、`UInteger`、`ULong` 和 `UShort`\)。|  
|`expressionlist`|在 `Case` 陳述式中為必要項。  運算式子句的清單，代表 `testexpression` 的符合值。  運算式子句之間以逗號 \(,\) 來分隔。  每個子句可為以下形式中的一種：<br /><br /> -   *expression1* `To` *expression2*<br />-   \[`Is`\] *comparisonoperator* *expression*<br />-   *expression*<br /><br /> 使用 `To` 關鍵字，為 `testexpression` 指定符合值範圍的界限。  `expression1` 的值必須小於或等於 `expression2` 的值。<br /><br /> 將 `Is` 關鍵字和比較運算子 \(`=`、`<>`、`<`、`<=`、`>` 或 `>=`\) 搭配使用，以便於 `testexpression` 的符合值上指定限制。  如果未提供 `Is` 關鍵字，則會自動將其插入在 *comparisonoperator* 之前。<br /><br /> 只指定 `expression` 的形式會被視為 `Is` 形式的特例，其中 *comparisonoperator* 就是等號 \(`=`\)。  這種形式會被評估為 `testexpression` \= `expression`。<br /><br /> `expressionlist` 中的運算式可以是任意資料型別，只要它們能隱含地轉換為 `testexpression` 型別，且用於這兩種型別的適當 `comparisonoperator` 是有效的即可。|  
|`statements`|選擇項。  一個或多個在 `Case` 之後的陳述式，會在 `testexpression` 符合 `expressionlist` 中的任何子句時執行。|  
|`elsestatements`|選擇項。  一個或多個在 `Case Else` 之後的陳述式，會在 `testexpression` 不符合任何 `Case` 陳述式之 `expressionlist` 中的子句時執行。|  
|`End Select`|終止 `Select`...`Case` 語法結構的定義。|  
  
## 備註  
 如果 `testexpression` 符合任何 `Case` `expressionlist` 子句，`Case` 陳述式之後的陳述式會執行，直到下一個 `Case`、`Case Else` 或 `End Select` 陳述式。  然後控制會被傳遞至接在 `End Select` 之後的陳述式。  如果 `testexpression` 會符合多個 `Case` 子句中的 `expressionlist` 子句，則只會執行第一個符合項之後的陳述式。  
  
 如果在 `testexpression` 和任何其他 `Case` 陳述式中的 `expressionlist` 子句之間都找不到符合項，則 `Case Else` 陳述式可用於引入要執行的 `elsestatements`。  雖然不需要這樣做，不過讓 `Select Case` 語法結構中的 `Case Else` 陳述式處理無法預測的 `testexpression` 值是很好的做法。  如果沒有任何 `Case` `expressionlist` 子句會符合 `testexpression` 而且沒有任何 `Case Else` 陳述式，則會將控制傳遞至 `End Select` 之後的陳述式。  
  
 您可以在每個 `Case` 子句中使用多個運算式或範圍。  例如，下列程式行是有效的。  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
>  用於 `Case` 和 `Case Else` 陳述式的 `Is` 關鍵字和用於物件參考比較的 [Is Operator](../../../visual-basic/language-reference/operators/is-operator.md) 不同。  
  
 您可以指定字元字串的範圍和多個運算式。  在下列範例中，`Case` 符合完全等於 "apples" 的字串、在 "nuts" 和 "soup" 之間具有依字母順序排列之值的字串，或是包含與 `testItem` 目前值完全相同之值的字串。  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 `Option Compare` 的設定會影響字串的比較。  使用 `Option Compare Text` 時，字串 "Apples" 和 "apples" 的比較結果會相等，但使用 `Option Compare Binary` 時則不相等。  
  
> [!NOTE]
>  具有多個子句的 `Case` 陳述式可以表現所謂「*最少運算*」的行為。  Visual Basic 會由左至右評估子句，如果某個子句產生 `testexpression` 的符合項，就不會評估剩下的子句。  執行最少運算可以增進效能，但如果您希望評估 `expressionlist` 中的每個運算式，則會產生非預期的結果。  如需最少運算的詳細資訊，請參閱[Boolean Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)。  
  
 如果 `Case` 或 `Case Else` 陳述式區塊中的程式碼不再需要執行區塊中的任何陳述式，則可以使用 `Exit Select` 陳述式結束區塊。  這麼做會將控制立即轉移至 `End Select` 後面的陳述式。  
  
 `Select Case` 語法結構可以是巢狀結構。  每個巢狀 `Select Case` 語法結構都必須具有相配的 `End Select` 陳述式，並且必須完整地包含在形成巢狀之 `Select Case` 語法結構外的單一 `Case` 或 `Case Else` 陳述式區塊中。  
  
## 範例  
 下列範例會使用 `Select Case` 語法結構，寫入與 `number` 變數的值相對應的程式行。  第二個 `Case` 陳述式會包含與目前 `number` 之值相符合的值，所以會執行寫著 "Between 6 and 8, inclusive" 的陳述式。  
  
 [!code-vb[VbVbalrStatements#54](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/select-case-statement_1.vb)]  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Interaction.Choose%2A>   
 [End Statement](../../../visual-basic/language-reference/statements/end-statement.md)   
 [If...Then...Else Statement](../../../visual-basic/language-reference/statements/if-then-else-statement.md)   
 [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md)   
 [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)