---
title: 使用以工作為基礎的非同步模式
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: 033cf871-ae24-433d-8939-7a3793e547bf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08b5dee94a9a23fdd1c9e635aa2ef848f59e86cf
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169139"
---
# <a name="consuming-the-task-based-asynchronous-pattern"></a>使用以工作為基礎的非同步模式

當您使用以工作為基礎的非同步模式 (TAP) 執行非同步作業時，您可以使用回撥來達到等待而不封鎖。  就工作而言，這可透過 <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> 之類的方法來達成。 以語言為基礎的非同步支援允許非同步作業在正常控制流程中等候，以隱藏回撥，而編譯器產生的程式碼提供這種相同的 API 層級支援。

## <a name="suspending-execution-with-await"></a>使用 Await 暫停執行
 從 .NET Framework 4.5 開始，您可以使用 C# 的 [await](../../csharp/language-reference/operators/await.md) 關鍵字和 Visual Basic 的 [Await 運算子](../../visual-basic/language-reference/operators/await-operator.md)，以非同步方式等候 <xref:System.Threading.Tasks.Task> 和 <xref:System.Threading.Tasks.Task%601> 物件。 當您等候的是 <xref:System.Threading.Tasks.Task> 時，`await` 運算式的類型會是 `void`。 當您等候的是 <xref:System.Threading.Tasks.Task%601> 時，`await` 運算式的類型會是 `TResult`。 `await` 運算式必須發生在非同步方法的主體內。 如需 .NET Framework 4.5 中的 C# 和 Visual Basic 語言支援的詳細資訊，請參閱 C# 和 Visual Basic 語言規格。

 實際上，等候功能會使用接續在工作上安裝回撥。  此回撥會從暫止點繼續非同步方法。 當非同步方法繼續時，如果等候的作業順利完成，而且是 <xref:System.Threading.Tasks.Task%601>，就會傳回其 `TResult`。  如果所等候的 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 以 <xref:System.Threading.Tasks.TaskStatus.Canceled> 狀態結束，則會擲回 <xref:System.OperationCanceledException> 例外狀況。  如果所等候的 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 以 <xref:System.Threading.Tasks.TaskStatus.Faulted> 狀態結束，則會擲回造成它發生錯誤的例外狀況。 `Task` 會因為多個例外狀況而錯誤，但只會傳播其中一個例外狀況。 不過，<xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> 屬性會傳回包含所有錯誤的 <xref:System.AggregateException> 例外狀況。

 如果同步處理內容 (<xref:System.Threading.SynchronizationContext> 物件) 與暫止時正在執行非同步方法的執行緒關聯 (例如，如果 <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> 屬性不是 `null`)，非同步方法就會在相同的同步處理內容上使用該內容的 <xref:System.Threading.SynchronizationContext.Post%2A> 方法繼續執行。 否則，它會依賴暫止時當前的工作排程器 (<xref:System.Threading.Tasks.TaskScheduler> 物件)。 通常，這會是以執行緒集區為目標的預設工作排程器 (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>)。 這個工作排程器決定等候的非同步作業是否應該在完成處繼續，還是應該排定繼續。 預設排程器通常允許在完成等候作業的執行緒上接續執行。

 呼叫非同步方法時會同步執行函式主體，直到尚未完成的可等候執行個體上的第一個 await 運算式為止，此時引動過程會返回呼叫端。 如果非同步方法並未傳回 `void`，則會傳回 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 物件來代表進行中的計算。 在非 void 非同步方法中，如果遇到 return 陳述式或到達方法主體的結尾，工作會以 <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> 最終狀態完成。 如果未處理的例外狀況導致控制權離開非同步方法的主體，工作則會以 <xref:System.Threading.Tasks.TaskStatus.Faulted> 狀態結束。 如果例外狀況是 <xref:System.OperationCanceledException>，工作就會變成在 <xref:System.Threading.Tasks.TaskStatus.Canceled> 狀態下結束。 就這樣，最後會發佈結果或例外狀況。

 此行為有數個重要的變化。  基於效能考量，如果工作在開始等候之前已完成，則不會讓出控制權，函式會繼續執行。  此外，返回原始內容不一見得是想要的行為，可以變更；下一節會詳細說明。

### <a name="configuring-suspension-and-resumption-with-yield-and-configureawait"></a>使用 Yield 和 ConfigureAwait 設定暫止和繼續
 有數種方法可以更充分掌控非同步方法的執行。 例如，您可以使用 <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> 方法在非同步方法的中導入 Yield 點：

