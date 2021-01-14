---
title: 在微服務中使用 IHostedService 和 BackgroundService 類別實作背景工作
description: .NET 微服務：容器化 .NET 應用程式的架構 | 了解在微服務 .NET Core 使用 IHostedService 和 BackgroundService 實作背景工作的新選項。
ms.date: 01/13/2021
ms.openlocfilehash: 26bc06c4a63cddcd32bf7da705f6258fab8eaafa
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188799"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a>在微服務中使用 IHostedService 和 BackgroundService 類別實作背景工作

背景工作和排程工作是您可能需要在任何應用程式中使用的內容，不論它是否遵循微服務架構模式。 使用微服務架構的差異在於，您可以在個別的進程/容器中執行背景工作來進行裝載，讓您可以根據您的需求相應減少/相應減少。

從一般觀點來看，在 .NET 中，我們呼叫了這類的工作 *託管服務*，因為它們是您在主機/應用程式/微服務內裝載的服務/邏輯。 請注意，在此情況下，託管服務就只是具有背景工作邏輯的類別。

自 .NET Core 2.0 開始，此架構提供名為 <xref:Microsoft.Extensions.Hosting.IHostedService> 的新介面，協助您輕鬆地實作託管服務。 基本概念是，您可以將多個背景工作註冊 (裝載的服務) 在您的 web 主機或主機正在執行時于背景中執行，如映射6-26 所示。

![比較 ASP.NET Core IWebHost 和 .NET Core IHost 的圖表。](./media/background-tasks-with-ihostedservice/ihosted-service-webhost-vs-host.png)

**圖 6-26**。 在 WebHost 與主機中使用 IHostedService

ASP.NET Core 1.x 和2.x 支援 `IWebHost` web 應用程式中的背景進程。 .NET Core 2.1 和更新版本支援 `IHost` 具有一般主控台應用程式的背景處理常式。 請注意 `WebHost` 與 `Host` 之間的差異。

