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
# <a name="create-grpc-client-libraries"></a><span data-ttu-id="c70c7-103">創建 gRPC 用戶端庫</span><span class="sxs-lookup"><span data-stu-id="c70c7-103">Create gRPC client libraries</span></span>

<span data-ttu-id="c70c7-104">不需要為 gRPC 應用程式分發用戶端庫。</span><span class="sxs-lookup"><span data-stu-id="c70c7-104">It isn't necessary to distribute client libraries for a gRPC application.</span></span> <span data-ttu-id="c70c7-105">您可以在組織內創建檔共用`.proto`庫，其他團隊可以使用這些檔在他們自己的專案中生成用戶端代碼。</span><span class="sxs-lookup"><span data-stu-id="c70c7-105">You can create a shared library of `.proto` files within your organization, and other teams can use those files to generate client code in their own projects.</span></span> <span data-ttu-id="c70c7-106">但是，如果您有一個私有的 NuGet 存儲庫，並且許多其他團隊正在使用 .NET Core，則可以創建和發佈用戶端 NuGet 包，作為服務專案的一部分。</span><span class="sxs-lookup"><span data-stu-id="c70c7-106">But if you have a private NuGet repository and many other teams are using .NET Core, you can create and publish client NuGet packages as part of your service project.</span></span> <span data-ttu-id="c70c7-107">這是分享和推廣服務的好方法。</span><span class="sxs-lookup"><span data-stu-id="c70c7-107">This can be a good way of sharing and promoting your service.</span></span>

<span data-ttu-id="c70c7-108">分發用戶端庫的一個優點是，您可以使用有用的"方便"方法和屬性增強生成的 gRPC 和 Protobuf 類。</span><span class="sxs-lookup"><span data-stu-id="c70c7-108">One advantage of distributing a client library is that you can enhance the generated gRPC and Protobuf classes with helpful "convenience" methods and properties.</span></span> <span data-ttu-id="c70c7-109">在用戶端代碼中，如在伺服器中，所有類都聲明為`partial`，因此您可以擴展它們，而無需編輯生成的代碼。</span><span class="sxs-lookup"><span data-stu-id="c70c7-109">In the client code, as in the server, all the classes are declared as `partial`, so you can extend them without editing the generated code.</span></span> <span data-ttu-id="c70c7-110">這意味著可以輕鬆地將建構函式、方法和計算屬性添加到基本類型。</span><span class="sxs-lookup"><span data-stu-id="c70c7-110">This means it's easy to add constructors, methods, and calculated properties to the basic types.</span></span>

> [!CAUTION]
> <span data-ttu-id="c70c7-111">不應使用自訂代碼來提供基本功能。</span><span class="sxs-lookup"><span data-stu-id="c70c7-111">You shouldn't use custom code to provide essential functionality.</span></span> <span data-ttu-id="c70c7-112">您不希望將該基本功能限制為使用共用庫的 .NET 團隊，而不是將其提供給使用其他語言或平臺（如 Python 或 JAVA）的團隊。</span><span class="sxs-lookup"><span data-stu-id="c70c7-112">You don't want to restrict that essential functionality to .NET teams that use the shared library, and not provide it to teams that use other languages or platforms, such as Python or Java.</span></span>

<span data-ttu-id="c70c7-113">確保盡可能多的團隊可以訪問您的 gRPC 服務。</span><span class="sxs-lookup"><span data-stu-id="c70c7-113">Ensure that as many teams as possible can access your gRPC service.</span></span> <span data-ttu-id="c70c7-114">最好的方法是共用`.proto`檔，以便開發人員可以生成自己的用戶端。</span><span class="sxs-lookup"><span data-stu-id="c70c7-114">The best way to do this is to share `.proto` files so developers can generate their own clients.</span></span> <span data-ttu-id="c70c7-115">在多平臺環境中尤其如此，其中不同的團隊經常使用不同的程式設計語言和框架，或者 API 是外部可訪問的。</span><span class="sxs-lookup"><span data-stu-id="c70c7-115">This is particularly true in a multi-platform environment, where different teams frequently use different programming languages and frameworks, or where your API is externally accessible.</span></span>

## <a name="useful-extensions"></a><span data-ttu-id="c70c7-116">有用的擴展</span><span class="sxs-lookup"><span data-stu-id="c70c7-116">Useful extensions</span></span>

<span data-ttu-id="c70c7-117">.NET 中有兩個常用介面用於處理物件流：<xref:System.Collections.Generic.IEnumerable%601>和<xref:System.IObservable%601>。</span><span class="sxs-lookup"><span data-stu-id="c70c7-117">There are two commonly used interfaces in .NET for dealing with streams of objects: <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IObservable%601>.</span></span> <span data-ttu-id="c70c7-118">從 .NET Core 3.0 和 C# 8.0<xref:System.Collections.Generic.IAsyncEnumerable%601>開始，有一個用於非同步處理`await foreach`流的介面，以及一個用於使用該介面的語法。</span><span class="sxs-lookup"><span data-stu-id="c70c7-118">Starting with .NET Core 3.0 and C# 8.0, there's an <xref:System.Collections.Generic.IAsyncEnumerable%601> interface for processing streams asynchronously, and an `await foreach` syntax for using the interface.</span></span> <span data-ttu-id="c70c7-119">本節介紹將這些介面應用於 gRPC 流的可重用代碼。</span><span class="sxs-lookup"><span data-stu-id="c70c7-119">This section presents reusable code for applying these interfaces to gRPC streams.</span></span>

