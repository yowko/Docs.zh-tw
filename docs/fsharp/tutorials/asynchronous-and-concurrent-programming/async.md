---
title: 非同步編程
description: 瞭解 F# 如何基於從核心函數程式設計概念派生的語言級程式設計模型為非同步提供乾淨的支援。
ms.date: 12/17/2018
ms.openlocfilehash: 9b2e3057c126d84474c21fde653da5bbee32938a
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2020
ms.locfileid: "81608032"
---
# <a name="async-programming-in-f"></a>F 中的非同步編程\#

非同步程式設計是一種機制,對於現代應用程式來說,由於各種原因至關重要。 大多數開發人員會遇到兩個主要用例:

- 顯示一個伺服器程序,該伺服器程序可以服務大量併發傳入請求,同時最小化請求處理時佔用的系統資源,等待來自該行程外部的系統或服務的輸入
- 維護回應靈敏的 UI 或主線程,同時推進後台工作

儘管後台工作通常涉及多個線程的利用,但單獨考慮非同步和多線程的概念非常重要。 事實上,它們是單獨的問題,一個並不意味著另一個。 本文中介紹的內容將更詳細地介紹這一點。

## <a name="asynchrony-defined"></a>定義非同步

前一點 -非同步與多個線程的利用率無關 - 值得進一步解釋一下。 有三個概念有時相關,但嚴格地相互獨立:

- 併發性;在重疊的時間段中執行多個計算時。
- 並行性;當多個計算或單個計算的幾個部分完全同時運行時。
- 異步;當一個或多個計算可以獨立於主程式流執行時。

這三個概念都是正交概念,但很容易組合,尤其是當它們一起使用時。 例如,您可能需要並行執行多個非同步計算。 這並不意味著並行性或異步性相互暗示。

如果考慮「非同步」一詞的詞源,則涉及兩個部分:

- "a",意思是"不"。
- "同步",意思是"同時"。

將這兩個術語放在一起時,您將看到"非同步"表示"不是同時" 就這麼簡單！ 這個定義中沒有併發性或並行性的含義。 在實踐中也是如此。

實際上,F# 中的非同步計算計畫獨立於主程式流執行。 這並不意味著併發性或並行性,也不意味著計算總是在後台發生。 事實上,非同步計算甚至可以同步執行,具體取決於計算的性質和計算執行的環境。

您應該有的主要要點是非同步計算獨立於主程式流。 儘管對異步計算執行的時間或方式幾乎沒有保證,但有一些方法來編排和調度它們。 本文的其餘部分將探討 F# 異步的核心概念以及如何使用 F# 中內置的類型、函數和運算式。

## <a name="core-concepts"></a>核心概念

在 F# 中,非同步程式設計圍繞三個核心概念:

- 表示`Async<'T>`可組合非同步計算的類型。
- 模組`Async`函數允許您安排非同步工作、撰寫非同步計算並轉換同步結果。
- `async { }`[計算運算式](../../language-reference/computation-expressions.md),為構建和控制非同步計算提供方便的語法。

您可以在以下範例中看到以下三個概念:

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

這個選項,`printTotalFileBytes`函數的類型`string -> Async<unit>`為 。 調用函數實際上不會執行非同步計算。 相反,它傳`Async<unit>`回 充當以非同步方式執行*的工作規範的*。 它在其`Async.AwaitTask`正文中調用,它將<xref:System.IO.File.ReadAllBytesAsync%2A>的結果 轉換為適當的類型。

另一個重要的行是呼叫`Async.RunSynchronously`。 這是 Async 模組啟動函數之一,如果要實際執行 F# 異步計算,則需要調用這些函數。

這與 C#/可視化`async`基本 程式設計風格有根本區別。 在 F# 中,非同步計算可以視為**冷工**。 它們必須顯式開始實際執行。 這具有一些優點,因為它允許您比 C# 或 Visual Basic 更容易組合和序列非同步工作。

## <a name="combine-asynchronous-computations"></a>合併非同步計算