在 `WebHost` `IWebHost` ASP.NET Core 2.0 中執行) 的 (基類是您用來提供 HTTP 伺服器功能給程式的基礎結構成品，例如當您在執行 MVC web 應用程式或 web API 服務時。 它提供 ASP.NET Core 中的所有新基礎結構，讓您可以使用相依性插入、在要求管線中插入中介軟體，以及類似的。 對於背景工作而言，會 `WebHost` 使用這些非常相同的 `IHostedServices` 。

.NET Core 2.1 中引進了 `Host` (實作 `IHost` 的基底類別)。 基本上，`Host` 可讓您擁有與 `WebHost` 類似的基礎結構 (相依性插入、託管服務等等)，但在此情況下，您只想要有主機的簡單且輕量程序，而不想要有與 MVC、Web API 或 HTTP 伺服器功能有關的程序。

因此，您可以選擇建立特製化的主機程式，並使用 `IHost` 來處理裝載的服務，而不需要任何其他專案（例如微服務）， `IHostedServices` 或者您也可以擴充現有的 ASP.NET Core `WebHost` ，例如現有的 ASP.NET Core WEB API 或 MVC 應用程式。

根據您的商務和延展性需求，每種方法都有其優缺點。 重點是，如果您的背景工作與 HTTP (無關， `IWebHost` 您應該使用的) `IHost` 。

## <a name="registering-hosted-services-in-your-webhost-or-host"></a>在 WebHost 或主機中註冊託管服務

讓我們進一步向下切入 `IHostedService` 介面，因為在或中，其使用方式相當類似 `WebHost` `Host` 。

SignalR 是使用託管服務之成品的一個範例，但您也可以將它用於下列更簡單的事項：

- 輪詢資料庫以找出變更的背景工作。
- 定期更新某個快取的已排定工作。
- 允許在背景執行緒上執行工作的 QueueBackgroundWorkItem 實作。
- 在共用 `ILogger` 這類通用服務時，於 Web 應用程式背景處理來自佇列的訊息。
- 使用 `Task.Run()` 啟動的背景工作。

基本上，您可以將任何這些動作卸載至執行的背景工作 `IHostedService` 。

您將一或多個加入 `IHostedServices` 至或中的方法 `WebHost` `Host` 是透過 <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A> ASP.NET Core (中的擴充方法，或在 `WebHost` `Host` .net Core 2.1 和更新版本) 中的擴充方法來註冊它們。 基本上，您必須在 `Startup` 類別的熟悉 `ConfigureServices()` 方法內註冊託管服務，如典型 ASP.NET WebHost 中的下列程式碼所示。

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

在該程式碼中，`GracePeriodManagerService` 託管服務是 eShopOnContainers 中來自 Ordering 商務微服務的真正程式碼，另兩個就只是兩個其他範例。

`IHostedService` 背景工作執行會與應用程式 (就此而言，是主機或微服務) 存留期一致。 您在應用程式啟動時註冊工作，並且在關閉應用程式時，有機會依正常程序進行某個動作或清除。

不使用 `IHostedService`，您還是一律可以啟動背景執行緒來執行任何工作。 當應用程式關閉時，該執行緒只會在沒有機會執行正常清除動作的情況下結束時，就會有很大的差異。

## <a name="the-ihostedservice-interface"></a>IHostedService 介面

當您註冊時 `IHostedService` ，.net 會 `StartAsync()` `StopAsync()` `IHostedService` 在應用程式啟動和停止的情況下，分別呼叫您的類型和方法。 如需詳細資訊，請參閱 [IHostedService 介面](/aspnet/core/fundamentals/host/hosted-services?tabs=visual-studio&view=aspnetcore-3.1#ihostedservice-interface)

假設您可以建立多個 IHostedService 實作，並在 `ConfigureService()` 方法中將它們註冊至 DI 容器，如前所示。 將會啟動與停止所有這些託管服務以及應用程式/微服務。

身為開發人員，您負責在主機觸發 `StopAsync()` 方法時處理停止動作或服務。

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a>使用衍生自 BackgroundService 基底類別的自訂託管服務類別來實作 IHostedService

您可以繼續並從頭開始建立自訂託管服務類別，並執行 `IHostedService` ，就像使用 .Net Core 2.0 和更新版本時所需的做法一樣。

不過，因為大部分背景工作都會有與取消權杖管理和其他典型作業相關的類似需求，所以有一個您可以從中衍生且名為 `BackgroundService` 的便利抽象基底類別 (自 .NET Core 2.1 起提供)。

該類別提供設定背景工作所需的主要工作。

下一個程式碼是在 .NET 中執行的抽象 BackgroundService 基類。

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

衍生自上一個抽象基底類別時，基於繼承的實作，您只需要在自己的自訂託管服務類別中實作 `ExecuteAsync()` 方法，如 eShopOnContainers 中的下列簡化程式碼所示，而此程式碼會輪詢資料庫並視需要將整合事件發佈至事件匯流排。

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

在 eShopOnContainers 這個特定案例中，它會執行應用程式方法來查詢資料庫資料表，以尋找具有特定狀態的訂單，以及在套用變更時，透過事件匯流排 (可以使用 RabbitMQ 或 Azure 服務匯流排) 發佈整合事件。

當然，您可以改為執行任何其他商務背景工作。

根據預設，解除標記會設定為5秒的超時時間，不過您可以在使用的擴充功能建立時變更該值 `WebHost` `UseShutdownTimeout` `IWebHostBuilder` 。 這表示，我們的服務應該在 5 秒內取消，否則就會更突然地終止。

下列程式碼會將該時間變更為 10 秒。

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a>摘要類別圖表

下圖顯示在執行 IHostedServices 時所牽涉到的類別和介面的視覺化摘要。

![此圖顯示 IWebHost 和 IHost 可以裝載許多服務。](./media/background-tasks-with-ihostedservice/class-diagram-custom-ihostedservice.png)

**圖 6-27**。 類別圖表，顯示多個與 IHostedService 相關的類別和介面

類別圖表：IWebHost 和 IHost 可以裝載許多服務，它們繼承自 BackgroundService，而 BackgroundService 實作 IHostedService。

### <a name="deployment-considerations-and-takeaways"></a>部署考量和心得

請務必注意，您部署 ASP.NET Core `WebHost` 或 .net 的方式 `Host` 可能會影響最終的解決方案。 例如，如果您在 IIS 上部署 `WebHost` 或一般 Azure App Service，則可能會因應用程式集區回收而關閉主機。 但是，如果您將主機作為容器部署到 Kubernetes 之類的協調器，您就可以控制主機的即時實例數目。 此外，您可以考慮在雲端中使用其他方法，特別是針對這些案例 (例如 Azure Functions)。 最後，如果您需要服務持續持行，並準備部署到 Windows Server 上，您可以使用 Windows 服務。

但即使是 `WebHost` 部署到應用程式集區的，還是會有一些案例，例如重新填入或清除應用程式的記憶體內部快取，但仍適用。

`IHostedService`介面提供一種便利的方式，可讓您在 .Net core 2.0 和更新) 版本中 (的 ASP.NET Core web 應用程式中啟動背景工作，或在任何程式/主機 (以) 啟動 .Net core 2.1 `IHost` 。 它的主要優點是您可以在主機本身關閉時，透過正常取消來清除背景工作程式碼的機會。

## <a name="additional-resources"></a>其他資源

- **在 ASP.NET Core/標準2.0 中建立排程工作** \
  <https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html>

- **在 ASP.NET Core 2.0 中執行 IHostedService** \
  <https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice>

- **使用 ASP.NET Core 2.1 的 GenericHost 範例** \
  <https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample>

> [!div class="step-by-step"]
> [上一個](test-aspnet-core-services-web-apps.md) 
> [下一步](implement-api-gateways-with-ocelot.md)
