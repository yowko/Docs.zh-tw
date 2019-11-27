---
title: 運算子結果的資料類型
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], operator result data types
- result data types [Visual Basic]
- operator result data types [Visual Basic]
- operators [Visual Basic], data types
- data types [Visual Basic], ranges
- operators [Visual Basic], result data types
ms.assetid: 9d524533-e1a1-4aa8-b1b8-622068173d06
ms.openlocfilehash: 3867d433ea5f9a6effe70db0ff4162390fb50b5c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331461"
---
# <a name="data-types-of-operator-results-visual-basic"></a>運算子結果的資料類型 (Visual Basic)
Visual Basic 根據運算元的資料類型來決定作業的結果資料類型。 在某些情況下，這可能是比任一運算元的範圍更大的資料類型。  
  
## <a name="data-type-ranges"></a>資料類型範圍  
 相關資料類型的範圍是從最小到最大的順序，如下所示：  
  
- [Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) -兩個可能的值  
  
- [SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)， [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md) -256 可能的整數值  
  
- [Short](../../../visual-basic/language-reference/data-types/short-data-type.md)、 [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md) —65536（6.5 ... E + 4）可能的整數值  
  
- [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)、 [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md) -4294967296 （4.2 ... E + 9）可能的整數值  
  
- [Long](../../../visual-basic/language-reference/data-types/long-data-type.md)、 [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md) -18446744073709551615 （1.8 ... E + 19）可能的整數值  
  
- [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) -1.5 ... e + 29 可能的整數值，最大範圍 7.9 ... e + 28 （絕對值）  
  
- [單一](../../../visual-basic/language-reference/data-types/single-data-type.md)-最大範圍 3.4 ... E + 38 （絕對值）  
  
- [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) —最大範圍 1.7 ... E + 308 （絕對值）  
  
 如需 Visual Basic 資料類型的詳細資訊，請參閱[資料類型](../../../visual-basic/language-reference/data-types/index.md)。  
  
 如果運算元評估為不是[任何](../../../visual-basic/language-reference/nothing.md)值，則 Visual Basic 算術運算子會將它視為零。  
  
## <a name="decimal-arithmetic"></a>十進位算術  
 請注意， [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)資料類型既不是浮點也不是整數。  
  
 如果 `+`、`–`、`*`、`/`或 `Mod` 運算的任一運算元都是 `Decimal`，而另一個不是 `Single` 或 `Double`，Visual Basic 將另一個運算元擴大至 `Decimal`。 它會在 `Decimal`中執行作業，並 `Decimal`結果資料類型。  
  
## <a name="floating-point-arithmetic"></a>浮點算術  
 Visual Basic 會在[雙精度](../../../visual-basic/language-reference/data-types/double-data-type.md)浮點數中執行大部分的浮點算數運算，這是這類作業最有效率的資料類型。 不過，如果一個運算元是[Single](../../../visual-basic/language-reference/data-types/single-data-type.md) ，而另一個不是 `Double`，Visual Basic 會在 `Single`中執行此作業。 它會視需要將每個運算元擴展至作業之前的適當資料類型，而結果會有該資料類型。  
  
### <a name="-and--operators"></a>/和 ^ 運算子  
 `/` 運算子只會針對[Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)、 [Single](../../../visual-basic/language-reference/data-types/single-data-type.md)和[Double](../../../visual-basic/language-reference/data-types/double-data-type.md)資料類型來定義。 Visual Basic 會視需要將每個運算元擴展至作業之前的適當資料類型，而結果會有該資料類型。  
  
 下表顯示 `/` 運算子的結果資料類型。 請注意，這是對稱的資料表;若為指定的運算元資料類型組合，不論運算元的順序為何，結果資料類型都是相同的。  
  
||||||  
|---|---|---|---|---|  
||`Decimal`|`Single`|`Double`|任何整數類型|  
|`Decimal`|Decimal|Single|Double|Decimal|  
|`Single`|Single|Single|Double|Single|  
|`Double`|Double|Double|Double|Double|  
|任何整數類型|Decimal|Single|Double|Double|  
  
 `^` 運算子只會針對 `Double` 資料類型定義。 Visual Basic 會視需要擴展每個運算元，以便在作業之前 `Double`，而結果資料類型一律會 `Double`。  
  
