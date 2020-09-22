---
title: While...End While 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.While
- vb.While...EndWhile
helpviewer_keywords:
- While statement [Visual Basic], While...End While
- While statement [Visual Basic]
- While...End While statements [Visual Basic]
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
ms.openlocfilehash: e3ab95f43e101a9ad8abe6fa61b94ae7542e409c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869483"
---
# <a name="whileend-while-statement-visual-basic"></a>While...End While 陳述式 (Visual Basic)

只要指定的條件為，就會執行一連串的語句 `True` 。  
  
## <a name="syntax"></a>Syntax  
  
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
|`condition`|必要。 `Boolean` 運算式。 如果 `condition` 為 `Nothing` ，Visual Basic 會將其視為 `False` 。|  
|`statements`|選擇性。 下列一或多個語句 `While` 會在每次執行 `condition` 時執行 `True` 。|  
|`Continue While`|選擇性。 將控制權傳輸至區塊的下一個反復專案 `While` 。|  
|`Exit While`|選擇性。 將控制權傳輸至 `While` 區塊。|  
|`End While`|必要。 終止 `While` 區塊的定義。|  
  
## <a name="remarks"></a>備註  

 `While...End While`當您想要重複一組語句，但只要條件仍然存在，請使用結構 `True` 。 如果您想要在測試條件或測試結果的位置有更大的彈性，您可能會想要 [.。。迴圈語句](do-loop-statement.md)。 如果您想要重複執行語句的次數， [請將下一個語句](for-next-statement.md) 通常是較佳的選擇。  
  
> [!NOTE]
> `While`關鍵字也可用於[Do .。。Loop 語句](do-loop-statement.md)、 [Skip while 子句](../queries/skip-while-clause.md)和[Take while 子句](../queries/take-while-clause.md)。  
  
 如果 `condition` 為 `True` ，則所有 `statements` 執行直到 `End While` 遇到語句為止。 然後，控制權會返回 `While` 語句，然後 `condition` 再次選取。 如果 `condition` 仍為 `True` ，則會重複處理常式。 如果是 `False` ，控制權會傳遞給語句後面的語句 `End While` 。  
  
 `While`語句在開始迴圈之前，一律會檢查條件。 當條件維持時，迴圈會繼續 `True` 。 如果 `condition` 是 `False` 當您第一次進入迴圈，則不會執行一次。  
  
 `condition`通常會比較兩個值，但它可以是任何評估為[布林資料類型](../data-types/boolean-data-type.md)值的運算式 (`True` 或 `False`) 。 此運算式可以包含已轉換成之另一個資料類型的值，例如數數值型別 `Boolean` 。  
  
 您可以藉 `While` 由在另一個迴圈內放置迴圈，來將迴圈嵌套。 您也可以在彼此之間嵌套不同類型的控制結構。 如需詳細資訊，請參閱 [嵌套控制項結構](../../programming-guide/language-features/control-flow/nested-control-structures.md)。  
  
## <a name="exit-while"></a>離開  

 [Exit While](exit-statement.md)語句可以提供另一種方式來結束 `While` 迴圈。 `Exit While` 立即將控制權傳輸至語句後面的語句 `End While` 。  
  
 您通常 `Exit While` 會在評估某些條件之後使用 (例如，在 `If...Then...Else` 結構) 中。 如果您偵測到導致不必要或無法繼續反覆運算的條件（例如錯誤值或終止要求），您可能會想要結束迴圈。 `Exit While`當您測試可能造成無止盡*迴圈*的條件時，可以使用，這是可能執行極大或甚至無限次數的迴圈。 然後，您可以使用 `Exit While` 來對迴圈進行換用。  
  
 您可以將任意數目的 `Exit While` 語句放在迴圈中的任何位置 `While` 。  
  
 在嵌套迴圈中使用時 `While` ，會 `Exit While` 將控制權從最內層的迴圈傳送到下一個較高層級的嵌套。  
  
 `Continue While`語句會立即將控制權轉移到迴圈的下一個反復專案。 如需詳細資訊，請參閱 [Continue 語句](continue-statement.md)。  
  
## <a name="example"></a>範例  

 在下列範例中，迴圈中的語句會繼續執行，直到 `index` 變數大於10為止。  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a>範例  

 下列範例說明如何使用 `Continue While` 和 `Exit While` 語句。  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a>範例  

 下列範例會讀取文字檔中的所有行。 <xref:System.IO.File.OpenText%2A>方法會開啟檔案，並傳回 <xref:System.IO.StreamReader> 讀取字元的。 在 `While` 條件中，的 <xref:System.IO.StreamReader.Peek%2A> 方法會判斷檔案 `StreamReader` 是否包含額外的字元。  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a>另請參閱

- [迴圈結構](../../programming-guide/language-features/control-flow/loop-structures.md)
- [Do...Loop 陳述式](do-loop-statement.md)
- [For...Next 陳述式](for-next-statement.md)
- [Boolean 資料類型](../data-types/boolean-data-type.md)
- [巢狀控制結構](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit 陳述式](exit-statement.md)
- [Continue 陳述式](continue-statement.md)
