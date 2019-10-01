---
title: '* 運算子（Visual Basic）'
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
ms.openlocfilehash: b5b601c7604cb7ce1afaebc98b2157634a77fda4
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701098"
---
# <a name="-operator-visual-basic"></a>* 運算子 (Visual Basic)
將兩個數字相乘。  
  
## <a name="syntax"></a>語法  
  
```vb  
number1 * number2  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`number1`|必要項。 任何數值運算式。|  
|`number2`|必要項。 任何數值運算式。|  
  
## <a name="result"></a>結果  
 結果為 `number1` 和 `number2` 的乘積。  
  
## <a name="supported-types"></a>支援的型別  
 所有數數值型別，包括不帶正負號的和浮點類型，以及 `Decimal`。  
  
## <a name="remarks"></a>備註  
 結果的資料類型取決於運算元的類型。 下表顯示如何判斷結果的資料類型。  
  
|運算元資料類型|結果資料類型|  
|---|---|  
|這兩個運算式都是整數資料類型（[SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)、 [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md)、 [Short](../../../visual-basic/language-reference/data-types/short-data-type.md)、 [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)、 [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)、 [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)、 [Long](../../../visual-basic/language-reference/data-types/long-data-type.md)、 [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)）|適用于 `number1` 和 `number2` 之資料類型的數值資料類型。 請參閱[運算子結果的資料類型](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)中的「整數算術」資料表。|  
|這兩個運算式都是[十進位](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`|  
|這兩個運算式都是[Single](../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`|  
|任一運算式是浮點資料類型（`Single` 或[雙精度](../../../visual-basic/language-reference/data-types/double-data-type.md)浮點數），但不能同時 `Single` （注意 `Decimal` 不是浮點資料類型）|`Double`|  
  
 如果運算式評估為不是[任何](../../../visual-basic/language-reference/nothing.md)值，則會將它視為零。  
  
## <a name="overloading"></a>多載化  
 @No__t-0 運算子可以多載 *，這*表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。 如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 這個範例會使用 `*` 運算子來將兩個數字相乘。 結果為兩個運算元的乘積。  
  
 [!code-vb[VbVbalrOperators#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#4)]  
  
## <a name="see-also"></a>另請參閱

- [*= 運算子](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic 中的算術運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
