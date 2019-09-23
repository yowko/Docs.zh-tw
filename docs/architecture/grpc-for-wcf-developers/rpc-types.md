---
title: WCF 開發人員的 RPC gRPC 類型
description: 瞭解 WCF 支援的遠端程序呼叫類型，以及它們在 gRPC 中的對等專案
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 4fed4ca7fa4ae6a0f861185719917ff0ed5929fd
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184159"
---
# <a name="types-of-rpc"></a><span data-ttu-id="4ace1-103">RPC 的類型</span><span class="sxs-lookup"><span data-stu-id="4ace1-103">Types of RPC</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="4ace1-104">身為 Windows Communication Foundation （WCF）開發人員，您可能會用來處理下列類型的遠端程序呼叫（RPC）：</span><span class="sxs-lookup"><span data-stu-id="4ace1-104">As a Windows Communication Foundation (WCF) developer, you're probably used to dealing with the following types of Remote Procedure Call (RPC):</span></span>

- <span data-ttu-id="4ace1-105">要求/回覆</span><span class="sxs-lookup"><span data-stu-id="4ace1-105">Request/Reply</span></span>
- <span data-ttu-id="4ace1-106">雙面</span><span class="sxs-lookup"><span data-stu-id="4ace1-106">Duplex:</span></span>
  - <span data-ttu-id="4ace1-107">使用會話的單向雙工</span><span class="sxs-lookup"><span data-stu-id="4ace1-107">One-way duplex with session</span></span>
  - <span data-ttu-id="4ace1-108">具有會話的全雙工</span><span class="sxs-lookup"><span data-stu-id="4ace1-108">Full duplex with session</span></span>
- <span data-ttu-id="4ace1-109">單向</span><span class="sxs-lookup"><span data-stu-id="4ace1-109">One-way</span></span>

<span data-ttu-id="4ace1-110">您可以將這些 RPC 類型相當自然地對應到現有的 gRPC 概念，本章將依序查看每一個區域。</span><span class="sxs-lookup"><span data-stu-id="4ace1-110">It's possible to map these RPC types fairly naturally to existing gRPC concepts and this chapter will look at each of these areas in turn.</span></span> <span data-ttu-id="4ace1-111">類似的範例會在[第5章](migrate-wcf-to-grpc.md)中更深入探討。</span><span class="sxs-lookup"><span data-stu-id="4ace1-111">Similar examples will be explored in much greater depth in [Chapter 5](migrate-wcf-to-grpc.md).</span></span>

| <span data-ttu-id="4ace1-112">WCF</span><span class="sxs-lookup"><span data-stu-id="4ace1-112">WCF</span></span> | <span data-ttu-id="4ace1-113">gRPC</span><span class="sxs-lookup"><span data-stu-id="4ace1-113">gRPC</span></span> |
| --- | ---- |
| <span data-ttu-id="4ace1-114">一般要求/回復</span><span class="sxs-lookup"><span data-stu-id="4ace1-114">Regular request/reply</span></span> | <span data-ttu-id="4ace1-115">一元</span><span class="sxs-lookup"><span data-stu-id="4ace1-115">Unary</span></span> |
| <span data-ttu-id="4ace1-116">具有使用用戶端回呼介面之會話的雙工服務</span><span class="sxs-lookup"><span data-stu-id="4ace1-116">Duplex service with session using a client callback interface</span></span> | <span data-ttu-id="4ace1-117">伺服器串流</span><span class="sxs-lookup"><span data-stu-id="4ace1-117">Server streaming</span></span> |
| <span data-ttu-id="4ace1-118">具有會話的全雙工服務</span><span class="sxs-lookup"><span data-stu-id="4ace1-118">Full duplex service with session</span></span> | <span data-ttu-id="4ace1-119">雙向串流</span><span class="sxs-lookup"><span data-stu-id="4ace1-119">Bidirectional streaming</span></span> |
| <span data-ttu-id="4ace1-120">單向作業</span><span class="sxs-lookup"><span data-stu-id="4ace1-120">One-way operations</span></span> | <span data-ttu-id="4ace1-121">用戶端串流</span><span class="sxs-lookup"><span data-stu-id="4ace1-121">Client streaming</span></span> |

