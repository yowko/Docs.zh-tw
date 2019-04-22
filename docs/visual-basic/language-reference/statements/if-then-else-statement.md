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
ms.openlocfilehash: d91a913d515f36a6b974850bc30079b000a919b4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58842690"
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

這篇文章包含數個範例，說明使用`If`...`Then`...`Else`陳述式：

* [多行的語法範例](#multi-line)
* [巢狀的語法範例](#nested)
* [單行語法範例](#single-line)

## <a name="parts"></a>組件  
 `condition`  
 必要項。 運算式。 必須評估為`True`或是`False`，或可以隱含轉換成資料類型`Boolean`。  
  
 如果運算式為[Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean`評估為的變數[Nothing](../../../visual-basic/language-reference/nothing.md)，條件是運算式會視為`False`和`Else`區塊執行。  
  
 `Then`  
 需要在單行語法;中的多行的語法，則為選用。  
  
 `statements`  
 選擇性。 一或多個陳述式的下列`If`...`Then`時，會執行`condition`評估為`True`。  
  
 `elseifcondition`  
 需要`ElseIf`存在。 運算式。 必須評估為`True`或是`False`，或可以隱含轉換成資料類型`Boolean`。  
  
 `elseifstatements`  
 選擇性。 一或多個陳述式的下列`ElseIf`...`Then`時，會執行`elseifcondition`評估為`True`。  
  
 `elsestatements`  
 選擇性。 如果沒有先前執行的一或多個陳述式`condition`或是`elseifcondition`運算式會評估為`True`。  
  
 `End If`  
 終止的多行版本`If`...`Then`...`Else`區塊。  
  
## <a name="remarks"></a>備註  
  
### <a name="multiline-syntax"></a>多行的語法  
 當`If`...`Then`...`Else`遇到陳述式，`condition`測試。 如果`condition`已`True`之後的陳述式、`Then`會執行。 如果`condition`已`False`，每個`ElseIf`陳述式 （如果有的話） 會評估順序。 當`True``elseifcondition`找到，緊接相關聯的陳述式`ElseIf`會執行。 如果沒有`elseifcondition`評估為`True`，或者如果有任何`ElseIf`陳述式，之後的陳述式`Else`會執行。 執行下列陳述式之後`Then`， `ElseIf`，或`Else`，之後的陳述式會繼續執行`End If`。  
  
 `ElseIf`和`Else`子句是兩者都是選擇性。 您可以擁有許多`ElseIf`子句，當您想要`If`...`Then`...`Else`陳述式，但不對`ElseIf`子句可以出現之後`Else`子句。 `If`...`Then`...`Else`陳述式可以在彼此內巢狀結構。  
  
 在多行的語法中，`If`陳述式必須是唯一的陳述式的第一行上。 `ElseIf`， `Else`，和`End If`陳述式只加行標籤。 `If`...`Then`...`Else`區塊的結尾必須`End If`陳述式。  
  
> [!TIP]
>  [選取...Case 陳述式](../../../visual-basic/language-reference/statements/select-case-statement.md)評估單一運算式，有幾個可能的值時，可能會更有用。  
  
### <a name="single-line-syntax"></a>單一列語法  
 您可以使用單一條件與程式碼的單行語法來執行，如果為 true。 不過，多行語法提供更多的結構和彈性，而且可以更輕鬆地閱讀、 維護和偵錯。  
  
 下面`Then`關鍵字會檢查以判斷在陳述式是單行`If`。 如果不是註解的任何項目出現之後`Then`同一行中，陳述式會被視為單行`If`陳述式。 如果`Then`不存在，它必須是多行開頭`If`...`Then`...`Else`.  
  
 在單行語法中，您可以有多個陳述式的結果執行`If`...`Then`決策。 所有的陳述式必須在同一行，並以冒號分隔。  

## <a name="multiline-syntax-example"></a>多行的語法範例

<a name="multi-line"></a>
 
 下列範例示範如何將多行的語法`If`...`Then`...`Else`陳述式。  
  
 [!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a>巢狀的語法範例

<a name="nested"></a>

 下列範例包含巢狀`If`...`Then`...`Else`陳述式。  
  
 [!code-vb[VbVbalrStatements#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#102)]

## <a name="single-line-syntax-example"></a>單行語法範例
  
<a name="single-line"></a> 下列範例說明使用單行語法。  
  
 [!code-vb[VbVbalrStatements#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#103)]
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- <xref:Microsoft.VisualBasic.Interaction.Switch%2A>
- [#If...Then...#Else 指示詞](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Select...Case 陳述式](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [巢狀控制結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [決策結構](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [在 Visual Basic 中的邏輯和位元運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [If 運算子](../../../visual-basic/language-reference/operators/if-operator.md)
