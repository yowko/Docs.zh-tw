---
title: 適用于 WCF 開發人員的 RPC 類型 - gRPC
description: 審查 WCF 支援的遠端程序呼叫的類型及其在 gRPC 中的等效調用
ms.date: 09/02/2019
ms.openlocfilehash: 40c0779dc015904e9dabbb448075e3c5aa5dc49a
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111084"
---
# <a name="types-of-rpc"></a><span data-ttu-id="96c87-103">RPC 類型</span><span class="sxs-lookup"><span data-stu-id="96c87-103">Types of RPC</span></span>

<span data-ttu-id="96c87-104">作為 Windows 通信基礎 （WCF） 開發人員，您可能習慣于處理以下類型的遠端程序呼叫 （RPC）：</span><span class="sxs-lookup"><span data-stu-id="96c87-104">As a Windows Communication Foundation (WCF) developer, you're probably used to dealing with the following types of remote procedure call (RPC):</span></span>

- <span data-ttu-id="96c87-105">請求/回復</span><span class="sxs-lookup"><span data-stu-id="96c87-105">Request/reply</span></span>
- <span data-ttu-id="96c87-106">雙工：</span><span class="sxs-lookup"><span data-stu-id="96c87-106">Duplex:</span></span>
  - <span data-ttu-id="96c87-107">帶會話的單向雙工</span><span class="sxs-lookup"><span data-stu-id="96c87-107">One-way duplex with session</span></span>
  - <span data-ttu-id="96c87-108">帶會話的全雙工</span><span class="sxs-lookup"><span data-stu-id="96c87-108">Full duplex with session</span></span>
- <span data-ttu-id="96c87-109">單向</span><span class="sxs-lookup"><span data-stu-id="96c87-109">One-way</span></span>

<span data-ttu-id="96c87-110">可以自然地將這些 RPC 類型映射到現有的 gRPC 概念。</span><span class="sxs-lookup"><span data-stu-id="96c87-110">It's possible to map these RPC types fairly naturally to existing gRPC concepts.</span></span> <span data-ttu-id="96c87-111">本章將依次介紹每個領域。</span><span class="sxs-lookup"><span data-stu-id="96c87-111">This chapter will look at each of these areas in turn.</span></span> <span data-ttu-id="96c87-112">[第五章](migrate-wcf-to-grpc.md)將更深入地探討類似的例子。</span><span class="sxs-lookup"><span data-stu-id="96c87-112">[Chapter 5](migrate-wcf-to-grpc.md) will explore similar examples in greater depth.</span></span>

| <span data-ttu-id="96c87-113">WCF</span><span class="sxs-lookup"><span data-stu-id="96c87-113">WCF</span></span> | <span data-ttu-id="96c87-114">gRPC</span><span class="sxs-lookup"><span data-stu-id="96c87-114">gRPC</span></span> |
| --- | ---- |
| <span data-ttu-id="96c87-115">定期請求/回復</span><span class="sxs-lookup"><span data-stu-id="96c87-115">Regular request/reply</span></span> | <span data-ttu-id="96c87-116">一元 (Unary)</span><span class="sxs-lookup"><span data-stu-id="96c87-116">Unary</span></span> |
| <span data-ttu-id="96c87-117">使用用戶端回檔介面使用會話的雙工服務</span><span class="sxs-lookup"><span data-stu-id="96c87-117">Duplex service with session using a client callback interface</span></span> | <span data-ttu-id="96c87-118">伺服器流式處理</span><span class="sxs-lookup"><span data-stu-id="96c87-118">Server streaming</span></span> |
| <span data-ttu-id="96c87-119">帶會話的全雙工服務</span><span class="sxs-lookup"><span data-stu-id="96c87-119">Full duplex service with session</span></span> | <span data-ttu-id="96c87-120">雙向流式處理</span><span class="sxs-lookup"><span data-stu-id="96c87-120">Bidirectional streaming</span></span> |
| <span data-ttu-id="96c87-121">單向操作</span><span class="sxs-lookup"><span data-stu-id="96c87-121">One-way operations</span></span> | <span data-ttu-id="96c87-122">用戶端流式處理</span><span class="sxs-lookup"><span data-stu-id="96c87-122">Client streaming</span></span> |

## <a name="requestreply"></a><span data-ttu-id="96c87-123">請求/回復</span><span class="sxs-lookup"><span data-stu-id="96c87-123">Request/reply</span></span>

