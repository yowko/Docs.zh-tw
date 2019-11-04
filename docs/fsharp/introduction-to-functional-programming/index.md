---
title: F# 函式程式設計簡介
description: 瞭解功能程式設計的基本概念F#。
ms.date: 10/29/2018
ms.openlocfilehash: e1a0edc61dbe13012c48e166d490e22ebc70d6a0
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424703"
---
# <a name="introduction-to-functional-programming-in-f"></a>F\# 中的功能性程式設計簡介

函式程式設計是一種程式設計風格，強調函式和不可變數據的使用。 具型別函式程式設計是指將功能程式設計與靜態型F#別（例如和）結合在一起。 一般來說，功能程式設計中會強調下列概念：

* 函式做為您使用的主要結構
* 運算式，而不是語句
* 變數上的不可變值
* 透過命令式程式設計進行宣告式程式設計

在此系列中，您將使用F#來探索功能程式設計中的概念和模式。 在過程中，您也會學F#到一些。

## <a name="terminology"></a>用語

函式程式設計（如其他程式設計範例）隨附于最終需要學習的詞彙。 以下是您將會看到的一些常見詞彙：

* **Function** -函式是一種結構，會在提供輸入時產生輸出。 更正式地說，它會將一個集合中的專案_對應_到另一個集合。 這個形式會以許多方式細分成具體，特別是當使用在資料集合上操作的函數時。 這是功能性程式設計中最基本（且重要）的概念。
* **運算式**-運算式是在程式碼中產生值的結構。 在F#中，必須系結或明確忽略此值。 運算式可以完整由函式呼叫取代。
* **純度**-純度是函式的屬性，使相同的引數的傳回值一律相同，而且其評估沒有副作用。 純虛擬函式完全取決於其引數。
* **參考透明度**-引用透明度是運算式的屬性，可將其取代為其輸出，而不會影響程式的行為。
* 不**可變性-不可變性表示**值無法就地變更。 這與可就地變更的變數相反。

## <a name="examples"></a>範例

下列範例示範這些核心概念。

### <a name="functions"></a>函式

函式程式設計中最常見和基本的結構是函數。 以下是將1新增至整數的簡單函式：

```fsharp
let addOne x = x + 1
```

其型別簽章如下所示：

```fsharp
val addOne: x:int -> int
```

簽章可以讀取為，「`addOne` 接受名為 `x` 的 `int`，而且會產生 `int`」。 更正式地說，`addOne` 會將一組整數的值_對應_至整數集合。 `->` token 表示此對應。 在F#中，您通常可以查看函式簽章，以瞭解其用途。

那麼，簽章為什麼很重要？ 在具類型的函式程式設計中，函數的執行通常比實際的類型簽章較不重要！ `addOne` 將值1新增至整數的事實在執行時間很有趣，但當您在建立程式時，它會接受並傳回 `int`，這會通知您實際使用此函數的方式。 此外，一旦您正確使用此函式（相對於其類型簽章），診斷任何問題都只能在 `addOne` 函式的主體中完成。 這是具型別功能性程式設計背後的促成。

### <a name="expressions"></a>運算式

運算式是評估為值的結構。 相對於執行動作的語句，運算式可以被視為執行動作來提供值。 運算式幾乎一律用於功能程式設計中的語句。

請考慮先前的函式，`addOne`。 `addOne` 的主體是運算式：

```fsharp
// 'x + 1' is an expression!
let addOne x = x + 1
```

這是定義 `addOne` 函數之結果類型的運算式結果。 例如，構成此函式的運算式可能會變更為不同的類型，例如 `string`：

```fsharp
let addOne x = x.ToString() + "1"
```

函數的簽章現在是：

```fsharp
val addOne: x:'a -> string
```

由於中F#的任何類型都可以在其上呼叫 `ToString()`，因此 `x` 的類型已成為泛型（稱為[自動一般化](../language-reference/generics/automatic-generalization.md)），而結果類型是 `string`。

運算式不只是函式的主體。 您可以擁有會產生您在其他地方使用之值的運算式。 常見的 `if`：

```fsharp
// Checks if 'x' is odd by using the mod operator
let isOdd x = x % 2 <> 0

let addOneIfOdd input =
    let result =
        if isOdd input then
            input + 1
        else
            input

    result
```

`if` 運算式會產生稱為 `result`的值。 請注意，您可以完全省略 `result`，讓 `if` 運算式成為 `addOneIfOdd` 函數的主體。 運算式的重點是要記住的是，它們會產生一個值。

有一種特殊的類型，`unit`，在沒有要傳回的內容時使用。 例如，請考慮這個簡單的函數：

```fsharp
let printString (str: string) =
    printfn "String is: %s" str
```

