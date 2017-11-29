---
title: "While...End While 陳述式 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.While
- vb.While...EndWhile
helpviewer_keywords:
- While statement [Visual Basic], While...End While
- While statement [Visual Basic]
- While...End While statements [Visual Basic]
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5f831f233eaa4f1c38d56f3a89bda9b0cf1bccaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="whileend-while-statement-visual-basic"></a>While...End While 陳述式 (Visual Basic)
執行一系列的陳述式，只要指定的條件為`True`。  
  
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
|`condition`|必要項。 `Boolean`運算式。 如果`condition`是`Nothing`，Visual Basic 會將它視為`False`。|  
|`statements`|選擇項。 一或多個陳述式下列`While`，每次執行的`condition`是`True`。|  
|`Continue While`|選擇項。 將控制項傳送至下一個反覆運算`While`區塊。|  
|`Exit While`|選擇項。 控制權轉移出`While`區塊。|  
|`End While`|必要項。 終止 `While` 區塊的定義。|  
  
## <a name="remarks"></a>備註  
 使用`While...End While`結構時您想要重複一組不定陳述式的次數，只要條件維持`True`。 如果您想要更多的彈性與您用來測試條件或何種結果測試它，您可能會偏好[執行...迴圈陳述式](../../../visual-basic/language-reference/statements/do-loop-statement.md)。 如果您想要重複陳述式的次數， [For...下一個陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)通常是比較好的選擇。  
  
> [!NOTE]
>  `While`關鍵字也用於[執行...迴圈陳述式](../../../visual-basic/language-reference/statements/do-loop-statement.md)、 [Skip While 子句](../../../visual-basic/language-reference/queries/skip-while-clause.md)和[Take While 子句](../../../visual-basic/language-reference/queries/take-while-clause.md)。  
  
 如果`condition`是`True`，則所有的`statements`執行直到`End While`遇到陳述式。 控制然後返回`While`陳述式，和`condition`再次檢查。 如果`condition`仍然是`True`，程序會重複。 如果有`False`，控制傳遞到之後的陳述式`End While`陳述式。  
  
 `While`陳述式一律會檢查該條件，再開始迴圈。 迴圈就會繼續條件維持`True`。 如果`condition`是`False`當您第一次輸入迴圈時，它不會執行一次。  
  
 `condition`通常比較結果的兩個值，但它可以是任何運算式評估為[布林資料型別](../../../visual-basic/language-reference/data-types/boolean-data-type.md)值 (`True`或`False`)。 這個運算式可以包含其他資料類型已轉換成數值類型，例如值`Boolean`。  
  
 您可以巢狀`While`放入另一個迴圈內的迴圈。 您也可以巢狀不同類型的另一個控制結構。 如需詳細資訊，請參閱[巢狀控制結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)。  
  
## <a name="exit-while"></a>結束時  
 [結束時](../../../visual-basic/language-reference/statements/exit-statement.md)陳述式可以提供另一種方式結束`While`迴圈。 `Exit While`立即將控制權傳輸至之後的陳述式`End While`陳述式。  
  
 您通常會使用`Exit While`評估某項條件之後 (例如，在`If...Then...Else`結構)。 您可能想要結束迴圈，若您偵測到的條件，使得不必要或不可能繼續重複執行，例如錯誤的數值或終止要求。 您可以使用`Exit While`當您測試的條件，可能會導致*無止盡迴圈*，即無法執行極大或甚至無限次數的迴圈。 然後您可以使用`Exit While`來逸出迴圈。  
  
 您可以將任意數目的`Exit While`隨處陳述式中的`While`迴圈。  
  
 使用時內巢狀`While`迴圈`Exit While`控制權從最內層的迴圈移至下一個高的層級的巢狀結構。  
  
 `Continue While`陳述式立即將控制權傳輸至迴圈的下一個反覆項目。 如需詳細資訊，請參閱[Continue 陳述式](../../../visual-basic/language-reference/statements/continue-statement.md)。  
  
## <a name="example"></a>範例  
 在下列範例中，在迴圈中的陳述式繼續執行直到`index`變數值大於 10。  
  
 [!code-vb[VbVbalrStatements#171](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_1.vb)]  
  
## <a name="example"></a>範例  
 下列範例說明使用`Continue While`和`Exit While`陳述式。  
  
 [!code-vb[VbVbalrStatements#172](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_2.vb)]  
  
## <a name="example"></a>範例  
 下列範例會讀取文字檔案中的所有行。 <xref:System.IO.File.OpenText%2A>方法開啟的檔案，並傳回<xref:System.IO.StreamReader>讀取的字元。 在`While`條件，<xref:System.IO.StreamReader.Peek%2A>方法`StreamReader`判斷檔案是否包含額外的字元。  
  
 [!code-vb[VbVbalrStatements#173](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_3.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [迴圈結構](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [Do...Loop 陳述式](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Boolean 資料類型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)  
 [巢狀控制結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Exit 陳述式](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [Continue 陳述式](../../../visual-basic/language-reference/statements/continue-statement.md)
