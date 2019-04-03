---
title: Widening (Visual Basic)
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
ms.openlocfilehash: d7d43d4f5f931881d5c8b663c719fe7f92559799
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825309"
---
# <a name="widening-visual-basic"></a>Widening (Visual Basic)
表示轉換運算子 (`CType`) 將類別或結構轉換成的型別，可以保留原始的類別或結構的所有可能的值。  
  
## <a name="converting-with-the-widening-keyword"></a>轉換擴展關鍵字  
 轉換程序必須指定`Public Shared`除了`Widening`。  
  
 擴展轉換時，一律在執行階段成功，而且永遠不會造成資料遺失。 範例包括`Single`要`Double`，`Char`到`String`，和其基底類型衍生型別。 因為衍生的型別包含基底類型的所有成員，因此是基底類型的執行個體，則會擴展這個最後一個轉換。  
  
 使用的程式碼不需要使用`CType`的擴展轉換，即使`Option Strict`是`On`。  
  
 `Widening`關鍵字可以用在此內容中：  
  
 [Operator 陳述式](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 定義擴展和縮小轉換運算子，例如看到[How to:定義轉換運算子](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)。  
  
## <a name="see-also"></a>另請參閱

- [Operator 陳述式](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [擴展和縮小轉換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [如何：定義運算子](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [CType 函式](../../../visual-basic/language-reference/functions/ctype-function.md)
- [Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [如何：定義轉換運算子](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
