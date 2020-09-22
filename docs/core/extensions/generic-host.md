---
title: .NET 泛型主機
author: IEvangelist
description: 瞭解 .NET 泛型主機，其負責應用程式啟動和存留期管理。
ms.author: dapine
ms.date: 09/18/2020
ms.openlocfilehash: c1b22b4490dc54d462482976d1c2e512f812c9a9
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875851"
---
# <a name="net-generic-host"></a><span data-ttu-id="03439-103">.NET 泛型主機</span><span class="sxs-lookup"><span data-stu-id="03439-103">.NET Generic Host</span></span>

<span data-ttu-id="03439-104">背景工作服務範本會建立 .NET 泛型主機 <xref:Microsoft.Extensions.Hosting.HostBuilder> 。</span><span class="sxs-lookup"><span data-stu-id="03439-104">The Worker Service templates create a .NET Generic Host, <xref:Microsoft.Extensions.Hosting.HostBuilder>.</span></span> <span data-ttu-id="03439-105">泛型主機可以與其他類型的 .NET 應用程式搭配使用，例如主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="03439-105">The Generic Host can be used with other types of .NET applications, such as Console apps.</span></span>

<span data-ttu-id="03439-106">「主機」\*\* 是封裝所有應用程式資源的物件，例如：</span><span class="sxs-lookup"><span data-stu-id="03439-106">A *host* is an object that encapsulates an app's resources, such as:</span></span>

- <span data-ttu-id="03439-107">相依性插入 (DI)</span><span class="sxs-lookup"><span data-stu-id="03439-107">Dependency injection (DI)</span></span>
- <span data-ttu-id="03439-108">記錄</span><span class="sxs-lookup"><span data-stu-id="03439-108">Logging</span></span>
- <span data-ttu-id="03439-109">設定</span><span class="sxs-lookup"><span data-stu-id="03439-109">Configuration</span></span>
- <span data-ttu-id="03439-110">`IHostedService` 實作</span><span class="sxs-lookup"><span data-stu-id="03439-110">`IHostedService` implementations</span></span>

<span data-ttu-id="03439-111">當主機啟動時，它會呼叫 <xref:Microsoft.Extensions.Hosting.IHostedService.StartAsync%2A?displayProperty=nameWithType> <xref:Microsoft.Extensions.Hosting.IHostedService> 服務容器的託管服務集合中註冊的每個執行。</span><span class="sxs-lookup"><span data-stu-id="03439-111">When a host starts, it calls <xref:Microsoft.Extensions.Hosting.IHostedService.StartAsync%2A?displayProperty=nameWithType> on each implementation of <xref:Microsoft.Extensions.Hosting.IHostedService> registered in the service container's collection of hosted services.</span></span> <span data-ttu-id="03439-112">在背景工作服務應用程式中， `IHostedService` 包含實例的所有 <xref:Microsoft.Extensions.Hosting.BackgroundService> 實例都會 <xref:Microsoft.Extensions.Hosting.BackgroundService.ExecuteAsync%2A?displayProperty=nameWithType> 呼叫其方法。</span><span class="sxs-lookup"><span data-stu-id="03439-112">In a worker service app, all `IHostedService` implementations that contain <xref:Microsoft.Extensions.Hosting.BackgroundService> instances have their <xref:Microsoft.Extensions.Hosting.BackgroundService.ExecuteAsync%2A?displayProperty=nameWithType> methods called.</span></span>

<span data-ttu-id="03439-113">在單一物件中包含所有應用程式相互依存資源的主要理由便是生命週期管理：控制應用程式的啟動及順利關機。</span><span class="sxs-lookup"><span data-stu-id="03439-113">The main reason for including all of the app's interdependent resources in one object is lifetime management: control over app startup and graceful shutdown.</span></span> <span data-ttu-id="03439-114">這可透過 Microsoft 擴充功能來達成 [。裝載](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="03439-114">This is achieved with the [Microsoft.Extensions.Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) NuGet package.</span></span>

## <a name="set-up-a-host"></a><span data-ttu-id="03439-115">設定主機</span><span class="sxs-lookup"><span data-stu-id="03439-115">Set up a host</span></span>

