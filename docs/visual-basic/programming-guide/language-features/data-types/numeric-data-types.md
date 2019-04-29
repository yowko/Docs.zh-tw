---
title: 數字資料類型 (Visual Basic)
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
ms.openlocfilehash: 75e60cb2a3a934956099ce6fc7d81bf6ecea4d11
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663371"
---
# <a name="numeric-data-types-visual-basic"></a>數字資料類型 (Visual Basic)
Visual Basic 提供數個*數值資料型別*來處理各種表示相互轉換的數字。 *整數*型別代表只有整數 （正數、 負數和零），並*整數*類型表示的整數和小數部分的數字。  
  
 資料表中顯示的 Visual Basic 資料類型的並排顯示比較，請參閱[資料型別](../../../../visual-basic/language-reference/data-types/index.md)。  
  
## <a name="integral-numeric-types"></a>整數數字類型  
 *整數資料類型*是指代表唯一的數字沒有小數部分。  
  
 *簽署*整數資料型別的[SByte 資料類型](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)（8 位元）、[簡短的資料型別](../../../../visual-basic/language-reference/data-types/short-data-type.md)（16 位元）、[整數資料類型](../../../../visual-basic/language-reference/data-types/integer-data-type.md)（32 位元）、 和[Long 資料類型](../../../../visual-basic/language-reference/data-types/long-data-type.md)（64 位元）。 如果變數一律是儲存整數，而不是小數的數字，將它宣告為其中一種類型。  
  
 *不帶正負號*整數類資料類型[Byte 資料類型](../../../../visual-basic/language-reference/data-types/byte-data-type.md)（8 位元）、 [UShort 資料類型](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)（16 位元）、 [UInteger 資料類型](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)（32 位元），以及[ULong 資料類型](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)（64 位元）。 如果變數包含二進位資料或未知的性質的資料，請將它做為其中一個這些類型宣告。  
  
### <a name="performance"></a>效能  
 算術運算會使用比其他資料類型的整數類資料類型更快。 它們是以最快`Integer`和`UInteger`Visual Basic 中的類型。  
  
### <a name="large-integers"></a>大整數  
 如果您需要保存的整數大於`Integer`資料類型，您可以使用`Long`請改為輸入資料。 `Long` 變數可以保留從-9223372036854775808 到 9,223,372,036,854,775,807 的數字。 使用作業`Long`會比使用稍微慢`Integer`。  
  
 如果您需要更大的值，您可以使用[十進位資料類型](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)。 您可以保有數字，介於-79228162514264337593543950335 到 79228162514264337593543950335 中從`Decimal`變數，如果您未使用任何小數位數。 不過，使用作業`Decimal`的數字是比使用其他任何數值資料類型相當慢。  
  
### <a name="small-integers"></a>小整數  
 如果您不需要的全套`Integer`資料類型，您可以使用`Short`資料型別，可保存從-32,768 到 32,767 的整數。 最小的整數範圍內，`SByte`資料類型會保留從-128 到 127 的整數。 如果您有非常大量的保留小整數的變數時，common language runtime 可以有時會儲存您`Short`和`SByte`變數更有效率且節省記憶體耗用量。 不過，使用作業`Short`並`SByte`會比使用有點慢`Integer`。  
  
### <a name="unsigned-integers"></a>不帶正負號的整數  
 如果您知道您的變數就永遠不需要保存負數的數字，您可以使用*類型不帶正負號*`Byte`， `UShort`， `UInteger`，和`ULong`。 每一種資料類型可以保留正整數大兩倍，其對應的帶正負號的類型 (`SByte`， `Short`， `Integer`，和`Long`)。 在效能方面，每個不帶正負號的類型是完全成使用效率比其對應的帶正負號類型。 特別是，`UInteger`與共用`Integer`的所有基本數字資料類型的最有效率的差異。  
  
## <a name="nonintegral-numeric-types"></a>非整數的數字類型  
 *非整數資料型別*所表示的整數和小數部分的數字。  
  
 非整數數值資料類型`Decimal`（128 位元固定的點），[單一的資料類型](../../../../visual-basic/language-reference/data-types/single-data-type.md)（32 位元浮點數），以及[Double 資料型別](../../../../visual-basic/language-reference/data-types/double-data-type.md)（64 位元浮點數）。 它們都是帶正負號的類型。 如果變數可以包含一小部分，將它宣告為其中一種類型。  
  
 `Decimal` 不是浮點資料類型。 `Decimal` 數字具有二進位整數值，並指定值的哪些部分是十進位小數的整數縮放比例。  
  
 您可以使用`Decimal`貨幣值的變數。 優點是值的有效位數。 `Double`資料型別比較快，而且需要較少的記憶體，但是它會受制於捨入錯誤。 `Decimal`資料類型會保留完整的精確度，到 28 的小數位數。  
  
 浮點數 (`Single`並`Double`) 數字具有較大的範圍比`Decimal`數字，但可能會受制於捨入錯誤。 浮點型別支援較少的有效位數比`Decimal`，但可以代表大的大小的值。  
  
 非整數數字的值可以表示為 mmmEeee 中, 即 mmm*尾數*（有效位數），而且 eee*指數*（10 的乘冪）。 非整數類型的最高的正值是 7.9228162514264337593543950335 e + 28 `Decimal`，3.4028235E + 38 `Single`，和 1.79769313486231570 e + 308 `Double`。  
  
### <a name="performance"></a>效能  
 `Double` 是最有效率的小數點後的資料類型，因為在目前的平台上的處理器執行雙精確度浮點數運算。 不過，使用作業`Double`不是最快的速度與整數類資料類型，例如`Integer`。  
  
### <a name="small-magnitudes"></a>最小範圍  
 最小的可能範圍 （最接近 0），使用的數字`Double`變數可以保有數字越小越-4.94065645841246544-324 負值，4.94065645841246544-324 的正數值。  
  
### <a name="small-fractional-numbers"></a>最小分數  
 如果您不需要的全套`Double`資料類型，您可以使用`Single`資料型別，可保存從-3.4028235E + 38 到 3.4028235E + 38 浮點數。 最小的範圍為`Single`變數是-1.401298E-45 的負數值，以及從 1.401298E-45 的正數值。 如果您有非常大量的保留小的浮點數的變數時，common language runtime 可以有時會儲存您`Single`變數更有效率且節省記憶體耗用量。  
  
## <a name="see-also"></a>另請參閱

- [基礎資料類型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [字元資料類型](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)
- [其他資料類型](../../../../visual-basic/programming-guide/language-features/data-types/miscellaneous-data-types.md)
- [資料類型的疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [如何：呼叫使用不帶正負號類型的 Windows 函式](../../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
