---
title: 非同步程式設計
description: 瞭解如何F#根據衍生自核心函式程式設計概念的語言層級程式設計模型，提供非同步全新支援。
ms.date: 12/17/2018
ms.openlocfilehash: 7021d7936d10f9ea6fceb4aa56db3285d21624ad
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628848"
---
# <a name="async-programming-in-f"></a>F\# 中的非同步程式設計

非同步程式設計是基於各種原因而對現代化應用程式而言不可或缺的一種機制。 大部分的開發人員都會遇到兩個主要的使用案例：

- 呈現可提供大量並行連入要求的伺服器進程，同時將所佔用的系統資源降至最低，同時要求處理會等候該進程外部系統或服務的輸入
- 在同時進行的背景工作時，維護回應式 UI 或主執行緒

雖然背景工作通常會牽涉到多個執行緒的使用率，但請務必考慮非同步和多執行緒的概念。 事實上，它們是不同的考慮，而其中一個則不代表另一個。 本文所述的內容將會更詳細地說明。

## <a name="asynchrony-defined"></a>非同步已定義

先前的重點是，非同步與多個執行緒的使用率無關，值得進一步說明。 有時候會有三個相關的概念，但完全獨立于另一個：

- 能力當多個計算在重迭的時間週期內執行時。
- 平行處理原則當單一計算的多個計算或數個部分在完全相同的時間執行時。
- 非同步當一或多個計算可與主要程式流程分開執行時。

這三種概念都是相互關聯的概念，但很容易混為一談，特別是當它們一起使用時。 例如，您可能需要以平行方式執行多個非同步計算。 這並不表示平行處理原則或非同步彼此隱含。

如果您考慮「非同步」一詞的 etymology，就會牽涉到兩個部分：

- "a"，表示 "not"。
- 「同步」，表示「同時」。

當您將這兩個詞彙放在一起時，您會看到「非同步」表示「不是同一時間」。 就這麼簡單！ 在此定義中，不會隱含並行或平行處理。 這在實務上也是如此。

實際上，中F#的非同步計算會排定為獨立執行主要程式流程。 這並不代表並行或平行處理，也不表示一定會在背景中進行計算。 事實上，非同步計算甚至可以同步執行，視計算的本質和計算執行所在的環境而定。

主要的重點是，非同步計算與主要程式流程無關。 雖然非同步計算的執行時間或方式有一些保證，但還是有一些方法可以協調和排程它們。 本文的其餘部分將探討F#非同步核心概念，以及如何使用內建的類型、函式和運算式F#。

## <a name="core-concepts"></a>核心概念

在F#中，非同步程式設計是以三個核心概念為中心：

- `Async<'T>` 類型，代表可組合的非同步計算。
- `Async` 模組函數，可讓您排程非同步工作、撰寫非同步計算，以及轉換非同步結果。
- `async { }`[計算運算式](../../language-reference/computation-expressions.md)，提供建立和控制非同步計算的便利語法。

您可以在下列範例中看到這三個概念：

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    printTotalFileBytes "path-to-file.txt"
    |> Async.RunSynchronously

    Console.Read() |> ignore
    0
```

在此範例中，`printTotalFileBytes` 函數的類型 `string -> Async<unit>`。 呼叫函數並不會實際執行非同步計算。 相反地，它會傳回 `Async<unit>`，作為要以非同步方式執行之工作的*規格*。 它會呼叫其主體中的 `Async.AwaitTask`，將 <xref:System.IO.File.ReadAllBytesAsync%2A> 的結果轉換成適當的類型。

另一個重要的程式程式碼是 `Async.RunSynchronously`的呼叫。 這是非同步模組的其中一個啟動函式，如果您想要實際執行非同步計算，就必須F#呼叫這個函式。

這是 `async` 程式設計的C#/Visual 基本樣式的基本差異。 在F#中，可以將非同步計算視為**冷**工作。 必須明確啟動才能實際執行。 這有一些優點，因為它可讓您比在或 Visual Basic 中C#更輕鬆地結合和排序非同步工作。

## <a name="combine-asynchronous-computations"></a>結合非同步計算

以下是藉由結合計算，以先前的版本為基礎的範例：

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
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

如您所見，`main` 函式已進行更多呼叫。 在概念上，它會執行下列動作：

1. 使用 `Array.map`，將命令列引數轉換成 `Async<unit>` 計算。
2. 建立 `Async<'T[]>`，以在執行時以平行方式排程和執行 `printTotalFileBytes` 計算。
3. 建立將會執行平行計算並忽略其結果的 `Async<unit>`。
4. 使用 `Async.RunSynchronously` 和 block 明確執行最後的計算，直到完成為止。