```csharp
public class Task : …
{
    public static YieldAwaitable Yield();
    …
}
```

 這相當於以非同步方式往回張貼或排定到目前的內容。

```csharp
Task.Run(async delegate
{
    for(int i=0; i<1000000; i++)
    {
        await Task.Yield(); // fork the continuation into a separate work item
        ...
    }
});
```

 您也可以使用 <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> 方法，更充分掌控非同步方法中的暫止和繼續。  如前面所述，根據預設，目前的內容是在非同步方法暫停時擷取，並在恢復時用該擷取的內容來叫用非同步方法的接續動作。  在許多情況下，這就是您想要的行為。  在其他情況下，您可能不在意接續內容，您可以避免這樣往回張貼到原始內容，以達到更高效能。  若要這樣做，請使用 <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> 方法來告知等候作業不要在內容上擷取和繼續，而是只要所等候的非同步作業完成，就繼續執行︰

```csharp
await someTask.ConfigureAwait(continueOnCapturedContext:false);
```

## <a name="canceling-an-asynchronous-operation"></a>取消非同步作業
 從 .NET Framework 4 開始，支援取消的 TAP 方法即至少提供一個可接受取消權杖 (<xref:System.Threading.CancellationToken> 物件) 的多載。

 建立取消權杖時，會透過某個取消權杖來源 (<xref:System.Threading.CancellationTokenSource> 物件) 來建立。  來源的 <xref:System.Threading.CancellationTokenSource.Token%2A> 屬性會傳回取消權杖，當呼叫來源的 <xref:System.Threading.CancellationTokenSource.Cancel%2A> 方法時，此權杖就會收到訊號。  例如，若要下載單一網頁，而且想要能夠取消作業，則需建立 <xref:System.Threading.CancellationTokenSource> 物件，將其權杖傳遞給 TAP 方法，然後在您準備好要取消作業時，呼叫來源的 <xref:System.Threading.CancellationTokenSource.Cancel%2A> 方法︰

```csharp
var cts = new CancellationTokenSource();
string result = await DownloadStringAsync(url, cts.Token);
… // at some point later, potentially on another thread
cts.Cancel();
```

 若要取消多個非同步引動過程，您可以將相同的語彙基元傳遞至所有引動過程︰

```csharp
var cts = new CancellationTokenSource();
    IList<string> results = await Task.WhenAll(from url in urls select DownloadStringAsync(url, cts.Token));
    // at some point later, potentially on another thread
    …
    cts.Cancel();
```

 或者，您可以將相同的語彙基元傳遞至一組經過挑選的作業︰

```csharp
var cts = new CancellationTokenSource();
    byte [] data = await DownloadDataAsync(url, cts.Token);
    await SaveToDiskAsync(outputPath, data, CancellationToken.None);
    … // at some point later, potentially on another thread
    cts.Cancel();
```

 任何執行緒都可能起始取消要求。

 您可以將 <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> 值傳遞給任何接受取消權杖的方法，以表示永遠不要求取消作業。  這會導致 <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> 屬性傳回 `false`，而可相應地將所呼叫的方法最佳化。  在測試時，您也可以傳入以建構函式具現化之預先取消的取消語彙基元，此建構函式接受布林值，以指出語彙基元最初應該處於已取消或不可取消狀態。

 這種取消方法有幾項優點︰

- 您可以將相同的取消語彙基元傳遞至任何數目的非同步和同步作業。

- 相同的取消要求可以擴散至任何數目的接聽程式。

- 非同步 API 的開發人員可以完全控制是否可要求取消及何時生效。

- 使用 API 的程式碼可能選擇性地決定要將取消要求傳播至其中的非同步引動過程。

## <a name="monitoring-progress"></a>監視進度
 某些非同步方法會透過傳遞至非同步方法的進度介面來公開進度。  例如，假設一個函式以非同步方式下載文字字串，對於過程中以進度更新顯示目前為止完成的下載百分比。  Windows Presentation Foundation (WPF) 應用程式中可以使用這種方法，如下所示︰

```csharp
private async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.IsEnabled = false;
    try
    {
        txtResult.Text = await DownloadStringAsync(txtUrl.Text,
            new Progress<int>(p => pbDownloadProgress.Value = p));
    }
    finally { btnDownload.IsEnabled = true; }
}
```

<a name="combinators"></a>
## <a name="using-the-built-in-task-based-combinators"></a>使用內建以工作為基礎的組合器
 <xref:System.Threading.Tasks> 命名空間包含數個用於撰寫和處理工作的方式。

