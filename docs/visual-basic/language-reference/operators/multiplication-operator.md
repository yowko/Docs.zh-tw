---
title: '* 運算子 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.*
helpviewer_keywords:
- arithmetic operators [Visual Basic], multiplication
- operators [Visual Basic], multiplication
- '* operator [Visual Basic]'
- multiplication operator [Visual Basic], syntax
- math operators [Visual Basic]
ms.assetid: 2b210382-99da-4195-89ba-b1d06f5e89ad
ms.openlocfilehash: 09b95585325b05c0b7925c4c1c9e123f45791e10
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936639"
---
# <a name="-operator-visual-basic"></a>* 運算子 (Visual Basic)
將兩個數字相乘。  
  
## <a name="syntax"></a>語法  
  
```  
number1 * number2  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`number1`|必要項。 任何數值運算式。|  
|`number2`|必要項。 任何數值運算式。|  
  
## <a name="result"></a>結果  
 結果是乘積`number1`和`number2`。  
  
## <a name="supported-types"></a>支援的型別  
 所有的數字類型，包括不帶正負號和浮點類型和`Decimal`。  
  
## <a name="remarks"></a>備註  
 結果的資料類型取決於運算元的類型。 下表顯示如何決定結果的資料類型。  
  
|運算元資料類型|結果資料類型|  
|---|---|  
|這兩個運算式都是整數資料類型 ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)，[位元組](../../../visual-basic/language-reference/data-types/byte-data-type.md)，[簡短](../../../visual-basic/language-reference/data-types/short-data-type.md)， [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)，[整數](../../../visual-basic/language-reference/data-types/integer-data-type.md)，[UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)，[長](../../../visual-basic/language-reference/data-types/long-data-type.md)， [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|適用於資料類型的數值資料類型`number1`和`number2`。 請參閱中的 「 整數算術 」 表格[資料類型的運算子結果](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)。|  
|這兩個運算式都是[十進位](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`|  
|這兩個運算式都是[單一](../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`|  
|任一個運算式是否為浮點資料類型 (`Single`或[Double](../../../visual-basic/language-reference/data-types/double-data-type.md))，但不是能兩者都`Single`(請注意`Decimal`不是浮點資料類型)|`Double`|  
  
 如果運算式評估為[Nothing](../../../visual-basic/language-reference/nothing.md)，它會被視為零。  
  
## <a name="overloading"></a>多載化  
 `*`運算子只能*多載*，這表示，類別或結構可以重新定義其行為時運算元具有該類別或結構的型別。 如果您的程式碼會使用這個運算子，這類類別或結構上，請務必了解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 這個範例會使用`*`運算子來將兩個數字相乘。 結果是兩個運算元的乘積。  
  
 [!code-vb[VbVbalrOperators#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#4)]  
  
## <a name="see-also"></a>另請參閱

- [*= 運算子](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [在 Visual Basic 中的算術運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
