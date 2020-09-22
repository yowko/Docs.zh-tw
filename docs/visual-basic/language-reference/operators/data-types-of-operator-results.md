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
ms.openlocfilehash: f7a1249cec159f98ede48b960fadc5e2ff4a75f3
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867106"
---
# <a name="data-types-of-operator-results-visual-basic"></a>運算子結果的資料類型 (Visual Basic)

Visual Basic 會根據運算元的資料類型決定作業的結果資料類型。 在某些情況下，這可能是資料類型的範圍大於任一個運算元的範圍。  
  
## <a name="data-type-ranges"></a>資料類型範圍  

 相關資料類型的範圍，從最小到最大的順序如下：  
  
- [布林](../data-types/boolean-data-type.md) 值：兩個可能的值  
  
- [SByte](../data-types/sbyte-data-type.md)、 [Byte](../data-types/byte-data-type.md) -256 可能的整數值  
  
- [Short](../data-types/short-data-type.md)、 [UShort](../data-types/ushort-data-type.md) -65536 (6.5 ... E + 4) 可能的整數值  
  
- [整數](../data-types/integer-data-type.md)， [UInteger](../data-types/uinteger-data-type.md) -4294967296 (4.2 ... E + 9) 可能的整數值  
  
- [Long](../data-types/long-data-type.md)、 [ULong](../data-types/ulong-data-type.md) -18446744073709551615 (1.8 ... E + 19) 可能的整數值  
  
- [Decimal](../data-types/decimal-data-type.md) -1.5 ... e + 29 可能的整數值、最大範圍 7.9 ... E + 28 (絕對值)   
  
- [Single](../data-types/single-data-type.md) -最大範圍 3.4 ... E + 38 (絕對值)   
  
- [Double](../data-types/double-data-type.md) -最大範圍 1.7 ... E + 308 (絕對值)   
  
 如需 Visual Basic 資料類型的詳細資訊，請參閱 [資料類型](../data-types/index.md)。  
  
 如果運算元評估為 [Nothing](../nothing.md)，Visual Basic 算術運算子會將其視為零。  
  
## <a name="decimal-arithmetic"></a>十進位算術  

 請注意， [Decimal](../data-types/decimal-data-type.md) 資料類型不是浮點數或整數。  
  
 如果、、、或運算的任一個運算元 `+` 為， `–` 而另一個運算元不是 `*` `/` `Mod` `Decimal` `Single` 或 `Double` ，Visual Basic 將另一個運算元擴大為 `Decimal` 。 它會執行中的作業 `Decimal` ，而結果資料類型為 `Decimal` 。  
  
## <a name="floating-point-arithmetic"></a>浮點算術  

 Visual Basic 會在 [雙精度](../data-types/double-data-type.md)浮點數中執行大部分的浮點運算，這是這類作業最有效率的資料類型。 但是，如果一個運算元是 [Single](../data-types/single-data-type.md) ，另一個則不是 `Double` ，Visual Basic 會在中執行作業 `Single` 。 它會視需要將每個運算元擴大至作業之前的適當資料類型，而結果具有該資料類型。  
  
### <a name="-and--operators"></a>/和 ^ 運算子  

 `/`運算子只會針對[Decimal](../data-types/decimal-data-type.md)、 [Single](../data-types/single-data-type.md)和[Double](../data-types/double-data-type.md)資料類型來定義。 Visual Basic 視需要將每個運算元擴大至作業之前的適當資料類型，而結果具有該資料類型。  
  
 下表顯示運算子的結果資料類型 `/` 。 請注意，此資料表為對稱式;針對指定的運算元資料類型組合，無論運算元的順序為何，結果資料類型都會相同。  
  
||||||  
|---|---|---|---|---|  
||`Decimal`|`Single`|`Double`|任何整數類型|  
|`Decimal`|Decimal|Single|Double|Decimal|  
|`Single`|Single|Single|Double|Single|  
|`Double`|Double|Double|Double|Double|  
|任何整數類型|Decimal|Single|Double|Double|  
  
 `^`運算子只會針對 `Double` 資料類型來定義。 Visual Basic 在作業之前視需要擴大每個運算元 `Double` ，且結果資料類型一律為 `Double` 。  
  
## <a name="integer-arithmetic"></a>整數算術  

 整數運算的結果資料類型取決於運算元的資料類型。 一般來說，Visual Basic 會使用下列原則來判斷結果資料類型：  
  
