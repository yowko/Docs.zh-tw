---
title: 符號和運算子參考
description: 深入了解符號和運算子，可在F#程式設計語言。
ms.date: 02/11/2019
ms.openlocfilehash: 11a02792dc949b0a7a0a6e7bb59786c489b3aa9d
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56092939"
---
# <a name="symbol-and-operator-reference"></a>符號和運算子參考

> [!NOTE]
> 本文中的 API 參考連結將帶您前往 MSDN。  docs.microsoft.com API 參考不完整。

本主題包含 F# 語言中使用的符號與運算子資料表。

## <a name="table-of-symbols-and-operators"></a>符號與運算子資料表

下表說明 F# 語言中使用的符號，提供可提供詳細資訊之主題的連結，並提供一些符號用法的簡短說明。 符號會依據 ASCII 字元集的順序加以排序。

|符號或運算子|連結|描述|
|------------------|-----|-----------|
|`!`|[參考儲存格](../reference-cells.md)<br /><br />[計算運算式](../computation-expressions.md)|<ul><li>取值參考儲存格。<br /></li><li>在關鍵字後面，代表由工作流程所控制的關鍵字行為之修改版本。<br /></li></ul>|
|`!=`|不適用。|<ul><li>F# 中不使用。 使用 `<>` 進行不等比較運算。<br /></li></ul>|
|`"`|[常值](../literals.md)<br /><br />[字串](../strings.md)|<ul><li>分隔文字字串。<br /></li></ul>|
|`"""`|[字串](../strings.md)|分隔逐字文字字串。 有別於 `@"..."`，因為您可以在字串中使用單引號來表示引號字元。|
|`#`|[編譯器指示詞](../compiler-directives.md)<br /><br />[彈性類型](../flexible-types.md)|<ul><li>開頭前置處理器或編譯器指示詞，例如，`#light`。<br /></li><li>與類型一起使用時，表示「彈性類型」，這指的是類型或任何一種其衍生的類型。<br /></li></ul>|
|`$`|沒有可用的詳細資訊。|<ul><li>使用於內部，用於特定編譯器產生的變數與函式名稱。<br /></li></ul>|
|`%`|[算術運算子](arithmetic-operators.md)<br /><br />[程式碼引號](../code-quotations.md)|<ul><li>計算整數餘數。<br /></li><li>用於將運算式接合成具類型的程式碼引號。<br /></li></ul>|
|`%%`|[程式碼引號](../code-quotations.md)|<ul><li>用於將運算式接合成不具類型的程式碼引號。<br /></li></ul>|
|`%?`|[可為 Null 的運算子](nullable-operators.md)|<ul><li>當右側是可為 null 的型別時，會計算整數餘數。<br /></li></ul>|
|`&`|[比對運算式](../match-expressions.md)|<ul><li>計算可變動值的位址，以在與其他語言相互操作時使用。<br /></li><li>用於 AND 模式中。<br /></li></ul>|
|`&&`|[布林運算子](boolean-operators.md)|<ul><li>計算布林值 AND 運算。<br /></li></ul>|
|`&&&`|[位元運算子](bitwise-operators.md)|<ul><li>計算位元 AND 運算。<br /></li></ul>|
|`'`|[常值](../literals.md)<br /><br />[自動一般化](../generics/automatic-generalization.md)|<ul><li>分隔單一字元常值。<br /></li><li>表示泛型類型參數。<br /></li></ul>|
|<code>&#96;&#96;...&#96;&#96;</code>|沒有可用的詳細資訊。|<ul><li>分隔若在其他狀況下不會是合法識別項的識別項，例如語言關鍵字。<br /></li></ul>|
|`( )`|[單位類型](../unit-type.md)|<ul><li>代表單位類型的單一值。<br /></li></ul>|
|`(...)`|[元組](../tuples.md)<br /><br />[運算子多載](../operator-overloading.md)|<ul><li>表示運算式的評估順序。<br /></li><li>分隔 Tuple。<br /></li><li>用於運算子定義中。<br /></li></ul>|
|`(*...*)`||<ul><li>分隔無法跨越多行的註解。<br /></li></ul>|
|<code>(&#124;...&#124;)</code>|[使用中模式](../active-patterns.md)|<ul><li>分隔使用中的模式。 也稱為「香蕉夾」。<br /></li></ul>|
|`*`|[算術運算子](arithmetic-operators.md)<br /><br />[元組](../tuples.md)<br /><br />[測量單位](../units-of-measure.md)|<ul><li>當做二元運算子使用時，將左側與右側相乘。<br /></li><li>在類型中，表示在 Tuple 中配對。<br /></li><li>用於測量單位類型中。<br /></li></ul>|
|`*?`|[可為 Null 的運算子](nullable-operators.md)|<ul><li>當右側是可為 null 類型時，將左側與右側相乘。<br /></li></ul>|
|`**`|[算術運算子](arithmetic-operators.md)|<ul><li>計算乘冪運算 (`x ** y` 表示 `x` 的 `y` 次方)。<br /></li></ul>|
|`+`|[算術運算子](arithmetic-operators.md)|<ul><li>當做二元運算子使用時，將左側與右側相加。<br /></li><li>當做一元運算子使用時，表示正數量。 (正式地說，它會產生正負號維持不變的相同值。)<br /></li></ul>|
|`+?`|[可為 Null 的運算子](nullable-operators.md)|<ul><li>當右側是可為 null 的類型時，將左側與右側相加。<br /></li></ul>|
|`,`|[元組](../tuples.md)|<ul><li>分隔 Tuple 的項目或型別參數。<br /></li></ul>|
|`-`|[算術運算子](arithmetic-operators.md)|<ul><li>當做二元運算子使用時，從左側減去右側。<br /></li><li>當做一元運算子使用時，執行負運算。<br /></li></ul>|
|`-`|[可為 Null 的運算子](nullable-operators.md)|<ul><li>當右側是可為 null 的類型時，從左側減去右側。<br /></li></ul>|
|`->`|[函式](../functions/index.md)<br /><br />[比對運算式](../match-expressions.md)|<ul><li>在函式類型中，分隔引數並傳回值。<br /></li><li>產生運算式 (在循序項運算式中)；相當於 `yield` 關鍵字。<br /></li><li>用於比對運算式中<br /></li></ul>|
|`.`|[成員](../members/index.md)<br /><br />[基本類型](../primitive-types.md)|<ul><li>存取成員，並分隔完整名稱中的個別名稱。<br /></li><li>以浮點數指定小數點。<br /></li></ul>|
|`..`|[迴圈：`for...in` 運算式](../loops-for-in-expression.md)|<ul><li>指定範圍。<br /></li></ul>|
|`.. ..`|[迴圈：`for...in` 運算式](../loops-for-in-expression.md)|<ul><li>指定範圍與遞增值。<br /></li></ul>|
|`.[...]`|[陣列](../arrays.md)|<ul><li>存取陣列元素。<br /></li></ul>|
|`/`|[算術運算子](arithmetic-operators.md)<br /><br />[測量單位](../units-of-measure.md)|<ul><li>左側 (分子) 除以右側 (分母)。<br /></li><li>用於測量單位類型中。<br /></li></ul>|
|`/?`|[可為 Null 的運算子](nullable-operators.md)|<ul><li>當右側是可為 null 的類型時，左側除以右側。<br /></li></ul>|
|`//`||<ul><li>表示單行註解的開頭。<br /></li></ul>|
|`///`|[XML 文件](../xml-documentation.md)|<ul><li>表示 XML 註解。<br /></li></ul>|
|`:`|[函式](../functions/index.md)|<ul><li>在類型註釋中，將參數或成員名稱與其類型分隔。<br /></li></ul>|
|`::`|[清單](../lists.md)<br /><br />[比對運算式](../match-expressions.md)|<ul><li>建立清單。 左側的項目會附加到右側清單的前面。<br /></li><li>用於模式比對中以分隔清單的組件。<br /></li></ul>|
|`:=`|[參考儲存格](../reference-cells.md)|<ul><li>將值指派給參考儲存格。<br /></li></ul>|
|`:>`|[轉型和轉換](../casting-and-conversions.md)|<ul><li>將類型轉換成階層中較高階的類型。<br /></li></ul>|
|`:?`|[比對運算式](../match-expressions.md)|<ul><li>會傳回`true`如果值符合指定的型別 （包括如果它是一個子類型）; 否則會傳回`false`（類型測試運算子）。<br /></li></ul>|
|`:?>`|[轉型和轉換](../casting-and-conversions.md)|<ul><li>將類型轉換成階層中較低階的類型。<br /></li></ul>|
|`;`|[詳細語法](../verbose-syntax.md)<br /><br />[清單](../lists.md)<br /><br />[記錄](../records.md)|<ul><li>分隔運算式 (大部分用於詳細語法中)。<br /></li><li>分隔清單的元素。<br /></li><li>分隔記錄的欄位。<br /></li></ul>|
|`<`|[算術運算子](arithmetic-operators.md)|<ul><li>計算小於運算。<br /></li></ul>|
|`<?`|[可為 Null 的運算子](nullable-operators.md)|當右側是可為 null 的類型時，計算小於運算。|
|`<<`|[函式](../functions/index.md)|<ul><li>以相反順序撰寫兩個函式；第二個函式會先執行 (反向撰寫運算子)。<br /></li></ul>|
|`<<<`|[位元運算子](bitwise-operators.md)|<ul><li>將左側中數量中的位元，向左移位右側所指定的位元數。<br /></li></ul>|
|`<-`|[值](../values/index.md)|<ul><li>將值指派給變數。<br /></li></ul>|
|`<...>`|[自動一般化](../generics/automatic-generalization.md)|<ul><li>分隔型別參數。<br /></li></ul>|
|`<>`|[算術運算子](arithmetic-operators.md)|<ul><li>如果左側不等於右側，即傳回 `true`；否則，傳回 false。<br /></li></ul>|
|`<>?`|[可為 Null 的運算子](nullable-operators.md)|<ul><li>當右側是可為 null 的類型時，計算「不等於」運算。<br /></li></ul>|
|`<=`|[算術運算子](arithmetic-operators.md)|<ul><li>如果左側小於或等於右側，即傳回 `true`；否則傳回 `false`。<br /></li></ul>|
|`<=?`|[可為 Null 的運算子](nullable-operators.md)|<ul><li>當右側是可為 null 的類型時，計算「小於或等於」運算。<br /></li></ul>|
|<code>&lt;&#124;</code>|[函式](../functions/index.md)|<ul><li>將右側的運算結果傳遞至左側的函式 (反向管道運算子)。<br /></li></ul>|
|<code>&lt;&#124;&#124;</code>|[Operators.&#40; &#60;&#124;&#124; &#41;&#60;'T1,'T2,'U&#62; 函式](https://msdn.microsoft.com/visualfsharpdocs/conceptual/operators.%5b-%5bhh-%5d%5b%27t1%2c%27t2%2c%27u%5d-function-%5bfsharp%5d)|<ul><li>將右側兩個引數的 Tuple 傳遞至左側的函式。<br /></li></ul>|
|<code>&lt;&#124;&#124;&#124;</code>|[Operators.&#40; &#60;&#124;&#124;&#124; &#41;&#60;'T1,'T2,'T3,'U&#62; 函式](https://msdn.microsoft.com/visualfsharpdocs/conceptual/operators.%5b-%5bhhh-%5d%5b%27t1%2c%27t2%2c%27t3%2c%27u%5d-function-%5bfsharp%5d)|<ul><li>將右側三個引數的 Tuple 傳遞至左側的函式。<br /></li></ul>|
|`<@...@>`|[程式碼引號](../code-quotations.md)|<ul><li>分隔具類型的程式碼引號。<br /></li></ul>|
|`<@@...@@>`|[程式碼引號](../code-quotations.md)|<ul><li>分隔不具類型的程式碼引號。<br /></li></ul>|
|`=`|[算術運算子](arithmetic-operators.md)|<ul><li>如果左側等於右側，即傳回 `true`；否則傳回 `false`。<br /></li></ul>|
|`=?`|[可為 Null 的運算子](nullable-operators.md)|<ul><li>當右側是可為 null 的類型時，計算「等於」運算。<br /></li></ul>|
|`==`|不適用。|<ul><li>F# 中不使用。 使用 `=` 進行等號比較運算。<br /></li></ul>|
|`>`|[算術運算子](arithmetic-operators.md)|<ul><li>如果左側大於右側，即傳回 `true`；否則傳回 `false`。<br /></li></ul>|
|`>?`|[可為 Null 的運算子](nullable-operators.md)|<ul><li>當右側是可為 null 的型別時，請計算 「 大於 」 運算。<br /></li></ul>|
|`>>`|[函式](../functions/index.md)|<ul><li>撰寫兩個函式 (正向撰寫運算子)。<br /></li></ul>|
|`>>>`|[位元運算子](bitwise-operators.md)|<ul><li>將左側數量中的位元，向右移位右側指定的位數。<br /></li></ul>|
|`>=`|[算術運算子](arithmetic-operators.md)|<ul><li>會傳回`true`左側是大於或等於右側，否則會傳回`false`。<br /></li></ul>|
|`>=?`|[可為 Null 的運算子](nullable-operators.md)|<ul><li>當右側是可為 null 的類型時，計算「大於或等於」運算。<br /></li></ul>|
|`?`|[參數和引數](../parameters-and-arguments.md)|<ul><li>指定選擇性引數。<br /></li><li>用做為動態方法及屬性呼叫的運算子。 您必須提供自己的實作。<br /></li></ul>|
|`? ... <- ...`|沒有可用的詳細資訊。|<ul><li>用來做為設定動態屬性的運算子。 您必須提供自己的實作。<br /></li></ul>|
|`?>=`, `?>`, `?<=`, `?<`, `?=`, `?<>`, `?+`, `?-`, `?*`, `?/`|[可為 Null 的運算子](nullable-operators.md)|<ul><li>相當於沒有 ? 前置詞的對應運算子， 其中可為 null 的類型在左側。<br /></li></ul>|
|`>=?`, `>?`, `<=?`, `<?`, `=?`, `<>?`, `+?`, `-?`, `*?`, `/?`|[可為 Null 的運算子](nullable-operators.md)|<ul><li>相當於沒有 ? 前置詞的對應運算子， 其中可為 null 的類型在右側。<br /></li></ul>|
|`?>=?`, `?>?`, `?<=?`, `?<?`, `?=?`, `?<>?`, `?+?`, `?-?`, `?*?`, `?/?`|[可為 Null 的運算子](nullable-operators.md)|<ul><li>相當於沒有問號括住的對應運算子，其兩側都是可為 null 的類型。<br /></li></ul>|
|`@`|[清單](../lists.md)<br /><br />[字串](../strings.md)|<ul><li>串連兩個清單。<br /></li><li>置於字串常值前面時，表示要逐字解譯字串，但是不解譯逸出字元。<br /></li></ul>|
|`[...]`|[清單](../lists.md)|<ul><li>分隔清單的元素。<br /></li></ul>|
|<code>[&#124;...&#124;]</code>|[陣列](../arrays.md)|<ul><li>分隔陣列的元素。<br /></li></ul>|
|`[<...>]`|[屬性](../attributes.md)|<ul><li>分隔屬性。<br /></li></ul>|
|`\`|[字串](../strings.md)|<ul><li>逸出下一個字元；用於字元和字串常值中。<br /></li></ul>|
|`^`|[以統計方式解析的類型參數](../generics/statically-resolved-type-parameters.md)<br /><br />[字串](../strings.md)|<ul><li>指定必須在編譯階段 (而非執行階段) 解析的型別參數。<br /></li><li>串連字串。<br /></li></ul>|
|`^^^`|[位元運算子](bitwise-operators.md)|<ul><li>計算位元互斥 OR 運算。<br /></li></ul>|
|`_`|[比對運算式](../match-expressions.md)<br /><br />[泛型](../generics/index.md)|<ul><li>表示萬用字元模式。<br /></li><li>指定匿名泛型參數。<br /></li></ul>|
|<code>&#96;</code>|[自動一般化](../generics/automatic-generalization.md)|<ul><li>使用於內部，用於表示泛型型別參數。<br /></li></ul>|
|`{...}`|[序列](../sequences.md)<br /><br />[記錄](../records.md)|<ul><li>分隔循序項運算式與計算運算式。<br /></li><li>用於記錄定義中。<br /></li></ul>|
|<code>&#124;</code>|[比對運算式](../match-expressions.md)|<ul><li>分隔各個相符的情況、個別差別聯集宣告和列舉值。<br /></li></ul>|
|<code>&#124;&#124;</code>|[布林運算子](boolean-operators.md)|<ul><li>計算布林值 OR 運算。<br /></li></ul>|
|<code>&#124;&#124;&#124;</code>|[位元運算子](bitwise-operators.md)|<ul><li>計算位元 OR 運算。<br /></li></ul>|
|<code>&#124;></code>|[函式](../functions/index.md)|<ul><li>將左側的結果傳遞至右側的函式 (正向管道運算子)。<br /></li></ul>|
|<code>&#124;&#124;></code>|[Operators.&#40; &#124;&#124;&#62; &#41;&#60;'T1,'T2,'U&#62; 函式](https://msdn.microsoft.com/visualfsharpdocs/conceptual/operators.%5b-hh%5d-%5d%5b%27t1%2c%27t2%2c%27u%5d-function-%5bfsharp%5d)|<ul><li>將左側兩個引數的 Tuple 傳遞至右側的函式。<br /></li></ul>|
|<code>&#124;&#124;&#124;></code>|[Operators.&#40; &#124;&#124;&#124;&#62; &#41;&#60;'T1,'T2,'T3,'U&#62; 函式](https://msdn.microsoft.com/visualfsharpdocs/conceptual/operators.%5b-hhh%5d-%5d%5b%27t1%2c%27t2%2c%27t3%2c%27u%5d-function-%5bfsharp%5d)|<ul><li>將左側三個引數的 Tuple 傳遞至右側的函式。<br /></li></ul>|
|`~~`|[運算子多載](../operator-overloading.md)|<ul><li>用以宣告一元負運算子的多載。<br /></li></ul>|
|`~~~`|[位元運算子](bitwise-operators.md)|<ul><li>計算位元 NOT 運算。<br /></li></ul>|
|`~-`|[運算子多載](../operator-overloading.md)|<ul><li>用以宣告一元相減運算子的多載。<br /></li></ul>|
|`~+`|[運算子多載](../operator-overloading.md)|<ul><li>用以宣告一元相加運算子的多載。<br /></li></ul>|

## <a name="operator-precedence"></a>運算子優先順序

下表顯示 F# 語言中運算子和其他運算式關鍵字的優先順序，順序從最低的優先順序到最高的優先順序。 同時列出關聯性 (如果適用的話)。

|運算子|順序關聯性|
|--------|-------------|
|`as`|右|
|`when`|右|
|<code>&#124;</code> （管線）|左|
|`;`|右|
|`let`|Nonassociative|
|`function`, `fun`, `match`, `try`|Nonassociative|
|`if`|Nonassociative|
|`->`|右|
|`:=`|右|
|`,`|Nonassociative|
|`or`、 <code>&#124;&#124;</code>|左|
|`&`、 `&&`|左|
|`:>`、 `:?>`|右|
|`<`*op*， `>` *op*， `=`， <code>&#124;</code> *op*， `&` *op*， `&`<br /><br />(包括 `<<<`、`>>>`、<code>&#124;&#124;&#124;</code>、`&&&`)|左|
|`^`*op*<br /><br />(包括 `^^^`)|右|
|`::`|右|
|`:?`|未關聯|
|`-`*op*、`+`*op*|適用於這些符號的中置用法|
|`*`*op*、`/`*op*、`%`*op*|左方|
|`**`*op*|右方|
|`f x` (函式應用程式)|左|
|<code>&#124;</code> （模式比對）|右|
|前置運算子 (`+`*op*、`-`*op*、`%`、`%%`、`&`、`&&`、`!`*op*、`~`*op*)|左|
|`.`|左|
|`f(x)`|左|
|`f<`*類型*`>`|左|

F# 支援自訂運算子多載。 這表示您可以定義自己的運算子。 在上表中，*op* 可以是任何有效的 (可能是空的) 運算子字元序列，即內建或使用者定義的序列。 因此，您可以使用此表格來判斷要對自訂運算子使用什麼字元序列，以達到您想要的優先順序等級。 前置 `.` 字元在編譯器判斷優先順序時，會予以忽略。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](../index.md)
- [運算子多載](../operator-overloading.md)