<span data-ttu-id="c70c7-120">使用 .NET Core gRPC 用戶端庫時，有`ReadAllAsync`一種擴展`IAsyncStreamReader<T>`方法用於創建`IAsyncEnumerable<T>`介面。</span><span class="sxs-lookup"><span data-stu-id="c70c7-120">With the .NET Core gRPC client libraries, there's a `ReadAllAsync` extension method for `IAsyncStreamReader<T>` that creates an `IAsyncEnumerable<T>` interface.</span></span> <span data-ttu-id="c70c7-121">對於使用反應式程式設計的開發人員，創建介面的`IObservable<T>`等效擴充方法可能類似于下一節中的示例。</span><span class="sxs-lookup"><span data-stu-id="c70c7-121">For developers using reactive programming, an equivalent extension method to create an `IObservable<T>` interface might look like the example in the following section.</span></span>

### <a name="iobservable"></a><span data-ttu-id="c70c7-122">可觀察</span><span class="sxs-lookup"><span data-stu-id="c70c7-122">IObservable</span></span>

<span data-ttu-id="c70c7-123">介面`IObservable<T>`是 中的"反應"反對。 `IEnumerable<T>`</span><span class="sxs-lookup"><span data-stu-id="c70c7-123">The `IObservable<T>` interface is the "reactive" inverse of `IEnumerable<T>`.</span></span> <span data-ttu-id="c70c7-124">被動方法允許流將專案推送到訂閱伺服器，而不是從流中提取專案。</span><span class="sxs-lookup"><span data-stu-id="c70c7-124">Rather than pulling items from a stream, the reactive approach lets the stream push items to a subscriber.</span></span> <span data-ttu-id="c70c7-125">這與 gRPC 流非常相似，並且很容易圍繞`IObservable<T>``IAsyncStreamReader<T>`介面包裝介面。</span><span class="sxs-lookup"><span data-stu-id="c70c7-125">This is very similar to gRPC streams, and it's easy to wrap an `IObservable<T>` interface around an `IAsyncStreamReader<T>` interface.</span></span>

<span data-ttu-id="c70c7-126">此代碼比`IAsyncEnumerable<T>`代碼長，因為 C# 沒有內置支援使用可觀察器。</span><span class="sxs-lookup"><span data-stu-id="c70c7-126">This code is longer than the `IAsyncEnumerable<T>` code, because C# doesn't have built-in support for working with observables.</span></span> <span data-ttu-id="c70c7-127">您必須手動創建實現類。</span><span class="sxs-lookup"><span data-stu-id="c70c7-127">You have to create the implementation class manually.</span></span> <span data-ttu-id="c70c7-128">但它是一個泛型類，因此單個實現適用于所有類型。</span><span class="sxs-lookup"><span data-stu-id="c70c7-128">It's a generic class, though, so a single implementation works across all types.</span></span>

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
> <span data-ttu-id="c70c7-129">此可觀察的實現只允許`Subscribe`調用一次該方法，因為有多個訂閱者嘗試從流中讀取將導致混亂。</span><span class="sxs-lookup"><span data-stu-id="c70c7-129">This observable implementation allows the `Subscribe` method to be called only once, because having multiple subscribers trying to read from the stream would result in chaos.</span></span> <span data-ttu-id="c70c7-130">有運算子，如`Replay` [System.Reactive.Linq，](https://www.nuget.org/packages/System.Reactive.Linq)它們支援可觀察的緩衝和可重複共用，這些可與此實現一起使用。</span><span class="sxs-lookup"><span data-stu-id="c70c7-130">There are operators, such as `Replay` in the [System.Reactive.Linq](https://www.nuget.org/packages/System.Reactive.Linq), that enable buffering and repeatable sharing of observables, which can be used with this implementation.</span></span>

<span data-ttu-id="c70c7-131">類`GrpcStreamSubscription`處理 的`IAsyncStreamReader`枚舉：</span><span class="sxs-lookup"><span data-stu-id="c70c7-131">The `GrpcStreamSubscription` class handles the enumeration of the `IAsyncStreamReader`:</span></span>

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

<span data-ttu-id="c70c7-132">現在只需要一個簡單的擴充方法，從流讀取器創建可觀察的。</span><span class="sxs-lookup"><span data-stu-id="c70c7-132">All that is required now is a simple extension method to create the observable from the stream reader.</span></span>

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

## <a name="summary"></a><span data-ttu-id="c70c7-133">摘要</span><span class="sxs-lookup"><span data-stu-id="c70c7-133">Summary</span></span>

<span data-ttu-id="c70c7-134">和`IAsyncEnumerable``IObservable`模型都是支援良好且記錄良好的處理 .NET 中非同步資料流程的方法。</span><span class="sxs-lookup"><span data-stu-id="c70c7-134">The `IAsyncEnumerable` and `IObservable` models are both well-supported and well-documented ways of dealing with asynchronous streams of data in .NET.</span></span> <span data-ttu-id="c70c7-135">gRPC 流很好地映射到這兩種範例，提供與 .NET Core 以及被動和非同步程式設計樣式的緊密集成。</span><span class="sxs-lookup"><span data-stu-id="c70c7-135">gRPC streams map well to both paradigms, offering close integration with .NET Core, and reactive and asynchronous programming styles.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c70c7-136">[上一個](streaming-versus-repeated.md)
>[下一個](security.md)</span><span class="sxs-lookup"><span data-stu-id="c70c7-136">[Previous](streaming-versus-repeated.md)
[Next](security.md)</span></span>