<span data-ttu-id="96c87-124">對於獲取和返回少量資料的簡單請求/回復方法，請使用最簡單的 gRPC 模式，即一元 RPC。</span><span class="sxs-lookup"><span data-stu-id="96c87-124">For simple request/reply methods that take and return small amounts of data, use the simplest gRPC pattern, the unary RPC.</span></span>

```protobuf
service Things {
    rpc Get(GetThingRequest) returns (GetThingResponse);
}
```

```csharp
public class ThingService : Things.ThingsBase
{
    public override async Task<GetThingResponse> Get(GetThingRequest request, ServerCallContext context)
    {
        // Get thing from database
        return new GetThingResponse { Thing = thing };
    }
}
```

```csharp
public async Task ShowThing(int thingId)
{
    var thing = await _thingsClient.GetAsync(new GetThingRequest { ThingId = thingId });
    Console.WriteLine($"{thing.Name}");
}
```

<span data-ttu-id="96c87-125">如您所見，實現 gRPC 一元 RPC 服務方法類似于實現 WCF 操作。</span><span class="sxs-lookup"><span data-stu-id="96c87-125">As you can see, implementing a gRPC unary RPC service method is similar to implementing a WCF operation.</span></span> <span data-ttu-id="96c87-126">區別在於，使用 gRPC，可以重寫基類方法，而不是實現介面。</span><span class="sxs-lookup"><span data-stu-id="96c87-126">The difference is that with gRPC, you override a base class method instead of implementing an interface.</span></span> <span data-ttu-id="96c87-127">在伺服器上，gRPC 基方法始終返回<xref:System.Threading.Tasks.Task%601>，儘管用戶端同時提供非同步和阻止方法來調用服務。</span><span class="sxs-lookup"><span data-stu-id="96c87-127">On the server, gRPC base methods always return <xref:System.Threading.Tasks.Task%601>, although the client provides both async and blocking methods to call the service.</span></span>

## <a name="wcf-duplex-one-way-to-client"></a><span data-ttu-id="96c87-128">WCF 雙工，用戶端的一種方式</span><span class="sxs-lookup"><span data-stu-id="96c87-128">WCF duplex, one way to client</span></span>

<span data-ttu-id="96c87-129">WCF 應用程式（具有某些綁定）可以在用戶端和伺服器之間創建持久連接。</span><span class="sxs-lookup"><span data-stu-id="96c87-129">WCF applications (with certain bindings) can create a persistent connection between client and server.</span></span> <span data-ttu-id="96c87-130">伺服器可以使用<xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType>屬性中指定的*回檔介面*將資料非同步發送到用戶端，直到連接關閉。</span><span class="sxs-lookup"><span data-stu-id="96c87-130">The server can asynchronously send data to the client until the connection is closed, by using a *callback interface* specified in the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="96c87-131">gRPC 服務提供與消息流類似的功能。</span><span class="sxs-lookup"><span data-stu-id="96c87-131">gRPC services provide similar functionality with message streams.</span></span> <span data-ttu-id="96c87-132">流在實現方面不會*精確*映射到 WCF 雙工服務，但您可以實現相同的結果。</span><span class="sxs-lookup"><span data-stu-id="96c87-132">Streams don't map *exactly* to WCF duplex services in terms of implementation, but you can achieve the same results.</span></span>

### <a name="grpc-streaming"></a><span data-ttu-id="96c87-133">gRPC 流式處理</span><span class="sxs-lookup"><span data-stu-id="96c87-133">gRPC streaming</span></span>

<span data-ttu-id="96c87-134">gRPC 支援創建從用戶端到伺服器以及從伺服器到用戶端的持久流。</span><span class="sxs-lookup"><span data-stu-id="96c87-134">gRPC supports the creation of persistent streams from client to server, and from server to client.</span></span> <span data-ttu-id="96c87-135">這兩種類型的流可以同時處於活動狀態。</span><span class="sxs-lookup"><span data-stu-id="96c87-135">Both types of stream can be active concurrently.</span></span> <span data-ttu-id="96c87-136">此功能稱為雙向流式處理。</span><span class="sxs-lookup"><span data-stu-id="96c87-136">This ability is called bidirectional streaming.</span></span>

<span data-ttu-id="96c87-137">隨著時間的推移，您可以將流用於任意的非同步消息傳遞。</span><span class="sxs-lookup"><span data-stu-id="96c87-137">You can use streams for arbitrary, asynchronous messaging over time.</span></span> <span data-ttu-id="96c87-138">或者，您可以使用它們傳遞太大的大型資料集，無法生成和發送單個請求或回應。</span><span class="sxs-lookup"><span data-stu-id="96c87-138">Or you can use them for passing large datasets that are too big to generate and send in a single request or response.</span></span>

