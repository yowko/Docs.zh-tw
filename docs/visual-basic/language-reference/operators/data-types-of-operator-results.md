---
title: "運算子結果 (Visual Basic) 的資料類型 |Microsoft 文件"
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
- data types [Visual Basic], operator result data types
- result data types
- operator result data types
- operators [Visual Basic], data types
- data types [Visual Basic], ranges
- operators [Visual Basic], result data types
ms.assetid: 9d524533-e1a1-4aa8-b1b8-622068173d06
caps.latest.revision: 27
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
ms.openlocfilehash: 577be6330cb76da436470c383841a717dd6e3200
ms.lasthandoff: 03/13/2017

---
# <a name="data-types-of-operator-results-visual-basic"></a>運算子結果的資料類型 (Visual Basic)
[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]判斷資料類型的運算元為基礎的運算的結果資料類型。 在某些情況下，這可能是較大的範圍以外的任一個運算元的資料型別。  
  
## <a name="data-type-ranges"></a>資料類型範圍  
 相關的資料類型，順序從最小到最大，範圍如下所示︰  
  
-   [布林](../../../visual-basic/language-reference/data-types/boolean-data-type.md)— 兩個可能值  
  
-   [SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)，[位元組](../../../visual-basic/language-reference/data-types/byte-data-type.md)— 256 個可能的整數值  
  
-   [簡短](../../../visual-basic/language-reference/data-types/short-data-type.md)， [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md) — 65536 (6.5...E + 4) 可能的整數值  
  
-   [整數](../../../visual-basic/language-reference/data-types/integer-data-type.md)， [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md) -4294967296 (4.2...E + 9) 可能的整數值  
  
-   [長](../../../visual-basic/language-reference/data-types/long-data-type.md)， [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md) -18446744073709551615 (1.8...E + 19) 可能的整數值  
  
-   [十進位](../../../visual-basic/language-reference/data-types/decimal-data-type.md)— 1.5...E + 29 可能整數的值，最大範圍 7.9...E + 28 （絕對值）  
  
-   [單一](../../../visual-basic/language-reference/data-types/single-data-type.md)— 最大範圍向...3.4 E + 38 （絕對值）  
  
-   [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) — 最大範圍向...1.7 E + 308 （絕對值）  
  
 如需有關[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]資料類型，請參閱[資料型別](../../../visual-basic/language-reference/data-types/data-type-summary.md)。  
  
 如果運算元等於[Nothing](../../../visual-basic/language-reference/nothing.md)、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]算術運算子會將其視為零。  
  
## <a name="decimal-arithmetic"></a>十進位運算  
 請注意，[十進位](../../../visual-basic/language-reference/data-types/decimal-data-type.md)資料型別不是浮點和整數。  
  
 如果任一運算元的`+`， `–`， `*`， `/`，或`Mod`作業`Decimal`，另一個不是`Single`或`Double`，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]擴展到另一個運算元`Decimal`。 執行中的作業`Decimal`，結果資料類型是`Decimal`。  
  
## <a name="floating-point-arithmetic"></a>浮點算術  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]執行中的大部分浮點算術[雙](../../../visual-basic/language-reference/data-types/double-data-type.md)，這是最有效率的資料類型等這類作業。 不過，如果有一個運算元是[單一](../../../visual-basic/language-reference/data-types/single-data-type.md)，另一個不是`Double`，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]執行中的作業`Single`。 它擴展為適當的資料型別作業前，視每個運算元和結果的該資料類型。  
  
### <a name="-and--operators"></a>/ 和 ^ 運算子  
 `/`運算子定義僅適用於[十進位](../../../visual-basic/language-reference/data-types/decimal-data-type.md)，[單一](../../../visual-basic/language-reference/data-types/single-data-type.md)，和[雙](../../../visual-basic/language-reference/data-types/double-data-type.md)資料型別。 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]作業，而結果會有該資料型別之前，請放大視適當的資料類型的每個運算元。  
  
 下表顯示結果的資料型別`/`運算子。 請注意，此資料表是對稱的。運算元資料類型的給定組合，結果資料類型會是運算元的順序相同。  
  
