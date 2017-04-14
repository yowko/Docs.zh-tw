---
title: "Consuming the Task-based Asynchronous Pattern | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET Framework, and TAP"
  - "asynchronous design patterns, .NET Framework"
  - "TAP, .NET Framework support for"
  - "Task-based Asynchronous Pattern, .NET Framework support for"
  - ".NET Framework, asynchronous design patterns"
ms.assetid: 033cf871-ae24-433d-8939-7a3793e547bf
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# Consuming the Task-based Asynchronous Pattern
當您使用以工作為基礎的非同步模式 \(點選\) 來做非同步作業時，您可以使用回呼避免有阻礙的等待。如需工作，這是透過以下方法來達成，例如 <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=fullName>。  以語言為基礎的非同步支援隱藏回呼，藉由讓非同步作業在一般控制流程中等待，且編譯器產生的程式碼會提供相同的應用程式開發介面支援層級。  
  
## 等待時，執行暫停  
 從開始 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]，您可以使用 C\# [await](../Topic/await%20\(C%23%20Reference\).md) 關鍵字和 [Await Operator](../Topic/Await%20Operator%20\(Visual%20Basic\).md) Visual Basic 做非同步等候 <xref:System.Threading.Tasks.Task> 和 <xref:System.Threading.Tasks.Task%601> 物件。  當您正在等候 <xref:System.Threading.Tasks.Task>時， `await` 運算式是 `void`型別。  當您正在等候 <xref:System.Threading.Tasks.Task%601>時， `await` 運算式是 `TResult`型別。  `await` 運算式必須發生在非同步方法的主體內。  如需更多 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]語言內C\# 和 Visual Basic支援的詳細資訊，請參閱支援 C\# 和 Visual Basic 語言規格。  
  
 在此支援下，等候功能藉由使用接續來安裝工作回呼。此回呼在停止時會繼續非同步方法。  當成功完成等候作業和 <xref:System.Threading.Tasks.Task%601>，其 `TResult` 傳回時，非同步方法會重新開始。如果等候的 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 在 <xref:System.Threading.Tasks.TaskStatus> 結束狀態， <xref:System.OperationCanceledException> 例外狀況 \(Exception\)將會被丟出。如果 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 在 <xref:System.Threading.Tasks.TaskStatus> 結束狀態，其導致錯誤的例外狀況 \(Exception\)會被丟出。   `Task` fault的原因可能是有很多例外狀況 ，不過只有其中一個例外狀況會被傳遞出去。  不過， <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=fullName> 屬性會傳回包含所有錯誤的 <xref:System.AggregateException> 例外狀況。  
  
 如果同步處理內容\(<xref:System.Threading.SynchronizationContext> 物件\) 與在停止時執行的非同步方法執行緒有關聯\(例如，若 <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=fullName> 屬性不是 `null`\)，非同步方法便會使用內容 <xref:System.Threading.SynchronizationContext.Post%2A> 方法來還原在該同步處理內容。  否則，它會根據工作排程器 \(<xref:System.Threading.Tasks.TaskScheduler> 物件\) 在停止時的最新資訊。  通常，這是使用執行緒集區的預設工作排程器 \(<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=fullName>\)。  這個工作排程器會判斷這個等候的非同步作業是否應該繼續完或還原是否應該被排程。  預設排程器通常會允許等候作業完成的執行緒繼續執行。  
  
 當非同步方法被呼叫時，將以同步方式執行函式主體，直到第一個未完成的await函式處於等候中的狀態 ，此時回傳給呼叫者。  如果非同步方法沒有傳回 `void`， <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 物件會被傳回來表示正在執行的計算。  在non\-void的非同步方法中，如果碰到return 陳述式，或到方法主體的結尾時，工作在<xref:System.Threading.Tasks.TaskStatus>達成最終狀態。  如果未處理的例外狀況導致控制項離開非同步方法的主體中，工作將在 <xref:System.Threading.Tasks.TaskStatus> 狀態下完成。  如果例外狀況是 <xref:System.OperationCanceledException>，工作則會在 <xref:System.Threading.Tasks.TaskStatus> 狀態下結束。  因此，結果或例外狀況最終將被發行。  
  
 在此行為中，有幾個很重要的差異。基於效能考量，如果工作在等待資料時就已完成，則控制項將不提供，但函式會繼續執行。此外，回到原來的內容不一定是預期行為，而且可以變更，這會在下一節將詳細說明。  
  
