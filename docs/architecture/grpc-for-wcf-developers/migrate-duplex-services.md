---
title: 將 wcf 雙工服務遷移至 WCF 開發人員的 gRPC-gRPC
description: 瞭解如何將各種形式的 WCF 雙工服務遷移至 gRPC 串流服務。
ms.date: 12/15/2020
ms.openlocfilehash: 4741e5ad5c12fa358853381d4f2c286add14f8f5
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938022"
---
# <a name="migrate-wcf-duplex-services-to-grpc"></a>將 WCF 雙面服務移轉至 gRPC

既然您已經瞭解基本概念，在本節中，您將探討更複雜的 *串流* gRPC 服務。

有多種方式可在 Windows Communication Foundation (WCF) 中使用雙工服務。 某些服務是由用戶端起始，然後從伺服器串流資料。 其他全雙工服務可能牽涉到更持續的雙向通訊，例如 WCF 檔中的傳統計算機範例。 本章將採用兩個可能的 WCF 股票行情，並將其遷移至 gRPC：一個使用伺服器串流 RPC，另一個則使用雙向串流 RPC。

## <a name="server-streaming-rpc"></a>伺服器串流 RPC

在 [範例 SIMPLESTOCKTICKER WCF 方案](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/SimpleStockTickerSample/wcf/SimpleStockTicker)SimpleStockPriceTicker 中，有一個雙工服務，用戶端會以股票符號清單來開始連線，而且伺服器會使用 *回呼介面* ，在更新可用時傳送更新。 用戶端會執行該介面，以回應來自伺服器的呼叫。

### <a name="the-wcf-solution"></a>WCF 方案

WCF 方案是以 .NET Framework 4 中的自我裝載 Net.tcp 伺服器形式來執行。*x* 主控台應用程式。

#### <a name="servicecontract"></a>ServiceContract

```csharp
[ServiceContract(SessionMode = SessionMode.Required, CallbackContract = typeof(ISimpleStockTickerCallback))]
public interface ISimpleStockTickerService
{
    [OperationContract(IsOneWay = true)]
    void Subscribe(string[] symbols);
}
```

服務有沒有傳回型別的單一方法，因為它會使用回呼介面 `ISimpleStockTickerCallback` 即時傳送資料給用戶端。

#### <a name="the-callback-interface"></a>回呼介面

```csharp
[ServiceContract]
public interface ISimpleStockTickerCallback
{
    [OperationContract(IsOneWay = true)]
    void Update(string symbol, decimal price);
}
```

您可以在方案中找到這些介面的實作為，以及提供測試資料的偽造外部相依性。

### <a name="grpc-streaming"></a>gRPC 串流

處理即時資料的 gRPC 程式與 WCF 處理常式不同。 從用戶端到伺服器的呼叫可以建立持續性資料流程，可針對以非同步方式抵達的訊息進行監視。 儘管有差異，資料流程還是可以更直覺地處理這項資料，而且在新式程式設計方面更有關聯性，其強調 LINQ、被動資料流程、功能性程式設計等等。

服務定義需要兩個訊息：一個用於要求，另一個用於資料流程。 服務會傳回訊息的資料流程， `StockTickerUpdate` 並 `stream` 在其宣告中使用關鍵字 `return` 。 建議您將加入 `Timestamp` 至更新，以顯示價格變更的確切時間。

#### <a name="simple_stock_tickerproto"></a>simple_stock_ticker proto

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.SimpleStockTickerServer.Protos";

import "google/protobuf/timestamp.proto";

package SimpleStockTickerServer;

service SimpleStockTicker {
  rpc Subscribe (SubscribeRequest) returns (stream StockTickerUpdate);
}

message SubscribeRequest {
  repeated string symbols = 1;
}

message StockTickerUpdate {
  string symbol = 1;
  int32 price_cents = 2;
  google.protobuf.Timestamp time = 3;
}
```

### <a name="implement-simplestockticker"></a>執行 SimpleStockTicker

`StockPriceSubscriber`從類別庫將三個類別複製 `TraderSys.StockMarket` 到目標方案中新的 .NET Standard 類別庫，以重複使用 WCF 專案中的假。 若要更妥善遵循最佳作法，請新增 `Factory` 型別來建立它的實例，並向 `IStockPriceSubscriberFactory` ASP.NET Core 的相依性插入服務註冊。

#### <a name="the-factory-implementation"></a>工廠的執行

```csharp
public interface IStockPriceSubscriberFactory
{
    IStockPriceSubscriber GetSubscriber(string[] symbols);
}

