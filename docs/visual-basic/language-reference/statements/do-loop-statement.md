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
ms.openlocfilehash: 3ff3d67f38f510b798da3e470de066cff1e98f29
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638771"
---
# <a name="doloop-statement-visual-basic"></a>Do...Loop 陳述式 (Visual Basic)
重複出現時的陳述式區塊`Boolean`條件`True`或直到條件變成`True`。  
  
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
|`Do`|必要項。 定義的開頭`Do`迴圈。|  
|`While`|除非使用 `Until`，否則為必要參數。 重複此迴圈，直到`condition`是`False`。|  
|`Until`|除非使用 `While`，否則為必要參數。 重複此迴圈，直到`condition`是`True`。|  
|`condition`|選擇性。 `Boolean` 運算式。 如果`condition`已`Nothing`，Visual Basic 會將其視為`False`。|  
|`statements`|選擇性。 一或多個陳述式時，或直到，會重複`condition`是`True`。|  
|`Continue Do`|選擇性。 將控制權轉移到下一個反覆運算`Do`迴圈。|  
|`Exit Do`|選擇性。 控制權轉移共`Do`迴圈。|  
|`Loop`|必要項。 結束的定義`Do`迴圈。|  
  
## <a name="remarks"></a>備註  
 使用`Do...Loop`結構，當您想要重複執行一組陳述式的不限數目的次數，直到滿足條件。 如果您想要重複陳述式的次數，固定數目[For...下一個陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)通常是較好的選擇。  
  
 您可以使用`While`或是`Until`指定`condition`，但非兩者。  
  
 您可以測試`condition`一次，在開始或結束迴圈。 如果您在測試`condition`開頭的迴圈 (在`Do`陳述式)，迴圈可能不會執行甚至一次。 如果您在迴圈結束測試 (在`Loop`陳述式)，迴圈永遠執行至少一次。  
  
 條件通常的結果比較的兩個值，但它可以是任何運算式評估為[布林資料型別](../../../visual-basic/language-reference/data-types/boolean-data-type.md)值 (`True`或`False`)。 這包括的其他資料類型，例如數值類型，已轉換成值`Boolean`。  
  
 您可以巢狀`Do`放在另一個迴圈的迴圈。 您也可以巢狀不同種類的控制結構彼此。 如需詳細資訊，請參閱 <<c0> [ 巢狀控制結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)。  
  
> [!NOTE]
>  `Do...Loop`結構可讓您更大的彈性比[時...結束 While 陳述式](../../../visual-basic/language-reference/statements/while-end-while-statement.md)因為它可讓您決定是否要結束迴圈時`condition`會停止正在`True`或是當它首次變成`True`。 它也可讓您測試`condition`開頭或結尾的迴圈。  
  
## <a name="exit-do"></a>結束執行  
 [Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md)陳述式可以提供替代的方式，來結束`Do…Loop`。 `Exit Do` 立即將控制權傳輸至後面的陳述式`Loop`陳述式。  
  
 `Exit Do` 通常用於評估某項條件，例如在之後`If...Then...Else`結構。 您可能想要結束迴圈，如果偵測到的條件，就不需要或無法繼續反覆執行，例如錯誤的數值或終止要求。 其中一種用法`Exit Do`就是要測試的條件，可能會導致*永無止盡的迴圈*，即無法執行大型或甚至是無限次數的迴圈。 您可以使用`Exit Do`來逸出迴圈。  
  
 您可以包含任意數目的`Exit Do`任何一處陳述式中的`Do…Loop`。  
  
 使用時內巢狀`Do`迴圈，`Exit Do`控制權出最內層的迴圈並進入下一個較高的層級，巢狀。  
  
## <a name="example"></a>範例  
 下列範例中，在迴圈中的陳述式會繼續執行，直到`index`變數是否大於 10。 `Until`子句是在迴圈的結尾。  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a>範例  
 下列範例會使用`While`子句，而不是`Until`子句，和`condition`測試的迴圈，而不是結尾開頭。  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a>範例  
 在下列範例中，`condition`停止迴圈時`index`變數是否大於 100。 `If`陳述式在迴圈中，不過，會導致`Exit Do`索引變數大於 10 時停止迴圈的陳述式。  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a>範例  
 下列範例會讀取文字檔案中的所有行。 <xref:System.IO.File.OpenText%2A>方法會開啟檔案，並傳回<xref:System.IO.StreamReader>讀取字元。 在 `Do...Loop`條件<xref:System.IO.StreamReader.Peek%2A>方法`StreamReader`判斷是否有任何額外的字元。  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a>另請參閱

- [迴圈結構](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Boolean 資料類型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [巢狀控制結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit 陳述式](../../../visual-basic/language-reference/statements/exit-statement.md)
- [While...End While 陳述式](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
