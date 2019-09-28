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
ms.openlocfilehash: 238c062b2dd0744ba96cf9ba8591c0ef39f81bb3
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592187"
---
# <a name="-operator-visual-basic"></a>/ 運算子 (Visual Basic)
將兩個數字相除，並傳回浮點結果。  
  
## <a name="syntax"></a>語法  
  
```vb  
expression1 / expression2  
```  
  
## <a name="parts"></a>組件  
 `expression1`  
 必要項。 任何數值運算式。  
  
 `expression2`  
 必要項。 任何數值運算式。  
  
## <a name="supported-types"></a>支援的型別  
 所有數數值型別，包括不帶正負號的和浮點類型，以及 `Decimal`。  
  
## <a name="result"></a>結果  
 結果是 `expression1` 除以 `expression2` 的完整商，包括任何餘數。  
  
 [\ 運算子（Visual Basic）](../../../visual-basic/language-reference/operators/integer-division-operator.md)會傳回整數商，這會捨棄餘數。  
  
## <a name="remarks"></a>備註  
 結果的資料類型取決於運算元的類型。 下表顯示如何判斷結果的資料類型。  
  
|運算元資料類型|結果資料類型|  
|------------------------|----------------------|  
|這兩個運算式都是整數資料類型（[SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)、 [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md)、 [Short](../../../visual-basic/language-reference/data-types/short-data-type.md)、 [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)、 [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)、 [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)、 [Long](../../../visual-basic/language-reference/data-types/long-data-type.md)、 [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)）|`Double`|  
|一個運算式是[單一](../../../visual-basic/language-reference/data-types/single-data-type.md)資料類型，另一個則不是[雙精度浮點數](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Single`|  
|一個運算式是[Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)資料型別，另一個則不是[單一](../../../visual-basic/language-reference/data-types/single-data-type.md)或[雙精度浮點數](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Decimal`|  
|任一運算式是[Double](../../../visual-basic/language-reference/data-types/double-data-type.md)資料類型|`Double`|  
  
 在執行除法之前，任何整數數值運算式都會擴展為 `Double`。 如果您將結果指派給整數資料類型，Visual Basic 會嘗試將 `Double` 的結果轉換成該類型。 如果結果不符合該類型，這可能會擲回例外狀況。 特別是，請參閱此說明頁面上的「嘗試除數為零」。  
  
 如果`expression1` 或`expression2`評估為[沒有任何](../../../visual-basic/language-reference/nothing.md)值，則會將它視為零。  
  
## <a name="attempted-division-by-zero"></a>嘗試除數為零  
 如果 `expression2` 評估為零，則 @no__t 1 運算子的行為會因不同的運算元資料類型而有所不同。 下表顯示可能的行為。  
  
|運算元資料類型|如果 `expression2` 為零時的行為|  
|------------------------|---------------------------------------|  
|浮點（`Single` 或 `Double`）|傳回無限大（<xref:System.Double.PositiveInfinity> 或 <xref:System.Double.NegativeInfinity>），如果 `expression1` 也為零，則傳回 <xref:System.Double.NaN> （不是數位）|  
|`Decimal`|擲回 <xref:System.DivideByZeroException>|  
|整數（帶正負號或不帶正負號）|嘗試轉換回整數類資料類型 <xref:System.OverflowException>，因為整數類型無法接受 <xref:System.Double.PositiveInfinity>、<xref:System.Double.NegativeInfinity> 或 <xref:System.Double.NaN>|  
  
> [!NOTE]
> @No__t-0 運算子可以多載 *，這*表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。 如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 這個範例會使用 `/` 運算子來執行浮點除法。 結果為兩個運算元的商。  
  
 [!code-vb[VbVbalrOperators#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#16)]  
  
 上述範例中的運算式會傳回2.5 和3.333333 的值。 請注意，即使兩個運算元都是整數常數，結果一律是浮點（`Double`）。  
  
## <a name="see-also"></a>另請參閱

- [/= 運算子（Visual Basic）](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [\ 運算子（Visual Basic）](../../../visual-basic/language-reference/operators/integer-division-operator.md)
- [運算子結果的資料類型](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)
- [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic 中的算術運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
