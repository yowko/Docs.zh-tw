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
ms.openlocfilehash: 4e2d1000afcf8951e8914335f7b5a278b49f6277
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603622"
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
|`number1`|必要。 任何數值運算式。|  
|`number2`|必要。 任何數值運算式。|  
  
## <a name="result"></a>結果  
 結果是產品的`number1`和`number2`。  
  
## <a name="supported-types"></a>支援的型別  
 所有數字類型，包括不帶正負號和浮點類型和`Decimal`。  
  
## <a name="remarks"></a>備註  
 結果的資料類型而定，運算元的類型。 下表顯示如何決定結果的資料類型。  
  
|運算元資料類型|結果資料類型|  
|---|---|  
|這兩個運算式都是整數類資料類型 ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)，[位元組](../../../visual-basic/language-reference/data-types/byte-data-type.md)，[簡短](../../../visual-basic/language-reference/data-types/short-data-type.md)， [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)，[整數](../../../visual-basic/language-reference/data-types/integer-data-type.md)，[UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)，[長](../../../visual-basic/language-reference/data-types/long-data-type.md)， [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|數值資料類型適合的資料型別`number1`和`number2`。 請參閱中的 「 整數算術 」 資料表[運算子結果的資料類型的](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)。|  
|這兩個運算式都是[十進位](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`|  
|這兩個運算式都是[單一](../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`|  
|任一個運算式是否為浮點資料類型 (`Single`或[Double](../../../visual-basic/language-reference/data-types/double-data-type.md)) 但不是能同時`Single`(請注意`Decimal`不是浮點數資料類型)|`Double`|  
  
 如果運算式評估為[Nothing](../../../visual-basic/language-reference/nothing.md)，它會被視為零。  
  
## <a name="overloading"></a>多載化  
 `*`運算子可以是*多載*，這表示，類別或結構可以重新定義它的行為時的運算元有該類別或結構的類型。 如果您的程式碼會使用此運算子，這類類別或結構上，請確定您了解其重新定義的行為。 如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 這個範例會使用`*`運算子讓兩個數字相乘。 結果是兩個運算元的產品。  
  
 [!code-vb[VbVbalrOperators#4](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/multiplication-operator_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [*= 運算子](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)  
 [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [在 Visual Basic 中的算術運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
