---
title: 參數和引數
description: '深入瞭解 F # 語言支援以定義參數，以及將引數傳遞至函式、方法和屬性。'
ms.date: 08/15/2020
ms.openlocfilehash: 6564fd31105427683af8fc6280672e638737e9b5
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811518"
---
# <a name="parameters-and-arguments"></a>參數和引數

本主題說明定義參數以及將引數傳遞至函式、方法和屬性的語言支援。 其中包含如何以傳址方式傳遞的資訊，以及如何定義和使用可採用可變動數目之引數的方法。

## <a name="parameters-and-arguments"></a>參數和引數

詞彙 *參數* 是用來描述預期要提供之值的名稱。 詞彙 *引數* 用於每個參數所提供的值。

您可以在元組或局部合併形式中指定參數，或以兩者的某種組合來指定參數。 您可以使用明確的參數名稱傳遞引數。 方法的參數可以指定為選擇性，並指定預設值。

## <a name="parameter-patterns"></a>參數模式

提供給函式和方法的參數通常是以空格分隔的模式。 這表示，在主體中，比對 [運算式](match-expressions.md) 中所述的任何模式都可以用於函數或成員的參數清單中。

方法通常會使用傳遞引數的元組形式。 因為元組格式符合在 .NET 方法中傳遞引數的方式，所以這可讓您從其他 .NET 語言的觀點來看得到更清楚的結果。

局部加表單最常用於使用系結所建立的函式 `let` 。

下列虛擬程式碼會顯示元組和引數的範例。

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

當某些引數位於元組中，而有些引數不是時，可能會合並形成。

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

其他模式也可以在參數清單中使用，但如果參數模式不符合所有可能的輸入，則執行時間可能會有不完整的相符項。 `MatchFailureException`當引數的值與參數清單中指定的模式不相符時，就會產生例外狀況。 當參數模式允許不完整的相符專案時，編譯器會發出警告。 至少有一個其他模式通常適用于參數清單，也就是萬用字元模式。 當您只想要忽略任何提供的引數時，請在參數清單中使用萬用字元模式。 下列程式碼說明如何在引數清單中使用萬用字元模式。

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

當您不想要使用通常以字串陣列形式提供的命令列引數時（如下列程式碼所示），當您不需要傳入的引數（例如在程式的主要進入點中）時，萬用字元模式會很有用。

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

有時在引數中使用的其他模式是 `as` 模式，以及與差異聯集和作用中模式相關聯的識別碼模式。 您可以使用單一案例的差異聯集模式，如下所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

輸出如下。

```console
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

使用中的模式可作為參數，例如，將引數轉換為所需的格式時，如下列範例所示：

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

您可以使用 `as` 模式來儲存相符的值作為區域值，如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

偶爾使用的另一個模式是一個函式，此函式會將最後一個引數保留為未命名的函式，該函式是在隱含引數上立即執行模式比對之 lambda 運算式的功能。 以下是這行程式碼的範例。

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

這段程式碼會定義一個函式，此函式會採用泛型清單，並 `true` 在清單空白時傳回，否則會傳回 `false` 。 使用這類技術可能使程式碼更難以閱讀。

有時候，牽涉到不完整相符專案的模式會很有用，例如，如果您知道程式中的清單只有三個元素，您可能會在參數清單中使用如下的模式。

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

使用具有不完整相符專案的模式最適合用於快速原型設計和其他暫存用途。 編譯器會發出這類程式碼的警告。 這類模式無法涵蓋所有可能輸入的一般案例，因此不適合元件 Api。

## <a name="named-arguments"></a>具名引數

方法的引數可以使用以逗號分隔的引數清單中的位置來指定，也可以藉由提供名稱，並在後面加上等號和要傳入的值，明確地傳遞給方法。 如果是藉由提供名稱所指定，則其顯示方式可能會與宣告中使用的順序不同。

具名引數可以讓程式碼更容易閱讀，而且可更適應 API 中特定類型的變更，例如重新排列方法參數的順序。

只有方法可以使用具名引數，而不是針對系結函 `let` 式、函數值或 lambda 運算式。

下列程式碼範例示範如何使用具名引數。

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

在呼叫類別的函式時，您可以使用類似具名引數的語法來設定類別的屬性值。 下列範例顯示此語法。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

如需詳細資訊，請參閱 [ (F # ) ](members/constructors.md)的函式。

## <a name="optional-parameters"></a>選擇性參數

您可以使用參數名稱前面的問號來指定方法的選擇性參數。 選擇性參數會被解釋為 F # 選項類型，因此您可以使用具有和的運算式，以定期查詢選項類型的方式來查詢它們 `match` `Some` `None` 。 只有成員可以使用選擇性參數，而不允許在使用系結所建立的函式上使用 `let` 。

您可以透過參數名稱將現有的選擇性值傳遞給方法，例如 `?arg=None` 或 `?arg=Some(3)` 或 `?arg=arg` 。 當您建立的方法會將選擇性引數傳遞給另一個方法時，這會很有用。

您也可以使用函 `defaultArg` 式，此函式會設定選擇性引數的預設值。 `defaultArg`函數會採用選擇性參數做為第一個引數，並使用預設值做為第二個引數。

下列範例說明選用參數的用法。

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

基於 c # 和 Visual Basic interop 的用途，您可以使用 `[<Optional; DefaultParameterValue<(...)>]` F # 中的屬性，讓呼叫端將引數視為選擇性。 這相當於在 c # 中將引數定義為選擇性，如中所示 `MyMethod(int i = 3)` 。

```fsharp
open System
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue("Hello world")>] message) =
        printfn "%s" message