下面是一個通過組合計算構建在前一個範例的基礎上的範例:

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

正如您所看到的,該`main`函數還有更多的調用。 從概念上講,它執行以下操作:

1. 將命令列參數轉換為`Async<unit>``Array.map`具有的計算。
2. 創建一`Async<'T[]>`個計劃並在運行時並行`printTotalFileBytes`運行計算。
3. 建立將`Async<unit>`執行並行計算並忽略此結果的
4. 顯式運行最後一個計算`Async.RunSynchronously`與和 塊,直到它完成。

執行此程式時,`printTotalFileBytes`每個命令列參數並行執行。 由於非同步計算獨立於程式流執行,因此它們無法按順序列印其資訊並完成執行。 計算將並行計劃,但不能保證其執行順序。

## <a name="sequence-asynchronous-computations"></a>序列非同步計算

因為`Async<'T>`是工作規範,而不是已經運行的任務,因此可以輕鬆地執行更複雜的轉換。 下面是一個示例,它對一組 Async 計算進行排序,以便它們逐一執行。

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

這將按計劃`printTotalFileBytes`按的元素的順序執行,`argv`而不是並行調度它們。 由於下一項不會計劃,直到最後一次計算完成執行后,計算將進行排序,以便其執行中沒有重疊。

## <a name="important-async-module-functions"></a>重要的非同步模組功能

在 F# 中編寫非同步碼時,通常會與處理計算計畫的框架進行互動。 但是,情況並非總是如此,因此最好了解各種啟動函數來安排非同步工作。

由於 F# 非同步計算是工作_規範_,而不是已執行的工作的表示形式,因此必須顯式從啟動函數開始。 有許多[Async 啟動函數](https://msdn.microsoft.com/library/ee370232.aspx)在不同的上下文中非常有用。 以下部分介紹一些更常見的起始函數。

### <a name="asyncstartchild"></a>非同步.開始兒童

在非同步計算中啟動子計算。 這允許同時執行多個非同步計算。 子計算與父計算共用取消權杖。 如果取消父計算,則子計算也會取消。

簽章：

```fsharp
computation: Async<'T> * timeout: ?int -> Async<Async<'T>>
```

使用時機：

- 當您要同時執行多個非同步計算,而不是一次執行一個非同步計算時,卻不希望將它們同時計畫。
- 當您希望將子計算的存留期與父計算的存留期綁定時。

需要注意的:

- 使用`Async.StartChild`啟動多個計算與並行調度計算計算策略不同。 如果要並行計劃計算,請使用`Async.Parallel`。
- 取消父計算將觸發取消它啟動的所有子計算。

### <a name="asyncstartimmediate"></a>非同步.立即啟動

運行非同步計算,立即開始在當前作業系統線程上。 如果您在計算期間需要更新調用線程上的內容,這非常有用。 例如,如果非同步計算必須更新 UI(如更新進度列),則`Async.StartImmediate`應使用。

簽章：

```fsharp
computation: Async<unit> - cancellationToken: ?CancellationToken -> unit
```

使用時機：

- 當您需要在非同步計算中更新呼叫線程上的內容時。

需要注意的:

- 非同步計算中的代碼將在預定的任何線程上運行。 如果該線程在某種程度上是敏感的(如UI線程),則可能會有問題。 在這種情況下,`Async.StartImmediate`很可能不適合使用。

### <a name="asyncstartastask"></a>非同步.StartAsTask

在線程池中執行計算。 返回將在<xref:System.Threading.Tasks.Task%601>計算終止后在相應狀態上完成的的(生成結果、引發異常或被取消)。 如果未提供取消權杖,則使用預設取消權杖。

簽章：

```fsharp
computation: Async<'T> - taskCreationOptions: ?TaskCreationOptions - cancellationToken: ?CancellationToken -> Task<'T>
```

使用時機：

- 當您需要調用 .NET API<xref:System.Threading.Tasks.Task%601>時,該 API 希望 表示非同步計算的結果。

需要注意的:

