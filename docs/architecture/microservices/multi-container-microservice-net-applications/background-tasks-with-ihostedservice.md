---
title: 在微服務中使用 IHostedService 和 BackgroundService 類別實作背景工作
description: .NET 微服務：容器化 .NET 應用程式的架構 | 了解在微服務 .NET Core 使用 IHostedService 和 BackgroundService 實作背景工作的新選項。
ms.date: 08/14/2020
ms.openlocfilehash: 4ab215f2196cd2e66b116465c3a582a9846c8066
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267993"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a><span data-ttu-id="79279-103">在微服務中使用 IHostedService 和 BackgroundService 類別實作背景工作</span><span class="sxs-lookup"><span data-stu-id="79279-103">Implement background tasks in microservices with IHostedService and the BackgroundService class</span></span>

<span data-ttu-id="79279-104">背景工作和排程工作是您可能需要在任何應用程式中使用的內容，不論它是否遵循微服務架構模式。</span><span class="sxs-lookup"><span data-stu-id="79279-104">Background tasks and scheduled jobs are something you might need to use in any application, whether or not it follows the microservices architecture pattern.</span></span> <span data-ttu-id="79279-105">使用微服務架構的差異在於，您可以在個別的進程/容器中執行背景工作來進行裝載，讓您可以根據您的需求相應減少/相應減少。</span><span class="sxs-lookup"><span data-stu-id="79279-105">The difference when using a microservices architecture is that you can implement the background task in a separate process/container for hosting so you can scale it down/up based on your need.</span></span>

<span data-ttu-id="79279-106">從一般觀點而言，在 .NET Core 中，我們將這些類型的工作稱為「託管服務」\*\*，因為它們是您在主機/應用程式/微服務內裝載的服務/邏輯。</span><span class="sxs-lookup"><span data-stu-id="79279-106">From a generic point of view, in .NET Core we called these type of tasks *Hosted Services*, because they are services/logic that you host within your host/application/microservice.</span></span> <span data-ttu-id="79279-107">請注意，在此情況下，託管服務就只是具有背景工作邏輯的類別。</span><span class="sxs-lookup"><span data-stu-id="79279-107">Note that in this case, the hosted service simply means a class with the background task logic.</span></span>

<span data-ttu-id="79279-108">自 .NET Core 2.0 開始，此架構提供名為 <xref:Microsoft.Extensions.Hosting.IHostedService> 的新介面，協助您輕鬆地實作託管服務。</span><span class="sxs-lookup"><span data-stu-id="79279-108">Since .NET Core 2.0, the framework provides a new interface named <xref:Microsoft.Extensions.Hosting.IHostedService> helping you to easily implement hosted services.</span></span> <span data-ttu-id="79279-109">基本概念是，您可以將多個背景工作註冊 (裝載的服務) 在您的 web 主機或主機正在執行時于背景中執行，如映射6-26 所示。</span><span class="sxs-lookup"><span data-stu-id="79279-109">The basic idea is that you can register multiple background tasks (hosted services) that run in the background while your web host or host is running, as shown in the image 6-26.</span></span>

![比較 ASP.NET Core IWebHost 和 .NET Core IHost 的圖表。](./media/background-tasks-with-ihostedservice/ihosted-service-webhost-vs-host.png)

<span data-ttu-id="79279-111">**圖 6-26**。</span><span class="sxs-lookup"><span data-stu-id="79279-111">**Figure 6-26**.</span></span> <span data-ttu-id="79279-112">在 WebHost 與主機中使用 IHostedService</span><span class="sxs-lookup"><span data-stu-id="79279-112">Using IHostedService in a WebHost vs. a Host</span></span>

