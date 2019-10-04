---
title: 將 WCF 雙工服務遷移至 WCF 開發人員的 gRPC-gRPC
description: 瞭解如何將各種形式的 WCF 雙工服務遷移至 gRPC 串流服務。
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 525dc3006c45f773242ab08b112dba72087a2e3f
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834512"
---
# <a name="migrate-wcf-duplex-services-to-grpc"></a><span data-ttu-id="482ab-103">將 WCF 雙面服務移轉至 gRPC</span><span class="sxs-lookup"><span data-stu-id="482ab-103">Migrate WCF duplex services to gRPC</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="482ab-104">現在基本概念已就緒，本節將探討更複雜的*串流*gRPC 服務。</span><span class="sxs-lookup"><span data-stu-id="482ab-104">Now that the basic concepts are in place, this section will look at the more complicated *streaming* gRPC services.</span></span>

<span data-ttu-id="482ab-105">有多種方式可以在 Windows Communication Foundation （WCF）中使用雙工服務。</span><span class="sxs-lookup"><span data-stu-id="482ab-105">There are multiple ways to use duplex services in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="482ab-106">某些服務是由用戶端起始，然後從伺服器串流資料。</span><span class="sxs-lookup"><span data-stu-id="482ab-106">Some services are initiated by the client and then they stream data from the server.</span></span> <span data-ttu-id="482ab-107">其他全雙工服務可能牽涉到更多進行中的雙向通訊，例如 WCF 檔中的傳統「計算機」範例。</span><span class="sxs-lookup"><span data-stu-id="482ab-107">Other full-duplex services might involve more ongoing two-way communication like the classic "Calculator" example from the WCF documentation.</span></span> <span data-ttu-id="482ab-108">本章將採用兩個可能的 WCF 「股票行情指示器」，並將其遷移至 gRPC：一個使用伺服器串流 RPC，另一個使用雙向串流 RPC。</span><span class="sxs-lookup"><span data-stu-id="482ab-108">This chapter will take two possible WCF "Stock Ticker" implementations and migrate them to gRPC: one using a server streaming RPC, and the other one using a bidirectional streaming RPC.</span></span>

## <a name="server-streaming-rpc"></a><span data-ttu-id="482ab-109">伺服器串流 RPC</span><span class="sxs-lookup"><span data-stu-id="482ab-109">Server streaming RPC</span></span>

<span data-ttu-id="482ab-110">在[範例 SIMPLESTOCKTICKER WCF 方案](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/SimpleStockTickerSample/wcf/SimpleStockTicker) *SimpleStockPriceTicker*中，有一個雙工服務，其中用戶端會使用內建符號清單來啟動連線，而伺服器會使用*回呼介面*來傳送更新可供使用。</span><span class="sxs-lookup"><span data-stu-id="482ab-110">In the [sample SimpleStockTicker WCF solution](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/SimpleStockTickerSample/wcf/SimpleStockTicker), *SimpleStockPriceTicker*, there's a duplex service where the client starts the connection with a list of stock symbols, and the server uses the *callback interface* to send updates as they become available.</span></span> <span data-ttu-id="482ab-111">用戶端會執行該介面，以回應來自伺服器的呼叫。</span><span class="sxs-lookup"><span data-stu-id="482ab-111">The client implements that interface to respond to calls from the server.</span></span>

### <a name="the-wcf-solution"></a><span data-ttu-id="482ab-112">WCF 解決方案</span><span class="sxs-lookup"><span data-stu-id="482ab-112">The WCF solution</span></span>

<span data-ttu-id="482ab-113">在 .NET Framework 4.x 主控台應用程式中，WCF 解決方案會實作為自我裝載的 NetTCP 伺服器。</span><span class="sxs-lookup"><span data-stu-id="482ab-113">The WCF solution is implemented as a self-hosted NetTCP server in a .NET Framework 4.x console application.</span></span>

#### <a name="the-servicecontract"></a><span data-ttu-id="482ab-114">ServiceContract</span><span class="sxs-lookup"><span data-stu-id="482ab-114">The ServiceContract</span></span>