### 設定暫止和繼續執行 Yield 和 ConfigureAwait  
 數個方法會提供對非同步方法執行的更多控制。  例如，您可以使用 <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=fullName> 方法來引入生產點給非同步方法:  
  
```csharp  
public class Task : …  
{  
    public static YieldAwaitable Yield();  
    …  
}  
  
```  
  
 這與非同步回傳或排程返回目前內容相似。  
  
```csharp  
Task.Run(async  delegate  
{  
    for(int i=0; i<1000000; i++)  
    {  
        await Task.Yield(); // fork the continuation into a separate work item  
        ...  
    }  
});  
  
```  
  
 您可以使用 <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=fullName> 方法來控制在同步方法內暫停和還原。前面提過，在預設情況下，目前的內容在非同步方法暫停時會被擷取，並在恢復時用該擷取的內容來叫用非同步方法的接續符號。在許多情況下，這實際上是您想要的行為。在其他情況下，您不需考慮繼續內容，且可以避免這類張貼至原始的內容中，以達到較佳的效能。若要啟用此功能，請使用方法 <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=fullName> 來通知等候作業不再在內容中擷取和還原，但等候完成的非同步作業仍繼續執行的地方:  
  
```csharp  
await someTask.ConfigureAwait(continueOnCapturedContext:false);  
  
```  
  
## 取消非同步作業  
 從[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]開始，支援取消的點選方法\(TAP\)提供取消至少有一個多載語彙\(<xref:System.Threading.CancellationToken> 物件\)。  
  
 取消語彙基元是建立在取消語彙基元的來源 \(<xref:System.Threading.CancellationTokenSource> 物件\) 。來源中的 <xref:System.Threading.CancellationTokenSource.Token%2A> 屬性將傳回 當來源中的 <xref:System.Threading.CancellationTokenSource.Cancel%2A> 方法被呼叫時的取消語彙基元。例如，如果要下載單一網頁而且您希望可以取消作業，請建立 <xref:System.Threading.CancellationTokenSource> 物件，透過屬性的語彙基元點選方法，然後呼叫來源的 <xref:System.Threading.CancellationTokenSource.Cancel%2A> 方法:  
  
```csharp  
var cts = new CancellationTokenSource();  
string result = await DownloadStringAsync(url, cts.Token);  
… // at some point later, potentially on another thread  
cts.Cancel();  
  
```  
  
 若要移除多個非同步引動過程，您可以傳遞相同的語彙基元 \(Token\) 至所有引動過程:  
  
```csharp  
var cts = new CancellationTokenSource();  
    IList<string> results = await Task.WhenAll(from url in urls select DownloadStringAsync(url, cts.Token));  
    // at some point later, potentially on another thread  
    …  
    cts.Cancel();  
  
```  
  
 或者，您可以傳遞相同的語彙基元至作業中的被選擇子集:  
  
```csharp  
var cts = new CancellationTokenSource();  
    byte [] data = await DownloadDataAsync(url, cts.Token);  
    await SaveToDiskAsync(outputPath, data, CancellationToken.None);  
    … // at some point later, potentially on another thread  
    cts.Cancel();  
  
```  
  
 取消的要求可從任何執行緒被啟始。  
  
 您可以傳送 <xref:System.Threading.CancellationToken.None%2A?displayProperty=fullName> 值至可接收取消語彙基元的任意方法中，以表示此取消將不會再重複被要求。這會導致 <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=fullName> 屬性傳回至 `false`，因此呼叫方法可最佳化。為了進行測試，您可以傳送一個欲取消且使用可接受布林值 \(Boolean\)來確認此語彙基元是否應該在已取消或未取消狀態開始的建構函式來執行個體化的語彙基元。  
  
 此取消的方法有下列幾個優點:  
  
-   您可以將相同的取消語彙基元傳到任何數目的非同步和同步處理作業。  
  
-   相同的取消要求可能激增至任何數目的接聽程式。  
  
-   非同步應用程式開發介面的開發人員是完整控制取消是否會被要求且取消可能產生的影響。  
  
-   消費應用程式開發介面的程式碼可能選擇性地判斷取消要求會被傳送到的非同步引動過程。  
  
