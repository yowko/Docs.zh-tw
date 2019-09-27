---
title: Select...Case 陳述式 (Visual Basic)
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
ms.openlocfilehash: 627318677270ba4ffa8ee430febea7ddf83bd245
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957650"
---
# <a name="selectcase-statement-visual-basic"></a>Select...Case 陳述式 (Visual Basic)
視運算式的值而定, 執行數個語句群組的其中一個。  
  
## <a name="syntax"></a>語法  
  
```  
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
|`testexpression`|必要項。 運算式. 必須評估為`Boolean`其中一個基本資料類型 (、 `Decimal` `Double` `Date` `Byte` `Char` 、、、`Long`、 、、`SByte`、、、、 、、、、、、、、、`Short` `Integer` `Object``Single`、 、`String` 、`ULong`和)。 `UInteger` `UShort`|  
|`expressionlist`|語句中的`Case`必要項。 表示之符合值的`testexpression`運算式子句清單。 多個運算式子句會以逗號分隔。 每個子句都可以採用下列其中一種形式:<br /><br /> -   *expression1* `To` *expression2*<br />-   [ `Is` ] *comparisonoperator* *expression*<br />-   *運算式*<br /><br /> 使用關鍵字來指定的相符`testexpression`值範圍的界限。 `To` 的值`expression1`必須小於或等於的`expression2`值。<br /><br /> `<` `<>` `<=`使用關鍵字搭配`>=`比較`=`運算子 (、、 `testexpression`、 、或)來指定的比對值限制。`>` `Is` 如果未提供關鍵字,則會在comparisonoperator之前自動`Is`插入。<br /><br /> 僅`expression`指定的表單會被視為`Is`表單的特殊案例, 其中*comparisonoperator*是等號 (`=`)。 這個表單會評估`testexpression`為 =  `expression`。<br /><br /> 中`expressionlist`的運算式可以是任何資料類型, 前提是它們會隱含地轉換成的`testexpression`類型, 而適當`comparisonoperator`的適用于搭配使用的兩個類型。|  
|`statements`|選擇性。 如果符合中`Case` `testexpression` 的任何`expressionlist`子句, 則在之後執行的一個或多個語句。|  
|`elsestatements`|選擇性。 如果`Case Else` 不`testexpression` 符合任何`Case`語句之中的任何子句, 則會在執行之後的一或多個語句。`expressionlist`|  
|`End Select`|結束的定義`Select`...`Case`結構。|  
  
## <a name="remarks"></a>備註  
 如果`testexpression`符合 any `Case` `End Select` `Case` `Case Else` `Case`子句, 則語句後面的語句會執行到下一個、或語句。 `expressionlist` 控制項接著會傳遞至後面`End Select`的語句。 如果`testexpression` 符合一個以上`Case`子句中的子句,則只會執行第一個相符專案之後的語句。`expressionlist`  
  
 如果`Case Else`在任何其他`elsestatements` `testexpression`語句的和`expressionlist`子句之間找不到相符項, 則會使用語句來導入要執行的。 `Case` 雖然並非必要, 但在您`Case Else` `Select Case`的結構中有語句來處理`testexpression`未預期的值是個不錯的主意。 如果沒有`Case` `expressionlist` `End Select`符合的子句,而且沒有語句,則控制權會傳遞至下列語句。`testexpression` `Case Else`  
  
 您可以在每個`Case`子句中使用多個運算式或範圍。 例如, 下列程式程式碼是有效的。  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
> 和`Case` `Is` 語句`Case Else`中所使用的關鍵字與[is 運算子](../../../visual-basic/language-reference/operators/is-operator.md)不同, 後者是用於物件參考比較。  
  
 您可以為字元字串指定範圍和多個運算式。 在下列範例中, `Case`會比對完全等於「蘋果」的任何字串、以字母順序表示「螺母」和「湯品」之間的值, 或包含與目前值完全相同的`testItem`值。  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 的設定`Option Compare`可能會影響字串比較。 在`Option Compare Text`下, 字串 "蘋果" 和 "蘋果" 比較為相等, 但在`Option Compare Binary`之下則不會。  
  
> [!NOTE]
> 具有`Case`多個子句的語句可以呈現稱為「最少運算」的行為。 Visual Basic 會從左至右評估子句, 而且如果其中一個會產生符合`testexpression`的, 則不會評估其餘的子句。 最短運算可以改善效能, 但如果您預期要評估中的`expressionlist`每個運算式, 可能會產生非預期的結果。 如需有關簡短運算的詳細資訊, 請參閱[布林運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)。  
  
 如果`Case` `Exit Select`或`Case Else`語句區塊內的程式碼不需要執行區塊中的任何其他語句, 它可以使用語句來結束區塊。 這會立即將控制權轉移給後面`End Select`的語句。  
  
 `Select Case`可以嵌套結構。 每個`Select Case`嵌套的結構都必須`End Select`有相符的語句, 而且必須完全包含`Case`在其所用之外部`Select Case`結構的單一或`Case Else`語句區塊內。  
  
## <a name="example"></a>範例  
 下列範例會使用`Select Case`結構來撰寫對應至變數`number`值的線條。 第二`Case`個語句包含符合目前`number`值的值, 因此會執行寫入「介於6和 8 (含)」的語句。  
  
 [!code-vb[VbVbalrStatements#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#54)]  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- [End 陳述式](../../../visual-basic/language-reference/statements/end-statement.md)
- [If...Then...Else 陳述式](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Option Compare 陳述式](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Exit 陳述式](../../../visual-basic/language-reference/statements/exit-statement.md)
