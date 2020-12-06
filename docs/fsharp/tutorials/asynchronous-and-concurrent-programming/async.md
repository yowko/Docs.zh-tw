---
title: 非同步程式設計
description: '瞭解 F # 如何根據衍生自核心功能程式設計概念的語言層級程式設計模型，提供非同步全新支援。'
ms.date: 08/15/2020
ms.openlocfilehash: 04b397ddbfb468aa3bc4ee245175d3ec9bdedb50
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739323"
---
# <a name="async-programming-in-f"></a>F 中的非同步程式設計\#

非同步程式設計是基於各種原因而對新式應用程式來說很重要的一種機制。 大部分的開發人員會遇到兩個主要的使用案例：

- 呈現可提供大量並行連入要求的伺服器程式，同時將要求處理期間所佔用的系統資源降至最低，同時等待來自該進程外部系統或服務的輸入
- 維護回應迅速的 UI 或主執行緒，同時進行背景工作

雖然背景工作通常牽涉到多個執行緒的使用率，但請務必考慮非同步和多執行緒的概念。 事實上，這些都是分開的考慮，而不是另一種。 本文將更詳細地說明不同的概念。

## <a name="asynchrony-defined"></a>非同步已定義

上一個重點是，非同步與多個執行緒的使用無關，值得進一步說明。 有時候相關的概念有三個，但彼此之間完全無關：

- Concurrency在重迭的時間週期內執行多個計算時。
- 並行當多個計算或單一計算的數個部分在相同時間執行時。
- 非同步當一或多個計算可以與主要程式流程分開執行時。

這三個都是互相關聯的概念，但很容易混為一談，尤其是在一起使用時。 例如，您可能需要以平行方式執行多個非同步計算。 此關聯性並不表示平行處理原則或非同步暗示另一個。

如果您考慮「非同步」這個字的 etymology，則牽涉到兩個部分：

- "a"，表示「不」。
- 「同步」，表示「同時」。

當您將這兩個詞彙結合在一起時，您會看到「非同步」表示「不是同時」。 這樣就完成了！ 這項定義中沒有平行存取或平行處理原則的含意。 在實務上也是如此。

在實際的情況下，F # 中的非同步計算排程為獨立于主要程式流程的執行。 此獨立執行不表示並行或平行處理，也不表示計算一律會在背景中發生。 事實上，根據計算的本質和計算執行所在的環境而定，非同步計算甚至可以同步執行。

您應該具備的主要重點是，非同步計算與主要程式流程無關。 雖然非同步計算的執行時間或方式有一些保證，但是有一些方法可協調和排程。 本文的其餘部分會探索 F # 非同步核心概念，以及如何使用 F # 內建的類型、函式和運算式。

## <a name="core-concepts"></a>核心概念

在 F # 中，非同步程式設計是以三個核心概念為中心：

- `Async<'T>`型別，表示可組合的非同步計算。
- `Async`模組函數可讓您排程非同步工作、撰寫非同步計算，以及轉換非同步結果。
- `async { }`[計算運算式](../../language-reference/computation-expressions.md)，提供建立和控制非同步計算的便利語法。

您可以在下列範例中看到這三個概念：

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn $"File {fileName} has %d{bytes.Length} bytes"
    }

[<EntryPoint>]
let main argv =
    printTotalFileBytes "path-to-file.txt"
    |> Async.RunSynchronously

    Console.Read() |> ignore
    0
```

在此範例中， `printTotalFileBytes` 函數的型別為 `string -> Async<unit>` 。 呼叫函數並不會實際執行非同步計算。 相反地，它會傳回 `Async<unit>` ，作為要以非同步方式執行的工作 *規格* 。 它會 `Async.AwaitTask` 在其主體中呼叫，以將的結果轉換 <xref:System.IO.File.ReadAllBytesAsync%2A> 為適當的類型。

另一個重要的程式列是的呼叫 `Async.RunSynchronously` 。 如果您想要實際執行 F # 非同步計算，這是啟動函式的其中一個非同步模組，您必須呼叫這些函式。

這是 c #/Visual 基本程式設計風格的基本差異 `async` 。 在 F # 中，可以將非同步計算視為 **冷** 工作。 它們必須明確地啟動，才能實際執行。 這有一些優點，因為它可讓您比使用 c # 或 Visual Basic 更輕鬆地結合和排序非同步工作。

## <a name="combine-asynchronous-computations"></a>合併非同步計算

以下是透過合併計算來建立上一個範例的範例：

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn $"File {fileName} has %d{bytes.Length} bytes"
    }

[<EntryPoint>]
let main argv =
    argv
    |> Array.map printTotalFileBytes
    |> Async.Parallel
    |> Async.Ignore
    |> Async.RunSynchronously

    0
```

