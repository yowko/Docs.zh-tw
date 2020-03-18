---
title: 為 WCF 開發人員創建 gRPC 用戶端庫 - gRPC
description: 討論 gRPC 服務的共用用戶端庫/包。
ms.date: 09/02/2019
ms.openlocfilehash: bb58cb3cda4b0cbb3a5d34129961349bcb0093e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401666"
---
# <a name="create-grpc-client-libraries"></a>創建 gRPC 用戶端庫

不需要為 gRPC 應用程式分發用戶端庫。 您可以在組織內創建檔共用`.proto`庫，其他團隊可以使用這些檔在他們自己的專案中生成用戶端代碼。 但是，如果您有一個私有的 NuGet 存儲庫，並且許多其他團隊正在使用 .NET Core，則可以創建和發佈用戶端 NuGet 包，作為服務專案的一部分。 這是分享和推廣服務的好方法。

分發用戶端庫的一個優點是，您可以使用有用的"方便"方法和屬性增強生成的 gRPC 和 Protobuf 類。 在用戶端代碼中，如在伺服器中，所有類都聲明為`partial`，因此您可以擴展它們，而無需編輯生成的代碼。 這意味著可以輕鬆地將建構函式、方法和計算屬性添加到基本類型。

> [!CAUTION]
> 不應使用自訂代碼來提供基本功能。 您不希望將該基本功能限制為使用共用庫的 .NET 團隊，而不是將其提供給使用其他語言或平臺（如 Python 或 JAVA）的團隊。

確保盡可能多的團隊可以訪問您的 gRPC 服務。 最好的方法是共用`.proto`檔，以便開發人員可以生成自己的用戶端。 在多平臺環境中尤其如此，其中不同的團隊經常使用不同的程式設計語言和框架，或者 API 是外部可訪問的。

## <a name="useful-extensions"></a>有用的擴展

.NET 中有兩個常用介面用於處理物件流：<xref:System.Collections.Generic.IEnumerable%601>和<xref:System.IObservable%601>。 從 .NET Core 3.0 和 C# 8.0<xref:System.Collections.Generic.IAsyncEnumerable%601>開始，有一個用於非同步處理`await foreach`流的介面，以及一個用於使用該介面的語法。 本節介紹將這些介面應用於 gRPC 流的可重用代碼。

使用 .NET Core gRPC 用戶端庫時，有`ReadAllAsync`一種擴展`IAsyncStreamReader<T>`方法用於創建`IAsyncEnumerable<T>`介面。 對於使用反應式程式設計的開發人員，創建介面的`IObservable<T>`等效擴充方法可能類似于下一節中的示例。

### <a name="iobservable"></a>可觀察

介面`IObservable<T>`是 中的"反應"反對。 `IEnumerable<T>` 被動方法允許流將專案推送到訂閱伺服器，而不是從流中提取專案。 這與 gRPC 流非常相似，並且很容易圍繞`IObservable<T>``IAsyncStreamReader<T>`介面包裝介面。

此代碼比`IAsyncEnumerable<T>`代碼長，因為 C# 沒有內置支援使用可觀察器。 您必須手動創建實現類。 但它是一個泛型類，因此單個實現適用于所有類型。

```csharp
using System;
using System.Diagnostics;
using System.Threading;
using System.Threading.Tasks;

namespace Grpc.Core
{
    public class GrpcStreamObservable<T> : IObservable<T>
    {
        private readonly IAsyncStreamReader<T> _reader;
        private readonly CancellationToken _token;
        private int _used;

        public Observable(IAsyncStreamReader<T> reader, CancellationToken token = default)
        {
            _reader = reader;
            _token = token;
            _used = 0;
        }

        public IDisposable Subscribe(IObserver<T> observer) =>
            Interlocked.Exchange(ref _used, 1) == 0
                ? new GrpcStreamSubscription(_reader, observer, _token)
                : throw new InvalidOperationException("Subscribe can only be called once.");

    }
}
```

> [!IMPORTANT]
> 此可觀察的實現只允許`Subscribe`調用一次該方法，因為有多個訂閱者嘗試從流中讀取將導致混亂。 有運算子，如`Replay` [System.Reactive.Linq，](https://www.nuget.org/packages/System.Reactive.Linq)它們支援可觀察的緩衝和可重複共用，這些可與此實現一起使用。

類`GrpcStreamSubscription`處理 的`IAsyncStreamReader`枚舉：

```csharp
public class GrpcStreamSubscription : IDisposable
{
    private readonly Task _task;
    private readonly CancellationTokenSource _tokenSource;
    private bool _completed;

    public Subscription(IAsyncStreamReader<T> reader, IObserver<T> observer, CancellationToken token)
    {
        Debug.Assert(reader != null);
        Debug.Assert(observer != null);
        _tokenSource = new CancellationTokenSource();
        token.Register(_tokenSource.Cancel);
        _task = Run(reader, observer, _tokenSource.Token);
    }

    private async Task Run(IAsyncStreamReader<T> reader, IObserver<T> observer, CancellationToken token)
    {
        while (!token.IsCancellationRequested)
        {
            try
            {
                if (!await reader.MoveNext(token)) break;
            }
            catch (RpcException e) when (e.StatusCode == Grpc.Core.StatusCode.NotFound)
            {
                break;
            }
            catch (OperationCanceledException)
            {
                break;
            }
            catch (Exception e)
            {
                observer.OnError(e);
                _completed = true;
                return;
            }

            observer.OnNext(reader.Current);
        }

        _completed = true;
        observer.OnCompleted();
    }

    public void Dispose()
    {
        if (!_completed && !_tokenSource.IsCancellationRequested)
        {
            _tokenSource.Cancel();
        }

        _tokenSource.Dispose();
        _task.Dispose();
    }

}
```

現在只需要一個簡單的擴充方法，從流讀取器創建可觀察的。

```csharp
using System;
using System.Diagnostics;
using System.Threading;
using System.Threading.Tasks;

namespace Grpc.Core
{
    public static class AsyncStreamReaderObservableExtensions
    {
        public static IObservable<T> AsObservable<T>(this IAsyncStreamReader<T> reader) =>
            new GrpcStreamObservable<T>(reader);
    }
}
```

## <a name="summary"></a>摘要

和`IAsyncEnumerable``IObservable`模型都是支援良好且記錄良好的處理 .NET 中非同步資料流程的方法。 gRPC 流很好地映射到這兩種範例，提供與 .NET Core 以及被動和非同步程式設計樣式的緊密集成。

>[!div class="step-by-step"]
>[上一個](streaming-versus-repeated.md)
>[下一個](security.md)