### <a name="taskrun"></a>Task.Run
 <xref:System.Threading.Tasks.Task>類別包含數個 <xref:System.Threading.Tasks.Task.Run%2A> 方法，可讓您輕鬆地將工作以 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 的形式卸載至執行緒集區，例如：

```csharp
public async void button1_Click(object sender, EventArgs e)
{
    textBox1.Text = await Task.Run(() =>
    {
        // … do compute-bound work here
        return answer;
    });
}
```

 這些 <xref:System.Threading.Tasks.Task.Run%2A> 方法中有些 (例如 <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> 多載) 會作為 <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> 方法的速記。  其他多載 (例如 <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>) 則可讓您在所卸載的工作中使用 await，例如：

```csharp
public async void button1_Click(object sender, EventArgs e)
{
    pictureBox1.Image = await Task.Run(async() =>
    {
        using(Bitmap bmp1 = await DownloadFirstImageAsync())
        using(Bitmap bmp2 = await DownloadSecondImageAsync())
        return Mashup(bmp1, bmp2);
    });
}
```

 這類多載在邏輯上等同於使用 <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> 方法搭配「工作平行程式庫」中的 <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> 擴充方法。

### <a name="taskfromresult"></a>Task.FromResult
 在可能已有資料可用，而只需從放在 <xref:System.Threading.Tasks.Task%601> 中的工作傳回方法傳回的情況下，請使用 <xref:System.Threading.Tasks.Task.FromResult%2A> 方法：

```csharp
public Task<int> GetValueAsync(string key)
{
    int cachedValue;
    return TryGetCachedValue(out cachedValue) ?
        Task.FromResult(cachedValue) :
        GetValueAsyncInternal();
}

private async Task<int> GetValueAsyncInternal(string key)
{
    …
}
```

### <a name="taskwhenall"></a>Task.WhenAll
 請使用 <xref:System.Threading.Tasks.Task.WhenAll%2A> 方法，以非同步方式等候多個以工作表示的非同步作業。  此方法有多個多載可支援一組非泛型工作或一組非統一泛型工作 (例如，非同步等候多個 void 傳回作業，或非同步等候多個值傳回方法，而每個值可能有不同型別)，也支援一組統一泛型工作 (例如，非同步等候多個 `TResult` 傳回方法)。

 假設您想要將電子郵件訊息傳送給數個客戶。 您可以重疊傳送訊息，不必等待一個訊息完成才傳送下一個訊息。 您也可以查明傳送作業何時完成及是否發生任何錯誤︰

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
await Task.WhenAll(asyncOps);
```

 以下程式碼不會明確處理可能發生的例外狀況，而是會在 <xref:System.Threading.Tasks.Task.WhenAll%2A> 產生的工作上，讓例外狀況從 `await` 傳播出來。  若要處理例外狀況，您可以使用下列程式碼︰

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
try
{
    await Task.WhenAll(asyncOps);
}
catch(Exception exc)
{
    ...
}
```

 在此案例中，如果任何非同步作業失敗，所有例外狀況會合併成一個 <xref:System.AggregateException> 例外狀況，並儲存在 <xref:System.Threading.Tasks.Task.WhenAll%2A> 方法所傳回的 <xref:System.Threading.Tasks.Task> 中。  不過，`await` 關鍵字只會傳播其中一個例外狀況。  如果您想要檢查所有例外狀況，您可以改寫先前的程式碼，如下所示︰

```csharp
Task [] asyncOps = (from addr in addrs select SendMailAsync(addr)).ToArray();
try
{
    await Task.WhenAll(asyncOps);
}
catch(Exception exc)
{
    foreach(Task faulted in asyncOps.Where(t => t.IsFaulted))
    {
        … // work with faulted and faulted.Exception
    }
}
```

 舉例說明，假設從 web 非同步下載多個檔案。  在此例子中，所有非同步作業有相同的結果型別，很容易存取結果︰

```csharp
string [] pages = await Task.WhenAll(
    from url in urls select DownloadStringAsync(url));
```

 您可以使用我們在先前 void 傳回案例中討論過的相同例外狀況處理技術︰

```csharp
Task [] asyncOps =
    (from url in urls select DownloadStringAsync(url)).ToArray();
try
{
    string [] pages = await Task.WhenAll(asyncOps);
    ...
}
catch(Exception exc)
{
    foreach(Task<string> faulted in asyncOps.Where(t => t.IsFaulted))
    {
        … // work with faulted and faulted.Exception
    }
}
```