```csharp
[ServiceContract(SessionMode = SessionMode.Required, CallbackContract = typeof(ISimpleStockTickerCallback))]
public interface ISimpleStockTickerService
{
    [OperationContract(IsOneWay = true)]
    void Subscribe(string[] symbols);
}
```

<span data-ttu-id="482ab-115">服務具有不具有傳回類型的單一方法，因為它會使用回呼介面`ISimpleStockTickerCallback` ，即時將資料傳送至用戶端。</span><span class="sxs-lookup"><span data-stu-id="482ab-115">The service has a single method with no return type, because it will be using the callback interface `ISimpleStockTickerCallback` to send data to the client in real time.</span></span>

#### <a name="the-callback-interface"></a><span data-ttu-id="482ab-116">回呼介面</span><span class="sxs-lookup"><span data-stu-id="482ab-116">The callback interface</span></span>

```csharp
[ServiceContract]
public interface ISimpleStockTickerCallback
{
    [OperationContract(IsOneWay = true)]
    void Update(string symbol, decimal price);
}
```

<span data-ttu-id="482ab-117">您可以在解決方案中找到這些介面的執行，以及偽造的外部相依性，以提供測試資料。</span><span class="sxs-lookup"><span data-stu-id="482ab-117">The implementations of these interfaces can be found in the solution, along with faked external dependencies to provide test data.</span></span>

### <a name="grpc-streaming"></a><span data-ttu-id="482ab-118">gRPC 串流</span><span class="sxs-lookup"><span data-stu-id="482ab-118">gRPC streaming</span></span>

<span data-ttu-id="482ab-119">處理即時資料的 gRPC 方式不同。</span><span class="sxs-lookup"><span data-stu-id="482ab-119">The gRPC way of handling real-time data is different.</span></span> <span data-ttu-id="482ab-120">從用戶端到伺服器的呼叫可以建立持續性資料流程，可以針對以非同步方式到達的訊息進行監視。</span><span class="sxs-lookup"><span data-stu-id="482ab-120">A call from client to server can create a persistent stream, which can be monitored for messages arriving asynchronously.</span></span> <span data-ttu-id="482ab-121">雖然不同，資料流程可以是更直覺的方式來處理這項資料，而且在現代化的程式設計上更具相關性，並著重于 LINQ、回應式資料流程、功能性程式設計等等。</span><span class="sxs-lookup"><span data-stu-id="482ab-121">Despite the difference, streams can be a more intuitive way of dealing with this data and are more relevant in modern programming with the emphasis on LINQ, Reactive Streams, functional programming, and so on.</span></span>

<span data-ttu-id="482ab-122">服務定義需要兩個訊息：一個用於要求，另一個用於資料流程。</span><span class="sxs-lookup"><span data-stu-id="482ab-122">The service definition needs two messages: one for the request, and one for the stream.</span></span> <span data-ttu-id="482ab-123">服務會在其`StockTickerUpdate` `return`宣告中使用關鍵字， `stream`以傳回訊息的資料流程。</span><span class="sxs-lookup"><span data-stu-id="482ab-123">The service returns a stream of the `StockTickerUpdate` message using the `stream` keyword in its `return` declaration.</span></span> <span data-ttu-id="482ab-124">建議您將新增`Timestamp`至更新，以顯示價格變更的確切時間。</span><span class="sxs-lookup"><span data-stu-id="482ab-124">It's recommended that you add a `Timestamp` to the update to show the exact time the price changed.</span></span>

