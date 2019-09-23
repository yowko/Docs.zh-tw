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
# <a name="create-grpc-client-libraries"></a><span data-ttu-id="90882-103">建立 gRPC 用戶端程式庫</span><span class="sxs-lookup"><span data-stu-id="90882-103">Create gRPC client libraries</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="90882-104">不需要散發 gPRC 應用程式的用戶端程式庫。</span><span class="sxs-lookup"><span data-stu-id="90882-104">It isn't necessary to distribute client libraries for a gPRC application.</span></span> <span data-ttu-id="90882-105">您可以在組織內建立檔案`.proto`的共用文件庫，而其他小組則可以使用這些檔案在自己的專案中產生用戶端程式代碼。</span><span class="sxs-lookup"><span data-stu-id="90882-105">You can create a shared library of `.proto` files within your organization, and other teams can use those files to generate client code in their own projects.</span></span> <span data-ttu-id="90882-106">但是，如果您有私用的 NuGet 存放庫，而且許多其他小組使用 .NET Core，則建立和發佈用戶端 NuGet 套件做為服務專案的一部分，可能是共用和升級服務的好方法。</span><span class="sxs-lookup"><span data-stu-id="90882-106">But if you have a private NuGet repository and many other teams are using .NET Core, creating and publishing client NuGet packages as part of your service project may be a good way of sharing and promoting your service.</span></span>

<span data-ttu-id="90882-107">散發用戶端程式庫的優點之一，是您可以使用實用的「便利性」方法和屬性，來增強產生的 gRPC 和 Protobuf 類別。</span><span class="sxs-lookup"><span data-stu-id="90882-107">One advantage of distributing a client library is that you can enhance the generated gRPC and Protobuf classes with helpful "convenience" methods and properties.</span></span> <span data-ttu-id="90882-108">在用戶端程式代碼中，就像在伺服器中一樣，所有類別`partial`都會宣告為，因此您可以在不編輯產生的程式碼的情況下擴充它們。</span><span class="sxs-lookup"><span data-stu-id="90882-108">In the client code, as in the server, all the classes are declared as `partial` so you can extend them without editing the generated code.</span></span> <span data-ttu-id="90882-109">這表示很容易就能將多個函式、方法、計算屬性和其他新增至基本類型。</span><span class="sxs-lookup"><span data-stu-id="90882-109">This means it's easy to add constructors, methods, calculated properties, and more to the basic types.</span></span>

> [!CAUTION]
> <span data-ttu-id="90882-110">您**不**應該使用自訂程式碼來提供基本的功能，因為這表示功能會限制為使用共用程式庫的 .net 小組，而不是使用 Python 或 JAVA 等其他語言或平臺的小組。</span><span class="sxs-lookup"><span data-stu-id="90882-110">You should **not** use custom code to provide essential functionality, as this would mean that functionality would be restricted to .NET teams using the shared library, and not to teams using other languages or platforms such as Python or Java.</span></span>

<span data-ttu-id="90882-111">在不同小組經常使用不同程式設計語言和架構的多平臺環境中，或您的 API 可從外部存取的情況`.proto`下，只需共用檔案，讓開發人員能夠產生自己的用戶端，是最佳的方式。請確定有許多小組可以存取您的 gRPC 服務。</span><span class="sxs-lookup"><span data-stu-id="90882-111">In a multi-platform environment where different teams frequently use different programming languages and frameworks, or where your API is externally accessible, simply sharing `.proto` files so developers can generate their own clients is the best way to ensure as many teams as possible can access your gRPC service.</span></span>

## <a name="useful-extensions"></a><span data-ttu-id="90882-112">有用的擴充功能</span><span class="sxs-lookup"><span data-stu-id="90882-112">Useful extensions</span></span>

<span data-ttu-id="90882-113">.Net 中有兩個常用的介面，可用來處理物件的資料流程<xref:System.Collections.Generic.IEnumerable%601> ： <xref:System.IObservable%601>和。</span><span class="sxs-lookup"><span data-stu-id="90882-113">There are two commonly used interfaces in .NET for dealing with streams of objects: <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IObservable%601>.</span></span> <span data-ttu-id="90882-114">從 .net Core 3.0 和C# 8.0 開始，有介面可<xref:System.Collections.Generic.IAsyncEnumerable%601> `await foreach`非同步處理資料流程，以及使用介面的語法。</span><span class="sxs-lookup"><span data-stu-id="90882-114">Starting with .NET Core 3.0 and C# 8.0, there's an <xref:System.Collections.Generic.IAsyncEnumerable%601> interface for processing streams asynchronously, and an `await foreach` syntax for using the interface.</span></span> <span data-ttu-id="90882-115">本節提供可重複使用的程式碼，以將這些介面套用至 gRPC 資料流程。</span><span class="sxs-lookup"><span data-stu-id="90882-115">This section presents reusable code for applying these interfaces to gRPC streams.</span></span>

