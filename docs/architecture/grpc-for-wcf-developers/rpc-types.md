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
# <a name="types-of-rpc"></a>RPC 的類型

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

身為 Windows Communication Foundation （WCF）開發人員，您可能會用來處理下列類型的遠端程序呼叫（RPC）：

- 要求/回覆
- 雙面
  - 使用會話的單向雙工
  - 具有會話的全雙工
- 單向

您可以將這些 RPC 類型相當自然地對應到現有的 gRPC 概念，本章將依序查看每一個區域。 類似的範例會在[第5章](migrate-wcf-to-grpc.md)中更深入探討。

| WCF | gRPC |
| --- | ---- |
| 一般要求/回復 | 一元 |
| 具有使用用戶端回呼介面之會話的雙工服務 | 伺服器串流 |
| 具有會話的全雙工服務 | 雙向串流 |
| 單向作業 | 用戶端串流 |

## <a name="requestreply"></a>要求/回復

針對採用並傳回少量資料的簡單要求/回復方法，請使用最簡單的 gRPC 模式（一元 RPC）。

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

如您所見，實 gRPC 一元 RPC 服務方法與執行 WCF 作業非常類似，不同之處在于 gRPC 會覆寫基類方法，而不是執行介面。 請注意，在伺服器上，gRPC 基底方法一律<xref:System.Threading.Tasks.Task%601>會傳回，雖然用戶端同時提供非同步和封鎖方法來呼叫服務。

## <a name="wcf-duplex-one-way-to-client"></a>WCF 雙工，單向至用戶端

WCF 應用程式（具有特定系結）可以在用戶端與伺服器之間建立持續連線，而伺服器可以使用指定<xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType>的*回呼介面*，以非同步方式將資料傳送至用戶端，直到關閉連接為止。property.

gRPC 服務提供與訊息資料流程類似的功能。 在執行方面，資料流程不會*完全*對應到 WCF 雙工服務，但也可以達成相同的結果。

### <a name="grpc-streaming"></a>gRPC 串流

gRPC 支援從用戶端到伺服器，以及從伺服器到用戶端的持續性資料流程建立。 這兩種類型的資料流程可能同時為作用中;這稱為雙向串流。 資料流程可以用於一段時間的任意非同步訊息，或傳遞太大而無法在單一要求或回應中產生和傳送的大型資料集。

下列範例顯示伺服器資料流程 RPC。

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

您可以從用戶端應用程式取用此伺服器資料流程，如下列程式碼所示：

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
> 伺服器串流 Rpc 適用于訂用帳戶式服務，也適用于在記憶體中建立整個資料集時，傳送非常大型的資料集。 不過，串流回應與在單一訊息中`repeated`傳送欄位的速度一樣快，因為不應針對小型資料集使用規則串流。

### <a name="differences-to-wcf"></a>WCF 的差異

WCF 雙工服務使用的用戶端回呼介面可以有多個方法。 GRPC 伺服器串流服務只能透過單一資料流程傳送訊息。 如果您需要多個方法，請使用具有[任何欄位或欄位之一的](protobuf-any-oneof.md)訊息類型來傳送不同的訊息，並在用戶端中撰寫程式碼來處理它們。

在 WCF 中，具有會話的[ServiceContract](xref:System.ServiceModel.ServiceContractAttribute)類別會保持運作，直到連接關閉為止，而且可以在會話內呼叫多個方法。 在 gRPC 中， `Task`由實方法所傳回的不應完成，直到連接關閉為止。

## <a name="wcf-one-way-operations-and-grpc-client-streaming"></a>WCF 單向作業和 gRPC 用戶端串流

WCF 提供單向作業（以標示）， `[OperationContract(IsOneWay = true)]`其會傳回傳輸特定的通知。 gRPC 服務方法一律會傳迴響應，即使它是空的，而且用戶端應該一律等待該回應。 如需 gRPC 中的「火災」樣式訊息，您可以建立用戶端串流服務。

### <a name="thing_logproto"></a>thing_log. proto

```protobuf
service ThingLog {
  rpc OpenConnection(stream Thing) returns (ConnectionClosedResponse);
}
```

### <a name="thinglogservicecs"></a>ThingLogService.cs

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

### <a name="thinglog-client-example"></a>ThingLog 用戶端範例

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

同樣地，用戶端串流處理 Rpc 也可以用於如前一個範例所示的引發和忘記訊息，但也適用于將非常大型的資料集傳送至伺服器。 適用于效能的相同警告：對於較小的資料`repeated`集，請使用一般訊息中的欄位。

## <a name="wcf-full-duplex-services"></a>WCF 全雙工服務

WCF 雙工系結支援服務介面和用戶端回呼介面上的多個單向作業，讓用戶端與伺服器之間進行的交談得以進行。 gRPC 支援類似于雙向串流 rpc 的專案，其中兩個參數都是`stream`以修飾詞標記。

### <a name="chatproto"></a>聊天. proto

```protobuf
service Chatter {
    rpc Connect(stream IncomingMessage) returns (stream OutgoingMessage);
}
```

### <a name="chatterservicecs"></a>ChatterService.cs

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

在上述範例中，您可以看到執行方法會同時接收要求資料流程（`IAsyncStreamReader<MessageRequest>`）和回應資料流程（`IServerStreamWriter<MessageResponse>`），而且可以讀取和寫入訊息，直到連接關閉為止。

### <a name="chatter-client"></a>Chatter 用戶端

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
>[上一頁](wcf-bindings.md)
>[下一頁](metadata.md)