#### <a name="simple_stock_tickerproto"></a><span data-ttu-id="482ab-125">simple_stock_ticker. proto</span><span class="sxs-lookup"><span data-stu-id="482ab-125">simple_stock_ticker.proto</span></span>

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
  int32 priceCents = 2;
  google.protobuf.Timestamp time = 3;
}
```

### <a name="implement-the-simplestockticker"></a><span data-ttu-id="482ab-126">執行 SimpleStockTicker</span><span class="sxs-lookup"><span data-stu-id="482ab-126">Implement the SimpleStockTicker</span></span>

<span data-ttu-id="482ab-127">將`TraderSys.StockMarket`類別庫`StockPriceSubscriber`中的三個類別複製到目標方案中的新 .NET Standard 類別庫，以重複使用 WCF 專案中的假。</span><span class="sxs-lookup"><span data-stu-id="482ab-127">Reuse the fake `StockPriceSubscriber` from the WCF project by copying the three classes from the `TraderSys.StockMarket` class library into a new .NET Standard class library in the target solution.</span></span> <span data-ttu-id="482ab-128">若要進一步遵循最佳做法，請`Factory`新增類型來建立其實例，並向`IStockPriceSubscriberFactory` ASP.NET Core 的相依性插入服務註冊。</span><span class="sxs-lookup"><span data-stu-id="482ab-128">To better follow best practices, add a `Factory` type to create instances of it and register the `IStockPriceSubscriberFactory` with ASP.NET Core's dependency injection services.</span></span>

#### <a name="the-factory-implementation"></a><span data-ttu-id="482ab-129">Factory 的執行</span><span class="sxs-lookup"><span data-stu-id="482ab-129">The factory implementation</span></span>

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

#### <a name="registering-the-factory"></a><span data-ttu-id="482ab-130">註冊 factory</span><span class="sxs-lookup"><span data-stu-id="482ab-130">Registering the factory</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddGrpc();
    services.AddSingleton<IStockPriceSubscriberFactory, StockPriceSubscriberFactory>();
}
```

<span data-ttu-id="482ab-131">現在，這個類別可以用來執行 gRPC StockTicker 服務。</span><span class="sxs-lookup"><span data-stu-id="482ab-131">Now, this class can be used to implement the gRPC StockTicker service.</span></span>

#### <a name="stocktickerservicecs"></a><span data-ttu-id="482ab-132">StockTickerService.cs</span><span class="sxs-lookup"><span data-stu-id="482ab-132">StockTickerService.cs</span></span>

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
            // Handle any errors due to broken connection etc.
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

<span data-ttu-id="482ab-133">如您所見，雖然檔案中`.proto`的宣告指出方法會「傳回」 `StockTickerUpdate`訊息的資料流程，事實上它會傳回 vanilla `Task`。</span><span class="sxs-lookup"><span data-stu-id="482ab-133">As you can see, although the declaration in the `.proto` file says the method "returns" a stream of `StockTickerUpdate` messages, in fact it returns a vanilla `Task`.</span></span> <span data-ttu-id="482ab-134">建立資料流程的作業是由產生的程式碼和 gRPC 執行時間程式庫（可提供`IServerStreamWriter<StockTickerUpdate>`回應資料流程）來處理，以供使用。</span><span class="sxs-lookup"><span data-stu-id="482ab-134">The job of creating the stream is handled by the generated code and the gRPC runtime libraries, which provide the `IServerStreamWriter<StockTickerUpdate>` response stream, ready to use.</span></span>

<span data-ttu-id="482ab-135">不同于 WCF 雙工服務，在連接開啟時，服務類別的實例會保持運作狀態，而 gRPC 服務則會使用傳回的工作來保持服務的運作狀態。</span><span class="sxs-lookup"><span data-stu-id="482ab-135">Unlike a WCF duplex service, where the instance of the service class is kept alive while the connection is open, the gRPC service uses the returned Task to keep the service alive.</span></span> <span data-ttu-id="482ab-136">工作不應完成，直到連接關閉為止。</span><span class="sxs-lookup"><span data-stu-id="482ab-136">The Task shouldn't complete until the connection is closed.</span></span>

<span data-ttu-id="482ab-137">服務可以使用`CancellationToken` `ServerCallContext`從來判斷用戶端已關閉連接的時機。</span><span class="sxs-lookup"><span data-stu-id="482ab-137">The service can tell when the client has closed the connection by using the `CancellationToken` from the `ServerCallContext`.</span></span> <span data-ttu-id="482ab-138">簡單的靜態方法`AwaitCancellation`是用來建立在解除標記時完成的工作。</span><span class="sxs-lookup"><span data-stu-id="482ab-138">A simple static method, `AwaitCancellation`, is used to create a Task that completes when the token is canceled.</span></span>