<span data-ttu-id="90882-116">使用 .net Core gRPC 用戶端程式庫時，有`ReadAllAsync`一個適用`IAsyncStreamReader<T>`于的擴充方法`IAsyncEnumerable<T>`，可建立。</span><span class="sxs-lookup"><span data-stu-id="90882-116">With the .NET Core gRPC client libraries, there's a `ReadAllAsync` extension method for `IAsyncStreamReader<T>` that creates an `IAsyncEnumerable<T>`.</span></span> <span data-ttu-id="90882-117">對於使用被動程式設計的開發人員，建立的`IObservable<T>`對等擴充方法可能會如下所示。</span><span class="sxs-lookup"><span data-stu-id="90882-117">For developers using reactive programming, an equivalent extension method to create an `IObservable<T>` might look like this.</span></span>

### <a name="iobservable"></a><span data-ttu-id="90882-118">IObservable</span><span class="sxs-lookup"><span data-stu-id="90882-118">IObservable</span></span>

<span data-ttu-id="90882-119">介面是的「被動」 `IEnumerable<T>`反轉。 `IObservable<T>`</span><span class="sxs-lookup"><span data-stu-id="90882-119">The `IObservable<T>` interface is the "reactive" inverse of `IEnumerable<T>`.</span></span> <span data-ttu-id="90882-120">「回應式」方法不會從資料流程提取專案，而是讓資料流程將專案推送至「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="90882-120">Rather than pulling items from a stream, the reactive approach lets the stream push items to a subscriber.</span></span> <span data-ttu-id="90882-121">這與 gRPC 資料流程非常類似，而且很容易就能將其包裝`IObservable<T>`在`IAsyncStreamReader<T>`周圍。</span><span class="sxs-lookup"><span data-stu-id="90882-121">This is very similar to gRPC streams, and it's easy to wrap an `IObservable<T>` around an `IAsyncStreamReader<T>`.</span></span>

<span data-ttu-id="90882-122">這段程式碼的長度`IAsyncEnumerable<T>`超過程式C#代碼，因為沒有內建的支援可使用可預見值，因此必須以手動方式建立執行類別。</span><span class="sxs-lookup"><span data-stu-id="90882-122">This code is longer than the `IAsyncEnumerable<T>` code because C# doesn't have built-in support for working with observables, so the implementation class has to be created manually.</span></span> <span data-ttu-id="90882-123">不過，它是一個泛型類別，因此單一的執行方式可跨所有類型使用。</span><span class="sxs-lookup"><span data-stu-id="90882-123">It's a generic class, though, so a single implementation will work across all types.</span></span>

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
> <span data-ttu-id="90882-124">這個可觀察的`Subscribe`執行只允許呼叫一次方法，因為嘗試從資料流程讀取的多個訂閱者會導致混亂。</span><span class="sxs-lookup"><span data-stu-id="90882-124">This observable implementation only allows the `Subscribe` method to be called once, as having multiple subscribers trying to read from the stream would result in chaos.</span></span> <span data-ttu-id="90882-125">在可預見值[中，有](https://www.nuget.org/packages/System.Reactive.Linq)一些運算子（例如）會啟用緩衝處理和可重複使用的共用，以用於此實作為。 `Replay`</span><span class="sxs-lookup"><span data-stu-id="90882-125">There are operators such as `Replay` in the [System.Reactive.Linq](https://www.nuget.org/packages/System.Reactive.Linq) that enable buffering and repeatable sharing of observables, which can be used with this implementation.</span></span>

<span data-ttu-id="90882-126">類別會處理的列舉`IAsyncStreamReader`。 `GrpcStreamSubscription`</span><span class="sxs-lookup"><span data-stu-id="90882-126">The `GrpcStreamSubscription` class handles the enumeration of the `IAsyncStreamReader`.</span></span>

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

<span data-ttu-id="90882-127">現在只需要一個簡單的擴充方法，即可從串流讀取器建立可觀察的。</span><span class="sxs-lookup"><span data-stu-id="90882-127">All that is required now is a simple extension method to create the observable from the stream reader.</span></span>

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

## <a name="summary"></a><span data-ttu-id="90882-128">總結</span><span class="sxs-lookup"><span data-stu-id="90882-128">Summary</span></span>

<span data-ttu-id="90882-129">`IAsyncEnumerable` 和`IObservable`模型都是在 .net 中處理非同步資料資料流程的妥善支援和妥善記載的方式。</span><span class="sxs-lookup"><span data-stu-id="90882-129">The `IAsyncEnumerable` and `IObservable` models are both well-supported and well-documented ways of dealing with asynchronous streams of data in .NET.</span></span> <span data-ttu-id="90882-130">gRPC 串流會妥善對應到這兩個範例，以提供與現代化 .NET Core 架構的緊密整合，以及被動/非同步程式設計樣式。</span><span class="sxs-lookup"><span data-stu-id="90882-130">gRPC streams map well to both paradigms, offering close integration with the modern .NET Core framework and reactive/asynchronous programming styles.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="90882-131">[上一頁](streaming-versus-repeated.md)
>[下一頁](security.md)</span><span class="sxs-lookup"><span data-stu-id="90882-131">[Previous](streaming-versus-repeated.md)
[Next](security.md)</span></span>
