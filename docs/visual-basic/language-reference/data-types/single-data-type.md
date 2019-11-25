---
title: Single 資料類型
ms.date: 07/20/2015
f1_keywords:
- vb.Single
helpviewer_keywords:
- Single data type
- F literal type character [Visual Basic]
- trailing zeros
- real numbers
- literal type characters [Visual Basic], F
- trailing 0 characters [Visual Basic]
- identifier type characters [Visual Basic], !
- single-precision numbers
- '! identifier type character'
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- floating-point numbers [Visual Basic], Single data type
- numbers [Visual Basic], real
- zeros, trailing
- numbers [Visual Basic], floating point
ms.assetid: 224a2795-4cd5-496c-8f7a-a4f05a06d45d
ms.openlocfilehash: 60a688c510f6e36dca5809566b37a388429e18c7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343923"
---
# <a name="single-data-type-visual-basic"></a>字串資料類型 (Visual Basic)

Holds signed IEEE 32-bit (4-byte) single-precision floating-point numbers ranging in value from -3.4028235E+38 through -1.401298E-45 for negative values and from 1.401298E-45 through 3.4028235E+38 for positive values. Single-precision numbers store an approximation of a real number.  
  
## <a name="remarks"></a>備註  

 Use the `Single` data type to contain floating-point values that do not require the full data width of `Double`. In some cases the common language runtime might be able to pack your `Single` variables closely together and save memory consumption.  
  
 `Single` 的預設值為 0。  
  
## <a name="programming-tips"></a>程式設計提示  
  
- **Precision.** When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory. This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator. For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
- **Widening.** The `Single` data type widens to `Double`. This means you can convert `Single` to `Double` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.  
  
- **Trailing Zeros.** The floating-point data types do not have any internal representation of trailing 0 characters. For example, they do not distinguish between 4.2000 and 4.2. Consequently, trailing 0 characters do not appear when you display or print floating-point values.  
  
- **Type Characters.** 將常值類型字元 `F` 附加到常值，會強制其成為 `Single` 資料類型。 將識別項類型字元 `!` 附加到任何識別項，會強制其成為 `Single`。  
  
- **Framework Type.** 在 .NET Framework 中對應的類型為 <xref:System.Single?displayProperty=nameWithType> 結構。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Single?displayProperty=nameWithType>
- [資料類型](../../../visual-basic/language-reference/data-types/index.md)
- [Decimal 資料類型](../../../visual-basic/language-reference/data-types/decimal-data-type.md)
- [Double 資料類型](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [資料類型的疑難排解](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
