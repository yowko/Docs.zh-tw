---
title: 運算子多載
description: 了解如何多載算術的運算子，在類別或記錄類型，然後在全域層級F#。
ms.date: 05/16/2016
ms.openlocfilehash: c4b52b02522b750aa55ca6cf4097295e35ab1739
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610758"
---
# <a name="operator-overloading"></a>運算子多載

本主題描述如何多載算術的運算子，在類別或記錄類型，並在全域層級。

## <a name="syntax"></a>語法

```fsharp
// Overloading an operator as a class or record member.
static member (operator-symbols) (parameter-list) =
    method-body
// Overloading an operator at the global level
let [inline] (operator-symbols) parameter-list = function-body
```

## <a name="remarks"></a>備註

在先前的語法*運算子符號*是其中一個`+`， `-`， `*`， `/`， `=`，依此類推。 *參數清單*它們出現的一般語法中該運算子的順序指定的運算元。 *方法主體*建構所產生的值。

運算子多載運算子都必須是靜態的。 運算子多載的一元運算子，例如`+`並`-`，必須使用波狀符號 (`~`) 中*運算子符號*表示的運算子是一元運算子和二元的運算子，如中所示下列宣告。

```fsharp
static member (~-) (v : Vector)
```

下列程式碼說明只有兩個運算子的向量類別，一個運算子用於一元減號運算，一個運算子用於純量乘法。 在範例中，因為不論向量和純量出現的順序必須一起使用的運算子需要兩個多載用於純量乘法。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4001.fs)]

## <a name="creating-new-operators"></a>建立新的運算子

您可以多載所有標準的運算子，但您也可以建立新的運算子，從特定的字元序列。 允許為運算子字元`!`， `%`， `&`， `*`， `+`， `-`， `.`， `/`， `<`， `=`， `>`， `?`， `@`， `^`， `|`，和`~`。 `~`字元具有特殊意義，讓操作員一元 （unary），且不是運算子字元序列的一部分。 並非所有運算子都可以都進行一元 （unary）。

根據您所使用的確切的字元順序，請您運算子會有特定優先順序和關聯性。 關聯性可以可能是從左至右或由右至左，而用時的相同層級的優先順序的運算子會出現在不含括弧的順序。

運算子字元`.`並不會影響優先順序，因此，比方說，如果您想要定義您自己的版本具有相同的優先順序和順序關聯性與一般的乘法的乘法的您可以建立運算子，例如`.*`.

只有運算子`?`並`?<-`可能會開始`?`。

資料表顯示中的所有運算子的優先順序F#篇[符號和運算子參考](symbol-and-operator-reference/index.md)。

## <a name="overloaded-operator-names"></a>多載的運算子名稱

當F#編譯器編譯的運算子的運算式，它會產生具有編譯器產生的名稱，該運算子的方法。 這是出現在方法中的 Microsoft intermediate language (MSIL)，也在反映和 IntelliSense 的名稱。 您通常不需要使用這些名稱在F#程式碼。

下表顯示標準的運算子和其對應產生的名稱。

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

其他這裡未列出的運算子字元的組合可以用作運算子，並藉由串連下表中的個別字元的名稱所組成的名稱。 例如，+ ！ 會變成`op_PlusBang`。

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

## <a name="prefix-and-infix-operators"></a>前置詞和中置運算子

*前置詞*運算子應該位於運算元或運算元，如同函式。 *中置*運算子有兩個運算元之間放置。

只有特定運算子可用來當做前置運算子。 有些運算子永遠前置運算子，其他人可以是中置或前置詞，而且其餘部分會一律中置運算子。 開頭為 `!` 的運算子 (不包括 `!=`) 以及 `~` 運算子或 `~` 的重複序列一律為前置運算子。 運算子`+`， `-`， `+.`， `-.`， `&`， `&&`， `%`，以及`%%`可以是前置運算子或中置運算子。 您從 中置版本區分這些運算子的前置版本加上`~`前置運算子所定義的開頭。 `~`時您使用運算子，它會定義時，才不會使用。

## <a name="example"></a>範例

下列程式碼說明如何使用運算子多載實作分數型別。 表示分數的分子和分母。 此函式`hcf`用來判斷最高常見因素，用來減少片段。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4002.fs)]

**輸出：**

```
3/4 + 1/2 = 5/4
3/4 - 1/2 = 1/4
3/4 * 1/2 = 3/8
3/4 / 1/2 = 3/2
3/4 + 1 = 7/4
```

## <a name="operators-at-the-global-level"></a>在全域層級的運算子

您也可以定義在全域層級的運算子。 下列程式碼定義了運算子`+?`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4003.fs)]

上述程式碼的輸出是`12`。

因為範圍規則，您可以重新定義以這種方式的一般算術運算子F#指定的新定義的運算子的優先順序高於內建的運算子。

關鍵字`inline`通常會搭配全域運算子，而這通常是最適合整合至呼叫端程式碼的小型函式。 讓運算子函式內嵌也可讓它們使用來產生以統計方式解析的一般程式碼以統計方式解析的型別參數。 如需詳細資訊，請參閱 <<c0> [ 內嵌函式](functions/inline-functions.md)並[以靜態方式解析的類型參數](generics/statically-resolved-type-parameters.md)。

## <a name="see-also"></a>另請參閱

- [成員](members/index.md)