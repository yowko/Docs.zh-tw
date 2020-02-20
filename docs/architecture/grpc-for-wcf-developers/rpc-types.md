---
title: WCF 開發人員的 RPC gRPC 類型
description: 瞭解 WCF 支援的遠端程序呼叫類型，以及它們在 gRPC 中的對等專案
ms.date: 09/02/2019
ms.openlocfilehash: 58f097bac61395e6810155e8ae9a6bbf2219ec5e
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503438"
---
# <a name="types-of-rpc"></a><span data-ttu-id="71a54-103">RPC 類型</span><span class="sxs-lookup"><span data-stu-id="71a54-103">Types of RPC</span></span>

<span data-ttu-id="71a54-104">身為 Windows Communication Foundation （WCF）開發人員，您可能會用來處理下列類型的遠端程序呼叫（RPC）：</span><span class="sxs-lookup"><span data-stu-id="71a54-104">As a Windows Communication Foundation (WCF) developer, you're probably used to dealing with the following types of remote procedure call (RPC):</span></span>

- <span data-ttu-id="71a54-105">要求/回復</span><span class="sxs-lookup"><span data-stu-id="71a54-105">Request/reply</span></span>
- <span data-ttu-id="71a54-106">雙面</span><span class="sxs-lookup"><span data-stu-id="71a54-106">Duplex:</span></span>
  - <span data-ttu-id="71a54-107">使用會話的單向雙工</span><span class="sxs-lookup"><span data-stu-id="71a54-107">One-way duplex with session</span></span>
  - <span data-ttu-id="71a54-108">具有會話的全雙工</span><span class="sxs-lookup"><span data-stu-id="71a54-108">Full duplex with session</span></span>
- <span data-ttu-id="71a54-109">單向</span><span class="sxs-lookup"><span data-stu-id="71a54-109">One-way</span></span>

<span data-ttu-id="71a54-110">您可以將這些 RPC 類型相當自然地對應到現有的 gRPC 概念。</span><span class="sxs-lookup"><span data-stu-id="71a54-110">It's possible to map these RPC types fairly naturally to existing gRPC concepts.</span></span> <span data-ttu-id="71a54-111">本章將依次探討每個區域。</span><span class="sxs-lookup"><span data-stu-id="71a54-111">This chapter will look at each of these areas in turn.</span></span> <span data-ttu-id="71a54-112">[第5章](migrate-wcf-to-grpc.md)將更深入探討類似的範例。</span><span class="sxs-lookup"><span data-stu-id="71a54-112">[Chapter 5](migrate-wcf-to-grpc.md) will explore similar examples in greater depth.</span></span>

| <span data-ttu-id="71a54-113">WCF</span><span class="sxs-lookup"><span data-stu-id="71a54-113">WCF</span></span> | <span data-ttu-id="71a54-114">gRPC</span><span class="sxs-lookup"><span data-stu-id="71a54-114">gRPC</span></span> |
| --- | ---- |
| <span data-ttu-id="71a54-115">一般要求/回復</span><span class="sxs-lookup"><span data-stu-id="71a54-115">Regular request/reply</span></span> | <span data-ttu-id="71a54-116">一元 (Unary)</span><span class="sxs-lookup"><span data-stu-id="71a54-116">Unary</span></span> |
| <span data-ttu-id="71a54-117">具有使用用戶端回呼介面之會話的雙工服務</span><span class="sxs-lookup"><span data-stu-id="71a54-117">Duplex service with session using a client callback interface</span></span> | <span data-ttu-id="71a54-118">伺服器串流</span><span class="sxs-lookup"><span data-stu-id="71a54-118">Server streaming</span></span> |
| <span data-ttu-id="71a54-119">具有會話的全雙工服務</span><span class="sxs-lookup"><span data-stu-id="71a54-119">Full duplex service with session</span></span> | <span data-ttu-id="71a54-120">雙向串流</span><span class="sxs-lookup"><span data-stu-id="71a54-120">Bidirectional streaming</span></span> |
| <span data-ttu-id="71a54-121">單向作業</span><span class="sxs-lookup"><span data-stu-id="71a54-121">One-way operations</span></span> | <span data-ttu-id="71a54-122">用戶端串流</span><span class="sxs-lookup"><span data-stu-id="71a54-122">Client streaming</span></span> |

## <a name="requestreply"></a><span data-ttu-id="71a54-123">要求/回復</span><span class="sxs-lookup"><span data-stu-id="71a54-123">Request/reply</span></span>

