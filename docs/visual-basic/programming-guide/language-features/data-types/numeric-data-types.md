---
title: "數值資料類型 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- integral types, Visual Basic
- Short data type, numeric data types
- Double data type, numeric data types
- Long data type, Visual Basic numeric data types
- numbers, whole
- fractions
- numbers
- whole numbers
- integer numbers
- numbers, integer
- fractional data types
- mantissas, of fractional numbers
- mantissas
- data types [Visual Basic], numeric
- Integer data type, numeric data types
- exponent, of fractional numbers
- integers
- numeric data types, Visual Basic
- Single data type, numeric types
- Decimal data type, numeric data types
ms.assetid: a27bd4d0-7e14-43eb-9cc4-b42eaab323c9
caps.latest.revision: 25
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3c3098370b8d9dcb6aafcb06dcfb8f4e144b899a
ms.lasthandoff: 03/13/2017

---
# <a name="numeric-data-types-visual-basic"></a>數字資料類型 (Visual Basic)
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]提供數個*數值資料型別*來處理各種表示相互轉換的數字。 *整數類資料*類型表示只有整數 （正數、 負數和零），和*整數*類型表示的數字的整數和分數部分。  
  
 顯示由並排比較資料表[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]資料類型，請參閱[資料型別](../../../../visual-basic/language-reference/data-types/data-type-summary.md)。  
  
## <a name="integral-numeric-types"></a>整數數字類型  
 *整數類資料類型*」 用來表示沒有小數部分的唯一數字。  
  
 *簽署*整數類資料類型是[SByte 資料類型](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)（8 位元）、[簡短的資料型別](../../../../visual-basic/language-reference/data-types/short-data-type.md)（16 位元）、[整數資料類型](../../../../visual-basic/language-reference/data-types/integer-data-type.md)（32 位元） 和[Long 資料型別](../../../../visual-basic/language-reference/data-types/long-data-type.md)（64 位元）。 如果變數一律是儲存整數，而不是小數的數字，將它宣告為其中一種類型。  
  
 *不帶正負號*整數類資料類型[Byte 資料類型](../../../../visual-basic/language-reference/data-types/byte-data-type.md)（8 位元）、 [UShort 資料類型](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)（16 位元）、 [UInteger 資料類型](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)（32 位元） 和[ULong 資料類型](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)（64 位元）。 如果變數包含二進位資料或未知的性質的資料，將它宣告為其中一種類型。  
  
### <a name="performance"></a>效能  
 算術運算是整數類資料類型與其他資料型別的更快。 它們是以最快`Integer`和`UInteger`中的型別[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。  
  
### <a name="large-integers"></a>大整數  
 如果您需要保存整數大於`Integer`可以保存的資料類型，您可以使用`Long`請改為輸入資料。 `Long`變數可以保留從-9223372036854775808 到 9223372036854775807 的數字。 作業`Long`稍微低於與`Integer`。  
  
 如果您需要更大的值，您可以使用[Decimal 資料型別](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)。 您可以保有數字-79228162514264337593543950335 到 79228162514264337593543950335 中從`Decimal`變數，如果您不使用任何小數位數。 不過，作業`Decimal`數字會慢很多比其他任何數值資料型別。  
  
### <a name="small-integers"></a>小整數  
 如果您不需要完整的`Integer`資料型別，您可以使用`Short`資料型別，可以用來保留從-32768 到 32767 的整數。 最小的整數範圍內，`SByte`資料型別可保留從-128 到 127 的整數。 如果您有非常大量的保存小整數變數，有時可以儲存 common language runtime 程式`Short`和`SByte`變數更有效率且節省記憶體耗用量。 不過，作業`Short`和`SByte`慢比使用`Integer`。  
  
### <a name="unsigned-integers"></a>不帶正負號的整數  
 如果您知道，變數就永遠不需要保存負的數字，您可以使用*不帶正負號型別*`Byte`， `UShort`， `UInteger`，和`ULong`。 每一種資料類型可以保留正整數兩次大小，其對應的帶正負號的類型 (`SByte`， `Short`， `Integer`，和`Long`)。 在效能方面，每個不帶正負號的類型的處理效率都與其對應的帶正負號型別。 特別是，`UInteger`與共用`Integer`的差別是最有效率的所有基本的數值資料類型。  
  
## <a name="nonintegral-numeric-types"></a>非整數的數字類型  
 *非整數類資料型別*是指代表具有整數和分數部分的數字。  
  
 非整數數值資料型別`Decimal`（128 位元固定的點），[單一資料型別](../../../../visual-basic/language-reference/data-types/single-data-type.md)（32 位元浮點數），和[Double 資料型別](../../../../visual-basic/language-reference/data-types/double-data-type.md)（64 位元浮點數）。 是帶正負號的型別。 如果變數可以包含一小部分，將它宣告為其中一種類型。  
  
 `Decimal`不是浮點數資料類型。 `Decimal`數字有二進位整數值，並指定值的部分是十進位小數的整數縮放比例。  
  
 您可以使用`Decimal`貨幣值的變數。 優點是值的精確度。 `Double`資料型別比較快，而且需要較少的記憶體，但是它會受制於捨入錯誤。 `Decimal`資料類型會保留至 28 位小數的正確性。  
  
 浮點數 (`Single`和`Double`) 數字有更大範圍比`Decimal`數字，但可能會受限於捨入錯誤。 浮點類型支援較少的有效位數比`Decimal`但可以代表更大範圍的值。  
  
 非整數的數字值中能表示為 mmmEeee，即 mmm*尾數*（有效位數） 和 eee 是*指數*（10 的次方）。 非整數類型的最高的正值是 7.9228162514264337593543950335 e + 28 `Decimal`，3.4028235 e + 38 `Single`，和 1.79769313486231570 e + 308 `Double`。  
  
### <a name="performance"></a>效能  
 `Double`是最有效率的小數點後的資料型別，因為目前的平台上的處理器執行雙精度浮點數運算。 不過，作業`Double`速度與整數類資料型別，例如`Integer`。  
  
### <a name="small-magnitudes"></a>最小範圍  
 數字的最小的可能範圍 （最接近 0），`Double`變數可以保有數字越小越-4.94065645841246544 e-324 的負數值和 4.94065645841246544-324 的正數值。  
  
### <a name="small-fractional-numbers"></a>最小分數  
 如果您不需要完整的`Double`資料型別，您可以使用`Single`資料型別，可以用來保留從-3.4028235 e + 38 到 3.4028235 e + 38 的浮點數。 最小的範圍為`Single`變數是-1.401298 e-45 的負數值，以及從 1.401298 e-45 的正數值。 如果您有非常大量的保留小的浮點數的變數，有時可以儲存 common language runtime 程式`Single`變數更有效率且節省記憶體耗用量。  
  
## <a name="see-also"></a>另請參閱  
 [基本資料型別](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [字元資料類型](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)   
 [其他資料類型](../../../../visual-basic/programming-guide/language-features/data-types/miscellaneous-data-types.md)   
 [資料類型疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [如何：呼叫使用不帶正負號類型的 Windows 函式](../../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