<span data-ttu-id="96c87-139">下面的示例顯示了伺服器流 RPC。</span><span class="sxs-lookup"><span data-stu-id="96c87-139">The following example shows a server-streaming RPC.</span></span>

```protobuf
service ClockStreamer {
    rpc Subscribe(ClockSubscribeRequest) returns (stream ClockMessage);
}
```

```csharp
public class ClockStreamerService : ClockStreamer.ClockStreamerBase
{
    public override async Task Subscribe(ClockSubscribeRequest request,
        IServerStreamWriter<ClockMessage> responseStream,
        ServerCallContext context)
    {
        while (!context.CancellationToken.IsCancellationRequested)
        {
            var time = DateTimeOffset.UtcNow;
            await responseStream.WriteAsync(new ClockMessage { message = $"The time is {time:t}." });
            await Task.Delay(TimeSpan.FromSeconds(10), context.CancellationToken);
        }
    }
}
```

<span data-ttu-id="96c87-140">此伺服器流可以從用戶端應用程式使用，如以下代碼所示：</span><span class="sxs-lookup"><span data-stu-id="96c87-140">This server stream can be consumed from a client application, as shown in the following code:</span></span>

```csharp
public async Task TellTheTimeAsync(CancellationToken token)
{
    var channel = GrpcChannel.ForAddress("https://localhost:5001");
    var client = new ClockStreamer.ClockStreamerClient(channel);

    var request = new ClockSubscribeRequest();
    var response = client.Subscribe(request);

    await foreach (var update in response.ResponseStream.ReadAllAsync(token))
    {
        Console.WriteLine(update.Message);
    }
}
```

> [!NOTE]
> <span data-ttu-id="96c87-141">伺服器流式處理中心對於訂閱樣式的服務很有用。</span><span class="sxs-lookup"><span data-stu-id="96c87-141">Server-streaming RPCs are useful for subscription-style services.</span></span> <span data-ttu-id="96c87-142">當在記憶體中構建整個資料集效率低下或不可能時，它們對於發送大型資料集也很有用。</span><span class="sxs-lookup"><span data-stu-id="96c87-142">They're also useful for sending large datasets when it would be inefficient or impossible to build the entire dataset in memory.</span></span> <span data-ttu-id="96c87-143">但是，流式處理回應不如在一條消息中`repeated`發送欄位快。</span><span class="sxs-lookup"><span data-stu-id="96c87-143">However, streaming responses isn't as fast as sending `repeated` fields in a single message.</span></span> <span data-ttu-id="96c87-144">通常，流式處理不應用於小型資料集。</span><span class="sxs-lookup"><span data-stu-id="96c87-144">As a rule, streaming shouldn't be used for small datasets.</span></span>

### <a name="differences-from-wcf"></a><span data-ttu-id="96c87-145">與 WCF 的差異</span><span class="sxs-lookup"><span data-stu-id="96c87-145">Differences from WCF</span></span>

<span data-ttu-id="96c87-146">WCF 雙工服務使用用戶端回檔介面，該介面可以有多個方法。</span><span class="sxs-lookup"><span data-stu-id="96c87-146">A WCF duplex service uses a client callback interface that can have multiple methods.</span></span> <span data-ttu-id="96c87-147">gRPC 伺服器流服務只能通過單個流發送消息。</span><span class="sxs-lookup"><span data-stu-id="96c87-147">A gRPC server-streaming service can only send messages over a single stream.</span></span> <span data-ttu-id="96c87-148">如果需要多種方法，請使用具有[Any 欄位或欄位之一](protobuf-any-oneof.md)的訊息類型發送不同的消息，並在用戶端中編寫代碼來處理它們。</span><span class="sxs-lookup"><span data-stu-id="96c87-148">If you need multiple methods, use a message type with either [an Any field or a oneof field](protobuf-any-oneof.md) to send different messages, and write code in the client to handle them.</span></span>

<span data-ttu-id="96c87-149">在 WCF 中，具有會話[的服務合同](xref:System.ServiceModel.ServiceContractAttribute)類將保持活動狀態，直到連接關閉。</span><span class="sxs-lookup"><span data-stu-id="96c87-149">In WCF, the [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) class with the session is kept alive until the connection is closed.</span></span> <span data-ttu-id="96c87-150">可以在會話中調用多種方法。</span><span class="sxs-lookup"><span data-stu-id="96c87-150">Multiple methods can be called within the session.</span></span> <span data-ttu-id="96c87-151">在 gRPC`Task`中，在關閉連接之前，實現方法返回的不應完成。</span><span class="sxs-lookup"><span data-stu-id="96c87-151">In gRPC, the `Task` that the implementation method returns shouldn't finish until the connection is closed.</span></span>