### <a name="taskwhenany"></a>Task.WhenAny
 您可以使用 <xref:System.Threading.Tasks.Task.WhenAny%2A> 方法，在多個以工作表示的非同步作業中，只以非同步方式等候其中一個完成。  這個方法適用於四種主要的使用案例：

- 備援：多次執行某項作業並選擇最先完成的作業 (例如，連絡會產生單一結果之提供股價報價服務的多個網站，且選擇最快完成的那一個)。

- 交錯：啟動多項作業並等候所有作業完成，不過，會在作業完成時才進行處理。

- 節流：當作業完成時，允許其他作業開始。  這是交錯情節的擴充。

- 提早釋出：例如，工作 t1 代表的作業可以在 <xref:System.Threading.Tasks.Task.WhenAny%2A> 工作中與另一個工作 t2 合併成群組，然後您可以等候 <xref:System.Threading.Tasks.Task.WhenAny%2A> 工作。 工作 t2 可代表造成 <xref:System.Threading.Tasks.Task.WhenAny%2A> 工作比 t1 更早完成的逾時、取消或一些其他訊號。

#### <a name="redundancy"></a>備援性
 假設您想決定是否購買股票。  您有好幾個信任的股票建議 Web 服務，不過依據每日負載，每個服務可能會在不同時間點變得很慢。  您可以使用 <xref:System.Threading.Tasks.Task.WhenAny%2A> 方法來接收任何作業完成的通知：

```csharp
var recommendations = new List<Task<bool>>()
{
    GetBuyRecommendation1Async(symbol),
    GetBuyRecommendation2Async(symbol),
    GetBuyRecommendation3Async(symbol)
};
Task<bool> recommendation = await Task.WhenAny(recommendations);
if (await recommendation) BuyStock(symbol);
```

 不同於 <xref:System.Threading.Tasks.Task.WhenAll%2A> 會傳回所有成功完成之工作的未包裝結果，<xref:System.Threading.Tasks.Task.WhenAny%2A> 會傳回已完成的工作。 如果工作失敗，必須知道它已失敗，如果工作成功，必須知道與傳回值相關聯的工作。  因此，您需要存取所傳回工作的結果，或進一步等待，如這個範例所示。

 與使用 <xref:System.Threading.Tasks.Task.WhenAll%2A> 時相同，您必須能夠通融例外狀況。  因為您要收回已完成的工作，您可以等候傳回的工作傳播錯誤，並適當地 `try/catch`，例如︰

```csharp
Task<bool> [] recommendations = …;
while(recommendations.Count > 0)
{
    Task<bool> recommendation = await Task.WhenAny(recommendations);
    try
    {
        if (await recommendation) BuyStock(symbol);
        break;
    }
    catch(WebException exc)
    {
        recommendations.Remove(recommendation);
    }
}
```

 此外，即使第一個工作成功完成，後續工作可能失敗。  此時，您有幾個處理例外狀況的選項：您可以等待所有啟動的工作完成，在這種情況下，您可以使用 <xref:System.Threading.Tasks.Task.WhenAll%2A> 方法，或者您可以決定所有例外狀況都很重要且必須全部記錄。  對此，您可以使用接續，在工作完成時以非同步方式接收通知︰

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => { if (t.IsFaulted) Log(t.Exception); });
}
```

 或：

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => Log(t.Exception), TaskContinuationOptions.OnlyOnFaulted);
}
```

 或甚至︰

```csharp
private static async void LogCompletionIfFailed(IEnumerable<Task> tasks)
{
    foreach(var task in tasks)
    {
        try { await task; }
        catch(Exception exc) { Log(exc); }
    }
}
…
LogCompletionIfFailed(recommendations);
```

 最後，您可能想要取消其餘所有作業︰

```csharp
var cts = new CancellationTokenSource();
var recommendations = new List<Task<bool>>()
{
    GetBuyRecommendation1Async(symbol, cts.Token),
    GetBuyRecommendation2Async(symbol, cts.Token),
    GetBuyRecommendation3Async(symbol, cts.Token)
};

Task<bool> recommendation = await Task.WhenAny(recommendations);
cts.Cancel();
if (await recommendation) BuyStock(symbol);
```

#### <a name="interleaving"></a>交錯
 假設您從 web 下載影像並處理每個影像 (例如，將影像新增至 UI 控制項)。  您必須在 UI 執行緒上循序處理，但您想要盡可能同時下載影像。 此外，您不想等到影像全部下載後才新增至 UI，您想要在影像完成下載時就新增：