- 此調用將分配一個`Task`附加物件,如果經常使用,可能會增加開銷。

### <a name="asyncparallel"></a>非同步.並行

計劃要並行執行的非同步計算序列。 通過指定`maxDegreesOfParallelism`參數,可以選擇調整/限制並行性的程度。

簽章：

```fsharp
computations: seq<Async<'T>> - ?maxDegreesOfParallelism: int -> Async<'T[]>
```

使用時機：

- 如果需要同時運行一組計算,並且不依賴於它們的執行順序。
- 如果不需要並行計劃計算的結果,直到它們全部完成。

需要注意的:

- 只有在所有計算完成後,才能訪問生成的值陣列。
- 計算將運行,但它們最終都會得到計劃。 這意味著您不能依賴他們的執行順序。

### <a name="asyncsequential"></a>非同步。順序

計劃一系列非同步計算,以便按傳遞順序執行。 將執行第一個計算,然後執行下一個計算,等等。 不會並行執行任何計算。

簽章：

```fsharp
computations: seq<Async<'T>> -> Async<'T[]>
```

使用時機：

- 如果需要按順序執行多個計算。

需要注意的:

- 只有在所有計算完成後,才能訪問生成的值陣列。
- 計算將以傳遞給此函數的順序運行,這可能意味著在返回結果之前將經過更多的時間。

### <a name="asyncawaittask"></a>非同步.Await任務

返回一個非同步計算,該計算等待給定<xref:System.Threading.Tasks.Task%601>的計算完成,並將其結果作為`Async<'T>`

簽章：

```fsharp
task: Task<'T>  -> Async<'T>
```

使用時機：

- 使用 .NET API<xref:System.Threading.Tasks.Task%601>時,API 在 F# 非同步計算中傳回 。

需要注意的:

- 異常按照任務並行庫<xref:System.AggregateException>的約定進行包裝,這與 F# 異步通常顯示異常的方式不同。

### <a name="asynccatch"></a>非同步.捕獲

建立一個非同步計算,該計算執行`Async<'T>`給定的`Async<Choice<'T, exn>>`,傳回 。 如果給定`Async<'T>`完成成功,則傳回`Choice1Of2`有結果值的傳回 。 如果在異常完成之前引發異常,`Choice2of2`則返回,並引發異常。 如果它用於由許多計算組成的非同步計算,並且其中一個計算引發異常,則包羅萬象的計算將完全停止。

簽章：

```fsharp
computation: Async<'T> -> Async<Choice<'T, exn>>
```

使用時機：

- 執行非同步工作時,可能會因異常而失敗,並且希望在調用方中處理該異常。

需要注意的:

- 使用組合或序列非同步計算時,如果包包含計算的內部"計算之一引發異常,則包包含計算將完全停止。

### <a name="asyncignore"></a>非同步.忽略

建立運行給定計算並忽略其結果的非同步計算。

簽章：

```fsharp
computation: Async<'T> -> Async<unit>
```

使用時機：

- 當您有不需要結果的非同步計算時。 這類似於非異步`ignore`代碼的代碼。

需要注意的:

- 如果必須使用此,因為您希望使用`Async.Start`或其他`Async<unit>`需要的功能,請考慮丟棄結果是否可以執行。 放棄結果只是為了適合類型簽名通常不應該做。

### <a name="asyncrunsynchronously"></a>非同步同步執行

運行非同步計算,並在調用線程上等待其結果。 此呼叫已阻塞。

簽章：

```fsharp
computation: Async<'T> - timeout: ?int - cancellationToken: ?CancellationToken -> 'T
```

使用時機：

- 如果需要,請僅在應用程式中使用它一次 - 在可執行檔的入口點。
- 當您不關心性能並希望同時執行一組其他非同步操作時。

需要注意的:

- 調用`Async.RunSynchronously`阻止調用線程,直到執行完成。

### <a name="asyncstart"></a>非同步.開始

線上程池中啟動可非同步計算,計算`unit`傳回 。 不等待結果。 從`Async.Start`開始嵌套計算完全獨立於調用它們的父計算開始。 其存留期不與任何父計算相關聯。 如果取消父計算,則不會取消子計算。

