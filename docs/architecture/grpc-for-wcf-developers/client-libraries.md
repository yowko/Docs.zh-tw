---
title: 建立 gRPC 用戶端程式庫-適用于 WCF 開發人員的 gRPC
description: 討論 gRPC 服務的共用用戶端程式庫/套件。
ms.date: 09/02/2019
ms.openlocfilehash: e47ccd958007f84d633bb9ad5808c5e97c231977
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "89358839"
---
# <a name="create-grpc-client-libraries"></a>建立 gRPC 用戶端程式庫

不需要散發 gRPC 應用程式的用戶端程式庫。 您可以在組織內建立共用的檔案程式庫 `.proto` ，而其他小組則可以使用這些檔案，在自己的專案中產生用戶端程式代碼。 但是，如果您有私用的 NuGet 存放庫，而且許多其他小組都使用 .NET Core，您可以建立併發布用戶端 NuGet 套件作為服務專案的一部分。 這可能是共用和推廣服務的好方法。

散發用戶端程式庫的優點之一，就是您可以使用有用的「便利性」方法和屬性來增強產生的 gRPC 和 Protobuf 類別。 在用戶端程式代碼中，如同在伺服器中一樣，所有類別都宣告為 `partial` ，因此您可以在不編輯產生的程式碼的情況下延伸它們。 這表示您可以輕鬆地將多個函式、方法和計算屬性新增至基本類型。

> [!CAUTION]
> 您不應該使用自訂程式碼來提供基本功能。 您不想要將該基本功能限制為使用共用文件庫的 .NET 小組，而不會將它提供給使用其他語言或平臺的小組（例如 Python 或 JAVA）。

請確定許多團隊都能存取您的 gRPC 服務。 若要這麼做，最好的方式是共用檔案 `.proto` ，讓開發人員可以產生自己的用戶端。 尤其是在多平臺環境中，不同小組經常使用不同的程式設計語言和架構，或是您的 API 可從外部存取的位置。

## <a name="useful-extensions"></a>有用的延伸模組

在 .NET 中，有兩個常用的介面可用來處理物件的資料流程： <xref:System.Collections.Generic.IEnumerable%601> 和 <xref:System.IObservable%601> 。 從 .NET Core 3.0 和 c # 8.0 開始，有 <xref:System.Collections.Generic.IAsyncEnumerable%601> 介面可用於非同步處理資料流程，以及 `await foreach` 使用介面的語法。 本節提供可重複使用的程式碼，以將這些介面套用至 gRPC 資料流程。

使用 .NET Core gRPC 用戶端程式庫時，有一個 `ReadAllAsync` `IAsyncStreamReader<T>` 可建立介面的擴充方法 `IAsyncEnumerable<T>` 。 針對使用回應式程式設計的開發人員，建立介面的相等擴充方法 `IObservable<T>` 可能看起來像下一節中的範例。

### <a name="iobservable"></a>IObservable

`IObservable<T>`介面是的「被動」反向 `IEnumerable<T>` 。 回應方法可讓資料流程將專案推送至訂閱者，而不是從資料流程提取專案。 這與 gRPC 資料流程非常類似，而且可以輕鬆地將介面包裝在 `IObservable<T>` `IAsyncStreamReader<T>` 介面周圍。

這段程式碼比程式 `IAsyncEnumerable<T>` 代碼長，因為 c # 沒有內建的支援可使用可預見值。 您必須手動建立實類別。 但是，它是一個泛型類別，所以單一的執行可跨所有類型運作。

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

        public GrpcStreamObservable(IAsyncStreamReader<T> reader, CancellationToken token = default)
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
> 這種可觀察的執行 `Subscribe` 只允許呼叫一次方法，因為有多個訂閱者嘗試從資料流程讀取會導致混亂。 有一些運算子（例如， `Replay` 在可預見值[System.Reactive.Linq](https://www.nuget.org/packages/System.Reactive.Linq)中）可啟用緩衝處理和可重複共用的，可用於此執行。

`GrpcStreamSubscription`類別會處理的列舉 `IAsyncStreamReader` ：

```csharp
public class GrpcStreamSubscription : IDisposable
{
    private readonly Task _task;
    private readonly CancellationTokenSource _tokenSource;
    private bool _completed;

    public GrpcStreamSubscription(IAsyncStreamReader<T> reader, IObserver<T> observer, CancellationToken token)
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

現在只需要一個簡單的擴充方法，即可從資料流程讀取器建立可觀察的。

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

`IAsyncEnumerable`和 `IObservable` 模型都是妥善支援的方式，而且是在 .net 中處理非同步資料流程的完整記錄方式。 gRPC 串流對應到兩個範例，提供與 .NET Core 的緊密整合，以及回應式和非同步程式設計樣式。

>[!div class="step-by-step"]
>[上一個](streaming-versus-repeated.md) 
>[下一步](security.md)