```csharp
List<Task<Bitmap>> imageTasks =
    (from imageUrl in urls select GetBitmapAsync(imageUrl)).ToList();
while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch{}
}
```

 如果所下載影像的 <xref:System.Threading.ThreadPool> 上涉及密集運算處理，您也可以套用交錯，例如：

```csharp
List<Task<Bitmap>> imageTasks =
    (from imageUrl in urls select GetBitmapAsync(imageUrl)
         .ContinueWith(t => ConvertImage(t.Result)).ToList();
while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch{}
}
```

#### <a name="throttling"></a>節流
 在交錯範例中，除非使用者下載太多影像，以至於必須節流下載。例如，您只想要同時進行一定數量的下載。 為了達到此目的，您可以先啟動一部分的非同步作業。  當這些作業完成時，您可以再啟動另一批作業︰

```csharp
const int CONCURRENCY_LEVEL = 15;
Uri [] urls = …;
int nextIndex = 0;
var imageTasks = new List<Task<Bitmap>>();
while(nextIndex < CONCURRENCY_LEVEL && nextIndex < urls.Length)
{
    imageTasks.Add(GetBitmapAsync(urls[nextIndex]));
    nextIndex++;
}

while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch(Exception exc) { Log(exc); }

    if (nextIndex < urls.Length)
    {
        imageTasks.Add(GetBitmapAsync(urls[nextIndex]));
        nextIndex++;
    }
}
```

#### <a name="early-bailout"></a>提早脫離
 假設您以非同步方式等候作業完成，同時也回應使用者的取消要求 (例如，使用者按一下取消按鈕)。 下列程式碼說明這種情節：

```csharp
private CancellationTokenSource m_cts;

public void btnCancel_Click(object sender, EventArgs e)
{
    if (m_cts != null) m_cts.Cancel();
}

public async void btnRun_Click(object sender, EventArgs e)
{
    m_cts = new CancellationTokenSource();
    btnRun.Enabled = false;
    try
    {
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text);
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);
        if (imageDownload.IsCompleted)
        {
            Bitmap image = await imageDownload;
            panel.AddImage(image);
        }
        else imageDownload.ContinueWith(t => Log(t));
    }
    finally { btnRun.Enabled = true; }
}

private static async Task UntilCompletionOrCancellation(
    Task asyncOp, CancellationToken ct)
{
    var tcs = new TaskCompletionSource<bool>();
    using(ct.Register(() => tcs.TrySetResult(true)))
        await Task.WhenAny(asyncOp, tcs.Task);
    return asyncOp;
}
```

 當您決定脫離時，此實作會立即重新啟用使用者介面，但不取消幕後的非同步作業。  另一種方式是在您決定脫離時取消暫止的作業，但在作業實際完成之前不重新建立使用者介面，可能是由於取消要求而提早結束︰

```csharp
private CancellationTokenSource m_cts;

public async void btnRun_Click(object sender, EventArgs e)
{
    m_cts = new CancellationTokenSource();

    btnRun.Enabled = false;
    try
    {
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text, m_cts.Token);
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);
        Bitmap image = await imageDownload;
        panel.AddImage(image);
    }
    catch(OperationCanceledException) {}
    finally { btnRun.Enabled = true; }
}
```

 另一個提早釋出的例子涉及使用 <xref:System.Threading.Tasks.Task.WhenAny%2A> 方法搭配 <xref:System.Threading.Tasks.Task.Delay%2A> 方法，如下一節所述。

### <a name="taskdelay"></a>Task.Delay
 您可以使用 <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> 方法在非同步方法的執行過程中引入暫停。  這適用於許多種功能，包括建置輪詢迴圈和將使用者輸入延遲一段預先定義的時間再處理。  <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> 與 <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> 搭配使用時也相當實用，可用來在等候上實作逾時。

 如果更大非同步作業 (例如，ASP.NET Web 服務) 中的一項工作太久才完成，將會波及整體作業，尤其是如果它根本無法完成。  因此，在非同步作業上等候時必須能夠逾時。  同步的 <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType><xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>及 <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> 方法可接受逾時值，但對應的 <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> 和先前提到的 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> 方法則無法接受逾時值。  您可以改用 <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> 搭配 <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> 來實作逾時。

 例如，在您的應用程式 UI 中，假設您想要下載影像，並於下載影像時停用 UI。 不過，如果下載的時間太長，您想要重新啟用 UI 並放棄下載︰

