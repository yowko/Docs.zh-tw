---
title: 運算子結果的資料類型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], operator result data types
- result data types [Visual Basic]
- operator result data types [Visual Basic]
- operators [Visual Basic], data types
- data types [Visual Basic], ranges
- operators [Visual Basic], result data types
ms.assetid: 9d524533-e1a1-4aa8-b1b8-622068173d06
ms.openlocfilehash: 135c44217debcddb15fd4cef7e73ca2f98903c43
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44221736"
---
# <a name="data-types-of-operator-results-visual-basic"></a>運算子結果的資料類型 (Visual Basic)
Visual Basic 決定結果資料類型的運算元資料類型為基礎的作業。 在某些情況下，這可能是較大的範圍以外的任一個運算元的資料類型。  
  
## <a name="data-type-ranges"></a>資料類型範圍  
 相關的資料類型，順序從最小到最大，範圍如下所示：  
  
-   [布林](../../../visual-basic/language-reference/data-types/boolean-data-type.md)— 兩個可能的值  
  
-   [SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)，[位元組](../../../visual-basic/language-reference/data-types/byte-data-type.md)— 256 個可能的整數值  
  
-   [簡短](../../../visual-basic/language-reference/data-types/short-data-type.md)， [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md) — 65,536 (6.5...E + 4) 可能的整數值  
  
-   [整數](../../../visual-basic/language-reference/data-types/integer-data-type.md)， [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md) -4294967296 (4.2...E + 9) 可能的整數值  
  
-   [長](../../../visual-basic/language-reference/data-types/long-data-type.md)， [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md) -18446744073709551615 (1.8...E + 19) 可能的整數值  
  
-   [十進位](../../../visual-basic/language-reference/data-types/decimal-data-type.md)-1.5...E + 29 可能整數的值，最大範圍 7.9...E + 28 （絕對值）  
  
-   [單一](../../../visual-basic/language-reference/data-types/single-data-type.md)— 最大範圍向...3.4 E + 38 （絕對值）  
  
-   [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) — 最大範圍向...1.7 E + 308 （絕對值）  
  
 如需有關 Visual Basic 資料類型的詳細資訊，請參閱 <<c0> [ 資料型別](../../../visual-basic/language-reference/data-types/index.md)。  
  
 如果運算元評估為[Nothing](../../../visual-basic/language-reference/nothing.md)，Visual Basic 算術運算子會將其視為零。  
  
## <a name="decimal-arithmetic"></a>十進位的算術運算  
 請注意，[十進位](../../../visual-basic/language-reference/data-types/decimal-data-type.md)資料類型既不是浮點數或整數。  
  
 如果任一個運算元`+`， `–`， `*`， `/`，或`Mod`作業`Decimal`，另一個不是`Single`或`Double`，Visual Basic 可擴展其他運算元`Decimal`. 它會執行中的作業`Decimal`，並將結果資料類型是`Decimal`。  
  
## <a name="floating-point-arithmetic"></a>浮點算術  
 Visual Basic 執行中的大部分浮點算術[Double](../../../visual-basic/language-reference/data-types/double-data-type.md)，這是最有效率的資料類型進行此類作業。 不過，如果有一個運算元[單一](../../../visual-basic/language-reference/data-types/single-data-type.md)，另一個不是`Double`，Visual Basic 執行中的作業`Single`。 它將視作業之前，適當的資料類型的每個運算元的擴展，結果將會有該資料型別。  
  
### <a name="-and--operators"></a>/ 和 ^ 運算子  
 `/`僅適用於定義運算子[十進位](../../../visual-basic/language-reference/data-types/decimal-data-type.md)，[單一](../../../visual-basic/language-reference/data-types/single-data-type.md)，和[Double](../../../visual-basic/language-reference/data-types/double-data-type.md)資料型別。 Visual Basic 可擴展視作業之前，適當的資料類型的每個運算元和結果的該資料類型。  
  
 下表顯示結果的資料型別`/`運算子。 請注意，此資料表是對稱;針對指定的運算元資料類型的組合，將結果資料類型是不論運算元的順序相同。  
  
||||||  
|---|---|---|---|---|  
||`Decimal`|`Single`|`Double`|任何整數類型|  
|`Decimal`|Decimal|Single|Double|Decimal|  
|`Single`|Single|Single|Double|Single|  
|`Double`|Double|Double|Double|Double|  
|任何整數類型|Decimal|Single|Double|Double|  
  
 `^`僅適用於定義運算子`Double`資料型別。 Visual Basic 將擴展為所需的每個運算元`Double`作業和資料類型一定是結果之前`Double`。  
  
## <a name="integer-arithmetic"></a>整數算術  
 整數運算的結果資料類型取決於資料類型的運算元。 一般情況下，Visual Basic 會使用下列原則來決定結果資料類型：  
  
-   如果二元運算子的兩個運算元具有相同的結果資料類型，擁有該資料型別。 例外狀況是`Boolean`，這要強制`Short`。  
  
-   如果帶正負號的運算元，參與的不帶正負號的運算元，結果的帶正負號的類型至少有最大範圍做為任一個運算元。  
  
-   否則，結果通常會具有較大的兩個運算元資料類型。  
  
 請注意結果資料類型可能不會做為任一個運算元資料類型相同。  
  
> [!NOTE]
>  將結果資料類型不一定大到足以保留作業所產生的所有可能的值。 <xref:System.OverflowException>如果值太大的結果資料類型，會發生例外狀況。  
  
