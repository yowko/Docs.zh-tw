---
title: 將 WCF 雙工服務遷移至 WCF 開發人員的 gRPC-gRPC
description: 瞭解如何將各種形式的 WCF 雙工服務遷移至 gRPC 串流服務。
ms.date: 09/02/2019
ms.openlocfilehash: 5737f02044ab9e4064f632164db764541a9c4d31
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628536"
---
# <a name="migrate-wcf-duplex-services-to-grpc"></a><span data-ttu-id="247b7-103">將 WCF 雙面服務移轉至 gRPC</span><span class="sxs-lookup"><span data-stu-id="247b7-103">Migrate WCF duplex services to gRPC</span></span>

<span data-ttu-id="247b7-104">既然您已經瞭解基本概念，在本節中，您將探討更複雜的*串流*gRPC 服務。</span><span class="sxs-lookup"><span data-stu-id="247b7-104">Now that you have a sense of the basic concepts, in this section, you'll look at the more complicated *streaming* gRPC services.</span></span>

<span data-ttu-id="247b7-105">有多種方式可以在 Windows Communication Foundation （WCF）中使用雙工服務。</span><span class="sxs-lookup"><span data-stu-id="247b7-105">There are multiple ways to use duplex services in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="247b7-106">某些服務是由用戶端起始，然後從伺服器串流資料。</span><span class="sxs-lookup"><span data-stu-id="247b7-106">Some services are initiated by the client and then they stream data from the server.</span></span> <span data-ttu-id="247b7-107">其他全雙工服務可能牽涉到更多進行中的雙向通訊，例如 WCF 檔中的傳統計算機範例。</span><span class="sxs-lookup"><span data-stu-id="247b7-107">Other full-duplex services might involve more ongoing two-way communication, like the classic Calculator example in the WCF documentation.</span></span> <span data-ttu-id="247b7-108">本章將會採用兩個可能的 WCF 股票行情，並將其遷移至 gRPC：一個使用伺服器串流 RPC，另一個使用雙向串流 RPC。</span><span class="sxs-lookup"><span data-stu-id="247b7-108">This chapter will take two possible WCF stock ticker implementations and migrate them to gRPC: one that uses a server streaming RPC and another one that uses a bidirectional streaming RPC.</span></span>

## <a name="server-streaming-rpc"></a><span data-ttu-id="247b7-109">伺服器串流 RPC</span><span class="sxs-lookup"><span data-stu-id="247b7-109">Server streaming RPC</span></span>

<span data-ttu-id="247b7-110">在[SIMPLESTOCKTICKER WCF 解決方案的範例](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/SimpleStockTickerSample/wcf/SimpleStockTicker)中，SimpleStockPriceTicker 有一個雙工服務，用戶端會使用內建符號清單來啟動連線，而伺服器則會使用*回呼介面*來在更新可用時進行傳送。</span><span class="sxs-lookup"><span data-stu-id="247b7-110">In the [sample SimpleStockTicker WCF solution](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/SimpleStockTickerSample/wcf/SimpleStockTicker), SimpleStockPriceTicker, there's a duplex service for which the client starts the connection with a list of stock symbols, and the server uses the *callback interface* to send updates as they become available.</span></span> <span data-ttu-id="247b7-111">用戶端會執行該介面，以回應來自伺服器的呼叫。</span><span class="sxs-lookup"><span data-stu-id="247b7-111">The client implements that interface to respond to calls from the server.</span></span>

### <a name="the-wcf-solution"></a><span data-ttu-id="247b7-112">WCF 解決方案</span><span class="sxs-lookup"><span data-stu-id="247b7-112">The WCF solution</span></span>

<span data-ttu-id="247b7-113">WCF 解決方案會實作為 .NET Framework 4 中的自我裝載 Net.tcp 伺服器。*x*主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="247b7-113">The WCF solution is implemented as a self-hosted Net.TCP server in a .NET Framework 4.*x* console application.</span></span>

#### <a name="servicecontract"></a><span data-ttu-id="247b7-114">ServiceContract</span><span class="sxs-lookup"><span data-stu-id="247b7-114">ServiceContract</span></span>