如您所見， `main` 函數有更多呼叫。 就概念而言，它會執行下列動作：

1. 使用將命令列引數轉換成 `Async<unit>` 計算 `Array.map` 。
2. 建立 `Async<'T[]>` ，以 `printTotalFileBytes` 在執行時平行排程和執行計算。
3. 建立 `Async<unit>` 會執行平行計算的，並忽略其結果。
4. 使用和封鎖來明確執行最後一個計算 `Async.RunSynchronously` ，直到完成為止。

當此程式執行時，會 `printTotalFileBytes` 針對每個命令列引數平行執行。 因為非同步計算獨立執行程式流程，所以沒有順序可讓它們列印其資訊並完成執行。 計算會以平行方式排程，但不保證其執行順序。

## <a name="sequence-asynchronous-computations"></a>順序非同步計算

由於 `Async<'T>` 是工作的規格，而不是已執行的工作，因此您可以輕鬆地執行更複雜的轉換。 以下範例會針對一組非同步計算進行順序，讓它們在另一個之後執行。

```fsharp
let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn $"File {fileName} has %d{bytes.Length} bytes"
    }

[<EntryPoint>]
let main argv =
    argv
    |> Array.map printTotalFileBytes
    |> Async.Sequential
    |> Async.Ignore
    |> Async.RunSynchronously
    |> ignore
```

這會排程依 `printTotalFileBytes` 元素循序執行， `argv` 而非以平行方式進行排程。 因為下一個專案將不會排定到最後一個計算完成執行，所以會排序計算，使其執行不會有任何重迭。

## <a name="important-async-module-functions"></a>重要的非同步模組函數

當您在 F # 中撰寫非同步程式碼時，通常會與處理計算排程的架構互動。 不過，這不一定都是如此，所以最好是學習各種啟動函式來排程非同步工作。

因為 F # 非同步計算是工作的 _規格_ ，而不是表示已在執行中的工作，所以必須使用啟動函式來明確地啟動它們。 有許多 [非同步啟動方法](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#section0) 在不同的內容中很有用。 下一節將說明一些較常見的啟動函式。

### <a name="asyncstartchild"></a>Async. Async.startchild

在非同步計算中啟動子計算。 這可讓您同時執行多個非同步計算。 子系計算會與父計算共用解除標記。 如果取消父代計算，子計算也會取消。

簽章：

```fsharp
computation: Async<'T> * timeout: ?int -> Async<Async<'T>>
```

使用時機：

- 當您想要同時執行多個非同步計算（而不是一次一個），但未以平行方式排程它們時。
- 當您想要將子計算的存留期與父計算的存留期系結時。

要注意的事項：

- 啟動多個計算和 `Async.StartChild` 平行排程不同。 如果您想要以平行方式排程計算，請使用 `Async.Parallel` 。
- 取消父計算將會觸發其啟動的所有子計算的取消。

### <a name="asyncstartimmediate"></a>Async. StartImmediate

執行非同步計算，並在目前的作業系統執行緒上立即開始。 如果您需要在計算期間更新呼叫執行緒上的某個內容，這會很有説明。 例如，如果非同步計算必須更新 UI (例如更新進度列) ，則 `Async.StartImmediate` 應該使用。

簽章：

```fsharp
computation: Async<unit> * cancellationToken: ?CancellationToken -> unit
```

使用時機：

- 當您需要在非同步計算的過程中，更新呼叫執行緒上的某些內容。

要注意的事項：

- 非同步計算中的程式碼將會在發生排程的任何執行緒上執行。 如果執行緒是以某種方式區分，例如 UI 執行緒，這可能會造成問題。 在這種情況下， `Async.StartImmediate` 可能不適合使用。

### <a name="asyncstartastask"></a>Async. Async.startastask

線上程集區中執行計算。 傳回 <xref:System.Threading.Tasks.Task%601> ，當計算終止 (產生結果、擲回例外狀況或取消) 時，會在對應的狀態下完成。 如果未提供取消權杖，則會使用預設解除標記。

簽章：

```fsharp
computation: Async<'T> * taskCreationOptions: ?TaskCreationOptions * cancellationToken: ?CancellationToken -> Task<'T>
```

