---
title: '>> 運算子 (Visual Basic)'
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
ms.openlocfilehash: 8803dc2e25edde756958a243d429dd30c5c78bcf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053284"
---
# <a name="-operator-visual-basic"></a>>> 運算子 (Visual Basic)
位元模式中執行算術右移位。  
  
## <a name="syntax"></a>語法  
  
```  
result = pattern >> amount  
```  
  
## <a name="parts"></a>組件  
 `result`  
 必要項。 整數值。 移位的位元模式的結果。 資料類型是屬於相同`pattern`。  
  
 `pattern`  
 必要項。 整數值的運算式。 要移位的位元模式。 資料類型必須是整數類資料類型 (`SByte`， `Byte`， `Short`， `UShort`， `Integer`， `UInteger`， `Long`，或`ULong`)。  
  
 `amount`  
 必要項。 數值運算式。 位元模式移位的位元數。 資料類型必須是`Integer`或擴展至`Integer`。  
  
## <a name="remarks"></a>備註  
 算術的排班不是循環，這表示移出結果的某一端的位元不會重新引入另一端。 在算術右移位，移位超過最右邊位元位置的位元會予以捨棄，並最左邊 （符號） 位元會傳播到左邊空出的位元位置。 這表示如果`pattern`的值是負數，空出的位置會設為其中一個; 否則設定為零。  
  
 請注意，資料類型`Byte`， `UShort`， `UInteger`，和`ULong`是不帶正負號，因此沒有傳播沒有正負號位元。 如果`pattern`的任何不帶正負號的類型、 空出的位置一律會設定為零。  
  
 若要避免超出結果所能持有更多的位元移位，Visual Basic 會遮罩的值`amount`具有對應的資料類型大小遮罩`pattern`。 這些值的二進位 AND 用於移位量。 遮罩的大小如下所示：  
  
|資料類型 `pattern`|大小遮罩 （十進位）|大小遮罩 （十六進位）|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`、 `Byte`|7|&H00000007|  
|`Short`、 `UShort`|15|&H0000000F|  
|`Integer`、 `UInteger`|31|&H0000001F|  
|`Long`、 `ULong`|63|&H0000003F|  
  
 如果`amount`為零，則值`result`的值一致`pattern`。 如果`amount`是負數，它是做為不帶正負號的值，加上適當的大小遮罩。  
  
 算術移位絕不會產生溢位例外狀況。  
  
## <a name="overloading"></a>多載化  
 `>>`運算子只能*多載*，這表示，類別或結構可以重新定義其行為時運算元具有該類別或結構的型別。 如果您的程式碼會使用這個運算子，這類類別或結構上，請務必了解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`>>`整數值上執行算術右移位運算子。 結果會有相同的資料類型的已移位的運算式。  
  
 [!code-vb[VbVbalrOperators#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#14)]  
  
 上述範例的結果如下所示：  
  
- `result1` 是 2560 (0000 1010年 0000 0000)。  
  
- `result2` 是 160 (0000 0000 1010年 0000)。  
  
- `result3` 為 2 (0000 0000 0000 0010)。  
  
- `result4` 為 640 (0000 0010 1000年 0000)。  
  
- `result5` 為 0 （右邊的移位 15 位數）。  
  
 移位量的`result4`的計算方式為 18 和 15，等於 2。  
  
 下列範例會顯示在負值上算術移位。  
  
 [!code-vb[VbVbalrOperators#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#55)]  
  
 上述範例的結果如下所示：  
  
- `negresult1` 是-512 (1111年 1110年 0000 0000)。  
  
- `negresult2` 為-1 （傳播正負號位元）。  
  
## <a name="see-also"></a>另請參閱

- [位元移位運算子](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [指派運算子](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [>>= 運算子](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [在 Visual Basic 中的算術運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
