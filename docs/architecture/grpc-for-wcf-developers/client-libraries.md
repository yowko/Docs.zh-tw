---
title: 建立 gRPC 用戶端程式庫-適用于 WCF 開發人員的 gRPC
description: 討論 gRPC 服務的共用用戶端程式庫/套件。
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: b403e7e1638496947ac7f6fc976cbeab2f435bbf
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73419926"
---
# <a name="create-grpc-client-libraries"></a>建立 gRPC 用戶端程式庫

不需要散發 gRPC 應用程式的用戶端程式庫。 您可以在組織內建立 `.proto` 檔案的共用程式庫，而其他小組則可以使用這些檔案在自己的專案中產生用戶端程式代碼。 但是，如果您有私用的 NuGet 存放庫，而且許多其他小組使用 .NET Core，則建立和發佈用戶端 NuGet 套件做為服務專案的一部分，可能是共用和升級服務的好方法。

散發用戶端程式庫的優點之一，是您可以使用實用的「便利性」方法和屬性，來增強產生的 gRPC 和 Protobuf 類別。 在用戶端程式代碼中，就像在伺服器中一樣，所有類別都會宣告為 `partial`，因此您可以在不編輯產生的程式碼的情況下擴充它們。 這表示很容易就能將多個函式、方法、計算屬性和其他新增至基本類型。

> [!CAUTION]
> 您**不**應該使用自訂程式碼來提供基本的功能，因為這表示功能會限制為使用共用程式庫的 .net 小組，而不是使用 Python 或 JAVA 等其他語言或平臺的小組。

在不同小組經常使用不同程式設計語言和架構的多平臺環境中，或您的 API 可從外部存取的情況下，只要共用 `.proto` 檔案，讓開發人員能夠產生自己的用戶端，是確保的最佳方式。盡可能有許多小組可以存取您的 gRPC 服務。

## <a name="useful-extensions"></a>有用的擴充功能

.NET 中有兩個常用的介面，可用來處理物件的資料流程： <xref:System.Collections.Generic.IEnumerable%601> 和 <xref:System.IObservable%601>。 從 .NET Core 3.0 和C# 8.0 開始，有一個用來非同步處理資料流程的 <xref:System.Collections.Generic.IAsyncEnumerable%601> 介面，以及使用介面的 `await foreach` 語法。 本節提供可重複使用的程式碼，以將這些介面套用至 gRPC 資料流程。

有了 .NET Core gRPC 用戶端程式庫，`IAsyncStreamReader<T>` 的 `ReadAllAsync` 擴充方法會建立 `IAsyncEnumerable<T>`。 對於使用被動程式設計的開發人員而言，建立 `IObservable<T>` 的同等擴充方法可能如下所示。

### <a name="iobservable"></a>IObservable

`IObservable<T>` 介面是 `IEnumerable<T>`的「被動」反轉。 「回應式」方法不會從資料流程提取專案，而是讓資料流程將專案推送至「訂閱者」。 這與 gRPC 串流非常類似，而且可以輕鬆地將 `IObservable<T>` 包裝 `IAsyncStreamReader<T>`。

這段程式碼的長度超過 `IAsyncEnumerable<T>` 的C#程式碼，因為沒有內建支援以使用可預見值，因此必須以手動方式建立執行類別。 不過，它是一個泛型類別，因此單一的執行方式可跨所有類型使用。

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
> 這個可觀察的執行只允許呼叫 `Subscribe` 方法一次，因為嘗試從資料流程讀取的多個訂閱者會導致混亂。 在可預見值[中，有](https://www.nuget.org/packages/System.Reactive.Linq)一些運算子（如 `Replay`）會啟用緩衝處理，並可重複共用可以與此實作為搭配使用的。

`GrpcStreamSubscription` 類別會處理 `IAsyncStreamReader`的列舉。

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

現在只需要一個簡單的擴充方法，即可從串流讀取器建立可觀察的。

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

## <a name="summary"></a>總結

`IAsyncEnumerable` 和 `IObservable` 模型都是受到妥善支援的方式，也是在 .NET 中處理非同步資料資料流程的完整記錄方法。 gRPC 串流會妥善對應到這兩個範例，以提供與現代化 .NET Core 架構的緊密整合，以及被動/非同步程式設計樣式。

>[!div class="step-by-step"]
>[上一頁](streaming-versus-repeated.md)
>[下一頁](security.md)