```csharp
public async void btnDownload_Click(object sender, EventArgs e)
{
    btnDownload.Enabled = false;
    try
    {
        Task<Bitmap> download = GetBitmapAsync(url);
        if (download == await Task.WhenAny(download, Task.Delay(3000)))
        {
            Bitmap bmp = await download;
            pictureBox.Image = bmp;
            status.Text = "Downloaded";
        }
        else
        {
            pictureBox.Image = null;
            status.Text = "Timed out";
            var ignored = download.ContinueWith(
                t => Trace("Task finally completed"));
        }
    }
    finally { btnDownload.Enabled = true; }
}
```

 這同樣適用於多個下載，因為 <xref:System.Threading.Tasks.Task.WhenAll%2A> 會傳回工作：

```csharp
public async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.Enabled = false;
    try
    {
        Task<Bitmap[]> downloads =
            Task.WhenAll(from url in urls select GetBitmapAsync(url));
        if (downloads == await Task.WhenAny(downloads, Task.Delay(3000)))
        {
            foreach(var bmp in downloads) panel.AddImage(bmp);
            status.Text = "Downloaded";
        }
        else
        {
            status.Text = "Timed out";
            downloads.ContinueWith(t => Log(t));
        }
    }
    finally { btnDownload.Enabled = true; }
}
```

## <a name="building-task-based-combinators"></a>建置以工作為基礎的組合器
 因為工作能夠完全代表非同步作業，並提供同步和非同步功能來聯結作業、擷取其結果等等，所以您可以建置實用的組合器程式庫，將工作組合以建置更大的模式。  如上一節所述，.NET Framework 包含數個內建的組合器，但您也可以建立自己的組合器。 下列章節提供幾個範例說明可能的結合器方法和型別。

### <a name="retryonfault"></a>RetryOnFault
 在許多情況下，您可能想要在作業前次嘗試失敗時重試。  在同步程式碼中，您可能建置協助程式方法來達到這個目的，例如下列範例中的 `RetryOnFault`︰

```csharp
public static T RetryOnFault<T>(
    Func<T> function, int maxTries)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return function(); }
        catch { if (i == maxTries-1) throw; }
    }
    return default(T);
}
```

 對於以 TAP 實作而傳回工作的非同步作業，您可以建置幾乎完全相同的協助程式方法：

```csharp
public static async Task<T> RetryOnFault<T>(
    Func<Task<T>> function, int maxTries)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return await function().ConfigureAwait(false); }
        catch { if (i == maxTries-1) throw; }
    }
    return default(T);
}
```

 然後，您可以利用此組合器，將重試編碼到應用程式的邏輯中，例如︰

```csharp
// Download the URL, trying up to three times in case of failure
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3);
```

 您可以進一步擴充 `RetryOnFault` 函式。 例如，此函式可以接受另一個 `Func<Task>` 在重試之間叫用，以判斷何時再次嘗試，例如︰

```csharp
public static async Task<T> RetryOnFault<T>(
    Func<Task<T>> function, int maxTries, Func<Task> retryWhen)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return await function().ConfigureAwait(false); }
        catch { if (i == maxTries-1) throw; }
        await retryWhen().ConfigureAwait(false);
    }
    return default(T);
}
```

 然後，您可以如下所示使用此函式，先等待一秒再重試作業︰

```csharp
// Download the URL, trying up to three times in case of failure,
// and delaying for a second between retries
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3, () => Task.Delay(1000));
```

### <a name="needonlyone"></a>NeedOnlyOne
 有時候，您可以利用備援性來改善作業的延遲，提高成功機會。  假設有多個 Web 服務在一天中的不同時間提供股票報價，每個服務可能提供不同的品質等級和回應時間。  為了因應這些變動，您可以發出要求給所有 Web 服務，只要從其中一個服務收到回應，就立刻取消其餘要求。  您可以實作協助程式函式，更輕鬆地實作這種常見模式，亦即啟動多項作業、等候任何回應，然後取消其餘作業。 下列範例中的 `NeedOnlyOne` 函式說明此情節：

```csharp
public static async Task<T> NeedOnlyOne(
    params Func<CancellationToken,Task<T>> [] functions)
{
    var cts = new CancellationTokenSource();
    var tasks = (from function in functions
                 select function(cts.Token)).ToArray();
    var completed = await Task.WhenAny(tasks).ConfigureAwait(false);
    cts.Cancel();
    foreach(var task in tasks)
    {
        var ignored = task.ContinueWith(
            t => Log(t), TaskContinuationOptions.OnlyOnFaulted);
    }
    return completed;
}
```

 然後，您可以如下所示使用此函式︰

