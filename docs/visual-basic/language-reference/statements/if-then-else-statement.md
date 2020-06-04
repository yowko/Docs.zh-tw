---
title: If...Then...Else 陳述式
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
ms.openlocfilehash: 0884b71c24742286e695e720add9d00dd4bfe52b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404585"
---
# <a name="ifthenelse-statement-visual-basic"></a>If...Then...Else 陳述式 (Visual Basic)

根據運算式的值而定，有條件地執行陳述式群組。

## <a name="syntax"></a>語法

```vb
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

本文包含幾個範例，說明如何使用 `If` ... `Then`...`Else`句

- [多行語法範例](#multi-line)
- [嵌套語法範例](#nested)
- [單行語法範例](#single-line)

## <a name="parts"></a>組件

`condition` \
必要。 運算式。 必須評估為 `True` 或 `False` ，或是可隱含轉換成的資料類型 `Boolean` 。

如果運算式是評估為「無」的[可為 null](../../programming-guide/language-features/data-types/nullable-value-types.md)的 `Boolean` 變數，則會將條件視為運算式為[Nothing](../nothing.md) `False` ，並 `ElseIf` 會評估區塊（如果有的話），或是 `Else` 區塊會在存在時執行。

`Then` \
單行語法中的必要項;在多行語法中為選擇性。

`statements` \
選擇性。 `If` `Then` 如果 `condition` 評估為，則會執行 `True` 下列一個或多個語句。

`elseifcondition` \
如果 `ElseIf` 存在，則為必要。 運算式。 必須評估為 `True` 或 `False` ，或是可隱含轉換成的資料類型 `Boolean` 。

`elseifstatements` \
選擇性。 `ElseIf` `Then` 如果 `elseifcondition` 評估為，則會執行 `True` 下列一個或多個語句。

`elsestatements` \
選擇性。 如果沒有上一個 `condition` or `elseifcondition` 運算式評估為，就會執行一或多個語句 `True` 。

`End If` \
終止的多行版本 `If` ... `Then`...`Else`總匯.

## <a name="remarks"></a>備註

### <a name="multiline-syntax"></a>多行語法

當 `If` ... `Then`...`Else`發現語句， `condition` 已進行測試。 如果 `condition` 為 `True` ，則 `Then` 會執行下列語句。 如果 `condition` 為 `False` ，則會依 `ElseIf` 序評估每個語句（如果有的話）。 找到時 `True` `elseifcondition` ，會執行緊接在相關聯的語句後面 `ElseIf` 。 如果沒有 `elseifcondition` 評估為 `True` ，或沒有任何 `ElseIf` 語句，則會執行下列語句 `Else` 。 執行、或之後的語句之後 `Then` `ElseIf` `Else` ，執行會繼續進行後面的語句 `End If` 。

`ElseIf`和 `Else` 子句都是選擇性的。 您可以 `ElseIf` 在 [ `If` ... `Then` ] 中擁有任意數目的子句。...`Else`語句，但 `ElseIf` 子句後面不能出現子句 `Else` 。 `If`...`Then`...`Else`語句可以在彼此之間嵌套。

在多行語法中， `If` 語句必須是第一行的唯一語句。 `ElseIf`、和語句的前面只能加上 `Else` `End If` 行標籤。 `If`... `Then`...`Else`區塊的結尾必須是 `End If` 語句。

> [!TIP]
> [[選取 ...]](select-case-statement.md)當您評估具有數個可能值的單一運算式時，Case 語句可能會更有用。

### <a name="single-line-syntax"></a>單行語法

若為 true，您可以將單行語法用於具有程式碼的單一條件來執行。 不過，多行語法提供更多的結構和彈性，且更容易讀取、維護和調試。

`Then`檢查關鍵字之後，判斷語句是否為單一行 `If` 。 如果批註以外的任何專案出現 `Then` 在同一行之後，則會將語句視為單行 `If` 語句。 如果 `Then` 不存在，它必須是多行 `If` `Then` 的開頭 .。。...`Else`.

在單行語法中，您可以將多個語句當做 `If` ... 決策的結果來執行。 `Then` 所有的語句都必須在同一行，並以冒號分隔。

## <a name="multiline-syntax-example"></a>多行語法範例

<a name="multi-line"></a>

下列範例說明如何使用的多行語法 `If` ... `Then`...`Else`句.

[!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a>嵌套語法範例

<a name="nested"></a>

下列範例包含 nested `If` ... `Then`...`Else`報表.

[!code-vb[VbVbalrStatements#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#102)]

## <a name="single-line-syntax-example"></a>單行語法範例

<a name="single-line"></a>下列範例說明如何使用單行語法。

[!code-vb[VbVbalrStatements#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#103)]

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- <xref:Microsoft.VisualBasic.Interaction.Switch%2A>
- [#If .。。Then ... #Else 指示詞](../directives/if-then-else-directives.md)
- [Select...Case 陳述式](select-case-statement.md)
- [巢狀控制結構](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [決策結構](../../programming-guide/language-features/control-flow/decision-structures.md)
- [Visual Basic 中的邏輯運算子和位元運算子](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [If 運算子](../operators/if-operator.md)