<span data-ttu-id="71a54-124">針對採用並傳回少量資料的簡單要求/回復方法，請使用最簡單的 gRPC 模式（一元 RPC）。</span><span class="sxs-lookup"><span data-stu-id="71a54-124">For simple request/reply methods that take and return small amounts of data, use the simplest gRPC pattern, the unary RPC.</span></span>

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

<span data-ttu-id="71a54-125">如您所見，執行 gRPC 一元 RPC 服務方法與執行 WCF 作業類似。</span><span class="sxs-lookup"><span data-stu-id="71a54-125">As you can see, implementing a gRPC unary RPC service method is similar to implementing a WCF operation.</span></span> <span data-ttu-id="71a54-126">其差異在於，使用 gRPC 時，您會覆寫基類方法，而不是執行介面。</span><span class="sxs-lookup"><span data-stu-id="71a54-126">The difference is that with gRPC, you override a base class method instead of implementing an interface.</span></span> <span data-ttu-id="71a54-127">在伺服器上，gRPC 基底方法一律會傳回 <xref:System.Threading.Tasks.Task%601>，雖然用戶端同時提供非同步和封鎖方法來呼叫服務。</span><span class="sxs-lookup"><span data-stu-id="71a54-127">On the server, gRPC base methods always return <xref:System.Threading.Tasks.Task%601>, although the client provides both async and blocking methods to call the service.</span></span>

## <a name="wcf-duplex-one-way-to-client"></a><span data-ttu-id="71a54-128">WCF 雙工，一種用戶端</span><span class="sxs-lookup"><span data-stu-id="71a54-128">WCF duplex, one way to client</span></span>

<span data-ttu-id="71a54-129">WCF 應用程式（具有特定系結）可以在用戶端與伺服器之間建立持續連線。</span><span class="sxs-lookup"><span data-stu-id="71a54-129">WCF applications (with certain bindings) can create a persistent connection between client and server.</span></span> <span data-ttu-id="71a54-130">伺服器可以使用 <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> 屬性中指定的*回呼介面*，以非同步方式將資料傳送至用戶端，直到關閉連接為止。</span><span class="sxs-lookup"><span data-stu-id="71a54-130">The server can asynchronously send data to the client until the connection is closed, by using a *callback interface* specified in the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="71a54-131">gRPC 服務提供與訊息資料流程類似的功能。</span><span class="sxs-lookup"><span data-stu-id="71a54-131">gRPC services provide similar functionality with message streams.</span></span> <span data-ttu-id="71a54-132">在執行方面，資料流程不會*完全*對應到 WCF 雙工服務，但您可以達到相同的結果。</span><span class="sxs-lookup"><span data-stu-id="71a54-132">Streams don't map *exactly* to WCF duplex services in terms of implementation, but you can achieve the same results.</span></span>

### <a name="grpc-streaming"></a><span data-ttu-id="71a54-133">gRPC 串流</span><span class="sxs-lookup"><span data-stu-id="71a54-133">gRPC streaming</span></span>

<span data-ttu-id="71a54-134">gRPC 支援從用戶端到伺服器，以及從伺服器到用戶端的持續性資料流程建立。</span><span class="sxs-lookup"><span data-stu-id="71a54-134">gRPC supports the creation of persistent streams from client to server, and from server to client.</span></span> <span data-ttu-id="71a54-135">這兩種類型的資料流程可以同時為作用中。</span><span class="sxs-lookup"><span data-stu-id="71a54-135">Both types of stream can be active concurrently.</span></span> <span data-ttu-id="71a54-136">這種功能稱為雙向串流。</span><span class="sxs-lookup"><span data-stu-id="71a54-136">This ability is called bidirectional streaming.</span></span> 

<span data-ttu-id="71a54-137">您可以使用資料流程來處理一段時間的任意非同步訊息。</span><span class="sxs-lookup"><span data-stu-id="71a54-137">You can use streams for arbitrary, asynchronous messaging over time.</span></span> <span data-ttu-id="71a54-138">或者，您可以使用它們來傳遞太大的大型資料集，以便在單一要求或回應中產生和傳送。</span><span class="sxs-lookup"><span data-stu-id="71a54-138">Or you can use them for passing large datasets that are too big to generate and send in a single request or response.</span></span>

<span data-ttu-id="71a54-139">下列範例顯示伺服器資料流程 RPC。</span><span class="sxs-lookup"><span data-stu-id="71a54-139">The following example shows a server-streaming RPC.</span></span>

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