使用時機：

- 當您需要呼叫的 .NET API 需要 <xref:System.Threading.Tasks.Task%601> 表示非同步計算的結果時。

要注意的事項：

- 此呼叫會配置額外的 `Task` 物件，如果經常使用，則會增加額外負荷。

### <a name="asyncparallel"></a>Async. Parallel

排定要平行執行的非同步計算順序。 藉由指定參數，可以選擇性地調整/節流處理平行處理原則的程度 `maxDegreesOfParallelism` 。

簽章：

```fsharp
computations: seq<Async<'T>> * ?maxDegreesOfParallelism: int -> Async<'T[]>
```

使用時機：

- 如果您需要同時執行一組計算，而不依賴它們的執行順序。
- 如果您不需要以平行方式排程的結果，直到它們全部完成為止。

要注意的事項：

- 一旦所有計算完成之後，您就只能存取產生的值陣列。
- 計算會在最後一次排程時執行。 此行為表示您無法依賴它們的執行順序。

### <a name="asyncsequential"></a>Async. 連續

排定以傳遞的循序執行非同步計算的順序。 第一個計算將會執行，然後再執行一次，依此類推。 不會以平行方式執行計算。

簽章：

```fsharp
computations: seq<Async<'T>> -> Async<'T[]>
```

使用時機：

- 如果您需要依序執行多個計算。

要注意的事項：

- 一旦所有計算完成之後，您就只能存取產生的值陣列。
- 計算將依傳遞給此函式的循序執行，這可能表示在傳回結果之前，會經歷更多時間。

### <a name="asyncawaittask"></a>Async. Async.awaittask

傳回非同步計算，等候指定的 <xref:System.Threading.Tasks.Task%601> 完成，並將其結果傳回為 `Async<'T>`

簽章：

```fsharp
task: Task<'T> -> Async<'T>
```

使用時機：

- 當您使用的 .NET API 會 <xref:System.Threading.Tasks.Task%601> 在 F # 非同步計算中傳回。

要注意的事項：

- 例外狀況會依照工作 <xref:System.AggregateException> 平行程式庫的慣例包裝，而這種行為與 F # async 通常會如何呈現例外狀況不同。

### <a name="asynccatch"></a>Async. Catch

建立異步計算，以執行指定的 `Async<'T>` ，傳回 `Async<Choice<'T, exn>>` 。 如果指定的 `Async<'T>` 成功完成，則 `Choice1Of2` 會傳回具有結果值的。 如果例外狀況在完成之前擲回，則 `Choice2of2` 會傳回，並產生例外狀況。 如果它是在由許多計算所組成的非同步計算上使用，且其中一個計算擲回例外狀況，則會完全停止包含的計算。

簽章：

```fsharp
computation: Async<'T> -> Async<Choice<'T, exn>>
```

使用時機：

- 當您執行的非同步工作可能因例外狀況而失敗，而您想要在呼叫端中處理該例外狀況時。

要注意的事項：

- 當使用結合或排序的非同步計算時，如果其中一個「內部」計算擲回例外狀況，則會完全停止包含的計算。

### <a name="asyncignore"></a>Async. Ignore

建立會執行指定計算並忽略其結果的非同步計算。

簽章：

```fsharp
computation: Async<'T> -> Async<unit>
```

使用時機：

- 當您有不需要結果的非同步計算時。 這類似于 `ignore` 非非同步程式碼的程式碼。

要注意的事項：

- 如果您必須使用 `Async.Ignore` ，因為您想要使用 `Async.Start` 或其他需要的函式 `Async<unit>` ，請考慮是否要捨棄結果。 避免只為了符合型別簽章而捨棄結果。

### <a name="asyncrunsynchronously"></a>Async. Async.runsynchronously

執行非同步計算，並等候其在呼叫執行緒上的結果。 此呼叫正在封鎖中。

簽章：

```fsharp
computation: Async<'T> * timeout: ?int * cancellationToken: ?CancellationToken -> 'T
```

使用時機：

- 如果需要，請在應用程式中只使用一次（在可執行檔的進入點）。
- 當您不在意效能，並且想要一次執行一組其他非同步作業時。

要注意的事項：

- 呼叫會 `Async.RunSynchronously` 封鎖呼叫的執行緒，直到執行完成為止。

### <a name="asyncstart"></a>Async. 開始