<span data-ttu-id="79279-113">ASP.NET Core 1.x 和2.x 支援 `IWebHost` web 應用程式中的背景進程。</span><span class="sxs-lookup"><span data-stu-id="79279-113">ASP.NET Core 1.x and 2.x support `IWebHost` for background processes in web apps.</span></span> <span data-ttu-id="79279-114">.NET Core 2.1 和更新版本支援 `IHost` 具有一般主控台應用程式的背景處理常式。</span><span class="sxs-lookup"><span data-stu-id="79279-114">.NET Core 2.1 and later versions support `IHost` for background processes with plain console apps.</span></span> <span data-ttu-id="79279-115">請注意 `WebHost` 與 `Host` 之間的差異。</span><span class="sxs-lookup"><span data-stu-id="79279-115">Note the difference made between `WebHost` and `Host`.</span></span>

<span data-ttu-id="79279-116">在 `WebHost` `IWebHost` ASP.NET Core 2.0 中執行) 的 (基類是您用來提供 HTTP 伺服器功能給程式的基礎結構成品，例如當您在執行 MVC web 應用程式或 web API 服務時。</span><span class="sxs-lookup"><span data-stu-id="79279-116">A `WebHost` (base class implementing `IWebHost`) in ASP.NET Core 2.0 is the infrastructure artifact you use to provide HTTP server features to your process, such as when you're implementing an MVC web app or Web API service.</span></span> <span data-ttu-id="79279-117">它提供 ASP.NET Core 中的所有新基礎結構，讓您可以使用相依性插入、在要求管線中插入中介軟體，以及類似的。</span><span class="sxs-lookup"><span data-stu-id="79279-117">It provides all the new infrastructure goodness in ASP.NET Core, enabling you to use dependency injection, insert middlewares in the request pipeline, and similar.</span></span> <span data-ttu-id="79279-118">對於背景工作而言，會 `WebHost` 使用這些非常相同的 `IHostedServices` 。</span><span class="sxs-lookup"><span data-stu-id="79279-118">The `WebHost` uses these very same `IHostedServices` for background tasks.</span></span>

<span data-ttu-id="79279-119">.NET Core 2.1 中引進了 `Host` (實作 `IHost` 的基底類別)。</span><span class="sxs-lookup"><span data-stu-id="79279-119">A `Host` (base class implementing `IHost`) was introduced in .NET Core 2.1.</span></span> <span data-ttu-id="79279-120">基本上，`Host` 可讓您擁有與 `WebHost` 類似的基礎結構 (相依性插入、託管服務等等)，但在此情況下，您只想要有主機的簡單且輕量程序，而不想要有與 MVC、Web API 或 HTTP 伺服器功能有關的程序。</span><span class="sxs-lookup"><span data-stu-id="79279-120">Basically, a `Host` allows you to have a similar infrastructure than what you have with `WebHost` (dependency injection, hosted services, etc.), but in this case, you just want to have a simple and lighter process as the host, with nothing related to MVC, Web API or HTTP server features.</span></span>

<span data-ttu-id="79279-121">因此，您可以選擇建立特製化的主機程式，並使用 `IHost` 來處理裝載的服務，而不需要任何其他專案（例如微服務）， `IHostedServices` 或者您也可以擴充現有的 ASP.NET Core `WebHost` ，例如現有的 ASP.NET Core WEB API 或 MVC 應用程式。</span><span class="sxs-lookup"><span data-stu-id="79279-121">Therefore, you can choose and either create a specialized host-process with `IHost` to handle the hosted services and nothing else, such a microservice made just for hosting the `IHostedServices`, or you can alternatively extend an existing ASP.NET Core `WebHost`, such as an existing ASP.NET Core Web API or MVC app.</span></span>

<span data-ttu-id="79279-122">根據您的商務和延展性需求，每種方法都有其優缺點。</span><span class="sxs-lookup"><span data-stu-id="79279-122">Each approach has pros and cons depending on your business and scalability needs.</span></span> <span data-ttu-id="79279-123">重點是，如果您的背景工作與 HTTP (無關， `IWebHost` 您應該使用的) `IHost` 。</span><span class="sxs-lookup"><span data-stu-id="79279-123">The bottom line is basically that if your background tasks have nothing to do with HTTP (`IWebHost`) you should use `IHost`.</span></span>

## <a name="registering-hosted-services-in-your-webhost-or-host"></a><span data-ttu-id="79279-124">在 WebHost 或主機中註冊託管服務</span><span class="sxs-lookup"><span data-stu-id="79279-124">Registering hosted services in your WebHost or Host</span></span>

<span data-ttu-id="79279-125">讓我們進一步向下切入 `IHostedService` 介面，因為在或中，其使用方式相當類似 `WebHost` `Host` 。</span><span class="sxs-lookup"><span data-stu-id="79279-125">Let's drill down further on the `IHostedService` interface since its usage is pretty similar in a `WebHost` or in a `Host`.</span></span>

<span data-ttu-id="79279-126">SignalR 是使用託管服務之成品的一個範例，但您也可以將它用於下列更簡單的事項：</span><span class="sxs-lookup"><span data-stu-id="79279-126">SignalR is one example of an artifact using hosted services, but you can also use it for much simpler things like:</span></span>

- <span data-ttu-id="79279-127">輪詢資料庫以找出變更的背景工作。</span><span class="sxs-lookup"><span data-stu-id="79279-127">A background task polling a database looking for changes.</span></span>
- <span data-ttu-id="79279-128">定期更新某個快取的已排定工作。</span><span class="sxs-lookup"><span data-stu-id="79279-128">A scheduled task updating some cache periodically.</span></span>
- <span data-ttu-id="79279-129">允許在背景執行緒上執行工作的 QueueBackgroundWorkItem 實作。</span><span class="sxs-lookup"><span data-stu-id="79279-129">An implementation of QueueBackgroundWorkItem that allows a task to be executed on a background thread.</span></span>
- <span data-ttu-id="79279-130">在共用 `ILogger` 這類通用服務時，於 Web 應用程式背景處理來自佇列的訊息。</span><span class="sxs-lookup"><span data-stu-id="79279-130">Processing messages from a message queue in the background of a web app while sharing common services such as `ILogger`.</span></span>
- <span data-ttu-id="79279-131">使用 `Task.Run()` 啟動的背景工作。</span><span class="sxs-lookup"><span data-stu-id="79279-131">A background task started with `Task.Run()`.</span></span>

<span data-ttu-id="79279-132">基本上，您可以將任何這些動作卸載至執行的背景工作 `IHostedService` 。</span><span class="sxs-lookup"><span data-stu-id="79279-132">You can basically offload any of those actions to a background task that implements `IHostedService`.</span></span>

<span data-ttu-id="79279-133">您將一或多個加入 `IHostedServices` 至或中的方法 `WebHost` `Host` 是透過 <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A>   ASP.NET Core (中的擴充方法， `WebHost` 或在 `Host` .net Core 2.1 和更新版本) 中的擴充方法來註冊它們。</span><span class="sxs-lookup"><span data-stu-id="79279-133">The way you add one or multiple `IHostedServices` into your `WebHost` or `Host` is by registering them up through the <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A> extension method in an ASP.NET Core `WebHost` (or in a `Host` in .NET Core 2.1 and above).</span></span> <span data-ttu-id="79279-134">基本上，您必須在 `Startup` 類別的熟悉 `ConfigureServices()` 方法內註冊託管服務，如典型 ASP.NET WebHost 中的下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="79279-134">Basically, you have to register the hosted services within the familiar `ConfigureServices()` method of the `Startup` class, as in the following code from a typical ASP.NET WebHost.</span></span>

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    //Other DI registrations;

    // Register Hosted Services
    services.AddHostedService<GracePeriodManagerService>();
    services.AddHostedService<MyHostedServiceB>();
    services.AddHostedService<MyHostedServiceC>();
    //...
}
```

<span data-ttu-id="79279-135">在該程式碼中，`GracePeriodManagerService` 託管服務是 eShopOnContainers 中來自 Ordering 商務微服務的真正程式碼，另兩個就只是兩個其他範例。</span><span class="sxs-lookup"><span data-stu-id="79279-135">In that code, the `GracePeriodManagerService` hosted service is real code from the Ordering business microservice in eShopOnContainers, while the other two are just two additional samples.</span></span>

<span data-ttu-id="79279-136">`IHostedService` 背景工作執行會與應用程式 (就此而言，是主機或微服務) 存留期一致。</span><span class="sxs-lookup"><span data-stu-id="79279-136">The `IHostedService` background task execution is coordinated with the lifetime of the application (host or microservice, for that matter).</span></span> <span data-ttu-id="79279-137">您在應用程式啟動時註冊工作，並且在關閉應用程式時，有機會依正常程序進行某個動作或清除。</span><span class="sxs-lookup"><span data-stu-id="79279-137">You register tasks when the application starts and you have the opportunity to do some graceful action or clean-up when the application is shutting down.</span></span>

<span data-ttu-id="79279-138">不使用 `IHostedService`，您還是一律可以啟動背景執行緒來執行任何工作。</span><span class="sxs-lookup"><span data-stu-id="79279-138">Without using `IHostedService`, you could always start a background thread to run any task.</span></span> <span data-ttu-id="79279-139">當應用程式關閉時，該執行緒只會在沒有機會執行正常清除動作的情況下結束時，就會有很大的差異。</span><span class="sxs-lookup"><span data-stu-id="79279-139">The difference is precisely at the app's shutdown time when that thread would simply be killed without having the opportunity to run graceful clean-up actions.</span></span>

## <a name="the-ihostedservice-interface"></a><span data-ttu-id="79279-140">IHostedService 介面</span><span class="sxs-lookup"><span data-stu-id="79279-140">The IHostedService interface</span></span>

<span data-ttu-id="79279-141">註冊 `IHostedService` 時，.NET Core 將會在應用程式啟動和停止期間分別呼叫 `IHostedService` 型別的 `StartAsync()` 和 `StopAsync()` 方法。</span><span class="sxs-lookup"><span data-stu-id="79279-141">When you register an `IHostedService`, .NET Core will call the `StartAsync()` and `StopAsync()` methods of your `IHostedService` type during application start and stop respectively.</span></span> <span data-ttu-id="79279-142">如需詳細資訊，請參閱 [IHostedService 介面](https://docs.microsoft.com/aspnet/core/fundamentals/host/hosted-services?view=aspnetcore-3.1&tabs=visual-studio#ihostedservice-interface)</span><span class="sxs-lookup"><span data-stu-id="79279-142">For more details, refer [IHostedService interface](https://docs.microsoft.com/aspnet/core/fundamentals/host/hosted-services?view=aspnetcore-3.1&tabs=visual-studio#ihostedservice-interface)</span></span>

<span data-ttu-id="79279-143">假設您可以建立多個 IHostedService 實作，並在 `ConfigureService()` 方法中將它們註冊至 DI 容器，如前所示。</span><span class="sxs-lookup"><span data-stu-id="79279-143">As you can imagine, you can create multiple implementations of IHostedService and register them at the `ConfigureService()` method into the DI container, as shown previously.</span></span> <span data-ttu-id="79279-144">將會啟動與停止所有這些託管服務以及應用程式/微服務。</span><span class="sxs-lookup"><span data-stu-id="79279-144">All those hosted services will be started and stopped along with the application/microservice.</span></span>

<span data-ttu-id="79279-145">身為開發人員，您負責在主機觸發 `StopAsync()` 方法時處理停止動作或服務。</span><span class="sxs-lookup"><span data-stu-id="79279-145">As a developer, you are responsible for handling the stopping action of your services when `StopAsync()` method is triggered by the host.</span></span>

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a><span data-ttu-id="79279-146">使用衍生自 BackgroundService 基底類別的自訂託管服務類別來實作 IHostedService</span><span class="sxs-lookup"><span data-stu-id="79279-146">Implementing IHostedService with a custom hosted service class deriving from the BackgroundService base class</span></span>

<span data-ttu-id="79279-147">您可以繼續並從頭開始建立自訂託管服務類別，並實作 `IHostedService`，就像使用 .NET Core 2.0 時所需執行的作業。</span><span class="sxs-lookup"><span data-stu-id="79279-147">You could go ahead and create your custom hosted service class from scratch and implement the `IHostedService`, as you need to do when using .NET Core 2.0.</span></span>

<span data-ttu-id="79279-148">不過，因為大部分背景工作都會有與取消權杖管理和其他典型作業相關的類似需求，所以有一個您可以從中衍生且名為 `BackgroundService` 的便利抽象基底類別 (自 .NET Core 2.1 起提供)。</span><span class="sxs-lookup"><span data-stu-id="79279-148">However, since most background tasks will have similar needs in regard to the cancellation tokens management and other typical operations, there is a convenient abstract base class you can derive from, named `BackgroundService` (available since .NET Core 2.1).</span></span>

<span data-ttu-id="79279-149">該類別提供設定背景工作所需的主要工作。</span><span class="sxs-lookup"><span data-stu-id="79279-149">That class provides the main work needed to set up the background task.</span></span>

<span data-ttu-id="79279-150">下個程式碼是 .NET Core 中所實作的抽象 BackgroundService 基底類別。</span><span class="sxs-lookup"><span data-stu-id="79279-150">The next code is the abstract BackgroundService base class as implemented in .NET Core.</span></span>

```csharp
// Copyright (c) .NET Foundation. Licensed under the Apache License, Version 2.0.
/// <summary>
/// Base class for implementing a long running <see cref="IHostedService"/>.
/// </summary>
public abstract class BackgroundService : IHostedService, IDisposable
{
    private Task _executingTask;
    private readonly CancellationTokenSource _stoppingCts =
                                                   new CancellationTokenSource();