||||||  
|---|---|---|---|---|  
||`Decimal`|`Single`|`Double`|任何整數類型|  
|`Decimal`|Decimal|Single|Double|Decimal|  
|`Single`|Single|Single|Double|Single|  
|`Double`|Double|Double|Double|Double|  
|任何整數類型|Decimal|Single|Double|Double|  
  
 `^`運算子定義僅適用於`Double`資料型別。 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]將每個運算元，視需要擴展`Double`之前運算和結果資料類型一律為`Double`。  
  
## <a name="integer-arithmetic"></a>整數算術  
 整數運算的結果資料類型取決於運算元的資料型別。 一般而言，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]決定結果資料類型可使用下列原則︰  
  
-   如果二元運算子的兩個運算元具有相同的結果資料類型，擁有該資料型別。 例外狀況是`Boolean`，這要強制`Short`。  
  
-   如果不帶正負號的運算元加入與帶正負號的運算元，結果的帶正負號型別至少有最大範圍其中一個運算元。  
  
-   否則，結果通常會具有較大的兩個運算元資料類型。  
  
 請注意結果資料類型可能不是運算元資料型別相同。  
  
> [!NOTE]
>  結果資料類型不是永遠足以容納作業所產生的所有可能值。 <xref:System.OverflowException>如果值是結果資料類型而言太大，可能會發生例外狀況。</xref:System.OverflowException>  
  
### <a name="unary--and--operators"></a>一元 + 和-運算子  
 下表顯示結果資料類型的兩個一元運算子，`+`和`–`。  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|一元 （unary)`+`|Short|SByte|Byte|Short|UShort|整數|UInteger|Long|ULong|  
|一元 （unary)`–`|Short|SByte|Short|Short|整數|整數|Long|Long|Decimal|  
  
### <a name="-and--operators"></a><\<和 >> 運算子  
 下表顯示結果資料類型的兩種位元移位運算子，`<<`和`>>`。 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]每一個位元移位運算子視為一元運算子的左運算元 （移位的位元模式） 上。  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`<<`, `>>`|Short|SByte|Byte|Short|UShort|整數|UInteger|Long|ULong|  
  
 如果左的運算元是`Decimal`， `Single`， `Double`，或`String`，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]嘗試將它轉換成`Long`之前運算和結果資料類型是`Long`。 右運算元 （要移位的位元位置數目） 必須是`Integer`或擴展至型別`Integer`。  
  
### <a name="binary----and-mod-operators"></a>二進位 +、-、 *、 和 Mod 運算子  
 下表顯示的結果資料類型之二進位檔`+`和`–`運算子和`*`和`Mod`運算子。 請注意，此資料表是對稱的。運算元資料類型的給定組合，結果資料類型會是運算元的順序相同。  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Short|SByte|Short|Short|整數|整數|Long|Long|Decimal|  
|`SByte`|SByte|SByte|Short|Short|整數|整數|Long|Long|Decimal|  
|`Byte`|Short|Short|Byte|Short|UShort|整數|UInteger|Long|ULong|  
|`Short`|Short|Short|Short|Short|整數|整數|Long|Long|Decimal|  
|`UShort`|整數|整數|UShort|整數|UShort|整數|UInteger|Long|ULong|  
|`Integer`|整數|整數|整數|整數|整數|整數|Long|Long|Decimal|  
|`UInteger`|Long|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Long|Long|Long|Long|Long|Long|Long|Long|Decimal|  
|`ULong`|Decimal|Decimal|ULong|Decimal|ULong|Decimal|ULong|Decimal|ULong|  
  
