---
title: Not 運算子
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
ms.openlocfilehash: 7d0beea16a2ac00be090c6a241f9790a0ba33390
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874800"
---
# <a name="not-operator-visual-basic"></a>Not 運算子 (Visual Basic)

對運算式執行邏輯否定 `Boolean` ，或在數值運算式上執行位否定。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
result = Not expression  
```  
  
## <a name="parts"></a>組件  

 `result`  
 必要。 任何 `Boolean` 或數值運算式。  
  
 `expression`  
 必要。 任何 `Boolean` 或數值運算式。  
  
## <a name="remarks"></a>備註  

 針對 `Boolean` 運算式，下表說明如何 `result` 決定。  
  
|如果 `expression` 為 |的值 `result` 為|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 若為數值運算式， `Not` 運算子會反轉任何數值運算式的位值，並根據下表設定對應的位 `result` 。  
  
|如果中的位 `expression` 為|中的位 `result` 為|  
|-------------------------------|----------------------------|  
|1|0|  
|0|1|  
  
> [!NOTE]
> 由於邏輯和位運算子的優先順序比其他算術和關係運算子低，因此任何位運算都應以括弧括住，以確保正確執行。  
  
## <a name="data-types"></a>資料類型  

 若為布林值否定，則結果的資料類型為 `Boolean` 。 針對位否定，結果資料類型與的結果相同 `expression` 。 但是，如果 expression 為 `Decimal` ，則結果為 `Long` 。  
  
## <a name="overloading"></a>多載化  

 可以多載 `Not` 運算子*overloaded*，這表示類別或結構在其運算元具有該類別或結構的型別時，可以重新定義其行為。 如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  

 下列範例會使用 `Not` 運算子來執行運算式的邏輯否定 `Boolean` 。 結果是 `Boolean` 代表運算式值反轉的值。  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 上述範例會分別產生和的結果 `False` `True` 。  
  
## <a name="example"></a>範例  

 下列範例會使用 `Not` 運算子來執行數值運算式之個別位的邏輯否定。 結果模式中的位會設定為運算元模式中對應位的反向，包括正負號位。  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 上述範例會分別產生–11、-9 和–7的結果。  
  
## <a name="see-also"></a>另請參閱

- [邏輯/位元運算子 (Visual Basic)](logical-bitwise-operators.md)
- [Visual Basic 中的運算子優先順序](operator-precedence.md)
- [依功能列出運算子](operators-listed-by-functionality.md)
- [Visual Basic 中的邏輯運算子和位元運算子](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