簽章：

```fsharp
computation: Async<unit> - cancellationToken: ?CancellationToken -> unit
```

只在:

- 非同步計算不會產生結果和/或需要處理一個結果。
- 您無需知道非同步計算何時完成。
- 您不關心非同步計算執行哪個線程。
- 您無需瞭解或報告任務產生的異常。

需要注意的:

- 由開始`Async.Start`計算引發的異常不會傳播到調用方。 調用堆疊將完全解功能。
- 任何有效的工作(如調用`printfn`)`Async.Start`開始 不會導致在程式執行的主線程上發生效果。

## <a name="interoperate-with-net"></a>與 .NET 互通

您可能正在使用使用[非同步/await-](../../../standard/async.md)樣式非同步程式設計的 .NET 庫或 C# 程式庫。 由於 C# 和大多數 .NET 庫使用<xref:System.Threading.Tasks.Task%601><xref:System.Threading.Tasks.Task>和 類型作為`Async<'T>`其核心抽象,而不是 ,您必須跨越這兩種非同步方法之間的邊界。

### <a name="how-to-work-with-net-async-and-taskt"></a>如何使用 .NET 同步與`Task<T>`

使用 .NET 非同步庫和代碼<xref:System.Threading.Tasks.Task%601>庫( 即具有返回值的非同步計算)非常簡單,並且具有 F# 的內置支援。

可以使用函數`Async.AwaitTask`等待 .NET 同步計算:

```fsharp
let getValueFromLibrary param =
    async {
        let! value = DotNetLibrary.GetValueAsync param |> Async.AwaitTask
        return value
    }
```

可以使用函數`Async.StartAsTask`將非同步計算到 .NET 呼叫者:

```fsharp
let computationForCaller param =
    async {
        let! result = getAsyncResult param
        return result
    } |> Async.StartAsTask
```

### <a name="how-to-work-with-net-async-and-task"></a>如何使用 .NET 同步與`Task`

要使用使用的<xref:System.Threading.Tasks.Task>API (即 .NET 非同步計算不傳回值),您可能需要新增`Async<'T>`一個轉換為的<xref:System.Threading.Tasks.Task>其他函數:

```fsharp
module Async =
    // Async<unit> -> Task
    let startTaskFromAsyncUnit (comp: Async<unit>) =
        Async.StartAsTask comp :> Task
```

已經有一個`Async.AwaitTask`接受<xref:System.Threading.Tasks.Task>作為 輸入的。 使用此函數和以前定義的`startTaskFromAsyncUnit`函數,可以從 F# 異<xref:System.Threading.Tasks.Task>步計算開始和等待類型。

## <a name="relationship-to-multi-threading"></a>與多線程的關係

儘管本文中提到了線程,但有兩件重要的事情需要記住:

1. 除非在當前線程上顯式啟動,否則非同步計算和線程之間沒有關聯。
1. F# 中的非同步程式設計不是多線程的抽象。

例如,計算實際上可能在其調用方的線程上運行,具體取決於工作的性質。 計算還可以「跳轉」線程之間,借用它們少量時間在「等待」期間(例如網路呼叫傳輸時)之間執行有用的工作。

儘管 F# 提供了在當前線程(或顯式不在當前線程上)啟動非同步計算的一些功能,但異步通常不與特定的線程策略相關聯。

## <a name="see-also"></a>另請參閱

- [F# 非同步程式設計模型](https://www.microsoft.com/research/publication/the-f-asynchronous-programming-model)
- [Jet.com 的 F# 非同步指南](https://medium.com/jettech/f-async-guide-eb3c8a2d180a)
- [F# 用於娛樂和盈利的非同步程式指導](https://fsharpforfunandprofit.com/posts/concurrency-async-and-parallel/)
- [C# 和 F# 中的非同步:C 中的非同步#](http://tomasp.net/blog/csharp-async-gotchas.aspx/)
