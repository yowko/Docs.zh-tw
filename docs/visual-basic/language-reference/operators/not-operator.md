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
ms.openlocfilehash: 4e54fdca9123ad5595eb9a8c5e2ac5bc303a8f6a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824196"
---
# <a name="not-operator-visual-basic"></a>Not 運算子 (Visual Basic)
上執行邏輯否定`Boolean`運算式或數值運算式上的位元否定。  
  
## <a name="syntax"></a>語法  
  
```  
result = Not expression  
```  
  
## <a name="parts"></a>組件  
 `result`  
 必要項。 任何`Boolean`或數值運算式。  
  
 `expression`  
 必要項。 任何`Boolean`或數值運算式。  
  
## <a name="remarks"></a>備註  
 針對`Boolean`運算式下, 表將說明如何`result`決定。  
  
|如果`expression`是|值`result`是|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 數值運算式，如`Not`運算子會反轉任何的數值運算式的位元值，並對應中位元設`result`根據下表。  
  
|如果位元`expression`是|中的位元`result`是|  
|-------------------------------|----------------------------|  
|1|0|  
|0|1|  
  
> [!NOTE]
>  因為邏輯和位元運算子會有較低的優先順序高於其他算術和關係運算子，所以任何位元的作業應該含括括號，以確保能夠正確執行。  
  
## <a name="data-types"></a>資料類型  
 布林值的否定運算結果的資料型別是`Boolean`。 對於位元否定運算中，將結果資料類型相當的`expression`。 不過，如果運算式為`Decimal`，結果是`Long`。  
  
## <a name="overloading"></a>多載化  
 `Not`運算子只能*多載*，這表示，類別或結構可以重新定義其行為時其運算元的該類別或結構的類型。 如果您的程式碼會使用這個運算子，這類類別或結構上，請務必了解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`Not`上執行邏輯否定運算子`Boolean`運算式。 結果是`Boolean`值，表示運算式的值相反。  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 上述範例產生的結果`False`和`True`分別。  
  
## <a name="example"></a>範例  
 下列範例會使用`Not`運算子執行邏輯否定的數值運算式的個別位元。 結果模式中的位元會設定為在運算元模式中，包括正負號位元的對應位元的反向。  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 上述範例中會分別產生結果-11-9，-7。  
  
## <a name="see-also"></a>另請參閱

- [邏輯/位元運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [在 Visual Basic 中的邏輯和位元運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
