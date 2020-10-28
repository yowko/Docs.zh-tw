---
title: .NET 中的相依性插入
description: 瞭解 .NET 如何實行相依性插入，以及如何使用它。
author: IEvangelist
ms.author: dapine
ms.date: 09/23/2020
ms.topic: overview
ms.openlocfilehash: d2dbe06597c99158eaa39812d4d5a95288450adc
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888562"
---
# <a name="dependency-injection-in-net"></a><span data-ttu-id="8ab38-103">.NET 中的相依性插入</span><span class="sxs-lookup"><span data-stu-id="8ab38-103">Dependency injection in .NET</span></span>

<span data-ttu-id="8ab38-104">.NET 支援 (DI) 軟體設計模式中的相依性插入，這項技術可讓您在類別與其相依性之間進行反向 [控制 (IoC) ](../../architecture/modern-web-apps-azure/architectural-principles.md#dependency-inversion) 。</span><span class="sxs-lookup"><span data-stu-id="8ab38-104">.NET supports the dependency injection (DI) software design pattern, which is a technique for achieving [Inversion of Control (IoC)](../../architecture/modern-web-apps-azure/architectural-principles.md#dependency-inversion) between classes and their dependencies.</span></span> <span data-ttu-id="8ab38-105">.NET 中的相依性插入是一流的 [公民](https://en.wikipedia.org/wiki/First-class_citizen)，以及設定、記錄和選項模式。</span><span class="sxs-lookup"><span data-stu-id="8ab38-105">Dependency injection in .NET is a [first-class citizen](https://en.wikipedia.org/wiki/First-class_citizen), along with configuration, logging, and the options pattern.</span></span>

<span data-ttu-id="8ab38-106">相依 *性是另* 一個物件所依存的物件。</span><span class="sxs-lookup"><span data-stu-id="8ab38-106">A *dependency* is an object that another object depends on.</span></span> <span data-ttu-id="8ab38-107">`MessageWriter`使用其他類別所依存的方法檢查下列類別 `Write` ：</span><span class="sxs-lookup"><span data-stu-id="8ab38-107">Examine the following `MessageWriter` class with a `Write` method that other classes depend on:</span></span>

```csharp
public class MessageWriter
{
    public void Write(string message)
    {
        Console.WriteLine($"MessageWriter.Write(message: \"{message}\")");
    }
}
```

<span data-ttu-id="8ab38-108">類別可以建立類別的實例 `MessageWriter` ，以使用其 `Write` 方法。</span><span class="sxs-lookup"><span data-stu-id="8ab38-108">A class can create an instance of the `MessageWriter` class to make use of its `Write` method.</span></span> <span data-ttu-id="8ab38-109">在下列範例中， `MessageWriter` 類別是類別的相依性 `Worker` ：</span><span class="sxs-lookup"><span data-stu-id="8ab38-109">In the following example, the `MessageWriter` class is a dependency of the `Worker` class:</span></span>

```csharp
public class Worker : BackgroundService
{
    private readonly MessageWriter _messageWriter = new MessageWriter();

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        while (!stoppingToken.IsCancellationRequested)
        {
            _messageWriter.Write($"Worker running at: {DateTimeOffset.Now}");
            await Task.Delay(1000, stoppingToken);
        }
    }
}
```

<span data-ttu-id="8ab38-110">類別會建立和直接相依于 `MessageWriter` 類別。</span><span class="sxs-lookup"><span data-stu-id="8ab38-110">The class creates and directly depends on the `MessageWriter` class.</span></span> <span data-ttu-id="8ab38-111">硬式編碼的相依性（例如在先前的範例中）有問題，因此應該避免因下列原因：</span><span class="sxs-lookup"><span data-stu-id="8ab38-111">Hard-coded dependencies, such as in the previous example, are problematic and should be avoided for the following reasons:</span></span>

- <span data-ttu-id="8ab38-112">若要以 `MessageWriter` 不同的實作為取代， `MessageService` 必須修改該類別。</span><span class="sxs-lookup"><span data-stu-id="8ab38-112">To replace `MessageWriter` with a different implementation, the `MessageService` class must be modified.</span></span>
- <span data-ttu-id="8ab38-113">如果 `MessageWriter` 有相依性，則也必須由類別設定 `MessageService` 。</span><span class="sxs-lookup"><span data-stu-id="8ab38-113">If `MessageWriter` has dependencies, they must also be configured by the `MessageService` class.</span></span> <span data-ttu-id="8ab38-114">在具有多個相依於 `MessageWriter` 之多個類別的大型專案中，設定程式碼在不同的應用程式之間會變得鬆散。</span><span class="sxs-lookup"><span data-stu-id="8ab38-114">In a large project with multiple classes depending on `MessageWriter`, the configuration code becomes scattered across the app.</span></span>
- <span data-ttu-id="8ab38-115">此實作難以進行單元測試。</span><span class="sxs-lookup"><span data-stu-id="8ab38-115">This implementation is difficult to unit test.</span></span> <span data-ttu-id="8ab38-116">應用程式應該使用模擬 (Mock) 或虛設常式 (Stub) `MessageWriter` 類別，這在使用此方法時無法使用。</span><span class="sxs-lookup"><span data-stu-id="8ab38-116">The app should use a mock or stub `MessageWriter` class, which isn't possible with this approach.</span></span>

<span data-ttu-id="8ab38-117">相依性插入可透過下列方式解決這些問題：</span><span class="sxs-lookup"><span data-stu-id="8ab38-117">Dependency injection addresses these problems through:</span></span>

- <span data-ttu-id="8ab38-118">使用介面或基底類別來將相依性資訊抽象化。</span><span class="sxs-lookup"><span data-stu-id="8ab38-118">The use of an interface or base class to abstract the dependency implementation.</span></span>
- <span data-ttu-id="8ab38-119">在服務容器中註冊相依性。</span><span class="sxs-lookup"><span data-stu-id="8ab38-119">Registration of the dependency in a service container.</span></span> <span data-ttu-id="8ab38-120">.NET 提供內建的服務容器 <xref:System.IServiceProvider> 。</span><span class="sxs-lookup"><span data-stu-id="8ab38-120">.NET provides a built-in service container, <xref:System.IServiceProvider>.</span></span> <span data-ttu-id="8ab38-121">服務通常會在應用程式啟動時註冊，並附加至 <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> 。</span><span class="sxs-lookup"><span data-stu-id="8ab38-121">Services are typically registered at the app's start-up, and appended to an <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span></span> <span data-ttu-id="8ab38-122">新增所有服務之後，您就可以使用 <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> 來建立服務容器。</span><span class="sxs-lookup"><span data-stu-id="8ab38-122">Once all services are added, you use <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> to create the service container.</span></span>
- <span data-ttu-id="8ab38-123">將服務「插入」  到服務使用位置之類別的建構函式。</span><span class="sxs-lookup"><span data-stu-id="8ab38-123">*Injection* of the service into the constructor of the class where it's used.</span></span> <span data-ttu-id="8ab38-124">架構會負責建立相依性的執行個體，並在不再需要時將它捨棄。</span><span class="sxs-lookup"><span data-stu-id="8ab38-124">The framework takes on the responsibility of creating an instance of the dependency and disposing of it when it's no longer needed.</span></span>

<span data-ttu-id="8ab38-125">例如， `IMessageWriter` 介面會定義 `Write` 方法：</span><span class="sxs-lookup"><span data-stu-id="8ab38-125">As an example, the `IMessageWriter` interface defines the `Write` method:</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/IMessageWriter.cs":::

<span data-ttu-id="8ab38-126">這個介面是由具象型別 `MessageWriter` 所實作：</span><span class="sxs-lookup"><span data-stu-id="8ab38-126">This interface is implemented by a concrete type, `MessageWriter`:</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/MessageWriter.cs":::

<span data-ttu-id="8ab38-127">範例程式碼會 `IMessageWriter` 使用具象類型來註冊服務 `MessageWriter` 。</span><span class="sxs-lookup"><span data-stu-id="8ab38-127">The sample code registers the `IMessageWriter` service with the concrete type `MessageWriter`.</span></span> <span data-ttu-id="8ab38-128"><xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A>方法會使用範圍存留期（單一要求的存留期）來註冊服務。</span><span class="sxs-lookup"><span data-stu-id="8ab38-128">The <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A> method registers the service with a scoped lifetime, the lifetime of a single request.</span></span> <span data-ttu-id="8ab38-129">將在此主題稍後將說明[服務存留期](#service-lifetimes)。</span><span class="sxs-lookup"><span data-stu-id="8ab38-129">[Service lifetimes](#service-lifetimes) are described later in this topic.</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/Program.cs" highlight="16":::

<span data-ttu-id="8ab38-130">在範例應用程式中， `IMessageWriter` 會要求服務並用來呼叫 `Write` 方法：</span><span class="sxs-lookup"><span data-stu-id="8ab38-130">In the sample app, the `IMessageWriter` service is requested and used to call the `Write` method:</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/Worker.cs":::

<span data-ttu-id="8ab38-131">使用 DI 模式時，背景工作角色服務：</span><span class="sxs-lookup"><span data-stu-id="8ab38-131">By using the DI pattern, the worker service:</span></span>

- <span data-ttu-id="8ab38-132">不會使用具象型別 `MessageWriter` ，而只會使用實作為的 `IMessageWriter` 介面。</span><span class="sxs-lookup"><span data-stu-id="8ab38-132">Doesn't use the concrete type `MessageWriter`, only the `IMessageWriter` interface that implements it.</span></span> <span data-ttu-id="8ab38-133">這可讓您輕鬆地變更控制器所使用的執行，而不需要修改控制器。</span><span class="sxs-lookup"><span data-stu-id="8ab38-133">That makes it easy to change the implementation that the controller uses without modifying the controller.</span></span>
- <span data-ttu-id="8ab38-134">不會建立的實例 `MessageWriter` ，而是由 DI 容器所建立。</span><span class="sxs-lookup"><span data-stu-id="8ab38-134">Doesn't create an instance of `MessageWriter`, it's created by the DI container.</span></span>

<span data-ttu-id="8ab38-135">您 `IMessageWriter` 可以使用內建的記錄 API 來改善介面的實作為：</span><span class="sxs-lookup"><span data-stu-id="8ab38-135">The implementation of the `IMessageWriter` interface can be improved by using the built-in logging API:</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/LoggingMessageWriter.cs":::

<span data-ttu-id="8ab38-136">更新的 `ConfigureServices` 方法會註冊新的 `IMessageWriter` 實作為：</span><span class="sxs-lookup"><span data-stu-id="8ab38-136">The updated `ConfigureServices` method registers the new `IMessageWriter` implementation:</span></span>

```csharp
static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureServices((_, services) =>
            services.AddHostedService<Worker>()
                    .AddScoped<IMessageWriter, LoggingMessageWriter>());
```

<span data-ttu-id="8ab38-137">`LoggingMessageWriter` 相依于 <xref:Microsoft.Extensions.Logging.ILogger%601> 它在函式中要求的。</span><span class="sxs-lookup"><span data-stu-id="8ab38-137">`LoggingMessageWriter` depends on <xref:Microsoft.Extensions.Logging.ILogger%601>, which it requests in the constructor.</span></span> <span data-ttu-id="8ab38-138">`ILogger<TCategoryName>` 是 [架構提供的服務](#framework-provided-services)。</span><span class="sxs-lookup"><span data-stu-id="8ab38-138">`ILogger<TCategoryName>` is a [framework-provided service](#framework-provided-services).</span></span>

<span data-ttu-id="8ab38-139">以鏈結方式使用相依性插入並非不尋常。</span><span class="sxs-lookup"><span data-stu-id="8ab38-139">It's not unusual to use dependency injection in a chained fashion.</span></span> <span data-ttu-id="8ab38-140">每個要求的相依性接著會要求其自己的相依性。</span><span class="sxs-lookup"><span data-stu-id="8ab38-140">Each requested dependency in turn requests its own dependencies.</span></span> <span data-ttu-id="8ab38-141">容器會解決圖形中的相依性，並傳回完全解析的服務。</span><span class="sxs-lookup"><span data-stu-id="8ab38-141">The container resolves the dependencies in the graph and returns the fully resolved service.</span></span> <span data-ttu-id="8ab38-142">必須先解析的相依性集合組通常稱為「相依性樹狀結構」  、「相依性圖形」  或「物件圖形」  。</span><span class="sxs-lookup"><span data-stu-id="8ab38-142">The collective set of dependencies that must be resolved is typically referred to as a *dependency tree* , *dependency graph* , or *object graph* .</span></span>

<span data-ttu-id="8ab38-143">容器會 `ILogger<TCategoryName>` 利用 [ (泛型) 開放式](/dotnet/csharp/language-reference/language-specification/types#open-and-closed-types)型別來解析，因此不需要註冊每個 [ (泛型) 結構類型](/dotnet/csharp/language-reference/language-specification/types#constructed-types)。</span><span class="sxs-lookup"><span data-stu-id="8ab38-143">The container resolves `ILogger<TCategoryName>` by taking advantage of [(generic) open types](/dotnet/csharp/language-reference/language-specification/types#open-and-closed-types), eliminating the need to register every [(generic) constructed type](/dotnet/csharp/language-reference/language-specification/types#constructed-types).</span></span>

<span data-ttu-id="8ab38-144">在相依性插入術語中，服務：</span><span class="sxs-lookup"><span data-stu-id="8ab38-144">In dependency injection terminology, a service:</span></span>

- <span data-ttu-id="8ab38-145">通常是為其他物件（例如服務）提供服務的物件 `IMessageWriter` 。</span><span class="sxs-lookup"><span data-stu-id="8ab38-145">Is typically an object that provides a service to other objects, such as the `IMessageWriter` service.</span></span>
- <span data-ttu-id="8ab38-146">與 web 服務無關，但服務可能會使用 web 服務。</span><span class="sxs-lookup"><span data-stu-id="8ab38-146">Is not related to a web service, although the service may use a web service.</span></span>

<span data-ttu-id="8ab38-147">架構會提供健全的記錄系統。</span><span class="sxs-lookup"><span data-stu-id="8ab38-147">The framework provides a robust logging system.</span></span> <span data-ttu-id="8ab38-148">`IMessageWriter`上述範例中所示的執行是為了示範基本 DI 而撰寫的，而不是用來執行記錄。</span><span class="sxs-lookup"><span data-stu-id="8ab38-148">The `IMessageWriter` implementations shown in the preceding examples were written to demonstrate basic DI, not to implement logging.</span></span> <span data-ttu-id="8ab38-149">大部分的應用程式都不需要撰寫記錄器。</span><span class="sxs-lookup"><span data-stu-id="8ab38-149">Most apps shouldn't need to write loggers.</span></span> <span data-ttu-id="8ab38-150">下列程式碼示範如何使用預設記錄，這只需要在 `Worker` 中註冊 `ConfigureServices` 為託管服務 <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A> ：</span><span class="sxs-lookup"><span data-stu-id="8ab38-150">The following code demonstrates using the default logging, which only requires the `Worker` to be registered in `ConfigureServices` as a hosted service <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A>:</span></span>

```csharp
public class Worker : BackgroundService
{
    private readonly ILogger<Worker> _logger;

    public Worker(ILogger<Worker> logger) =>
        _logger = logger;

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        while (!stoppingToken.IsCancellationRequested)
        {
            _logger.LogInformation("Worker running at: {time}", DateTimeOffset.Now);
            await Task.Delay(1000, stoppingToken);
        }
    }
}
```

<span data-ttu-id="8ab38-151">使用上述程式碼不需要更新 `ConfigureServices` ，因為記錄是由架構提供。</span><span class="sxs-lookup"><span data-stu-id="8ab38-151">Using the preceding code, there is no need to update `ConfigureServices`, because logging is provided by the framework.</span></span>

## <a name="register-groups-of-services-with-extension-methods"></a><span data-ttu-id="8ab38-152">使用擴充方法來註冊服務群組</span><span class="sxs-lookup"><span data-stu-id="8ab38-152">Register groups of services with extension methods</span></span>

<span data-ttu-id="8ab38-153">Microsoft 延伸模組使用註冊一組相關服務的慣例。</span><span class="sxs-lookup"><span data-stu-id="8ab38-153">Microsoft Extensions uses a convention for registering a group of related services.</span></span> <span data-ttu-id="8ab38-154">慣例是使用單一 `Add{GROUP_NAME}` 擴充方法來註冊架構功能所需的所有服務。</span><span class="sxs-lookup"><span data-stu-id="8ab38-154">The convention is to use a single `Add{GROUP_NAME}` extension method to register all of the services required by a framework feature.</span></span> <span data-ttu-id="8ab38-155">例如， <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A> 擴充方法會註冊使用選項所需的所有服務。</span><span class="sxs-lookup"><span data-stu-id="8ab38-155">For example, the <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A> extension method registers all of the services required for using options.</span></span>

## <a name="framework-provided-services"></a><span data-ttu-id="8ab38-156">架構提供的服務</span><span class="sxs-lookup"><span data-stu-id="8ab38-156">Framework-provided services</span></span>

<span data-ttu-id="8ab38-157">`ConfigureServices`方法會註冊應用程式所使用的服務，包括平臺功能。</span><span class="sxs-lookup"><span data-stu-id="8ab38-157">The `ConfigureServices` method registers services that the app uses, including platform features.</span></span> <span data-ttu-id="8ab38-158">一開始， `IServiceCollection` 提供給的是 `ConfigureServices` 由架構定義的服務，視 [主機的設定方式](generic-host.md#host-configuration)而定。</span><span class="sxs-lookup"><span data-stu-id="8ab38-158">Initially, the `IServiceCollection` provided to `ConfigureServices` has services defined by the framework depending on [how the host was configured](generic-host.md#host-configuration).</span></span> <span data-ttu-id="8ab38-159">針對以 .NET 範本為基礎的應用程式，架構會註冊數百項服務。</span><span class="sxs-lookup"><span data-stu-id="8ab38-159">For apps based on the .NET templates, the framework registers hundreds of services.</span></span>

<span data-ttu-id="8ab38-160">下表列出這些架構註冊服務的小型範例：</span><span class="sxs-lookup"><span data-stu-id="8ab38-160">The following table lists a small sample of these framework-registered services:</span></span>

| <span data-ttu-id="8ab38-161">服務類型</span><span class="sxs-lookup"><span data-stu-id="8ab38-161">Service Type</span></span>                                                                       | <span data-ttu-id="8ab38-162">存留期</span><span class="sxs-lookup"><span data-stu-id="8ab38-162">Lifetime</span></span>  |
|------------------------------------------------------------------------------------|-----------|
| <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime>                       | <span data-ttu-id="8ab38-163">單一</span><span class="sxs-lookup"><span data-stu-id="8ab38-163">Singleton</span></span> |
| <xref:Microsoft.Extensions.Logging.ILogger%601?displayProperty=fullName>           | <span data-ttu-id="8ab38-164">單一</span><span class="sxs-lookup"><span data-stu-id="8ab38-164">Singleton</span></span> |
| <xref:Microsoft.Extensions.Logging.ILoggerFactory?displayProperty=fullName>        | <span data-ttu-id="8ab38-165">單一</span><span class="sxs-lookup"><span data-stu-id="8ab38-165">Singleton</span></span> |
| <xref:Microsoft.Extensions.ObjectPool.ObjectPoolProvider?displayProperty=fullName> | <span data-ttu-id="8ab38-166">單一</span><span class="sxs-lookup"><span data-stu-id="8ab38-166">Singleton</span></span> |
| <xref:Microsoft.Extensions.Options.IConfigureOptions%601?displayProperty=fullName> | <span data-ttu-id="8ab38-167">暫時性</span><span class="sxs-lookup"><span data-stu-id="8ab38-167">Transient</span></span> |
| <xref:Microsoft.Extensions.Options.IOptions%601?displayProperty=fullName>          | <span data-ttu-id="8ab38-168">單一</span><span class="sxs-lookup"><span data-stu-id="8ab38-168">Singleton</span></span> |
| <xref:System.Diagnostics.DiagnosticListener?displayProperty=fullName>              | <span data-ttu-id="8ab38-169">單一</span><span class="sxs-lookup"><span data-stu-id="8ab38-169">Singleton</span></span> |
| <xref:System.Diagnostics.DiagnosticSource?displayProperty=fullName>                | <span data-ttu-id="8ab38-170">單一</span><span class="sxs-lookup"><span data-stu-id="8ab38-170">Singleton</span></span> |

## <a name="service-lifetimes"></a><span data-ttu-id="8ab38-171">服務存留期</span><span class="sxs-lookup"><span data-stu-id="8ab38-171">Service lifetimes</span></span>

<span data-ttu-id="8ab38-172">您可以使用下列其中一種存留期來註冊服務：</span><span class="sxs-lookup"><span data-stu-id="8ab38-172">Services can be registered with one of the following lifetimes:</span></span>

- <span data-ttu-id="8ab38-173">暫時性</span><span class="sxs-lookup"><span data-stu-id="8ab38-173">Transient</span></span>
- <span data-ttu-id="8ab38-174">具範圍</span><span class="sxs-lookup"><span data-stu-id="8ab38-174">Scoped</span></span>
- <span data-ttu-id="8ab38-175">單一</span><span class="sxs-lookup"><span data-stu-id="8ab38-175">Singleton</span></span>

<span data-ttu-id="8ab38-176">下列各節將說明每個先前的存留期。</span><span class="sxs-lookup"><span data-stu-id="8ab38-176">The following sections describe each of the preceding lifetimes.</span></span> <span data-ttu-id="8ab38-177">為每個已註冊的服務選擇適當的存留期。</span><span class="sxs-lookup"><span data-stu-id="8ab38-177">Choose an appropriate lifetime for each registered service.</span></span>

### <a name="transient"></a><span data-ttu-id="8ab38-178">暫時性</span><span class="sxs-lookup"><span data-stu-id="8ab38-178">Transient</span></span>

<span data-ttu-id="8ab38-179">每次從服務容器要求暫時性存留期服務時都會建立它們。</span><span class="sxs-lookup"><span data-stu-id="8ab38-179">Transient lifetime services are created each time they're requested from the service container.</span></span> <span data-ttu-id="8ab38-180">此存留期最適合用於輕量型的無狀態服務。</span><span class="sxs-lookup"><span data-stu-id="8ab38-180">This lifetime works best for lightweight, stateless services.</span></span> <span data-ttu-id="8ab38-181">使用註冊暫時性服務 <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddTransient%2A> 。</span><span class="sxs-lookup"><span data-stu-id="8ab38-181">Register transient services with <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddTransient%2A>.</span></span>

<span data-ttu-id="8ab38-182">在處理要求的應用程式中，會在要求結束時處置暫時性服務。</span><span class="sxs-lookup"><span data-stu-id="8ab38-182">In apps that process requests, transient services are disposed at the end of the request.</span></span>

### <a name="scoped"></a><span data-ttu-id="8ab38-183">具範圍</span><span class="sxs-lookup"><span data-stu-id="8ab38-183">Scoped</span></span>

<span data-ttu-id="8ab38-184">針對 web 應用程式，限域存留期表示每個用戶端要求都會建立服務一次， (連接) 。</span><span class="sxs-lookup"><span data-stu-id="8ab38-184">For web applications a scoped lifetime indicates that services are created once per client request (connection).</span></span> <span data-ttu-id="8ab38-185">使用註冊已設定範圍的服務 <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A> 。</span><span class="sxs-lookup"><span data-stu-id="8ab38-185">Register scoped services with <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A>.</span></span>

<span data-ttu-id="8ab38-186">在處理要求的應用程式中，會在要求結束時處置範圍服務。</span><span class="sxs-lookup"><span data-stu-id="8ab38-186">In apps that process requests, scoped services are disposed at the end of the request.</span></span>

<span data-ttu-id="8ab38-187">使用 Entity Framework Core 時， <xref:Microsoft.Extensions.DependencyInjection.EntityFrameworkServiceCollectionExtensions.AddDbContext%2A> 擴充方法預設會註冊 `DbContext` 具有範圍存留期的類型。</span><span class="sxs-lookup"><span data-stu-id="8ab38-187">When using Entity Framework Core, the <xref:Microsoft.Extensions.DependencyInjection.EntityFrameworkServiceCollectionExtensions.AddDbContext%2A> extension method registers `DbContext` types with a scoped lifetime by default.</span></span>

> [!NOTE]
> <span data-ttu-id="8ab38-188">請 \* **not** _ 從 singleton 解析已設定範圍的服務，並小心不要間接執行，例如透過暫時性的服務。</span><span class="sxs-lookup"><span data-stu-id="8ab38-188">Do \* **not** _ resolve a scoped service from a singleton and be careful not to do so indirectly, for example, through a transient service.</span></span> <span data-ttu-id="8ab38-189">處理後續要求時，它可能會導致服務有不正確的狀態。</span><span class="sxs-lookup"><span data-stu-id="8ab38-189">It may cause the service to have incorrect state when processing subsequent requests.</span></span> <span data-ttu-id="8ab38-190">您可以：</span><span class="sxs-lookup"><span data-stu-id="8ab38-190">It's fine to:</span></span>
>
> - <span data-ttu-id="8ab38-191">從範圍或暫時性服務解析單一服務。</span><span class="sxs-lookup"><span data-stu-id="8ab38-191">Resolve a singleton service from a scoped or transient service.</span></span>
> - <span data-ttu-id="8ab38-192">從另一個範圍或暫時性服務解析已設定範圍的服務。</span><span class="sxs-lookup"><span data-stu-id="8ab38-192">Resolve a scoped service from another scoped or transient service.</span></span>

<span data-ttu-id="8ab38-193">根據預設，在開發環境中，從較長存留期的另一個服務解析服務，會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8ab38-193">By default, in the development environment, resolving a service from another service with a longer lifetime throws an exception.</span></span> <span data-ttu-id="8ab38-194">如需詳細資訊，請參閱[範圍驗證](#scope-validation)。</span><span class="sxs-lookup"><span data-stu-id="8ab38-194">For more information, see [Scope validation](#scope-validation).</span></span>

### <a name="singleton"></a><span data-ttu-id="8ab38-195">單一</span><span class="sxs-lookup"><span data-stu-id="8ab38-195">Singleton</span></span>

<span data-ttu-id="8ab38-196">系統會建立單一存留期服務：</span><span class="sxs-lookup"><span data-stu-id="8ab38-196">Singleton lifetime services are created either:</span></span>

- <span data-ttu-id="8ab38-197">第一次要求時。</span><span class="sxs-lookup"><span data-stu-id="8ab38-197">The first time they're requested.</span></span>
- <span data-ttu-id="8ab38-198">由開發人員直接將實實例提供給容器。</span><span class="sxs-lookup"><span data-stu-id="8ab38-198">By the developer, when providing an implementation instance directly to the container.</span></span> <span data-ttu-id="8ab38-199">這種方法很少需要。</span><span class="sxs-lookup"><span data-stu-id="8ab38-199">This approach is rarely needed.</span></span>

<span data-ttu-id="8ab38-200">從相依性插入容器每個後續的服務執行要求都會使用相同的實例。</span><span class="sxs-lookup"><span data-stu-id="8ab38-200">Every subsequent request of the service implementation from the dependency injection container uses the same instance.</span></span> <span data-ttu-id="8ab38-201">如果應用程式需要單一行為，請允許服務容器管理服務的存留期。</span><span class="sxs-lookup"><span data-stu-id="8ab38-201">If the app requires singleton behavior, allow the service container to manage the service's lifetime.</span></span> <span data-ttu-id="8ab38-202">請勿實行 singleton 設計模式，並提供程式碼來處置 singleton。</span><span class="sxs-lookup"><span data-stu-id="8ab38-202">Don't implement the singleton design pattern and provide code to dispose of the singleton.</span></span> <span data-ttu-id="8ab38-203">服務絕對不能由從容器解析服務的程式碼處置。</span><span class="sxs-lookup"><span data-stu-id="8ab38-203">Services should never be disposed by code that resolved the service from the container.</span></span> <span data-ttu-id="8ab38-204">如果類型或 factory 註冊為 singleton，則容器會自動處置 singleton。</span><span class="sxs-lookup"><span data-stu-id="8ab38-204">If a type or factory is registered as a singleton, the container disposes the singleton automatically.</span></span>

<span data-ttu-id="8ab38-205">使用註冊單一服務 <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A> 。</span><span class="sxs-lookup"><span data-stu-id="8ab38-205">Register singleton services with <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A>.</span></span> <span data-ttu-id="8ab38-206">單一服務必須是安全線程，而且通常用於無狀態服務。</span><span class="sxs-lookup"><span data-stu-id="8ab38-206">Singleton services must be thread safe and are often used in stateless services.</span></span>

<span data-ttu-id="8ab38-207">在處理要求的應用程式中，會在應用程式關閉時處置單一服務 <xref:Microsoft.Extensions.DependencyInjection.ServiceProvider> 。</span><span class="sxs-lookup"><span data-stu-id="8ab38-207">In apps that process requests, singleton services are disposed when the <xref:Microsoft.Extensions.DependencyInjection.ServiceProvider> is disposed on application shutdown.</span></span> <span data-ttu-id="8ab38-208">因為在關閉應用程式之前不會釋出記憶體，請考慮使用單一服務的記憶體。</span><span class="sxs-lookup"><span data-stu-id="8ab38-208">Because memory is not released until the app is shut down, consider memory use with a singleton service.</span></span>

> [!WARNING]
> <span data-ttu-id="8ab38-209">請勿 _\*_從 singleton 解析已_\*_ 設定範圍的服務。</span><span class="sxs-lookup"><span data-stu-id="8ab38-209">Do _*_not_*_ resolve a scoped service from a singleton.</span></span> <span data-ttu-id="8ab38-210">處理後續要求時，它可能會導致服務有不正確的狀態。</span><span class="sxs-lookup"><span data-stu-id="8ab38-210">It may cause the service to have incorrect state when processing subsequent requests.</span></span> <span data-ttu-id="8ab38-211">從範圍或暫時性服務解析單一服務是很好的。</span><span class="sxs-lookup"><span data-stu-id="8ab38-211">It's fine to resolve a singleton service from a scoped or transient service.</span></span>

## <a name="service-registration-methods"></a><span data-ttu-id="8ab38-212">服務註冊方法</span><span class="sxs-lookup"><span data-stu-id="8ab38-212">Service registration methods</span></span>

<span data-ttu-id="8ab38-213">此架構提供適用于特定案例的服務註冊延伸方法：</span><span class="sxs-lookup"><span data-stu-id="8ab38-213">The framework provides service registration extension methods that are useful in specific scenarios:</span></span>

| <span data-ttu-id="8ab38-214">方法</span><span class="sxs-lookup"><span data-stu-id="8ab38-214">Method</span></span> | <span data-ttu-id="8ab38-215">自動</span><span class="sxs-lookup"><span data-stu-id="8ab38-215">Automatic</span></span><br><span data-ttu-id="8ab38-216">物件 (object)</span><span class="sxs-lookup"><span data-stu-id="8ab38-216">object</span></span><br><span data-ttu-id="8ab38-217">處置</span><span class="sxs-lookup"><span data-stu-id="8ab38-217">disposal</span></span> | <span data-ttu-id="8ab38-218">多個</span><span class="sxs-lookup"><span data-stu-id="8ab38-218">Multiple</span></span><br><span data-ttu-id="8ab38-219">實作</span><span class="sxs-lookup"><span data-stu-id="8ab38-219">implementations</span></span> | <span data-ttu-id="8ab38-220">傳遞引數</span><span class="sxs-lookup"><span data-stu-id="8ab38-220">Pass args</span></span> |
|--|:-:|:-:|:-:|
| `Add{LIFETIME}<{SERVICE}, {IMPLEMENTATION}>()`<br><br><span data-ttu-id="8ab38-221">範例：</span><span class="sxs-lookup"><span data-stu-id="8ab38-221">Example:</span></span><br><br>`services.AddSingleton<IMyDep, MyDep>();` | <span data-ttu-id="8ab38-222">是</span><span class="sxs-lookup"><span data-stu-id="8ab38-222">Yes</span></span> | <span data-ttu-id="8ab38-223">是</span><span class="sxs-lookup"><span data-stu-id="8ab38-223">Yes</span></span> | <span data-ttu-id="8ab38-224">否</span><span class="sxs-lookup"><span data-stu-id="8ab38-224">No</span></span> |
| `Add{LIFETIME}<{SERVICE}>(sp => new {IMPLEMENTATION})`<br><br><span data-ttu-id="8ab38-225">範例：</span><span class="sxs-lookup"><span data-stu-id="8ab38-225">Examples:</span></span><br><br>`services.AddSingleton<IMyDep>(sp => new MyDep());`<br>`services.AddSingleton<IMyDep>(sp => new MyDep(99));` | <span data-ttu-id="8ab38-226">是</span><span class="sxs-lookup"><span data-stu-id="8ab38-226">Yes</span></span> | <span data-ttu-id="8ab38-227">是</span><span class="sxs-lookup"><span data-stu-id="8ab38-227">Yes</span></span> | <span data-ttu-id="8ab38-228">是</span><span class="sxs-lookup"><span data-stu-id="8ab38-228">Yes</span></span> |
| `Add{LIFETIME}<{IMPLEMENTATION}>()`<br><br><span data-ttu-id="8ab38-229">範例：</span><span class="sxs-lookup"><span data-stu-id="8ab38-229">Example:</span></span><br><br>`services.AddSingleton<MyDep>();` | <span data-ttu-id="8ab38-230">是</span><span class="sxs-lookup"><span data-stu-id="8ab38-230">Yes</span></span> | <span data-ttu-id="8ab38-231">否</span><span class="sxs-lookup"><span data-stu-id="8ab38-231">No</span></span> | <span data-ttu-id="8ab38-232">否</span><span class="sxs-lookup"><span data-stu-id="8ab38-232">No</span></span> |
| `AddSingleton<{SERVICE}>(new {IMPLEMENTATION})`<br><br><span data-ttu-id="8ab38-233">範例：</span><span class="sxs-lookup"><span data-stu-id="8ab38-233">Examples:</span></span><br><br>`services.AddSingleton<IMyDep>(new MyDep());`<br>`services.AddSingleton<IMyDep>(new MyDep(99));` | <span data-ttu-id="8ab38-234">否</span><span class="sxs-lookup"><span data-stu-id="8ab38-234">No</span></span> | <span data-ttu-id="8ab38-235">是</span><span class="sxs-lookup"><span data-stu-id="8ab38-235">Yes</span></span> | <span data-ttu-id="8ab38-236">是</span><span class="sxs-lookup"><span data-stu-id="8ab38-236">Yes</span></span> |
| `AddSingleton(new {IMPLEMENTATION})`<br><br><span data-ttu-id="8ab38-237">範例：</span><span class="sxs-lookup"><span data-stu-id="8ab38-237">Examples:</span></span><br><br>`services.AddSingleton(new MyDep());`<br>`services.AddSingleton(new MyDep(99));` | <span data-ttu-id="8ab38-238">否</span><span class="sxs-lookup"><span data-stu-id="8ab38-238">No</span></span> | <span data-ttu-id="8ab38-239">否</span><span class="sxs-lookup"><span data-stu-id="8ab38-239">No</span></span> | <span data-ttu-id="8ab38-240">是</span><span class="sxs-lookup"><span data-stu-id="8ab38-240">Yes</span></span> |

<span data-ttu-id="8ab38-241">如需類型處置的詳細資訊，請參閱[＜服務處置＞](dependency-injection-guidelines.md#disposal-of-services)一節。</span><span class="sxs-lookup"><span data-stu-id="8ab38-241">For more information on type disposal, see the [Disposal of services](dependency-injection-guidelines.md#disposal-of-services) section.</span></span>

<span data-ttu-id="8ab38-242">此架構也會提供 `TryAdd{LIFETIME}` 擴充方法，只有在尚未註冊任何執行時，才會註冊服務。</span><span class="sxs-lookup"><span data-stu-id="8ab38-242">The framework also provides `TryAdd{LIFETIME}` extension methods, which register the service only if there isn't already an implementation registered.</span></span>

<span data-ttu-id="8ab38-243">在下列範例中，呼叫以註冊為的 `AddSingleton` `MessageWriter` 實作為的 `IMessageWriter` 。</span><span class="sxs-lookup"><span data-stu-id="8ab38-243">In the following example, the call to `AddSingleton` registers `MessageWriter` as an implementation for `IMessageWriter`.</span></span> <span data-ttu-id="8ab38-244">的呼叫 `TryAddSingleton` 沒有任何作用，因為 `IMessageWriter` 已經有已註冊的實作為：</span><span class="sxs-lookup"><span data-stu-id="8ab38-244">The call to `TryAddSingleton` has no effect because `IMessageWriter` already has a registered implementation:</span></span>

```csharp
services.AddSingleton<IMessageWriter, MessageWriter>();
services.TryAddSingleton<IMessageWriter, DifferentMessageWriter>();
```

<span data-ttu-id="8ab38-245">沒有 `TryAddSingleton` 任何作用，因為它已經加入，而且 "try" 將會失敗。</span><span class="sxs-lookup"><span data-stu-id="8ab38-245">The `TryAddSingleton` has no effect, as it was already added and the "try" will fail.</span></span>

<span data-ttu-id="8ab38-246">如需詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="8ab38-246">For more information, see:</span></span>

- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAdd%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddTransient%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddScoped%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddSingleton%2A>

<span data-ttu-id="8ab38-247">只有在尚未有 _of 相同類型 \* 的 TryAddEnumerable 時， [ (ServiceDescriptor) ](xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddEnumerable%2A) 方法才會註冊服務。</span><span class="sxs-lookup"><span data-stu-id="8ab38-247">The [TryAddEnumerable(ServiceDescriptor)](xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddEnumerable%2A) methods register the service only if there isn't already an implementation _of the same type\*.</span></span> <span data-ttu-id="8ab38-248">多個服務會透過 `IEnumerable<{SERVICE}>` 解析。</span><span class="sxs-lookup"><span data-stu-id="8ab38-248">Multiple services are resolved via `IEnumerable<{SERVICE}>`.</span></span> <span data-ttu-id="8ab38-249">註冊服務時，如果尚未加入相同類型的實例，請新增實例。</span><span class="sxs-lookup"><span data-stu-id="8ab38-249">When registering services, add an instance if one of the same types hasn't already been added.</span></span> <span data-ttu-id="8ab38-250">程式庫作者會使用 `TryAddEnumerable` 來避免在容器中註冊多個執行複本。</span><span class="sxs-lookup"><span data-stu-id="8ab38-250">Library authors use `TryAddEnumerable` to avoid registering multiple copies of an implementation in the container.</span></span>

<span data-ttu-id="8ab38-251">在下列範例中，第一次呼叫 `TryAddEnumerable` 註冊為的 `MessageWriter` 實作為 `IMessageWriter1` 。</span><span class="sxs-lookup"><span data-stu-id="8ab38-251">In the following example, the first call to `TryAddEnumerable` registers `MessageWriter` as an implementation for `IMessageWriter1`.</span></span> <span data-ttu-id="8ab38-252">第二個呼叫會註冊 `MessageWriter` `IMessageWriter2` 。</span><span class="sxs-lookup"><span data-stu-id="8ab38-252">The second call registers `MessageWriter` for `IMessageWriter2`.</span></span> <span data-ttu-id="8ab38-253">第三個呼叫沒有任何作用，因為 `IMessageWriter1` 已註冊的實作為 `MessageWriter` ：</span><span class="sxs-lookup"><span data-stu-id="8ab38-253">The third call has no effect because `IMessageWriter1` already has a registered implementation of `MessageWriter`:</span></span>

```csharp
public interface IMessageWriter1 { }
public interface IMessageWriter2 { }

public class MessageWriter : IMessageWriter1, IMessageWriter2
{
}

services.TryAddEnumerable(ServiceDescriptor.Singleton<IMessageWriter1, MessageWriter>());
services.TryAddEnumerable(ServiceDescriptor.Singleton<IMessageWriter2, MessageWriter>());
services.TryAddEnumerable(ServiceDescriptor.Singleton<IMessageWriter1, MessageWriter>());
```

<span data-ttu-id="8ab38-254">除非註冊相同類型的多個執行，否則服務註冊通常會獨立排序。</span><span class="sxs-lookup"><span data-stu-id="8ab38-254">Service registration is generally order independent except when registering multiple implementations of the same type.</span></span>

<span data-ttu-id="8ab38-255">`IServiceCollection` 是物件的集合 <xref:Microsoft.Extensions.DependencyInjection.ServiceDescriptor> 。</span><span class="sxs-lookup"><span data-stu-id="8ab38-255">`IServiceCollection` is a collection of <xref:Microsoft.Extensions.DependencyInjection.ServiceDescriptor> objects.</span></span> <span data-ttu-id="8ab38-256">下列範例顯示如何藉由建立和新增來註冊服務 `ServiceDescriptor` ：</span><span class="sxs-lookup"><span data-stu-id="8ab38-256">The following example shows how to register a service by creating and adding a `ServiceDescriptor`:</span></span>

```csharp
string secretKey = Configuration["SecretKey"];
var descriptor = new ServiceDescriptor(
    typeof(IMessageWriter),
    _ => new DefaultMessageWriter(secretKey),
    ServiceLifetime.Transient);

services.Add(descriptor);
```

<span data-ttu-id="8ab38-257">內建方法會 `Add{LIFETIME}` 使用相同的方法。</span><span class="sxs-lookup"><span data-stu-id="8ab38-257">The built-in `Add{LIFETIME}` methods use the same approach.</span></span> <span data-ttu-id="8ab38-258">例如，請參閱 [AddScoped 來源程式碼](https://github.com/dotnet/extensions/blob/v3.1.8/src/DependencyInjection/DI.Abstractions/src/ServiceCollectionServiceExtensions.cs#L216-L237)。</span><span class="sxs-lookup"><span data-stu-id="8ab38-258">For example, see the [AddScoped source code](https://github.com/dotnet/extensions/blob/v3.1.8/src/DependencyInjection/DI.Abstractions/src/ServiceCollectionServiceExtensions.cs#L216-L237).</span></span>

### <a name="constructor-injection-behavior"></a><span data-ttu-id="8ab38-259">建構函式插入行為</span><span class="sxs-lookup"><span data-stu-id="8ab38-259">Constructor injection behavior</span></span>

<span data-ttu-id="8ab38-260">您可以使用下列方法來解析服務：</span><span class="sxs-lookup"><span data-stu-id="8ab38-260">Services can be resolved by using:</span></span>

- <xref:System.IServiceProvider>
- <span data-ttu-id="8ab38-261"><xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities>:</span><span class="sxs-lookup"><span data-stu-id="8ab38-261"><xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities>:</span></span>
  - <span data-ttu-id="8ab38-262">建立未在容器中註冊的物件。</span><span class="sxs-lookup"><span data-stu-id="8ab38-262">Creates objects that aren't registered in the container.</span></span>
  - <span data-ttu-id="8ab38-263">搭配一些架構功能使用。</span><span class="sxs-lookup"><span data-stu-id="8ab38-263">Used with some framework features.</span></span>

<span data-ttu-id="8ab38-264">建構函式可以接受不是由相依性插入提供的引數，但引數必須指派預設值。</span><span class="sxs-lookup"><span data-stu-id="8ab38-264">Constructors can accept arguments that aren't provided by dependency injection, but the arguments must assign default values.</span></span>

<span data-ttu-id="8ab38-265">當服務由 `IServiceProvider` 或 `ActivatorUtilities` 解析時，建構函式插入會要求 *public* 建構函式。</span><span class="sxs-lookup"><span data-stu-id="8ab38-265">When services are resolved by `IServiceProvider` or `ActivatorUtilities`, constructor injection requires a *public* constructor.</span></span>

<span data-ttu-id="8ab38-266">當服務由 `ActivatorUtilities` 解析時，建構函式插入只要求只能有一個適用的建構函式存在。</span><span class="sxs-lookup"><span data-stu-id="8ab38-266">When services are resolved by `ActivatorUtilities`, constructor injection requires that only one applicable constructor exists.</span></span> <span data-ttu-id="8ab38-267">支援建構函式多載，但只能有一個多載存在，其引數可以藉由相依性插入而完成。</span><span class="sxs-lookup"><span data-stu-id="8ab38-267">Constructor overloads are supported, but only one overload can exist whose arguments can all be fulfilled by dependency injection.</span></span>

## <a name="scope-validation"></a><span data-ttu-id="8ab38-268">範圍驗證</span><span class="sxs-lookup"><span data-stu-id="8ab38-268">Scope validation</span></span>

<span data-ttu-id="8ab38-269">當應用程式在環境中執行 `Development` 並呼叫 [>createdefaultbuilder](generic-host.md#default-builder-settings) 來建立主機時，預設服務提供者會執行檢查，以確認：</span><span class="sxs-lookup"><span data-stu-id="8ab38-269">When the app runs in the `Development` environment and calls [CreateDefaultBuilder](generic-host.md#default-builder-settings) to build the host, the default service provider performs checks to verify that:</span></span>

- <span data-ttu-id="8ab38-270">範圍服務無法從根服務提供者解析。</span><span class="sxs-lookup"><span data-stu-id="8ab38-270">Scoped services aren't resolved from the root service provider.</span></span>
- <span data-ttu-id="8ab38-271">範圍服務不會插入 singleton 中。</span><span class="sxs-lookup"><span data-stu-id="8ab38-271">Scoped services aren't injected into singletons.</span></span>

<span data-ttu-id="8ab38-272">根服務提供者會在呼叫 <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> 時建立。</span><span class="sxs-lookup"><span data-stu-id="8ab38-272">The root service provider is created when <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> is called.</span></span> <span data-ttu-id="8ab38-273">當提供者啟動應用程式時，根服務提供者的存留期會對應到應用程式的存留期，並在應用程式關閉時處置。</span><span class="sxs-lookup"><span data-stu-id="8ab38-273">The root service provider's lifetime corresponds to the app's lifetime when the provider starts with the app and is disposed when the app shuts down.</span></span>

<span data-ttu-id="8ab38-274">範圍服務會由建立這些服務的容器處置。</span><span class="sxs-lookup"><span data-stu-id="8ab38-274">Scoped services are disposed by the container that created them.</span></span> <span data-ttu-id="8ab38-275">如果在根容器中建立範圍服務，服務的存留期會有效地升階為 singleton，因為它只會在應用程式關閉時由根容器處置。</span><span class="sxs-lookup"><span data-stu-id="8ab38-275">If a scoped service is created in the root container, the service's lifetime is effectively promoted to singleton because it's only disposed by the root container when the app shuts down.</span></span> <span data-ttu-id="8ab38-276">當呼叫 `BuildServiceProvider` 時，驗證服務範圍會攔截到這些情況。</span><span class="sxs-lookup"><span data-stu-id="8ab38-276">Validating service scopes catches these situations when `BuildServiceProvider` is called.</span></span>

## <a name="see-also"></a><span data-ttu-id="8ab38-277">請參閱</span><span class="sxs-lookup"><span data-stu-id="8ab38-277">See also</span></span>

- [<span data-ttu-id="8ab38-278">使用 .NET 中的相依性插入</span><span class="sxs-lookup"><span data-stu-id="8ab38-278">Use dependency injection in .NET</span></span>](dependency-injection-usage.md)
- [<span data-ttu-id="8ab38-279">相依性插入指導方針</span><span class="sxs-lookup"><span data-stu-id="8ab38-279">Dependency injection guidelines</span></span>](dependency-injection-guidelines.md)
- [<span data-ttu-id="8ab38-280">ASP.NET Core 中的相依性插入</span><span class="sxs-lookup"><span data-stu-id="8ab38-280">Dependency injection in ASP.NET Core</span></span>](/aspnet/core/fundamentals/dependency-injection)
- [<span data-ttu-id="8ab38-281">適用于 DI 應用程式開發的 NDC 會議模式</span><span class="sxs-lookup"><span data-stu-id="8ab38-281">NDC Conference Patterns for DI app development</span></span>](https://www.youtube.com/watch?v=x-C-CNBVTaY)
- [<span data-ttu-id="8ab38-282">明確相依性準則</span><span class="sxs-lookup"><span data-stu-id="8ab38-282">Explicit dependencies principle</span></span>](../../architecture/modern-web-apps-azure/architectural-principles.md#explicit-dependencies)
- [<span data-ttu-id="8ab38-283">控制的容器和相依性插入模式的反轉 (聖馬丁 Fowler) </span><span class="sxs-lookup"><span data-stu-id="8ab38-283">Inversion of control containers and the dependency injection pattern (Martin Fowler)</span></span>](https://www.martinfowler.com/articles/injection.html)
- <span data-ttu-id="8ab38-284">應該在 [github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues) 存放庫中建立 DI bug</span><span class="sxs-lookup"><span data-stu-id="8ab38-284">DI bugs should be created in the [github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues) repo</span></span>
