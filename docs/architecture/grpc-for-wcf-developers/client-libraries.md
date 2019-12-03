---
title: 建立 gRPC 用戶端程式庫-適用于 WCF 開發人員的 gRPC
description: 討論 gRPC 服務的共用用戶端程式庫/套件。
ms.date: 09/02/2019
ms.openlocfilehash: bb58cb3cda4b0cbb3a5d34129961349bcb0093e9
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711462"
---
# <a name="create-grpc-client-libraries"></a><span data-ttu-id="31f05-103">建立 gRPC 用戶端程式庫</span><span class="sxs-lookup"><span data-stu-id="31f05-103">Create gRPC client libraries</span></span>

<span data-ttu-id="31f05-104">不需要散發 gRPC 應用程式的用戶端程式庫。</span><span class="sxs-lookup"><span data-stu-id="31f05-104">It isn't necessary to distribute client libraries for a gRPC application.</span></span> <span data-ttu-id="31f05-105">您可以在組織內建立 `.proto` 檔案的共用程式庫，而其他小組則可以使用這些檔案在自己的專案中產生用戶端程式代碼。</span><span class="sxs-lookup"><span data-stu-id="31f05-105">You can create a shared library of `.proto` files within your organization, and other teams can use those files to generate client code in their own projects.</span></span> <span data-ttu-id="31f05-106">但是，如果您有私用的 NuGet 存放庫，而且有許多其他小組使用 .NET Core，您就可以建立用戶端 NuGet 封裝，並將其發佈為服務專案的一部分。</span><span class="sxs-lookup"><span data-stu-id="31f05-106">But if you have a private NuGet repository and many other teams are using .NET Core, you can create and publish client NuGet packages as part of your service project.</span></span> <span data-ttu-id="31f05-107">這可以是共用和推廣服務的好方法。</span><span class="sxs-lookup"><span data-stu-id="31f05-107">This can be a good way of sharing and promoting your service.</span></span>

<span data-ttu-id="31f05-108">散發用戶端程式庫的優點之一，是您可以使用實用的「便利性」方法和屬性，來增強產生的 gRPC 和 Protobuf 類別。</span><span class="sxs-lookup"><span data-stu-id="31f05-108">One advantage of distributing a client library is that you can enhance the generated gRPC and Protobuf classes with helpful "convenience" methods and properties.</span></span> <span data-ttu-id="31f05-109">在用戶端程式代碼中，就像在伺服器中一樣，所有類別都會宣告為 `partial`，因此您可以擴充它們，而不需要編輯產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="31f05-109">In the client code, as in the server, all the classes are declared as `partial`, so you can extend them without editing the generated code.</span></span> <span data-ttu-id="31f05-110">這表示，您可以輕鬆地將「函式」、「方法」和「計算」屬性加入至基本類型。</span><span class="sxs-lookup"><span data-stu-id="31f05-110">This means it's easy to add constructors, methods, and calculated properties to the basic types.</span></span>

> [!CAUTION]
> <span data-ttu-id="31f05-111">您不應該使用自訂程式碼來提供基本功能。</span><span class="sxs-lookup"><span data-stu-id="31f05-111">You shouldn't use custom code to provide essential functionality.</span></span> <span data-ttu-id="31f05-112">您不想要將該基本功能限制為使用共用程式庫的 .NET 小組，而不是將其提供給使用其他語言或平臺的小組，例如 Python 或 JAVA。</span><span class="sxs-lookup"><span data-stu-id="31f05-112">You don't want to restrict that essential functionality to .NET teams that use the shared library, and not provide it to teams that use other languages or platforms, such as Python or Java.</span></span>

<span data-ttu-id="31f05-113">請確定有許多小組可以存取您的 gRPC 服務。</span><span class="sxs-lookup"><span data-stu-id="31f05-113">Ensure that as many teams as possible can access your gRPC service.</span></span> <span data-ttu-id="31f05-114">這麼做的最佳方式是共用 `.proto` 檔案，讓開發人員可以產生自己的用戶端。</span><span class="sxs-lookup"><span data-stu-id="31f05-114">The best way to do this is to share `.proto` files so developers can generate their own clients.</span></span> <span data-ttu-id="31f05-115">這特別適用于多平臺環境，其中不同的小組經常使用不同的程式設計語言和架構，或者您的 API 可從外部存取。</span><span class="sxs-lookup"><span data-stu-id="31f05-115">This is particularly true in a multi-platform environment, where different teams frequently use different programming languages and frameworks, or where your API is externally accessible.</span></span>

## <a name="useful-extensions"></a><span data-ttu-id="31f05-116">有用的擴充功能</span><span class="sxs-lookup"><span data-stu-id="31f05-116">Useful extensions</span></span>

<span data-ttu-id="31f05-117">.NET 中有兩個常用的介面，可用來處理物件的資料流程： <xref:System.Collections.Generic.IEnumerable%601> 和 <xref:System.IObservable%601>。</span><span class="sxs-lookup"><span data-stu-id="31f05-117">There are two commonly used interfaces in .NET for dealing with streams of objects: <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IObservable%601>.</span></span> <span data-ttu-id="31f05-118">從 .NET Core 3.0 和C# 8.0 開始，有一個用來非同步處理資料流程的 <xref:System.Collections.Generic.IAsyncEnumerable%601> 介面，以及使用介面的 `await foreach` 語法。</span><span class="sxs-lookup"><span data-stu-id="31f05-118">Starting with .NET Core 3.0 and C# 8.0, there's an <xref:System.Collections.Generic.IAsyncEnumerable%601> interface for processing streams asynchronously, and an `await foreach` syntax for using the interface.</span></span> <span data-ttu-id="31f05-119">本節提供可重複使用的程式碼，以將這些介面套用至 gRPC 資料流程。</span><span class="sxs-lookup"><span data-stu-id="31f05-119">This section presents reusable code for applying these interfaces to gRPC streams.</span></span>

