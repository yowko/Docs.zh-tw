---
title: 模式比對
description: '瞭解如何在 F # 中使用模式來比較資料與邏輯結構、將資料分解為構成部分，或從資料中取出資訊。'
ms.date: 11/12/2020
ms.openlocfilehash: e167712b082b7f587e41a78edcaf0a0db9c7294b
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94687801"
---
# <a name="pattern-matching"></a>模式比對

模式是轉換輸入資料的規則。 在 F # 語言中會使用它們來比較資料與邏輯結構或結構、將資料分解為構成部分，或從資料以各種方式將資訊解壓縮。

## <a name="remarks"></a>備註

模式用於許多語言結構，例如 `match` 運算式。 當您要處理系結中函式的引數 `let` 、lambda 運算式，以及與運算式相關聯的例外狀況處理常式時，就會使用這些函數 `try...with` 。 如需詳細資訊，請參閱 [Match 運算式](match-expressions.md)、 [let Bindings](./functions/let-bindings.md)、 [Lambda 運算式： `fun` 關鍵字](./functions/lambda-expressions-the-fun-keyword.md)和 [例外狀況： `try...with` 運算式](./exception-handling/the-try-with-expression.md)。

例如，在運算式中 `match` ， *模式* 會跟在管道符號之後。

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

每個模式都是以某種方式轉換輸入的規則。 在 `match` 運算式中，會依序檢查每個模式，以查看輸入資料是否與模式相容。 如果找到相符的結果運算式，就會執行結果運算式。 如果找不到相符項，則會測試下一個模式規則。 在比對 [運算式](match-expressions.md)中說明選擇性的 when *條件* 部分。

下表顯示支援的模式。 在執行時間，輸入會根據表格中所列的順序，針對下列每個模式進行測試，而模式會以遞迴方式套用（從第一次到最後，當它們出現在您的程式碼中），並從左至右套用至每一行的模式。