```csharp
double currentPrice = await NeedOnlyOne(
    ct => GetCurrentPriceFromServer1Async("msft", ct),
    ct => GetCurrentPriceFromServer2Async("msft", ct),
    ct => GetCurrentPriceFromServer3Async("msft", ct));
```

### <a name="interleaved-operations"></a>交錯作業
 當您處理非常大量的工作時，使用 <xref:System.Threading.Tasks.Task.WhenAny%2A> 方法來支援交錯案例會有潛在的效能問題。  對 <xref:System.Threading.Tasks.Task.WhenAny%2A> 發出的每個呼叫會導致向每個工作登錄接續。 以 N 個工作為例，這會導致在交錯作業的存留期建立 O(N2) 個接續。  如果您要處理的工作量很大，可以使用組合器 (如下列範例中的 `Interleaved`) 來解決效能問題：

```csharp
static IEnumerable<Task<T>> Interleaved<T>(IEnumerable<Task<T>> tasks)
{
    var inputTasks = tasks.ToList();
    var sources = (from _ in Enumerable.Range(0, inputTasks.Count)
                   select new TaskCompletionSource<T>()).ToList();
    int nextTaskIndex = -1;
    foreach (var inputTask in inputTasks)
    {
        inputTask.ContinueWith(completed =>
        {
            var source = sources[Interlocked.Increment(ref nextTaskIndex)];
            if (completed.IsFaulted)
                source.TrySetException(completed.Exception.InnerExceptions);
            else if (completed.IsCanceled)
                source.TrySetCanceled();
            else
                source.TrySetResult(completed.Result);
        }, CancellationToken.None,
           TaskContinuationOptions.ExecuteSynchronously,
           TaskScheduler.Default);
    }
    return from source in sources
           select source.Task;
}
```

 然後，您可以利用組合器處理工作完成時的結果，例如︰

```csharp
IEnumerable<Task<int>> tasks = ...;
foreach(var task in Interleaved(tasks))
{
    int result = await task;
    …
}
```

### <a name="whenallorfirstexception"></a>WhenAllOrFirstException
 在某些分散/集中的情節中，您可能想要等候一個集合的所有工作，但如果其中一個發生錯誤，您想要在發生例外狀況時立刻停止等候。  您可以使用結合器方法來達到此目的，如下列範例中的 `WhenAllOrFirstException`︰

```csharp
public static Task<T[]> WhenAllOrFirstException<T>(IEnumerable<Task<T>> tasks)
{
    var inputs = tasks.ToList();
    var ce = new CountdownEvent(inputs.Count);
    var tcs = new TaskCompletionSource<T[]>();

    Action<Task> onCompleted = (Task completed) =>
    {
        if (completed.IsFaulted)
            tcs.TrySetException(completed.Exception.InnerExceptions);
        if (ce.Signal() && !tcs.Task.IsCompleted)
            tcs.TrySetResult(inputs.Select(t => t.Result).ToArray());
    };

    foreach (var t in inputs) t.ContinueWith(onCompleted);
    return tcs.Task;
}
```

## <a name="building-task-based-data-structures"></a>建置以工作為基礎的資料結構
 除了建置以工作為基礎之自訂組合器的能力之外，在 <xref:System.Threading.Tasks.Task> 和 <xref:System.Threading.Tasks.Task%601> 中提供資料結構來同時代表非同步作業的結果及與其聯結時所需的同步處理，還可讓它變成非常強大的類型，在此類型上即可建置用於非同步案例中的自訂資料結構。

### <a name="asynccache"></a>AsyncCache
 工作的其中一個重要層面就是它可以交給多個取用者，這些取用者全都可以等待它、向它登錄接續、取得其結果或例外狀況 (如果是 <xref:System.Threading.Tasks.Task%601>)等。  這使得 <xref:System.Threading.Tasks.Task> 和 <xref:System.Threading.Tasks.Task%601> 非常適合用於非同步快取基礎結構中。  以下示範一個以 <xref:System.Threading.Tasks.Task%601> 為基礎建置的小型但功能強大的非同步快取：