### <a name="unary--and--operators"></a>一元 （unary) + 和-運算子  
 下表顯示結果資料類型的兩個的一元 （unary） 運算子，如`+`和`–`。  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|一元 （unary) `+`|Short|SByte|Byte|Short|UShort|整數|UInteger|Long|ULong|  
|一元 （unary) `–`|Short|SByte|Short|Short|整數|整數|Long|Long|Decimal|  
  
### <a name="-and--operators"></a><\< 和 >> 運算子  
 下表顯示結果資料類型的兩個的位元移位運算子，如`<<`和`>>`。 Visual Basic 會視為一元運算子的左運算元 （要移位的位元模式） 中的每一個位元移位運算子。  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`<<`, `>>`|Short|SByte|Byte|Short|UShort|整數|UInteger|Long|ULong|  
  
 如果左運算元`Decimal`， `Single`， `Double`，或`String`，Visual Basic 會嘗試將它轉換成`Long`作業和資料類型的結果之前`Long`。 （要移位的位元位置數目） 的右運算元必須是`Integer`的類型，可擴展為`Integer`。  
  
### <a name="binary----and-mod-operators"></a>二進位 +、-、 *、 和 Mod 運算子  
 下表顯示的結果資料類型之二進位檔`+`並`–`運算子以及`*`和`Mod`運算子。 請注意，此資料表是對稱;針對指定的運算元資料類型的組合，將結果資料類型是不論運算元的順序相同。  
  
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
 下表顯示結果的資料型別`\`運算子。 請注意，此資料表是對稱;針對指定的運算元資料類型的組合，將結果資料類型是不論運算元的順序相同。  
  
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
  
 如果的任一個運算元`\`操作員[十進位](../../../visual-basic/language-reference/data-types/decimal-data-type.md)，[單一](../../../visual-basic/language-reference/data-types/single-data-type.md)，或[Double](../../../visual-basic/language-reference/data-types/double-data-type.md)，Visual Basic 會嘗試將它轉換成[Long](../../../visual-basic/language-reference/data-types/long-data-type.md)作業和資料類型的結果之前`Long`。  
  
## <a name="relational-and-bitwise-comparisons"></a>關聯式與位元的比較  
 關聯式作業的結果資料類型 (`=`， `<>`， `<`， `>`， `<=`， `>=`) 一律`Boolean`[布林資料型別](../../../visual-basic/language-reference/data-types/boolean-data-type.md)。 這也適用於邏輯作業 (`And`， `AndAlso`， `Not`， `Or`， `OrElse`， `Xor`) 上`Boolean`運算元。  
  
 位元邏輯運算的結果資料類型取決於資料類型的運算元。 請注意，`AndAlso`並`OrElse`定義僅適用於`Boolean`，和 Visual Basic 會將轉換為所需的每一個運算元`Boolean`之前執行此作業。  
  
### <a name="-----and--operators"></a>=、 <>， \<，>， \<= 和 > = 運算子  
 如果兩個運算元都`Boolean`，Visual Basic 會考慮`True`要小於`False`。 如果為數值類型相較於`String`，Visual Basic 會嘗試將`String`到`Double`作業之前。 A`Char`或`Date`運算元只能與相同的資料類型的另一個運算元。 結果資料類型一定是`Boolean`。  
  
### <a name="bitwise-not-operator"></a>位元 Not 運算子  
 下表顯示的結果資料類型的位元`Not`運算子。  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Not`|Boolean|SByte|Byte|Short|UShort|整數|UInteger|Long|ULong|  
  
 如果運算元`Decimal`， `Single`， `Double`，或`String`，Visual Basic 會嘗試將它轉換成`Long`作業和資料類型的結果之前`Long`。  
  
### <a name="bitwise-and-or-and-xor-operators"></a>位元，或者，和 Xor 運算子  
 下表顯示的結果資料類型的位元`And`， `Or`，和`Xor`運算子。 請注意，此資料表是對稱;針對指定的運算元資料類型的組合，將結果資料類型是不論運算元的順序相同。  
  
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
  
 如果運算元`Decimal`， `Single`， `Double`，或`String`，Visual Basic 會嘗試將它轉換成`Long`之前運算和結果資料類型會與相同該運算元必須已經被`Long`。  
  
## <a name="miscellaneous-operators"></a>雜項運算子  
 `&`運算子只定義的串連`String`運算元。 Visual Basic 會將轉換為所需的每個運算元`String`作業和資料類型一定是結果之前`String`。 針對目的`&`運算子、 所有轉換成`String`會被視為擴展，即使`Option Strict`是`On`。  
  
 `Is`和`IsNot`運算子需要兩個運算元必須是參考型別。 `TypeOf`...`Is`運算式必須是參考類型的第一個運算元與第二個運算元必須是資料型別名稱。 在所有這些案例的結果資料類型是`Boolean`。  
  
 `Like`定義運算子只用於模式比對的`String`運算元。 Visual Basic 會嘗試將視每個運算元`String`作業之前。 結果資料類型一定是`Boolean`。  
  
## <a name="see-also"></a>另請參閱  
 [資料類型](../../../visual-basic/language-reference/data-types/index.md)  
 [運算子和運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [在 Visual Basic 中的算術運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [在 Visual Basic 中的比較運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [運算子](../../../visual-basic/language-reference/operators/index.md)  
 [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [比較運算子](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)
