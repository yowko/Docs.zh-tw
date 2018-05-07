---
title: 'F # 中的非同步程式設計'
description: '了解如何完成 F # 非同步程式設計的語言層級的程式設計模型是易於使用和自然語言，透過。'
ms.date: 06/20/2016
ms.openlocfilehash: 93ecd05efc493489435214dcd7ae78fffcccec1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="async-programming-in-f"></a>F # 中的非同步程式設計 #

> [!NOTE]
> 本文章中發現某些不準確。  它正在重寫。  請參閱[問題 #666](https://github.com/dotnet/docs/issues/666)若要了解所做的變更。

非同步程式設計 F # 中，即可完成設計為易於使用和自然語言的語言層級程式設計模型。

F # 中的非同步程式設計的核心是`Async<'T>`，可以觸發要在背景中執行的工作的表示法其中`'T`透過特殊傳回的型別`return`關鍵字或`unit`如果非同步工作流程沒有。傳回的結果。

若要了解的重要概念是非同步運算式的類型是`Async<'T>`，也就是只_規格_的工作來完成非同步的內容中。 不會執行直到明確地以其中一個開始的函式的開頭 (例如`Async.RunSynchronously`)。 雖然這是不同的方式來思考執行工作時，它最終會被實際上相當簡單。

例如，假設您想要從 dotnetfoundation.org 下載 HTML，而不會封鎖主執行緒。 您可以完成它，就像這樣：

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

就是這麼容易！ 除了使用`async`， `let!`，和`return`，這是一般只要 F # 程式碼。

有幾個語法建構是值得注意：

*   `let!` 將繫結運算式結果的非同步 （它是在其他內容）。
*   `use!` 運作方式就像`let!`，但超出範圍時便會處置它繫結的資源。
*   `do!` 將會等候非同步工作流程，後者則不會傳回任何項目。
*   `return` 只從非同步運算式會傳回結果。
*   `return!` 執行另一個非同步工作流程並傳回它的傳回值的結果。

此外，一般`let`， `use`，和`do`關鍵字可以用旁邊的非同步版本，就如同一般函式中。

## <a name="how-to-start-async-code-in-f"></a>如何啟動 F # 中的非同步程式碼 #

如先前所述，非同步程式碼會為要進行明確的啟動所需的其他內容中的工作規格。 以下是兩個主要的方式可完成這項作業：

1.  `Async.RunSynchronously` 將啟動另一個執行緒上非同步工作流程，並等候其結果。

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

2.  `Async.Start` 開始非同步工作流程，另一個執行緒上，將**不**等候其結果。

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

還有其他方式啟動非同步工作流程提供給其他特定的情況。 它們詳述[非同步參考中](https://msdn.microsoft.com/library/ee370232.aspx)。

### <a name="a-note-on-threads"></a>在執行緒上附註

上述 「 在另一個執行緒"片語，但請務必了解**這不表示非同步工作流程的外觀的多執行緒**。 工作流程實際"跳 」 之間需它們靠借貸小的一段時間才能執行有用的工作的執行緒。 當非同步工作流程會有效地 「 正在等候 」 （例如，等待網路呼叫，以傳回內容） 時，它所需靠借貸時的任何執行緒被釋出最有用的工作移執行上其他項目。 這可讓非同步工作流程，以利用的系統盡可能有效率地執行，並使其更大量的 I/O 案例特別強大。

## <a name="how-to-add-parallelism-to-async-code"></a>如何將平行處理原則新增至非同步程式碼

有時候您可能需要執行多個非同步作業以平行方式，收集其結果，並以某種方式解譯。 `Async.Parallel` 可讓您執行這項操作，而不需要使用工作平行程式庫，這會牽涉到要強制轉型需要`Task<'T>`和`Async<'T>`型別。

下列範例會使用`Async.Parallel`若要下載 HTML 從四個熱門的網站，以平行方式，等候這些工作完成，然後再列印已下載的 HTML。

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

*   將"Async"附加至您要使用的任何函式的結尾

 雖然這是只使用命名慣例，但它並簡化之類的應用程式開發介面可搜尋性。 特別是如果有同步和非同步版本的相同的常式，最好明確陳述這是非同步的名稱。

*   聆聽編譯器 ！

 F # 編譯器非常嚴格，讓您幾乎不可能做到麻煩類似"async"的程式碼同步執行。 如果您遇到警告時，這是程式碼將不會執行自己設想將會使用正負號。 如果您可以讓編譯器滿意，如預期般，將最有可能會執行您的程式碼。

## <a name="for-the-cvb-programmer-looking-into-f"></a>針對 C# /VB 程式設計人員想要 F # #

本節假設您熟悉 C# 中的非同步模型 / VB 如果不是，[以 C# 撰寫的非同步](../../../csharp/async.md)是起始點。

沒有 C# /VB 非同步模型與 F # 非同步模型之間的基本差異。

當您呼叫的函式會傳回`Task`或`Task<'T>`，該作業已開始執行。 傳回的控制代碼表示已經在執行非同步作業。 相反地，當您呼叫 async 函式在 F #`Async<'a>`傳回代表工作都將**產生**在某個時間點。 了解此模型是功能強大，因為它允許 F # 中的非同步作業的鏈結在一起更方便地有條件地執行，而且會使用更精細的資料粒度的控制項來啟動。

有幾個其他相似性與值得注意的差異。

### <a name="similarities"></a>相似之處

*   `let!``use!`，和`do!`類似於`await`內呼叫非同步作業時`async{ }`區塊。

 三個關鍵字只可用於`async { }`區塊，類似`await`只內叫用`async`方法。 簡單地說，`let!`適用於當您想要擷取並使用結果，`use!`相同，但是為之後使用時，應該清除其資源的項目和`do!`適用於當您想要等候的非同步工作流程完成不傳回值再進行。

*   F # 類似的方式支援資料平行處理原則。

 其運作方式非常不同，雖然`Async.Parallel`對應至`Task.WhenAll`它們全部完成時，由一組非同步工作的結果的案例。

### <a name="differences"></a>差異

*   巢狀`let!`不允許，不同於巢狀結構 `await`

 不同於`await`，這可以巢狀無限期地`let!`無法和其結果，然後再將它在另一個繫結必須`let!`， `do!`，或`use!`。

*   取消支援是在 F # 與 C# 中更簡單 / VB

 在 C# /VB 支援取消的工作中途島，透過其執行需要檢查`IsCancellationRequested`屬性或呼叫`ThrowIfCancellationRequested()`上`CancellationToken`傳遞至非同步方法的物件。

相反地，F # 非同步工作流程會較自然可取消。 取消是簡單的三個步驟程序。

1.  建立新的 `CancellationTokenSource`。
2.  請將它傳遞到起始的函式。
3.  呼叫`Cancel`對這個語彙基元。

範例：

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

let token = new CancellationTokenSource()
Async.Start (workflow, token)

// Immediately cancel uploadDataAsync after it's been started.
token.Cancel()
```

就是這麼容易！

## <a name="further-resources"></a>進一步的資源：

*   [MSDN 上的非同步工作流程](https://msdn.microsoft.com/library/dd233250.aspx)
*   [F # 的非同步順序](https://fsprojects.github.io/FSharp.Control.AsyncSeq/library/AsyncSeq.html)
*   [F # 資料 HTTP 公用程式](https://fsharp.github.io/FSharp.Data/library/Http.html)
