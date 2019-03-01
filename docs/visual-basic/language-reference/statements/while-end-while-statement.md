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
ms.openlocfilehash: 269a4c0f069b3837959b04f8463f96e7c5d5fdf7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970138"
---
# <a name="whileend-while-statement-visual-basic"></a>While...End While 陳述式 (Visual Basic)
在執行一系列的陳述式，只要指定的條件是`True`。  
  
## <a name="syntax"></a>語法  
  
```  
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
|`condition`|必要項。 `Boolean` 運算式。 如果`condition`已`Nothing`，Visual Basic 會將其視為`False`。|  
|`statements`|選擇性。 一或多個陳述式的下列`While`，每次執行所在`condition`是`True`。|  
|`Continue While`|選擇性。 將控制權轉移到下一個反覆運算`While`區塊。|  
|`Exit While`|選擇性。 控制權轉移共`While`區塊。|  
|`End While`|必要項。 終止 `While` 區塊的定義。|  
  
## <a name="remarks"></a>備註  
 使用`While...End While`結構，當您想要重複執行一組陳述式的不限數目的次數，只要在條件仍`True`。 如果您想要更多的彈性，與您用來測試條件或何種結果測試它，您可能會偏好[執行...迴圈陳述式](../../../visual-basic/language-reference/statements/do-loop-statement.md)。 如果您想要重複陳述式的次數，固定數目[For...下一個陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)通常是較好的選擇。  
  
> [!NOTE]
>  `While`關鍵字也會在[執行...迴圈陳述式](../../../visual-basic/language-reference/statements/do-loop-statement.md)，則[Skip While 子句](../../../visual-basic/language-reference/queries/skip-while-clause.md)並[Take While 子句](../../../visual-basic/language-reference/queries/take-while-clause.md)。  
  
 如果`condition`已`True`，則所有的`statements`執行直到`End While`遇到陳述式。 控制然後返回`While`陳述式，和`condition`再次檢查。 如果`condition`仍然是`True`，程序會重複。 如果有`False`，控制傳遞到後面的陳述式`End While`陳述式。  
  
 `While`陳述式一律會檢查條件，再開始迴圈。 迴圈會繼續條件維持`True`。 如果`condition`是`False`時第一次，就會進入迴圈，它不會執行一次。  
  
 `condition`通常比較的兩個值，但它的結果可以是任何運算式，評估為[布林資料型別](../../../visual-basic/language-reference/data-types/boolean-data-type.md)值 (`True`或`False`)。 這個運算式可以包含其他資料類型，已轉換成數值類型，例如值`Boolean`。  
  
 您可以巢狀`While`加上另一個迴圈內的迴圈。 您也可以巢狀不同類型的另一個控制結構。 如需詳細資訊，請參閱 <<c0> [ 巢狀控制結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)。  
  
## <a name="exit-while"></a>結束時  
 [結束時](../../../visual-basic/language-reference/statements/exit-statement.md)陳述式可以提供另一種方式結束`While`迴圈。 `Exit While` 立即將控制權傳輸至後面的陳述式`End While`陳述式。  
  
 您通常會使用`Exit While`某些條件會評估之後 (例如，在`If...Then...Else`結構)。 您可能想要結束迴圈，如果偵測到的條件，就不需要或無法繼續反覆執行，例如錯誤的數值或終止要求。 您可以使用`Exit While`當您測試的條件，可能會導致*永無止盡的迴圈*，即無法執行極大或甚至是無限次數的迴圈。 您可以接著使用`Exit While`來逸出迴圈。  
  
 您可以將任意數目的放`Exit While`任何一處陳述式中的`While`迴圈。  
  
 使用時內巢狀`While`迴圈，`Exit While`控制權出最內層的迴圈並進入下一個較高的層級，巢狀。  
  
 `Continue While`陳述式立即將控制權轉移到迴圈的下一個反覆項目。 如需詳細資訊，請參閱 < [Continue 陳述式](../../../visual-basic/language-reference/statements/continue-statement.md)。  
  
## <a name="example"></a>範例  
 下列範例中，在迴圈中的陳述式會繼續執行，直到`index`變數是否大於 10。  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a>範例  
 下列範例示範如何將`Continue While`和`Exit While`陳述式。  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a>範例  
 下列範例會讀取文字檔案中的所有行。 <xref:System.IO.File.OpenText%2A>方法會開啟檔案，並傳回<xref:System.IO.StreamReader>讀取字元。 在 `While`條件<xref:System.IO.StreamReader.Peek%2A>方法`StreamReader`判斷檔案是否包含額外的字元。  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a>另請參閱
- [迴圈結構](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Do...Loop 陳述式](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Boolean 資料類型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [巢狀控制結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit 陳述式](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Continue 陳述式](../../../visual-basic/language-reference/statements/continue-statement.md)