當此程式執行時，`printTotalFileBytes` 會針對每個命令列引數以平行方式執行。 因為非同步計算獨立執行程式流程，所以不會列印其資訊並完成執行。 計算會以平行方式排程，但不保證其執行順序。

## <a name="sequence-asynchronous-computations"></a>順序非同步計算

由於 `Async<'T>` 是工作的規格，而不是已執行的工作，因此您可以輕鬆地執行更複雜的轉換。 以下範例會排序一組非同步計算，讓它們逐一執行。

```fsharp
let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
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

這會依照 `argv` 元素的順序來排程 `printTotalFileBytes` 執行，而不是以平行方式進行排程。 因為下一個專案在最後一個計算完成執行後才會排程，所以計算會進行排序，使其執行不會有任何重迭。

## <a name="important-async-module-functions"></a>重要的非同步模組函式

當您在中F#撰寫非同步程式碼時，通常會與處理計算排程的架構互動。 不過，這不一定會發生，因此最好學習各種啟動函數來排程非同步工作。

因為F#非同步計算是工作的_規格_，而不是已在執行中的工作表示法，所以必須以起始函式明確啟動。 有許多[非同步啟動函數](https://msdn.microsoft.com/library/ee370232.aspx)在不同的內容中很有説明。 下一節將說明一些較常見的啟動函數。

### <a name="asyncstartchild"></a>Async.startchild

在非同步計算中啟動子計算。 這可讓多個非同步計算同時執行。 子計算會與父計算共用解除標記。 如果父計算已取消，子計算也會一併取消。

簽章

```fsharp
computation: Async<'T> - timeout: ?int -> Async<Async<'T>>
```

使用時機：

- 當您想要同時執行多個非同步計算，而不是一次，但未以平行方式排程它們時。
- 當您想要將子計算的存留期系結至父計算的存留期間。

要注意的事項：

- 使用 `Async.StartChild` 啟動多個計算，與以平行方式進行排程並不相同。 如果您想要平行排程計算，請使用 `Async.Parallel`。
- 取消父計算會觸發其啟動之所有子計算的取消作業。

### <a name="asyncstartimmediate"></a>StartImmediate

執行非同步計算，並在目前的作業系統執行緒上立即啟動。 如果您需要在計算期間更新呼叫執行緒上的某個專案，這會很有説明。 例如，如果非同步計算必須更新 UI （例如更新進度列），則應該使用 `Async.StartImmediate`。

簽章

```fsharp
computation: Async<unit> - cancellationToken: ?CancellationToken -> unit
```

使用時機：

- 當您需要在非同步計算過程中更新呼叫執行緒上的某些專案時。

要注意的事項：

- 非同步計算中的程式碼會在任何一個要排程的執行緒上執行。 如果該執行緒以某種方式區分，例如 UI 執行緒，這可能會造成問題。 在這種情況下，`Async.StartImmediate` 可能不適合使用。

### <a name="asyncstartastask"></a>Async.startastask

執行執行緒集區中的計算。 傳回在計算終止（產生結果、擲回例外狀況或取消）時，將在對應狀態下完成的 <xref:System.Threading.Tasks.Task%601>。 如果未提供解除標記，則會使用預設的解除標記。

簽章

```fsharp
computation: Async<'T> - taskCreationOptions: ?TaskCreationOptions - cancellationToken: ?CancellationToken -> Task<'T>
```

使用時機：

- 當您需要呼叫 .NET API，而該應用程式預期會有 <xref:System.Threading.Tasks.Task%601> 來表示非同步計算的結果時。

要注意的事項：

- 此呼叫會配置額外的 `Task` 物件，如果經常使用，則會增加額外負荷。

### <a name="asyncparallel"></a>Async。 Parallel

排定要平行執行的一系列非同步計算。 藉由指定 `maxDegreesOfParallelism` 參數，可以選擇性地調整/節流處理平行處理原則的程度。

簽章

```fsharp
computations: seq<Async<'T>> - ?maxDegreesOfParallelism: int -> Async<'T[]>
```

使用時機：

- 如果您需要同時執行一組計算，而且不依賴其執行順序。
- 如果您不需要以平行方式排程的結果，直到全部完成為止。

要注意的事項：

- 一旦所有計算完成之後，您就只能存取產生的值陣列。
- 計算將會執行，但最終會進行排程。 這表示您無法依賴其執行順序。

### <a name="asyncsequential"></a>非同步。連續

排程要依行程順序執行的一系列非同步計算。 第一次計算將會執行，接下來是下一個，依此類推。 不會平行執行計算。

簽章

```fsharp
computations: seq<Async<'T>> -> Async<'T[]>
```

使用時機：

- 如果您需要依序執行多個計算。

要注意的事項：

- 一旦所有計算完成之後，您就只能存取產生的值陣列。
- 計算會依照傳遞至此函式的循序執行，這可能表示傳回結果之前會經過較多的時間。

### <a name="asyncawaittask"></a>Async.awaittask

傳回非同步計算，等候指定的 <xref:System.Threading.Tasks.Task%601> 完成，並將其結果傳回為 `Async<'T>`