```

您也可以將新的物件指定為預設參數值。 例如， `Foo` 成員可以改為使用選擇性的 `CancellationToken` 作為輸入：

```fsharp
open System.Threading
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue(CancellationToken())>] ct: CancellationToken) =
        printfn "%A" ct
```

提供做為引數的值 `DefaultParameterValue` 必須符合參數的類型。 例如，不允許下列動作：

```fsharp
type C =
    static member Wrong([<Optional; DefaultParameterValue("string")>] i:int) = ()
```

在這種情況下，編譯器會產生警告，而且會完全忽略這兩個屬性。 請注意，預設值 `null` 必須以類型標注，否則編譯器會推斷錯誤的型別，亦即 `[<Optional; DefaultParameterValue(null:obj)>] o:obj` 。

## <a name="passing-by-reference"></a>以傳址方式傳遞

以傳址方式傳遞 F # 值牽涉到 [byref](byrefs.md)，也就是 managed 指標類型。 應使用何種類型的指引如下：

- `inref<'T>`如果您只需要讀取指標，請使用。
- `outref<'T>`如果您只需要寫入指標，請使用。
- `byref<'T>`如果您需要讀取和寫入指標，請使用。

```fsharp
let example1 (x: inref<int>) = printfn "It's %d" x

let example2 (x: outref<int>) = x <- x + 1

let example3 (x: byref<int>) =
    printfn "It'd %d" x
    x <- x + 1

let test () =
    // No need to make it mutable, since it's read-only
    let x = 1
    example1 &x

    // Needs to be mutable, since we write to it
    let mutable y = 2
    example2 &y
    example3 &y // Now 'y' is 3
```

因為參數是指標，且值是可變動的，所以在執行函式之後，會保留值的任何變更。

您可以使用元組作為傳回值，以 `out` 在 .net 程式庫方法中儲存任何參數。 或者，您可以將 `out` 參數視為 `byref` 參數。 下列程式碼範例說明這兩種方式。

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a>參數陣列

有時候，您必須定義一個函式，該函式會接受任意數量的異類類型參數。 建立所有可能的多載方法，以考慮可使用的所有類型，並不是很實用的做法。 .NET 執行可透過參數陣列功能提供這類方法的支援。 在其簽章中接受參數陣列的方法可以提供任意數目的參數。 參數會放入陣列中。 陣列元素的類型會決定可以傳遞給函式的參數類型。 如果您使用 `System.Object` 做為元素類型來定義參數陣列，則用戶端程式代碼可以傳遞任何類型的值。

在 F # 中，只能在方法中定義參數陣列。 它們不能用在模組中定義的獨立函式或函數中。

您可以使用屬性定義參數陣列 `ParamArray` 。 `ParamArray`屬性只能套用至最後一個參數。

下列程式碼說明如何呼叫採用參數陣列的 .NET 方法，以及 F # 中具有接受參數陣列之方法的型別定義。

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
