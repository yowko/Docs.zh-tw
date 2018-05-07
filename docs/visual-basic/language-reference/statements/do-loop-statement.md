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
ms.openlocfilehash: e12cdc1ae405b877d4d27d1947c98dcb51938ba7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="doloop-statement-visual-basic"></a>Do...Loop 陳述式 (Visual Basic)
持續重複陳述式時區塊`Boolean`條件是`True`或直到條件變成`True`。  
  
## <a name="syntax"></a>語法  
  
```  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
-or-  
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
|`Do`|必要。 定義的開頭`Do`迴圈。|  
|`While`|除非使用 `Until`，否則為必要參數。 重複此迴圈直到`condition`是`False`。|  
|`Until`|除非使用 `While`，否則為必要參數。 重複此迴圈直到`condition`是`True`。|  
|`condition`|選擇性。 `Boolean` 運算式。 如果`condition`是`Nothing`，Visual Basic 會將它視為`False`。|  
|`statements`|選擇性。 一或多個陳述式時，或直到，重複的`condition`是`True`。|  
|`Continue Do`|選擇性。 將控制項傳送至下一個反覆運算`Do`迴圈。|  
|`Exit Do`|選擇性。 控制權轉移出`Do`迴圈。|  
|`Loop`|必要。 結束的定義`Do`迴圈。|  
  
## <a name="remarks"></a>備註  
 使用`Do...Loop`結構時您想要重複一組不定陳述式的次數，直到滿足條件為止。 如果您想要重複陳述式的次數， [For...下一個陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)通常是比較好的選擇。  
  
 您可以使用`While`或`Until`指定`condition`，但非兩者。  
  
 您可以測試`condition`僅一次，開頭或結尾的迴圈。 如果您在測試`condition`迴圈的開頭 (在`Do`陳述式)，在迴圈執行可能甚至一次。 如果您在迴圈結束測試 (在`Loop`陳述式)，迴圈永遠執行至少一次。  
  
 條件通常來自兩個值的比較，但它可以是任何運算式評估為[布林資料型別](../../../visual-basic/language-reference/data-types/boolean-data-type.md)值 (`True`或`False`)。 這包括其他資料類型，例如的已轉換成數值類型的值`Boolean`。  
  
 您可以巢狀`Do`將放入另一個迴圈內的迴圈。 您也可以巢狀不同類型的其他控制結構。 如需詳細資訊，請參閱[巢狀控制結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)。  
  
> [!NOTE]
>  `Do...Loop`結構可讓您更大的彈性比[時...結束 While 陳述式](../../../visual-basic/language-reference/statements/while-end-while-statement.md)因為它可讓您決定是否要結束迴圈時`condition`停止`True`或當它第一次變成`True`。 它也可讓您測試`condition`開頭或結尾的迴圈。  
  
## <a name="exit-do"></a>結束執行  
 [結束執行](../../../visual-basic/language-reference/statements/exit-statement.md)陳述式可以提供替代方式，以結束`Do…Loop`。 `Exit Do` 立即將控制權傳輸至之後的陳述式`Loop`陳述式。  
  
 `Exit Do` 通常是評估某項條件，例如在之後`If...Then...Else`結構。 您可能想要結束迴圈，若您偵測到的條件，使得不必要或不可能繼續重複執行，例如錯誤的數值或終止要求。 使用一`Exit Do`就是要測試的條件，可能會導致*無止盡迴圈*，即無法執行大型或甚至無限次數的迴圈。 您可以使用`Exit Do`來逸出迴圈。  
  
 您可以包含任意數目的`Exit Do`隨處陳述式中的`Do…Loop`。  
  
 使用時內巢狀`Do`迴圈`Exit Do`控制權從最內層的迴圈移至下一個高的層級的巢狀結構。  
  
## <a name="example"></a>範例  
 在下列範例中，在迴圈中的陳述式繼續執行直到`index`變數值大於 10。 `Until`子句是在迴圈的結尾。  
  
 [!code-vb[VbVbalrStatements#131](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_1.vb)]  
  
## <a name="example"></a>範例  
 下列範例會使用`While`子句，而不要`Until`子句，和`condition`測試的迴圈，而不是結尾的開頭。  
  
 [!code-vb[VbVbalrStatements#132](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_2.vb)]  
  
## <a name="example"></a>範例  
 在下列範例中，`condition`停止迴圈時`index`變數大於 100。 `If`陳述式在迴圈中，不過，會導致`Exit Do`陳述式來索引變數大於 10 時停止迴圈。  
  
 [!code-vb[VbVbalrStatements#133](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_3.vb)]  
  
## <a name="example"></a>範例  
 下列範例會讀取文字檔案中的所有行。 <xref:System.IO.File.OpenText%2A>方法開啟的檔案，並傳回<xref:System.IO.StreamReader>讀取的字元。 在`Do...Loop`條件，<xref:System.IO.StreamReader.Peek%2A>方法`StreamReader`判斷是否有任何額外的字元。  
  
 [!code-vb[VbVbalrStatements#134](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_4.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [迴圈結構](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Boolean 資料類型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)  
 [巢狀控制結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Exit 陳述式](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [While...End While 陳述式](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