簽章

```fsharp
task: Task<'T>  -> Async<'T>
```

使用時機：

- 當您使用的 .NET API 會在F#非同步計算中傳回 <xref:System.Threading.Tasks.Task%601>。

要注意的事項：

- 例外狀況會依照工作平行程式庫的慣例包裝在 <xref:System.AggregateException> 中，這與非同步一般呈現F#例外狀況的方式不同。

### <a name="asynccatch"></a>Async Catch

建立異步計算，以執行指定的 `Async<'T>`，並傳回 `Async<Choice<'T, exn>>`。 如果指定的 `Async<'T>` 成功完成，則會傳回包含結果值的 `Choice1Of2`。 如果在完成之前擲回例外狀況，則會傳回具有引發例外狀況的 `Choice2of2`。 如果它用於本身由許多計算組成的非同步計算，而其中一個計算擲回例外狀況，則會完全停止內含的計算。

簽章

```fsharp
computation: Async<'T> -> Async<Choice<'T, exn>>
```

使用時機：

- 當您執行可能因例外狀況而失敗的非同步工作，而且您想要在呼叫端處理該例外狀況。

要注意的事項：

- 當使用結合或排序的非同步計算時，如果其中一個「內部」計算擲回例外狀況，則包含的計算將會完全停止。

### <a name="asyncignore"></a>Async。忽略

建立異步計算來執行指定的計算，並忽略其結果。

簽章

```fsharp
computation: Async<'T> -> Async<unit>
```

使用時機：

- 當您有不需要其結果的非同步計算時。 這類似于非非同步程式碼的 `ignore` 程式碼。

要注意的事項：

- 如果您因為想要使用 `Async.Start` 或其他需要 `Async<unit>`的函式而必須使用此功能，請考慮捨棄結果是否可以執行。 通常不應該只是為了符合類型簽章而捨棄結果。

### <a name="asyncrunsynchronously"></a>Async.runsynchronously

執行非同步計算，並在呼叫執行緒上等候其結果。 此呼叫正在封鎖。

簽章

```fsharp
computation: Async<'T> - timeout: ?int - cancellationToken: ?CancellationToken -> 'T
```

使用時機：

- 如果您需要，請在應用程式中使用它（在可執行檔的進入點上）。
- 當您不在意效能，而且想要一次執行一組其他非同步作業時。

要注意的事項：

- 呼叫 `Async.RunSynchronously` 會封鎖呼叫執行緒，直到執行完成為止。

### <a name="asyncstart"></a>Async. Start

線上程集區中啟動會傳回 `unit`的非同步計算。 不等候其結果。 以 `Async.Start` 開始的嵌套計算會與呼叫它們的父系計算完全獨立地啟動。 其存留期不會系結至任何父系計算。 如果父代計算已取消，則不會取消任何子計算。