<span data-ttu-id="71a54-140">您可以從用戶端應用程式取用此伺服器資料流程，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="71a54-140">This server stream can be consumed from a client application, as shown in the following code:</span></span>

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
> <span data-ttu-id="71a54-141">伺服器串流處理 Rpc 適用于訂用帳戶樣式服務。</span><span class="sxs-lookup"><span data-stu-id="71a54-141">Server-streaming RPCs are useful for subscription-style services.</span></span> <span data-ttu-id="71a54-142">當大型資料集在記憶體中建立整個資料集沒有效率或無法完成時，它們也很有用。</span><span class="sxs-lookup"><span data-stu-id="71a54-142">They're also useful for sending large datasets when it would be inefficient or impossible to build the entire dataset in memory.</span></span> <span data-ttu-id="71a54-143">不過，串流回應與在單一訊息中傳送 `repeated` 欄位的速度一樣快。</span><span class="sxs-lookup"><span data-stu-id="71a54-143">However, streaming responses isn't as fast as sending `repeated` fields in a single message.</span></span> <span data-ttu-id="71a54-144">作為規則，串流不應用於小型資料集。</span><span class="sxs-lookup"><span data-stu-id="71a54-144">As a rule, streaming shouldn't be used for small datasets.</span></span>

### <a name="differences-from-wcf"></a><span data-ttu-id="71a54-145">WCF 的差異</span><span class="sxs-lookup"><span data-stu-id="71a54-145">Differences from WCF</span></span>

<span data-ttu-id="71a54-146">WCF 雙工服務使用的用戶端回呼介面可以有多個方法。</span><span class="sxs-lookup"><span data-stu-id="71a54-146">A WCF duplex service uses a client callback interface that can have multiple methods.</span></span> <span data-ttu-id="71a54-147">GRPC 伺服器串流服務只能透過單一資料流程傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="71a54-147">A gRPC server-streaming service can only send messages over a single stream.</span></span> <span data-ttu-id="71a54-148">如果您需要多個方法，請使用具有[任何欄位或欄位之一的](protobuf-any-oneof.md)訊息類型來傳送不同的訊息，並在用戶端中撰寫程式碼來處理它們。</span><span class="sxs-lookup"><span data-stu-id="71a54-148">If you need multiple methods, use a message type with either [an Any field or a oneof field](protobuf-any-oneof.md) to send different messages, and write code in the client to handle them.</span></span>

<span data-ttu-id="71a54-149">在 WCF 中，具有會話的[ServiceContract](xref:System.ServiceModel.ServiceContractAttribute)類別會保持運作，直到連接關閉為止。</span><span class="sxs-lookup"><span data-stu-id="71a54-149">In WCF, the [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) class with the session is kept alive until the connection is closed.</span></span> <span data-ttu-id="71a54-150">可以在會話內呼叫多個方法。</span><span class="sxs-lookup"><span data-stu-id="71a54-150">Multiple methods can be called within the session.</span></span> <span data-ttu-id="71a54-151">在 gRPC 中，執行方法傳回的 `Task` 不應完成，直到連接關閉為止。</span><span class="sxs-lookup"><span data-stu-id="71a54-151">In gRPC, the `Task` that the implementation method returns shouldn't finish until the connection is closed.</span></span>

## <a name="wcf-one-way-operations-and-grpc-client-streaming"></a><span data-ttu-id="71a54-152">WCF 單向作業和 gRPC 用戶端串流</span><span class="sxs-lookup"><span data-stu-id="71a54-152">WCF one-way operations and gRPC client streaming</span></span>

<span data-ttu-id="71a54-153">WCF 提供單向作業（以 `[OperationContract(IsOneWay = true)]`標記），其會傳回傳輸特定的通知。</span><span class="sxs-lookup"><span data-stu-id="71a54-153">WCF provides one-way operations (marked with `[OperationContract(IsOneWay = true)]`) that return a transport-specific acknowledgement.</span></span> <span data-ttu-id="71a54-154">gRPC 服務方法一律會傳迴響應，即使它是空的也一樣。</span><span class="sxs-lookup"><span data-stu-id="71a54-154">gRPC service methods always return a response, even if it's empty.</span></span> <span data-ttu-id="71a54-155">用戶端應該一律等待該回應。</span><span class="sxs-lookup"><span data-stu-id="71a54-155">The client should always await that response.</span></span> <span data-ttu-id="71a54-156">如需 gRPC 中的「暫時訊息」模式，您可以建立用戶端串流服務。</span><span class="sxs-lookup"><span data-stu-id="71a54-156">For the "fire-and-forget" style of messaging in gRPC, you can create a client streaming service.</span></span>

