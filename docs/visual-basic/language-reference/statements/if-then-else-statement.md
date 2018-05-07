---
title: If...Then...Else 陳述式 (Visual Basic)
ms.date: 04/16/2018
f1_keywords:
- vb.ElseIf
- vb.Then
- vb.If
- vb.EndIf
helpviewer_keywords:
- ElseIf statement [Visual Basic], If...Then...Else
- Then statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], branching
- execution [Visual Basic], conditional
- TypeOf...Is expression, and If...Then...Else statements
- If...Then...Else statements
- If statement [Visual Basic], If...Then...Else
- If statement [Visual Basic]
- Is operator [Visual Basic], in If...Then...Else statements
- If Operator [Visual Basic]
- branching [Visual Basic], conditional
- If function [Visual Basic], and If...Then...Else statements
- Else statement [Visual Basic]
ms.assetid: 790068a2-1307-4e28-8a72-be5ebda099e9
ms.openlocfilehash: 08d51326ee0c9f91eec02467ebcb116354b5033f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ifthenelse-statement-visual-basic"></a>If...Then...Else 陳述式 (Visual Basic)
根據運算式的值而定，有條件地執行陳述式群組。  
  
## <a name="syntax"></a>語法  
  
```  
' Multiline syntax:  
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

## <a name="quick-links-to-example-code"></a>範例程式碼的快速連結

本文包含數個範例說明使用`If`...`Then`...`Else`陳述式：

* [多行的語法範例](#multi-line)
* [巢狀的語法範例](#nested)
* [單行語法範例](#single-line)

## <a name="parts"></a>組件  
 `condition`  
 必要。 運算式。 必須評估為`True`或`False`，或可以隱含轉換成資料型別`Boolean`。  
  
 如果運算式是[Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean`變數評估為[Nothing](../../../visual-basic/language-reference/nothing.md)，條件是運算式會視為`False`和`Else`執行區塊。  
  
 `Then`  
 在單行語法; 所需選擇性參數的多行的語法。  
  
 `statements`  
 選擇性。 一或多個陳述式下列`If`...`Then`時，會執行`condition`評估為`True`。  
  
 `elseifcondition`  
 若`ElseIf`存在。 運算式。 必須評估為`True`或`False`，或可以隱含轉換成資料型別`Boolean`。  
  
 `elseifstatements`  
 選擇性。 一或多個陳述式下列`ElseIf`...`Then`時，會執行`elseifcondition`評估為`True`。  
  
 `elsestatements`  
 選擇性。 如果沒有先前執行的一或多個陳述式`condition`或`elseifcondition`運算式評估為`True`。  
  
 `End If`  
 終止的多行新版`If`...`Then`...`Else`區塊。  
  
## <a name="remarks"></a>備註  
  
### <a name="multiline-syntax"></a>多行的語法  
 當`If`...`Then`...`Else`遇到陳述式時，`condition`進行測試。 如果`condition`是`True`、 陳述式`Then`會執行。 如果`condition`是`False`，每個`ElseIf`陳述式 （如果有的話） 會評估順序。 當`True``elseifcondition`找到，緊接相關聯的陳述式`ElseIf`會執行。 如果沒有`elseifcondition`評估為`True`，或者如果有任何`ElseIf`陳述式、 陳述式`Else`會執行。 在執行下列陳述式之後`Then`， `ElseIf`，或`Else`，之後的陳述式會繼續執行`End If`。  
  
 `ElseIf`和`Else`子句是選擇性。 您可以擁有許多`ElseIf`子句做為您想要`If`...`Then`...`Else`陳述式，但不是`ElseIf`子句可以出現在之後`Else`子句。 `If`...`Then`...`Else`可以彼此嵌入陳述式。  
  
 在多行的語法中，`If`陳述式必須是唯一的陳述式的第一行。 `ElseIf`， `Else`，和`End If`陳述式前面可以有只有行標籤。 `If`...`Then`...`Else`區塊的結尾必須`End If`陳述式。  
  
> [!TIP]
>  [選取...陳述式的大小寫](../../../visual-basic/language-reference/statements/select-case-statement.md)評估單一運算式，有幾個可能的值時，可能會更有用。  
  
### <a name="single-line-syntax"></a>單行語法  
 您可以使用單一條件與程式碼的單行語法來執行，如果是 true。 不過，多行語法可提供更多的結構和彈性，而且易於讀取、 維護及偵錯。  
  
 下面這樣`Then`關鍵字會檢查以判斷在陳述式是否為單行`If`。 如果不是註解後面出現`Then`同一行中，陳述式會被視為單一線條`If`陳述式。 如果`Then`不存在，它必須是多行開頭`If`...`Then`...`Else`.  
  
 在單行語法中，您可以有多個陳述式的結果執行`If`...`Then`決策。 所有陳述式必須在同一行，並以冒號分隔。  

## <a name="multiline-syntax-example"></a>多行的語法範例

<a name="multi-line"></a>
 
 下列範例說明使用的多行的語法`If`...`Then`...`Else`陳述式。  
  
 [!code-vb[VbVbalrStatements#101](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_1.vb?highlight=11,14,17,19)]

## <a name="nested-syntax-example"></a>巢狀的語法範例

<a name="nested"></a>

 下列範例包含巢狀`If`...`Then`...`Else`陳述式。  
  
 [!code-vb[VbVbalrStatements#102](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_2.vb?highlight=14,15,17,19,20,21,23,25,26,28)]

## <a name="single-line-syntax-example"></a>單行語法範例
  
<a name="single-line"></a> 下列範例說明使用單行語法。  
  
 [!code-vb[VbVbalrStatements#103](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_3.vb?highlight=18)]
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.Interaction.Choose%2A>  
 <xref:Microsoft.VisualBasic.Interaction.Switch%2A>  
 [#If...Then...#Else 指示詞](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [Select...Case 陳述式](../../../visual-basic/language-reference/statements/select-case-statement.md)  
 [巢狀控制結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [決策結構](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [在 Visual Basic 中的邏輯和位元運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [If 運算子](../../../visual-basic/language-reference/operators/if-operator.md)
