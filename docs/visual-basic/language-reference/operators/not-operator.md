---
title: Not 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Not
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator [Visual Basic]
- inverse bit values in variables [Visual Basic]
- bitwise operators [Visual Basic], NOT operator
- bitwise comparison [Visual Basic]
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
ms.openlocfilehash: 5ebc5f9dbf674a9a6560bd96b3e8c9edcae08a81
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701083"
---
# <a name="not-operator-visual-basic"></a>Not 運算子 (Visual Basic)
在 `Boolean` 運算式上執行邏輯否定，或在數值運算式上執行位否定。  
  
## <a name="syntax"></a>語法  
  
```vb  
result = Not expression  
```  
  
## <a name="parts"></a>組件  
 `result`  
 必要項。 Any `Boolean`或 numeric 運算式。  
  
 `expression`  
 必要項。 Any `Boolean`或 numeric 運算式。  
  
## <a name="remarks"></a>備註  
 若為 `Boolean` 運算式，下表說明如何決定 `result`。  
  
|如果`expression`為|@No__t-0 的值為|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 對於數值運算式，`Not` 運算子會反轉任何數值運算式的位值，並根據下表，在 `result` 中設定對應的位。  
  
|如果 @no__t 中的位-0 是|@No__t-0 中的位是|  
|-------------------------------|----------------------------|  
|1|0|  
|0|1|  
  
> [!NOTE]
> 由於邏輯和位運算子的優先順序比其他算術和關係運算子低，因此應該將任何位運算括在括弧中，以確保正確執行。  
  
## <a name="data-types"></a>資料類型  
 若為布林值否定，結果的資料類型會 `Boolean`。 若為位否定，結果資料類型與 `expression` 相同。 不過，如果 expression `Decimal`，則結果為 `Long`。  
  
## <a name="overloading"></a>多載化  
 @No__t-0 運算子可以多載 *，這*表示當類別或結構的運算元具有該類別或結構的類型時，可以重新定義其行為。 如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用 `Not` 運算子來執行 @no__t 1 運算式的邏輯否定。 結果為 @no__t 0 的值，表示運算式值的反轉。  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 上述範例會分別產生 `False` 和 `True` 的結果。  
  
## <a name="example"></a>範例  
 下列範例會使用 `Not` 運算子來執行數值運算式之個別位的邏輯否定。 結果模式中的位會設定為運算元模式中對應位的反向，包括符號位。  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 上述範例會分別產生–11、–9和–7的結果。  
  
## <a name="see-also"></a>另請參閱

- [邏輯/位運算子（Visual Basic）](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic 中的邏輯和位運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