## 監視進度  
 某些非同步方法透過進度介面公開傳遞至非同步方法。比方說，請考慮以非同步方式下載的文字，並一路引發字串函式的進度更新，包括下載到目前為止完成的百分比。這種方法可以使用在 Windows Presentation Foundation\(WPF\) 應用程式中，如下所示：  
  
```csharp  
private async  void btnDownload_Click(object sender, RoutedEventArgs e)    
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
## 使用內建的任務取向的結合功能  
 <xref:System.Threading.Tasks>命名空間包含了幾種方法來工作和撰寫任務。  
  
### Task.Run  
 <xref:System.Threading.Tasks.Task> 類別 包含多種<xref:System.Threading.Tasks.Task.Run%2A>方法如<xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 至執行緒集區來輕鬆地卸載工作，如下所示:  
  
```csharp  
public async  void button1_Click(object sender, EventArgs e)  
{  
    textBox1.Text = await Task.Run(() =>  
    {  
        // … do compute-bound work here  
        return answer;  
    });  
}  
  
```  
  
 某些 <xref:System.Threading.Tasks.Task.Run%2A> 方法，例如 <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=fullName> 多載，形式存在 <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=fullName> 方法的簡略方式。其他多載，例如 <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=fullName>，可讓您在卸載的工作中等候，如下所示:  
  
```csharp  
public async  void button1_Click(object sender, EventArgs e)  
{  
    pictureBox1.Image = await Task.Run(async() =>  
    {  
        using(Bitmap bmp1 = await DownloadFirstImageAsync())  
        using(Bitmap bmp2 = await DownloadSecondImageAsync())  
        return Mashup(bmp1, bmp2);  
    });  
}  
```  
  
 此類多載在邏輯上等於使用 <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=fullName> 方法與 <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> 擴充方法結合在工作平行程式庫中。  
  
### Task.FromResult  
 使用 <xref:System.Threading.Tasks.Task.FromResult%2A> 方法資料可能必須已有和需要從某個工作會傳回的方法傳回之列舉型別 <xref:System.Threading.Tasks.Task%601>的案例:  
  
```csharp  
public Task<int> GetValueAsync(string key)  
{  
    int cachedValue;  
    return TryGetCachedValue(out cachedValue) ?  
        Task.FromResult(cachedValue) :  
        GetValueAsyncInternal();  
}  
  
private async  Task<int> GetValueAsyncInternal(string key)  
{  
    …  
}  
  
```  
  
### Task.WhenAll  
 使用 <xref:System.Threading.Tasks.Task.WhenAll%2A> 方法來非同步等候代表工作的多個非同步作業。這個方法支援一組非泛型工作或不一致的一組一般工作的多載 \(例如，非同步等候的多個 Null 傳回的作業或非同步等候多個傳回值的方法的值可能有不同的型別\) 和支援一組制式的一般工作 \(例如非同步等候多個 `TResult`\-傳回的方法\)。  
  
 假設您想要傳送電子郵件給多個客戶。  您可以重疊傳送訊息，因此不需在傳送下一封訊息之前等候此訊息完成。  您也可以得知傳送作業何時完成和是否有任何錯誤發生:  
  
```csharp  
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);  
await Task.WhenAll(asyncOps);  
  
```  
  
 這個程式碼不會明確地處理可能發生的例外狀況，但是，讓例外狀況傳播到所產生工作的 `await` 外部從 <xref:System.Threading.Tasks.Task.WhenAll%2A>。若要處理例外狀況，您可以使用下列程式碼:  
  
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
  
 在這個案例中，如果任何非同步作業失敗，所有例外狀況都包含在 <xref:System.AggregateException> 例外狀況中，而此將會被儲存在從<xref:System.Threading.Tasks.Task.WhenAll%2A> 方法傳回的 <xref:System.Threading.Tasks.Task> 不過，只有一個例外狀況會藉由 `await` 關鍵字被傳播。如果您要檢查所有例外狀況，您可以重新撰寫上一個程式碼如下所示:  
  
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
  
 請參考從網路非同步地下載多個檔案之範例。在這個案例中，所有非同步作業有同類型結果型別，且很容易存取結果:  
  
```csharp  
string [] pages = await Task.WhenAll(  
    from url in urls select DownloadStringAsync(url));  
