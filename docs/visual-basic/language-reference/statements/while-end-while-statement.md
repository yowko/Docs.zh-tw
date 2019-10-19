---
title: While...End While 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.While
- vb.While...EndWhile
helpviewer_keywords:
- While statement [Visual Basic], While...End While
- While statement [Visual Basic]
- While...End While statements [Visual Basic]
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
ms.openlocfilehash: 5da05835998b2e9ef9aeefe5b00faf9e1ecb9ce2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582263"
---
# <a name="whileend-while-statement-visual-basic"></a>While...End While 陳述式 (Visual Basic)
只要指定的條件為 `True`，就會執行一系列的語句。  
  
## <a name="syntax"></a>語法  
  
```vb  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`condition`|必要項。 `Boolean` 運算式。 如果 `Nothing` `condition`，Visual Basic 會將它視為 `False`。|  
|`statements`|選擇項。 @No__t_0 後面的一或多個語句，會在每次 `True` `condition` 時執行。|  
|`Continue While`|選擇項。 將控制權轉移至 `While` 區塊的下一個反復專案。|  
|`Exit While`|選擇項。 將控制權轉移出 `While` 區塊。|  
|`End While`|必要項。 終止 `While` 區塊的定義。|  
  
## <a name="remarks"></a>備註  
 當您想要重複一組不限次數的語句時（只要條件仍然 `True`，請使用 `While...End While` 結構）。 如果您想要在測試條件的位置或測試它的結果時擁有更大的彈性，您可能會想[要 .。。Loop 語句](../../../visual-basic/language-reference/statements/do-loop-statement.md)。 如果您想要重複語句[設定的次數，請將 .。。下一個語句](../../../visual-basic/language-reference/statements/for-next-statement.md)通常是較好的選擇。  
  
> [!NOTE]
> @No__t_0 關鍵字也會[用於 .。。Loop 語句](../../../visual-basic/language-reference/statements/do-loop-statement.md)、 [Skip while 子句](../../../visual-basic/language-reference/queries/skip-while-clause.md)和[Take While 子句](../../../visual-basic/language-reference/queries/take-while-clause.md)。  
  
 如果 `True` `condition`，所有 `statements` 都會執行，直到遇到 `End While` 語句為止。 控制項接著會回到 `While` 語句，然後再次檢查 `condition`。 如果仍然 `True` `condition`，則會重複處理常式。 如果 `False`，控制權會傳遞給在 `End While` 語句之後的語句。  
  
 @No__t_0 語句在啟動迴圈之前，一律會檢查條件。 當條件保持 `True` 時，迴圈就會繼續進行。 如果您在第一次進入迴圈時 `False` `condition`，它甚至不會執行一次。  
  
 @No__t_0 通常是由兩個值的比較所產生，但它可以是任何會評估為[布林資料類型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)值（`True` 或 `False`）的運算式。 這個運算式可以包含另一個資料類型的值，例如已轉換成 `Boolean` 的數數值型別。  
  
 您可以藉由將一個迴圈放在另一個迴圈中，來將 `While` 迴圈。 您也可以將不同種類的控制結構嵌套在另一種。 如需詳細資訊，請參閱[嵌套控制項結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)。  
  
## <a name="exit-while"></a>結束  
 [Exit While](../../../visual-basic/language-reference/statements/exit-statement.md)語句可以提供結束 `While` 迴圈的另一種方式。 `Exit While` 會立即將控制權轉移至 `End While` 語句後面的語句。  
  
 在評估某些條件（例如，在 `If...Then...Else` 結構中）之後，通常會使用 `Exit While`。 如果您偵測到不必要或無法繼續反覆運算的條件（例如錯誤值或終止要求），您可能會想要結束迴圈。 當您測試的條件可能會造成無止盡的*迴圈*時，您可以使用 `Exit While`，這是一種迴圈，可以執行極大或甚至無限的次數。 然後，您可以使用 `Exit While` 來對迴圈進行 escape。  
  
 您可以將任意數目的 `Exit While` 語句放在 `While` 迴圈中的任何位置。  
  
 在嵌套 `While` 迴圈中使用時，`Exit While` 會將控制權從最內層的迴圈轉移到下一個較高層級的嵌套。  
  
 @No__t_0 語句會立即將控制權轉移到迴圈的下一個反復專案。 如需詳細資訊，請參閱[Continue 語句](../../../visual-basic/language-reference/statements/continue-statement.md)。  
  
## <a name="example"></a>範例  
 在下列範例中，迴圈中的語句會繼續執行，直到 `index` 變數大於10為止。  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a>範例  
 下列範例說明如何使用 `Continue While` 和 `Exit While` 語句。  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a>範例  
 下列範例會讀取文字檔中的所有行。 @No__t_0 方法會開啟檔案，並傳回讀取字元的 <xref:System.IO.StreamReader>。 在 `While` 條件中，`StreamReader` 的 <xref:System.IO.StreamReader.Peek%2A> 方法會判斷檔案是否包含額外的字元。  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a>請參閱

- [迴圈結構](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Do...Loop 陳述式](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Boolean 資料類型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [巢狀控制結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit 陳述式](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Continue 陳述式](../../../visual-basic/language-reference/statements/continue-statement.md)