在傳回的執行緒集區中啟動非同步計算 `unit` 。 不會等待其結果。 以啟動的嵌套計算 `Async.Start` 會與呼叫它們的父代計算分開啟動。 其存留期未系結至任何父代計算。 如果取消父代計算，則不會取消任何子計算。

簽章：

```fsharp
computation: Async<unit> * cancellationToken: ?CancellationToken -> unit
```

僅用於：

- 您有不產生結果及/或需要處理一項的非同步計算。
- 非同步計算完成時，您不需要知道。
- 您不在意非同步計算執行所在的執行緒。
- 您不需要留意或報告工作所產生的例外狀況。

要注意的事項：

- 從開始計算所引發的例外狀況 `Async.Start` 不會傳播至呼叫端。 呼叫堆疊將會完全展開。
- 任何工作 (例如 `printfn`) 啟動的呼叫都 `Async.Start` 不會導致程式執行的主要執行緒發生效果。

## <a name="interoperate-with-net"></a>與 .NET 交互操作

您可以使用 .NET 程式庫或使用 [async/await](../../../standard/async.md)樣式非同步程式設計的 c # 程式碼基底。 因為 c # 和大部分的 .NET 程式庫都使用 <xref:System.Threading.Tasks.Task%601> 和 <xref:System.Threading.Tasks.Task> 類型作為其核心抽象概念，而不是 `Async<'T>` ，所以您必須在這兩種方法之間的界限之間進行非同步。

### <a name="how-to-work-with-net-async-and-taskt"></a>如何使用 .NET async 和 `Task<T>`

使用使用 (的 .NET 非同步程式庫和程式碼基底 <xref:System.Threading.Tasks.Task%601> ，) 具有傳回值的非同步計算相當簡單，而且具備 F # 的內建支援。

您可以使用 `Async.AwaitTask` 函數來等候 .net 非同步計算：

```fsharp
let getValueFromLibrary param =
    async {
        let! value = DotNetLibrary.GetValueAsync param |> Async.AwaitTask
        return value
    }
```

您可以使用 `Async.StartAsTask` 函數，將非同步計算行程給 .net 呼叫端：

```fsharp
let computationForCaller param =
    async {
        let! result = getAsyncResult param
        return result
    } |> Async.StartAsTask
```

### <a name="how-to-work-with-net-async-and-task"></a>如何使用 .NET async 和 `Task`

若要使用的 Api 使用 <xref:System.Threading.Tasks.Task> (也就是不會傳回值) 的 .net 非同步計算，您可能需要加入其他函式，以將轉換成 `Async<'T>` <xref:System.Threading.Tasks.Task> ：

```fsharp
module Async =
    // Async<unit> -> Task
    let startTaskFromAsyncUnit (comp: Async<unit>) =
        Async.StartAsTask comp :> Task
```

已經有 `Async.AwaitTask` 接受 <xref:System.Threading.Tasks.Task> as 輸入的。 使用這個與先前定義的函 `startTaskFromAsyncUnit` 式，您可以 <xref:System.Threading.Tasks.Task> 從 F # 非同步計算啟動和等候類型。

## <a name="relationship-to-multi-threading"></a>多執行緒的關聯性

雖然這篇文章中提到執行緒，但是有兩個重要事項要記住：

1. 非同步計算和執行緒之間沒有任何關聯性，除非在目前的執行緒上明確啟動。
1. F # 中的非同步程式設計不是多重執行緒的抽象概念。

例如，根據工作的本質而定，計算實際上可能會在其呼叫端的執行緒上執行。 計算也可以線上程之間「跳躍」，以在一小段時間內進行處理，以在「等候」 (期間（例如，當網路通話處於傳輸) 時執行有用的工作）。

雖然 F # 提供了一些功能，可讓您在目前的執行緒上啟動非同步計算 (或明確地不) 目前的執行緒上，非同步通常不會與特定的執行緒策略相關聯。

## <a name="see-also"></a>另請參閱

- [F # 非同步程式設計模型](https://www.microsoft.com/research/publication/the-f-asynchronous-programming-model)
- [Jet .com 的 F # 非同步指南](https://medium.com/jettech/f-async-guide-eb3c8a2d180a)
- [適用于有趣和收益之非同步程式設計指南的 F #](https://fsharpforfunandprofit.com/posts/concurrency-async-and-parallel/)
- [C # 中的非同步和 F #： C 中的非同步陷阱#](http://tomasp.net/blog/csharp-async-gotchas.aspx/)