### <a name="thing_logproto"></a><span data-ttu-id="71a54-157">thing_log. proto</span><span class="sxs-lookup"><span data-stu-id="71a54-157">thing_log.proto</span></span>

```protobuf
service ThingLog {
  rpc OpenConnection(stream Thing) returns (ConnectionClosedResponse);
}
```

### <a name="thinglogservicecs"></a><span data-ttu-id="71a54-158">ThingLogService.cs</span><span class="sxs-lookup"><span data-stu-id="71a54-158">ThingLogService.cs</span></span>

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

### <a name="thinglog-client-example"></a><span data-ttu-id="71a54-159">ThingLog 用戶端範例</span><span class="sxs-lookup"><span data-stu-id="71a54-159">ThingLog client example</span></span>

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

<span data-ttu-id="71a54-160">您可以使用用戶端串流 Rpc 來進行引發和忘記的訊息，如先前範例所示。</span><span class="sxs-lookup"><span data-stu-id="71a54-160">You can use client-streaming RPCs for fire-and-forget messaging, as shown in the previous example.</span></span> <span data-ttu-id="71a54-161">您也可以使用它們將非常大型的資料集傳送至伺服器。</span><span class="sxs-lookup"><span data-stu-id="71a54-161">You can also use them for sending very large datasets to the server.</span></span> <span data-ttu-id="71a54-162">適用于效能的相同警告：對於較小的資料集，請在一般訊息中使用 `repeated` 欄位。</span><span class="sxs-lookup"><span data-stu-id="71a54-162">The same warning about performance applies: for smaller datasets, use `repeated` fields in regular messages.</span></span>

## <a name="wcf-full-duplex-services"></a><span data-ttu-id="71a54-163">WCF 全雙工服務</span><span class="sxs-lookup"><span data-stu-id="71a54-163">WCF full-duplex services</span></span>

<span data-ttu-id="71a54-164">WCF 雙工系結支援服務介面和用戶端回呼介面上的多個單向作業。</span><span class="sxs-lookup"><span data-stu-id="71a54-164">WCF duplex binding supports multiple one-way operations on both the service interface and the client callback interface.</span></span> <span data-ttu-id="71a54-165">這種支援可讓用戶端與伺服器之間進行進行中的交談。</span><span class="sxs-lookup"><span data-stu-id="71a54-165">This support allows ongoing conversations between client and server.</span></span> <span data-ttu-id="71a54-166">gRPC 支援類似于雙向串流 Rpc 的專案，其中兩個參數都以 `stream` 修飾詞標記。</span><span class="sxs-lookup"><span data-stu-id="71a54-166">gRPC supports something similar with bidirectional streaming RPCs, where both parameters are marked with the `stream` modifier.</span></span>

### <a name="chatproto"></a><span data-ttu-id="71a54-167">聊天. proto</span><span class="sxs-lookup"><span data-stu-id="71a54-167">chat.proto</span></span>

```protobuf
service Chatter {
    rpc Connect(stream IncomingMessage) returns (stream OutgoingMessage);
}
```

### <a name="chatterservicecs"></a><span data-ttu-id="71a54-168">ChatterService.cs</span><span class="sxs-lookup"><span data-stu-id="71a54-168">ChatterService.cs</span></span>

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

<span data-ttu-id="71a54-169">在上述範例中，您可以看到執行方法會同時收到要求資料流程（`IAsyncStreamReader<MessageRequest>`）和回應資料流程（`IServerStreamWriter<MessageResponse>`）。</span><span class="sxs-lookup"><span data-stu-id="71a54-169">In the previous example, you can see that the implementation method receives both a request stream (`IAsyncStreamReader<MessageRequest>`) and a response stream (`IServerStreamWriter<MessageResponse>`).</span></span> <span data-ttu-id="71a54-170">方法可以讀取和寫入訊息，直到連接關閉為止。</span><span class="sxs-lookup"><span data-stu-id="71a54-170">The method can read and write messages until the connection is closed.</span></span>

### <a name="chatter-client"></a><span data-ttu-id="71a54-171">Chatter 用戶端</span><span class="sxs-lookup"><span data-stu-id="71a54-171">Chatter client</span></span>

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
><span data-ttu-id="71a54-172">[上一頁](wcf-bindings.md)
>[下一頁](metadata.md)</span><span class="sxs-lookup"><span data-stu-id="71a54-172">[Previous](wcf-bindings.md)
[Next](metadata.md)</span></span>