    protected abstract Task ExecuteAsync(CancellationToken stoppingToken);

    public virtual Task StartAsync(CancellationToken cancellationToken)
    {
        // Store the task we're executing
        _executingTask = ExecuteAsync(_stoppingCts.Token);

        // If the task is completed then return it,
        // this will bubble cancellation and failure to the caller
        if (_executingTask.IsCompleted)
        {
            return _executingTask;
        }

        // Otherwise it's running
        return Task.CompletedTask;
    }

    public virtual async Task StopAsync(CancellationToken cancellationToken)
    {
        // Stop called without start
        if (_executingTask == null)
        {
            return;
        }

        try
        {
            // Signal cancellation to the executing method
            _stoppingCts.Cancel();
        }
        finally
        {
            // Wait until the task completes or the stop token triggers
            await Task.WhenAny(_executingTask, Task.Delay(Timeout.Infinite,
                                                          cancellationToken));
        }

    }

    public virtual void Dispose()
    {
        _stoppingCts.Cancel();
    }
}
```

<span data-ttu-id="79279-151">衍生自上一個抽象基底類別時，基於繼承的實作，您只需要在自己的自訂託管服務類別中實作 `ExecuteAsync()` 方法，如 eShopOnContainers 中的下列簡化程式碼所示，而此程式碼會輪詢資料庫並視需要將整合事件發佈至事件匯流排。</span><span class="sxs-lookup"><span data-stu-id="79279-151">When deriving from the previous abstract base class, thanks to that inherited implementation, you just need to implement the `ExecuteAsync()` method in your own custom hosted service class, as in the following simplified code from eShopOnContainers which is polling a database and publishing integration events into the Event Bus when needed.</span></span>

```csharp
public class GracePeriodManagerService : BackgroundService
{
    private readonly ILogger<GracePeriodManagerService> _logger;
    private readonly OrderingBackgroundSettings _settings;

