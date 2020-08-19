---
title: 運算子多載
description: '瞭解如何在類別或記錄類型，以及在 F # 的全域層級上多載算術運算子。'
ms.date: 08/15/2020
ms.openlocfilehash: fb86ceb95101fcc1f157ec9ba17a9d8145b11a91
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557577"
---
# <a name="operator-overloading"></a>運算子多載

本主題描述如何在類別或記錄類型，以及在全域層級上多載算術運算子。

## <a name="syntax"></a>語法

```fsharp
// Overloading an operator as a class or record member.
static member (operator-symbols) (parameter-list) =
    method-body
// Overloading an operator at the global level
let [inline] (operator-symbols) parameter-list = function-body
```

## <a name="remarks"></a>備註

在先前的語法中， *運算子-符號* 是、、、、等等之一 `+` `-` `*` `/` `=` 。 *參數清單*會以該運算子的一般語法來指定運算元。 *方法主體*會構造產生的值。

運算子的運算子多載必須是靜態的。 一元運算子的運算子多載（例如 `+` 和 `-` ）必須 `~` 在 *運算子-符號* 中使用波狀符號 () ，以指出運算子是一元運算子而非二元運算子，如下列宣告所示。

```fsharp
static member (~-) (v : Vector)
```

下列程式碼說明只有兩個運算子的向量類別，一個運算子用於一元減號運算，一個運算子用於純量乘法。 在此範例中，需要兩個純量運算的多載，因為不論向量和純量的出現順序為何，運算子都必須運作。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4001.fs)]

## <a name="creating-new-operators"></a>建立新的運算子

您可以多載所有標準運算子，但您也可以在特定字元的序列中建立新的運算子。 允許的運算子字元為 `!` 、、、、、、、、、、、、、、 `%` `&` `*` `+` `-` `.` `/` `<` `=` `>` `?` `@` `^` `|` 和 `~` 。 `~`字元具有建立運算子一元的特殊意義，而不是運算子字元序列的一部分。 並非所有運算子都可以成為一元。

根據您所使用的確切字元順序，操作員將擁有特定的優先順序和關聯性。 關聯性可以是由左至右或由右至左，而每當相同層級的運算子以順序出現時，就會使用括弧。

運算子字元不 `.` 會影響優先順序，例如，如果您想要定義您自己的乘法與一般乘法具有相同優先順序和關聯性的版本，您可以建立像這樣的運算子 `.*` 。

只有運算子 `?` 和 `?<-` 可以從開始 `?` 。

在 [符號和運算子參考](./symbol-and-operator-reference/index.md)中，可以找到顯示 F # 中所有運算子之優先順序的資料表。

## <a name="overloaded-operator-names"></a>多載的運算子名稱

當 F # 編譯器編譯運算子運算式時，它會產生具有編譯器為該運算子產生之名稱的方法。 這是出現在 Microsoft 中繼語言 (MSIL) 的方法，也是反映和 IntelliSense 中的名稱。 您通常不需要在 F # 程式碼中使用這些名稱。

下表顯示標準運算子及其對應產生的名稱。

|運算子|產生的名稱|
|--------|--------------|
|`[]`|`op_Nil`|
|`::`|`op_Cons`|
|`+`|`op_Addition`|
|`-`|`op_Subtraction`|
|`*`|`op_Multiply`|
|`/`|`op_Division`|
|`@`|`op_Append`|
|`^`|`op_Concatenate`|
|`%`|`op_Modulus`|
|`&&&`|`op_BitwiseAnd`|
|<code>&#124;&#124;&#124;</code>|`op_BitwiseOr`|
|`^^^`|`op_ExclusiveOr`|
|`<<<`|`op_LeftShift`|
|`~~~`|`op_LogicalNot`|
|`>>>`|`op_RightShift`|
|`~+`|`op_UnaryPlus`|
|`~-`|`op_UnaryNegation`|
|`=`|`op_Equality`|
|`<=`|`op_LessThanOrEqual`|
|`>=`|`op_GreaterThanOrEqual`|
|`<`|`op_LessThan`|
|`>`|`op_GreaterThan`|
|`?`|`op_Dynamic`|
|`?<-`|`op_DynamicAssignment`|
|<code>&#124;></code>|`op_PipeRight`|
|<code><&#124;</code>|`op_PipeLeft`|
|`!`|`op_Dereference`|
|`>>`|`op_ComposeRight`|
|`<<`|`op_ComposeLeft`|
|`<@ @>`|`op_Quotation`|
|`<@@ @@>`|`op_QuotationUntyped`|
|`+=`|`op_AdditionAssignment`|
|`-=`|`op_SubtractionAssignment`|
|`*=`|`op_MultiplyAssignment`|
|`/=`|`op_DivisionAssignment`|
|`..`|`op_Range`|
|`.. ..`|`op_RangeStep`|