<span data-ttu-id="482ab-139">在方法中，取得並加入事件處理常式，以寫入至回應資料流程。 `StockPriceSubscriber` `Subscribe`</span><span class="sxs-lookup"><span data-stu-id="482ab-139">In the `Subscribe` method, then, get a `StockPriceSubscriber` and add an event handler that writes to the response stream.</span></span> <span data-ttu-id="482ab-140">然後在立即處置`subscriber`之前，等待連接關閉，以防止它嘗試將資料寫入已關閉的資料流程。</span><span class="sxs-lookup"><span data-stu-id="482ab-140">Then wait for the connection to be closed, before immediately disposing the `subscriber` to prevent it trying to write data to the closed stream.</span></span>

<span data-ttu-id="482ab-141">方法有一個`try` 區塊，可`catch`處理將訊息寫入資料流程時可能發生的任何錯誤。 / `WriteUpdateAsync`</span><span class="sxs-lookup"><span data-stu-id="482ab-141">The `WriteUpdateAsync` method has a `try`/`catch` block to handle any errors that might happen when writing a message to the stream.</span></span> <span data-ttu-id="482ab-142">這是透過網路的持續連線中的重要考慮，不論是刻意或因為發生失敗，都可以在任何毫秒中斷。</span><span class="sxs-lookup"><span data-stu-id="482ab-142">This is an important consideration in persistent connections over networks, which could be broken at any millisecond, whether intentionally or because of a failure somewhere.</span></span>

### <a name="using-the-stocktickerservice-from-a-client-application"></a><span data-ttu-id="482ab-143">從用戶端應用程式使用 StockTickerService</span><span class="sxs-lookup"><span data-stu-id="482ab-143">Using the StockTickerService from a client application</span></span>

<span data-ttu-id="482ab-144">遵循上一節中的相同步驟，從`.proto`檔案建立可共用的用戶端類別庫。</span><span class="sxs-lookup"><span data-stu-id="482ab-144">Follow the same steps in the previous section to create a shareable client class library from the `.proto` file.</span></span> <span data-ttu-id="482ab-145">在此範例中，有一個 .NET Core 3.0 主控台應用程式，示範如何使用用戶端。</span><span class="sxs-lookup"><span data-stu-id="482ab-145">In the sample, there's a .NET Core 3.0 console application that demonstrates how to use the client.</span></span>

#### <a name="example-programcs"></a><span data-ttu-id="482ab-146">範例 Program.cs</span><span class="sxs-lookup"><span data-stu-id="482ab-146">Example Program.cs</span></span>

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

<span data-ttu-id="482ab-147">在此情況下， `Subscribe`產生的用戶端上的方法不是非同步。</span><span class="sxs-lookup"><span data-stu-id="482ab-147">In this case, the `Subscribe` method on the generated client isn't asynchronous.</span></span> <span data-ttu-id="482ab-148">資料流程會立即建立並可供使用，因為它`MoveNext`的方法是非同步，而且第一次呼叫它時，必須等到連接正常運作後才會完成。</span><span class="sxs-lookup"><span data-stu-id="482ab-148">The stream is created and usable right away, because its `MoveNext` method is asynchronous and the first time it's called it won't complete until the connection is alive.</span></span>

<span data-ttu-id="482ab-149">資料流程會傳遞至非同步`DisplayAsync`方法; 接著，應用程式會等待使用者按下某個按鍵，然後取消該`DisplayAsync`方法並等候工作完成後再結束。</span><span class="sxs-lookup"><span data-stu-id="482ab-149">The stream is passed to an async `DisplayAsync` method; the application then waits for the user to press a key, then cancels the `DisplayAsync` method and waits for the task to complete before exiting.</span></span>

> [!NOTE]
> <span data-ttu-id="482ab-150">此程式碼會使用新C#的 8 "using 宣告" 語法來處置資料流程，並在`Main`方法結束時處理通道。</span><span class="sxs-lookup"><span data-stu-id="482ab-150">This code is using the new C# 8 "using declaration" syntax to dispose of the stream and the channel when the `Main` method exits.</span></span> <span data-ttu-id="482ab-151">這是一項很小的變更，但可減少縮排和空白行的好處。</span><span class="sxs-lookup"><span data-stu-id="482ab-151">It's a small change, but a nice one that reduces indentations and empty lines.</span></span>