<span data-ttu-id="03439-116">主機通常由 `Program` 類別的程式碼來設定、建置並執行。</span><span class="sxs-lookup"><span data-stu-id="03439-116">The host is typically configured, built, and run by code in the `Program` class.</span></span> <span data-ttu-id="03439-117">`Main` 方法：</span><span class="sxs-lookup"><span data-stu-id="03439-117">The `Main` method:</span></span>

- <span data-ttu-id="03439-118">呼叫 <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder> 方法來建立及設定建立器物件。</span><span class="sxs-lookup"><span data-stu-id="03439-118">Calls a <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder> method to create and configure a builder object.</span></span>
- <span data-ttu-id="03439-119">呼叫 <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> 以建立 <xref:Microsoft.Extensions.Hosting.IHost> 實例。</span><span class="sxs-lookup"><span data-stu-id="03439-119">Calls <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> to create an <xref:Microsoft.Extensions.Hosting.IHost> instance.</span></span>
- <span data-ttu-id="03439-120"><xref:Microsoft.Extensions.Hosting.HostingAbstractionsHostExtensions.Run%2A> <xref:Microsoft.Extensions.Hosting.HostingAbstractionsHostExtensions.RunAsync%2A> 在主機物件上呼叫或方法。</span><span class="sxs-lookup"><span data-stu-id="03439-120">Calls <xref:Microsoft.Extensions.Hosting.HostingAbstractionsHostExtensions.Run%2A> or <xref:Microsoft.Extensions.Hosting.HostingAbstractionsHostExtensions.RunAsync%2A> method on the host object.</span></span>

<span data-ttu-id="03439-121">.NET 背景工作服務範本會產生下列程式碼來建立泛型主機：</span><span class="sxs-lookup"><span data-stu-id="03439-121">The .NET Worker Service templates generate the following code to create a Generic Host:</span></span>

```csharp
public class Program
{
    public static void Main(string[] args)
    {
        CreateHostBuilder(args).Build().Run();
    }

    public static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureServices((hostContext, services) =>
            {
                services.AddHostedService<Worker>();
            });
}
```

## <a name="default-builder-settings"></a><span data-ttu-id="03439-122">預設建立器設定</span><span class="sxs-lookup"><span data-stu-id="03439-122">Default builder settings</span></span>

<span data-ttu-id="03439-123"><xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder%2A> 方法：</span><span class="sxs-lookup"><span data-stu-id="03439-123">The <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder%2A> method:</span></span>