|名稱|描述|範例|
|----|-----------|-------|
|常數模式|任何數值、字元或字串常值、列舉常數或已定義的常值識別碼|`1.0`, `"test"`, `30`, `Color.Red`|
|識別碼模式|差異聯集的 case 值、例外狀況標籤或作用中模式案例|`Some(x)`<br /><br />`Failure(msg)`|
|變數模式|*identifier*|`a`|
|`as` 模式|*模式* as *識別碼*|`(a, b) as tuple1`|
|或模式|*pattern1* &#124; *pattern2*|<code>([h] &#124; [h; _])</code>|
|AND 模式|*pattern1* &amp;*pattern2*|`(a, b) & (_, "test")`|
|缺點模式|*identifier* ：： *list-identifier*|`h :: t`|
|清單模式|[ *pattern_1*; ...; *pattern_n* ]|`[ a; b; c ]`|
|陣列模式|[&#124; *pattern_1*; ...; *pattern_n* &#124;]|<code>[&#124; a; b; c &#124;]</code>|
|括弧模式| ( *模式* ) |`( a )`|
|元組模式| ( *pattern_1*， *pattern_n* ) |`( a, b )`|
|記錄模式|{ *identifier1*  = *pattern_1*;... ;*identifier_n*  = *pattern_n* }|`{ Name = name; }`|
|萬用字元模式|_|`_`|
|搭配類型注釋的模式|*模式* ： *類型*|`a : int`|
|類型測試模式|:? *類型* [as *識別碼* ]|`:? System.DateTime as dt`|
|Null 模式|null|`null`|
|Nameof 模式|*nameof 運算式*|`nameof str`|

## <a name="constant-patterns"></a>常數模式

常數模式包括數值、字元和字串常值、列舉常數 (包含) 包含的列舉型別名稱。 `match`只有常數模式的運算式可以與其他語言的 case 語句進行比較。 輸入會與常值進行比較，如果值相等，則模式會相符。 常值的型別必須與輸入的型別相容。

下列範例示範如何使用常值模式，並同時使用變數模式和或模式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

常值模式的另一個範例是以列舉常數為基礎的模式。 當您使用列舉常數時，必須指定列舉型別名稱。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a>識別碼模式

如果模式是形成有效識別碼的字元字串，則識別碼的格式會決定模式的比對方式。 如果識別碼的長度超過單一字元，並以大寫字元開頭，則編譯器會嘗試使其符合識別碼模式。 此模式的識別碼可能是以常值屬性標記的值、差異聯集大小寫、例外狀況識別碼或使用中的模式案例。 如果找不到相符的識別碼，則比對會失敗，而下一個模式規則（變數模式）會與輸入進行比較。

差異聯集模式可以是簡單名稱的案例，也可以具有值或包含多個值的元組。 如果有值，您必須指定值的識別碼。 在元組的案例中，您必須為元組的每個專案提供具有識別碼的元組模式，或使用一個或多個命名聯集欄位的功能變數名稱來提供識別碼。 如需範例，請參閱本節中的程式碼範例。

此 `option` 類型是具有兩個案例的差異聯集， `Some` 以及 `None` 。 其中一個案例 (`Some`) 有一個值，但另一個 (`None`) 只是一個命名的案例。 因此， `Some` 必須有與案例相關聯之值的變數 `Some` ，但 `None` 必須單獨出現。 在下列程式碼中，會將變數 `var1` 指定為符合大小寫所取得的值 `Some` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

在下列範例中，差異聯 `PersonName` 集包含混合的字串和字元，表示可能的名稱形式。 差異聯集的案例為 `FirstOnly` 、 `LastOnly` 和 `FirstLast` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

針對具有命名欄位的差異聯集，您可以使用等號 (=) 來將命名欄位的值解壓縮。 例如，請考慮使用類似如下的宣告的差異聯集。

```fsharp
type Shape =
    | Rectangle of height : float * width : float
    | Circle of radius : float
```

您可以使用模式比對運算式中的命名欄位，如下所示。

```fsharp
let matchShape shape =
    match shape with
    | Rectangle(height = h) -> printfn "Rectangle with length %f" h
    | Circle(r) -> printfn "Circle with radius %f" r
```

使用命名欄位是選擇性的，因此在上述範例中， `Circle(r)` 和都 `Circle(radius = r)` 有相同的效果。

當您指定多個欄位時，請使用分號 (; ) 作為分隔符號。

```fsharp
match shape with
| Rectangle(height = h; width = w) -> printfn "Rectangle with height %f and width %f" h w
| _ -> ()
```

現用模式可讓您定義更複雜的自訂模式比對。 如需使用中模式的詳細資訊，請參閱使用中的 [模式](active-patterns.md)。

在例外狀況處理常式內容中的模式比對中，會使用識別碼為例外狀況的情況。 如需例外狀況處理中的模式比對的詳細資訊，請參閱 [例外狀況： `try...with` 運算式](./exception-handling/the-try-with-expression.md)。

## <a name="variable-patterns"></a>變數模式

變數模式會將符合的值指派給變數名稱，然後在符號右邊的執行運算式中使用 `->` 。 變數模式只會比對任何輸入，但變數模式通常會出現在其他模式內，因此可讓您將更複雜的結構（例如元組和陣列）分解為變數。

下列範例示範在元組模式內的變數模式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a>as 模式

`as`模式是一種已 `as` 附加子句的模式。 子句會將 `as` 相符的值系結至運算式的執行運算式中可使用的名稱 `match` ，或者，如果在系結中使用此模式，則會將 `let` 名稱加入至區域範圍的系結。

下列範例會使用 `as` 模式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a>或模式

當輸入資料可以比對多個模式，而您想要執行與結果相同的程式碼時，就會使用或模式。 或模式兩側的類型都必須相容。

下列範例示範或模式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a>AND 模式

和模式要求輸入必須符合兩個模式。 和模式兩邊的類型都必須相容。

下列範例類似于 `detectZeroTuple` 本主題稍後的「元組模式」一節中所示，但在這裡， `var1` 和 `var2` 都是使用和模式來取得值。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a>缺點模式

缺點模式可用來將清單分解為第一個元素、 *head*，以及包含其餘元素（ *結尾*）的清單。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a>清單模式

清單模式可將清單分解成多個元素。 清單模式本身只能比對特定元素數目的清單。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a>陣列模式

陣列模式與清單模式類似，可用於分解特定長度的陣列。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a>括弧模式

括弧可在模式周圍分組，以達成所需的關聯性。 在下列範例中，括弧是用來控制和模式之間的關聯性，以及缺點模式之間的關聯性。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a>元組模式

元組模式會比對元組形式的輸入，並使用元組中的每個位置的模式比對變數，將元組分解為其組成元素。

下列範例將示範元組模式，也會使用常值模式、變數模式和萬用字元模式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a>記錄模式

記錄模式用於分解記錄，以將欄位值解壓縮。 模式不需要參考記錄的所有欄位;任何省略的欄位都不會參與比對，也不會解壓縮。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a>萬用字元模式

萬用字元模式是以底線 () 字元表示，並比對 `_` 任何輸入（如同變數模式），但會捨棄輸入而不是指派給變數。 萬用字元模式通常用於其他模式中，作為符號右邊運算式中不需要的值預留位置 `->` 。 萬用字元模式也經常用於模式清單的結尾，以符合任何不相符的輸入。 本主題的許多程式碼範例會示範萬用字元模式。 請參閱上述程式碼中的一個範例。

## <a name="patterns-that-have-type-annotations"></a>具有類型注釋的模式

模式可以有類型注釋。 這些行為類似其他類型注釋和參考參考，例如其他類型注釋。 模式中的類型注釋周圍需要括弧。 下列程式碼顯示具有類型注釋的模式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a>類型測試模式

型別測試模式是用來比對輸入與型別。 如果輸入類型與 (的相符項或) 類型中所指定之類型的衍生型別相符，則比對成功。

下列範例示範型別測試模式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

如果您只是要檢查識別碼是否屬於特定的衍生類型，則不需要模式的 `as identifier` 部分，如下列範例所示：

```fsharp
type A() = class end
type B() = inherit A()
type C() = inherit A()

let m (a: A) =
    match a with
    | :? B -> printfn "It's a B"
    | :? C -> printfn "It's a C"
    | _ -> ()
```

## <a name="null-pattern"></a>Null 模式

Null 模式符合當您使用允許 null 值的類型時，可能出現的 null 值。 當與 .NET Framework 程式碼交互操作時，經常會使用 Null 模式。 例如，.NET API 的傳回值可能是運算式的輸入 `match` 。 您可以根據傳回值是否為 null，以及傳回值的其他特性來控制程式流程。 您可以使用 null 模式來防止 null 值傳播至程式的其餘部分。

下列範例會使用 null 模式和變數模式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="nameof-pattern"></a>Nameof 模式

`nameof`當字串值等於關鍵字後面的運算式時，模式會與字串相符 `nameof` 。 例如：

```fsharp
let f (str: string) =
    match str with
    | nameof str -> "It's 'str'!"
    | _ -> "It is not 'str'!"

f "str" // matches
f "asdf" // does not match
```

[`nameof`](nameof.md)如需您可以使用之名稱的相關資訊，請參閱運算子。

## <a name="see-also"></a>另請參閱

- [比對運算式](match-expressions.md)
- [現用模式](active-patterns.md)
- [F # 語言參考](index.md)
