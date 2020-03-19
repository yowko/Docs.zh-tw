---
title: 參數和引數
description: 瞭解 F# 語言對定義參數和將參數傳遞給函數、方法和屬性的支援。
ms.date: 12/04/2019
ms.openlocfilehash: b234ef939128e7cf09d35f9580d4d5010d7dc639
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400194"
---
# <a name="parameters-and-arguments"></a>參數和引數

本主題介紹定義參數和將參數傳遞給函數、方法和屬性的語言支援。 它包括有關如何通過引用傳遞的資訊，以及如何定義和使用可以採用可變參數數的方法。

## <a name="parameters-and-arguments"></a>參數和引數

術語*參數*用於描述預期提供的值的名稱。 術語*參數*用於為每個參數提供的值。

參數可以以元組或咖喱形式指定，也可以以兩者的某些組合指定。 可以使用顯式參數名稱傳遞參數。 方法的參數可以指定為可選，並給出預設值。

## <a name="parameter-patterns"></a>參數模式

提供給函數和方法的參數一般是由空格分隔的模式。 這意味著，原則上，[匹配運算式](match-expressions.md)中描述的任何模式都可以在函數或成員的參數清單中使用。

方法通常使用傳遞參數的元組形式。 從其他 .NET 語言的角度來看，這可實現更清晰的結果，因為元組形式與在 .NET 方法中傳遞參數的方式匹配。

咖喱表單最常用於使用`let`綁定創建的函數。

下面的偽代碼顯示了元組和咖喱參數的示例。

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

當某些參數位於組合中，而有些參數不是時，可以組合形式。

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

其他模式也可以在參數清單中使用，但如果參數模式與所有可能的輸入不匹配，則運行時可能存在不完全符合。 當參數`MatchFailureException`的值與參數清單中指定的模式不匹配時，將生成異常。 當參數模式允許不完全符合時，編譯器發出警告。 至少有一個其他模式通常可用於參數清單，即萬用字元模式。 當您只想忽略提供的任何參數時，在參數清單中使用萬用字元模式。 以下代碼說明了萬用字元模式在參數清單中的使用。

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

當您不需要傳入的參數（如程式的主進入點）時，當您對通常作為字串陣列提供的命令列參數不感興趣時，萬用字元模式非常有用，如以下代碼。

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

參數中有時使用的其他模式是與受歧視的聯合`as`和活動模式關聯的模式和識別碼模式。 可以使用單例區分聯合模式，如下所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

輸出如下。