## <a name="requestreply"></a><span data-ttu-id="4ace1-122">要求/回復</span><span class="sxs-lookup"><span data-stu-id="4ace1-122">Request/reply</span></span>

<span data-ttu-id="4ace1-123">針對採用並傳回少量資料的簡單要求/回復方法，請使用最簡單的 gRPC 模式（一元 RPC）。</span><span class="sxs-lookup"><span data-stu-id="4ace1-123">For simple request/reply methods that take and return small amounts of data, use the simplest gRPC pattern, the unary RPC.</span></span>

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

<span data-ttu-id="4ace1-124">如您所見，實 gRPC 一元 RPC 服務方法與執行 WCF 作業非常類似，不同之處在于 gRPC 會覆寫基類方法，而不是執行介面。</span><span class="sxs-lookup"><span data-stu-id="4ace1-124">As you can see, implementing a gRPC unary RPC service method is very similar to implementing a WCF operation, except that with gRPC you override a base class method instead of implementing an interface.</span></span> <span data-ttu-id="4ace1-125">請注意，在伺服器上，gRPC 基底方法一律<xref:System.Threading.Tasks.Task%601>會傳回，雖然用戶端同時提供非同步和封鎖方法來呼叫服務。</span><span class="sxs-lookup"><span data-stu-id="4ace1-125">Note that on the server, gRPC base methods always return a <xref:System.Threading.Tasks.Task%601>, although the client provides both async and blocking methods to call the service.</span></span>

## <a name="wcf-duplex-one-way-to-client"></a><span data-ttu-id="4ace1-126">WCF 雙工，單向至用戶端</span><span class="sxs-lookup"><span data-stu-id="4ace1-126">WCF duplex, one-way to client</span></span>

<span data-ttu-id="4ace1-127">WCF 應用程式（具有特定系結）可以在用戶端與伺服器之間建立持續連線，而伺服器可以使用指定<xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType>的*回呼介面*，以非同步方式將資料傳送至用戶端，直到關閉連接為止。property.</span><span class="sxs-lookup"><span data-stu-id="4ace1-127">WCF applications (with certain bindings) can create a persistent connection between client and server, and the server can asynchronously send data to the client until the connection is closed, using a *callback interface* specified in the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="4ace1-128">gRPC 服務提供與訊息資料流程類似的功能。</span><span class="sxs-lookup"><span data-stu-id="4ace1-128">gRPC services provide similar functionality with message streams.</span></span> <span data-ttu-id="4ace1-129">在執行方面，資料流程不會*完全*對應到 WCF 雙工服務，但也可以達成相同的結果。</span><span class="sxs-lookup"><span data-stu-id="4ace1-129">Streams don't map *exactly* to WCF duplex services in terms of implementation, but the same results can be achieved.</span></span>

### <a name="grpc-streaming"></a><span data-ttu-id="4ace1-130">gRPC 串流</span><span class="sxs-lookup"><span data-stu-id="4ace1-130">gRPC streaming</span></span>

<span data-ttu-id="4ace1-131">gRPC 支援從用戶端到伺服器，以及從伺服器到用戶端的持續性資料流程建立。</span><span class="sxs-lookup"><span data-stu-id="4ace1-131">gRPC supports the creation of persistent streams from client to server, and from server to client.</span></span> <span data-ttu-id="4ace1-132">這兩種類型的資料流程可能同時為作用中;這稱為雙向串流。</span><span class="sxs-lookup"><span data-stu-id="4ace1-132">Both types of stream may be active concurrently; this is called bidirectional streaming.</span></span> <span data-ttu-id="4ace1-133">資料流程可以用於一段時間的任意非同步訊息，或傳遞太大而無法在單一要求或回應中產生和傳送的大型資料集。</span><span class="sxs-lookup"><span data-stu-id="4ace1-133">Streams can be used for arbitrary, asynchronous messaging over time, or for passing large datasets that are too big to generate and send in a single request or response.</span></span>

<span data-ttu-id="4ace1-134">下列範例顯示伺服器資料流程 RPC。</span><span class="sxs-lookup"><span data-stu-id="4ace1-134">The following example shows a server streaming RPC.</span></span>

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