- 如果二元運算子的兩個運算元都有相同的資料類型，則結果會有該資料類型。 例外狀況是 `Boolean` 強制的 `Short` 。  
  
- 如果不帶正負號的運算元參與帶正負號的運算元，結果就會有一個帶正負號的類型，其範圍至少與任一個運算元的範圍相同。  
  
- 否則，結果通常會有兩個運算元資料類型中較大的一個。  
  
 請注意，結果資料類型可能與任一個運算元資料類型不相同。  
  
> [!NOTE]
> 結果資料類型的大小不一定足以容納作業所產生的所有可能值。 <xref:System.OverflowException>如果值對結果資料類型而言太大，就會發生例外狀況。  
  
### <a name="unary--and--operators"></a>一元 + 和–運算子  

 下表顯示兩個一元運算子和的結果資料類型 `+` `–` 。  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|元 `+`|Short|SByte|Byte|Short|UShort|整數|UInteger|long|ULong|  
|元 `–`|Short|SByte|Short|Short|整數|整數|long|long|Decimal|  
  
### <a name="-and--operators"></a><\< and >> 運算子  

 下表顯示兩個位移位運算子和的結果資料類型 `<<` `>>` 。 Visual Basic 會將每個位移位運算子視為其左運算元的一元運算子， (要移動) 的位模式。  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`<<`, `>>`|Short|SByte|Byte|Short|UShort|整數|UInteger|long|ULong|  
  
 如果左運算元是 `Decimal` 、、 `Single` `Double` 或 `String` ，Visual Basic 會嘗試在作業之前將它轉換成， `Long` 而結果資料類型為 `Long` 。 右運算元 (要移位的位位置數目) 必須是 `Integer` 或擴大為的類型 `Integer` 。  
  
### <a name="binary----and-mod-operators"></a>Binary +、–、 \* 和 Mod 運算子  

 下表顯示二元 `+` `–` 運算子和 `*` 和運算子的結果資料類型 `Mod` 。 請注意，此資料表為對稱式;針對指定的運算元資料類型組合，無論運算元的順序為何，結果資料類型都會相同。  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Short|SByte|Short|Short|整數|整數|long|long|Decimal|  
|`SByte`|SByte|SByte|Short|Short|整數|整數|long|long|Decimal|  
|`Byte`|Short|Short|Byte|Short|UShort|整數|UInteger|long|ULong|  
|`Short`|Short|Short|Short|Short|整數|整數|long|long|Decimal|  
|`UShort`|整數|整數|UShort|整數|UShort|整數|UInteger|long|ULong|  
|`Integer`|整數|整數|整數|整數|整數|整數|long|long|Decimal|  
|`UInteger`|long|long|UInteger|long|UInteger|long|UInteger|long|ULong|  
|`Long`|long|long|long|long|long|long|long|long|Decimal|  
|`ULong`|Decimal|Decimal|ULong|Decimal|ULong|Decimal|ULong|Decimal|ULong|  
  
