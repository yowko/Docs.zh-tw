---
title: 運算子多載
description: 瞭解如何在類別或記錄類型和中F#的全域層級上多載算術運算子。
ms.date: 05/16/2016
ms.openlocfilehash: c656c1c47938e62386c8f063cf9a6caaaf69d0fe
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627397"
---
# <a name="operator-overloading"></a>運算子多載

本主題描述如何在類別或記錄類型, 以及在全域層級上多載算術運算子。

## <a name="syntax"></a>語法

```fsharp
// Overloading an operator as a class or record member.
static member (operator-symbols) (parameter-list) =
    method-body
// Overloading an operator at the global level
let [inline] (operator-symbols) parameter-list = function-body
```

## <a name="remarks"></a>備註

在先前的語法中,*運算子-符號*是`+` `=`、 `-`、 `*` `/`、、等其中一個。 *參數清單*會以它們在該運算子的一般語法中出現的順序來指定運算元。 *方法主體*會結構產生的值。

運算子的運算子多載必須是靜態的。 一元運算子的運算子多載 (例如`+`和`-`) 必須在*運算子符號*中`~`使用波狀符號 (), 以表示運算子是一元運算子, 而不是二元運算子, 如下所示清點.

```fsharp
static member (~-) (v : Vector)
```

下列程式碼說明只有兩個運算子的向量類別，一個運算子用於一元減號運算，一個運算子用於純量乘法。 在此範例中, 需要兩個純量的多載, 因為不論向量和純量的出現順序為何, 運算子都必須可行。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4001.fs)]

## <a name="creating-new-operators"></a>建立新的運算子

您可以多載所有標準運算子, 但您也可以從特定字元序列中建立新的運算子。 允許的運算子字元`!`為`%`、 `&` `*` `+` 、`-`、、、 、、`.`、、、、 `/` `<` `=` `>` `?` 、`@`、 、`^`和`~`。 `|` `~`字元具有建立運算子一元的特殊意義, 而不是運算子字元序列的一部分。 並非所有運算子都可以成為一元。

視您使用的確切字元順序而定, 您的運算子會有特定的優先順序和關聯性。 關聯性可以由左至右或由右至左, 並且會在每次相同優先順序的運算子以不含括弧的順序顯示時使用。

運算子字元`.`不會影響優先順序, 因此, 舉例來說, 如果您想要定義自己的乘法版本, 且其優先順序和關聯性與一般乘法相同, 您可以建立運算子, 例如`.*`.

只有運算子`?`和`?<-`可以從開始`?`。

在F# [符號和運算子參考](./symbol-and-operator-reference/index.md)中, 可以找到顯示所有運算子優先順序的資料表。

## <a name="overloaded-operator-names"></a>多載的運算子名稱

F#當編譯器編譯運算子運算式時, 它會產生具有編譯器為該運算子所產生之名稱的方法。 這是在方法的 Microsoft 中繼語言 (MSIL) 中顯示的名稱, 也是在反映和 IntelliSense 中。 您通常不需要在程式碼中F#使用這些名稱。

下表顯示標準運算子及其對應的產生名稱。

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

此處未列出的其他運算子字元組合可以做為運算子使用, 並透過串連下表中個別字元的名稱來建立名稱。 例如, +! 會`op_PlusBang`變成。

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

## <a name="prefix-and-infix-operators"></a>前置詞和中綴運算子

*前置*運算子應該放在運算元或運算元的前方, 非常類似于函式。 中*綴*運算子應該放在兩個運算元之間。

只有特定運算子可以當做前置詞運算子使用。 有些運算子一律是前置詞運算子, 有些則可以是中置或前置詞, 而其餘的則一律是中綴運算子。 開頭為 `!` 的運算子 (不包括 `!=`) 以及 `~` 運算子或 `~` 的重複序列一律為前置運算子。 `+`運算子、`&`、、 、`%`、、和`%%`可以是前置運算子或中綴運算子。 `&&` `-` `+.` `-.` 您可以將這些運算子的前置詞版本與`~`上綴版本區別, 方法是在定義前置詞運算子的開頭新增。 當您使用運算子時, 只有在定義時才會使用。`~`

## <a name="example"></a>範例

下列程式碼說明如何使用運算子多載來執行分數類型。 分數是以分子和分母表示。 函數`hcf`是用來判斷最常見的因素, 這是用來減少分數。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4002.fs)]

**輸出：**

```
3/4 + 1/2 = 5/4
3/4 - 1/2 = 1/4
3/4 * 1/2 = 3/8
3/4 / 1/2 = 3/2
3/4 + 1 = 7/4
```

## <a name="operators-at-the-global-level"></a>全域層級的運算子

您也可以在全域層級定義運算子。 下列程式碼會定義運算子`+?`。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4003.fs)]

上述程式碼的輸出為`12`。

您可以用這種方式重新定義一般算術運算子, 因為的範圍F#規則會規定新定義的運算子優先于內建的運算子。

關鍵字`inline`通常與全域運算子搭配使用, 這通常是很小的函式, 最適合與呼叫程式碼整合。 讓運算子函式內嵌也可以讓它們使用靜態解析的類型參數, 以產生靜態解析的泛型程式碼。 如需詳細資訊, 請參閱[內嵌](./functions/inline-functions.md)函式和以[靜態方式解析的類型參數](./generics/statically-resolved-type-parameters.md)。

## <a name="see-also"></a>另請參閱

- [成員](./members/index.md)
