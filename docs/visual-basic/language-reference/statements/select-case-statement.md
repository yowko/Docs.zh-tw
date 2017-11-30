---
title: "Select...Case 陳述式 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a7527763a05ec32af88c6ba66ef717d839c33154
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="selectcase-statement-visual-basic"></a>Select...Case 陳述式 (Visual Basic)
執行其中一個陳述式中，運算式的值而定的數個群組。  
  
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
|`testexpression`|必要項。 運算式。 必須評估為其中一種基本資料類型 (`Boolean`， `Byte`， `Char`， `Date`， `Double`， `Decimal`， `Integer`， `Long`， `Object`， `SByte`， `Short`，`Single`， `String`， `UInteger`， `ULong`，和`UShort`)。|  
|`expressionlist`|中需要`Case`陳述式。 代表比對值運算式子句的清單`testexpression`。 多個運算式子句會以逗號分隔。 每個子句可以採用下列格式之一：<br /><br /> -   *expression1* `To` *expression2*<br />-[ `Is` ]*關係運算子**運算式*<br />-   *運算式*<br /><br /> 使用`To`關鍵字來指定比對的範圍界限值`testexpression`。 值`expression1`必須小於或等於值`expression2`。<br /><br /> 使用`Is`關鍵字搭配比較運算子 (`=`， `<>`， `<`， `<=`， `>`，或`>=`) 來比對值的指定限制`testexpression`。 如果`Is`關鍵字未提供，它會自動插入之前*關係運算子*。<br /><br /> 只指定表單`expression`的特殊案例會被視為`Is`形成 where*關係運算子*為等號 (`=`)。 此表單會評估為`testexpression`  =  `expression`。<br /><br /> 中的運算式`expressionlist`可以是任何資料類型，提供可以隱含地轉換成的型別`testexpression`和適當`comparisonoperator`適用於兩種類型與正在使用它。|  
|`statements`|選擇項。 一或多個陳述式下列`Case`，執行的如果`testexpression`符合中的任何子句`expressionlist`。|  
|`elsestatements`|選擇項。 一或多個陳述式下列`Case Else`，執行的如果`testexpression`不相符在任何子句`expressionlist`其中任一`Case`陳述式。|  
|`End Select`|結束的定義`Select`...`Case`建構。|  
  
## <a name="remarks"></a>備註  
 如果`testexpression`符合任何`Case``expressionlist`子句，陳述式，`Case`陳述式執行到下`Case`， `Case Else`，或`End Select`陳述式。 然後會將控制權傳遞給之後的陳述式`End Select`。 如果`testexpression`符合`expressionlist`中多個子句`Case`子句之後的第一個符合的陳述式執行。  
  
 `Case Else`陳述式用於介紹`elsestatements`執行，如果沒有找到符合的之間`testexpression`和`expressionlist`中任何其他子句`Case`陳述式。 雖然並非必要，最好在其中具有`Case Else`陳述式中的您`Select Case`建構來處理無法預料`testexpression`值。 如果沒有`Case``expressionlist`子句符合`testexpression`，而且沒有任何`Case Else`陳述式之後的陳述式來控制傳遞`End Select`。  
  
 您可以使用多個運算式或範圍中每個`Case`子句。 例如下, 面是有效的。  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
>  `Is`關鍵字用於`Case`和`Case Else`陳述式不是相同[Is 運算子](../../../visual-basic/language-reference/operators/is-operator.md)，用於物件參考比較。  
  
 您可以指定範圍和多個運算式的字元字串。 在下列範例中，`Case`比對任何字串完全等於 「 蘋果 」、 「 nuts"和"soup 」 之間的值依字母順序，或包含目前的值完全相同的值`testItem`。  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 設定`Option Compare`可能會影響字串比較。 在下`Option Compare Text`，「 蘋果 」 和 「 蘋果 」 的字串比較結果為相等，但在`Option Compare Binary`，不相符。  
  
> [!NOTE]
>  A`Case`展現具有多個子句的陳述式的行為稱為*最少運算*。 Visual Basic 評估從左到右的子句，和如果有一個會產生相符`testexpression`，不會評估其餘的子句。 最少運算可改善效能，但它可以產生非預期的結果，如果您預期會在每個運算式`expressionlist`進行評估。 如需最少運算的詳細資訊，請參閱[布林運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)。  
  
 如果中的程式碼`Case`或`Case Else`陳述式區塊就不需要執行更多的陳述式區塊中，它可以使用結束區塊`Exit Select`陳述式。 這將控制項傳送立即之後的陳述式`End Select`。  
  
 `Select Case`語法結構，可以是巢狀。 每個巢狀`Select Case`建構必須具有相符`End Select`陳述式，而且必須完全包含在單一`Case`或`Case Else`陳述式區塊外部`Select Case`建構巢狀內。  
  
## <a name="example"></a>範例  
 下列範例會使用`Select Case`建構來寫入變數的值對應的行`number`。 第二個`Case`陳述式包含的值符合目前的值， `number`，因此陳述式會將寫入 「 介於 6 和 8 （含) 」 執行。  
  
 [!code-vb[VbVbalrStatements#54](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/select-case-statement_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.Interaction.Choose%2A>  
 [End 陳述式](../../../visual-basic/language-reference/statements/end-statement.md)  
 [If...Then...Else 陳述式](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [Option Compare 陳述式](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [Exit 陳述式](../../../visual-basic/language-reference/statements/exit-statement.md)
