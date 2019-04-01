---
title: 在微服務中使用 IHostedService 和 BackgroundService 類別實作背景工作
description: .NET 微服務：容器化 .NET 應用程式的架構 | 了解在微服務 .NET Core 使用 IHostedService 和 BackgroundService 實作背景工作的新選項。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: 7af65077eccfaddeaf25b5f403f1b9824ed4ea17
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2019
ms.locfileid: "58465174"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a>在微服務中使用 IHostedService 和 BackgroundService 類別實作背景工作

在微服務應用程式或任何類型的應用程式中，背景工作和已排定工作最後是您可能需要實作的工作。 使用微服務架構的差異在於您可以實作單一微服務程序/容器來裝載這些背景工作，讓您可以視需要進行相應減少/相應增加，或者甚至可以確定它執行該微服務程序/容器的單一執行個體。

從一般觀點而言，在 .NET Core 中，我們將這些類型的工作稱為「託管服務」，因為它們是您在主機/應用程式/微服務內裝載的服務/邏輯。 請注意，在此情況下，託管服務就只是具有背景工作邏輯的類別。

自 .NET Core 2.0 開始，此架構提供名為 <xref:Microsoft.Extensions.Hosting.IHostedService> 的新介面，協助您輕鬆地實作託管服務。 基本概念是您可以註冊多個背景工作 (託管服務)，以在 WebHost 或主機執行時於背景中執行，如圖 6-26 所示。

![ASP.NET Core 1.x 和 2.x 針對 Web 應用程式中的背景處理序支援 IWebHost，.NET Core 2.1 針對使用一般主控台應用程式的背景處理序支援 IHost。](./media/image26.png)

**圖 6-26**。 在 WebHost 與主機中使用 IHostedService

請注意 `WebHost` 與 `Host` 之間的差異。 

ASP.NET Core 2.0 中的 `WebHost` (實作 `IWebHost` 的基底類別) 是用來將 HTTP 伺服器功能提供給程序的基礎結構成品，就像您是實作 MVC Web 應用程式或 Web API 服務一樣。 它會提供 ASP.NET Core 中的所有新基礎結構優點，讓您可以使用相依性插入、在要求管道中插入中介軟體等等，以及精確地針對背景工作使用這些 `IHostedServices`。

.NET Core 2.1 中引進了 `Host` (實作 `IHost` 的基底類別)。 基本上，`Host` 可讓您擁有與 `WebHost` 類似的基礎結構 (相依性插入、託管服務等等)，但在此情況下，您只想要有主機的簡單且輕量程序，而不想要有與 MVC、Web API 或 HTTP 伺服器功能有關的程序。

因此，您可以選擇並使用 IHost 建立特殊化託管程序以處理託管服務，但不處理其他項目 (例如其製作目的只是要裝載 `IHostedServices` 的微服務)，也可以擴充現有 ASP.NET Core `WebHost` (例如現有 ASP.NET Core Web API 或 MVC 應用程式)。 

根據您的商務和延展性需求，每種方法都有其優缺點。 底線基本上是，如果您的背景工作與 HTTP (IWebHost) 無關，則您應該使用 IHost。

## <a name="registering-hosted-services-in-your-webhost-or-host"></a>在 WebHost 或主機中註冊託管服務

讓我們更深入了解 `IHostedService` 介面，因為它在 `WebHost` 或 `Host` 中的使用相當類似。 

SignalR 是使用託管服務之成品的一個範例，但您也可以將它用於下列更簡單的事項：

-   輪詢資料庫以找出變更的背景工作。
-   定期更新某個快取的已排定工作。
-   允許在背景執行緒上執行工作的 QueueBackgroundWorkItem 實作。
-   在共用 `ILogger` 這類通用服務時，於 Web 應用程式背景處理來自佇列的訊息。
-   使用 `Task.Run()` 啟動的背景工作。

您基本上可以根據 IHostedService，將其中任何動作卸載至背景工作。

