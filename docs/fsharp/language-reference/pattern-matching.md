---
title: 模式比對 (F#)
description: '了解如何使用模式在 F # 中比較具有邏輯結構的資料、 將資料分解成構成部分，或從資料擷取資訊。'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 31a5b321e5daecdc3add9a205d60b63b2c00ccd2
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="pattern-matching"></a>模式比對

模式是轉換輸入的資料的規則。 它們會使用 F # 語言來比較邏輯的結構或結構的資料、 將資料分解成構成部分，或從各種資料擷取資訊。


## <a name="remarks"></a>備註
模式中使用許多語言建構，例如`match`運算式。 您正在處理中的函式的引數時，它們會使用`let`繫結和 lambda 運算式和相關聯的例外狀況處理常式中`try...with`運算式。 如需詳細資訊，請參閱[比對運算式](match-expressions.md)， [let 繫結](functions/let-bindings.md)， [Lambda 運算式：`fun`關鍵字](functions/lambda-expressions-the-fun-keyword.md)，和[例外狀況： `try...with`運算式](exception-handling/the-try-with-expression.md)。

例如，在`match`運算式*模式*是縱線符號後面。

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

每個模式會做為轉換以某種方式輸入的規則。 在`match`運算式中，每個模式會接著檢查以查看是否相容的模式與輸入的資料。 如果找到相符項目，將執行結果運算式。 如果找不到相符項目，則會測試的下一個模式規則。 選擇性當*條件*組件中會說明[比對運算式](match-expressions.md)。

支援的模式下表中顯示。 在執行階段，輸入會針對每個資料表中列出的順序的下列模式來測試和模式會遞迴地套用，從第一次到最後一個出現在您的程式碼中，從左到右的模式，便在每一行。

|名稱|描述|範例|
|----|-----------|-------|
|常數模式|任何數值、 字元或字串常值、 列舉常數或定義常值的識別項|`1.0`、`"test"`、`30``Color.Red`|
|識別項模式|差別等位、 例外狀況標籤或現用模式大小寫的 case 值|`Some(x)`<br /><br />`Failure(msg)`|
|變數模式|*identifier*|`a`|
|`as` 模式|*模式*為*識別碼*|`(a, b) as tuple1`|
|或圖樣|*pattern1* &#124; *pattern2*|<code>([h] &#124; [h; _])</code>|
|和模式|*pattern1* &amp; *pattern2*|`(a, b) & (_, "test")`|
|Cons 模式|*識別項*::*清單識別碼*|`h :: t`|
|清單模式|[ *pattern_1*;...;*pattern_n* ]|`[ a; b; c ]`|
|陣列模式|[&#124; *pattern_1*;..;*pattern_n* &#124;]|<code>[&#124; a; b; c &#124;]</code>|
|括號括住模式|(*模式*)|`( a )`|
|Tuple 模式|( *pattern_1*，...， *pattern_n* )|`( a, b )`|
|記錄模式|{ *identifier1* = *pattern_1*;...;*identifier_n* = *pattern_n* }|`{ Name = name; }`|
|萬用字元模式|_|`_`|
|搭配類型註釋的模式|*模式*:*類型*|`a : int`|
|類型測試模式|:? *型別*[做為*識別碼*]|`:? System.DateTime as dt`|
|Null 模式|null|`null`|

## <a name="constant-patterns"></a>常數的模式
常數的模式是 （使用包含列舉型別名稱） 的數值、 字元和字串常值、 列舉常數。 A`match`只常數模式的運算式可以與其他語言中的 case 陳述式。 輸入比較的常值和模式會比對的值是否相等。 常值類型必須與輸入的類型相容。

下列範例會示範如何使用常值模式，並也會使用變數的模式和 OR 模式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

常值模式的另一個範例是根據列舉常數的模式。 當您使用的列舉常數，您必須指定列舉型別名稱。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a>識別項模式
如果模式是字元字串構成有效的識別項，識別項的格式會決定如何比對模式。 如果識別項長度超過單一字元，且開頭為大寫的字元，編譯器會嘗試比對識別項模式。 此模式的識別項可能是標記為常值的屬性、 差別的聯集、 例外狀況的識別項或現用模式大小寫的值。 如果不找到任何相符的識別項，則比對失敗下, 一個模式規則，該變數的模式，會與輸入。

差別等位模式可以是簡單名稱的情況下，或它們可以有一個值或包含多個值的 tuple。 如果沒有值，您必須指定值的識別碼。 Tuple，您必須提供每個元素 tuple 的識別碼或識別項具有一個欄位名稱與 tuple 模式或多個名為聯集的欄位。 請參閱本節的範例中的程式碼範例。

`option`類型是具有兩種情況下，差別的等位`Some`和`None`。 其中一個案例中 (`Some`) 具有值，但其他 (`None`) 是只具名的情況。 因此，`Some`必須有相關聯的值的變數`Some`案例，但`None`必須單獨出現。 下列程式碼變數`var1`透過比對的值會指定`Some`案例。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

在下列範例中，`PersonName`差別等位包含字串和字元，表示名稱的可能表單的混合。 差別等位的情況下會`FirstOnly`， `LastOnly`，和`FirstLast`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

差別聯集已命名欄位，您可以使用等號 （=） 來擷取具名欄位的值。 例如，請考慮具有宣告，如下所示的差別等位。

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

具名欄位的使用是選擇性的因此在前一個範例中，同時`Circle(r)`和`Circle(radius = r)`有相同的效果。

當您指定多個欄位時，請使用分號 （;） 做為分隔符號。

```
match shape with
| Rectangle(height = h; width = w) -> printfn "Rectangle with height %f and width %f" h w
| _ -> ()
```

現用模式可讓您定義更複雜的自訂模式比對。 如需現用模式的詳細資訊，請參閱[現用模式](active-patterns.md)。

例外狀況處理常式的內容中的比對模式中所使用的情況下，識別項例外狀況。 模式比對中例外狀況處理的相關資訊，請參閱[例外狀況：`try...with`運算式](exception-handling/the-try-with-expression.md)。


## <a name="variable-patterns"></a>變數模式
變數模式所比對變數的名稱，然後是可用於執行運算式右邊的值指派`->`符號。 單獨變數模式會比對任何輸入，但變數模式通常出現在其他的模式，因此啟用更複雜的結構，例如 tuple 和分解成變數的陣列。

下列範例會示範內 tuple 模式的變數模式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a>as 模式
`as`模式為模式，具有`as`子句附加至它。 `as`子句相符的值繫結可用於執行運算式中的名稱`match`運算式，或在此模式中的使用位置的情況下`let`繫結，名稱會新增為本機領域的繫結。

下列範例會使用`as`模式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a>或圖樣
OR 模式時輸入的資料可以比對多個模式，而且您想要執行相同的程式碼，如此一來使用。 OR 模式的兩邊的類型必須相容。

下列範例會示範 OR 模式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a>和模式
AND 模式需要輸入符合兩個模式。 AND 模式的兩邊的類型必須相容。

下列範例很相似`detectZeroTuple`示[Tuple 模式](https://msdn.microsoft.com/library/#tuple)> 一節稍後在本主題中，但這裡`var1`和`var2`取得方式是使用 AND 模式做為值。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a>Cons 模式
Cons 模式用來將清單分解成第一個項目， *head*，和包含其餘的項目，清單*結尾*。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a>清單模式
清單模式可讓清單來分解成一些項目。 在清單模式可以比對僅特定數目的項目清單。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a>陣列模式
陣列模式類似於清單模式，而且可用來將分解的特定長度的陣列。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a>括號括住模式
括號可以分組模式來達成所需的順序關聯性。 在下列範例中，括號用來控制 AND 模式和 cons 模式之間的關聯性。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a>Tuple 模式
Tuple 模式比對中 tuple 形式的輸入，並可讓 tuple 來分解成其組成的項目使用模式比對 tuple 中的每個位置的變數。

下列範例示範的 tuple 模式，並也會使用常值的模式、 變數的模式和萬用字元模式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a>記錄模式
記錄模式用來將分解記錄擷取欄位的值。 模式沒有參考所有欄位的記錄。只要任何省略的欄位不會參與比對，並不會擷取。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a>萬用字元模式
萬用字元模式由底線 (`_`) 字元和符合任何輸入，就像該變數的模式，不同之處在於輸入會捨棄而不是指派給變數。 萬用字元模式通常用於在其他模式內才能做為預留位置值右邊的運算式中不需要`->`符號。 萬用字元模式也經常使用的模式清單的結尾來比對任何不相符的輸入。 本主題中的許多程式碼範例會示範萬用字元模式。 請參閱上述的程式碼的其中一個範例。


## <a name="patterns-that-have-type-annotations"></a>有類型註釋的模式
模式可以有類型註釋。 這些行為與其他類型註釋一樣，引導推斷像其他類型註釋。 模式中的型別註解前後需要加括號。 下列程式碼會示範具有類型註釋的模式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a>類型測試模式
類型測試模式用來比對輸入對型別。 如果輸入的類型是符合項目 （或衍生型別） 在模式中，比對指定的型別將會成功。

下列範例會示範類型測試模式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

## <a name="null-pattern"></a>Null 模式
Null 模式比對您正在使用 允許 null 值的類型，可能會出現 null 值。 與.NET Framework 程式碼交互作用時，通常會使用 null 的模式。 .NET API 的傳回值，例如可能的輸入`match`運算式。 您可以控制是否傳回的值為 null，以及傳回值的其他特性為基礎的程式流程。 若要防止 null 的值傳播到其他的程式，您可以使用 null 的模式。

下列範例會使用 null 的模式和變數的模式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="see-also"></a>另請參閱
[比對運算式](match-expressions.md)

[使用中模式](active-patterns.md)

[F# 語言參考](index.md)