#### <a name="consume-the-stream"></a><span data-ttu-id="482ab-152">使用資料流程</span><span class="sxs-lookup"><span data-stu-id="482ab-152">Consume the stream</span></span>

<span data-ttu-id="482ab-153">WCF 使用的回呼介面，可讓伺服器直接呼叫用戶端上的方法。</span><span class="sxs-lookup"><span data-stu-id="482ab-153">WCF used callback interfaces to allow the server to call methods directly on the client.</span></span> <span data-ttu-id="482ab-154">gRPC 串流的工作方式不同。</span><span class="sxs-lookup"><span data-stu-id="482ab-154">gRPC streams work differently.</span></span> <span data-ttu-id="482ab-155">用戶端會逐一查看傳回的資料流程並處理訊息，就像是從傳回的本機方法`IEnumerable`傳回的一樣。</span><span class="sxs-lookup"><span data-stu-id="482ab-155">The client iterates over the returned stream and processes messages, just as though they were returned from a local method returning an `IEnumerable`.</span></span>

<span data-ttu-id="482ab-156">類型的運作方式非常`IEnumerator<T>`類似：有一個`MoveNext`方法會在有更多資料時傳回 true，而`Current`屬性則會傳回最新的值。 `IAsyncStreamReader<T>`</span><span class="sxs-lookup"><span data-stu-id="482ab-156">The `IAsyncStreamReader<T>` type works much like an `IEnumerator<T>`: there's a `MoveNext` method that will return true as long as there's more data, and a `Current` property that returns the latest value.</span></span> <span data-ttu-id="482ab-157">唯一的差別在於， `MoveNext`方法`Task<bool>`會傳回，而不是只`bool`傳回。</span><span class="sxs-lookup"><span data-stu-id="482ab-157">The only difference is that the `MoveNext` method returns a `Task<bool>` instead of just a `bool`.</span></span> <span data-ttu-id="482ab-158">擴充方法會將資料流程包裝在標準C#的 8 `IAsyncEnumerable`中，以用於新`await foreach`的語法。 `ReadAllAsync`</span><span class="sxs-lookup"><span data-stu-id="482ab-158">The `ReadAllAsync` extension method wraps the stream in a standard C# 8 `IAsyncEnumerable` that can be used with the new `await foreach` syntax.</span></span>

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
> <span data-ttu-id="482ab-159">本章節結尾的[用戶端程式庫](client-libraries.md#iobservable)一節將探討如何新增擴充方法和類別，以包裝`IAsyncStreamReader<T>`在中，讓開發人員使用回應式的程式`IObservable<T>`設計模式。</span><span class="sxs-lookup"><span data-stu-id="482ab-159">The section on [client libraries](client-libraries.md#iobservable) at the end of this chapter looks at how to add an extension method and classes to wrap `IAsyncStreamReader<T>` in an `IObservable<T>` for developers using reactive programming patterns.</span></span>

<span data-ttu-id="482ab-160">同樣地，請小心在此處攔截例外狀況<xref:System.OperationCanceledException> ，因為可能發生網路失敗，以及可避免擲回的，因為程式碼<xref:System.Threading.CancellationToken>使用來中斷迴圈。</span><span class="sxs-lookup"><span data-stu-id="482ab-160">Again, be careful to catch exceptions here because of the possibility of network failure, as well as the <xref:System.OperationCanceledException> that will inevitably be thrown because the code is using a <xref:System.Threading.CancellationToken> to break the loop.</span></span> <span data-ttu-id="482ab-161">型別有許多關於 gRPC 執行時間錯誤的實用資訊， `StatusCode`包括。 `RpcException`</span><span class="sxs-lookup"><span data-stu-id="482ab-161">The `RpcException` type has a lot of useful information about gRPC runtime errors, including the `StatusCode`.</span></span> <span data-ttu-id="482ab-162">如需詳細資訊，請參閱[第4章中的*錯誤處理*](error-handling.md)。</span><span class="sxs-lookup"><span data-stu-id="482ab-162">For more information, see [*Error handling* in Chapter 4](error-handling.md).</span></span>

## <a name="bidirectional-streaming"></a><span data-ttu-id="482ab-163">雙向串流</span><span class="sxs-lookup"><span data-stu-id="482ab-163">Bidirectional streaming</span></span>

<span data-ttu-id="482ab-164">WCF 全雙工服務可雙向進行非同步即時訊息傳遞。</span><span class="sxs-lookup"><span data-stu-id="482ab-164">A WCF full-duplex service allows for asynchronous, real-time messaging in both directions.</span></span> <span data-ttu-id="482ab-165">在伺服器串流範例中，用戶端會啟動要求，然後接收更新的串流。</span><span class="sxs-lookup"><span data-stu-id="482ab-165">In the server streaming example, the client starts a request, then receives a stream of updates.</span></span> <span data-ttu-id="482ab-166">該服務的較佳版本可讓用戶端在清單中新增和移除股票，而不需要停止和建立新的訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="482ab-166">A better version of that service would allow the client to add and remove stocks from the list without having to stop and create a new subscription.</span></span> <span data-ttu-id="482ab-167">該功能已在[FullStockTicker 範例解決方案](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/wcf/FullStockTicker)中執行。</span><span class="sxs-lookup"><span data-stu-id="482ab-167">That functionality has been implemented in the [FullStockTicker sample solution](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/wcf/FullStockTicker).</span></span>

<span data-ttu-id="482ab-168">`IFullStockTickerService`介面提供三種方法：</span><span class="sxs-lookup"><span data-stu-id="482ab-168">The `IFullStockTickerService` interface provides three methods:</span></span>

- <span data-ttu-id="482ab-169">`Subscribe`啟動連接。</span><span class="sxs-lookup"><span data-stu-id="482ab-169">`Subscribe` starts the connection.</span></span>
- <span data-ttu-id="482ab-170">`AddSymbol`新增要監看的股票符號。</span><span class="sxs-lookup"><span data-stu-id="482ab-170">`AddSymbol` adds a stock symbol to watch.</span></span>
- <span data-ttu-id="482ab-171">`RemoveSymbol`從監看清單中移除符號。</span><span class="sxs-lookup"><span data-stu-id="482ab-171">`RemoveSymbol` removes a symbol from the watched list.</span></span>

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

<span data-ttu-id="482ab-172">回呼介面保持不變。</span><span class="sxs-lookup"><span data-stu-id="482ab-172">The callback interface remains the same.</span></span>

<span data-ttu-id="482ab-173">在 gRPC 中執行此模式較不簡單，因為現在有兩個數據串流會傳遞訊息：一個是從用戶端到伺服器，另一個則是從伺服器到用戶端。</span><span class="sxs-lookup"><span data-stu-id="482ab-173">Implementing this pattern in gRPC is less straightforward, because there are now two streams of data with messages being passed: one from client to server, and another from server to client.</span></span> <span data-ttu-id="482ab-174">您無法使用多個方法來執行新增和移除作業，但是可以在單一資料流程上傳遞多個類型的訊息，方法是使用[第3章](protobuf-any-oneof.md)所`Any`涵蓋的`oneof`類型或關鍵字。</span><span class="sxs-lookup"><span data-stu-id="482ab-174">It isn't possible to use multiple methods to implement the Add and Remove operation, but more than one type of message can be passed on a single stream, using either the `Any` type or `oneof` keyword, which were covered in [Chapter 3](protobuf-any-oneof.md).</span></span>

<span data-ttu-id="482ab-175">在有一組可接受的特定類型的情況下， `oneof`是較好的方式。</span><span class="sxs-lookup"><span data-stu-id="482ab-175">For a case where there's a specific set of types that are acceptable, `oneof` is a better way to go.</span></span> <span data-ttu-id="482ab-176">使用可以保存`AddSymbolRequest` 或`RemoveSymbolRequest`的。 `ActionMessage`</span><span class="sxs-lookup"><span data-stu-id="482ab-176">Use an `ActionMessage` that can hold either an `AddSymbolRequest` or a `RemoveSymbolRequest`.</span></span>

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

<span data-ttu-id="482ab-177">宣告採用`ActionMessage`訊息資料流程的雙向串流服務。</span><span class="sxs-lookup"><span data-stu-id="482ab-177">Declare a bi-directional streaming service that takes a stream of `ActionMessage` messages.</span></span>

```protobuf
service FullStockTicker {
  rpc Subscribe (stream ActionMessage) returns (stream StockTickerUpdate);
}
```

<span data-ttu-id="482ab-178">這項服務的實作為與上一個範例`Subscribe`類似，但方法的第一個參數`IAsyncStreamReader<ActionMessage>`現在是，它可以用來處理`Add`和`Remove`要求。</span><span class="sxs-lookup"><span data-stu-id="482ab-178">The implementation for this service is similar to the previous example, except the first parameter of the `Subscribe` method is now an `IAsyncStreamReader<ActionMessage>`, which can be used to handle the `Add` and `Remove` requests.</span></span>

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
        // Handle any errors due to broken connection etc.
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

<span data-ttu-id="482ab-179">GRPC 為我們產生的`Add` `Remove` `null`類別可確保只有其中一個和屬性可以設定，並找出哪一個不是有效的方法來尋找所使用的訊息類型，但還有更好的方法`ActionMessage`.</span><span class="sxs-lookup"><span data-stu-id="482ab-179">The `ActionMessage` class that gRPC has generated for us guarantees that only one of the `Add` and `Remove` properties can be set, and finding which one isn't `null` is a valid way of finding which type of message is used, but there's a better way.</span></span> <span data-ttu-id="482ab-180">程式`enum ActionOneOfCase`代碼產生也會`ActionMessage`在類別中建立，如下所示：</span><span class="sxs-lookup"><span data-stu-id="482ab-180">The code generation also created an `enum ActionOneOfCase` in the `ActionMessage` class, which looks like this:</span></span>

```csharp
public enum ActionOneofCase {
    None = 0,
    Add = 1,
    Remove = 2,
}
```

<span data-ttu-id="482ab-181">物件上的`ActionCase` 屬性`switch`可以與語句搭配使用，以決定要設定的欄位。 `ActionMessage`</span><span class="sxs-lookup"><span data-stu-id="482ab-181">The property `ActionCase` on the `ActionMessage` object can be used with a `switch` statement to determine which field is set.</span></span>

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
> <span data-ttu-id="482ab-182">語句有一個`default`案例，會在遇到未知`ActionOneOfCase`的值時記錄警告。 `switch`</span><span class="sxs-lookup"><span data-stu-id="482ab-182">The `switch` statement has a `default` case that logs a warning if an unknown `ActionOneOfCase` value is encountered.</span></span> <span data-ttu-id="482ab-183">這在表示用戶端正在使用較新版本`.proto`的檔案，而該檔案已新增更多動作時很有用。</span><span class="sxs-lookup"><span data-stu-id="482ab-183">This could be useful in indicating that a client is using a later version of the `.proto` file which has added more actions.</span></span> <span data-ttu-id="482ab-184">這是使用的`switch`原因之一，比`null`在已知的欄位上測試更好。</span><span class="sxs-lookup"><span data-stu-id="482ab-184">This is one reason why using a `switch` is better than testing for `null` on known fields.</span></span>

### <a name="use-the-fullstocktickerservice-from-a-client-application"></a><span data-ttu-id="482ab-185">從用戶端應用程式使用 FullStockTickerService</span><span class="sxs-lookup"><span data-stu-id="482ab-185">Use the FullStockTickerService from a client application</span></span>

<span data-ttu-id="482ab-186">有一個簡單的 .NET Core 3.0 WPF 應用程式，示範如何使用這個更複雜的用戶端。</span><span class="sxs-lookup"><span data-stu-id="482ab-186">There's a simple .NET Core 3.0 WPF application to demonstrate use of this more complex client.</span></span> <span data-ttu-id="482ab-187">您可以[在 GitHub 上](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTicker)找到完整的應用程式。</span><span class="sxs-lookup"><span data-stu-id="482ab-187">The full application can be found [on GitHub](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTicker).</span></span>

<span data-ttu-id="482ab-188">用戶端是在`MainWindowViewModel`類別中使用，它會從相依性插入取得`FullStockTicker.FullStockTickerClient`類型的實例。</span><span class="sxs-lookup"><span data-stu-id="482ab-188">The client is used in the `MainWindowViewModel` class, which gets an instance of the `FullStockTicker.FullStockTickerClient` type from dependency injection.</span></span>

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

<span data-ttu-id="482ab-189">`client.Subscribe()`方法所傳回的物件現在是 gRPC 程式庫類型`AsyncDuplexStreamingCall<TRequest, TResponse>`的實例，它會提供`RequestStream`將要求傳送至伺服器的，以及`ResponseStream`用於處理回應的。</span><span class="sxs-lookup"><span data-stu-id="482ab-189">The object returned by the `client.Subscribe()` method is now an instance of the gRPC library type `AsyncDuplexStreamingCall<TRequest, TResponse>`, which provides a `RequestStream` for sending requests to the server, and a `ResponseStream` for handling responses.</span></span>

<span data-ttu-id="482ab-190">從某些 WPF `ICommand`方法使用要求資料流程來加入和移除符號。</span><span class="sxs-lookup"><span data-stu-id="482ab-190">The request stream is used from some WPF `ICommand` methods to add and remove symbols.</span></span> <span data-ttu-id="482ab-191">針對每個作業，設定`ActionMessage`物件的相關欄位：</span><span class="sxs-lookup"><span data-stu-id="482ab-191">For each operation, set the relevant field on an `ActionMessage` object:</span></span>

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
> <span data-ttu-id="482ab-192">在訊息上設定欄位的值會自動清除先前已設定的所有欄位。`oneof`</span><span class="sxs-lookup"><span data-stu-id="482ab-192">Setting a `oneof` field's value on a message automatically clears any fields that have been previously set.</span></span>

<span data-ttu-id="482ab-193">回應的資料流程會在`async`方法中處理，而傳回的`Task`則會在視窗關閉時保持處置。</span><span class="sxs-lookup"><span data-stu-id="482ab-193">The stream of responses is handled in an `async` method, and the `Task` it returns is held to be disposed when the window is closed.</span></span>

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

### <a name="client-clean-up"></a><span data-ttu-id="482ab-194">用戶端清理</span><span class="sxs-lookup"><span data-stu-id="482ab-194">Client clean-up</span></span>

<span data-ttu-id="482ab-195">當視窗關閉`MainWindowViewModel`並處置（從的`Closed`事件`MainWindow`）時，建議您適當地處置`AsyncDuplexStreamingCall`物件。</span><span class="sxs-lookup"><span data-stu-id="482ab-195">When the window is closed and the `MainWindowViewModel` is disposed (from the `Closed` event of `MainWindow`), it's recommended that you properly dispose the `AsyncDuplexStreamingCall` object.</span></span> <span data-ttu-id="482ab-196">特別的是， `CompleteAsync` `RequestStream`應該呼叫上的方法，以正常關閉伺服器上的資料流程。</span><span class="sxs-lookup"><span data-stu-id="482ab-196">In particular, the `CompleteAsync` method on the `RequestStream` should be called to gracefully close the stream on the server.</span></span> <span data-ttu-id="482ab-197">下列範例顯示範例視圖`DisposeAsync`模型中的方法：</span><span class="sxs-lookup"><span data-stu-id="482ab-197">The following example shows the `DisposeAsync` method from the sample view-model:</span></span>

```csharp
public ValueTask DisposeAsync()
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

<span data-ttu-id="482ab-198">關閉要求資料流程可讓伺服器及時處置自己的資源。</span><span class="sxs-lookup"><span data-stu-id="482ab-198">Closing request streams enables the server to dispose of its own resources in a timely manner.</span></span> <span data-ttu-id="482ab-199">這可以改善服務的效率和擴充性，並避免發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="482ab-199">This improves the efficiency and scalability of services and prevents exceptions.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="482ab-200">[上一頁](migrate-request-reply.md)
>[下一頁](streaming-versus-repeated.md)</span><span class="sxs-lookup"><span data-stu-id="482ab-200">[Previous](migrate-request-reply.md)
[Next](streaming-versus-repeated.md)</span></span>