<span data-ttu-id="4ace1-135">您可以從用戶端應用程式取用此伺服器資料流程，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="4ace1-135">This server stream could be consumed from a client application as shown in the following code:</span></span>

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
> <span data-ttu-id="4ace1-136">伺服器串流 Rpc 適用于訂用帳戶式服務，也適用于在記憶體中建立整個資料集時，傳送非常大型的資料集。</span><span class="sxs-lookup"><span data-stu-id="4ace1-136">Server streaming RPCs are useful for subscription-style services, and also for sending very large datasets when it would be inefficient or impossible to build the entire dataset in memory.</span></span> <span data-ttu-id="4ace1-137">不過，串流回應與在單一訊息中`repeated`傳送欄位的速度一樣快，因為不應針對小型資料集使用規則串流。</span><span class="sxs-lookup"><span data-stu-id="4ace1-137">However, streaming responses isn't as fast as sending `repeated` fields in a single message, so as a rule streaming shouldn't be used for small datasets.</span></span>

### <a name="differences-to-wcf"></a><span data-ttu-id="4ace1-138">WCF 的差異</span><span class="sxs-lookup"><span data-stu-id="4ace1-138">Differences to WCF</span></span>

<span data-ttu-id="4ace1-139">WCF 雙工服務使用的用戶端回呼介面可以有多個方法。</span><span class="sxs-lookup"><span data-stu-id="4ace1-139">A WCF duplex service uses a client callback interface that can have multiple methods.</span></span> <span data-ttu-id="4ace1-140">GRPC 伺服器串流服務只能透過單一資料流程傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="4ace1-140">A gRPC server streaming service can only send messages over a single stream.</span></span> <span data-ttu-id="4ace1-141">如果您需要多個方法，請使用具有[任何欄位或欄位之一的](protobuf-any-oneof.md)訊息類型來傳送不同的訊息，並在用戶端中撰寫程式碼來處理它們。</span><span class="sxs-lookup"><span data-stu-id="4ace1-141">If you need multiple methods, use a message type with either [an Any field or a oneof field](protobuf-any-oneof.md) to send different messages, and write code in the client to handle them.</span></span>

<span data-ttu-id="4ace1-142">在 WCF 中，具有會話的[ServiceContract](xref:System.ServiceModel.ServiceContractAttribute)類別會保持運作，直到連接關閉為止，而且可以在會話內呼叫多個方法。</span><span class="sxs-lookup"><span data-stu-id="4ace1-142">In WCF, the [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) class with the session is kept alive until the connection is closed, and multiple methods may be called within the session.</span></span> <span data-ttu-id="4ace1-143">在 gRPC 中， `Task`由實方法所傳回的不應完成，直到連接關閉為止。</span><span class="sxs-lookup"><span data-stu-id="4ace1-143">In gRPC, the `Task` returned by the implementation method shouldn't complete until the connection is closed.</span></span>

## <a name="wcf-one-way-operations-and-grpc-client-streaming"></a><span data-ttu-id="4ace1-144">WCF 單向作業和 gRPC 用戶端串流</span><span class="sxs-lookup"><span data-stu-id="4ace1-144">WCF one-way operations and gRPC client streaming</span></span>

<span data-ttu-id="4ace1-145">WCF 提供單向作業（以標示）， `[OperationContract(IsOneWay = true)]`其會傳回傳輸特定的通知。</span><span class="sxs-lookup"><span data-stu-id="4ace1-145">WCF provides one-way operations (marked with `[OperationContract(IsOneWay = true)]`) that return a transport-specific acknowledgement.</span></span> <span data-ttu-id="4ace1-146">gRPC 服務方法一律會傳迴響應，即使它是空的，而且用戶端應該一律等待該回應。</span><span class="sxs-lookup"><span data-stu-id="4ace1-146">gRPC service methods always return a response, even if it's empty, and the client should always await that response.</span></span> <span data-ttu-id="4ace1-147">如需 gRPC 中的「火災」樣式訊息，您可以建立用戶端串流服務。</span><span class="sxs-lookup"><span data-stu-id="4ace1-147">For "fire-and-forget" style messaging in gRPC, you can create a client streaming service.</span></span>

