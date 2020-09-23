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
ms.openlocfilehash: 317c0862953e7bb866faa4712d42dfd5995ecf35
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086227"
---
# <a name="numeric-data-types-visual-basic"></a>數字資料類型 (Visual Basic)

Visual Basic 提供數種 *數值資料類型* 來處理各種標記法中的數位。 *整數* 類資料類型只代表整數 (正數、 *負數和零) ，而非* 整數類型代表具有整數和小數部分的數位。  
  
 如需顯示 Visual Basic 資料類型的並列比較的資料表，請參閱 [資料類型](../../../language-reference/data-types/index.md)。  
  
## <a name="integral-numeric-types"></a>整數數數值型別  

 *整數資料類型* 是指只代表沒有小數部分之數位的資料類型。  
  
 *帶正負*號的整數資料類型是[SByte 資料類型](../../../language-reference/data-types/sbyte-data-type.md) (8 位) [、Short 資料類型](../../../language-reference/data-types/short-data-type.md) (16 位) 、[整數資料類型](../../../language-reference/data-types/integer-data-type.md) (32 位) 和[LONG 資料型別](../../../language-reference/data-types/long-data-type.md) (64 位) 。 如果變數一律儲存整數而不是小數，請將它宣告為這些類型的其中一種。  
  
 不 *帶正負* 號的整數類資料類型是 (8 位) 的 [位元組資料](../../../language-reference/data-types/byte-data-type.md) 類型、 [UShort 資料類型](../../../language-reference/data-types/ushort-data-type.md) (16 位) 、 [UInteger 資料類型](../../../language-reference/data-types/uinteger-data-type.md) (32 位) 以及 [ULONG 資料型別](../../../language-reference/data-types/ulong-data-type.md) (64 位) 。 如果變數包含二進位資料或未知本質的資料，請將它宣告為這些類型的其中一種。  
  
### <a name="performance"></a>效能  

 使用整數類資料類型比其他資料類型更快的算數運算。 它們在 `Integer` Visual Basic 中是和類型的速度最快 `UInteger` 。  
  
### <a name="large-integers"></a>大型整數  

 如果您需要保留大於 `Integer` 資料類型所能保存的整數，則可以 `Long` 改用資料類型。 `Long` 變數可以保留從-9223372036854775808 到9223372036854775807的數位。 使用的作業 `Long` 會比使用稍微慢一點 `Integer` 。  
  
 如果您需要更大的值，您可以使用 [Decimal 資料類型](../../../language-reference/data-types/decimal-data-type.md)。 `Decimal`如果您未使用任何小數位數，您可以在變數中保存-79228162514264337593543950335 到79228162514264337593543950335的數位。 不過，具有數位的作業 `Decimal` 會比其他任何數值資料類型來得慢很多。  
  
### <a name="small-integers"></a>小整數  

 如果您不需要資料類型的完整範圍 `Integer` ，您可以使用 `Short` 資料類型，該資料類型可以保留從-32768 到32767的整數。 針對最小整數範圍， `SByte` 資料類型會保留從-128 到127的整數。 如果您有非常大量的變數來容納小整數，則 common language runtime 有時可以 `Short` `SByte` 更有效率地儲存和變數，並節省記憶體耗用量。 不過，使用和的作業 `Short` `SByte` 有點慢于 `Integer` 。  
  
### <a name="unsigned-integers"></a>不帶正負號的整數  

 如果您知道變數永遠不需要保留負數，則可以使用不帶正負號的*類型* `Byte` 、、 `UShort` `UInteger` 和 `ULong` 。 這些資料類型的每一個都可以將正整數保留為其對應的帶正負號類型 (`SByte` 、、 `Short` `Integer` 和 `Long`) 兩次。 在效能方面，每個不帶正負號的類型都與其對應的帶正負號型別一樣有效率。 尤其是， `UInteger` 共用的 `Integer` 差異在於最有效率的所有基本數值資料類型。  
  
## <a name="nonintegral-numeric-types"></a>非整數數數值型別  

 非整數資料類型就是代表具有整數和小數部分之數位的*資料類型*。  
  
 非整數數值資料類型是 `Decimal` (128 位的固定點) 、 [單一資料類型](../../../language-reference/data-types/single-data-type.md) (32 位浮點數) ，以及 (64 位浮點數) 的 [Double 資料類型](../../../language-reference/data-types/double-data-type.md) 。 它們都是帶正負號的類型。 如果變數可以包含分數，請將它宣告為這些類型的其中一種。  
  
 `Decimal` 不是浮點資料類型。 `Decimal` 數位具有二進位整數值和整數縮放比例，可指定值的哪個部分是小數小數。  
  
 您可以使用 `Decimal` 變數來取得 money 值。 優點是值的有效位數。 `Double`資料類型的速度較快，而且需要較少的記憶體，但會受到舍入錯誤的要求。 `Decimal`資料類型會將完整的精確度保留為28個小數位數。  
  
 浮點數 (`Single` 和 `Double`) 數位的範圍比數位更大， `Decimal` 但可能受舍入錯誤所需。 浮點數類型支援的有效位數較少 `Decimal` ，但可代表較大範圍的值。  
  
 非整數值可以表示為 mmmEeee，其中 mmm 是) 的 *尾數* (有效位數，而 eee 是 *指數* (10) 的乘冪。 非整數類型的最大正值為 7.9228162514264337593543950335 E + 28 （適用于、 `Decimal` 3.4028235 e + 38 `Single` 、以及 1.79769313486231570 e + 308） `Double` 。  
  
### <a name="performance"></a>效能  

 `Double` 是最有效率的小數資料類型，因為目前平臺上的處理器會以雙精確度執行浮點運算。 不過，使用的作業 `Double` 不像整數類資料類型一樣快 `Integer` 。  
  
### <a name="small-magnitudes"></a>Small 巨量  

 若為具有最小可能幅度 (最接近 0) 的數位，則 `Double` 變數可以將數值以小於-4.94065645841246544 e-324 的數位保留給負值，並針對正值 4.94065645841246544 e-324。  
  
### <a name="small-fractional-numbers"></a>小小小數位數  

 如果您不需要資料類型的完整範圍 `Double` ，您可以使用 `Single` 資料類型，此資料類型可以保留從-3.4028235 e + 38 到 3.4028235 e + 38 的浮點數。 變數的最小巨量為 `Single` -1.401298 e-45 （代表負值）和 1.401298 e-45 （代表正數值）。 如果您有非常大量的變數來保存小型浮點數，則 common language runtime 有時可以 `Single` 更有效率地儲存變數並節省記憶體耗用量。  
  
## <a name="see-also"></a>另請參閱

- [基礎資料類型](elementary-data-types.md)
- [字元資料類型](character-data-types.md)
- [其他資料類型](miscellaneous-data-types.md)
- [疑難排解資料類型的問題](troubleshooting-data-types.md)
- [作法：呼叫不帶正負號的類型的 Windows 函式](../../com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