```csharp
public class AsyncCache<TKey, TValue>
{
    private readonly Func<TKey, Task<TValue>> _valueFactory;
    private readonly ConcurrentDictionary<TKey, Lazy<Task<TValue>>> _map;

    public AsyncCache(Func<TKey, Task<TValue>> valueFactory)
    {
        if (valueFactory == null) throw new ArgumentNullException("loader");
        _valueFactory = valueFactory;
        _map = new ConcurrentDictionary<TKey, Lazy<Task<TValue>>>();
    }

    public Task<TValue> this[TKey key]
    {
        get
        {
            if (key == null) throw new ArgumentNullException("key");
            return _map.GetOrAdd(key, toAdd =>
                new Lazy<Task<TValue>>(() => _valueFactory(toAdd))).Value;
        }
    }
}
```

 [AsyncCache\<TKey,TValue>](https://blogs.msdn.microsoft.com/pfxteam/2010/04/23/parallelextensionsextras-tour-12-asynccache/) 類別可接受採用 `TKey` 並傳回 <xref:System.Threading.Tasks.Task%601> 的函式作為對其建構函式的委派。  先前從快取中存取的任何值會儲存在內部字典中，`AsyncCache` 會確保每個索引鍵只產生一個工作，即使並行存取快取也一樣。

 例如，您可以為下載的網頁建置快取︰

```csharp
private AsyncCache<string,string> m_webPages =
    new AsyncCache<string,string>(DownloadStringAsync);
```

 然後，每當您需要網頁的內容時，您可以在非同步方法中使用此快取。 `AsyncCache` 類別可確保儘可能下載較少的頁面並快取結果。

```csharp
private async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.IsEnabled = false;
    try
    {
        txtContents.Text = await m_webPages["https://www.microsoft.com"];
    }
    finally { btnDownload.IsEnabled = true; }
}
```

### <a name="asyncproducerconsumercollection"></a>AsyncProducerConsumerCollection
 您也可以使用工作來建置資料結構，以協調非同步活動。  請考量其中一種傳統的平行設計模式︰產生者/取用者。  在此模式中，產生者產生由取用者取用的資料，產生者和消費者可以平行執行。 比方說，取用者處理先前由產生者產生的項目 1，而產生者現在產生項目 2。  在產生者/取用者模式中，您無可避免地一定要使用某種資料結構來儲存產生者建立的工作，才能讓取用者在新資料出現時收到通知並且找到新資料。

 以下是根據工作建置的簡單資料結構，可將非同步方法當做產生者和取用者︰

```csharp
public class AsyncProducerConsumerCollection<T>
{
    private readonly Queue<T> m_collection = new Queue<T>();
    private readonly Queue<TaskCompletionSource<T>> m_waiting =
        new Queue<TaskCompletionSource<T>>();

    public void Add(T item)
    {
        TaskCompletionSource<T> tcs = null;
        lock (m_collection)
        {
            if (m_waiting.Count > 0) tcs = m_waiting.Dequeue();
            else m_collection.Enqueue(item);
        }
        if (tcs != null) tcs.TrySetResult(item);
    }

    public Task<T> Take()
    {
        lock (m_collection)
        {
            if (m_collection.Count > 0)
            {
                return Task.FromResult(m_collection.Dequeue());
            }
            else
            {
                var tcs = new TaskCompletionSource<T>();
                m_waiting.Enqueue(tcs);
                return tcs.Task;
            }
        }
    }
}
```

 利用該資料結構，您可以撰寫如下所示的程式碼︰

```csharp
private static AsyncProducerConsumerCollection<int> m_data = …;
…
private static async Task ConsumerAsync()
{
    while(true)
    {
        int nextItem = await m_data.Take();
        ProcessNextItem(nextItem);
    }
}
…
private static void Produce(int data)
{
    m_data.Add(data);
}
```

<xref:System.Threading.Tasks.Dataflow> 命名空間包含 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 類型，使用方式很類似，但不需要建置自訂集合類型︰

```csharp
private static BufferBlock<int> m_data = …;
…
private static async Task ConsumerAsync()
{
    while(true)
    {
        int nextItem = await m_data.ReceiveAsync();
        ProcessNextItem(nextItem);
    }
}
…
private static void Produce(int data)
{
    m_data.Post(data);
}
```

> [!NOTE]
> .NET Framework 4.5 有提供 <xref:System.Threading.Tasks.Dataflow> 命名空間，可透過 **NuGet** 取得。 若要安裝包含 <xref:System.Threading.Tasks.Dataflow> 命名空間的組件，請在 Visual Studio 中開啟您的專案，從 [專案] 功能表中選擇 [管理 NuGet 套件]  ，然後在線上搜尋 Microsoft.Tpl.Dataflow 套件。

## <a name="see-also"></a>另請參閱

- [工作式非同步模式 (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [實作以工作為基礎的非同步模式](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)
- [與其他非同步模式和型別互通](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)
