---
title: Do...Loop 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Do
- vb.Loop
- vb.Until
helpviewer_keywords:
- conditional statements [Visual Basic], Do�Loop
- while statement [Visual Basic], Do...Loop
- execution [Visual Basic], conditional
- Do loops
- Until keyword [Visual Basic], Do...Loop statement
- Do...Loop statement
- instructions, repeating
- Do statement [Visual Basic]
- Exit statement [Visual Basic], in Do...Loop statements
- loop structures [Visual Basic], Do�Loop statements
- do-while statements [Visual Basic]
- loops, exiting
- Loop keyword [Visual Basic], Do...Loop statement
ms.assetid: 892f9096-b3e2-4aee-834d-83bc4e2c379d
ms.openlocfilehash: eff5239e07ca27f40ece5af68f46c491be91cf09
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583448"
---
# <a name="doloop-statement-visual-basic"></a>Do...Loop 陳述式 (Visual Basic)
當 `Boolean` 條件 `True` 或直到條件變成 `True` 時，重複語句區塊。  
  
## <a name="syntax"></a>語法  
  
```vb  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
' -or-  
Do  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop { While | Until } condition  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`Do`|必要項。 啟動 `Do` 迴圈的定義。|  
|`While`|除非使用 `Until`，否則為必要參數。 重複執行迴圈，直到 `False` `condition` 為止。|  
|`Until`|除非使用 `While`，否則為必要參數。 重複執行迴圈，直到 `True` `condition` 為止。|  
|`condition`|選擇項。 `Boolean` 運算式。 如果 `Nothing` `condition`，Visual Basic 會將它視為 `False`。|  
|`statements`|選擇項。 一或多個在 `condition` `True` 時重複的語句。|  
|`Continue Do`|選擇項。 將控制權轉移至 `Do` 迴圈的下一個反復專案。|  
|`Exit Do`|選擇項。 將控制權轉移 `Do` 迴圈。|  
|`Loop`|必要項。 結束 `Do` 迴圈的定義。|  
  
## <a name="remarks"></a>備註  
 當您想要重複一組不限次數的語句，直到滿足條件為止，請使用 `Do...Loop` 結構。 如果您想要重複語句[設定的次數，請將 .。。下一個語句](../../../visual-basic/language-reference/statements/for-next-statement.md)通常是較好的選擇。  
  
 您可以使用 `While` 或 `Until` 來指定 `condition`，而不是兩者。  
  
 您只能在迴圈的開頭或結尾測試一次 `condition`。 如果您在迴圈開始時測試 `condition` （在 `Do` 語句中），迴圈可能不會執行一次。 如果您在迴圈結尾（在 `Loop` 語句中）進行測試，迴圈一律至少會執行一次。  
  
 此條件的結果通常是兩個值的比較，但它可以是評估為[布林資料類型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)值（`True` 或 `False`）的任何運算式。 這包括已轉換成 `Boolean` 之其他資料類型（例如數數值型別）的值。  
  
 您可以藉由將一個迴圈放在另一個迴圈中，來將 `Do` 迴圈。 您也可以在彼此之間嵌套不同類型的控制結構。 如需詳細資訊，請參閱[嵌套控制項結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)。  
  
> [!NOTE]
> @No__t_0 結構提供比 While 更大的彈性 ... [End While 語句](../../../visual-basic/language-reference/statements/while-end-while-statement.md)，因為它可讓您決定在 `condition` 停止 `True` 或第一次變成 `True` 時，是否要結束迴圈。 它也可讓您測試迴圈開始或結束時的 `condition`。  
  
## <a name="exit-do"></a>Exit Do  
 [Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md)語句可以提供結束 `Do…Loop` 的替代方式。 `Exit Do` 會立即將控制權轉移到 `Loop` 語句後面的語句。  
  
 在評估某些條件（例如在 `If...Then...Else` 結構中）時，通常會使用 `Exit Do`。 如果您偵測到不必要或無法繼續反覆運算的條件（例如錯誤值或終止要求），您可能會想要結束迴圈。 @No__t_0 的其中一種用途是測試可能導致無止盡*迴圈*的條件，這是一種迴圈，可能會執行很長或無限次的次數。 您可以使用 `Exit Do` 來 escape 迴圈。  
  
 您可以在 `Do…Loop` 中的任何位置包含任意數目的 `Exit Do` 語句。  
  
 在嵌套 `Do` 迴圈中使用時，`Exit Do` 會將控制權從最內層的迴圈轉移到下一個較高層級的嵌套。  
  
## <a name="example"></a>範例  
 在下列範例中，迴圈中的語句會繼續執行，直到 `index` 變數大於10為止。 @No__t_0 子句位於迴圈的結尾。  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a>範例  
 下列範例會使用 `While` 子句，而不是 `Until` 子句，而且 `condition` 會在迴圈開始時進行測試，而不是在結尾處進行測試。  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a>範例  
 在下列範例中，當 `index` 變數大於100時，`condition` 停止迴圈。 不過，迴圈中的 `If` 語句會導致 `Exit Do` 語句在索引變數大於10時停止迴圈。  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a>範例  
 下列範例會讀取文字檔中的所有行。 @No__t_0 方法會開啟檔案，並傳回讀取字元的 <xref:System.IO.StreamReader>。 在 `Do...Loop` 條件中，`StreamReader` 的 <xref:System.IO.StreamReader.Peek%2A> 方法會決定是否有任何額外的字元。  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a>請參閱

- [迴圈結構](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Boolean 資料類型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [巢狀控制結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit 陳述式](../../../visual-basic/language-reference/statements/exit-statement.md)
- [While...End While 陳述式](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