public class StockPriceSubscriberFactory : IStockPriceSubscriberFactory
{
    public IStockPriceSubscriber GetSubscriber(string[] symbols)
    {
        return new StockPriceSubscriber(symbols);
    }
}
```

#### <a name="register-the-factory"></a>註冊工廠

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddGrpc();
    services.AddSingleton<IStockPriceSubscriberFactory, StockPriceSubscriberFactory>();
}
```

這個類別現在可以用來執行 gRPC `StockTickerService` 。

#### <a name="stocktickerservicecs"></a>StockTickerService.cs

```csharp
public class StockTickerService : Protos.SimpleStockTicker.SimpleStockTickerBase
{
    private readonly IStockPriceSubscriberFactory _subscriberFactory;

    public StockTickerService(IStockPriceSubscriberFactory subscriberFactory)
    {
        _subscriberFactory = subscriberFactory;
    }

    public override async Task Subscribe(SubscribeRequest request, IServerStreamWriter<StockTickerUpdate> responseStream, ServerCallContext context)
    {
        var subscriber = _subscriberFactory.GetSubscriber(request.Symbols.ToArray());

        subscriber.Update += async (sender, args) =>
            await WriteUpdateAsync(responseStream, args.Symbol, args.Price);

        await AwaitCancellation(context.CancellationToken);
    }

    private async Task WriteUpdateAsync(IServerStreamWriter<StockTickerUpdate> stream, string symbol, decimal price)
    {
        try
        {
            await stream.WriteAsync(new StockTickerUpdate
            {
                Symbol = symbol,
                PriceCents = (int)(price * 100),
                Time = Timestamp.FromDateTimeOffset(DateTimeOffset.UtcNow)
            });
        }
        catch (Exception e)
        {
            // Handle any errors caused by broken connection, etc.
            _logger.LogError($"Failed to write message: {e.Message}");
        }
    }

    private static Task AwaitCancellation(CancellationToken token)
    {
        var completion = new TaskCompletionSource<object>();
        token.Register(() => completion.SetResult(null));
        return completion.Task;
    }
}
```

您可以看到，雖然檔案中的宣告 `.proto` 指出方法會傳回訊息的資料流程 `StockTickerUpdate` ，但實際上會傳回 `Task` 。 建立資料流程的工作是由產生的程式碼和 gRPC 執行時間程式庫（可提供 `IServerStreamWriter<StockTickerUpdate>` 回應資料流程）來處理，可供使用。

不同于 WCF 雙工服務，當連接開啟時，服務類別的實例會保持運作狀態，gRPC 服務會使用傳回的工作，讓服務保持在運作狀態。 在關閉連接之前，工作不應完成。

服務可以使用來自的來分辨用戶端關閉連接的時間 `CancellationToken` `ServerCallContext` 。 簡單的靜態方法 `AwaitCancellation` 是用來建立在解除標記時完成的工作。

`Subscribe`然後，在方法中，取得 `StockPriceSubscriber` 並加入寫入至回應資料流程的事件處理常式。 然後在立即處置之前等候連接關閉， `subscriber` 以防止它嘗試將資料寫入關閉的資料流程。

`WriteUpdateAsync`方法具有 `try` / `catch` 區塊，可處理將訊息寫入資料流程時可能發生的任何錯誤。 這項考慮對於透過網路的持續連線很重要，無論是刻意或因為某處發生失敗，都可能會中斷。

### <a name="use-stocktickerservice-from-a-client-application"></a>從用戶端應用程式使用 StockTickerService

遵循上一節中的相同步驟，從檔案建立可共用的用戶端類別庫 `.proto` 。 在此範例中，有一個 .NET 主控台應用程式會示範如何使用用戶端。

#### <a name="example-programcs"></a>範例 Program.cs