- <span data-ttu-id="03439-124">設定 <xref:System.IO.Directory.GetCurrentDirectory> 所傳回路徑的內容根目錄。</span><span class="sxs-lookup"><span data-stu-id="03439-124">Sets the content root to the path returned by <xref:System.IO.Directory.GetCurrentDirectory>.</span></span>
- <span data-ttu-id="03439-125">從下列項目載入[主機組態](#host-configuration)：</span><span class="sxs-lookup"><span data-stu-id="03439-125">Loads [host configuration](#host-configuration) from:</span></span>
  - <span data-ttu-id="03439-126">前面加上的環境變數 `DOTNET_` 。</span><span class="sxs-lookup"><span data-stu-id="03439-126">Environment variables prefixed with `DOTNET_`.</span></span>
  - <span data-ttu-id="03439-127">命令列引數。</span><span class="sxs-lookup"><span data-stu-id="03439-127">Command-line arguments.</span></span>
- <span data-ttu-id="03439-128">從下列項目載入應用程式組態：</span><span class="sxs-lookup"><span data-stu-id="03439-128">Loads app configuration from:</span></span>
  - <span data-ttu-id="03439-129">*appsettings.js開啟*。</span><span class="sxs-lookup"><span data-stu-id="03439-129">*appsettings.json*.</span></span>
  - <span data-ttu-id="03439-130">*appsettings.{Environment}.json*</span><span class="sxs-lookup"><span data-stu-id="03439-130">*appsettings.{Environment}.json*.</span></span>
  - <span data-ttu-id="03439-131">應用程式在  環境中執行時的`Development`祕密管理員。</span><span class="sxs-lookup"><span data-stu-id="03439-131">Secret Manager when the app runs in the `Development` environment.</span></span>
  - <span data-ttu-id="03439-132">環境變數。</span><span class="sxs-lookup"><span data-stu-id="03439-132">Environment variables.</span></span>
  - <span data-ttu-id="03439-133">命令列引數。</span><span class="sxs-lookup"><span data-stu-id="03439-133">Command-line arguments.</span></span>
- <span data-ttu-id="03439-134">新增下列記錄提供者：</span><span class="sxs-lookup"><span data-stu-id="03439-134">Adds the following logging providers:</span></span>
  - <span data-ttu-id="03439-135">主控台</span><span class="sxs-lookup"><span data-stu-id="03439-135">Console</span></span>
  - <span data-ttu-id="03439-136">偵錯</span><span class="sxs-lookup"><span data-stu-id="03439-136">Debug</span></span>
  - <span data-ttu-id="03439-137">EventSource</span><span class="sxs-lookup"><span data-stu-id="03439-137">EventSource</span></span>
  - <span data-ttu-id="03439-138">EventLog (僅當在 Windows 上執行時)</span><span class="sxs-lookup"><span data-stu-id="03439-138">EventLog (only when running on Windows)</span></span>
- <span data-ttu-id="03439-139">當環境為時，可啟用範圍驗證和相依性 [驗證](xref:Microsoft.Extensions.DependencyInjection.ServiceProviderOptions.ValidateOnBuild) `Development` 。</span><span class="sxs-lookup"><span data-stu-id="03439-139">Enables scope validation and [dependency validation](xref:Microsoft.Extensions.DependencyInjection.ServiceProviderOptions.ValidateOnBuild) when the environment is `Development`.</span></span>

<span data-ttu-id="03439-140">`ConfigureServices`方法會公開將服務加入至實例的功能 <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="03439-140">The `ConfigureServices` method exposes the ability to add services to the <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="03439-141">之後，這些服務可以從相依性插入中取得。</span><span class="sxs-lookup"><span data-stu-id="03439-141">Later, these services can be made available from dependency injection.</span></span>

## <a name="framework-provided-services"></a><span data-ttu-id="03439-142">架構提供的服務</span><span class="sxs-lookup"><span data-stu-id="03439-142">Framework-provided services</span></span>

<span data-ttu-id="03439-143">下列服務會自動註冊：</span><span class="sxs-lookup"><span data-stu-id="03439-143">The following services are registered automatically:</span></span>

- [<span data-ttu-id="03439-144">IHostApplicationLifetime</span><span class="sxs-lookup"><span data-stu-id="03439-144">IHostApplicationLifetime</span></span>](#ihostapplicationlifetime)
- [<span data-ttu-id="03439-145">IHostLifetime</span><span class="sxs-lookup"><span data-stu-id="03439-145">IHostLifetime</span></span>](#ihostlifetime)
- [<span data-ttu-id="03439-146">IHostEnvironment</span><span class="sxs-lookup"><span data-stu-id="03439-146">IHostEnvironment</span></span>](#ihostenvironment)

## <a name="ihostapplicationlifetime"></a><span data-ttu-id="03439-147">IHostApplicationLifetime</span><span class="sxs-lookup"><span data-stu-id="03439-147">IHostApplicationLifetime</span></span>

<span data-ttu-id="03439-148">將 <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime> 服務插入任何類別，以處理啟動後和正常關機工作。</span><span class="sxs-lookup"><span data-stu-id="03439-148">Inject the <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime> service into any class to handle post-startup and graceful shutdown tasks.</span></span> <span data-ttu-id="03439-149">介面上的三個屬性是用於註冊應用程式啟動和應用程式關閉事件處理程序方法的取消語彙基元。</span><span class="sxs-lookup"><span data-stu-id="03439-149">Three properties on the interface are cancellation tokens used to register app start and app stop event handler methods.</span></span> <span data-ttu-id="03439-150">介面也包括 <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime.StopApplication> 方法。</span><span class="sxs-lookup"><span data-stu-id="03439-150">The interface also includes a <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime.StopApplication> method.</span></span>

<span data-ttu-id="03439-151">下列範例是 `IHostedService` 註冊事件的實作為 `IHostApplicationLifetime` ：</span><span class="sxs-lookup"><span data-stu-id="03439-151">The following example is an `IHostedService` implementation that registers `IHostApplicationLifetime` events:</span></span>

:::code language="csharp" source="snippets/configuration/app-lifetime/ExampleHostedService.cs" highlight="18-20":::

<span data-ttu-id="03439-152">您可以修改背景工作服務範本以新增 `ExampleHostedService` 實作為：</span><span class="sxs-lookup"><span data-stu-id="03439-152">The Worker Service template could be modified to add the `ExampleHostedService` implementation:</span></span>

:::code language="csharp" source="snippets/configuration/app-lifetime/Program.cs" range="1-16,36" highlight="15":::

<span data-ttu-id="03439-153">應用程式會寫入下列範例輸出：</span><span class="sxs-lookup"><span data-stu-id="03439-153">The application would write the following sample output:</span></span>

:::code language="csharp" source="snippets/configuration/app-lifetime/Program.cs" range="17-35":::

## <a name="ihostlifetime"></a><span data-ttu-id="03439-154">IHostLifetime</span><span class="sxs-lookup"><span data-stu-id="03439-154">IHostLifetime</span></span>

<span data-ttu-id="03439-155"><xref:Microsoft.Extensions.Hosting.IHostLifetime> 實作會控制主機啟動及停止的時機。</span><span class="sxs-lookup"><span data-stu-id="03439-155">The <xref:Microsoft.Extensions.Hosting.IHostLifetime> implementation controls when the host starts and when it stops.</span></span> <span data-ttu-id="03439-156">會使用最後一個註冊的實作。</span><span class="sxs-lookup"><span data-stu-id="03439-156">The last implementation registered is used.</span></span>

<span data-ttu-id="03439-157">`Microsoft.Extensions.Hosting.Internal.ConsoleLifetime` 是預設的 `IHostLifetime` 實作。</span><span class="sxs-lookup"><span data-stu-id="03439-157">`Microsoft.Extensions.Hosting.Internal.ConsoleLifetime` is the default `IHostLifetime` implementation.</span></span> <span data-ttu-id="03439-158">`ConsoleLifetime`:</span><span class="sxs-lookup"><span data-stu-id="03439-158">`ConsoleLifetime`:</span></span>

- <span data-ttu-id="03439-159">接聽<kbd>Ctrl</kbd> + <kbd>C</kbd>、 [SIGINT](https://en.wikipedia.org/wiki/Signal_(IPC)#SIGINT)或[SIGTERM](https://en.wikipedia.org/wiki/Signal_(IPC)#SIGTERM) ，並呼叫 <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime.StopApplication%2A> 以啟動關機程式。</span><span class="sxs-lookup"><span data-stu-id="03439-159">Listens for <kbd>Ctrl</kbd>+<kbd>C</kbd>, [SIGINT](https://en.wikipedia.org/wiki/Signal_(IPC)#SIGINT), or [SIGTERM](https://en.wikipedia.org/wiki/Signal_(IPC)#SIGTERM) and calls <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime.StopApplication%2A> to start the shutdown process.</span></span>
- <span data-ttu-id="03439-160">解除封鎖擴充功能 `RunAsync` ，例如和 `WaitForShutdownAsync` 。</span><span class="sxs-lookup"><span data-stu-id="03439-160">Unblocks extensions such as `RunAsync` and `WaitForShutdownAsync`.</span></span>

## <a name="ihostenvironment"></a><span data-ttu-id="03439-161">IHostEnvironment</span><span class="sxs-lookup"><span data-stu-id="03439-161">IHostEnvironment</span></span>

<span data-ttu-id="03439-162">將服務插入至 <xref:Microsoft.Extensions.Hosting.IHostEnvironment> 類別，以取得下列設定的相關資訊：</span><span class="sxs-lookup"><span data-stu-id="03439-162">Inject the <xref:Microsoft.Extensions.Hosting.IHostEnvironment> service into a class to get information about the following settings:</span></span>

- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.ApplicationName?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.ContentRootFileProvider?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.ContentRootPath?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.EnvironmentName?displayProperty=nameWithType>

## <a name="host-configuration"></a><span data-ttu-id="03439-163">主機組態</span><span class="sxs-lookup"><span data-stu-id="03439-163">Host configuration</span></span>

<span data-ttu-id="03439-164">主機組態用於 <xref:Microsoft.Extensions.Hosting.IHostEnvironment> 實作的屬性。</span><span class="sxs-lookup"><span data-stu-id="03439-164">Host configuration is used for the properties of the <xref:Microsoft.Extensions.Hosting.IHostEnvironment> implementation.</span></span>

<span data-ttu-id="03439-165">主機組態位於 <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureAppConfiguration%2A> 內的 [HostBuilderContext.Configuration](xref:Microsoft.Extensions.Hosting.HostBuilderContext.Configuration)。</span><span class="sxs-lookup"><span data-stu-id="03439-165">Host configuration is available from [HostBuilderContext.Configuration](xref:Microsoft.Extensions.Hosting.HostBuilderContext.Configuration) inside <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureAppConfiguration%2A>.</span></span> <span data-ttu-id="03439-166">在 `ConfigureAppConfiguration` 之後，應用程式組態會取代 `HostBuilderContext.Configuration`。</span><span class="sxs-lookup"><span data-stu-id="03439-166">After `ConfigureAppConfiguration`, `HostBuilderContext.Configuration` is replaced with the app config.</span></span>

<span data-ttu-id="03439-167">若要新增主機組態，請呼叫 `IHostBuilder` 上的 <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureHostConfiguration%2A>。</span><span class="sxs-lookup"><span data-stu-id="03439-167">To add host configuration, call <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureHostConfiguration%2A> on `IHostBuilder`.</span></span> <span data-ttu-id="03439-168">`ConfigureHostConfiguration` 可以多次呼叫，其結果是累加的。</span><span class="sxs-lookup"><span data-stu-id="03439-168">`ConfigureHostConfiguration` can be called multiple times with additive results.</span></span> <span data-ttu-id="03439-169">主機會使用指定索引鍵上最後設定值的任何選項。</span><span class="sxs-lookup"><span data-stu-id="03439-169">The host uses whichever option sets a value last on a given key.</span></span>

<span data-ttu-id="03439-170">下列範例會建立主機組態：</span><span class="sxs-lookup"><span data-stu-id="03439-170">The following example creates host configuration:</span></span>

:::code language="csharp" source="snippets/configuration/console-host/Program.cs" highlight="13-19":::

## <a name="app-configuration"></a><span data-ttu-id="03439-171">應用程式設定</span><span class="sxs-lookup"><span data-stu-id="03439-171">App configuration</span></span>

<span data-ttu-id="03439-172">應用程式組態的建立方式是在 `IHostBuilder` 上呼叫 <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureAppConfiguration%2A>。</span><span class="sxs-lookup"><span data-stu-id="03439-172">App configuration is created by calling <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureAppConfiguration%2A> on `IHostBuilder`.</span></span> <span data-ttu-id="03439-173">`ConfigureAppConfiguration` 可以多次呼叫，其結果是累加的。</span><span class="sxs-lookup"><span data-stu-id="03439-173">`ConfigureAppConfiguration` can be called multiple times with additive results.</span></span> <span data-ttu-id="03439-174">應用程式會使用指定索引鍵上最後設定值的任何選項。</span><span class="sxs-lookup"><span data-stu-id="03439-174">The app uses whichever option sets a value last on a given key.</span></span>

<span data-ttu-id="03439-175">由 `ConfigureAppConfiguration` 建立的組態位於 [HostBuilderContext.Configuration](xref:Microsoft.Extensions.Hosting.HostBuilderContext.Configuration%2A)，可用於後續作業並用作 DI 中的服務。</span><span class="sxs-lookup"><span data-stu-id="03439-175">The configuration created by `ConfigureAppConfiguration` is available at [HostBuilderContext.Configuration](xref:Microsoft.Extensions.Hosting.HostBuilderContext.Configuration%2A) for subsequent operations and as a service from DI.</span></span> <span data-ttu-id="03439-176">主機組態也會新增至應用程式組態。</span><span class="sxs-lookup"><span data-stu-id="03439-176">The host configuration is also added to the app configuration.</span></span>

<span data-ttu-id="03439-177">如需詳細資訊，請參閱 [.net 中](configuration.md)的設定。</span><span class="sxs-lookup"><span data-stu-id="03439-177">For more information, see [Configuration in .NET](configuration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="03439-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03439-178">See also</span></span>

- [<span data-ttu-id="03439-179">.NET 中的設定</span><span class="sxs-lookup"><span data-stu-id="03439-179">Configuration in .NET</span></span>](configuration.md)
- [<span data-ttu-id="03439-180">ASP.NET Core Web 主機</span><span class="sxs-lookup"><span data-stu-id="03439-180">ASP.NET Core Web Host</span></span>](/aspnet/core/fundamentals/host/web-host)