## <a name="integer-arithmetic"></a>整數算術  
 整數運算的結果資料類型取決於運算元的資料類型。 一般來說，Visual Basic 會使用下列原則來決定結果資料類型：  
  
- 如果二元運算子的兩個運算元具有相同的資料類型，則結果會有該資料類型。 `Boolean`，會強制 `Short`例外狀況。  
  
- 如果不帶正負號的運算元參與了帶正負號的運算元，則結果會具有已簽署的類型，且其範圍至少會與任一運算元相同。  
  
- 否則，結果通常會有兩個運算元資料類型中較大的一個。  
  
 請注意，結果資料類型可能不會與任一運算元資料類型相同。  
  
> [!NOTE]
> 結果資料類型的大小不一定足以保存作業所產生的所有可能值。 如果值對結果資料類型而言太大，可能會發生 <xref:System.OverflowException> 例外狀況。  
  
### <a name="unary--and--operators"></a>一元 + 和–運算子  
 下表顯示兩個一元運算子的結果資料類型，`+` 和 `–`。  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|一元 `+`|Short|SByte|位元組|Short|UShort|整數|UInteger|Long|ULong|  
|一元 `–`|Short|SByte|Short|Short|整數|整數|Long|Long|Decimal|  
  
### <a name="-and--operators"></a><\< 和 > > 運算子  
 下表顯示兩個位移位運算子的結果資料類型，`<<` 和 `>>`。 Visual Basic 會將每個位移位運算子視為其左運算元的一元運算子（要移位的位模式）。  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`<<`, `>>`|Short|SByte|位元組|Short|UShort|整數|UInteger|Long|ULong|  
  
 如果左運算元是 `Decimal`、`Single`、`Double`或 `String`，Visual Basic 會嘗試先將它轉換成 `Long` 再進行運算，而且結果資料類型是 `Long`。 右運算元（要移位的位位置數目）必須 `Integer` 或擴大為 `Integer`的類型。  
  
### <a name="binary----and-mod-operators"></a>Binary +、–、\*和 Mod 運算子  
 下表顯示 binary `+` 和 `–` 運算子以及 `*` 和 `Mod` 運算子的結果資料類型。 請注意，這是對稱的資料表;若為指定的運算元資料類型組合，不論運算元的順序為何，結果資料類型都是相同的。  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Short|SByte|Short|Short|整數|整數|Long|Long|Decimal|  
|`SByte`|SByte|SByte|Short|Short|整數|整數|Long|Long|Decimal|  
|`Byte`|Short|Short|位元組|Short|UShort|整數|UInteger|Long|ULong|  
|`Short`|Short|Short|Short|Short|整數|整數|Long|Long|Decimal|  
|`UShort`|整數|整數|UShort|整數|UShort|整數|UInteger|Long|ULong|  
|`Integer`|整數|整數|整數|整數|整數|整數|Long|Long|Decimal|  
|`UInteger`|Long|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Long|Long|Long|Long|Long|Long|Long|Long|Decimal|  
|`ULong`|Decimal|Decimal|ULong|Decimal|ULong|Decimal|ULong|Decimal|ULong|  
  