### <a name="-operator"></a>\\ 運算子  

 下表顯示運算子的結果資料類型 `\` 。 請注意，此資料表為對稱式;針對指定的運算元資料類型組合，無論運算元的順序為何，結果資料類型都會相同。  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Short|SByte|Short|Short|整數|整數|long|long|long|  
|`SByte`|SByte|SByte|Short|Short|整數|整數|long|long|long|  
|`Byte`|Short|Short|Byte|Short|UShort|整數|UInteger|long|ULong|  
|`Short`|Short|Short|Short|Short|整數|整數|long|long|long|  
|`UShort`|整數|整數|UShort|整數|UShort|整數|UInteger|long|ULong|  
|`Integer`|整數|整數|整數|整數|整數|整數|long|long|long|  
|`UInteger`|long|long|UInteger|long|UInteger|long|UInteger|long|ULong|  
|`Long`|long|long|long|long|long|long|long|long|long|  
|`ULong`|long|long|ULong|long|ULong|long|ULong|long|ULong|  
  
 如果運算子的任一個運算元 `\` 為 [Decimal](../data-types/decimal-data-type.md)、 [Single](../data-types/single-data-type.md)或 [Double](../data-types/double-data-type.md)，Visual Basic 會嘗試在作業之前將它轉換為 [Long](../data-types/long-data-type.md) ，而結果資料類型為 `Long` 。  
  
## <a name="relational-and-bitwise-comparisons"></a>關聯式和位比較  

 關聯式作業的結果資料類型 (`=` 、 `<>` 、 `<` 、 `>` 、 `<=` `>=`) 一律為 `Boolean` [布林資料類型](../data-types/boolean-data-type.md)。 邏輯作業 (、、、、、 `And` `AndAlso` `Not` `Or` `OrElse` `Xor`) 在 `Boolean` 運算元上也是如此。  
  
 位邏輯運算的結果資料類型取決於運算元的資料類型。 請注意， `AndAlso` 和 `OrElse` 只能針對進行定義 `Boolean` ，而 Visual Basic 會在執行作業之前，視需要將每個運算元轉換成 `Boolean` 。  
  
### <a name="-----and--operators"></a>=、 <>、 \<, > 、 \<=, and > = 運算子  

 如果兩個運算元都是 `Boolean` ，Visual Basic `True` 會將視為小於 `False` 。 如果數數值型別與相同 `String` ，Visual Basic 會嘗試在作業之前將轉換 `String` 成 `Double` 。 `Char`或 `Date` 運算元只能與相同資料類型的另一個運算元進行比較。 結果資料類型一律為 `Boolean` 。  
  
### <a name="bitwise-not-operator"></a>位 Not 運算子  

 下表顯示位運算子的結果資料類型 `Not` 。  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Not`|布林值|SByte|Byte|Short|UShort|整數|UInteger|long|ULong|  
  
 如果運算元為 `Decimal` 、、 `Single` `Double` 或 `String` ，Visual Basic 會嘗試在作業之前將它轉換成， `Long` 而結果資料類型為 `Long` 。  
  
### <a name="bitwise-and-or-and-xor-operators"></a>位 And、Or 和 Xor 運算子  

 下表顯示位 `And` 、和運算子的結果資料類型 `Or` `Xor` 。 請注意，此資料表為對稱式;針對指定的運算元資料類型組合，無論運算元的順序為何，結果資料類型都會相同。  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|布林值|SByte|Short|Short|整數|整數|long|long|long|  
|`SByte`|SByte|SByte|Short|Short|整數|整數|long|long|long|  
|`Byte`|Short|Short|Byte|Short|UShort|整數|UInteger|long|ULong|  
|`Short`|Short|Short|Short|Short|整數|整數|long|long|long|  
|`UShort`|整數|整數|UShort|整數|UShort|整數|UInteger|long|ULong|  
|`Integer`|整數|整數|整數|整數|整數|整數|long|long|long|  
|`UInteger`|long|long|UInteger|long|UInteger|long|UInteger|long|ULong|  
|`Long`|long|long|long|long|long|long|long|long|long|  
|`ULong`|long|long|ULong|long|ULong|long|ULong|long|ULong|  
  
 如果運算元為 `Decimal` 、、 `Single` `Double` 或 `String` ，Visual Basic 會嘗試在作業之前將它轉換成， `Long` 而且結果資料類型會與運算元已經相同 `Long` 。  
  
## <a name="miscellaneous-operators"></a>雜項運算子  

 `&`運算子只會針對運算元的串連而定義 `String` 。 Visual Basic 會在作業之前視需要將每個運算元轉換成 `String` ，而且結果資料類型一律為 `String` 。 基於運算子的目的 `&` ，所有的轉換都會被 `String` 視為擴展，即使 `Option Strict` 是 `On` 。  
  
 `Is`和 `IsNot` 運算子要求兩個運算元都是參考型別。 `TypeOf`... `Is` 運算式要求第一個運算元必須是參考型別，而第二個運算元必須是資料類型的名稱。 在上述所有情況下，結果資料類型為 `Boolean` 。  
  
 `Like`運算子只會定義于運算元的模式比對 `String` 。 Visual Basic 會在作業之前，視需要將每個運算元轉換 `String` 。 結果資料類型一律為 `Boolean` 。  
  
## <a name="see-also"></a>另請參閱

- [Data types (資料類型)](../data-types/index.md)
- [運算子和運算式](../../programming-guide/language-features/operators-and-expressions/index.md)
- [Visual Basic 的算術運算子](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Comparison Operators in Visual Basic](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [運算子](index.md)
- [Visual Basic 中的運算子優先順序](operator-precedence.md)
- [依功能列出運算子](operators-listed-by-functionality.md)
- [算術運算子](arithmetic-operators.md)
- [比較運算子](comparison-operators.md)
- [Long](../statements/option-strict-statement.md)