### <a name="-operator"></a>\ 運算子  
 下表顯示結果的資料型別`\`運算子。 請注意，此資料表是對稱的。運算元資料類型的給定組合，結果資料類型會是運算元的順序相同。  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Short|SByte|Short|Short|整數|整數|Long|Long|Long|  
|`SByte`|SByte|SByte|Short|Short|整數|整數|Long|Long|Long|  
|`Byte`|Short|Short|Byte|Short|UShort|整數|UInteger|Long|ULong|  
|`Short`|Short|Short|Short|Short|整數|整數|Long|Long|Long|  
|`UShort`|整數|整數|UShort|整數|UShort|整數|UInteger|Long|ULong|  
|`Integer`|整數|整數|整數|整數|整數|整數|Long|Long|Long|  
|`UInteger`|Long|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Long|Long|Long|Long|Long|Long|Long|Long|Long|  
|`ULong`|Long|Long|ULong|Long|ULong|Long|ULong|Long|ULong|  
  
 如果任一個運算元的`\`運算子是[十進位](../../../visual-basic/language-reference/data-types/decimal-data-type.md)，[單一](../../../visual-basic/language-reference/data-types/single-data-type.md)，或[雙](../../../visual-basic/language-reference/data-types/double-data-type.md)，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]嘗試將它轉換成[長](../../../visual-basic/language-reference/data-types/long-data-type.md)之前運算和結果資料類型是`Long`。  
  
## <a name="relational-and-bitwise-comparisons"></a>關係和位元比較  
 關聯式作業的結果資料類型 (`=`， `<>`， `<`， `>`， `<=`， `>=`) 一律為`Boolean`[布林資料型別](../../../visual-basic/language-reference/data-types/boolean-data-type.md)。 同樣適用於邏輯運算 (`And`， `AndAlso`， `Not`， `Or`， `OrElse`， `Xor`) 上`Boolean`運算元。  
  
 位元邏輯運算的結果資料類型取決於運算元的資料型別。 請注意，`AndAlso`和`OrElse`定義僅適用於`Boolean`，和[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]將轉換為所需的每一個運算元`Boolean`再執行作業。  
  
### <a name="-----and--operators"></a>=, <>, \<, >, \<=, and >= Operators  
 如果這兩個運算元都是`Boolean`，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]認為`True`是小於`False`。 如果是數值類型與`String`，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]會嘗試將`String`至`Double`作業之前。 A`Char`或`Date`運算元只能與相同的資料類型的另一個運算元。 結果資料類型一定是`Boolean`。  
  
### <a name="bitwise-not-operator"></a>位元 Not 運算子  
 下表顯示結果的位元資料型別`Not`運算子。  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Not`|Boolean|SByte|Byte|Short|UShort|整數|UInteger|Long|ULong|  
  
 如果運算元是`Decimal`， `Single`， `Double`，或`String`，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]嘗試將它轉換成`Long`之前運算和結果資料類型是`Long`。  
  
### <a name="bitwise-and-or-and-xor-operators"></a>位元，或者，和 Xor 運算子  
 下表顯示結果的位元資料型別`And`， `Or`，和`Xor`運算子。 請注意，此資料表是對稱的。運算元資料類型的給定組合，結果資料類型會是運算元的順序相同。  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Boolean|SByte|Short|Short|整數|整數|Long|Long|Long|  
|`SByte`|SByte|SByte|Short|Short|整數|整數|Long|Long|Long|  
|`Byte`|Short|Short|Byte|Short|UShort|整數|UInteger|Long|ULong|  
|`Short`|Short|Short|Short|Short|整數|整數|Long|Long|Long|  
|`UShort`|整數|整數|UShort|整數|UShort|整數|UInteger|Long|ULong|  
|`Integer`|整數|整數|整數|整數|整數|整數|Long|Long|Long|  
|`UInteger`|Long|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Long|Long|Long|Long|Long|Long|Long|Long|Long|  
|`ULong`|Long|Long|ULong|Long|ULong|Long|ULong|Long|ULong|  
  
 如果運算元是`Decimal`， `Single`， `Double`，或`String`，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]嘗試將它轉換成`Long`之前運算和結果資料類型會與相同該運算元必須已經過`Long`。  
  
## <a name="miscellaneous-operators"></a>雜項運算子  
 `&`運算子只定義的串連`String`運算元。 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]將轉換為所需的每一個運算元`String`之前運算和結果資料類型一律為`String`。 為了`&`運算子、 所有轉換為`String`會被視為擴展，即使`Option Strict`是`On`。  
  
 `Is`和`IsNot`運算子需要兩個運算元必須是參考型別。 The `TypeOf`...`Is`運算式需要第一個運算元必須是參考型別和資料型別名稱的第二個運算元。 在所有這些案例的結果資料類型是`Boolean`。  
  
 `Like`只定義運算子的模式比對`String`運算元。 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]嘗試轉換為所需的每一個運算元`String`作業之前。 結果資料類型一定是`Boolean`。  
  
## <a name="see-also"></a>另請參閱  
 [資料型別](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [運算子和運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [在 Visual Basic 中的算術運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [在 Visual Basic 中的比較運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [運算子](../../../visual-basic/language-reference/operators/index.md)   
 [在 Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [依功能排列的運算子](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [比較運算子](../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)
