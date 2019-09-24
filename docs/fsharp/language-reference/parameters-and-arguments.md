---
title: 參數和引數
description: 瞭解定義F#參數的語言支援，以及將引數傳遞至函式、方法和屬性的功能。
ms.date: 05/16/2016
ms.openlocfilehash: e8094ffbc55870b5de75acb740aa2736ec6590a5
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216833"
---
# <a name="parameters-and-arguments"></a>參數和引數

本主題說明定義參數以及將引數傳遞至函式、方法和屬性的語言支援。 其中包含有關如何以傳址方式傳遞的資訊，以及如何定義和使用可接受可變數目之引數的方法。

## <a name="parameters-and-arguments"></a>參數和引數

詞彙*參數*是用來描述預期要提供之值的名稱。 詞彙*引數*會用於為每個參數提供的值。

參數可以指定于元組或擴充形式，或兩者的某種組合中。 您可以使用明確的參數名稱傳遞引數。 方法的參數可以指定為選擇性，並提供預設值。

## <a name="parameter-patterns"></a>參數模式

在一般情況下，提供給函式和方法的參數是以空格分隔的模式。 這表示，在「比對[運算式](match-expressions.md)」中所描述的任何模式，都可以用於函式或成員的參數清單中。

方法通常會使用傳遞引數的元組形式。 這可從其他 .NET 語言的觀點來得到更清楚的結果，因為元組表單符合在 .NET 方法中傳遞引數的方式。

使用系結所建立`let`的函式最常使用「擴充表單」。

下列虛擬代碼顯示元組和擴充引數的範例。

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

當某些引數位於元組中，而有些則不是時，可能會結合表單。

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

其他模式也可以在參數清單中使用，但如果參數模式不符合所有可能的輸入，則在執行時間可能會有不完整的相符項。 當自`MatchFailureException`變數的值不符合參數清單中指定的模式時，就會產生例外狀況。 當參數模式允許不完整的相符專案時，編譯器會發出警告。 至少另一個模式通常適用于參數清單，而這是萬用字元模式。 當您只想要忽略所提供的任何引數時，您可以在參數清單中使用萬用字元模式。 下列程式碼說明如何在引數清單中使用萬用字元模式。

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

當您不想對通常提供為字串陣列的命令列引數（如下列程式碼所示）時，萬用字元模式就很有用，因為當您不需要傳入的引數時（例如在程式的主要進入點中）。

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

有時在引數中使用的`as`其他模式是模式，以及與不同等位和作用中模式相關聯的識別碼模式。 您可以使用單一案例的區分聯集模式，如下所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

輸出如下。

```console
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

作用中模式可以做為參數使用，例如，將引數轉換成所需的格式時，如下列範例所示：

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

您可以使用`as`模式來儲存符合的值做為區域值，如下列程式程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

偶爾使用的另一個模式是將最後一個引數保留為未命名的函式，方法是提供，做為函數的主體，此 lambda 運算式會立即執行隱含引數的模式比對。 下面這行程式碼就是其中一個範例。

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

這段程式碼會定義一個採用泛型清單的函`true`式，並在清單是空`false`的時傳回，否則會傳回。 使用這類技術可能會使程式碼更容易閱讀。

有時候，包含不完整相符專案的模式很有用，例如，如果您知道程式中的清單只有三個元素，您可以在參數清單中使用類似下列的模式。

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

使用具有不完整相符專案的模式，最好是保留給快速原型設計和其他暫存用途。 編譯器會發出這類程式碼的警告。 這類模式無法涵蓋所有可能輸入的一般案例，因此不適合元件 Api。

## <a name="named-arguments"></a>具名引數

方法的引數可以透過以逗號分隔的引數清單中的位置來指定，也可以藉由提供名稱（後面接著等號和要傳入的值）明確地傳遞給方法。 如果藉由提供名稱來指定，它們可以與宣告中使用的不同順序出現。

具名引數可讓程式碼更容易閱讀，並更適應 API 中特定類型的變更，例如方法參數的重新排列。

具名引數僅適用于方法，不允許用於`let`系結函式、函數值或 lambda 運算式。

下列程式碼範例示範如何使用具名引數。

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

在類別函式的呼叫中，您可以使用類似于具名引數的語法來設定類別的屬性值。 下列範例顯示此語法。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

如需詳細資訊，請參閱[函數（F#）](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05)。

## <a name="optional-parameters"></a>選擇性參數

您可以使用參數名稱前面的問號來指定方法的選擇性參數。 選擇性參數會被F#視為選項類型，因此您可以使用`match`運算式`Some`搭配和`None`，以一般方式查詢選項類型。 選擇性參數只能用於成員，而不允許使用`let`系結所建立的函式。

您可以使用參數名稱（例如`?arg=None`或`?arg=Some(3)`或`?arg=arg`），將現有的選擇性值傳遞給方法。 建立將選擇性引數傳遞至另一個方法的方法時，這會很有用。

您也可以使用函數`defaultArg`來設定選擇性引數的預設值。 `defaultArg`函式會接受選擇性參數作為第一個引數，並使用預設值做為第二個。

下列範例說明選擇性參數的用法。

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

輸出如下。

```console
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
```

為了讓C#和 Visual Basic interop，您可以使用中`[<Optional; DefaultParameterValue<(...)>]` F#的屬性，讓呼叫端將引數視為選擇性。 這相當於在中將引數定義為C#選擇性`MyMethod(int i = 3)`的。

```fsharp
open System
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue("Hello world")>] message) =
        printfn "%s" message
