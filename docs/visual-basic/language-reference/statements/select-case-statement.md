---
title: Select...Case 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.Select
- vb.Case
helpviewer_keywords:
- Select statement [Visual Basic]
- Case statement [Visual Basic]
- Select...Case statements
- conditional statements [Visual Basic], Select Case
- control flow [Visual Basic], branching
- Else keyword [Visual Basic], in Select...Case statements
- execution [Visual Basic], conditional
- To keyword [Visual Basic], in Select...Case statements
- Select Case statement [Visual Basic], Select...Case
- Select statement [Visual Basic], Select...Case
- Is operator [Visual Basic], in Select...Case statements
- branching [Visual Basic], conditional
- Case Else statement [Visual Basic], Select...Case
- End keyword [Visual Basic], Select Case statements
- Case statement [Visual Basic], Select...Case
ms.assetid: 68877b65-5419-4bf0-a465-20cd0e4c7d44
ms.openlocfilehash: 4dddfe5fbf7092c911291ffc6841e76f8c2748e9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352820"
---
# <a name="selectcase-statement-visual-basic"></a>Select...Case 陳述式 (Visual Basic)
視運算式的值而定，執行數個語句群組的其中一個。  
  
## <a name="syntax"></a>語法  
  
```vb  
Select [ Case ] testexpression  
    [ Case expressionlist  
        [ statements ] ]  
    [ Case Else  
        [ elsestatements ] ]  
End Select  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`testexpression`|必要。 運算式. 必須評估為其中一個基本資料類型（`Boolean`、`Byte`、`Char`、`Date`、`Double`、`Decimal`、`Integer`、`Long`、`Object`、`SByte`、`Short`、`Single`、`String`、`UInteger`、`ULong`和 `UShort`）。|  
|`expressionlist`|在 `Case` 語句中為必要項。 表示 `testexpression`之相符值的運算式子句清單。 多個運算式子句會以逗號分隔。 每個子句都可以採用下列其中一種形式：<br /><br /> -   *運算式*2 `To`*運算式*2<br />-[`Is`] *comparisonoperator* *運算式*<br />-   *運算式*<br /><br /> 請使用 `To` 關鍵字來指定 `testexpression`範圍的相符值界限。 `expression1` 的值必須小於或等於 `expression2`的值。<br /><br /> 使用 `Is` 關鍵字搭配比較運算子（`=`、`<>`、`<`、`<=`、`>`或 `>=`）來指定 `testexpression`的比對值限制。 如果未提供 `Is` 關鍵字，則會在*comparisonoperator*之前自動插入。<br /><br /> 僅指定 `expression` 的表單會被視為 `Is` 格式的特殊案例，其中*comparisonoperator*是等號（`=`）。 此表單會評估為 `testexpression` = `expression`。<br /><br /> `expressionlist` 中的運算式可以是任何資料類型，前提是它們會隱含地轉換成 `testexpression` 的類型，而適當的 `comparisonoperator` 適用于其所使用的兩個類型。|  
|`statements`|選擇性。 如果 `testexpression` 符合 `expressionlist`中的任何子句，則會在執行 `Case` 之後的一或多個語句。|  
|`elsestatements`|選擇性。 如果 `testexpression` 不符合任何 `Case` 語句的 `expressionlist` 中的任何子句，則會在執行 `Case Else` 之後的一或多個語句。|  
|`End Select`|結束 `Select`...`Case` 結構的定義。|  
  
## <a name="remarks"></a>備註  
 如果 `testexpression` 符合任何 `Case` `expressionlist` 子句，則在該 `Case` 語句之後的語句會執行到下一個 `Case`、`Case Else`或 `End Select` 語句。 控制項接著會傳遞至 `End Select`後面的語句。 如果 `testexpression` 符合一個以上 `Case` 子句中的 `expressionlist` 子句，則只會執行第一個相符專案之後的語句。  
  
 如果在 `testexpression` 與 `expressionlist` 子句之間找不到任何其他 `Case` 語句中的相符項，則會使用 `Case Else` 語句來引入要執行的 `elsestatements`。 雖然並非必要，但在您的 `Select Case` 結構中有 `Case Else` 語句，以處理未預期的 `testexpression` 值是個不錯的主意。 如果沒有 `Case` `expressionlist` 子句符合 `testexpression` 而且沒有 `Case Else` 語句，則控制權會傳遞給下列 `End Select`後面的語句。  
  
 您可以在每個 `Case` 子句中使用多個運算式或範圍。 例如，下列程式程式碼是有效的。  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
> `Case` 和 `Case Else` 語句中所使用的 `Is` 關鍵字與[Is 運算子](../../../visual-basic/language-reference/operators/is-operator.md)不同，後者是用於物件參考比較。  
  
 您可以為字元字串指定範圍和多個運算式。 在下列範例中，`Case` 符合完全等於 "蘋果" 的任何字串、具有字母順序的「螺母」和「湯品」之間的值，或包含與目前 `testItem`的值完全相同的值。  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 `Option Compare` 的設定可能會影響字串比較。 在 `Option Compare Text`之下，"蘋果" 和 "蘋果" 的字串比較為相等，但在 `Option Compare Binary`之下則不會。  
  
> [!NOTE]
> 具有多個子句的 `Case` 語句，可以呈現稱為「最少運算 *」的行為。* Visual Basic 會從左至右評估子句，而且如果其中一個會產生與 `testexpression`的相符項，則不會評估其餘的子句。 最少運算可以改善效能，但如果您預期要評估 `expressionlist` 中的每個運算式，可能會產生非預期的結果。 如需有關簡短運算的詳細資訊，請參閱[布林運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)。  
  
 如果 `Case` 或 `Case Else` 語句區塊內的程式碼不需要執行區塊中的任何其他語句，則可以使用 `Exit Select` 語句來結束區塊。 這會立即將控制權轉移至 `End Select`後面的語句。  
  
 `Select Case` 的結構可以嵌套。 每個嵌套 `Select Case` 結構都必須有相符的 `End Select` 語句，而且必須完全包含在其所用的外部 `Select Case` 結構內的單一 `Case` 或 `Case Else` 語句區塊內。  
  
## <a name="example"></a>範例  
 下列範例會使用 `Select Case` 結構，撰寫對應于變數 `number`值的一行。 第二個 `Case` 語句包含符合目前 `number`值的值，因此會執行寫入「介於6和8（含）」的語句。  
  
 [!code-vb[VbVbalrStatements#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#54)]  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- [End 陳述式](../../../visual-basic/language-reference/statements/end-statement.md)
- [If...Then...Else 陳述式](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Option Compare 陳述式](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Exit 陳述式](../../../visual-basic/language-reference/statements/exit-statement.md)