## <a name="wcf-one-way-operations-and-grpc-client-streaming"></a><span data-ttu-id="96c87-152">WCF 單向操作和 gRPC 用戶端流</span><span class="sxs-lookup"><span data-stu-id="96c87-152">WCF one-way operations and gRPC client streaming</span></span>

<span data-ttu-id="96c87-153">WCF 提供單向操作（標記為`[OperationContract(IsOneWay = true)]`），返回特定于傳輸的確認。</span><span class="sxs-lookup"><span data-stu-id="96c87-153">WCF provides one-way operations (marked with `[OperationContract(IsOneWay = true)]`) that return a transport-specific acknowledgment.</span></span> <span data-ttu-id="96c87-154">gRPC 服務方法始終返回回應，即使它為空。</span><span class="sxs-lookup"><span data-stu-id="96c87-154">gRPC service methods always return a response, even if it's empty.</span></span> <span data-ttu-id="96c87-155">用戶端應始終等待該回應。</span><span class="sxs-lookup"><span data-stu-id="96c87-155">The client should always await that response.</span></span> <span data-ttu-id="96c87-156">對於 gRPC 中"即用即用"消息傳遞樣式，您可以創建用戶端流服務。</span><span class="sxs-lookup"><span data-stu-id="96c87-156">For the "fire-and-forget" style of messaging in gRPC, you can create a client streaming service.</span></span>

### <a name="thing_logproto"></a><span data-ttu-id="96c87-157">thing_log.proto</span><span class="sxs-lookup"><span data-stu-id="96c87-157">thing_log.proto</span></span>

```protobuf
service ThingLog {
  rpc OpenConnection(stream Thing) returns (ConnectionClosedResponse);
}
```

### <a name="thinglogservicecs"></a><span data-ttu-id="96c87-158">ThingLogService.cs</span><span class="sxs-lookup"><span data-stu-id="96c87-158">ThingLogService.cs</span></span>

```csharp
public class ThingLogService : Protos.ThingLog.ThingLogBase
{
    private static readonly ConnectionClosedResponse EmptyResponse = new ConnectionClosedResponse();
    private readonly ILogger<ThingLogService> _logger;
    public ThingLogService(ILogger<ThingLogService> logger)
    {
        _logger = logger;
    }

    public override async Task<CompletedResponse> OpenConnection(IAsyncStreamReader<Thing> requestStream, ServerCallContext context)
    {
        while (await requestStream.MoveNext(context.CancellationToken))
        {
            _logger.LogInformation(requestStream.Current.Description);
        }
        return EmptyResponse;
    }
}
```

### <a name="thinglog-client-example"></a><span data-ttu-id="96c87-159">ThingLog 用戶端示例</span><span class="sxs-lookup"><span data-stu-id="96c87-159">ThingLog client example</span></span>

```csharp
public class ThingLogger : IAsyncDisposable
{
    private readonly ThingLog.ThingLogClient _client;
    private readonly AsyncClientStreamingCall<ThingLogRequest, CompletedResponse> _stream;

    public ThingLogger(ThingLog.ThingLogClient client)
    {
        _client = client;
        _stream = client.OpenConnection();
    }

    public async Task WriteAsync(string description)
    {
        await _stream.RequestStream.WriteAsync(new Thing
        {
            Description = description,
            Time = Timestamp.FromDateTimeOffset(DateTimeOffset.UtcNow)
        });
    }

    public async ValueTask DisposeAsync()
    {
        await _stream.RequestStream.CompleteAsync();
        _stream.Dispose();
    }
}
```

<span data-ttu-id="96c87-160">您可以使用用戶端流 RPC 進行觸發和忘記消息傳遞，如上例所示。</span><span class="sxs-lookup"><span data-stu-id="96c87-160">You can use client-streaming RPCs for fire-and-forget messaging, as shown in the previous example.</span></span> <span data-ttu-id="96c87-161">您還可以使用它們向伺服器發送非常大的資料集。</span><span class="sxs-lookup"><span data-stu-id="96c87-161">You can also use them for sending very large datasets to the server.</span></span> <span data-ttu-id="96c87-162">相同的性能警告適用：對於較小的資料集，在`repeated`常規消息中使用欄位。</span><span class="sxs-lookup"><span data-stu-id="96c87-162">The same warning about performance applies: for smaller datasets, use `repeated` fields in regular messages.</span></span>

