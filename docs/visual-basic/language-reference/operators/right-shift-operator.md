---
title: '>> 運算子'
ms.date: 07/20/2015
f1_keywords:
- vb.>>
helpviewer_keywords:
- operator>>
- '>> operator [Visual Basic]'
- bit shift operators [Visual Basic]
- operator >>
- right shift operators [Visual Basic]
ms.assetid: 054dc6a6-47d9-47ef-82da-cfa2b59fbf8f
ms.openlocfilehash: 10b07da22b8b43d6a966fa7c334ac6a0ef4b430d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406362"
---
# <a name="-operator-visual-basic"></a>>> 運算子（Visual Basic）
在位模式上執行算術右移位。  
  
## <a name="syntax"></a>語法  
  
```vb  
result = pattern >> amount  
```  
  
## <a name="parts"></a>組件  
 `result`  
 必要。 整數數值。 位元模式移位的結果。 資料型別與 `pattern` 的型別相同。  
  
 `pattern`  
 必要。 整數值運算式。 要移位的位元模式。 資料型別必須是整數類資料型別 (Integral Type) (`SByte`、`Byte`、`Short`、`UShort`、`Integer`、`UInteger`、`Long` 或 `ULong`)。  
  
 `amount`  
 必要。 數值運算式。 位元模式移位的位元數。 資料型別必須是 `Integer` 或擴展至 `Integer`。  
  
## <a name="remarks"></a>備註  
 算術移位不是迴圈的，這表示不會在另一端重新進入從結果的一端移位的位。 在算術右移位中，會捨棄超出最右邊位位置的位，而最左邊的（符號）位會傳播到左側空出的位位置。 這表示如果 `pattern` 有負值，空出的位置會設定為1，否則會設定為零。  
  
 請注意，資料類型 `Byte` 、 `UShort` 、 `UInteger` 和 `ULong` 不帶正負號，因此不會傳播任何符號位。 如果 `pattern` 是任何不帶正負號的類型，空出的位置一律會設定為零。  
  
 為了避免超過結果所能容納的位數，Visual Basic 會以 `amount` 對應至資料類型的大小遮罩來遮罩的值 `pattern` 。 這些值的二進位和會用於移位量。 大小遮罩如下所示：  
  
|的資料類型`pattern`|大小遮罩（十進位）|大小遮罩（十六進位）|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|&H00000007|  
|`Short`, `UShort`|15|&H0000000F|  
|`Integer`, `UInteger`|31|&H0000001F|  
|`Long`, `ULong`|63|&H0000003F|  
  
 如果 `amount` 為零，則的值與的 `result` 值相同 `pattern` 。 如果 `amount` 是負數，則會將它視為不帶正負號的值，並以適當的大小遮罩加以遮罩。  
  
 算術移位絕不會產生溢位例外狀況。  
  
## <a name="overloading"></a>多載化  
 `>>`運算子可以多載*overloaded*，這表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。 如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用 `>>` 運算子，在整數值上執行算術右移位。 結果的資料類型一律會與移動的運算式相同。  
  
 [!code-vb[VbVbalrOperators#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#14)]  
  
 上述範例的結果如下所示：  
  
- `result1`為2560（0000 1010 0000 0000）。  
  
- `result2`為160（0000 0000 1010 0000）。  
  
- `result3`為2（0000 0000 0000 0010）。  
  
- `result4`為640（0000 0010 1000 0000）。  
  
- `result5`為0（向右移動15個位置）。  
  
 的移位量 `result4` 會計算為18和15，等於2。  
  
 下列範例顯示負數值的算術移位。  
  
 [!code-vb[VbVbalrOperators#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#55)]  
  
 上述範例的結果如下所示：  
  
- `negresult1`為-512 （1111 1110 0000 0000）。  
  
- `negresult2`為-1 （傳播符號位）。  
  
## <a name="see-also"></a>另請參閱

- [位元移位運算子](bit-shift-operators.md)
- [指派運算子](assignment-operators.md)
- [>>= 運算子](right-shift-assignment-operator.md)
- [Visual Basic 中的運算子優先順序](operator-precedence.md)
- [依功能列出運算子](operators-listed-by-functionality.md)
- [Visual Basic 的算術運算子](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