### <a name="thing_logproto"></a><span data-ttu-id="4ace1-148">thing_log. proto</span><span class="sxs-lookup"><span data-stu-id="4ace1-148">thing_log.proto</span></span>

```protobuf
service ThingLog {
  rpc OpenConnection(stream Thing) returns (ConnectionClosedResponse);
}
```

### <a name="thinglogservicecs"></a><span data-ttu-id="4ace1-149">ThingLogService.cs</span><span class="sxs-lookup"><span data-stu-id="4ace1-149">ThingLogService.cs</span></span>

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

### <a name="thinglog-client-example"></a><span data-ttu-id="4ace1-150">ThingLog 用戶端範例</span><span class="sxs-lookup"><span data-stu-id="4ace1-150">ThingLog client example</span></span>

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

<span data-ttu-id="4ace1-151">同樣地，用戶端串流處理 Rpc 也可以用於如前一個範例所示的引發和忘記訊息，但也適用于將非常大型的資料集傳送至伺服器。</span><span class="sxs-lookup"><span data-stu-id="4ace1-151">Again, client streaming RPCs can be used for fire-and-forget messaging as shown in the previous example, but also for sending very large datasets to the server.</span></span> <span data-ttu-id="4ace1-152">適用于效能的相同警告：對於較小的資料`repeated`集，請使用一般訊息中的欄位。</span><span class="sxs-lookup"><span data-stu-id="4ace1-152">The same warning about performance applies: for smaller datasets, use `repeated` fields in regular messages.</span></span>

## <a name="wcf-full-duplex-services"></a><span data-ttu-id="4ace1-153">WCF 全雙工服務</span><span class="sxs-lookup"><span data-stu-id="4ace1-153">WCF full duplex services</span></span>

<span data-ttu-id="4ace1-154">WCF 雙工系結支援服務介面和用戶端回呼介面上的多個單向作業，讓用戶端與伺服器之間進行的交談得以進行。</span><span class="sxs-lookup"><span data-stu-id="4ace1-154">WCF duplex binding supports multiple one-way operations on both the service interface and the client callback interface, allowing ongoing conversations between client and server.</span></span> <span data-ttu-id="4ace1-155">gRPC 支援類似于雙向串流 rpc 的專案，其中兩個參數都是`stream`以修飾詞標記。</span><span class="sxs-lookup"><span data-stu-id="4ace1-155">gRPC supports something similar with bidirectional streaming RPCs, where both parameters are marked with the `stream` modifier.</span></span>

### <a name="chatproto"></a><span data-ttu-id="4ace1-156">聊天. proto</span><span class="sxs-lookup"><span data-stu-id="4ace1-156">chat.proto</span></span>

```protobuf
service Chatter {
    rpc Connect(stream IncomingMessage) returns (stream OutgoingMessage);
}
```

### <a name="chatterservicecs"></a><span data-ttu-id="4ace1-157">ChatterService.cs</span><span class="sxs-lookup"><span data-stu-id="4ace1-157">ChatterService.cs</span></span>

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

<span data-ttu-id="4ace1-158">在上述範例中，您可以看到執行方法會同時接收要求資料流程（`IAsyncStreamReader<MessageRequest>`）和回應資料流程（`IServerStreamWriter<MessageResponse>`），而且可以讀取和寫入訊息，直到連接關閉為止。</span><span class="sxs-lookup"><span data-stu-id="4ace1-158">In the previous example, you can see that the implementation method receives both a request stream (`IAsyncStreamReader<MessageRequest>`) and a response stream (`IServerStreamWriter<MessageResponse>`), and can read and write messages until the connection is closed.</span></span>

### <a name="chatter-client"></a><span data-ttu-id="4ace1-159">Chatter 用戶端</span><span class="sxs-lookup"><span data-stu-id="4ace1-159">Chatter client</span></span>

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
><span data-ttu-id="4ace1-160">[上一頁](wcf-bindings.md)
>[下一頁](metadata.md)</span><span class="sxs-lookup"><span data-stu-id="4ace1-160">[Previous](wcf-bindings.md)
[Next](metadata.md)</span></span>