```  
  
 您可以使用先前討論傳回void案例中的例外狀況處理技術:  
  
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
  
### Task.WhenAny  
 您可以使用 <xref:System.Threading.Tasks.Task.WhenAny%2A> 方法來非同步等候以工作的形式表示的多個非同步作業完成。這個方法為四個主要使用案例服務：  
  
-   重複：多次執行某作業並選擇最先完成者\(例如，聯絡多個提供股價報價服務的網站，而此會產生單一結果並且選擇最快完成的那一個\)  
  
-   插入：啟動多個作業並等候所有作業完成，不過當他們完成時處理它們。  
  
-   資料流程：當此作業完成時，允許其他作業開始。這是跨案例的延伸。  
  
-   早期保釋：例如，工作 t1 所表示的作業可以在 <xref:System.Threading.Tasks.Task.WhenAny%2A> 工作中與另一個工作 t2合為一工作群組，然後，您可以在 <xref:System.Threading.Tasks.Task.WhenAny%2A> 工作上等候。  工作 T2 可以表示逾時或取消，或在 t1 完成之前，產生其他序號使 <xref:System.Threading.Tasks.Task.WhenAny%2A> 工作完成。  
  
#### 備援能力  
 考量您將在哪裡決定是否購買股票的情況。有好幾個您信任的股票建議 Web 服務，不過依據每日負載，每個服務結束會可能會在不同時間點變得很慢。您可以使用 <xref:System.Threading.Tasks.Task.WhenAny%2A> 方法來接收任何作業完成的告知：  
  
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
  
 不同於 <xref:System.Threading.Tasks.Task.WhenAll%2A>，傳回所有工作完成時的未包裝結果， <xref:System.Threading.Tasks.Task.WhenAny%2A> 傳回完成的工作。  如果工作執行失敗，因此您必須瞭解它失敗，相反的，如果工作成功，因此您必須瞭解哪一項工作會傳回哪一個相對應的值。因此，如此範例所示，您需要存取這項所傳回之工作的結果或進一步等待。  
  
 使用 <xref:System.Threading.Tasks.Task.WhenAll%2A>，必須可以容納例外狀況。由於您接收到已完成的工作，您可以等候這個傳回的工作來管理錯誤傳播和適當的 `try/catch` 它們;例如:  
  
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
  
 此外，即使第一項工作可順利完成，後續的工作也可能會失敗。此時，您有幾個選項來處理例外狀況：您可以等待，直到所有啟動的工作完成，在這種情況下，您可以使用 <xref:System.Threading.Tasks.Task.WhenAll%2A> 方法的情況下，或者您可以決定所有例外狀況是很重要的，而且必須記錄。對此而言，當工作非同步完成時，您可以使用繼續接收告知:  
  
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
  
 或甚至是：  
  
```  
private static async  void LogCompletionIfFailed(IEnumerable<Task> tasks)  
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
  
 最後，您可能會想要移除所有剩餘的作業:  
  
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
  
#### 交錯  
 考量您從網路下載影像並處理各個影像的情況下 \(例如，將影像加入至 UI 控制項\)。您必須在 UI 執行緒上進行循序處理，不過，您想要盡可能在同一時間內下載多個影像。  此外，您不想阻攔將影像加入至 UI，直到所有的影像都已下載結束\-也就是說，您想在他們都完成後，再將他們一併加入UI:  
  
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
  
 您也可以交錯應用在需要在 <xref:System.Threading.ThreadPool> 上精密計算地處理應用在下載影像的案例;例如:  
  
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
  
#### 節流  
 考慮交錯範例，除了使用者正使用節流閥下載許多影像，例如，您控制特定數量的下載量在同一時間進行。  若要達成這個目的，您可以啟動非同步作業的子集。做為作業完成，您可以啟動其他作業來取代他們的位置:  
  
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
  
#### 早期的備援  
 考量您正在等待非同步作業完成時，同時回應使用者的取消要求時 \(例如，使用者按一下 \[取消\] 按鈕\)。  下列程式碼會說明這個行為：  
  