簽章

```fsharp
computation: Async<unit> - cancellationToken: ?CancellationToken -> unit
```

只在下列情況使用：

- 您的非同步計算不會產生結果，也不需要處理一次。
- 您不需要知道非同步計算何時完成。
- 您不在意非同步計算執行所在的執行緒。
- 您不需要留意或報告工作所產生的例外狀況。

要注意的事項：

- 以 `Async.Start` 開頭的計算所引發的例外狀況不會傳播至呼叫者。 將完全展開呼叫堆疊。
- `Async.Start` 啟動的任何 effectful 工作（例如呼叫 `printfn`）都不會造成此效果在程式執行的主要執行緒上發生。

## <a name="interoperate-with-net"></a>與 .NET 交互操作

您可能使用的 .NET 程式庫或C#程式碼基底，會使用非同步[/await](../../../standard/async.md)樣式的非同步程式設計。 因為C#大部分的 .net 程式庫會使用 <xref:System.Threading.Tasks.Task%601> 和 <xref:System.Threading.Tasks.Task> 類型做為其核心抽象概念，而不是 `Async<'T>`，所以您必須在這兩種方法之間，將界限交叉到非同步。

### <a name="how-to-work-with-net-async-and-taskt"></a>如何使用 .NET async 和 `Task<T>`

使用 <xref:System.Threading.Tasks.Task%601> 的 .NET async 程式庫和程式碼基底（也就是具有傳回值的非同步計算）很簡單，而且具有內建F#的支援。

您可以使用 `Async.AwaitTask` 函數來等待 .NET 非同步計算：

```fsharp
let getValueFromLibrary param =
    async {
        let! value = DotNetLibrary.GetValueAsync param |> Async.AwaitTask
        return value
    }
```

您可以使用 `Async.StartAsTask` 函式，將非同步計算行程給 .NET 呼叫者：

```fsharp
let computationForCaller param =
    async {
        let! result = getAsyncResult param
        return result
    } |> Async.StartAsTask
```

### <a name="how-to-work-with-net-async-and-task"></a>如何使用 .NET async 和 `Task`

若要使用 <xref:System.Threading.Tasks.Task> 的 Api （也就是不會傳回值的 .NET 非同步計算），您可能需要新增額外的函式，以將 `Async<'T>` 轉換為 <xref:System.Threading.Tasks.Task>：

```fsharp
module Async =
    // Async<unit> -> Task
    let startTaskFromAsyncUnit (comp: Async<unit>) =
        Async.StartAsTask comp :> Task
```

已經有可接受 <xref:System.Threading.Tasks.Task> 做為輸入的 `Async.AwaitTask`。 使用此和先前定義的 `startTaskFromAsyncUnit` 函式F# ，您可以從非同步計算啟動和等待 <xref:System.Threading.Tasks.Task> 類型。

## <a name="relationship-to-multi-threading"></a>多執行緒的關聯性

雖然這篇文章中提到了執行緒，但有兩個重要的事項要記住：

1. 除非在目前線程上明確啟動，否則非同步計算和執行緒之間沒有相似性。
1. 中F#的非同步程式設計不是多執行緒的抽象概念。

例如，計算實際上可能會在其呼叫端的執行緒上執行，視工作的本質而定。 計算也可以線上程之間「跳躍」，以一小段時間來進行，以在「等候」期間執行有用的工作（例如當網路呼叫正在傳輸時）。

雖然F#提供在目前線程上啟動非同步計算的一些功能（或明確地不在目前線程上），但非同步通常不會與特定的執行緒策略相關聯。

## <a name="see-also"></a>另請參閱

- [F#非同步程式設計模型](https://www.microsoft.com/research/publication/the-f-asynchronous-programming-model)
- [Jet .com 的F#非同步指南](https://medium.com/jettech/f-async-guide-eb3c8a2d180a)
- [F#針對有趣和利潤的非同步程式設計指南](https://fsharpforfunandprofit.com/posts/concurrency-async-and-parallel/)
- [和F#中C#的非同步：中的非同步陷阱C#](http://tomasp.net/blog/csharp-async-gotchas.aspx/)
