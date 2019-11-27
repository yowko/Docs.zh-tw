---
title: Narrowing
ms.date: 07/20/2015
f1_keywords:
- vb.narrowing
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Narrowing keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
ms.openlocfilehash: b252f7939e812f31103d4bd98ffd50953679f042
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351468"
---
# <a name="narrowing-visual-basic"></a>Narrowing (Visual Basic)
表示轉換運算子（`CType`）會將類別或結構轉換成可能無法保存原始類別或結構之某些可能值的類型。  
  
## <a name="converting-with-the-narrowing-keyword"></a>使用縮小關鍵字進行轉換  
 轉換程式除了 `Narrowing`之外，還必須指定 `Public Shared`。  
  
 縮小轉換在執行時間不一定會成功，而且可能會失敗或產生資料遺失。 範例 `Long` `Integer`、`String` `Date`，以及基底類型到衍生類型。 最後一個轉換會縮小，因為基底類型可能不包含衍生類型的所有成員，因此不是衍生類型的實例。  
  
 如果 `On``Option Strict`，則取用程式碼必須使用 `CType` 來進行所有的縮小轉換。  
  
 `Narrowing` 關鍵字可以在此內容中使用：  
  
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a>請參閱

- [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Widening](../../../visual-basic/language-reference/modifiers/widening.md)
- [擴展和縮小轉換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [如何：定義運算子](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [CType 函式](../../../visual-basic/language-reference/functions/ctype-function.md)
- [Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)