```csharp
class Program
{
    static async Task Main(string[] args)
    {
        using var channel = GrpcChannel.ForAddress("https://localhost:5001");
        var client = new SimpleStockTicker.SimpleStockTickerClient(channel);

        var request = new SubscribeRequest();
        request.Symbols.AddRange(args);

        using var stream = client.Subscribe(request);

        var tokenSource = new CancellationTokenSource();

        var task = DisplayAsync(stream.ResponseStream, tokenSource.Token);

        WaitForExitKey();

        tokenSource.Cancel();
        await task;
    }
}
```

在此情況下， `Subscribe` 產生的用戶端上的方法不是非同步。 資料流程會立即建立並可供使用，因為它的 `MoveNext` 方法是非同步，而且第一次呼叫它將不會完成，直到連接存留為止。

資料流程會傳遞至非同步 `DisplayAsync` 方法。 然後，應用程式會等待使用者按下某個按鍵，然後取消 `DisplayAsync` 方法並等候工作完成後，才會結束。

> [!NOTE]
> 此程式碼會使用新的 c # 8 宣告語法，在 `using` 方法結束時處置資料流程和通道 `Main` 。 這是一項小變更，但可減少縮排和空白行的優點。

#### <a name="consume-the-stream"></a>使用資料流程

WCF 會使用回呼介面，以允許伺服器直接在用戶端上呼叫方法。 gRPC 資料流程的運作方式不同。 用戶端會反復查看傳回的資料流程並處理訊息，就像是從傳回的本機方法傳回 `IEnumerable` 。

此 `IAsyncStreamReader<T>` 類型的運作方式非常類似 `IEnumerator<T>` 。 有一個 `MoveNext` 方法會傳回 true （只要有更多資料），以及傳回 `Current` 最新值的屬性。 唯一的差別在於方法會傳回， `MoveNext` `Task<bool>` 而不是只傳回 `bool` 。 `ReadAllAsync`擴充方法會將資料流程包裝在 `IAsyncEnumerable` 可搭配新語法使用的標準 c # 8 中 `await foreach` 。

```csharp
static async Task DisplayAsync(IAsyncStreamReader<StockTickerUpdate> stream, CancellationToken token)
{
    try
    {
        await foreach (var update in stream.ReadAllAsync(token))
        {
            Console.WriteLine($"{update.Symbol}: {update.Price}");
        }
    }
    catch (RpcException e) when (e.StatusCode == StatusCode.Cancelled)
    {
        return;
    }
    catch (OperationCanceledException)
    {
        Console.WriteLine("Finished.");
    }
}
```

