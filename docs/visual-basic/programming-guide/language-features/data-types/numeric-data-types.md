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
ms.openlocfilehash: 8fa88172c9914a071e1b24e959c9030e6d219a30
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="numeric-data-types-visual-basic"></a>數字資料類型 (Visual Basic)
Visual Basic 提供數個*數值資料型別*來處理各種表示相互轉換的數字。 *整數類資料*類型表示只有整數 （正數、 負數和零），和*整數*類型與整數和分數部分代表數字。  
  
 顯示的 Visual Basic 資料類型來並行比較表，請參閱[資料型別](../../../../visual-basic/language-reference/data-types/data-type-summary.md)。  
  
## <a name="integral-numeric-types"></a>整數數字類型  
 *整數類資料類型*則代表不含小數部分的唯一數字。  
  
 *簽署*整數類資料類型是[SByte 資料類型](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)（8 位元）、[短的資料型別](../../../../visual-basic/language-reference/data-types/short-data-type.md)（16 位元）、[整數資料類型](../../../../visual-basic/language-reference/data-types/integer-data-type.md)（32 位元） 和[Long 資料類型](../../../../visual-basic/language-reference/data-types/long-data-type.md)（64 位元）。 如果變數一律是儲存整數，而不是小數的數字，將它宣告為其中一個類型。  
  
 *不帶正負號*整數類資料類型[Byte 資料類型](../../../../visual-basic/language-reference/data-types/byte-data-type.md)（8 位元）、 [UShort 資料類型](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)（16 位元）、 [UInteger 資料類型](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)（32 位元） 和[ULong 資料類型](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)（64 位元）。 如果變數包含二進位資料或未知的性質的資料，請將它做為其中一個這些類型宣告。  
  
### <a name="performance"></a>效能  
 算術運算是整數類資料類型與其他資料型別的更快。 它們是以最快`Integer`和`UInteger`Visual Basic 中的類型。  
  
### <a name="large-integers"></a>大整數  
 如果您需要保存整數大於`Integer`可以保存的資料類型，您可以使用`Long`資料改為輸入。 `Long` 變數可以保留從-9223372036854775808 到 9,223,372,036,854,775,807 的數字。 作業`Long`稍微低於與`Integer`。  
  
 如果您需要更大的值，您可以使用[Decimal 資料類型](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)。 您可以保有數字-79228162514264337593543950335 到 79228162514264337593543950335 中從`Decimal`變數，如果您未使用任何小數位數。 不過，作業`Decimal`數字會慢很多超過其他任何數值資料型別。  
  
### <a name="small-integers"></a>小整數  
 如果您不需要的完整範圍`Integer`資料型別，您可以使用`Short`資料型別，可保存從-32,768 到 32,767 的整數。 最小的整數範圍內，`SByte`資料類型會保留從-128 到 127 的整數。 如果您有非常大量的變數，保存小整數，common language runtime 可以有時候會儲存您`Short`和`SByte`變數儲存記憶體耗用量和更有效率。 不過，作業`Short`和`SByte`稍微低於與`Integer`。  
  
### <a name="unsigned-integers"></a>不帶正負號的整數  
 如果您知道您的變數就永遠不需要保存為負數，您可以使用*不帶正負號類型*`Byte`， `UShort`， `UInteger`，和`ULong`。 每個資料類型可以保存的正整數兩次大小，其對應的帶正負號的類型 (`SByte`， `Short`， `Integer`，和`Long`)。 在效能方面，每個不帶正負號的類型是完全效率和其對應的帶正負號型別一樣。 特別是，`UInteger`與共用`Integer`的所有基本的數值資料類型的最有效率的差別。  
  
## <a name="nonintegral-numeric-types"></a>非整數數值類型  
 *非整數類資料型別*是指代表整數和分數部分的數字。  
  
 非整數數值資料類型為`Decimal`（128 位元固定的點），[單一的資料型別](../../../../visual-basic/language-reference/data-types/single-data-type.md)（32 位元浮點） 和[Double 資料類型](../../../../visual-basic/language-reference/data-types/double-data-type.md)（64 位元浮點數）。 它們都是帶正負號的類型。 如果變數可以包含一小部分，將它宣告為其中一個類型。  
  
 `Decimal` 不是浮點數資料類型。 `Decimal` 數字必須是二進位的整數值，指定值的哪些部分是十進位小數的整數縮放比例。  
  
 您可以使用`Decimal`貨幣值的變數。 優點是值的精確度。 `Double`資料型別會加快，需要較少的記憶體，但它會受制於捨入錯誤。 `Decimal`資料類型會保留完整的精確度為 28 的小數位數。  
  
 浮點數 (`Single`和`Double`) 數字有更大範圍比`Decimal`數字，但可以是受制於捨入錯誤。 浮點類型支援較少的有效位數比`Decimal`但可以代表更大範圍的值。  
  
 非整數的數字值可以表示為 mmmEeee 中, 即 mmm*尾數*（有效位數） 而且 eee*指數*（10 的次方）。 非整數類型的最高的正數值會 7.9228162514264337593543950335 e + 28 `Decimal`，3.4028235 e + 38 `Single`，和 1.79769313486231570 e + 308 `Double`。  
  
### <a name="performance"></a>效能  
 `Double` 是最有效率的分數的資料類型，因為在目前的平台上的處理器執行雙精度浮點數運算。 不過，作業`Double`速度與整數類資料類型，例如`Integer`。  
  
### <a name="small-magnitudes"></a>最小範圍  
 數字最小的可能範圍 （最接近 0），與`Double`變數可以保有數字越小越-4.94065645841246544-324 負值，4.94065645841246544-324 的正數值。  
  
### <a name="small-fractional-numbers"></a>最小分數  
 如果您不需要的完整範圍`Double`資料型別，您可以使用`Single`資料型別，可保存從-3.4028235 e + 38 到 3.4028235 e + 38 浮點數。 最小的範圍為`Single`變數是-1.401298-負數值和 1.401298 45-45 的正數值。 如果您有非常大量的保留小的浮點數的變數時，common language runtime 可以有時候會儲存您`Single`變數儲存記憶體耗用量和更有效率。  
  
## <a name="see-also"></a>另請參閱  
 [基礎資料類型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [字元資料類型](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)  
 [其他資料類型](../../../../visual-basic/programming-guide/language-features/data-types/miscellaneous-data-types.md)  
 [資料類型的疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [操作說明：呼叫使用不帶正負號類型的 Windows 函式](../../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
