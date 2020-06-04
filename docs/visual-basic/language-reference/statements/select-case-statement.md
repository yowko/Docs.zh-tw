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
ms.openlocfilehash: 3dedd43f920b493a0aca9ce48460b00815e1af5c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404235"
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
|`testexpression`|必要。 運算式。 必須評估為其中一個基本資料類型（、、、、、、、、、、、、、、 `Boolean` `Byte` `Char` `Date` `Double` `Decimal` `Integer` `Long` `Object` `SByte` `Short` `Single` `String` `UInteger` `ULong` 和 `UShort` ）。|  
|`expressionlist`|語句中的必要項 `Case` 。 表示之符合值的運算式子句清單 `testexpression` 。 多個運算式子句會以逗號分隔。 每個子句都可以採用下列其中一種形式：<br /><br /> -   *運算式* `To`*運算式*2<br />-[ `Is` ] *comparisonoperator* *運算式*<br />-   *運算式*<br /><br /> 使用 `To` 關鍵字來指定的相符值範圍的界限 `testexpression` 。 的值 `expression1` 必須小於或等於的值 `expression2` 。<br /><br /> 使用 `Is` 關鍵字搭配比較運算子（ `=` 、 `<>` 、、、 `<` `<=` `>` 或 `>=` ）來指定的比對值限制 `testexpression` 。 如果 `Is` 未提供關鍵字，則會在*comparisonoperator*之前自動插入。<br /><br /> 僅指定的表單 `expression` 會被視為表單的特殊案例， `Is` 其中*comparisonoperator*是等號（ `=` ）。 這個表單會評估為 `testexpression`  =  `expression` 。<br /><br /> 中的運算式 `expressionlist` 可以是任何資料類型，前提是它們會隱含地轉換成的類型， `testexpression` 而適當的適用 `comparisonoperator` 于搭配使用的兩個類型。|  
|`statements`|選擇性。 `Case`如果 `testexpression` 符合中的任何子句，則在之後執行的一個或多個語句 `expressionlist` 。|  
|`elsestatements`|選擇性。 `Case Else`如果 `testexpression` 不符合任何語句之中的任何子句，則會在執行之後的一或多個語句 `expressionlist` `Case` 。|  
|`End Select`|終止 `Select` ... 結構的定義。 `Case`|  
  
## <a name="remarks"></a>備註  
 如果 `testexpression` 符合 any `Case` `expressionlist` 子句，則語句後面的語句會 `Case` 執行到下一個 `Case` 、 `Case Else` 或 `End Select` 語句。 控制項接著會傳遞至後面的語句 `End Select` 。 如果 `testexpression` 符合一個 `expressionlist` 以上子句中的子句 `Case` ，則只會執行第一個相符專案之後的語句。  
  
 `Case Else` `elsestatements` 如果在 `testexpression` `expressionlist` 任何其他語句的和子句之間找不到相符項，則會使用語句來導入要執行的 `Case` 。 雖然並非必要，但在 `Case Else` 您的結構中有語句來處理未預期的值是個不錯的主意 `Select Case` `testexpression` 。 如果沒有 `Case` `expressionlist` 符合的子句 `testexpression` ，而且沒有 `Case Else` 語句，則控制權會傳遞至下列語句 `End Select` 。  
  
 您可以在每個子句中使用多個運算式或範圍 `Case` 。 例如，下列程式程式碼是有效的。  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
> `Is`和語句中所使用的關鍵字與 `Case` `Case Else` [is 運算子](../operators/is-operator.md)不同，後者是用於物件參考比較。  
  
 您可以為字元字串指定範圍和多個運算式。 在下列範例中， `Case` 會比對完全等於「蘋果」的任何字串、以字母順序表示「螺母」和「湯品」之間的值，或包含與目前值完全相同的值 `testItem` 。  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 的設定 `Option Compare` 可能會影響字串比較。 在下 `Option Compare Text` ，字串 "蘋果" 和 "蘋果" 比較為相等，但在之下則 `Option Compare Binary` 不會。  
  
> [!NOTE]
> `Case`具有多個子句的語句可以呈現稱為「最少運算 *」的*行為。 Visual Basic 會從左至右評估子句，而且如果其中一個會產生符合的 `testexpression` ，則不會評估其餘的子句。 最短運算可以改善效能，但如果您預期要評估中的每個運算式，可能會產生非預期的結果 `expressionlist` 。 如需有關簡短運算的詳細資訊，請參閱[布林運算式](../../programming-guide/language-features/operators-and-expressions/boolean-expressions.md)。  
  
 如果或語句區塊內的程式碼 `Case` `Case Else` 不需要執行區塊中的任何其他語句，它可以使用語句來結束區塊 `Exit Select` 。 這會立即將控制權轉移給後面的語句 `End Select` 。  
  
 `Select Case`可以嵌套結構。 每個嵌套 `Select Case` 的結構都必須有相符的 `End Select` 語句，而且必須完全包含 `Case` 在 `Case Else` `Select Case` 其所用之外部結構的單一或語句區塊內。  
  
## <a name="example"></a>範例  
 下列範例會使用 `Select Case` 結構來撰寫對應至變數值的線條 `number` 。 第二個 `Case` 語句包含符合目前值的值 `number` ，因此會執行寫入「介於6和8（含）」的語句。  
  
 [!code-vb[VbVbalrStatements#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#54)]  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- [End 語句](end-statement.md)
- [If...Then...Else 陳述式](if-then-else-statement.md)
- [Option Compare 陳述式](option-compare-statement.md)
- [Exit 陳述式](exit-statement.md)
