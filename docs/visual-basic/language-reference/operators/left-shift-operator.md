---
title: << 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: 75c16c27dc919ba365cbe3c28c61a1e46496b0ae
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58824282"
---
# <a name="-operator-visual-basic"></a>\<\< 運算子 (Visual Basic)
位元模式中執行算術左的移位。  
  
## <a name="syntax"></a>語法  
  
```  
result = pattern << amount  
```  
  
## <a name="parts"></a>組件  
 `result`  
 必要項。 整數值。 移位的位元模式的結果。 資料類型是屬於相同`pattern`。  
  
 `pattern`  
 必要項。 整數值的運算式。 要移位的位元模式。 資料類型必須是整數類資料類型 (`SByte`， `Byte`， `Short`， `UShort`， `Integer`， `UInteger`， `Long`，或`ULong`)。  
  
 `amount`  
 必要項。 數值運算式。 位元模式移位的位元數。 資料類型必須是`Integer`或擴展至`Integer`。  
  
## <a name="remarks"></a>備註  
 算術的排班不是循環，這表示移出結果的某一端的位元不會重新引入另一端。 在算術左移位，移位超出結果資料類型之範圍的位元會捨棄，而且在右邊空出的位元位置會設定為零。  
  
 若要避免超出結果所能持有更多的位元位移，Visual Basic 會遮罩的值`amount`對應至的資料型別，大小遮罩`pattern`。 這些值的二進位 AND 用於移位量。 遮罩的大小如下所示：  
  
|資料類型 `pattern`|大小遮罩 （十進位）|大小遮罩 （十六進位）|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`、 `Byte`|7|&H00000007|  
|`Short`、 `UShort`|15|&H0000000F|  
|`Integer`、 `UInteger`|31|&H0000001F|  
|`Long`、 `ULong`|63|&H0000003F|  
  
 如果`amount`為零，則值`result`的值一致`pattern`。 如果`amount`是負數，它是做為不帶正負號的值，加上適當的大小遮罩。  
  
 算術移位絕不會產生溢位例外狀況。  
  
> [!NOTE]
>  `<<`運算子只能*多載*，這表示，類別或結構可以重新定義其行為時運算元具有該類別或結構的型別。 如果您的程式碼會使用此運算子，這類類別或結構上，請確定您了解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`<<`運算子來執行算術左移位整數值。 結果會有相同的資料類型的已移位的運算式。  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 上述範例的結果如下所示：  
  
-   `result1` 為 192 (0000 0000 1100年 0000)。  
  
-   `result2` 是 3072 (0000 1100年 0000 0000)。  
  
-   `result3` 是介於-32768 (1000年 0000 0000 0000)。  
  
-   `result4` 為 384 (0000 0001 1000年 0000)。  
  
-   `result5` 為 0 （左邊的移位 15 位數）。  
  
 移位量的`result4`的計算方式為 17 和 15，等於 1。  
  
## <a name="see-also"></a>另請參閱

- [位元移位運算子](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [指派運算子](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<<= 運算子](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [在 Visual Basic 中的算術運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
