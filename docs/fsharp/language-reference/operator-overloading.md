---
title: "運算子多載 (F#)"
description: "了解如何在類別或記錄類型，F # 中的全域層級的算術運算子多載。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 019277ed-f649-4fa5-ad43-097865f449d9
ms.openlocfilehash: 76ddab5339e11d71bb326b60d727017eb838ccf4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="operator-overloading"></a>運算子多載

本主題描述如何在類別或記錄類型，也可以在全域層級的算術運算子多載。


## <a name="syntax"></a>語法

```fsharp
// Overloading an operator as a class or record member.
static member (operator-symbols) (parameter-list) =
    method-body
// Overloading an operator at the global level
let [inline] (operator-symbols) parameter-list = function-body
```

## <a name="remarks"></a>備註
在先前的語法，*運算子符號*是其中一個`+`， `-`， `*`， `/`， `=`，依此類推。 *參數清單*它們出現在一般的語法，該運算子的順序指定的運算元。 *方法主體*建構產生的值。

運算子多載運算子都必須是靜態的。 運算子多載一元運算子，例如`+`和`-`，必須使用波狀符號 (`~`) 中*運算子符號*來表示運算子是一元運算子和二元的運算子，如中所示下列宣告。

```fsharp
static member (~-) (v : Vector)
```

下列程式碼說明只有兩個運算子的向量類別，一個運算子用於一元減號運算，一個運算子用於純量乘法。 在範例中，因為運算子必須使用向量和純量出現的順序為何，所需的純量乘法的兩個多載。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4001.fs)]

## <a name="creating-new-operators"></a>建立新的運算子
您可以多載所有標準的運算子，但您也可以建立新的運算子，超出特定的字元序列。 允許的運算子字元為`!`， `%`， `&`， `*`， `+`， `-`， `.`， `/`， `<`， `=`， `>`， `?`， `@`， `^`， `|`，和`~`。 `~`字元具有特殊意義的一元運算子，並不是運算子字元序列的一部分。 並非所有運算子都無法都進行一元 （unary）。

根據您使用的確切的字元序列，您的運算子會有特定優先順序和關聯性。 關聯性可以在從左至右或由右至左可能保留，且不含括弧的順序出現相同層級的優先順序的運算子時，都會使用。

運算子字元`.`以便比方說，如果您想要定義您自己有相同的優先順序和順序關聯性與一般乘法的乘法的版本，您可以建立運算子，例如，不會影響優先順序，`.*`.

只有運算子`?`和`?<-`可能開頭`?`。

可以在中找到的資料表是顯示 F # 中的所有運算子的優先順序[符號和運算子參考](symbol-and-operator-reference/index.md)。


## <a name="overloaded-operator-names"></a>多載的運算子名稱
當 F # 編譯器編譯的運算子的運算式時，它會產生具有編譯器產生的名稱，該運算子的方法。 這是出現在方法的 Microsoft intermediate language (MSIL)，也在反映和 IntelliSense 的名稱。 您通常不需要在 F # 程式碼中使用這些名稱。

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
其他未在此處列出的運算子字元的組合可用來當作運算子，且有下表中的個別字元的名稱串連起來所組成的名稱。 例如，+ ！ 會變成`op_PlusBang`。



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
*前置詞*運算子應該放置在運算元或運算元，非常類似函式前面。 *中置*運算子應該有兩個運算元之間。

只有特定運算子可用來當做前置運算子。 有些運算子永遠前置運算子，其他人可以是中置或前置詞，而且其餘部分永遠是中置運算子。 開頭為 `!` 的運算子 (不包括 `!=`) 以及 `~` 運算子或 `~` 的重複序列一律為前置運算子。 運算子`+`， `-`， `+.`， `-.`， `&`， `&&`， `%`，和`%%`可以是前置運算子或中置運算子。 中置版本區分這些運算子的前置詞新版加`~`前置運算子定義時的開頭。 `~`時只有在定義時，會使用運算子，不會使用。

## <a name="example"></a>範例

下列程式碼說明如何使用運算子多載實作分數型別。 分數的分子，分母所表示。 此函式`hcf`用來判斷最高公因數，用來減少分數。

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
您也可以定義的全域層級的運算子。 下列程式碼定義的運算子`+?`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4003.fs)]

上述程式碼的輸出是`12`。

因為的範圍規則的 F # 聽寫的新定義的運算子的優先順序高於內建運算子，您可以重新定義以這種方式的一般算術運算子。

關鍵字`inline`常搭配全域運算子，而這通常是最佳整合呼叫程式碼的小型函式。 內嵌函式進行運算子也可讓它們使用來產生以統計方式解析的一般程式碼以統計方式解析的型別參數。 如需詳細資訊，請參閱[內嵌函式](functions/inline-functions.md)和[以靜態方式解析的型別參數](generics/statically-resolved-type-parameters.md)。

## <a name="see-also"></a>另請參閱
[成員](members/index.md)