## <a name="wcf-full-duplex-services"></a><span data-ttu-id="96c87-163">WCF 全雙工服務</span><span class="sxs-lookup"><span data-stu-id="96c87-163">WCF full-duplex services</span></span>

<span data-ttu-id="96c87-164">WCF 雙工綁定支援在服務介面和用戶端回檔介面上執行多個單向操作。</span><span class="sxs-lookup"><span data-stu-id="96c87-164">WCF duplex binding supports multiple one-way operations on both the service interface and the client callback interface.</span></span> <span data-ttu-id="96c87-165">這種支援允許用戶端和伺服器之間持續對話。</span><span class="sxs-lookup"><span data-stu-id="96c87-165">This support allows ongoing conversations between client and server.</span></span> <span data-ttu-id="96c87-166">gRPC 支援與雙向流式處理 RPC 類似的內容，其中兩個參數`stream`都用修飾符標記。</span><span class="sxs-lookup"><span data-stu-id="96c87-166">gRPC supports something similar with bidirectional streaming RPCs, where both parameters are marked with the `stream` modifier.</span></span>

### <a name="chatproto"></a><span data-ttu-id="96c87-167">聊天.proto</span><span class="sxs-lookup"><span data-stu-id="96c87-167">chat.proto</span></span>

```protobuf
service Chatter {
    rpc Connect(stream IncomingMessage) returns (stream OutgoingMessage);
}
```

### <a name="chatterservicecs"></a><span data-ttu-id="96c87-168">ChatterService.cs</span><span class="sxs-lookup"><span data-stu-id="96c87-168">ChatterService.cs</span></span>

```csharp
public class ChatterService : Chatter.ChatterBase
{
    private readonly IChatHub _hub;

    public ChatterService(IChatHub hub)
    {
        _hub = hub;
    }

    public override async Task Connect(IAsyncStreamReader<MessageRequest> requestStream, IServerStreamWriter<MessageResponse> responseStream, ServerCallContext context)
    {
        _hub.MessageReceived += async (sender, args) =>
            await responseStream.WriteAsync(new MessageResponse {Text = args.Message});

        while (await requestStream.MoveNext(context.CancellationToken))
        {
            await _hub.SendAsync(requestStream.Current.Text);
        }
    }
}
```

<span data-ttu-id="96c87-169">在前面的示例中，您可以看到實現方法同時接收請求流 （`IAsyncStreamReader<MessageRequest>`） 和回應流 （`IServerStreamWriter<MessageResponse>`。</span><span class="sxs-lookup"><span data-stu-id="96c87-169">In the previous example, you can see that the implementation method receives both a request stream (`IAsyncStreamReader<MessageRequest>`) and a response stream (`IServerStreamWriter<MessageResponse>`).</span></span> <span data-ttu-id="96c87-170">該方法可以讀取和寫入消息，直到連接關閉。</span><span class="sxs-lookup"><span data-stu-id="96c87-170">The method can read and write messages until the connection is closed.</span></span>

### <a name="chatter-client"></a><span data-ttu-id="96c87-171">聊天用戶端</span><span class="sxs-lookup"><span data-stu-id="96c87-171">Chatter client</span></span>

```csharp
public class Chat : IAsyncDisposable
{
    private readonly Chatter.ChatterClient _client;
    private readonly AsyncDuplexStreamingCall<MessageRequest, MessageResponse> _stream;
    private readonly CancellationTokenSource _cancellationTokenSource;
    private readonly Task _readTask;

    public Chat(Chatter.ChatterClient client)
    {
        _client = client;
        _stream = _client.Connect();
        _cancellationTokenSource = new CancellationTokenSource();
        _readTask = ReadAsync(_cancellationTokenSource.Token);
    }

    public async Task SendAsync(string message)
    {
        await _stream.RequestStream.WriteAsync(new MessageRequest {Text = message});
    }

    private async Task ReadAsync(CancellationToken token)
    {
        while (await _stream.ResponseStream.MoveNext(token))
        {
            Console.WriteLine(_stream.ResponseStream.Current.Text);
        }
    }

    public async ValueTask DisposeAsync()
    {
        await _stream.RequestStream.CompleteAsync();
        await _readTask;
        _stream.Dispose();
    }
}
```

>[!div class="step-by-step"]
><span data-ttu-id="96c87-172">[上一個](wcf-bindings.md)
>[下一個](metadata.md)</span><span class="sxs-lookup"><span data-stu-id="96c87-172">[Previous](wcf-bindings.md)
[Next](metadata.md)</span></span>
