---
title: Or 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Or
helpviewer_keywords:
- Or operator [Visual Basic]
- operators [Visual Basic], bitwise
- inclusive Or operator [Visual Basic]
- bitwise operators [Visual Basic], OR operator
- Or keyword [Visual Basic]
- operators [Visual Basic], inclusive or
- operators [Visual Basic], disjunction
- bitwise comparison [Visual Basic]
- logical disjunction
- disjunction operator [Visual Basic]
ms.assetid: 41ed6905-bf3d-468a-9e3b-03c10d461891
ms.openlocfilehash: 0277b6f24e62ed5f0cad3dae225c86fffc4c09b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013513"
---
# <a name="or-operator-visual-basic"></a>Or 運算子 (Visual Basic)
對兩個執行邏輯分離`Boolean`運算式或兩個數值運算式的位元分離。  
  
## <a name="syntax"></a>語法  
  
```  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a>組件  
 `result`  
 必要項。 任何`Boolean`或數值運算式。 針對`Boolean`相較之下，`result`是兩個內含邏輯分離`Boolean`值。 對於位元運算，`result`是數值，代表兩個數值位元模式 （含） 的位元分離。  
  
 `expression1`  
 必要項。 任何`Boolean`或數值運算式。  
  
 `expression2`  
 必要項。 任何`Boolean`或數值運算式。  
  
## <a name="remarks"></a>備註  
 針對`Boolean`相較之下，`result`是`False`並僅有兩個`expression1`並`expression2`評估為`False`。 下表將說明如何`result`決定。  
  
|如果`expression1`是|和`expression2`是|值`result`是|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  在 `Boolean`相較之下，`Or`運算子一律會評估這兩個運算式，這可能包括程序呼叫。 [OrElse 運算子](../../../visual-basic/language-reference/operators/orelse-operator.md)會執行*最少運算*，這表示如果`expression1`是`True`，然後`expression2`不會評估。  
  
 位元運算，如`Or`運算子會在兩個數值運算式之間執行位元比較相同位置的位元，並對應中位元設`result`根據下表。  
  
|如果位元`expression1`是|在位元和`expression2`是|中的位元`result`是|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
>  因為邏輯和位元運算子會有較低的優先順序高於其他算術和關係運算子，所以任何位元的作業應該含括括號，以確保能夠正確執行。  
  
## <a name="data-types"></a>資料類型  
 如果包含運算元`Boolean`Visual Basic 運算式及一個數值運算式，將轉換`Boolean`為數值的運算式 (– 1`True`以 0 代表`False`) 和執行位元運算。  
  
 針對`Boolean`相較之下，結果的資料型別是`Boolean`。 如需位元的比較，將結果資料類型是數值類型適合的資料類型`expression1`和`expression2`。 請參閱 < 關聯式和位元比較 」 的表格[資料類型的運算子結果](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)。  
  
## <a name="overloading"></a>多載化  
 `Or`運算子只能*多載*，這表示，類別或結構可以重新定義其行為時運算元具有該類別或結構的型別。 如果您的程式碼會使用這個運算子，這類類別或結構上，請務必了解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`Or`操作員兩個運算式上執行內含邏輯分離。 結果是`Boolean`值，表示其中兩個運算式是否`True`。  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 上述範例產生的結果`True`， `True`，和`False`分別。  
  
## <a name="example"></a>範例  
 下列範例會使用`Or`運算子的兩個數值運算式的個別位元執行內含邏輯分離。 如果任一運算元的對應位元設為 1，會設定結果模式中的位元。  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 上述範例中會分別產生 10、 14 及 14 的結果。  
  
## <a name="see-also"></a>另請參閱

- [邏輯/位元運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [OrElse 運算子](../../../visual-basic/language-reference/operators/orelse-operator.md)
- [在 Visual Basic 中的邏輯和位元運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
