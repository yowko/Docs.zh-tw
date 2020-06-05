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
ms.openlocfilehash: d9eb8cb95d46e860aa127954d7b44e37991d4a13
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84391582"
---
# <a name="whileend-while-statement-visual-basic"></a>While...End While 陳述式 (Visual Basic)
只要指定的條件為，就會執行一連串的語句 `True` 。  
  
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
|`condition`|必要。 `Boolean` 運算式。 如果 `condition` 為 `Nothing` ，Visual Basic 會將它視為 `False` 。|  
|`statements`|選擇性。 後面的一或多個語句 `While` ，每次 `condition` 都會執行 `True` 。|  
|`Continue While`|選擇性。 將控制權轉移到區塊的下一個反復專案 `While` 。|  
|`Exit While`|選擇性。 將控制權傳輸至 `While` 區塊。|  
|`End While`|必要。 終止 `While` 區塊的定義。|  
  
## <a name="remarks"></a>備註  
 `While...End While`當您想要重複一組語句而不限次數時（只要條件仍然存在），請使用結構 `True` 。 如果您想要在測試條件的位置或測試它的結果時擁有更大的彈性，您可能會想[要 .。。Loop 語句](do-loop-statement.md)。 如果您想要重複語句[設定的次數，請將 .。。下一個語句](for-next-statement.md)通常是較好的選擇。  
  
> [!NOTE]
> `While`關鍵字也用於 [ [...]Loop 語句](do-loop-statement.md)、 [Skip while 子句](../queries/skip-while-clause.md)和[Take While 子句](../queries/take-while-clause.md)。  
  
 如果 `condition` 為 `True` ，則所有 `statements` 執行直到 `End While` 遇到語句為止。 控制項接著 `While` 會回到語句，並 `condition` 再次檢查。 如果 `condition` 仍然是 `True` ，則會重複處理常式。 如果是 `False` ，則控制權會傳遞至語句後面的語句 `End While` 。  
  
 `While`語句在啟動迴圈之前，一律會檢查條件。 當條件保留時，迴圈就會繼續進行 `True` 。 `condition` `False` 當您第一次進入迴圈時，它不會執行一次。  
  
 `condition`通常是兩個值的比較所得到的結果，但它可以是任何會評估為[布林資料類型](../data-types/boolean-data-type.md)值（ `True` 或 `False` ）的運算式。 這個運算式可以包含另一個資料類型的值，例如已轉換成的數數值型別 `Boolean` 。  
  
 您可以藉 `While` 由在另一個迴圈內放置迴圈來加以嵌套。 您也可以將不同種類的控制結構嵌套在另一種。 如需詳細資訊，請參閱[嵌套控制項結構](../../programming-guide/language-features/control-flow/nested-control-structures.md)。  
  
## <a name="exit-while"></a>結束  
 [Exit While](exit-statement.md)語句可以提供另一個結束迴圈的方式 `While` 。 `Exit While`會立即將控制權轉移至語句後面的語句 `End While` 。  
  
 您通常 `Exit While` 會在評估某些條件（例如，在結構中）時使用 `If...Then...Else` 。 如果您偵測到不必要或無法繼續反覆運算的條件（例如錯誤值或終止要求），您可能會想要結束迴圈。 `Exit While`當您測試的條件可能會造成無止盡的*迴圈*時，您可以使用，這是一種迴圈，可以執行極大或甚至無限的次數。 然後，您可以使用 `Exit While` 來對迴圈進行 escape。  
  
 您可以將任意數目的 `Exit While` 語句放在迴圈中的任何位置 `While` 。  
  
 在嵌套迴圈中使用時 `While` ，會 `Exit While` 將控制項從最內層的迴圈轉移到下一個較高層級的嵌套。  
  
 `Continue While`語句會立即將控制權轉移到迴圈的下一個反復專案。 如需詳細資訊，請參閱[Continue 語句](continue-statement.md)。  
  
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
- [Continue 語句](continue-statement.md)
