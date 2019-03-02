---
title: / 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb./
helpviewer_keywords:
- division operator [Visual Basic], floating point
- floating-point numbers [Visual Basic], division operator
- slash (/) operator
- zero, division by zero
- operators [Visual Basic], arithmetic
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- operators [Visual Basic], division
- division operator [Visual Basic], syntax
- / operator [Visual Basic]
- math operators [Visual Basic]
ms.assetid: 335e97f2-c434-439e-9064-76973a051101
ms.openlocfilehash: 7d9b02a9c997ffcfdd61e277a6ed3779d8821831
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202453"
---
# <a name="-operator-visual-basic"></a>/ 運算子 (Visual Basic)
兩數相除並傳回浮點結果。  
  
## <a name="syntax"></a>語法  
  
```  
expression1 / expression2  
```  
  
## <a name="parts"></a>組件  
 `expression1`  
 必要項。 任何數值運算式。  
  
 `expression2`  
 必要項。 任何數值運算式。  
  
## <a name="supported-types"></a>支援的型別  
 所有的數字類型，包括不帶正負號和浮點類型和`Decimal`。  
  
## <a name="result"></a>結果  
 結果是完整的商數`expression1`除以`expression2`，包括任何餘數。  
  
 [\ 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)傳回整數商數，這會卸除其餘部分。  
  
## <a name="remarks"></a>備註  
 結果的資料類型取決於運算元的類型。 下表顯示如何決定結果的資料類型。  
  
|運算元資料類型|結果資料類型|  
|------------------------|----------------------|  
|這兩個運算式都是整數資料類型 ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)，[位元組](../../../visual-basic/language-reference/data-types/byte-data-type.md)，[簡短](../../../visual-basic/language-reference/data-types/short-data-type.md)， [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)，[整數](../../../visual-basic/language-reference/data-types/integer-data-type.md)，[UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)，[長](../../../visual-basic/language-reference/data-types/long-data-type.md)， [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|`Double`|  
|一個運算式[單一](../../../visual-basic/language-reference/data-types/single-data-type.md)資料類型和其他不是[Double](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Single`|  
|一個運算式[十進位](../../../visual-basic/language-reference/data-types/decimal-data-type.md)資料類型和其他不[單一](../../../visual-basic/language-reference/data-types/single-data-type.md)或[Double](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Decimal`|  
|任何一個運算式[Double](../../../visual-basic/language-reference/data-types/double-data-type.md)資料類型|`Double`|  
  
 任何整數類資料的數值運算式執行除法之前，都會擴展為`Double`。 如果您將結果指派給整數資料型別時，Visual Basic 會嘗試將轉換的結果`Double`為該型別。 如果結果無法放入該類型，這會擲回例外狀況。 特別的是，在此 [說明] 頁面上看到 「 嘗試以零為除數"。  
  
 如果`expression1`或是`expression2`評估為[Nothing](../../../visual-basic/language-reference/nothing.md)，它會被視為零。  
  
## <a name="attempted-division-by-zero"></a>嘗試的除以零  
 如果`expression2`評估為零，`/`運算子具有不同行為不同的運算元資料類型。 下表顯示可能的行為。  
  
|運算元資料類型|行為如果`expression2`為零|  
|------------------------|---------------------------------------|  
|浮點數 (`Single`或`Double`)|傳回無限大 (<xref:System.Double.PositiveInfinity>或是<xref:System.Double.NegativeInfinity>)，或<xref:System.Double.NaN>（不是數字） 如果`expression1`也是零|  
|`Decimal`|會擲回 <xref:System.DivideByZeroException>|  
|整數 （帶正負號或不帶正負號）|嘗試轉換回整數類資料類型會擲回<xref:System.OverflowException>無法接受整數類資料類型，所以<xref:System.Double.PositiveInfinity>， <xref:System.Double.NegativeInfinity>，或 <xref:System.Double.NaN>|  
  
> [!NOTE]
>  `/`運算子只能*多載*，這表示，類別或結構可以重新定義其行為時運算元具有該類別或結構的型別。 如果您的程式碼會使用這個運算子，這類類別或結構上，請務必了解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 這個範例會使用`/`執行浮點除法運算子。 結果是兩個運算元的商。  
  
 [!code-vb[VbVbalrOperators#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#16)]  
  
 在上述範例中的運算式會傳回 2.5 和 3.333333 的值。 請注意，結果一律是浮點數 (`Double`)，即使兩個運算元都是整數常數。  
  
## <a name="see-also"></a>另請參閱
- [/ = 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [\ 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)
- [運算子結果的資料類型](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)
- [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [在 Visual Basic 中的算術運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
