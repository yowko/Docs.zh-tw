---
title: "輸入字元 (Visual Basic) |Microsoft 文件"
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
- '&H prefix for hexadecimal values'
- hexadecimal literals
- F literal type character
- '& identifier type character'
- type characters
- octal literals
- literals, hexadecimal
- '&O prefix for octal values'
- literals, default types
- defaults, literal types
- C literal type character
- type characters, literal
- $ identifier type character
- L literal type character
- UI literal type characters
- default literal types
- D literal type character
- literals, octal
- S literal type character
- '! identifier type character'
- US literal type characters
- '% identifier type character'
- data types [Visual Basic], type characters
- characters, identifier type
- type characters, identifier
- '# identifier type character'
- identifier type characters
- literal type characters
- I literal type character
- R literal type character
- '@ identifier type character'
- UL literal type characters
- literal types, default
ms.assetid: 6353cb9b-6ee4-4af6-a5a8-88ce39f90cc5
caps.latest.revision: 22
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 6e112e7d221ef8e7a660094306bbb242c988e843
ms.lasthandoff: 03/13/2017

---
# <a name="type-characters-visual-basic"></a>類型字元 (Visual Basic)
除了宣告陳述式中指定的資料類型，您可以強制一些程式設計項目使用的資料型別*輸入字元*。 型別字元必須緊接元素中，但沒有任何種類的中介字元。  
  
 型別字元不是項目的名稱的一部分。 定義型別字元的項目可以參考不含型別字元。  
  
## <a name="identifier-type-characters"></a>識別項類型字元  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]提供一組*識別項類型字元*，其中您可以使用宣告中指定變數或常數的資料型別。 下表顯示可用的識別項類型字元，與使用方式的範例。  
  
|識別項類型字元|資料類型|範例|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 存在任何識別項類型字元`Boolean`， `Byte`， `Char`， `Date`， `Object`， `SByte`， `Short`， `UInteger`， `ULong`，或`UShort`資料型別，或任何複合資料類型，例如陣列或結構。  
  
 在某些情況下，您可以附加`$`字元[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]函式，例如`Left$`而不是`Left`，以取得傳回的值型別為`String`。  
  
 在所有情況下，識別項類型字元必須緊接識別項名稱。  
  
## <a name="literal-type-characters"></a>常值類型字元  
 A*常值*是資料類型的特定值的文字表示。  
  
### <a name="default-literal-types"></a>預設常值類型  
 常值的形式通常出現在您的程式碼中決定其資料型別。 下表顯示這些預設型別。  
  
|文字格式的常值|預設資料類型|範例|  
|-----------------------------|-----------------------|-------------|  
|數字，沒有小數部分|`Integer`|`2147483647`|  
|數字，沒有小數部分，太大`Integer`|`Long`|`2147483648`|  
|數字，分數部分|`Double`|`1.2`|  
|以雙引號括住|`String`|`"A"`|  
|數字符號括住|`Date`|`#5/17/1993 9:32 AM#`|  
  
### <a name="forced-literal-types"></a>強制常值型別  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]提供一組*常值類型字元*，您可以使用強制常以外的資料類型的形式來表示。 您可以將字元附加到常值的結尾。 下表顯示可用的常值型別字元與用法的範例。  
  
|常值類型字元|資料類型|範例|  
|----------------------------|---------------|-------------|  
|`S`|`Short`|`I = 347S`|  
|`I`|`Integer`|`J = 347I`|  
|`L`|`Long`|`K = 347L`|  
|`D`|`Decimal`|`X = 347D`|  
|`F`|`Single`|`Y = 347F`|  
|`R`|`Double`|`Z = 347R`|  
|`US`|`UShort`|`L = 347US`|  
|`UI`|`UInteger`|`M = 347UI`|  
|`UL`|`ULong`|`N = 347UL`|  
|`C`|`Char`|`Q = "."C`|  
  
 不常值類型字元存在`Boolean`， `Byte`， `Date`， `Object`， `SByte`，或`String`資料型別，或任何複合資料類型，例如陣列或結構。  
  
 常值也可以使用識別項類型字元 (`%`， `&`， `@`， `!`， `#`， `$`)，可能是變數、 常數和運算式。 不過，常值類型字元 (`S`， `I`， `L`， `D`， `F`， `R`， `C`) 可以僅能搭配常值。  
  
 在所有情況下，常值類型字元必須緊接的常值。  
  
## <a name="hexadecimal-and-octal-literals"></a>十六進位和八進位常值  
 編譯器通常 construes 整數常值為十進位 (基底 10) 數字系統。 您可以強制整數常值是十六進位 (基底 16) 與`&H`前置詞，而且您可以強制為八進位 (基底 8) 與`&O`前置詞。 請依照下列前置詞的數字必須適用於數字系統。 下表將說明這點。  
  
|數字基底|前置詞|有效的數字值|範例|  
|-----------------|------------|------------------------|-------------|  
|十六進位 (基底 16)|`&H`|0-9 和 A-F|`&HFFFF`|  
|八進位 (基底 8)|`&O`|0-7|`&O77`|  
  
 您可以依照前置的常值與常值類型字元。 下列範例示範這點。  
  
```  
Dim counter As Short = &H8000S  
Dim flags As UShort = &H8000US  
```  
  
 在上述範例中，`counter`的十進位值為-32768，和`flags`32768 十進位值。  
  
## <a name="see-also"></a>另請參閱  
 [資料型別](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [基本資料型別](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [實值型別和參考型別](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [在 Visual Basic 中的型別轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [資料類型疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [資料類型](../../../../visual-basic/language-reference/data-types/data-type-summary.md)