請注意， `not` F # 中的運算子不會發出， `op_Inequality` 因為它不是符號運算子。 它是發出 IL 以否定布林運算式的函數。

此處未列出的其他運算子字元組合可以用來做為運算子，而且具有藉由串連下表中個別字元名稱所組成的名稱。 例如，+！ 成為 `op_PlusBang` 。

|運算子字元|名稱|
|------------------|----|
|`>`|`Greater`|
|`<`|`Less`|
|`+`|`Plus`|
|`-`|`Minus`|
|`*`|`Multiply`|
|`/`|`Divide`|
|`=`|`Equals`|
|`~`|`Twiddle`|
|`%`|`Percent`|
|`.`|`Dot`|
|`&`|`Amp`|
|<code>&#124;</code>|`Bar`|
|`@`|`At`|
|`^`|`Hat`|
|`!`|`Bang`|
|`?`|`Qmark`|
|`(`|`LParen`|
|`,`|`Comma`|
|`)`|`RParen`|
|`[`|`LBrack`|
|`]`|`RBrack`|

## <a name="prefix-and-infix-operators"></a>前置和中置運算子

*前置* 運算子必須放在運算元或運算元前面，與函式非常類似。 中*置運算子應*放在兩個運算元之間。

只有特定運算子可以當做前置運算子使用。 某些運算子一律為前置運算子，其他運算子可以是中置或前置詞，而其餘的一律是中置運算子。 開頭為 `!` 的運算子 (不包括 `!=`) 以及 `~` 運算子或 `~` 的重複序列一律為前置運算子。 運算子 `+` 、 `-` 、、、、、 `+.` `-.` `&` `&&` `%` 和 `%%` 可以是前置運算子或中置運算子。 您可以藉由在前置運算子的開頭新增，來區別這些運算子的前置詞版本與中置版本 `~` 。 `~`只有在定義時，才會使用運算子。

## <a name="example"></a>範例

下列程式碼說明如何使用運算子多載來執行分數類型。 分數是以分子和分母表示。 函數 `hcf` 是用來決定最高的常見因數，這會用來減少分數。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4002.fs)]

**輸出：**

```console
3/4 + 1/2 = 5/4
3/4 - 1/2 = 1/4
3/4 * 1/2 = 3/8
3/4 / 1/2 = 3/2
3/4 + 1 = 7/4
```

## <a name="operators-at-the-global-level"></a>全域層級的運算子

您也可以在全域層級定義運算子。 下列程式碼會定義操作員 `+?` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4003.fs)]

上述程式碼的輸出為 `12` 。

您可以用這種方式重新定義一般算術運算子，因為 F # 的範圍規則會規定新定義的運算子優先于內建運算子。

關鍵字 `inline` 通常會與全域運算子搭配使用，這通常是最適合整合至呼叫程式碼的小型函式。 使運算子函式內嵌也可讓它們使用靜態解析的型別參數，以產生靜態解析的一般程式碼。 如需詳細資訊，請參閱 [內嵌](./functions/inline-functions.md) 函式和 [靜態解析的型別參數](./generics/statically-resolved-type-parameters.md)。

## <a name="see-also"></a>另請參閱

- [成員](./members/index.md)