```csharp  
private CancellationTokenSource m_cts;   
  
public void btnCancel_Click(object sender, EventArgs e)  
{  
    if (m_cts != null) m_cts.Cancel();  
}  
  
public async  void btnRun_Click(object sender, EventArgs e)  
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
  
private static async  Task UntilCompletionOrCancellation(  
    Task asyncOp, CancellationToken ct)  
{  
    var tcs = new TaskCompletionSource<bool>();  
    using(ct.Register(() => tcs.TrySetResult(true)))  
        await Task.WhenAny(asyncOp, tcs.Task);  
    return asyncOp;  
}  
  
```  
  
 這個實作重新啟用使用者介面，一旦您決定使用備援，但不會移除對應的非同步作業。當您決定紓困時，另一種選擇是取消待判定的作業，但不要重新建置使用者介面，直到作業的完成，而此可能是因為取消要求而造成的提早結束:  
  
```csharp  
private CancellationTokenSource m_cts;  
  
public async  void btnRun_Click(object sender, EventArgs e)  
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
  
 另一個關於早期紓困的範例使用 <xref:System.Threading.Tasks.Task.WhenAny%2A> 方法與 <xref:System.Threading.Tasks.Task.Delay%2A> 方法，如下一節中所述。  
  
### Task.Delay  
 您可以使用 <xref:System.Threading.Tasks.Task.Delay%2A> 方法引入暫停的非同步方法。對於許多功能來說這是非常有用的，包括建置輪詢迴圈和延遲處理使用者在某一預先決定的時間。<xref:System.Threading.Tasks.Task.Delay%2A> 方法也可以與實作等待逾時的 <xref:System.Threading.Tasks.Task.WhenAny%2A> 整合將會更有用。  
  
 如果是較大的非同步作業工作 \(例如， ASP.NET Web 服務\) 的一部分需要很長的時間才能完成，而此作業沒有成功完成的畫，可能會受到相當程度的影響。因此，在等待非同步作業期間，能逾時是很重要的。同步處理 <xref:System.Threading.Tasks.Task.Wait%2A>, <xref:System.Threading.Tasks.Task.%2A> WaitAll?qualifyHint=False&autoUpgrade=True, 和 <xref:System.Threading.Tasks.Task.%2A> WaitAny?qualifyHint=False&autoUpgrade=True 方法時，會接受逾時值，但是相對應的 <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A>\/<xref:System.Threading.Tasks.Task.WhenAny%2A> 和先前提到的 <xref:System.Threading.Tasks.Task.WhenAll%2A>\/<xref:System.Threading.Tasks.Task.WhenAny%2A> 則不能。相反地，您可以使用 <xref:System.Threading.Tasks.Task.Delay%2A> 和 <xref:System.Threading.Tasks.Task.WhenAny%2A> 的結合來實作逾時。  
  
 例如，在您的應用程式 UI，假設您想要下載影像並同時停用 UI 。  不過，如果下載時間太長，您想要重新啟用 UI 並捨棄下載:  
  
```csharp  
public async  void btnDownload_Click(object sender, EventArgs e)  
{  
    btnDownload.Enabled = false;  
    try  
    {  
        Task<Bitmap> download = GetBitmapAsync(url);  
        if (download == await Task.WhenAny(download, Task.Delay(3000)))  
        {  
            Bitmap bmp = await download;  
            pictureBox.Image = bmp;  
            status.Text = “Downloaded”;  
        }  
        else  
        {  
            pictureBox.Image = null;  
            status.Text = “Timed out”;  
            var ignored = download.ContinueWith(  
                t => Trace(“Task finally completed”));  
        }  
    }  
    finally { btnDownload.Enabled = true; }  
}  
  
```  
  
 因為 <xref:System.Threading.Tasks.Task.WhenAll%2A> 傳回一工作的關係，相同的可以應用在多個下載  
  
```csharp  
public async  void btnDownload_Click(object sender, RoutedEventArgs e)  
{  
    btnDownload.Enabled = false;  
    try  
    {  
        Task<Bitmap[]> downloads =   
            Task.WhenAll(from url in urls select GetBitmapAsync(url));  
        if (downloads == await Task.WhenAny(downloads, Task.Delay(3000)))  
        {  
            foreach(var bmp in downloads) panel.AddImage(bmp);  
            status.Text = “Downloaded”;  
        }  
        else  
        {  
            status.Text = “Timed out”;  
            downloads.ContinueWith(t => Log(t));  
        }  
    }  
    finally { btnDownload.Enabled = true; }  
}  
  
