---
title: 數值資料類型
ms.date: 07/20/2015
helpviewer_keywords:
- integral types [Visual Basic], Visual Basic
- Short data type [Visual Basic], numeric data types
- Double data type [Visual Basic], numeric data types
- Long data type [Visual Basic], Visual Basic numeric data types
- numbers [Visual Basic], whole
- fractions
- numbers
- whole numbers
- integer numbers
- numbers [Visual Basic], integer
- fractional data types [Visual Basic]
- mantissas, of fractional numbers
- mantissas
- data types [Visual Basic], numeric
- Integer data type [Visual Basic], numeric data types
- exponent, of fractional numbers
- integers [Visual Basic]
- numeric data types [Visual Basic], Visual Basic
- Single data type [Visual Basic], numeric types
- Decimal data type [Visual Basic], numeric data types
ms.assetid: a27bd4d0-7e14-43eb-9cc4-b42eaab323c9
ms.openlocfilehash: dc8b630eebc48e5733344a00664b453360769c0b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346315"
---
# <a name="numeric-data-types-visual-basic"></a>數字資料類型 (Visual Basic)
Visual Basic 提供數個*數值資料類型*來處理各種標記法中的數位。 *整數*類資料類型只代表整數（正、負和零） *，而非整數類型*則代表同時包含整數和小數部分的數位。  
  
 如需顯示 Visual Basic 資料類型並存比較的資料表，請參閱[資料類型](../../../../visual-basic/language-reference/data-types/index.md)。  
  
## <a name="integral-numeric-types"></a>整數數數值型別  
 *整數資料類型*是指只代表沒有小數部分的數位。  
  
 *帶正負*號的整數資料類型是[SByte 資料類型](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)（8位） [、Short 資料類型](../../../../visual-basic/language-reference/data-types/short-data-type.md)（16位）、[整數資料類型](../../../../visual-basic/language-reference/data-types/integer-data-type.md)（32位）和[LONG 資料型別](../../../../visual-basic/language-reference/data-types/long-data-type.md)（64位）。 如果變數一律會儲存整數，而不是小數數位，請將它宣告為其中一種類型。  
  
 不*帶正負*號的整數類資料類型為[Byte 資料類型](../../../../visual-basic/language-reference/data-types/byte-data-type.md)（8位）、 [UShort 資料類型](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)（16位）、 [UInteger 資料類型](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)（32位）和[ULONG 資料型別](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)（64位）。 如果變數包含二進位資料或未知性質的資料，請將它宣告為下列其中一種類型。  
  
### <a name="performance"></a>效能  
 與其他資料類型相比，算數運算比整數類型更快。 使用 Visual Basic 中的 `Integer` 和 `UInteger` 類型，它們的速度最快。  
  
### <a name="large-integers"></a>大整數  
 如果您需要保留大於 `Integer` 資料類型可以保留的整數，您可以改用 `Long` 資料類型。 `Long` 變數可以保存-9223372036854775808 到9223372036854775807之間的數位。 具有 `Long` 的作業會比使用 `Integer`稍微慢一點。  
  
 如果您需要更大的值，您可以使用[Decimal 資料類型](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)。 如果您未使用任何小數位數，您可以在 `Decimal` 變數中保存-79228162514264337593543950335 到79228162514264337593543950335之間的數位。 不過，具有 `Decimal` 數位的作業會比使用任何其他數值資料類型來得慢很多。  
  
### <a name="small-integers"></a>小整數  
 如果您不需要 `Integer` 資料類型的完整範圍，您可以使用 `Short` 資料類型，其中可以包含-32768 到32767之間的整數。 針對最小的整數範圍，`SByte` 資料類型會保存從-128 到127的整數。 如果您有非常大量的變數會保存小型整數，則 common language runtime 有時可以更有效率地儲存您的 `Short` 和 `SByte` 變數，並節省記憶體耗用量。 不過，具有 `Short` 和 `SByte` 的作業會比使用 `Integer`稍微慢一點。  
  
### <a name="unsigned-integers"></a>不帶正負號的整數  
 如果您知道變數永遠不需要保存負數，可以使用不帶正負號的*類型*`Byte`、`UShort`、`UInteger`和 `ULong`。 這些資料類型的每一個都可以保存一個正整數，如同其對應的帶正負號類型（`SByte`、`Short`、`Integer`和 `Long`）。 就效能而言，每個不帶正負號的型別都與對應的帶正負號型別一樣有效率。 特別的是，`UInteger` 共用，`Integer` 區分最有效率的所有基本數值資料類型。  
  
## <a name="nonintegral-numeric-types"></a>非整數數數值型別  
 非整數*類資料類型*是指同時包含整數和小數部分的數位。  
  
 非整數數值資料類型是 `Decimal` （128位固定點）、[單一資料類型](../../../../visual-basic/language-reference/data-types/single-data-type.md)（32位浮點）和[Double 資料類型](../../../../visual-basic/language-reference/data-types/double-data-type.md)（64位浮點）。 這些全都是已簽署的類型。 如果變數可以包含某個分數，請將它宣告為其中一種類型。  
  
 `Decimal` 不是浮點資料類型。 `Decimal` 數位具有二進位整數值和整數縮放因數，可指定值的哪個部分為小數部分。  
  
 您可以針對 money 值使用 `Decimal` 變數。 優點是值的有效位數。 `Double` 資料類型的速度較快，而且需要較少的記憶體，但會受到四捨五入錯誤的要求。 `Decimal` 資料類型會將完整精確度保留28個小數位數。  
  
 浮點（`Single` 和 `Double`）數位的範圍比 `Decimal` 數位大，但可能會受到四捨五入誤差。 浮點類型支援的有效位數比 `Decimal` 少，但是可以代表較大的值。  
  
 非整數數值可以用 mmmEeee 表示，其中 mmm 是*尾數*（有效位數），而 eee 是*指數*（10的乘冪）。 非整數類型的最大正數值為 `Decimal`的 7.9228162514264337593543950335 E + 28、`Single`的 3.4028235 E + 38，以及 `Double`的 1.79769313486231570 E + 308。  
  
### <a name="performance"></a>效能  
 `Double` 是小數資料類型最有效率的方式，因為目前平臺上的處理器會以雙精確度執行浮點運算。 不過，具有 `Double` 的作業不如使用整數類資料類型（例如 `Integer`）的速度快。  
  
### <a name="small-magnitudes"></a>小型巨量  
 對於具有最小可能大小（最接近0）的數位，`Double` 變數可以針對負值將數值和 4.94065645841246544 E-324 保留為小型的 4.94065645841246544 E-324 值。  
  
### <a name="small-fractional-numbers"></a>小小數數位  
 如果您不需要 `Double` 資料類型的完整範圍，您可以使用 `Single` 資料類型，其可從-3.4028235 E + 38 到 3.4028235 E + 38 保存浮點數。 為負數值，`Single` 變數的最小巨量是-1.401298 E-45，正值則為 1.401298 E-45。 如果您有非常大量的變數會保存小型的浮點數，則 common language runtime 有時可以更有效率地儲存 `Single` 變數，並節省記憶體耗用量。  
  
## <a name="see-also"></a>另請參閱

- [基礎資料類型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [字元資料類型](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)
- [其他資料類型](../../../../visual-basic/programming-guide/language-features/data-types/miscellaneous-data-types.md)
- [資料類型的疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [操作說明：呼叫使用不帶正負號類型的 Windows 函式](../../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