```

您也可以指定新的物件做為預設參數值。 例如， `Foo`成員可能會有選擇性`CancellationToken`的作為輸入，而不是：

```fsharp
open System.Threading
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue(CancellationToken())>] ct: CancellationToken) =
        printfn "%A" ct
```

指定為引數`DefaultParameterValue`的值必須符合參數的類型。 例如，不允許下列情況：

```fsharp
type C =
    static member Wrong([<Optional; DefaultParameterValue("string")>] i:int) = ()
```

在此情況下，編譯器會產生警告，並同時忽略這兩個屬性。 請注意，預設值`null`必須以類型標注，否則編譯器會推斷錯誤的類型， `[<Optional; DefaultParameterValue(null:obj)>] o:obj`亦即。

## <a name="passing-by-reference"></a>以傳址方式傳遞

以傳F#址方式傳遞值牽涉到[byref](byrefs.md)，也就是 managed 指標類型。 要使用何種類型的指導方針如下：

- 如果`inref<'T>`您只需要讀取指標，請使用。
- 如果`outref<'T>`您只需要寫入指標，請使用。
- 如果`byref<'T>`您需要讀取和寫入指標，請使用。

```fsharp
let example1 (x: inref<int>) = printfn "It's %d" x

let example2 (x: outref<int>) = x <- x + 1

let example3 (x: byref<int>) =
    printfn "It'd %d" x
    x <- x + 1

// No need to make it mutable, since it's read-only
let x = 1
example1 &x

// Needs to be mutable, since we write to it
let mutable y = 2
example2 &y
example3 &y // Now 'y' is 3
```

由於參數是指標，而值是可變動的，因此在函式執行之後，對值所做的任何變更都會保留。

您可以使用元組做為傳回值，以將`out`任何參數儲存在 .net 程式庫方法中。 或者，您可以將`out`參數`byref`視為參數。 下列程式碼範例說明這兩種方式。

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a>參數陣列

有時候，您必須定義一個函式，以接受異類類型的任意數目參數。 建立所有可能的多載方法，以考慮所有可使用的類型，並不可行。 .NET 部署透過參數陣列功能提供這類方法的支援。 在其簽章中採用參數陣列的方法，可以使用任意數目的參數來提供。 參數會放入陣列中。 陣列元素的類型會決定可以傳遞至函數的參數類型。 如果您將參數陣列`System.Object`定義為做為元素類型，則用戶端程式代碼可以傳遞任何類型的值。

在F#中，只能在方法中定義參數陣列。 它們不能用於獨立函數或模組中定義的函式。

您可以使用`ParamArray`屬性來定義參數陣列。 `ParamArray`屬性只能套用至最後一個參數。

下列程式碼說明如何呼叫採用參數陣列的 .NET 方法，以及中F#具有接受參數陣列之方法的類型定義。

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

在專案中執行時，上述程式碼的輸出如下所示：

```console
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a>另請參閱

- [成員](./members/index.md)