```console
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

活動模式可用作參數，例如，將參數轉換為所需格式時，如以下示例所示：

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

可以使用`as`模式將匹配值存儲為本地值，如下程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

偶爾使用的另一種模式是一個函數，該函數通過提供 lambda 運算式（作為函數的正文）來保留最後一個參數未命名，該運算式將立即對隱式參數執行模式匹配。 例如以下程式碼。

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

此代碼定義一個函數，該函數獲取泛型清單`true`，並在清單為空時返回`false`，否則返回。 使用此類技術會使代碼更難閱讀。

有時，涉及不完全符合的模式很有用，例如，如果您知道程式中的清單只有三個元素，則可以在參數清單中使用如下所示的模式。

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

使用匹配不完全的模式最好保留用於快速原型設計和其他臨時用途。 編譯器將針對此類代碼發出警告。 此類模式不能涵蓋所有可能輸入的一般情況，因此不適合元件 API。

## <a name="named-arguments"></a>具名引數

方法的參數可以按逗號分隔參數清單中的位置指定，也可以通過提供名稱（後跟等符號和要傳入的值）顯式傳遞給方法。 如果通過提供名稱指定，它們可以按與聲明中使用的順序不同的顯示順序顯示。

具名引數可以使代碼更具可讀性，並更適應 API 中的某些類型的更改，例如方法參數的重新排序。

具名引數僅允許用於方法，不適用於`let`綁定函數、函數值或 lambda 運算式。

以下代碼示例演示了具名引數的使用。

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

在調用類建構函式時，可以使用類似于具名引數的語法來設置類的屬性值。 下面的示例顯示了此語法。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

有關詳細資訊，請參閱[建構函式 （F#）。](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05)

## <a name="optional-parameters"></a>選擇性參數

可以使用參數名稱前面的問號為方法指定可選參數。 可選參數被解釋為 F# 選項類型，因此可以使用 的`match``Some`運算式 和 ，以查詢選項類型的常規方式查詢它們。 `None` 可選參數僅允許在成員上，不允許使用`let`綁定創建的函數。

可以按參數名稱將現有可選值傳遞給方法，例如`?arg=None`或`?arg=Some(3)``?arg=arg`。 這在構建將可選參數傳遞給另一種方法的方法時非常有用。

您還可以使用 函數`defaultArg`，它設置可選參數的預設值。 函數`defaultArg`將可選參數作為第一個參數，將預設值作為第二個參數。

下面的示例說明了可選參數的使用。

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

出於 C# 和 Visual Basic 交互操作的目的，可以使用`[<Optional; DefaultParameterValue<(...)>]`F# 中的屬性，以便調用方將參數視為可選參數。 這相當於在 C# 中將參數定義為可選參數，如`MyMethod(int i = 3)`在 中。

```fsharp
open System
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue("Hello world")>] message) =
        printfn "%s" message
```

還可以指定新物件作為預設參數值。 例如，`Foo`成員可以改為具有可選`CancellationToken`作為輸入：

```fsharp
open System.Threading
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue(CancellationToken())>] ct: CancellationToken) =
        printfn "%A" ct
```

作為參數給出的值`DefaultParameterValue`必須與參數的類型匹配。 例如，不允許使用以下內容：

```fsharp
type C =
    static member Wrong([<Optional; DefaultParameterValue("string")>] i:int) = ()
```

在這種情況下，編譯器將生成警告，並將完全忽略這兩個屬性。 請注意，需要對預設值`null`進行類型注釋，否則編譯器將推斷錯誤的類型，即`[<Optional; DefaultParameterValue(null:obj)>] o:obj`。

## <a name="passing-by-reference"></a>通過引用傳遞

通過引用傳遞 F# 值涉及[byrefs，](byrefs.md)它們是託管指標類型。 使用哪種類型的指南如下所示：

- 如果`inref<'T>`只需要讀取指標，請使用。
- 如果`outref<'T>`只需要寫入指標，請使用。
- 如果需要`byref<'T>`同時讀取指標並寫入指標，請使用。

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

由於參數是指標，並且值是可變的，因此在執行函數後將保留對值的任何更改。

可以使用元組作為傳回值，在 .NET 庫`out`方法中存儲任何參數。 或者，您可以將參數`out`視為參數。 `byref` 以下代碼示例說明了這兩種方法。

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a>參數陣列

有時，需要定義一個函數，該函數採用異構類型的任意數量的參數。 創建所有可能的重載方法以考慮可以使用的所有類型是不現實的。 .NET 實現通過參數陣列功能為這些方法提供支援。 在其簽名中採用參數陣列的方法可以提供任意數量的參數。 參數被放入陣列中。 陣列元素的類型確定可傳遞給函數的參數類型。 如果將參數陣列`System.Object`定義為元素類型，則用戶端代碼可以傳遞任何類型的值。

在 F# 中，只能在方法中定義參數陣列。 它們不能用於在模組中定義的獨立函數或函數中。

通過使用`ParamArray`屬性定義參數陣列。 該`ParamArray`屬性只能應用於最後一個參數。

以下代碼說明了調用採用參數陣列的 .NET 方法，以及 F# 中具有採用參數陣列的方法的類型的定義。

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

在專案中運行時，前一個代碼的輸出如下所示：

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