```csharp
[ServiceContract(SessionMode = SessionMode.Required, CallbackContract = typeof(ISimpleStockTickerCallback))]
public interface ISimpleStockTickerService
{
    [OperationContract(IsOneWay = true)]
    void Subscribe(string[] symbols);
}
```

<span data-ttu-id="247b7-115">服務具有不具有傳回類型的單一方法，因為它會使用回呼介面 `ISimpleStockTickerCallback`，即時將資料傳送至用戶端。</span><span class="sxs-lookup"><span data-stu-id="247b7-115">The service has a single method with no return type because it uses the callback interface `ISimpleStockTickerCallback` to send data to the client in real time.</span></span>

#### <a name="the-callback-interface"></a><span data-ttu-id="247b7-116">回呼介面</span><span class="sxs-lookup"><span data-stu-id="247b7-116">The callback interface</span></span>

```csharp
[ServiceContract]
public interface ISimpleStockTickerCallback
{
    [OperationContract(IsOneWay = true)]
    void Update(string symbol, decimal price);
}
```

<span data-ttu-id="247b7-117">您可以在方案中找到這些介面的執行，以及偽造的外部相依性來提供測試資料。</span><span class="sxs-lookup"><span data-stu-id="247b7-117">You can find the implementations of these interfaces in the solution, along with faked external dependencies to provide test data.</span></span>

### <a name="grpc-streaming"></a><span data-ttu-id="247b7-118">gRPC 串流</span><span class="sxs-lookup"><span data-stu-id="247b7-118">gRPC streaming</span></span>

<span data-ttu-id="247b7-119">處理即時資料的 gRPC 程式與 WCF 進程不同。</span><span class="sxs-lookup"><span data-stu-id="247b7-119">The gRPC process for handling real-time data is different from the WCF process.</span></span> <span data-ttu-id="247b7-120">從用戶端到伺服器的呼叫可以建立持續性資料流程，可以針對以非同步方式抵達的訊息進行監視。</span><span class="sxs-lookup"><span data-stu-id="247b7-120">A call from client to server can create a persistent stream, which can be monitored for messages that arrive asynchronously.</span></span> <span data-ttu-id="247b7-121">雖然不同，資料流程可以是更直覺的方式來處理這項資料，而且在新式程式設計中更為相關，這強調 LINQ、回應式資料流程、功能性程式設計等等。</span><span class="sxs-lookup"><span data-stu-id="247b7-121">Despite the difference, streams can be a more intuitive way of dealing with this data and are more relevant in modern programming, which emphasizes LINQ, Reactive Streams, functional programming, and so on.</span></span>

<span data-ttu-id="247b7-122">服務定義需要兩個訊息：一個用於要求，另一個用於資料流程。</span><span class="sxs-lookup"><span data-stu-id="247b7-122">The service definition needs two messages: one for the request and one for the stream.</span></span> <span data-ttu-id="247b7-123">服務會傳回其 `return` 宣告中具有 `stream` 關鍵字之 `StockTickerUpdate` 訊息的資料流程。</span><span class="sxs-lookup"><span data-stu-id="247b7-123">The service returns a stream of the `StockTickerUpdate` message with the `stream` keyword in its `return` declaration.</span></span> <span data-ttu-id="247b7-124">我們建議您將 `Timestamp` 新增至更新，以顯示價格變更的確切時間。</span><span class="sxs-lookup"><span data-stu-id="247b7-124">We recommend that you add a `Timestamp` to the update to show the exact time of the price change.</span></span>

#### <a name="simple_stock_tickerproto"></a><span data-ttu-id="247b7-125">simple_stock_ticker. proto</span><span class="sxs-lookup"><span data-stu-id="247b7-125">simple_stock_ticker.proto</span></span>

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

### <a name="implement-simplestockticker"></a><span data-ttu-id="247b7-126">執行 SimpleStockTicker</span><span class="sxs-lookup"><span data-stu-id="247b7-126">Implement SimpleStockTicker</span></span>

