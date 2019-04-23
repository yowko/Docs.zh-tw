---
title: 非同步程式設計
description: 了解如何F#非同步程式設計透過語言層級的程式設計模型，而且容易使用自然語言來完成。
ms.date: 06/20/2016
ms.openlocfilehash: 6925a0132f9beed6be5f9dded3630b551072bea2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59343450"
---
# <a name="async-programming-in-f"></a>在 F 中的非同步程式設計\#

> [!NOTE]
> 已在這篇文章探索一些不準確。  它是正在重寫。  請參閱[問題 #666](https://github.com/dotnet/docs/issues/666)若要了解所做的變更。

非同步程式設計中F#即可完成設計為易於使用且自然語言的語言層級程式設計模型。

非同步程式設計中的核心F#是`Async<'T>`，可觸發在背景中執行的工作的表示法所在`'T`會傳回透過特殊的型別`return`關鍵字或`unit`如果非同步工作流程具有可傳回的結果。

若要了解的重要概念是非同步運算式的型別`Async<'T>`，也就是只_規格_要在非同步處理內容中完成的工作。 它不會執行直到明確地與其中一個開始的函式開始 (例如`Async.RunSynchronously`)。 雖然這是不同的方式來思考執行工作時，它最後是實際上相當簡單。

例如，假設您想要從 dotnetfoundation.org 下載 HTML，而不會封鎖主執行緒。 您可以完成此作業就像這樣：

```fsharp
open System
open System.Net

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()

        // Execution of fetchHtmlAsync won't continue until the result
        // of AsyncDownloadString is bound.
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

let html = "https://dotnetfoundation.org" |> fetchHtmlAsync |> Async.RunSynchronously
printfn "%s" html
```

就是這麼容易！ 除了使用`async`， `let!`，並`return`，這是正常的只是F#程式碼。

有幾個語法建構是值得一提：

*   `let!` 繫結非同步運算式 （它是在另一個內容） 的結果。
*   `use!` 運作方式就像`let!`，但它超出範圍時，處置其繫結的資源。
*   `do!` 將等候的非同步工作流程不會傳回任何項目。
*   `return` 從非同步運算式，只會傳回結果。
*   `return!` 執行另一個非同步工作流程，並因此會傳回其傳回的值。

此外，正常`let`， `use`，和`do`可以與非同步版本一起使用的關鍵字，就如同一般函式中。

## <a name="how-to-start-async-code-in-f"></a>如何開始在 F 中的非同步程式碼\#

如先前所述，非同步程式碼會是工作的要在需要明確地啟動另一個內容中完成規格。 以下是為了達成此目的的兩種主要方式：

1. `Async.RunSynchronously` 將另一個執行緒上啟動非同步工作流程，並等待其結果。

```fsharp
open System
open System.Net

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

 // Execution will pause until fetchHtmlAsync finishes
 let html = "https://dotnetfoundation.org" |> fetchHtmlAsync |> Async.RunSynchronously

 // you actually have the result from fetchHtmlAsync now!
 printfn "%s" html
 ```

2. `Async.Start` 將會啟動非同步工作流程，另一個執行緒，並將**不**等待其結果。

```fsharp
open System
open System.Net
  
let uploadDataAsync url data = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        webClient.UploadStringAsync(uri, data)
    }

let workflow = uploadDataAsync "https://url-to-upload-to.com" "hello, world!"

// Execution will continue after calling this!
Async.Start(workflow)

printfn "%s" "uploadDataAsync is running in the background..."
 ```

有其他方式來啟動非同步工作流程適用於較特定案例。 這些方式詳述[非同步參考中](https://msdn.microsoft.com/library/ee370232.aspx)。

### <a name="a-note-on-threads"></a>在執行緒上附註

片語 「 在另一個執行緒 」 前面所述，但務必要知道**這不表示非同步工作流程是一個外觀進行多執行緒處理**。 工作流程實際上 」 就會跳 「 之間採用它們的少量的時間才能執行有用工作的執行緒。 非同步工作流程會有效地 「 等待 」 （例如，等候網路呼叫傳回的項目），它採用在任何執行緒是會釋出到移執行其他有用的工作。 這可讓非同步工作流程，利用它們盡可能的情況下，有效地執行的系統，並使其可針對大量 I/O 的情況下特別強大。

## <a name="how-to-add-parallelism-to-async-code"></a>如何將非同步程式碼中的平行處理原則

有時您可能需要執行多個非同步作業以平行方式，收集其結果，並以某種方式解譯這些。 `Async.Parallel` 可讓您執行這項操作，而不需要使用工作平行程式庫，其中會包含您需要強制轉型`Task<'T>`和`Async<'T>`型別。

下列範例會使用`Async.Parallel`到從四種熱門的網站，以平行方式下載 HTML，等候這些工作完成，並再列印已下載的 HTML。

```fsharp
open System
open System.Net

let urlList = 
    [ "https://www.microsoft.com"
      "https://www.google.com"
      "https://www.amazon.com"
      "https://www.facebook.com" ]

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

let getHtmlList urls =
    urls
    |> Seq.map fetchHtmlAsync   // Build an Async<'T> for each site
    |> Async.Parallel           // Returns an Async<'T []>
    |> Async.RunSynchronously   // Wait for the result of the parallel work

let htmlList = getHtmlList urlList

// We now have the downloaded HTML for each site!
for html in htmlList do
    printfn "%s" html
```

## <a name="important-info-and-advice"></a>重要資訊和建議

*   將"Async"附加至您將使用的任何函式的結尾

 雖然這只是命名慣例，它會簡化 API 搜尋功能等項目。 特別是如果有相同的例行工作的同步和非同步版本，最好明確陳述這是非同步，透過名稱。

*   聆聽編譯器 ！

 F#編譯器是非常嚴格，因此幾乎不可能進行像是麻煩以同步方式執行"async"程式碼。 如果您遇到警告時，這是登，程式碼不會認為它將如何執行。 如果您可以讓編譯器滿意，您的程式碼將很有可能會執行，如預期般運作。

## <a name="for-the-cvb-programmer-looking-into-f"></a>針對C#/VB 程式設計人員想成 F\#

本節假設您已熟悉使用中的非同步模型C#/VB. 如果您不是[中的非同步程式設計C#](../../../csharp/async.md)是起始點。

沒有基本差別在於C#/VB 非同步模型和F#非同步模型。

當您呼叫的函式會傳回`Task`或`Task<'T>`，該作業已開始執行。 傳回的控制代碼表示已在執行非同步作業。 相反地，當您呼叫的非同步函式F#，則`Async<'a>`傳回代表工作將會**產生**在某個時間點。 了解此模型是功能強大，因為它可讓您在非同步作業F#鏈結在一起更方便地有條件地執行，並開始時具有更細微的資料粒度的控制。

有幾個其他的相似性與差異值得一提。

### <a name="similarities"></a>相似之處

*   `let!``use!`，並`do!`類似`await`內呼叫的非同步作業時`async{ }`區塊。

 三個關鍵字只可用於`async { }`區塊中，類似`await`才會叫用內部`async`方法。 簡單地說，`let!`是的當您想要擷取並使用結果，`use!`相同，但是為項目使用之後，應該取得清除其資源和`do!`是當您想要等候的非同步工作流程，且沒有傳回值，以完成再繼續。

*   F#類似的方式支援資料平行處理原則。

 其運作方式非常不同的是，雖然`Async.Parallel`對應至`Task.WhenAll`想的一組非同步作業的結果，在全部完成時的案例。

### <a name="differences"></a>差異

*   巢狀`let!`不允許，不同於巢狀結構 `await`

 不同於`await`，這可以巢狀無限期`let!`無法和其結果，然後再將它在另一個繫結必須`let!`， `do!`，或`use!`。

*   取消支援會在F#比C#/VB.

 支援在執行工作中途取消C#/VB 需要檢查`IsCancellationRequested`屬性或呼叫`ThrowIfCancellationRequested()`上`CancellationToken`傳遞至非同步方法的物件。

相反地，F#非同步工作流程是較自然地取消。 取消是簡單的三步驟程序。

1. 建立新的 `CancellationTokenSource`。
2. 請將它傳遞到起始函式。
3. 呼叫`Cancel`語彙基元。

範例：

```fsharp
open System.Threading

// Create a workflow which will loop forever.
let workflow =
    async {
        while true do
            printfn "Working..."
            do! Async.Sleep 1000
    }
    
let tokenSource = new CancellationTokenSource()

// Start the workflow in the background
Async.Start (workflow, tokenSource.Token)

// Executing the next line will stop the workflow
tokenSource.Cancel()
```

就是這麼容易！

## <a name="further-resources"></a>其他資源︰

*   [MSDN 上的非同步工作流程](https://msdn.microsoft.com/library/dd233250.aspx)
*   [非同步順序F#](https://fsprojects.github.io/FSharp.Control.AsyncSeq/library/AsyncSeq.html)
*   [F#HTTP 資料公用程式](https://fsharp.github.io/FSharp.Data/library/Http.html)