    private readonly IEventBus _eventBus;

    public GracePeriodManagerService(IOptions<OrderingBackgroundSettings> settings,
                                     IEventBus eventBus,
                                     ILogger<GracePeriodManagerService> logger)
    {
        // Constructor's parameters validations...
    }

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        _logger.LogDebug($"GracePeriodManagerService is starting.");

        stoppingToken.Register(() =>
            _logger.LogDebug($" GracePeriod background task is stopping."));

        while (!stoppingToken.IsCancellationRequested)
        {
            _logger.LogDebug($"GracePeriod task doing background work.");

            // This eShopOnContainers method is querying a database table
            // and publishing events into the Event Bus (RabbitMQ / ServiceBus)
            CheckConfirmedGracePeriodOrders();

            await Task.Delay(_settings.CheckUpdateTime, stoppingToken);
        }

        _logger.LogDebug($"GracePeriod background task is stopping.");
    }

    .../...
}
```

<span data-ttu-id="79279-152">在 eShopOnContainers 這個特定案例中，它會執行應用程式方法來查詢資料庫資料表，以尋找具有特定狀態的訂單，以及在套用變更時，透過事件匯流排 (可以使用 RabbitMQ 或 Azure 服務匯流排) 發佈整合事件。</span><span class="sxs-lookup"><span data-stu-id="79279-152">In this specific case for eShopOnContainers, it's executing an application method that's querying a database table looking for orders with a specific state and when applying changes, it is publishing integration events through the event bus (underneath it can be using RabbitMQ or Azure Service Bus).</span></span>

<span data-ttu-id="79279-153">當然，您可以改為執行任何其他商務背景工作。</span><span class="sxs-lookup"><span data-stu-id="79279-153">Of course, you could run any other business background task, instead.</span></span>

<span data-ttu-id="79279-154">根據預設，解除標記會設定為5秒的超時時間，不過您可以在使用的擴充功能建立時變更該值 `WebHost` `UseShutdownTimeout` `IWebHostBuilder` 。</span><span class="sxs-lookup"><span data-stu-id="79279-154">By default, the cancellation token is set with a 5 seconds timeout, although you can change that value when building your `WebHost` using the `UseShutdownTimeout` extension of the `IWebHostBuilder`.</span></span> <span data-ttu-id="79279-155">這表示，我們的服務應該在 5 秒內取消，否則就會更突然地終止。</span><span class="sxs-lookup"><span data-stu-id="79279-155">This means that our service is expected to cancel within 5 seconds otherwise it will be more abruptly killed.</span></span>

<span data-ttu-id="79279-156">下列程式碼會將該時間變更為 10 秒。</span><span class="sxs-lookup"><span data-stu-id="79279-156">The following code would be changing that time to 10 seconds.</span></span>

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a><span data-ttu-id="79279-157">摘要類別圖表</span><span class="sxs-lookup"><span data-stu-id="79279-157">Summary class diagram</span></span>

<span data-ttu-id="79279-158">下圖顯示在執行 IHostedServices 時所牽涉到的類別和介面的視覺化摘要。</span><span class="sxs-lookup"><span data-stu-id="79279-158">The following image shows a visual summary of the classes and interfaces involved when implementing IHostedServices.</span></span>

![此圖顯示 IWebHost 和 IHost 可以裝載許多服務。](./media/background-tasks-with-ihostedservice/class-diagram-custom-ihostedservice.png)

<span data-ttu-id="79279-160">**圖 6-27**。</span><span class="sxs-lookup"><span data-stu-id="79279-160">**Figure 6-27**.</span></span> <span data-ttu-id="79279-161">類別圖表，顯示多個與 IHostedService 相關的類別和介面</span><span class="sxs-lookup"><span data-stu-id="79279-161">Class diagram showing the multiple classes and interfaces related to IHostedService</span></span>

<span data-ttu-id="79279-162">類別圖表：IWebHost 和 IHost 可以裝載許多服務，它們繼承自 BackgroundService，而 BackgroundService 實作 IHostedService。</span><span class="sxs-lookup"><span data-stu-id="79279-162">Class diagram: IWebHost and IHost can host many services, which inherit from BackgroundService, which implements IHostedService.</span></span>

### <a name="deployment-considerations-and-takeaways"></a><span data-ttu-id="79279-163">部署考量和心得</span><span class="sxs-lookup"><span data-stu-id="79279-163">Deployment considerations and takeaways</span></span>

<span data-ttu-id="79279-164">請務必注意 ASP.NET Core `WebHost` 或 .NET Core `Host` 的部署方式可能會影響最後的解決方案。</span><span class="sxs-lookup"><span data-stu-id="79279-164">It is important to note that the way you deploy your ASP.NET Core `WebHost` or .NET Core `Host` might impact the final solution.</span></span> <span data-ttu-id="79279-165">例如，如果您在 IIS 上部署 `WebHost` 或一般 Azure App Service，則可能會因應用程式集區回收而關閉主機。</span><span class="sxs-lookup"><span data-stu-id="79279-165">For instance, if you deploy your `WebHost` on IIS or a regular Azure App Service, your host can be shut down because of app pool recycles.</span></span> <span data-ttu-id="79279-166">但是，如果您將主機作為容器部署到 Kubernetes 之類的協調器，您就可以控制主機的即時實例數目。</span><span class="sxs-lookup"><span data-stu-id="79279-166">But if you are deploying your host as a container into an orchestrator like Kubernetes, you can control the assured number of live instances of your host.</span></span> <span data-ttu-id="79279-167">此外，您可以考慮在雲端中使用其他方法，特別是針對這些案例 (例如 Azure Functions)。</span><span class="sxs-lookup"><span data-stu-id="79279-167">In addition, you could consider other approaches in the cloud especially made for these scenarios, like Azure Functions.</span></span> <span data-ttu-id="79279-168">最後，如果您需要服務持續持行，並準備部署到 Windows Server 上，您可以使用 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="79279-168">Finally, if you need the service to be running all the time and are deploying on a Windows Server you could use a Windows Service.</span></span>

<span data-ttu-id="79279-169">但即使是 `WebHost` 部署到應用程式集區的，還是會有一些案例，例如重新填入或清除應用程式的記憶體內部快取，但仍適用。</span><span class="sxs-lookup"><span data-stu-id="79279-169">But even for a `WebHost` deployed into an app pool, there are scenarios like repopulating or flushing application's in-memory cache that would be still applicable.</span></span>

<span data-ttu-id="79279-170">`IHostedService`介面提供一種便利的方式，可讓您在 .Net core 2.0 和更新) 版本中 (的 ASP.NET Core web 應用程式中啟動背景工作，或在任何程式/主機 (以) 啟動 .Net core 2.1 `IHost` 。</span><span class="sxs-lookup"><span data-stu-id="79279-170">The `IHostedService` interface provides a convenient way to start background tasks in an ASP.NET Core web application (in .NET Core 2.0 and later versions) or in any process/host (starting in .NET Core 2.1 with `IHost`).</span></span> <span data-ttu-id="79279-171">它的主要優點是您可以在主機本身關閉時，透過正常取消來清除背景工作程式碼的機會。</span><span class="sxs-lookup"><span data-stu-id="79279-171">Its main benefit is the opportunity you get with the graceful cancellation to clean-up the code of your background tasks when the host itself is shutting down.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="79279-172">其他資源</span><span class="sxs-lookup"><span data-stu-id="79279-172">Additional resources</span></span>

- <span data-ttu-id="79279-173">**在 ASP.NET Core/標準2.0 中建立排程工作** </span><span class="sxs-lookup"><span data-stu-id="79279-173">**Building a scheduled task in ASP.NET Core/Standard 2.0** </span></span>\
  <https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html>

- <span data-ttu-id="79279-174">**在 ASP.NET Core 2.0 中執行 IHostedService** </span><span class="sxs-lookup"><span data-stu-id="79279-174">**Implementing IHostedService in ASP.NET Core 2.0** </span></span>\
  <https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice>

- <span data-ttu-id="79279-175">**使用 ASP.NET Core 2.1 的 GenericHost 範例** </span><span class="sxs-lookup"><span data-stu-id="79279-175">**GenericHost Sample using ASP.NET Core 2.1** </span></span>\
  <https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample>

> [!div class="step-by-step"]
> <span data-ttu-id="79279-176">[上一個](test-aspnet-core-services-web-apps.md) 
> [下一步](implement-api-gateways-with-ocelot.md)</span><span class="sxs-lookup"><span data-stu-id="79279-176">[Previous](test-aspnet-core-services-web-apps.md)
[Next](implement-api-gateways-with-ocelot.md)</span></span>
