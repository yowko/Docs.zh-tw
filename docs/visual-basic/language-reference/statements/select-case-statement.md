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
ms.openlocfilehash: f99db4f1dc224e5f75ee67ba94c3745f28438724
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783886"
---
# <a name="selectcase-statement-visual-basic"></a>Select...Case 陳述式 (Visual Basic)
執行其中一個陳述式、 運算式的值而定的數個群組。  
  
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
|`testexpression`|必要項。 運算式。 必須評估為其中一個基礎資料類型 (`Boolean`， `Byte`， `Char`， `Date`， `Double`， `Decimal`， `Integer`， `Long`， `Object`， `SByte`， `Short`，`Single`， `String`， `UInteger`， `ULong`，和`UShort`)。|  
|`expressionlist`|需要`Case`陳述式。 代表相符項目值的運算式子句的清單`testexpression`。 以逗號分隔多個運算式子句。 每個子句可以採用下列格式之一：<br /><br /> -   *expression1* `To` *expression2*<br />-   [ `Is` ] *comparisonoperator* *expression*<br />-   *expression*<br /><br /> 使用`To`關鍵字來指定比對之範圍的界限值`testexpression`。 值`expression1`必須是小於或等於值`expression2`。<br /><br /> 使用`Is`關鍵字搭配比較運算子 (`=`， `<>`， `<`， `<=`， `>`，或`>=`) 來比對值的指定限制`testexpression`。 如果`Is`不會提供關鍵字，它會自動插入之前*關係運算子*。<br /><br /> 只有指定的表單`expression`的特殊案例會被視為`Is`形成 where*關係運算子*為等號 (`=`)。 此表單會評估為`testexpression`  =  `expression`。<br /><br /> 中的運算式`expressionlist`可以是任何資料類型，前提是它們隱含地轉換成的型別`testexpression`適當`comparisonoperator`適用於兩種類型搭配使用它。|  
|`statements`|選擇性。 一或多個陳述式的下列`Case`，執行的如果`testexpression`比對中的任何子句`expressionlist`。|  
|`elsestatements`|選擇性。 一或多個陳述式的下列`Case Else`，執行的如果`testexpression`不符中的任何子句`expressionlist`任一`Case`陳述式。|  
|`End Select`|結束的定義`Select`...`Case`建構。|  
  
## <a name="remarks"></a>備註  
 如果`testexpression`符合任何`Case``expressionlist`子句，後面的陳述式`Case`陳述式執行至下一個`Case`， `Case Else`，或`End Select`陳述式。 然後會將控制權傳遞給之後的陳述式`End Select`。 如果`testexpression`符合`expressionlist`中一個以上的子句`Case`子句中，遵循第一個相符項目陳述式執行。  
  
 `Case Else`陳述式用來介紹`elsestatements`執行，如果沒有相符`testexpression`並`expressionlist`子句中任何其他`Case`陳述式。 雖然並非必要，它會是個不錯的主意，能夠`Case Else`陳述式，在您`Select Case`建構來處理無法預見`testexpression`值。 如果沒有`Case``expressionlist`子句與相符`testexpression`且沒有任何`Case Else`陳述式之後的陳述式來控制傳遞`End Select`。  
  
 您可以使用多個運算式或範圍中每個`Case`子句。 例如下, 面這一行是有效的。  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
>  `Is`中所使用的關鍵字`Case`並`Case Else`陳述式不是相同[Is 運算子](../../../visual-basic/language-reference/operators/is-operator.md)，它用於物件參考的比較。  
  
 您可以指定範圍和字元字串的多個運算式。 在下列範例中，`Case`比對任何字串，是完全等於"apples"、"nuts 」 和 「 詳細 」 之間的值依字母順序，或包含與目前的值完全相同的值`testItem`。  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 設定`Option Compare`可能會影響字串比較。 底下`Option Compare Text`，"Apples"和"apples"字串比較為相等，但下`Option Compare Binary`，不相符。  
  
> [!NOTE]
>  A`Case`具有多個子句的陳述式可以表現所謂*最少運算*。 Visual Basic 會評估從左到右的子句，和如果有一個會產生符合`testexpression`，不會評估其餘的子句。 最少運算可改善效能，但它可以產生非預期的結果，如果您預期中的每個運算式`expressionlist`評估。 如需有關最少運算的詳細資訊，請參閱[布林運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)。  
  
 如果中的程式碼`Case`或是`Case Else`陳述式區塊就不需要執行區塊中的 更多的陳述式，它可以使用，以結束區塊`Exit Select`陳述式。 此控制項將立即轉移到之後的陳述式`End Select`。  
  
 `Select Case` 可以是巢狀建構。 每個巢狀`Select Case`建構必須具有相符`End Select`陳述式，必須完全包含在單一`Case`或`Case Else`陳述式區塊外部`Select Case`巢狀所在的建構。  
  
## <a name="example"></a>範例  
 下列範例會使用`Select Case`建構來撰寫對應到變數的值行`number`。 第二個`Case`陳述式包含符合目前的值的值`number`，因此 「 介於 6 和 8，內含 「 寫入陳述式執行。  
  
 [!code-vb[VbVbalrStatements#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#54)]  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- [End 陳述式](../../../visual-basic/language-reference/statements/end-statement.md)
- [If...Then...Else 陳述式](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Option Compare 陳述式](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Exit 陳述式](../../../visual-basic/language-reference/statements/exit-statement.md)
