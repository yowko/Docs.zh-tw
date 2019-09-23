---
title: 建立 gRPC 用戶端程式庫-適用于 WCF 開發人員的 gRPC
description: 討論 gRPC 服務的共用用戶端程式庫/套件。
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 44a749c888528ca244f41b5b88354d7ed1db4190
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184586"
---
# <a name="create-grpc-client-libraries"></a>建立 gRPC 用戶端程式庫

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

不需要散發 gPRC 應用程式的用戶端程式庫。 您可以在組織內建立檔案`.proto`的共用文件庫，而其他小組則可以使用這些檔案在自己的專案中產生用戶端程式代碼。 但是，如果您有私用的 NuGet 存放庫，而且許多其他小組使用 .NET Core，則建立和發佈用戶端 NuGet 套件做為服務專案的一部分，可能是共用和升級服務的好方法。

散發用戶端程式庫的優點之一，是您可以使用實用的「便利性」方法和屬性，來增強產生的 gRPC 和 Protobuf 類別。 在用戶端程式代碼中，就像在伺服器中一樣，所有類別`partial`都會宣告為，因此您可以在不編輯產生的程式碼的情況下擴充它們。 這表示很容易就能將多個函式、方法、計算屬性和其他新增至基本類型。

> [!CAUTION]
> 您**不**應該使用自訂程式碼來提供基本的功能，因為這表示功能會限制為使用共用程式庫的 .net 小組，而不是使用 Python 或 JAVA 等其他語言或平臺的小組。

在不同小組經常使用不同程式設計語言和架構的多平臺環境中，或您的 API 可從外部存取的情況`.proto`下，只需共用檔案，讓開發人員能夠產生自己的用戶端，是最佳的方式。請確定有許多小組可以存取您的 gRPC 服務。

## <a name="useful-extensions"></a>有用的擴充功能

.Net 中有兩個常用的介面，可用來處理物件的資料流程<xref:System.Collections.Generic.IEnumerable%601> ： <xref:System.IObservable%601>和。 從 .net Core 3.0 和C# 8.0 開始，有介面可<xref:System.Collections.Generic.IAsyncEnumerable%601> `await foreach`非同步處理資料流程，以及使用介面的語法。 本節提供可重複使用的程式碼，以將這些介面套用至 gRPC 資料流程。

使用 .net Core gRPC 用戶端程式庫時，有`ReadAllAsync`一個適用`IAsyncStreamReader<T>`于的擴充方法`IAsyncEnumerable<T>`，可建立。 對於使用被動程式設計的開發人員，建立的`IObservable<T>`對等擴充方法可能會如下所示。

### <a name="iobservable"></a>IObservable

介面是的「被動」 `IEnumerable<T>`反轉。 `IObservable<T>` 「回應式」方法不會從資料流程提取專案，而是讓資料流程將專案推送至「訂閱者」。 這與 gRPC 資料流程非常類似，而且很容易就能將其包裝`IObservable<T>`在`IAsyncStreamReader<T>`周圍。

這段程式碼的長度`IAsyncEnumerable<T>`超過程式C#代碼，因為沒有內建的支援可使用可預見值，因此必須以手動方式建立執行類別。 不過，它是一個泛型類別，因此單一的執行方式可跨所有類型使用。

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
> 這個可觀察的`Subscribe`執行只允許呼叫一次方法，因為嘗試從資料流程讀取的多個訂閱者會導致混亂。 在可預見值[中，有](https://www.nuget.org/packages/System.Reactive.Linq)一些運算子（例如）會啟用緩衝處理和可重複使用的共用，以用於此實作為。 `Replay`

類別會處理的列舉`IAsyncStreamReader`。 `GrpcStreamSubscription`

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

`IAsyncEnumerable` 和`IObservable`模型都是在 .net 中處理非同步資料資料流程的妥善支援和妥善記載的方式。 gRPC 串流會妥善對應到這兩個範例，以提供與現代化 .NET Core 架構的緊密整合，以及被動/非同步程式設計樣式。

>[!div class="step-by-step"]
>[上一頁](streaming-versus-repeated.md)
>[下一頁](security.md)
