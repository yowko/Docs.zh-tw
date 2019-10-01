---
title: < < 運算子（Visual Basic）
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: 1300ab60e825e7910825be2c65dcab90135ba988
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701119"
---
# <a name="-operator-visual-basic"></a>\<\<運算子（Visual Basic）
在位模式上執行算術左移位。  
  
## <a name="syntax"></a>語法  
  
```vb  
result = pattern << amount  
```  
  
## <a name="parts"></a>組件  
 `result`  
 必要項。 整數數值。 移位位模式的結果。 資料類型與相同`pattern`。  
  
 `pattern`  
 必要項。 整數數值運算式。 要移位的位模式。 資料類型`SByte`必須是整數類型（、 `UShort` `Short` `Integer` 、、`UInteger`、 、、`ULong`或）。 `Long` `Byte`  
  
 `amount`  
 必要項。 數值運算式。 要移位位模式的位數。 資料類型必須是`Integer`或擴大為。 `Integer`  
  
## <a name="remarks"></a>備註  
 算術移位不是迴圈的，這表示不會在另一端重新進入從結果的一端移位的位。 在算術左移位中，會捨棄超出結果資料類型範圍的位，而且右邊空出的位位置會設定為零。  
  
 為了避免超過結果所能容納的位移位數，Visual Basic 會以對應至 `pattern` 之資料類型的大小遮罩來遮罩 `amount` 的值。 這些值的二進位和會用於移位量。 大小遮罩如下所示：  
  
|@No__t 的資料類型-0|大小遮罩（十進位）|大小遮罩（十六進位）|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`、 `Byte`|7|& H00000007|  
|`Short`、 `UShort`|15|& H0000000F|  
|`Integer`、 `UInteger`|31|& H0000001F|  
|`Long`、 `ULong`|63|& H0000003F|  
  
 如果 `amount` 為零，則 `result` 的值與 `pattern` 的值相同。 如果 `amount` 為負數，則會將它視為不帶正負號的值，並以適當的大小遮罩加以遮罩。  
  
 算術移位絕不會產生溢位例外狀況。  
  
> [!NOTE]
> @No__t-0 運算子可以多載 *，這*表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。 如果您的程式碼在這類類別或結構上使用這個運算子，請確定您瞭解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用 `<<` 運算子，在整數值上執行算術左移位。 結果的資料類型一律會與移動的運算式相同。  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 上一個範例的結果如下所示：  
  
- `result1` 為192（0000 0000 1100 0000）。  
  
- `result2` 為3072（0000 1100 0000 0000）。  
  
- `result3` 是-32768 （1000 0000 0000 0000）。  
  
- `result4` 為384（0000 0001 1000 0000）。  
  
- `result5` 為0（向左移動15個位置）。  
  
 @No__t-0 的位移數量是以17和15計算，等於1。  
  
## <a name="see-also"></a>另請參閱

- [位元移位運算子](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [指派運算子](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<<= 運算子](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic 中的算術運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
