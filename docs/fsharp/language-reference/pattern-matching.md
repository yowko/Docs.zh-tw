---
title: 模式比對 (F#)
description: '了解模式如何在 F # 中用來比較具有邏輯結構的資料、 將資料分解為構成部分，或從資料擷取資訊。'
ms.date: 05/16/2016
ms.openlocfilehash: 5ad3d3e1a78246afdfa2948fd0fb84fa04686d30
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "45991420"
---
# <a name="pattern-matching"></a>模式比對

模式是轉換輸入的資料的規則。 它們可在 F # 語言比較具有邏輯結構或結構的資料、 將資料分解為構成部分，或以各種方式從資料擷取資訊。

## <a name="remarks"></a>備註

模式可用於許多語言建構，例如`match`運算式。 您正在處理中的函式的引數時，它們會使用`let`繫結、 lambda 運算式，並與相關聯的例外狀況處理常式中`try...with`運算式。 如需詳細資訊，請參閱 <<c0> [ 比對運算式](match-expressions.md)， [let 繫結](functions/let-bindings.md)， [Lambda 運算式：`fun`關鍵字](functions/lambda-expressions-the-fun-keyword.md)，以及[例外狀況： `try...with`運算式](exception-handling/the-try-with-expression.md)。

例如，在`match`運算式*模式*是什麼位於管道符號後面。

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

每個模式做為轉換以某種方式輸入的規則。 在 `match`運算式中，每個模式會接著檢查輸入的資料是否與模式相容。 如果找到相符項目，則會執行結果運算式。 如果找不到相符項目，則會測試下一個模式規則。 選擇性 when*條件*組件會說明[比對運算式](match-expressions.md)。

下表顯示支援的模式。 在執行階段，針對每個資料表中列出的順序中的下列模式輸入測試和模式，遞迴地套用，從第一次到最後一個出現在您的程式碼，並從左到右的模式，便在每一行。

|名稱|描述|範例|
|----|-----------|-------|
|常數模式|任何數值、 字元或字串常值、 列舉常數或定義的常值識別項|`1.0`, `"test"`, `30`, `Color.Red`|
|識別項模式|已區分的聯集、 例外狀況標籤或作用中模式案例的情況下，值|`Some(x)`<br /><br />`Failure(msg)`|
|變數模式|*identifier*|`a`|
|`as` 模式|*圖樣*做為*識別碼*|`(a, b) as tuple1`|
|或模式|*pattern1* &#124; *pattern2*|<code>([h] &#124; [h; _])</code>|
|和模式|*pattern1* &amp; *pattern2*|`(a, b) & (_, "test")`|
|Cons 模式|*識別項*::*清單識別碼*|`h :: t`|
|清單模式|[ *pattern_1*;...&lt;*pattern_n* ]|`[ a; b; c ]`|
|陣列模式|[&#124; *pattern_1*;..;*pattern_n* &#124;]|<code>[&#124; a; b; c &#124;]</code>|
|括號模式|(*模式*)|`( a )`|
|Tuple 模式|( *pattern_1*，...， *pattern_n* )|`( a, b )`|
|記錄模式|{ *identifier1* = *pattern_1*;...&lt;*identifier_n* = *pattern_n* }|`{ Name = name; }`|
|萬用字元模式|_|`_`|
|搭配類型附註的模式|*圖樣*:*類型*|`a : int`|
|類型測試模式|:? *型別*[做為*識別碼*]|`:? System.DateTime as dt`|
|Null 模式|null|`null`|

## <a name="constant-patterns"></a>常數模式

常數模式是 （使用包含列舉型別名稱） 的數值、 字元和字串常值、 列舉常數。 A`match`只有常數模式的運算式好比其他語言的 case 陳述式。 與常值進行比較的輸入和模式比對的值是否相等。 常值類型必須與輸入的類型相容。

下列範例會示範如何使用常值的模式，並也會使用變數模式和 OR 模式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

常值模式的另一個範例是基於列舉常數的模式。 當您使用列舉常數時，您必須指定列舉型別名稱。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a>識別項模式

如果模式是形成有效識別碼字元的字串，識別項的格式會決定如何比對的模式。 如果識別項的長度大於單一字元，且開頭為大寫的字元，編譯器會嘗試比對識別項模式。 此模式的識別項可能是常值的屬性、 差別的聯集、 例外狀況識別項或現用模式案例所標記的值。 如果不找到任何相符的識別項，則比對失敗下, 一個模式規則，該變數的模式，相較於輸入。

已區分的聯集模式可以是簡單的具名案例，或可以有一個值或包含多個值的 tuple。 如果沒有值，您必須指定值的識別碼。 如果是 tuple，您必須提供 tuple 模式 tuple 的每個元素的識別碼或識別項使用欄位名稱，其中一個或多個具名聯合欄位。 請參閱本節的範例中的程式碼範例。

`option`型別是具有兩個案例的已區分聯集`Some`和`None`。 其中一個案例 (`Some`) 有值，但其他 (`None`) 只是具名的案例。 因此，`Some`必須有相關聯的值的變數`Some`案例，但`None`必須單獨出現。 下列程式碼中，變數`var1`的值會指定所比對，以取得`Some`案例。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

在下列範例中，`PersonName`差別等位包含字串和字元，表示可能名稱形式的混合。 已區分的聯集的情況下都`FirstOnly`， `LastOnly`，和`FirstLast`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

針對擁有具名欄位的差別聯集，您可以使用等號 （=） 擷取具名欄位的值。 比方說，請考慮使用的宣告，如下所示的已區分聯集。

```fsharp
type Shape =
    | Rectangle of height : float * width : float
    | Circle of radius : float
```

您可以使用模式比對運算式中的具名的欄位，如下所示。

```fsharp
let matchShape shape =
    match shape with
    | Rectangle(height = h) -> printfn "Rectangle with length %f" h
    | Circle(r) -> printfn "Circle with radius %f" r
```

具名欄位的使用是選擇性的因此在上述範例中，同時`Circle(r)`和`Circle(radius = r)`有相同的效果。

當您指定多個欄位時，請使用分號 （;） 做為分隔符號。

```
match shape with
| Rectangle(height = h; width = w) -> printfn "Rectangle with height %f and width %f" h w
| _ -> ()
```

作用中的模式可讓您定義更複雜的自訂模式比對。 如需有關使用中模式的詳細資訊，請參閱[作用中的模式](active-patterns.md)。

識別項例外狀況的情況用於模式比對的例外狀況處理常式內容中。 模式比對的例外狀況處理的相關資訊，請參閱[例外狀況：`try...with`運算式](exception-handling/the-try-with-expression.md)。

## <a name="variable-patterns"></a>變數模式

變數模式會將符合變數的名稱，就可用於執行運算式右邊的值指派`->`符號。 變數模式本身會符合任何輸入，但是變數模式通常會出現在其他模式，因此可讓更複雜的結構，例如 tuple 和分解為變數的陣列。

下列範例會示範 tuple 模式中的變數模式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a>as 模式

`as`模式是具有模式`as`子句附加到它。 `as`子句將相符的值繫結至可用的執行運算式中的名稱`match`運算式，或在此模式中的使用案例中`let`繫結，名稱會加入為區域範圍繫結。

下列範例會使用`as`模式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a>或模式

時輸入的資料可以符合多個模式，而且您想要執行相同的程式碼，如此一來，就會使用 OR 模式。 OR 模式兩邊的類型必須相容。

下列範例會示範 OR 模式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a>和模式

AND 模式要求輸入應符合兩個模式。 AND 模式兩邊的類型必須相容。

下列範例很相似`detectZeroTuple`示[Tuple 模式](https://msdn.microsoft.com/library/#tuple)稍後本主題中，但在此節`var1`和`var2`透過 AND 模式取得的值。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a>Cons 模式

Cons 模式用來將清單分解為第一個項目中， *head*，以及包含其餘的項目，清單*結尾*。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a>清單模式

清單模式可讓清單分解為的項目數目。 清單模式本身可以比對只列出特定數目的項目。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a>陣列模式

陣列模式類似於清單模式，並可用於分解特定長度的陣列。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a>括號模式

括號可括住模式，達到所需的關聯性。 在下列範例中，會使用括號控制 AND 模式和 cons 模式之間的關聯性。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a>Tuple 模式

Tuple 模式比對 tuple 形式的輸入，並讓 tuple 分解為其構成項目使用模式比對 tuple 中的每個位置的變數。

下列範例會示範 tuple 模式，並也會使用常值模式、 變數模式和萬用字元模式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a>記錄模式

記錄模式用來分解記錄以擷取欄位的值。 此模式不需要參考記錄; 的所有欄位只要任何省略的欄位不會參與比對，並不會擷取。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a>萬用字元模式

萬用字元模式以底線 (`_`) 字元和符合任何輸入，如同變數模式中，不同之處在於將輸入捨棄而不是指派給變數。 萬用字元模式通常用來在其他模式做為預留位置值右邊的運算式中不需要`->`符號。 萬用字元模式也常使用的模式清單結尾來比對任何不相符的輸入。 本主題中的許多程式碼範例將示範萬用字元模式。 請參閱上述的程式碼取得一例。

## <a name="patterns-that-have-type-annotations"></a>具有類型附註的模式

模式可以有類型註解。 這些行為類似其他型別註解，會指引推斷等其他型別註解。 在模式中的型別附註前後需要括號。 下列程式碼會顯示有類型註釋的模式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a>類型測試模式

類型測試模式用來比對類型。 如果輸入的類型比對 （或衍生的型別） 中的模式比對指定的類型就會成功。

下列範例將示範類型測試模式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

## <a name="null-pattern"></a>Null 模式

Null 模式比對您正在使用允許 null 值的類型，可能會出現 null 值。 Null 模式常用於與.NET Framework 程式碼交互作用時。 例如，.NET API 的傳回值可能的輸入`match`運算式。 您可以控制是否傳回的值為 null，同時也會在傳回值的其他特性為基礎的程式流程。 您可以使用 null 模式，以防止將 null 值傳播至程式其餘部分。

下列範例會使用 null 模式和變數模式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="see-also"></a>另請參閱

- [比對運算式](match-expressions.md)
- [使用中模式](active-patterns.md)
- [F# 語言參考](index.md)