```  
  
## 建置工作為基礎的結合器  
 因為工作可以完全代表一非同步作業 \(Asynchronous Operation\) 和藉由指定聯結提供同步和非同步功能與作業，擷取其結果等等，您可以建立combinators 有用的程式庫來建構更大的工作模式。如上一節所述， .NET Framework 包括數個內建 combinators，不過，您也可以建立自己的控制項。  下列章節提供多個可能會使用的 combinator 方法和型別的範例。  
  
### RetryOnFault  
 在大部分情況下，如果先前嘗試失敗，您可能想要重試作業。如需同步處理程式碼，您可以在接下來的範例中建置一個協助程式方法 \(例如 `RetryOnFault` :  
  
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
  
 您可以建立一個與非同步作業中以TAP實作且會傳回工作的方法幾乎相同的協助程式方法:  
  
```csharp  
public static async  Task<T> RetryOnFault<T>(  
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
  
 您可以使用這 combinator 編碼並重新載入應用程式的邏輯，例如:  
  
```csharp  
// Download the URL, trying up to three times in case of failure  
string pageContents = await RetryOnFault(  
    () => DownloadStringAsync(url), 3);  
  
```  
  
 您可以進一步延伸 `RetryOnFault` 函式。  例如，函式可接受 `Func<Task>` ，而此會在重新判斷是否在執行作業時會被引發，例如:  
  
```csharp  
public static async  Task<T> RetryOnFault<T>(  
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
  
 您可以使用下列函式，在重試作業前等待一秒:  
  
```csharp  
// Download the URL, trying up to three times in case of failure,  
// and delaying for a second between retries  
string pageContents = await RetryOnFault(  
    () => DownloadStringAsync(url), 3, () => Task.Delay(1000));  
  
```  
  
### NeedOnlyOne  
 在某些情況下，您可以利用冗位來改善作業的延遲，並且意外成功。考慮提供股價的多個 Web 服務，不過，一天幾次，每個服務可能都會提供不同的品質標準和回應時間。若要處理這些計算時，您可以向所有的Web 服務發出要求，並且當您從某一個取得回應後，取消其他剩餘的要求。您可以實作協助程式函式，來使實作啟動多個作業，等待任何移除，然後取消剩餘的這個通用模式更加輕鬆。  在下列範例中的 `NeedOnlyOne` 函式來說明這種情況:  
  
```csharp  
public static async  Task<T> NeedOnlyOne(  
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
  
 您可以使用這個函式:  
  
```csharp  
double currentPrice = await NeedOnlyOne(  
    ct => GetCurrentPriceFromServer1Async(“msft”, ct),  
    ct => GetCurrentPriceFromServer2Async(“msft”, ct),  
    ct => GetCurrentPriceFromServer3Async(“msft”, ct));  
```  
  
### 交錯作業  
 當您有非常大的工作量時，使用 <xref:System.Threading.Tasks.Task.WhenAny%2A> 方法來支援跨案例，但此會有潛在的效能問題。對 <xref:System.Threading.Tasks.Task.WhenAny%2A> 的每個呼叫都會導致繼續移至每項工作註冊。  如需 N 個工作，則在跨作業的生命期中，會產生 O \(N2\) 個接續。如果您有很大量的工作，您可以使用 combinator \(如下列範例所示的`Interleaved` \) 來解決效能問題：  
  
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
  
 您可以在工作完成時，使用 combinator 來處理結果;例如:  
  
```csharp  
IEnumerable<Task<int>> tasks = ...;  
foreach(var task in Interleaved(tasks))  
{  
    int result = await task;  
    …  
}  
```  
  
### WhenAllOrFirstException  
 在某些散佈\-收集式案例中，您可以等待一個集中的所有任務，除非其中有錯誤，在這種情況下您想要停止等候時就會發生例外狀況。您可以達成此目的，藉由使用該 combinator 方法 \(如下列範例中的 `WhenAllOrFirstException` :  
  
```csharp  
public static Task<T[]> WhenAllOrFirstException<T>(IEnumerable<Task<T>> tasks)  
{  
    var inputs = tasks.ToList();  
    var ce = new CountdownEvent(inputs.Count);  
    var tcs = new TaskCompletionSource<T[]>();  
  
    Action<Task> onCompleted = (Task completed) =>  
    {  
        if (completed.IsFaulted)   
            tcs.TrySetException(completed.Exception.InnerExceptions);  
        if (ce.Signal() && !tcs.Task.IsCompleted)  
            tcs.TrySetResult(inputs.Select(t => t.Result).ToArray());  
    };  
  
    foreach (var t in inputs) t.ContinueWith(onCompleted);  
    return tcs.Task;  
}  
  
```  
  
## 建置工作為基礎的資料結構  
 除了能夠建置自訂工作的 combinators外，有其資料結構在 <xref:System.Threading.Tasks.Task> ，和 <xref:System.Threading.Tasks.Task%601> ，此具有表示非同步作業的結果和必要的同步處理聯結結果，因此擁有一個建立於非同步案例中的自訂資料結構 的強大型別。  
  
### AsyncCache  
 對一個工作而言，有一個非常重要的面向，那就是他可以分配給許多使用者，且他們全部都在等待註冊延遲，並取得它的結果 \(如果是<xref:System.Threading.Tasks.Task%601>\) 或例外狀況等等。這使 <xref:System.Threading.Tasks.Task> 和 <xref:System.Threading.Tasks.Task%601> 非常適合於使用在非同步快取基礎結構中。這是個小但強大且建置在 <xref:System.Threading.Tasks.Task%601>上方的非同步快取範例，:  
  
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
  
 做為委派的 [AsyncCache\<TKey， TValue\>](http://go.microsoft.com/fwlink/p/?LinkId=251941) 類別接受其建構函式中使用 `TKey` 並傳回 <xref:System.Threading.Tasks.Task%601>的函式。從先前儲存在內部字典中快取的值，和`AsyncCache` 是在確保即使快取在同一時間做存取，仍然只有一個工作會產生金鑰。  
  
 例如，您可以建立一個下載網頁的快取:  
  
```csharp  
private AsyncCache<string,string> m_webPages =   
    new AsyncCache<string,string>(DownloadStringAsync);  
  
```  
  
 您可以隨時在非同步方法中使用此快取。  `AsyncCache` 類別可確保您下載越少越好網頁，並快取結果。  
  
```csharp  
private async  void btnDownload_Click(object sender, RoutedEventArgs e)   
{  
    btnDownload.IsEnabled = false;  
    try  
    {  
        txtContents.Text = await m_webPages["http://www.microsoft.com"];  
    }  
    finally { btnDownload.IsEnabled = true; }  
}  
  
```  
  
### AsyncProducerConsumerCollection  
 您也可以使用工作來建置協調非同步活動的資料結構。請考慮其中一種傳統的平行設計模式： 產生者\/取用者。在這個模式，生產者產生消費者使用的資料，因此，生產者和消費者可以平行執行。  例如，消費者處理項目 1，先前由現在產生項目 2的生產者所產生。對於生產者\/消費者模式，您不需要變更一些資料結構儲存生產者建立的工作，以便消費者可以被告知新資料，並在可用時尋找之。  
  
 以下是在任務上建立簡單的資料結構，可讓非同步方法用在產生者和消費者：  
  
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
  
 有此適當的資料結構，您可以撰寫下列程式碼:  
  
```csharp  
private static AsyncProducerConsumerCollection<int> m_data = …;  
…  
private static async  Task ConsumerAsync()  
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
  
 <xref:System.Threading.Tasks.Dataflow> 命名空間包含 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 型別，您可以用類似的方式來使用，而不需要建立自訂集合型別:  
  
```csharp  
private static BufferBlock<int> m_data = …;  
…  
private static async  Task ConsumerAsync()  
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
>  <xref:System.Threading.Tasks.Dataflow> 命名空間可在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 透過 \[**NuGet**\]使用。  若要安裝包含 <xref:System.Threading.Tasks.Dataflow> 命名空間的組件中，請在 [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]中開啟您的專案，請從專案功能表選取 \[**處理 NuGet 套件**\] ，並在線上搜尋 Microsoft.Tpl.Dataflow 封裝。  
  
## 請參閱  
 [Task\-based Asynchronous Pattern \(TAP\)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)   
 [Implementing the Task\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)   
 [Interop with Other Asynchronous Patterns and Types](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)