> [!TIP]
> 針對使用回應式程式設計模式的開發人員，本章結尾的 [用戶端程式庫](client-libraries.md#iobservable) 一節會示範如何加入擴充方法和類別，以包裝 `IAsyncStreamReader<T>` 在中 `IObservable<T>` 。

同樣地，請務必在此處攔截例外狀況，因為可能發生網路失敗，而且由於 <xref:System.OperationCanceledException> 程式碼使用 <xref:System.Threading.CancellationToken> 來中斷迴圈，因此不會擲回例外狀況。 `RpcException`型別有許多有關 gRPC 執行階段錯誤的實用資訊，包括 `StatusCode` 。 如需詳細資訊，請參閱 [第4章中的 *錯誤處理*](error-handling.md)。

## <a name="bidirectional-streaming"></a>雙向串流

WCF 全雙工服務可讓您以雙向方式進行非同步即時通訊。 在伺服器串流範例中，用戶端會啟動要求，然後接收更新的資料流程。 這項服務可讓用戶端在清單中新增和移除股票，而不需要停止和建立新的訂用帳戶。 這項功能已在 [FullStockTicker 範例方案](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/wcf/FullStockTicker)中執行。

`IFullStockTickerService`介面提供三種方法：

- `Subscribe` 開始連接。
- `AddSymbol` 新增要監看的股票符號。
- `RemoveSymbol` 移除監看清單中的符號。

```csharp
[ServiceContract(SessionMode = SessionMode.Required, CallbackContract = typeof(IFullStockTickerCallback))]
public interface IFullStockTickerService
{
    [OperationContract(IsOneWay = true)]
    void Subscribe();

    [OperationContract(IsOneWay = true)]
    void AddSymbol(string symbol);

    [OperationContract(IsOneWay = true)]
    void RemoveSymbol(string symbol);
}
```

回呼介面保持不變。

在 gRPC 中執行此模式比較不簡單，因為現在有兩個數據串流正在傳遞訊息：一個是從用戶端到伺服器，另一個則是從伺服器到用戶端。 您無法使用多個方法來執行新增和移除作業，但您可以使用類型或關鍵字在單一資料流程上傳遞多個訊息類型 `Any` `oneof` ，這是在 [第3章](protobuf-any-oneof.md)中所述。

如果有一組可接受的特定類型， `oneof` 則是更好的做法。 使用 `ActionMessage` 可保存 `AddSymbolRequest` 或的 `RemoveSymbolRequest` ：

```protobuf
message ActionMessage {
  oneof action {
    AddSymbolRequest add = 1;
    RemoveSymbolRequest remove = 2;
  }
}

message AddSymbolRequest {
  string symbol = 1;
}

message RemoveSymbolRequest {
  string symbol = 1;
}
```

宣告採用訊息資料流程的雙向串流服務 `ActionMessage` ：

```protobuf
service FullStockTicker {
  rpc Subscribe (stream ActionMessage) returns (stream StockTickerUpdate);
}
```

這項服務的執行方式與上一個範例中的相同，但方法的第一個參數 `Subscribe` 現在是 `IAsyncStreamReader<ActionMessage>` ，可以用來處理 `Add` 和 `Remove` 要求：

```csharp
public override async Task Subscribe(IAsyncStreamReader<ActionMessage> requestStream, IServerStreamWriter<StockTickerUpdate> responseStream, ServerCallContext context)
{
    using var subscriber = _subscriberFactory.GetSubscriber();

    subscriber.Update += async (sender, args) =>
        await WriteUpdateAsync(responseStream, args.Symbol, args.Price);

    var actionsTask = HandleActions(requestStream, subscriber, context.CancellationToken);

    _logger.LogInformation("Subscription started.");
    await AwaitCancellation(context.CancellationToken);

    try { await actionsTask; } catch { /* Ignored */ }

    _logger.LogInformation("Subscription finished.");
}

private async Task WriteUpdateAsync(IServerStreamWriter<StockTickerUpdate> stream, string symbol, decimal price)
{
    try
    {
        await stream.WriteAsync(new StockTickerUpdate
        {
            Symbol = symbol,
            PriceCents = (int)(price * 100),
            Time = Timestamp.FromDateTimeOffset(DateTimeOffset.UtcNow)
        });
    }
    catch (Exception e)
    {
        // Handle any errors caused by broken connection, etc.
        _logger.LogError($"Failed to write message: {e.Message}");
    }
}

private static Task AwaitCancellation(CancellationToken token)
{
    var completion = new TaskCompletionSource<object>();
    token.Register(() => completion.SetResult(null));
    return completion.Task;
}
```

`ActionMessage`GRPC 產生的類別可保證只能 `Add` 設定和屬性的其中一個 `Remove` 。 找出哪一個不 `null` 是有效的方式來判斷要使用哪種類型的訊息，但有更好的方法。 程式碼產生也會 `enum ActionOneOfCase` 在類別中建立，如下所 `ActionMessage` 示：

```csharp
public enum ActionOneofCase {
    None = 0,
    Add = 1,
    Remove = 2,
}
```

`ActionCase`物件上的屬性 `ActionMessage` 可以搭配 `switch` 語句使用，以判斷所設定的欄位：

```csharp
private async Task HandleActions(IAsyncStreamReader<ActionMessage> requestStream, IFullStockPriceSubscriber subscriber, CancellationToken token)
{
    await foreach (var action in requestStream.ReadAllAsync(token))
    {
        switch (action.ActionCase)
        {
            case ActionMessage.ActionOneofCase.None:
                _logger.LogWarning("No Action specified.");
                break;
            case ActionMessage.ActionOneofCase.Add:
                subscriber.Add(action.Add.Symbol);
                break;
            case ActionMessage.ActionOneofCase.Remove:
                subscriber.Remove(action.Remove.Symbol);
                break;
            default:
                _logger.LogWarning($"Unknown Action '{action.ActionCase}'.");
                break;
        }
    }
}
```

> [!TIP]
> `switch` `default` 如果遇到未知值，語句會有記錄警告的情況 `ActionOneOfCase` 。 這可能有助於指出用戶端使用較新版本的檔案，而該檔案 `.proto` 已新增更多動作。 這是使用的原因 `switch` 優於 `null` 在已知欄位上測試的原因之一。

### <a name="use-fullstocktickerservice-from-a-client-application"></a>從用戶端應用程式使用 FullStockTickerService

有一個簡單的 .NET WPF 應用程式，示範如何使用這個更複雜的用戶端。 您可以在 [GitHub](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTicker)上找到完整的應用程式。

用戶端用於 `MainWindowViewModel` 類別中，它會從相依性插入取得型別的實例 `FullStockTicker.FullStockTickerClient` ：

```csharp
public class MainWindowViewModel : IAsyncDisposable, INotifyPropertyChanged
{
    private readonly FullStockTicker.FullStockTickerClient _client;
    private readonly AsyncDuplexStreamingCall<ActionMessage, StockTickerUpdate> _duplexStream;
    private readonly CancellationTokenSource _cancellationTokenSource;
    private readonly Task _responseTask;
    private string _addSymbol;

    public MainWindowViewModel(FullStockTicker.FullStockTickerClient client)
    {
        _cancellationTokenSource = new CancellationTokenSource();
        _client = client;
        _duplexStream = _client.Subscribe();
        _responseTask = HandleResponsesAsync(_cancellationTokenSource.Token);

        AddCommand = new AsyncCommand(Add, CanAdd);
    }
```

方法所傳回的物件 `client.Subscribe()` 現在是 gRPC 程式庫類型的實例 `AsyncDuplexStreamingCall<TRequest, TResponse>` ，它會提供將 `RequestStream` 要求傳送至伺服器的，以及 `ResponseStream` 用於處理回應的。

從某些 WPF 方法使用要求資料流程 `ICommand` 來新增和移除符號。 針對每個作業，在物件上設定相關的欄位 `ActionMessage` ：

```csharp
private async Task Add()
{
    if (CanAdd())
    {
        await _duplexStream.RequestStream.WriteAsync(new ActionMessage {Add = new AddSymbolRequest {Symbol = AddSymbol}});
    }
}

public async Task Remove(PriceViewModel priceViewModel)
{
    await _duplexStream.RequestStream.WriteAsync(new ActionMessage {Remove = new RemoveSymbolRequest {Symbol = priceViewModel.Symbol}});
    Prices.Remove(priceViewModel);
}
```

> [!IMPORTANT]
> `oneof`在訊息上設定欄位的值會自動清除先前設定的任何欄位。

回應的資料流程是在方法中處理 `async` 。 `Task`當視窗關閉時，會保留它所傳回的來處置：

```csharp
private async Task HandleResponsesAsync(CancellationToken token)
{
    var stream = _duplexStream.ResponseStream;

    try
    {
        await foreach (var update in stream.ReadAllAsync(token))
        {
            var price = Prices.FirstOrDefault(p => p.Symbol.Equals(update.Symbol));
            if (price == null)
            {
                price = new PriceViewModel(this) {Symbol = update.Symbol, Price = update.PriceCents / 100m};
                Prices.Add(price);
            }
            else
            {
                price.Price = update.PriceCents / 100m;
            }
        }
    }
    catch (OperationCancelledException) { }
}
```

### <a name="client-cleanup"></a>用戶端清除

當視窗關閉且 `MainWindowViewModel` (從) 的事件處置時 `Closed` `MainWindow` ，我們建議您正確地處置 `AsyncDuplexStreamingCall` 物件。 尤其 `CompleteAsync` 是，應該呼叫上的方法， `RequestStream` 以適當地關閉伺服器上的資料流程。 此範例顯示 `DisposeAsync` 範例視圖模型中的方法：

```csharp
public async ValueTask DisposeAsync()
{
    try
    {
        await _duplexStream.RequestStream.CompleteAsync().ConfigureAwait(false);
        await _responseTask.ConfigureAwait(false);
    }
    finally
    {
        _duplexStream.Dispose();
    }
}
```

關閉要求資料流程可讓伺服器及時處置自己的資源。 這可改善服務的效率和擴充性，並防止例外狀況。

>[!div class="step-by-step"]
>[上一個](migrate-request-reply.md) 
>[下一步](streaming-versus-repeated.md)
