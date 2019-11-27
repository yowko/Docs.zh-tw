---
title: Widening
ms.date: 07/20/2015
f1_keywords:
- vb.widening
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Widening keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 646ae263-94d3-40a2-b0cc-64f619292f56
ms.openlocfilehash: 1c9aa78549ca6e41c9fe54c12e0aaec8e7cc30cb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347837"
---
# <a name="widening-visual-basic"></a>Widening (Visual Basic)
表示轉換運算子（`CType`）會將類別或結構轉換成可保存原始類別或結構之所有可能值的類型。  
  
## <a name="converting-with-the-widening-keyword"></a>使用加寬關鍵字進行轉換  
 轉換程式除了 `Widening`之外，還必須指定 `Public Shared`。  
  
 擴輾轉換一律會在執行時間成功，而且永遠不會產生資料遺失。 範例 `Single` `Double`、`Char` `String`，以及衍生型別到其基底型別。 最後一次轉換是擴大的，因為衍生類型包含基底類型的所有成員，因此是基底類型的實例。  
  
 取用程式碼不需要使用 `CType` 進行擴輾轉換，即使 `Option Strict` `On`。  
  
 `Widening` 關鍵字可以在此內容中使用：  
  
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 如需擴展和縮小轉換運算子的範例定義，請參閱[如何：定義轉換運算子](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)。  
  
## <a name="see-also"></a>請參閱

- [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [擴展和縮小轉換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [如何：定義運算子](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [CType 函式](../../../visual-basic/language-reference/functions/ctype-function.md)
- [Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [如何：定義轉換運算子](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