簽章看起來像這樣：

```fsharp
val printString: str:string -> unit
```

`unit` 類型表示沒有傳回實際的值。 當您有一個必須「執行工作」的常式時，雖然沒有任何值會因該工作而傳回，這項功能就很有用。

這與命令式程式設計相反，其中對等的 `if` 結構是語句，而產生值通常是透過改變變數來完成。 例如，在中C#，程式碼的撰寫方式可能如下所示：

```csharp
bool IsOdd(int x) => x % 2 != 0;

int AddOneIfOdd(int input)
{
    var result = input;

    if (IsOdd(input))
    {
        result = input + 1;
    }

    return result;
}
```

值得注意的是， C#和其他 C 樣式語言都支援[三元運算式](../../csharp/language-reference/operators/conditional-operator.md)，這可允許以運算式為基礎的條件式程式設計。

在功能性程式設計中，使用語句來改變值很罕見。 雖然某些功能性語言支援語句和變化，但在函程式設計中使用這些概念並不常見。

### <a name="pure-functions"></a>純虛擬函式

如先前所述，純虛擬函式是函式：

* 針對相同的輸入，一律評估為相同的值。
* 沒有任何副作用。

在此內容中考慮數學函式會很有説明。 在數學中，函式只會相依于其引數，而且沒有任何副作用。 在數學函數 `f(x) = x + 1`中，`f(x)` 的值只取決於 `x`的值。 函式程式設計中的純虛擬函式是以相同的方式運作。

撰寫純虛擬函式時，函式必須只依賴其引數，而不會執行任何會產生副作用的動作。

以下是非純虛擬函式的範例，因為它相依于全域、可變的狀態：

```fsharp
let mutable value = 1

let addOneToValue x = x + value
```

`addOneToValue` 函式會清楚非純虛擬，因為 `value` 可以隨時變更，使其值不同于1。 視全域值而定，這種模式可避免在功能性程式設計中使用。

以下是非純虛擬函式的另一個範例，因為它會執行副作用：

```fsharp
let addOneToValue x =
    printfn "x is %d" x
    x + 1
```

雖然此函式不會相依于全域值，但它會將 `x` 的值寫入至程式的輸出。 雖然這麼做並沒有任何問題，但這也表示該函式不是純粹的。 如果程式的另一個部分相依于程式以外的某個專案（例如輸出緩衝區），則呼叫此函式可能會影響程式的其他部分。

移除 `printfn` 語句會讓函式成為純虛擬：

```fsharp
let addOneToValue x = x + 1
```

雖然此_函數原本就不如使用_`printfn` 語句的舊版，但它確實會保證所有此函式都會傳回值。 呼叫此函式會產生相同的結果：它只會產生值。 由純度所提供的可預測性是許多功能程式設計人員所致力的。

### <a name="immutability"></a>不變性

最後，具型別函式程式設計的最基本概念之一就是不可變性的。 在F#中，所有值預設都是不可變的。 這表示除非您明確地將它們標示為可變動，否則無法就地變動。

實際上，使用固定值表示您將程式設計的方法從「我需要變更某些專案」變更為「我需要產生新的值」。

例如，將1新增至值表示產生新的值，而不會改變現有的值：

```fsharp
let value = 1
let secondValue = value + 1
```

在F#中，下列程式碼**不會改變**`value` 函數;相反地，它會執行相等檢查：

```fsharp
let value = 1
value = value + 1 // Produces a 'bool' value!
```

有些功能性程式設計語言根本不支援變動。 在F#中，這是支援的，但不是值的預設行為。

此概念更進一步延伸至資料結構。 在功能性程式設計中，固定的資料結構（例如集合（和其他許多）會有不同于最初預期的執行方式。 在概念上，將專案加入至集合的作業並不會變更集合，它會產生_新_的集合，並加上值。 實際上，這通常是由不同的資料結構所完成，可讓您有效率地追蹤值，以便將適當的資料標記法指定為結果。

這種使用值和資料結構的樣式非常重要，因為它會強制您將任何修改專案的作業視為其建立新版本。 這可讓您的程式中的等號和可比較性保持一致。

## <a name="next-steps"></a>後續步驟

下一節將徹底探討函式，探索可在函式程式設計中使用它們的不同方式。

[第一級函式](first-class-functions.md)會深入探索函式，並示範如何在各種不同的內容中使用這些功能。

## <a name="further-reading"></a>進一步閱讀

[思考功能](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/)系列是另一個絕佳的資源，可供您瞭解F#如何使用進行功能程式設計。 其中涵蓋功能程式設計的基本概念，並以實用且容易閱讀的方式使用F#功能來說明概念。