將一或多個 `IHostedServices` 新增至 `WebHost` 或 `Host` 的方法是透過 ASP.NET Core `WebHost` (或 .NET Core 2.1 和更高版本中的 `Host`) 中的標準 DI (相依性插入) 註冊它們。 基本上，您必須在 `Startup` 類別的熟悉 `ConfigureServices()` 方法內註冊託管服務，如典型 ASP.NET WebHost 中的下列程式碼所示。 

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{            
    //Other DI registrations;

    // Register Hosted Services
    services.AddSingleton<IHostedService, GracePeriodManagerService>();
    services.AddSingleton<IHostedService, MyHostedServiceB>();
    services.AddSingleton<IHostedService, MyHostedServiceC>();
    //...
}
```

在該程式碼中，`GracePeriodManagerService` 託管服務是 eShopOnContainers 中來自 Ordering 商務微服務的真正程式碼，另兩個就只是兩個其他範例。

`IHostedService` 背景工作執行會與應用程式 (就此而言，是主機或微服務) 存留期一致。 您在應用程式啟動時註冊工作，並且在關閉應用程式時，有機會依正常程序進行某個動作或清除。

不使用 `IHostedService`，您還是一律可以啟動背景執行緒來執行任何工作。 差異就在於只終止該執行緒而沒有機會依正常程序執行清除動作時的應用程式關閉時間。

## <a name="the-ihostedservice-interface"></a>IHostedService 介面

註冊 `IHostedService` 時，.NET Core 將會在應用程式啟動和停止期間分別呼叫 `IHostedService` 型別的 `StartAsync()` 和 `StopAsync()` 方法。 具體而言，在啟動伺服器之後會呼叫啟動，並觸發 `IApplicationLifetime.ApplicationStarted`。

.NET Core 中所定義的 `IHostedService` 如下。

```csharp
namespace Microsoft.Extensions.Hosting
{
    //
    // Summary:
    //     Defines methods for objects that are managed by the host.
    public interface IHostedService
    {
        //
        // Summary:
        // Triggered when the application host is ready to start the service.
        Task StartAsync(CancellationToken cancellationToken);
        //
        // Summary:
        // Triggered when the application host is performing a graceful shutdown.
        Task StopAsync(CancellationToken cancellationToken);
    }
}
```
假設您可以建立多個 IHostedService 實作，並在 `ConfigureService()` 方法中將它們註冊至 DI 容器，如前所示。 將會啟動與停止所有這些託管服務以及應用程式/微服務。

身為開發人員，您負責在主機觸發 `StopAsync()` 方法時處理停止動作或服務。

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a>使用衍生自 BackgroundService 基底類別的自訂託管服務類別來實作 IHostedService

您可以繼續並從頭開始建立自訂託管服務類別，並實作 `IHostedService`，就像使用 .NET Core 2.0 時所需執行的作業。 

不過，因為大部分背景工作都會有與取消權杖管理和其他典型作業相關的類似需求，所以有一個您可以從中衍生且名為 `BackgroundService` 的便利抽象基底類別 (自 .NET Core 2.1 起提供)。

該類別提供設定背景工作所需的主要工作。

下個程式碼是 .NET Core 中所實作的抽象 BackgroundService 基底類別。

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
        //Constructor’s parameters validations...       
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
            // and publishing events into the Event Bus (RabbitMS / ServiceBus)
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

取消權杖預設會設定 5 秒的逾時，但您可以在使用 `IWebHostBuilder` 的 `UseShutdownTimeout` 延伸模組建置 `WebHost` 時變更該值。 這表示，我們的服務應該在 5 秒內取消，否則就會更突然地終止。

下列程式碼會將該時間變更為 10 秒。

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a>摘要類別圖表

下圖顯示在實作 IHostedServices 時所涉類別和介面的視覺效果摘要。
 
![類別圖表：IWebHost 和 IHost 可以裝載許多服務，它們繼承自 BackgroundService，而 BackgroundService 實作 IHostedService。](./media/image27.png)

**圖 6-27**。 類別圖表，顯示多個與 IHostedService 相關的類別和介面

### <a name="deployment-considerations-and-takeaways"></a>部署考量和心得

請務必注意 ASP.NET Core `WebHost` 或 .NET Core `Host` 的部署方式可能會影響最後的解決方案。 例如，如果您在 IIS 上部署 `WebHost` 或一般 Azure App Service，則可能會因應用程式集區回收而關閉主機。 但是，如果您要將主機當成容器部署至 Kubernetes 或 Service Fabric 這類協調器，則可以控制保證的主機即時執行個體數目。 此外，您可以考慮在雲端中使用其他方法，特別是針對這些案例 (例如 Azure Functions)。 最後，如果您需要服務持續持行，並準備部署到 Windows Server 上，您可以使用 Windows 服務。

但即使針對部署至應用程式集區的 `WebHost`，有些重新擴展或排清應用程式記憶體中快取的情況可能仍然會發生。

`IHostedService` 介面提供一種便利方式可在 ASP.NET Core Web 應用程式 (於 .NET Core 2.0 中) 或任何程序/主機 (使用 `IHost` 在 .NET Core 2.1 中啟動) 中啟動背景工作。 它的主要優點是，在主機本身正在關機時，您可以依正常程序取消清除背景工作的程式碼。

#### <a name="additional-resources"></a>其他資源

-   **在 ASP.NET Core/Standard 2.0 中建置已排定工作** <br/>
    [https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html](https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html)

-   **在 ASP.NET Core 2.0 中實作 IHostedService** <br/>
    [https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice](https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice)

-   **使用 ASP.NET Core 2.1 的 GenericHost 樣本** <br/>
    [https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample](https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample)

>[!div class="step-by-step"]
>[上一頁](test-aspnet-core-services-web-apps.md)
>[下一頁](implement-api-gateways-with-ocelot.md)