<span data-ttu-id="31f05-120">有了 .NET Core gRPC 用戶端程式庫，`IAsyncStreamReader<T>` 的 `ReadAllAsync` 擴充方法會建立 `IAsyncEnumerable<T>` 介面。</span><span class="sxs-lookup"><span data-stu-id="31f05-120">With the .NET Core gRPC client libraries, there's a `ReadAllAsync` extension method for `IAsyncStreamReader<T>` that creates an `IAsyncEnumerable<T>` interface.</span></span> <span data-ttu-id="31f05-121">對於使用被動程式設計的開發人員而言，建立 `IObservable<T>` 介面的同等擴充方法可能會類似下一節中的範例。</span><span class="sxs-lookup"><span data-stu-id="31f05-121">For developers using reactive programming, an equivalent extension method to create an `IObservable<T>` interface might look like the example in the following section.</span></span>

### <a name="iobservable"></a><span data-ttu-id="31f05-122">IObservable</span><span class="sxs-lookup"><span data-stu-id="31f05-122">IObservable</span></span>

<span data-ttu-id="31f05-123">`IObservable<T>` 介面是 `IEnumerable<T>`的「被動」反轉。</span><span class="sxs-lookup"><span data-stu-id="31f05-123">The `IObservable<T>` interface is the "reactive" inverse of `IEnumerable<T>`.</span></span> <span data-ttu-id="31f05-124">「回應式」方法不會從資料流程提取專案，而是讓資料流程將專案推送至「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="31f05-124">Rather than pulling items from a stream, the reactive approach lets the stream push items to a subscriber.</span></span> <span data-ttu-id="31f05-125">這與 gRPC 資料流程非常類似，而且可以輕鬆地在 `IAsyncStreamReader<T>` 介面周圍包裝 `IObservable<T>` 介面。</span><span class="sxs-lookup"><span data-stu-id="31f05-125">This is very similar to gRPC streams, and it's easy to wrap an `IObservable<T>` interface around an `IAsyncStreamReader<T>` interface.</span></span>

<span data-ttu-id="31f05-126">此程式碼的長度超過 `IAsyncEnumerable<T>` 的程式碼C# ，因為沒有使用可預見值的內建支援。</span><span class="sxs-lookup"><span data-stu-id="31f05-126">This code is longer than the `IAsyncEnumerable<T>` code, because C# doesn't have built-in support for working with observables.</span></span> <span data-ttu-id="31f05-127">您必須手動建立實類別。</span><span class="sxs-lookup"><span data-stu-id="31f05-127">You have to create the implementation class manually.</span></span> <span data-ttu-id="31f05-128">不過，它是一個泛型類別，因此單一的實作用會跨所有類型運作。</span><span class="sxs-lookup"><span data-stu-id="31f05-128">It's a generic class, though, so a single implementation works across all types.</span></span>

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
> <span data-ttu-id="31f05-129">這個可觀察的執行只會呼叫一次 `Subscribe` 方法，因為嘗試從資料流程讀取的多個訂閱者會導致混亂。</span><span class="sxs-lookup"><span data-stu-id="31f05-129">This observable implementation allows the `Subscribe` method to be called only once, because having multiple subscribers trying to read from the stream would result in chaos.</span></span> <span data-ttu-id="31f05-130">在可預見值中，有一些運算子（`Replay`[例如）會](https://www.nuget.org/packages/System.Reactive.Linq)啟用緩衝和可重複共用的，這可以與此實作為搭配使用。</span><span class="sxs-lookup"><span data-stu-id="31f05-130">There are operators, such as `Replay` in the [System.Reactive.Linq](https://www.nuget.org/packages/System.Reactive.Linq), that enable buffering and repeatable sharing of observables, which can be used with this implementation.</span></span>

<span data-ttu-id="31f05-131">`GrpcStreamSubscription` 類別會處理 `IAsyncStreamReader`的列舉：</span><span class="sxs-lookup"><span data-stu-id="31f05-131">The `GrpcStreamSubscription` class handles the enumeration of the `IAsyncStreamReader`:</span></span>

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

<span data-ttu-id="31f05-132">現在只需要一個簡單的擴充方法，即可從串流讀取器建立可觀察的。</span><span class="sxs-lookup"><span data-stu-id="31f05-132">All that is required now is a simple extension method to create the observable from the stream reader.</span></span>

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

## <a name="summary"></a><span data-ttu-id="31f05-133">總結</span><span class="sxs-lookup"><span data-stu-id="31f05-133">Summary</span></span>

<span data-ttu-id="31f05-134">`IAsyncEnumerable` 和 `IObservable` 模型都是受到妥善支援的方式，也是在 .NET 中處理非同步資料資料流程的完整記錄方法。</span><span class="sxs-lookup"><span data-stu-id="31f05-134">The `IAsyncEnumerable` and `IObservable` models are both well-supported and well-documented ways of dealing with asynchronous streams of data in .NET.</span></span> <span data-ttu-id="31f05-135">gRPC 串流會妥善對應到兩個範例，提供與 .NET Core 的緊密整合，以及回應式和非同步程式設計樣式。</span><span class="sxs-lookup"><span data-stu-id="31f05-135">gRPC streams map well to both paradigms, offering close integration with .NET Core, and reactive and asynchronous programming styles.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="31f05-136">[上一頁](streaming-versus-repeated.md)
>[下一頁](security.md)</span><span class="sxs-lookup"><span data-stu-id="31f05-136">[Previous](streaming-versus-repeated.md)
[Next](security.md)</span></span>