### <a name="-operator"></a>\\ 運算子  
 下表顯示 `\` 運算子的結果資料類型。 請注意，這是對稱的資料表;若為指定的運算元資料類型組合，不論運算元的順序為何，結果資料類型都是相同的。  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Short|SByte|Short|Short|整數|整數|Long|Long|Long|  
|`SByte`|SByte|SByte|Short|Short|整數|整數|Long|Long|Long|  
|`Byte`|Short|Short|位元組|Short|UShort|整數|UInteger|Long|ULong|  
|`Short`|Short|Short|Short|Short|整數|整數|Long|Long|Long|  
|`UShort`|整數|整數|UShort|整數|UShort|整數|UInteger|Long|ULong|  
|`Integer`|整數|整數|整數|整數|整數|整數|Long|Long|Long|  
|`UInteger`|Long|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Long|Long|Long|Long|Long|Long|Long|Long|Long|  
|`ULong`|Long|Long|ULong|Long|ULong|Long|ULong|Long|ULong|  
  
 如果 `\` 運算子的任一個運算元為[Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)、 [Single](../../../visual-basic/language-reference/data-types/single-data-type.md)或[Double](../../../visual-basic/language-reference/data-types/double-data-type.md)，Visual Basic 會嘗試在作業之前將它轉換成[Long](../../../visual-basic/language-reference/data-types/long-data-type.md) ，並 `Long`結果資料類型。  
  
## <a name="relational-and-bitwise-comparisons"></a>關聯式和位比較  
 關聯式運算的結果資料類型（`=`、`<>`、`<`、`>`、`<=`、`>=`）一律 `Boolean`[布林資料類型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)。 這也適用于 `OrElse`運算元上的邏輯作業（`And`、`AndAlso`、`Not`、`Or`、`Xor`、`Boolean`）。  
  
 位邏輯運算的結果資料類型取決於運算元的資料類型。 請注意，`AndAlso` 和 `OrElse` 僅針對 `Boolean`所定義，而且 Visual Basic 會在執行作業之前，將每個運算元轉換為 `Boolean`。  
  
### <a name="-----and--operators"></a>=、< >、\<、>、\<= 和 > = 運算子  
 如果兩個運算元都 `Boolean`，Visual Basic 會將 `True` 視為小於 `False`。 如果數數值型別與 `String`比較，Visual Basic 會嘗試將 `String` 轉換為作業前的 `Double`。 `Char` 或 `Date` 運算元只能與相同資料類型的另一個運算元進行比較。 結果資料類型一律為 `Boolean`。  
  
### <a name="bitwise-not-operator"></a>位 Not 運算子  
 下表顯示位 `Not` 運算子的結果資料類型。  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Not`|布林值|SByte|位元組|Short|UShort|整數|UInteger|Long|ULong|  
  
 如果運算元是 `Decimal`、`Single`、`Double`或 `String`，Visual Basic 會嘗試在作業之前將它轉換成 `Long`，並 `Long`結果資料類型。  
  
### <a name="bitwise-and-or-and-xor-operators"></a>位 And、Or 和 Xor 運算子  
 下表顯示位 `And`、`Or`和 `Xor` 運算子的結果資料類型。 請注意，這是對稱的資料表;若為指定的運算元資料類型組合，不論運算元的順序為何，結果資料類型都是相同的。  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|布林值|SByte|Short|Short|整數|整數|Long|Long|Long|  
|`SByte`|SByte|SByte|Short|Short|整數|整數|Long|Long|Long|  
|`Byte`|Short|Short|位元組|Short|UShort|整數|UInteger|Long|ULong|  
|`Short`|Short|Short|Short|Short|整數|整數|Long|Long|Long|  
|`UShort`|整數|整數|UShort|整數|UShort|整數|UInteger|Long|ULong|  
|`Integer`|整數|整數|整數|整數|整數|整數|Long|Long|Long|  
|`UInteger`|Long|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Long|Long|Long|Long|Long|Long|Long|Long|Long|  
|`ULong`|Long|Long|ULong|Long|ULong|Long|ULong|Long|ULong|  
  
 如果運算元是 `Decimal`、`Single`、`Double`或 `String`，Visual Basic 會嘗試在作業之前將它轉換成 `Long`，而結果資料類型則與已經 `Long`該運算元相同。  
  
## <a name="miscellaneous-operators"></a>雜項運算子  
 `&` 運算子只會針對 `String` 運算元的串連而定義。 Visual Basic 會視需要將每個運算元轉換成在作業之前 `String`，而結果資料類型一律會 `String`。 基於 `&` 運算子的目的，所有對 `String` 的轉換都會視為擴展，即使 `Option Strict` `On`。  
  
 `Is` 和 `IsNot` 運算子需要兩個運算元都是參考型別。 `TypeOf`...`Is` 運算式需要第一個運算元是參考型別，而第二個運算元必須是資料類型的名稱。 在所有這些情況下，結果資料類型都是 `Boolean`。  
  
 `Like` 運算子只會針對 `String` 運算元的模式比對進行定義。 Visual Basic 嘗試在作業之前，先將每個運算元轉換為 `String`。 結果資料類型一律為 `Boolean`。  
  
## <a name="see-also"></a>另請參閱

- [資料類型](../../../visual-basic/language-reference/data-types/index.md)
- [運算子和運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Visual Basic 中的算術運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Visual Basic 中的比較運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [運算子](../../../visual-basic/language-reference/operators/index.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [比較運算子](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)