<span data-ttu-id="247b7-127">將 `TraderSys.StockMarket` 類別庫中的三個類別複製到目標方案中的新 .NET Standard 類別庫，以重複使用 WCF 專案中的假 `StockPriceSubscriber`。</span><span class="sxs-lookup"><span data-stu-id="247b7-127">Reuse the fake `StockPriceSubscriber` from the WCF project by copying the three classes from the `TraderSys.StockMarket` class library into a new .NET Standard class library in the target solution.</span></span> <span data-ttu-id="247b7-128">若要進一步遵循最佳做法，請新增 `Factory` 類型來建立其實例，並向 ASP.NET Core 相依性插入服務註冊 `IStockPriceSubscriberFactory`。</span><span class="sxs-lookup"><span data-stu-id="247b7-128">To better follow best practices, add a `Factory` type to create instances of it, and register the `IStockPriceSubscriberFactory` with the ASP.NET Core dependency injection services.</span></span>

#### <a name="the-factory-implementation"></a><span data-ttu-id="247b7-129">Factory 的執行</span><span class="sxs-lookup"><span data-stu-id="247b7-129">The factory implementation</span></span>

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

#### <a name="register-the-factory"></a><span data-ttu-id="247b7-130">註冊工廠</span><span class="sxs-lookup"><span data-stu-id="247b7-130">Register the factory</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddGrpc();
    services.AddSingleton<IStockPriceSubscriberFactory, StockPriceSubscriberFactory>();
}
```

<span data-ttu-id="247b7-131">這個類別現在可以用來執行 gRPC `StockTickerService`。</span><span class="sxs-lookup"><span data-stu-id="247b7-131">This class can now be used to implement the gRPC `StockTickerService`.</span></span>

#### <a name="stocktickerservicecs"></a><span data-ttu-id="247b7-132">StockTickerService.cs</span><span class="sxs-lookup"><span data-stu-id="247b7-132">StockTickerService.cs</span></span>

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

<span data-ttu-id="247b7-133">如您所見，雖然 `.proto` 檔案中的宣告指出方法會傳回 `StockTickerUpdate` 訊息的資料流程，但實際上會傳回 `Task`。</span><span class="sxs-lookup"><span data-stu-id="247b7-133">As you can see, although the declaration in the `.proto` file says the method returns a stream of `StockTickerUpdate` messages, it actually returns a `Task`.</span></span> <span data-ttu-id="247b7-134">建立資料流程的作業是由產生的程式碼和 gRPC 執行時間程式庫（可提供 `IServerStreamWriter<StockTickerUpdate>` 回應資料流程）處理，以供使用。</span><span class="sxs-lookup"><span data-stu-id="247b7-134">The job of creating the stream is handled by the generated code and the gRPC runtime libraries, which provide the `IServerStreamWriter<StockTickerUpdate>` response stream, ready to use.</span></span>

<span data-ttu-id="247b7-135">不同于 WCF 雙工服務，在連接開啟時，服務類別的實例會保持運作狀態，而 gRPC 服務則會使用傳回的工作來保持服務的運作狀態。</span><span class="sxs-lookup"><span data-stu-id="247b7-135">Unlike a WCF duplex service, where the instance of the service class is kept alive while the connection is open, the gRPC service uses the returned task to keep the service alive.</span></span> <span data-ttu-id="247b7-136">工作不應完成，直到連接關閉為止。</span><span class="sxs-lookup"><span data-stu-id="247b7-136">The task shouldn't complete until the connection is closed.</span></span>

<span data-ttu-id="247b7-137">服務可以使用 `ServerCallContext`中的 `CancellationToken` 來判斷用戶端何時關閉連接。</span><span class="sxs-lookup"><span data-stu-id="247b7-137">The service can tell when the client has closed the connection by using the `CancellationToken` from the `ServerCallContext`.</span></span> <span data-ttu-id="247b7-138">簡單的靜態方法（`AwaitCancellation`）是用來建立在解除標記時完成的工作。</span><span class="sxs-lookup"><span data-stu-id="247b7-138">A simple static method, `AwaitCancellation`, is used to create a task that completes when the token is canceled.</span></span>

<span data-ttu-id="247b7-139">在 `Subscribe` 方法中，取得 `StockPriceSubscriber` 並加入寫入回應資料流程的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="247b7-139">In the `Subscribe` method, then, get a `StockPriceSubscriber` and add an event handler that writes to the response stream.</span></span> <span data-ttu-id="247b7-140">然後等候連接關閉，然後立即處置 `subscriber`，以防止它嘗試將資料寫入已關閉的資料流程。</span><span class="sxs-lookup"><span data-stu-id="247b7-140">Then wait for the connection to be closed before immediately disposing the `subscriber` to prevent it from trying to write data to the closed stream.</span></span>

<span data-ttu-id="247b7-141">`WriteUpdateAsync` 方法具有 `try`/`catch` 區塊，可處理將訊息寫入至資料流程時可能發生的任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="247b7-141">The `WriteUpdateAsync` method has a `try`/`catch` block to handle any errors that might happen when a message is written to the stream.</span></span> <span data-ttu-id="247b7-142">這項考慮在透過網路的持續性連線中很重要，不論是刻意或因為某處發生故障，都可能會在任何毫秒中斷。</span><span class="sxs-lookup"><span data-stu-id="247b7-142">This consideration is important in persistent connections over networks, which could be broken at any millisecond, whether intentionally or because of a failure somewhere.</span></span>

### <a name="use-stocktickerservice-from-a-client-application"></a><span data-ttu-id="247b7-143">從用戶端應用程式使用 StockTickerService</span><span class="sxs-lookup"><span data-stu-id="247b7-143">Use StockTickerService from a client application</span></span>

<span data-ttu-id="247b7-144">遵循上一節中的相同步驟，從 `.proto` 檔案建立可共用的用戶端類別庫。</span><span class="sxs-lookup"><span data-stu-id="247b7-144">Follow the same steps in the previous section to create a shareable client class library from the `.proto` file.</span></span> <span data-ttu-id="247b7-145">在此範例中，有一個 .NET Core 3.0 主控台應用程式，示範如何使用用戶端。</span><span class="sxs-lookup"><span data-stu-id="247b7-145">In the sample, there's a .NET Core 3.0 console application that demonstrates how to use the client.</span></span>

#### <a name="example-programcs"></a><span data-ttu-id="247b7-146">範例 Program.cs</span><span class="sxs-lookup"><span data-stu-id="247b7-146">Example Program.cs</span></span>

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

<span data-ttu-id="247b7-147">在此情況下，產生的用戶端上的 `Subscribe` 方法不是非同步。</span><span class="sxs-lookup"><span data-stu-id="247b7-147">In this case, the `Subscribe` method on the generated client isn't asynchronous.</span></span> <span data-ttu-id="247b7-148">資料流程會立即建立並可供使用，因為它的 `MoveNext` 方法是非同步，而且第一次呼叫它時，必須等到連接運作後才會完成。</span><span class="sxs-lookup"><span data-stu-id="247b7-148">The stream is created and usable right away because its `MoveNext` method is asynchronous and the first time it's called it won't complete until the connection is alive.</span></span>

<span data-ttu-id="247b7-149">資料流程會傳遞至非同步 `DisplayAsync` 方法。</span><span class="sxs-lookup"><span data-stu-id="247b7-149">The stream is passed to an asynchronous `DisplayAsync` method.</span></span> <span data-ttu-id="247b7-150">應用程式接著會等待使用者按下某個按鍵，然後取消 `DisplayAsync` 方法，並等候工作完成後再結束。</span><span class="sxs-lookup"><span data-stu-id="247b7-150">The application then waits for the user to press a key, and then cancels the `DisplayAsync` method and waits for the task to complete before exiting.</span></span>

> [!NOTE]
> <span data-ttu-id="247b7-151">當 `Main` 方法結束時C# ，此程式碼會使用新的 8 `using` 宣告語法來處置資料流程和通道。</span><span class="sxs-lookup"><span data-stu-id="247b7-151">This code uses the new C# 8 `using` declaration syntax to dispose of the stream and the channel when the `Main` method exits.</span></span> <span data-ttu-id="247b7-152">這是一項很小的變更，但可減少縮排和空白行的好處。</span><span class="sxs-lookup"><span data-stu-id="247b7-152">It's a small change, but a nice one that reduces indentations and empty lines.</span></span>

#### <a name="consume-the-stream"></a><span data-ttu-id="247b7-153">使用資料流程</span><span class="sxs-lookup"><span data-stu-id="247b7-153">Consume the stream</span></span>

<span data-ttu-id="247b7-154">WCF 使用回呼介面，允許伺服器直接在用戶端上呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="247b7-154">WCF uses callback interfaces to allow the server to call methods directly on the client.</span></span> <span data-ttu-id="247b7-155">gRPC 串流的工作方式不同。</span><span class="sxs-lookup"><span data-stu-id="247b7-155">gRPC streams work differently.</span></span> <span data-ttu-id="247b7-156">用戶端會逐一查看傳回的資料流程並處理訊息，就像是從傳回 `IEnumerable`的本機方法傳回的一樣。</span><span class="sxs-lookup"><span data-stu-id="247b7-156">The client iterates over the returned stream and processes messages, just as though they were returned from a local method returning an `IEnumerable`.</span></span>

<span data-ttu-id="247b7-157">`IAsyncStreamReader<T>` 類型的運作方式非常類似于 `IEnumerator<T>`。</span><span class="sxs-lookup"><span data-stu-id="247b7-157">The `IAsyncStreamReader<T>` type works much like an `IEnumerator<T>`.</span></span> <span data-ttu-id="247b7-158">只要有更多資料，`MoveNext` 方法就會傳回 true，而 `Current` 屬性則會傳回最新的值。</span><span class="sxs-lookup"><span data-stu-id="247b7-158">There's a `MoveNext` method that returns true as long as there's more data, and a `Current` property that returns the latest value.</span></span> <span data-ttu-id="247b7-159">唯一的差別在於 `MoveNext` 方法會傳回 `Task<bool>`，而不只是 `bool`。</span><span class="sxs-lookup"><span data-stu-id="247b7-159">The only difference is that the `MoveNext` method returns a `Task<bool>` instead of just a `bool`.</span></span> <span data-ttu-id="247b7-160">`ReadAllAsync` 擴充方法會將資料流程包裝在標準C# 8 `IAsyncEnumerable` 中，以搭配新的 `await foreach` 語法使用。</span><span class="sxs-lookup"><span data-stu-id="247b7-160">The `ReadAllAsync` extension method wraps the stream in a standard C# 8 `IAsyncEnumerable` that can be used with the new `await foreach` syntax.</span></span>

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
> <span data-ttu-id="247b7-161">對於使用回應式程式設計模式的開發人員，本章結尾的[用戶端程式庫](client-libraries.md#iobservable)一節會示範如何加入擴充方法和類別，以將 `IAsyncStreamReader<T>` 包裝在 `IObservable<T>`中。</span><span class="sxs-lookup"><span data-stu-id="247b7-161">For developers using reactive programming patterns, the section on [client libraries](client-libraries.md#iobservable) at the end of this chapter shows how to add an extension method and classes to wrap `IAsyncStreamReader<T>` in an `IObservable<T>`.</span></span>

<span data-ttu-id="247b7-162">同樣地，請務必在此處攔截例外狀況，因為可能發生網路失敗，而且因為程式碼使用 <xref:System.Threading.CancellationToken> 來中斷迴圈，所以可能會擲回 <xref:System.OperationCanceledException>。</span><span class="sxs-lookup"><span data-stu-id="247b7-162">Again, be sure to catch exceptions here because of the possibility of network failure, and because of the <xref:System.OperationCanceledException> that will inevitably be thrown because the code is using a <xref:System.Threading.CancellationToken> to break the loop.</span></span> <span data-ttu-id="247b7-163">`RpcException` 型別有許多關於 gRPC 執行時間錯誤的實用資訊，包括 `StatusCode`。</span><span class="sxs-lookup"><span data-stu-id="247b7-163">The `RpcException` type has a lot of useful information about gRPC runtime errors, including the `StatusCode`.</span></span> <span data-ttu-id="247b7-164">如需詳細資訊，請參閱[第4章中的*錯誤處理*](error-handling.md)。</span><span class="sxs-lookup"><span data-stu-id="247b7-164">For more information, see [*Error handling* in Chapter 4](error-handling.md).</span></span>

## <a name="bidirectional-streaming"></a><span data-ttu-id="247b7-165">雙向串流</span><span class="sxs-lookup"><span data-stu-id="247b7-165">Bidirectional streaming</span></span>

<span data-ttu-id="247b7-166">WCF 全雙工服務可雙向進行非同步即時訊息傳遞。</span><span class="sxs-lookup"><span data-stu-id="247b7-166">A WCF full-duplex service allows for asynchronous, real-time messaging in both directions.</span></span> <span data-ttu-id="247b7-167">在伺服器串流範例中，用戶端會啟動要求，然後接收更新的串流。</span><span class="sxs-lookup"><span data-stu-id="247b7-167">In the server streaming example, the client starts a request and then receives a stream of updates.</span></span> <span data-ttu-id="247b7-168">該服務的較佳版本可讓用戶端在清單中新增和移除股票，而不需要停止和建立新的訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="247b7-168">A better version of that service would allow the client to add and remove stocks from the list without having to stop and create a new subscription.</span></span> <span data-ttu-id="247b7-169">該功能已在[FullStockTicker 範例解決方案](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/wcf/FullStockTicker)中執行。</span><span class="sxs-lookup"><span data-stu-id="247b7-169">That functionality has been implemented in the [FullStockTicker sample solution](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/wcf/FullStockTicker).</span></span>

<span data-ttu-id="247b7-170">`IFullStockTickerService` 介面提供三種方法：</span><span class="sxs-lookup"><span data-stu-id="247b7-170">The `IFullStockTickerService` interface provides three methods:</span></span>

- <span data-ttu-id="247b7-171">`Subscribe` 會啟動連接。</span><span class="sxs-lookup"><span data-stu-id="247b7-171">`Subscribe` starts the connection.</span></span>
- <span data-ttu-id="247b7-172">`AddSymbol` 新增要監看的股票符號。</span><span class="sxs-lookup"><span data-stu-id="247b7-172">`AddSymbol` adds a stock symbol to watch.</span></span>
- <span data-ttu-id="247b7-173">`RemoveSymbol` 從監看清單中移除符號。</span><span class="sxs-lookup"><span data-stu-id="247b7-173">`RemoveSymbol` removes a symbol from the watched list.</span></span>

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

<span data-ttu-id="247b7-174">回呼介面保持不變。</span><span class="sxs-lookup"><span data-stu-id="247b7-174">The callback interface remains the same.</span></span>

<span data-ttu-id="247b7-175">在 gRPC 中執行此模式較不簡單，因為現在有兩個數據串流會傳遞訊息：一個是從用戶端到伺服器，另一個則是從伺服器到用戶端。</span><span class="sxs-lookup"><span data-stu-id="247b7-175">Implementing this pattern in gRPC is less straightforward because there are now two streams of data with messages being passed: one from client to server and another from server to client.</span></span> <span data-ttu-id="247b7-176">您無法使用多個方法來執行新增和移除作業，但是您可以使用 `Any` 類型或 `oneof` 關鍵字（已在[第3章](protobuf-any-oneof.md)中涵蓋），在單一資料流程上傳遞多種類型的訊息。</span><span class="sxs-lookup"><span data-stu-id="247b7-176">It isn't possible to use multiple methods to implement the add and remove operations, but you can pass more than one type of message on a single stream by using either the `Any` type or the `oneof` keyword, which were covered in [Chapter 3](protobuf-any-oneof.md).</span></span>

<span data-ttu-id="247b7-177">在有一組可接受的特定類型的情況下，`oneof` 是較好的方式。</span><span class="sxs-lookup"><span data-stu-id="247b7-177">In a case where there's a specific set of types that are acceptable, `oneof` is a better way to go.</span></span> <span data-ttu-id="247b7-178">使用可保存 `AddSymbolRequest` 或 `RemoveSymbolRequest`的 `ActionMessage`：</span><span class="sxs-lookup"><span data-stu-id="247b7-178">Use an `ActionMessage` that can hold either an `AddSymbolRequest` or a `RemoveSymbolRequest`:</span></span>

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

<span data-ttu-id="247b7-179">宣告取得 `ActionMessage` 訊息資料流程的雙向串流服務：</span><span class="sxs-lookup"><span data-stu-id="247b7-179">Declare a bidirectional streaming service that takes a stream of `ActionMessage` messages:</span></span>

```protobuf
service FullStockTicker {
  rpc Subscribe (stream ActionMessage) returns (stream StockTickerUpdate);
}
```

<span data-ttu-id="247b7-180">這項服務的執行方式與上一個範例相同，不同之處在于 `Subscribe` 方法的第一個參數現在是一個 `IAsyncStreamReader<ActionMessage>`，可以用來處理 `Add` 和 `Remove` 要求：</span><span class="sxs-lookup"><span data-stu-id="247b7-180">The implementation for this service is similar to that of the previous example, except the first parameter of the `Subscribe` method is now an `IAsyncStreamReader<ActionMessage>`, which can be used to handle the `Add` and `Remove` requests:</span></span>

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

<span data-ttu-id="247b7-181">GRPC 所產生的 `ActionMessage` 類別，保證只能設定其中一個 `Add` 和 `Remove` 屬性。</span><span class="sxs-lookup"><span data-stu-id="247b7-181">The `ActionMessage` class that gRPC has generated guarantees that only one of the `Add` and `Remove` properties can be set.</span></span> <span data-ttu-id="247b7-182">尋找哪一個不 `null` 是有效的方式來判斷所使用的訊息類型，但還有更好的方法。</span><span class="sxs-lookup"><span data-stu-id="247b7-182">Finding which one isn't `null` is a valid way to determine which type of message is used, but there's a better way.</span></span> <span data-ttu-id="247b7-183">程式碼產生也會在 `ActionMessage` 類別中建立 `enum ActionOneOfCase`，如下所示：</span><span class="sxs-lookup"><span data-stu-id="247b7-183">The code generation also created an `enum ActionOneOfCase` in the `ActionMessage` class, which looks like this:</span></span>

```csharp
public enum ActionOneofCase {
    None = 0,
    Add = 1,
    Remove = 2,
}
```

<span data-ttu-id="247b7-184">`ActionMessage` 物件上 `ActionCase` 屬性可以與 `switch` 語句搭配使用，以決定要設定的欄位：</span><span class="sxs-lookup"><span data-stu-id="247b7-184">The property `ActionCase` on the `ActionMessage` object can be used with a `switch` statement to determine which field is set:</span></span>

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
> <span data-ttu-id="247b7-185">`switch` 語句有一個 `default` 的案例，它會在遇到未知的 `ActionOneOfCase` 值時記錄警告。</span><span class="sxs-lookup"><span data-stu-id="247b7-185">The `switch` statement has a `default` case that logs a warning if it encounters an unknown `ActionOneOfCase` value.</span></span> <span data-ttu-id="247b7-186">這可能有助於指出用戶端正在使用較新版本的 `.proto` 檔案，該檔案已新增更多動作。</span><span class="sxs-lookup"><span data-stu-id="247b7-186">This could be useful to indicate that a client is using a later version of the `.proto` file that has added more actions.</span></span> <span data-ttu-id="247b7-187">這是使用 `switch` 比測試已知欄位 `null` 更好的原因之一。</span><span class="sxs-lookup"><span data-stu-id="247b7-187">This is one reason why using a `switch` is better than testing for `null` on known fields.</span></span>

### <a name="use-fullstocktickerservice-from-a-client-application"></a><span data-ttu-id="247b7-188">從用戶端應用程式使用 FullStockTickerService</span><span class="sxs-lookup"><span data-stu-id="247b7-188">Use FullStockTickerService from a client application</span></span>

<span data-ttu-id="247b7-189">有一個簡單的 .NET Core 3.0 WPF 應用程式，示範如何使用這個更複雜的用戶端。</span><span class="sxs-lookup"><span data-stu-id="247b7-189">There's a simple .NET Core 3.0 WPF application that demonstrates the use of this more complex client.</span></span> <span data-ttu-id="247b7-190">您可以在[GitHub](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTicker)上找到完整的應用程式。</span><span class="sxs-lookup"><span data-stu-id="247b7-190">You can find the full application on [GitHub](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTicker).</span></span>

<span data-ttu-id="247b7-191">用戶端用於 `MainWindowViewModel` 類別中，它會從相依性插入取得 `FullStockTicker.FullStockTickerClient` 類型的實例：</span><span class="sxs-lookup"><span data-stu-id="247b7-191">The client is used in the `MainWindowViewModel` class, which gets an instance of the `FullStockTicker.FullStockTickerClient` type from dependency injection:</span></span>

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

<span data-ttu-id="247b7-192">`client.Subscribe()` 方法所傳回的物件現在是 gRPC 程式庫類型的實例 `AsyncDuplexStreamingCall<TRequest, TResponse>`，它會提供將要求傳送至伺服器的 `RequestStream`，以及處理回應的 `ResponseStream`。</span><span class="sxs-lookup"><span data-stu-id="247b7-192">The object returned by the `client.Subscribe()` method is now an instance of the gRPC library type `AsyncDuplexStreamingCall<TRequest, TResponse>`, which provides a `RequestStream` for sending requests to the server and a `ResponseStream` for handling responses.</span></span>

<span data-ttu-id="247b7-193">從某些 WPF `ICommand` 方法中，會使用要求資料流程來加入和移除符號。</span><span class="sxs-lookup"><span data-stu-id="247b7-193">The request stream is used from some WPF `ICommand` methods to add and remove symbols.</span></span> <span data-ttu-id="247b7-194">針對每個作業，設定 `ActionMessage` 物件上的相關欄位：</span><span class="sxs-lookup"><span data-stu-id="247b7-194">For each operation, set the relevant field on an `ActionMessage` object:</span></span>

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
> <span data-ttu-id="247b7-195">在訊息上設定 `oneof` 欄位的值時，會自動清除先前設定的任何欄位。</span><span class="sxs-lookup"><span data-stu-id="247b7-195">Setting a `oneof` field's value on a message automatically clears any fields that have been set previously.</span></span>

<span data-ttu-id="247b7-196">回應的資料流程會在 `async` 方法中處理。</span><span class="sxs-lookup"><span data-stu-id="247b7-196">The stream of responses is handled in an `async` method.</span></span> <span data-ttu-id="247b7-197">當視窗關閉時，會保留要處置它所傳回的 `Task`：</span><span class="sxs-lookup"><span data-stu-id="247b7-197">The `Task` it returns is held to be disposed when the window is closed:</span></span>

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

### <a name="client-cleanup"></a><span data-ttu-id="247b7-198">用戶端清除</span><span class="sxs-lookup"><span data-stu-id="247b7-198">Client cleanup</span></span>

<span data-ttu-id="247b7-199">當視窗關閉並處置 `MainWindowViewModel` （從 `MainWindow`的 `Closed` 事件）時，建議您適當地處置 `AsyncDuplexStreamingCall` 物件。</span><span class="sxs-lookup"><span data-stu-id="247b7-199">When the window is closed and the `MainWindowViewModel` is disposed (from the `Closed` event of `MainWindow`), we recommend that you properly dispose the `AsyncDuplexStreamingCall` object.</span></span> <span data-ttu-id="247b7-200">特別是，應該呼叫 `RequestStream` 上的 `CompleteAsync` 方法，以正常地關閉伺服器上的資料流程。</span><span class="sxs-lookup"><span data-stu-id="247b7-200">In particular, the `CompleteAsync` method on the `RequestStream` should be called to gracefully close the stream on the server.</span></span> <span data-ttu-id="247b7-201">這個範例會顯示範例視圖模型中的 `DisposeAsync` 方法：</span><span class="sxs-lookup"><span data-stu-id="247b7-201">This example shows the `DisposeAsync` method from the sample view-model:</span></span>

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

<span data-ttu-id="247b7-202">關閉要求資料流程可讓伺服器及時處置自己的資源。</span><span class="sxs-lookup"><span data-stu-id="247b7-202">Closing request streams enables the server to dispose of its own resources in a timely way.</span></span> <span data-ttu-id="247b7-203">這可以改善服務的效率和擴充性，並避免發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="247b7-203">This improves the efficiency and scalability of services and prevents exceptions.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="247b7-204">[上一頁](migrate-request-reply.md)
>[下一頁](streaming-versus-repeated.md)</span><span class="sxs-lookup"><span data-stu-id="247b7-204">[Previous](migrate-request-reply.md)
[Next](streaming-versus-repeated.md)</span></span>
