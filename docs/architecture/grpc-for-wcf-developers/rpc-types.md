---
title: 適用于 WCF 開發人員的 RPC 類型 - gRPC
description: 審查 WCF 支援的遠端程序呼叫的類型及其在 gRPC 中的等效調用
ms.date: 09/02/2019
ms.openlocfilehash: b9d4ce7cae693ed7904229483cbccfe3b299b640
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401680"
---
# <a name="types-of-rpc"></a>RPC 類型

作為 Windows 通信基礎 （WCF） 開發人員，您可能習慣于處理以下類型的遠端程序呼叫 （RPC）：

- 請求/回復
- 雙工：
  - 帶會話的單向雙工
  - 帶會話的全雙工
- 單向

可以自然地將這些 RPC 類型映射到現有的 gRPC 概念。 本章將依次介紹每個領域。 [第五章](migrate-wcf-to-grpc.md)將更深入地探討類似的例子。

| WCF | gRPC |
| --- | ---- |
| 定期請求/回復 | 一元 (Unary) |
| 使用用戶端回檔介面使用會話的雙工服務 | 伺服器流式處理 |
| 帶會話的全雙工服務 | 雙向流式處理 |
| 單向操作 | 用戶端流式處理 |

## <a name="requestreply"></a>請求/回復

對於獲取和返回少量資料的簡單請求/回復方法，請使用最簡單的 gRPC 模式，即一元 RPC。

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

如您所見，實現 gRPC 一元 RPC 服務方法類似于實現 WCF 操作。 區別在於，使用 gRPC，可以重寫基類方法，而不是實現介面。 在伺服器上，gRPC 基方法始終返回<xref:System.Threading.Tasks.Task%601>，儘管用戶端同時提供非同步和阻止方法來調用服務。

## <a name="wcf-duplex-one-way-to-client"></a>WCF 雙工，用戶端的一種方式

WCF 應用程式（具有某些綁定）可以在用戶端和伺服器之間創建持久連接。 伺服器可以使用<xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType>屬性中指定的*回檔介面*將資料非同步發送到用戶端，直到連接關閉。

gRPC 服務提供與消息流類似的功能。 流在實現方面不會*精確*映射到 WCF 雙工服務，但您可以實現相同的結果。

### <a name="grpc-streaming"></a>gRPC 流式處理

gRPC 支援創建從用戶端到伺服器以及從伺服器到用戶端的持久流。 這兩種類型的流可以同時處於活動狀態。 此功能稱為雙向流式處理。

隨著時間的推移，您可以將流用於任意的非同步消息傳遞。 或者，您可以使用它們傳遞太大的大型資料集，無法生成和發送單個請求或回應。

下面的示例顯示了伺服器流 RPC。

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

此伺服器流可以從用戶端應用程式使用，如以下代碼所示：

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
> 伺服器流式處理中心對於訂閱樣式的服務很有用。 當在記憶體中構建整個資料集效率低下或不可能時，它們對於發送大型資料集也很有用。 但是，流式處理回應不如在一條消息中`repeated`發送欄位快。 通常，流式處理不應用於小型資料集。

### <a name="differences-from-wcf"></a>與 WCF 的差異

WCF 雙工服務使用用戶端回檔介面，該介面可以有多個方法。 gRPC 伺服器流服務只能通過單個流發送消息。 如果需要多種方法，請使用具有[Any 欄位或欄位之一](protobuf-any-oneof.md)的訊息類型發送不同的消息，並在用戶端中編寫代碼來處理它們。

在 WCF 中，具有會話[的服務合同](xref:System.ServiceModel.ServiceContractAttribute)類將保持活動狀態，直到連接關閉。 可以在會話中調用多種方法。 在 gRPC`Task`中，在關閉連接之前，實現方法返回的不應完成。

## <a name="wcf-one-way-operations-and-grpc-client-streaming"></a>WCF 單向操作和 gRPC 用戶端流

WCF 提供單向操作（標記為`[OperationContract(IsOneWay = true)]`），返回特定于傳輸的確認。 gRPC 服務方法始終返回回應，即使它為空。 用戶端應始終等待該回應。 對於 gRPC 中"即用即用"消息傳遞樣式，您可以創建用戶端流服務。

### <a name="thing_logproto"></a>thing_log.proto

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

### <a name="thinglog-client-example"></a>ThingLog 用戶端示例

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

您可以使用用戶端流 RPC 進行觸發和忘記消息傳遞，如上例所示。 您還可以使用它們向伺服器發送非常大的資料集。 相同的性能警告適用：對於較小的資料集，在`repeated`常規消息中使用欄位。

## <a name="wcf-full-duplex-services"></a>WCF 全雙工服務

WCF 雙工綁定支援在服務介面和用戶端回檔介面上執行多個單向操作。 這種支援允許用戶端和伺服器之間持續對話。 gRPC 支援與雙向流式處理 RPC 類似的內容，其中兩個參數`stream`都用修飾符標記。

### <a name="chatproto"></a>聊天.proto

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

在前面的示例中，您可以看到實現方法同時接收請求流 （`IAsyncStreamReader<MessageRequest>`） 和回應流 （`IServerStreamWriter<MessageResponse>`。 該方法可以讀取和寫入消息，直到連接關閉。

### <a name="chatter-client"></a>聊天用戶端

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
>[上一個](wcf-bindings.md)
>[下一個](metadata.md)
