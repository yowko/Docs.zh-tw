---
title: / 運算子
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
ms.openlocfilehash: 765a80d45908e0ecf17e4c21b748dbf6b2a4c0f5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867039"
---
# <a name="-operator-visual-basic"></a>/ 運算子 (Visual Basic)

兩數相除並傳回浮點結果。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
expression1 / expression2  
```  
  
## <a name="parts"></a>組件  

 `expression1`  
 必要。 任何數值運算式。  
  
 `expression2`  
 必要。 任何數值運算式。  
  
## <a name="supported-types"></a>支援的型別  

 所有數數值型別，包括不帶正負號的和浮點數類型，以及 `Decimal` 。  
  
## <a name="result"></a>結果  

 結果是除以的完整商 `expression1` `expression2` ，包含任何餘數。  
  
 [\ 運算子 (Visual Basic) ](integer-division-operator.md)會傳回整數商，這會捨棄餘數。  
  
## <a name="remarks"></a>備註  

 結果的資料類型取決於運算元的類型。 下表顯示如何決定結果的資料類型。  
  
|運算元資料類型|結果資料類型|  
|------------------------|----------------------|  
|這兩個運算式都是整數資料類型 ([SByte](../data-types/sbyte-data-type.md)、 [Byte](../data-types/byte-data-type.md)、 [Short](../data-types/short-data-type.md)、 [UShort](../data-types/ushort-data-type.md)、 [Integer](../data-types/integer-data-type.md)、 [UInteger](../data-types/uinteger-data-type.md)、 [Long](../data-types/long-data-type.md)、 [ULong](../data-types/ulong-data-type.md)) |`Double`|  
|一個運算式是 [單一](../data-types/single-data-type.md) 資料類型，另一個則不是 [雙精度浮點數](../data-types/double-data-type.md)|`Single`|  
|其中一個運算式是[Decimal](../data-types/decimal-data-type.md)資料類型，另一個則不是[單一](../data-types/single-data-type.md)或[雙精度浮點數](../data-types/double-data-type.md)。|`Decimal`|  
|任一個運算式是 [Double](../data-types/double-data-type.md) 資料類型|`Double`|  
  
 在執行除法之前，任何整數數值運算式都會擴展至 `Double` 。 如果您將結果指派給整數資料類型，Visual Basic 會嘗試將結果轉換 `Double` 為該類型。 如果結果不符合該類型，這可能會擲回例外狀況。 特別是，請參閱此說明頁面上的「嘗試零除」。  
  
 如果 `expression1` 或 `expression2` 評估為 [Nothing](../nothing.md)，則會將其視為零。  
  
## <a name="attempted-division-by-zero"></a>嘗試除以零  

 如果 `expression2` 評估為零， `/` 運算子的行為會因不同的運算元資料類型而有所不同。 下表顯示可能的行為。  
  
|運算元資料類型|如果 `expression2` 為零，則為行為|  
|------------------------|---------------------------------------|  
|浮點數 (`Single` 或 `Double`) |<xref:System.Double.PositiveInfinity>如果也是零，則傳回無限大 (或 <xref:System.Double.NegativeInfinity>) ，或 <xref:System.Double.NaN> (非數位) `expression1`|  
|`Decimal`|拋出 <xref:System.DivideByZeroException>|  
|整數 (帶正負號或不帶正負號的) |<xref:System.OverflowException>因為整數類資料類型無法接受 <xref:System.Double.PositiveInfinity> 、或，所以嘗試轉換回整數類資料類型 <xref:System.Double.NegativeInfinity><xref:System.Double.NaN>|  
  
> [!NOTE]
> 可以多載 `/` 運算子*overloaded*，這表示當運算元具有該類別或結構的型別時，類別或結構可以重新定義其行為。 如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  

 這個範例會使用 `/` 運算子來執行浮點除法。 結果會是兩個運算元的商。  
  
 [!code-vb[VbVbalrOperators#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#16)]  
  
 上述範例中的運算式傳回的值為2.5 和3.333333。 請注意， `Double` 即使這兩個運算元都是整數常數，但結果一律為浮點數 () 。  
  
## <a name="see-also"></a>另請參閱

- [/= 運算子 (Visual Basic) ](floating-point-division-assignment-operator.md)
- [\ 運算子 (Visual Basic) ](integer-division-operator.md)
- [運算子結果的資料類型](data-types-of-operator-results.md)
- [算術運算子](arithmetic-operators.md)
- [Visual Basic 中的運算子優先順序](operator-precedence.md)
- [依功能列出運算子](operators-listed-by-functionality.md)
- [Visual Basic 的算術運算子](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
