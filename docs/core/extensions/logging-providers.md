---
title: .NET 中的記錄提供者
description: 瞭解如何在 .NET 應用程式中使用記錄提供者 API。
author: IEvangelist
ms.author: dapine
ms.date: 09/25/2020
ms.openlocfilehash: 936413be1514e6cea20e28a7d4431c572560d193
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2020
ms.locfileid: "91614693"
---
# <a name="logging-providers-in-net"></a><span data-ttu-id="55125-103">.NET 中的記錄提供者</span><span class="sxs-lookup"><span data-stu-id="55125-103">Logging providers in .NET</span></span>

<span data-ttu-id="55125-104">除了提供者之外，記錄提供者會保存記錄，只會將 `Console` 記錄顯示為標準輸出。</span><span class="sxs-lookup"><span data-stu-id="55125-104">Logging providers persist logs, except for the `Console` provider, which only displays logs as standard output.</span></span> <span data-ttu-id="55125-105">例如，Azure 應用程式 Insights 提供者會將記錄儲存在 Azure 應用程式深入解析中。</span><span class="sxs-lookup"><span data-stu-id="55125-105">For example, the Azure Application Insights provider stores logs in Azure Application Insights.</span></span> <span data-ttu-id="55125-106">可以啟用多個提供者。</span><span class="sxs-lookup"><span data-stu-id="55125-106">Multiple providers can be enabled.</span></span>

<span data-ttu-id="55125-107">預設的 .NET 背景工作應用程式範本：</span><span class="sxs-lookup"><span data-stu-id="55125-107">The default .NET Worker app templates:</span></span>

- <span data-ttu-id="55125-108">使用 [一般主機](generic-host.md)。</span><span class="sxs-lookup"><span data-stu-id="55125-108">Use the [Generic Host](generic-host.md).</span></span>
- <span data-ttu-id="55125-109">呼叫 <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder%2A> ，這會新增下列記錄提供者：</span><span class="sxs-lookup"><span data-stu-id="55125-109">Call <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder%2A>, which adds the following logging providers:</span></span>
  - [<span data-ttu-id="55125-110">主控台</span><span class="sxs-lookup"><span data-stu-id="55125-110">Console</span></span>](#console)
  - [<span data-ttu-id="55125-111">偵錯</span><span class="sxs-lookup"><span data-stu-id="55125-111">Debug</span></span>](#debug)
  - [<span data-ttu-id="55125-112">EventSource</span><span class="sxs-lookup"><span data-stu-id="55125-112">EventSource</span></span>](#event-source)
  - <span data-ttu-id="55125-113">[EventLog](#windows-eventlog)：僅限 Windows</span><span class="sxs-lookup"><span data-stu-id="55125-113">[EventLog](#windows-eventlog): Windows only</span></span>

:::code language="csharp" source="snippets/configuration/console/Program.cs" highlight="12":::

<span data-ttu-id="55125-114">上述程式碼顯示 `Program` 使用 .net 背景工作應用程式範本所建立的類別。</span><span class="sxs-lookup"><span data-stu-id="55125-114">The preceding code shows the `Program` class created with the .NET Worker app templates.</span></span> <span data-ttu-id="55125-115">接下來的幾節會根據使用一般主機的 .NET 背景工作應用程式範本提供範例。</span><span class="sxs-lookup"><span data-stu-id="55125-115">The next several sections provide samples based on the .NET Worker app templates, which use the Generic Host.</span></span>

<span data-ttu-id="55125-116">若要覆寫所加入的預設記錄提供者集合 `Host.CreateDefaultBuilder` ，請呼叫 `ClearProviders` 並加入您想要的記錄提供者。</span><span class="sxs-lookup"><span data-stu-id="55125-116">To override the default set of logging providers added by `Host.CreateDefaultBuilder`, call `ClearProviders` and add the logging providers you want.</span></span> <span data-ttu-id="55125-117">例如，下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="55125-117">For example, the following code:</span></span>

- <span data-ttu-id="55125-118">從產生器 <xref:Microsoft.Extensions.Logging.LoggingBuilderExtensions.ClearProviders%2A> 中移除所有實例的呼叫 <xref:Microsoft.Extensions.Logging.ILoggerProvider> 。</span><span class="sxs-lookup"><span data-stu-id="55125-118">Calls <xref:Microsoft.Extensions.Logging.LoggingBuilderExtensions.ClearProviders%2A> to remove all the <xref:Microsoft.Extensions.Logging.ILoggerProvider> instances from the builder.</span></span>
- <span data-ttu-id="55125-119">新增 [主控台](#console) 記錄提供者。</span><span class="sxs-lookup"><span data-stu-id="55125-119">Adds the [Console](#console) logging provider.</span></span>

```csharp
static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureLogging(logging =>
        {
            logging.ClearProviders();
            logging.AddConsole();
        });
```

<span data-ttu-id="55125-120">如需其他提供者，請參閱：</span><span class="sxs-lookup"><span data-stu-id="55125-120">For additional providers, see:</span></span>

- <span data-ttu-id="55125-121">[內建的記錄提供者](#built-in-logging-providers)。</span><span class="sxs-lookup"><span data-stu-id="55125-121">[Built-in logging providers](#built-in-logging-providers).</span></span>
- <span data-ttu-id="55125-122">[協力廠商記錄提供者](#third-party-logging-providers)。</span><span class="sxs-lookup"><span data-stu-id="55125-122">[Third-party logging providers](#third-party-logging-providers).</span></span>

## <a name="configure-a-service-that-depends-on-ilogger"></a><span data-ttu-id="55125-123">設定相依于 ILogger 的服務</span><span class="sxs-lookup"><span data-stu-id="55125-123">Configure a service that depends on ILogger</span></span>

<span data-ttu-id="55125-124">若要設定相依的服務 `ILogger<T>` ，請使用函式插入或提供 factory 方法。</span><span class="sxs-lookup"><span data-stu-id="55125-124">To configure a service that depends on `ILogger<T>`, use constructor injection or provide a factory method.</span></span> <span data-ttu-id="55125-125">只有在沒有其他選項時，才建議使用 Factory 方法。</span><span class="sxs-lookup"><span data-stu-id="55125-125">The factory method approach is recommended only if there is no other option.</span></span> <span data-ttu-id="55125-126">例如，假設有一個服務需要 `ILogger<T>` DI 提供的實例：</span><span class="sxs-lookup"><span data-stu-id="55125-126">For example, consider a service that needs an `ILogger<T>` instance provided by DI:</span></span>

```csharp
.ConfigureServices(services =>
    services.AddSingleton<IExampleService>(container =>
        new DefaultExampleService
        {
            Logger = container.GetRequiredService<ILogger<IExampleService>>()
        }));
```

<span data-ttu-id="55125-127">上述程式碼是 [Func<IServiceProvider，IExampleService>](/dotnet/api/system.func-2) ，它會在 DI 容器第一次需要建立的實例時執行 `IExampleService` 。</span><span class="sxs-lookup"><span data-stu-id="55125-127">The preceding code is a [Func<IServiceProvider, IExampleService>](/dotnet/api/system.func-2) that runs the first time the DI container needs to construct an instance of `IExampleService`.</span></span> <span data-ttu-id="55125-128">您可以用此方式存取任何已註冊的服務。</span><span class="sxs-lookup"><span data-stu-id="55125-128">You can access any of the registered services in this way.</span></span>

## <a name="built-in-logging-providers"></a><span data-ttu-id="55125-129">內建記錄提供者</span><span class="sxs-lookup"><span data-stu-id="55125-129">Built-in logging providers</span></span>

<span data-ttu-id="55125-130">Microsoft 擴充功能包含下列記錄提供者，作為執行時間程式庫的一部分：</span><span class="sxs-lookup"><span data-stu-id="55125-130">Microsoft Extensions include the following logging providers as part of the runtime libraries:</span></span>

- [<span data-ttu-id="55125-131">主控台</span><span class="sxs-lookup"><span data-stu-id="55125-131">Console</span></span>](#console)
- [<span data-ttu-id="55125-132">偵錯</span><span class="sxs-lookup"><span data-stu-id="55125-132">Debug</span></span>](#debug)
- [<span data-ttu-id="55125-133">EventSource</span><span class="sxs-lookup"><span data-stu-id="55125-133">EventSource</span></span>](#event-source)
- [<span data-ttu-id="55125-134">EventLog</span><span class="sxs-lookup"><span data-stu-id="55125-134">EventLog</span></span>](#windows-eventlog)

<span data-ttu-id="55125-135">下列記錄提供者是由 Microsoft 所提供，但不是執行時間程式庫的一部分。</span><span class="sxs-lookup"><span data-stu-id="55125-135">The following logging providers are shipped by Microsoft, but not as part of the runtime libraries.</span></span> <span data-ttu-id="55125-136">它們必須安裝為其他 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="55125-136">They must be installed as additional NuGet packages.</span></span>

- [<span data-ttu-id="55125-137">AzureAppServicesFile 和 AzureAppServicesBlob</span><span class="sxs-lookup"><span data-stu-id="55125-137">AzureAppServicesFile and AzureAppServicesBlob</span></span>](#azure-app-service)
- [<span data-ttu-id="55125-138">ApplicationInsights</span><span class="sxs-lookup"><span data-stu-id="55125-138">ApplicationInsights</span></span>](#azure-application-insights)

### <a name="console"></a><span data-ttu-id="55125-139">主控台</span><span class="sxs-lookup"><span data-stu-id="55125-139">Console</span></span>

<span data-ttu-id="55125-140">`Console`提供者會將輸出記錄到主控台。</span><span class="sxs-lookup"><span data-stu-id="55125-140">The `Console` provider logs output to the console.</span></span> <span data-ttu-id="55125-141">如需有關在開發期間查看記錄的詳細資訊 `Console` ，請參閱 [從 dotnet 執行和 Visual Studio 記錄輸出](logging.md#logging-output-from-dotnet-run-and-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="55125-141">For more information on viewing `Console` logs in development, see [Logging output from dotnet run and Visual Studio](logging.md#logging-output-from-dotnet-run-and-visual-studio).</span></span>

### <a name="debug"></a><span data-ttu-id="55125-142">偵錯</span><span class="sxs-lookup"><span data-stu-id="55125-142">Debug</span></span>

<span data-ttu-id="55125-143">`Debug`提供者會使用 system.servicemodel 類別來寫入[System.Diagnostics.Debug](/dotnet/api/system.diagnostics.debug)記錄檔輸出。</span><span class="sxs-lookup"><span data-stu-id="55125-143">The `Debug` provider writes log output by using the [System.Diagnostics.Debug](/dotnet/api/system.diagnostics.debug) class.</span></span> <span data-ttu-id="55125-144">要 `System.Diagnostics.Debug.WriteLine` 寫入 `Debug` 提供者的呼叫。</span><span class="sxs-lookup"><span data-stu-id="55125-144">Calls to `System.Diagnostics.Debug.WriteLine` write to the `Debug` provider.</span></span>

<span data-ttu-id="55125-145">在 Linux 上， `Debug` 提供者記錄檔位置是散發相依的，可能是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="55125-145">On Linux, the `Debug` provider log location is distribution-dependent and may be one of the following:</span></span>

- <span data-ttu-id="55125-146">*/var/log/message*</span><span class="sxs-lookup"><span data-stu-id="55125-146">*/var/log/message*</span></span>
- <span data-ttu-id="55125-147">*/var/log/syslog*</span><span class="sxs-lookup"><span data-stu-id="55125-147">*/var/log/syslog*</span></span>

### <a name="event-source"></a><span data-ttu-id="55125-148">事件來源</span><span class="sxs-lookup"><span data-stu-id="55125-148">Event Source</span></span>

<span data-ttu-id="55125-149">`EventSource`提供者會以名稱寫入跨平臺事件來源 `Microsoft-Extensions-Logging` 。</span><span class="sxs-lookup"><span data-stu-id="55125-149">The `EventSource` provider writes to a cross-platform event source with the name `Microsoft-Extensions-Logging`.</span></span> <span data-ttu-id="55125-150">在 Windows 上，提供者會使用 [ETW](/windows/win32/etw/event-tracing-portal)。</span><span class="sxs-lookup"><span data-stu-id="55125-150">On Windows, the provider uses [ETW](/windows/win32/etw/event-tracing-portal).</span></span>

#### <a name="dotnet-trace-tooling"></a><span data-ttu-id="55125-151">dotnet 追蹤工具</span><span class="sxs-lookup"><span data-stu-id="55125-151">dotnet trace tooling</span></span>

<span data-ttu-id="55125-152">[Dotnet 追蹤](../diagnostics/dotnet-trace.md)工具是一種跨平臺 CLI 全域工具，可讓您收集正在執行之進程的 .net Core 追蹤。</span><span class="sxs-lookup"><span data-stu-id="55125-152">The [dotnet-trace](../diagnostics/dotnet-trace.md) tool is a cross-platform CLI global tool that enables the collection of .NET Core traces of a running process.</span></span> <span data-ttu-id="55125-153">此工具會 <xref:Microsoft.Extensions.Logging.EventSource> 使用來收集提供者資料 <xref:Microsoft.Extensions.Logging.EventSource.LoggingEventSource> 。</span><span class="sxs-lookup"><span data-stu-id="55125-153">The tool collects <xref:Microsoft.Extensions.Logging.EventSource> provider data using a <xref:Microsoft.Extensions.Logging.EventSource.LoggingEventSource>.</span></span>

<span data-ttu-id="55125-154">如需安裝指示，請參閱 [dotnet](../diagnostics/dotnet-trace.md) 。</span><span class="sxs-lookup"><span data-stu-id="55125-154">See [dotnet-trace](../diagnostics/dotnet-trace.md) for installation instructions.</span></span> <span data-ttu-id="55125-155">如需使用的診斷教學課程 `dotnet-trace` ，請參閱 [.net Core 中的高 CPU 使用率的調試](/../diagnostics/debug-highcpu.md)程式。</span><span class="sxs-lookup"><span data-stu-id="55125-155">For a diagnostic tutorial using `dotnet-trace`, see [Debug high CPU usage in .NET Core](/../diagnostics/debug-highcpu.md).</span></span>

### <a name="windows-eventlog"></a><span data-ttu-id="55125-156">Windows EventLog</span><span class="sxs-lookup"><span data-stu-id="55125-156">Windows EventLog</span></span>

<span data-ttu-id="55125-157">此 `EventLog` 提供者會將記錄輸出傳送至 Windows 事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="55125-157">The `EventLog` provider sends log output to the Windows Event Log.</span></span> <span data-ttu-id="55125-158">不同于其他提供者， `EventLog` 提供者 ***不*** 會繼承預設的非提供者設定。</span><span class="sxs-lookup"><span data-stu-id="55125-158">Unlike the other providers, the `EventLog` provider does ***not*** inherit the default non-provider settings.</span></span> <span data-ttu-id="55125-159">如果 `EventLog` 未指定記錄檔設定，則預設為 `LogLevel.Warning` 。</span><span class="sxs-lookup"><span data-stu-id="55125-159">If `EventLog` log settings aren't specified, they default to `LogLevel.Warning`.</span></span>

<span data-ttu-id="55125-160">若要記錄低於 <xref:Microsoft.Extensions.Logging.LogLevel.Warning?displayProperty=nameWithType> 的事件，請明確設定記錄層級。</span><span class="sxs-lookup"><span data-stu-id="55125-160">To log events lower than <xref:Microsoft.Extensions.Logging.LogLevel.Warning?displayProperty=nameWithType>, explicitly set the log level.</span></span> <span data-ttu-id="55125-161">下列範例會將事件記錄檔的預設記錄層級設定為 <xref:Microsoft.Extensions.Logging.LogLevel.Information?displayProperty=nameWithType> ：</span><span class="sxs-lookup"><span data-stu-id="55125-161">The following example sets the Event Log default log level to <xref:Microsoft.Extensions.Logging.LogLevel.Information?displayProperty=nameWithType>:</span></span>

```json
"Logging": {
  "EventLog": {
    "LogLevel": {
      "Default": "Information"
    }
  }
}
```

<span data-ttu-id="55125-162">[AddEventLog](xref:Microsoft.Extensions.Logging.EventLoggerFactoryExtensions) 多載可傳入 <xref:Microsoft.Extensions.Logging.EventLog.EventLogSettings> 。</span><span class="sxs-lookup"><span data-stu-id="55125-162">[AddEventLog overloads](xref:Microsoft.Extensions.Logging.EventLoggerFactoryExtensions) can pass in <xref:Microsoft.Extensions.Logging.EventLog.EventLogSettings>.</span></span> <span data-ttu-id="55125-163">如果 `null` 未指定，則會使用下列預設設定：</span><span class="sxs-lookup"><span data-stu-id="55125-163">If `null` or not specified, the following default settings are used:</span></span>

- <span data-ttu-id="55125-164">`LogName`：「應用程式」</span><span class="sxs-lookup"><span data-stu-id="55125-164">`LogName`: "Application"</span></span>
- <span data-ttu-id="55125-165">`SourceName`：「.NET 執行時間」</span><span class="sxs-lookup"><span data-stu-id="55125-165">`SourceName`: ".NET Runtime"</span></span>
- <span data-ttu-id="55125-166">`MachineName`：使用本機電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="55125-166">`MachineName`: The local machine name is used.</span></span>

<span data-ttu-id="55125-167">下列程式碼會將的 `SourceName` 預設值從變更 `".NET Runtime"` 為 `CustomLogs` ：</span><span class="sxs-lookup"><span data-stu-id="55125-167">The following code changes the `SourceName` from the default value of `".NET Runtime"` to `CustomLogs`:</span></span>

```csharp
public class Program
{
    public static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging =>
                logging.AddEventLog(configuration =>
                    configuration.SourceName = "CustomLogs"));
}
```

### <a name="azure-app-service"></a><span data-ttu-id="55125-168">Azure App Service</span><span class="sxs-lookup"><span data-stu-id="55125-168">Azure App Service</span></span>

<span data-ttu-id="55125-169">[Microsoft.Extensions.Logging.AzureAppServices](https://www.nuget.org/packages/Microsoft.Extensions.Logging.AzureAppServices) 提供者套件會將記錄寫入至 Azure App Service 應用程式檔案系統中的文字檔，並寫入至 Azure 儲存體帳戶中的 [Blob 儲存體](/azure/storage/blobs/storage-quickstart-blobs-dotnet#what-is-blob-storage)。</span><span class="sxs-lookup"><span data-stu-id="55125-169">The [Microsoft.Extensions.Logging.AzureAppServices](https://www.nuget.org/packages/Microsoft.Extensions.Logging.AzureAppServices) provider package writes logs to text files in an Azure App Service app's file system and to [blob storage](/azure/storage/blobs/storage-quickstart-blobs-dotnet#what-is-blob-storage) in an Azure Storage account.</span></span>

<span data-ttu-id="55125-170">提供者套件未包含在執行時間程式庫中。</span><span class="sxs-lookup"><span data-stu-id="55125-170">The provider package isn't included in the runtime libraries.</span></span> <span data-ttu-id="55125-171">若要使用提供者，請將提供者套件新增至專案。</span><span class="sxs-lookup"><span data-stu-id="55125-171">To use the provider, add the provider package to the project.</span></span>

<span data-ttu-id="55125-172">如果要進行提供者設定，請使用 <xref:Microsoft.Extensions.Logging.AzureAppServices.AzureFileLoggerOptions> 和 <xref:Microsoft.Extensions.Logging.AzureAppServices.AzureBlobLoggerOptions>，如以下範例中所示：</span><span class="sxs-lookup"><span data-stu-id="55125-172">To configure provider settings, use <xref:Microsoft.Extensions.Logging.AzureAppServices.AzureFileLoggerOptions> and <xref:Microsoft.Extensions.Logging.AzureAppServices.AzureBlobLoggerOptions>, as shown in the following example:</span></span>

```csharp
class Program
{
    static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging =>
                logging.AddAzureWebAppDiagnostics())
            .ConfigureServices(services =>
                services.Configure<AzureFileLoggerOptions>(options =>
                {
                    options.FileName = "azure-diagnostics-";
                    options.FileSizeLimit = 50 * 1024;
                    options.RetainedFileCountLimit = 5;
                })
                .Configure<AzureBlobLoggerOptions>(options =>
                {
                    options.BlobName = "log.txt";
                }));
}
```

<span data-ttu-id="55125-173">當部署到 Azure App Service 時，應用程式會使用 Azure 入口網站之**App Service**頁面的 [ [App Service 記錄](/azure/app-service/web-sites-enable-diagnostic-log/#enable-application-logging-windows)] 區段中的設定。</span><span class="sxs-lookup"><span data-stu-id="55125-173">When deployed to Azure App Service, the app uses the settings in the [App Service logs](/azure/app-service/web-sites-enable-diagnostic-log/#enable-application-logging-windows) section of the **App Service** page of the Azure portal.</span></span> <span data-ttu-id="55125-174">當下列設定更新時，變更會立即生效，而不需要重新啟動或重新部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="55125-174">When the following settings are updated, the changes take effect immediately without requiring a restart or redeployment of the app.</span></span>

- <span data-ttu-id="55125-175">**應用程式記錄 (檔案系統)**</span><span class="sxs-lookup"><span data-stu-id="55125-175">**Application Logging (Filesystem)**</span></span>
- <span data-ttu-id="55125-176">**應用程式記錄 (Blob)**</span><span class="sxs-lookup"><span data-stu-id="55125-176">**Application Logging (Blob)**</span></span>

<span data-ttu-id="55125-177">記錄檔的預設位置為 *D:\\home\\LogFiles\\Application* 資料夾，而預設檔案名稱為 *diagnostics-yyyymmdd.txt*。</span><span class="sxs-lookup"><span data-stu-id="55125-177">The default location for log files is in the *D:\\home\\LogFiles\\Application* folder, and the default file name is *diagnostics-yyyymmdd.txt*.</span></span> <span data-ttu-id="55125-178">預設檔案大小限制為 10 MB，而預設保留的檔案數目上限為 2。</span><span class="sxs-lookup"><span data-stu-id="55125-178">The default file size limit is 10 MB, and the default maximum number of files retained is 2.</span></span> <span data-ttu-id="55125-179">預設 Blob 名稱為 *{app-name}{timestamp}/yyyy/mm/dd/hh/{guid}-applicationLog.txt*。</span><span class="sxs-lookup"><span data-stu-id="55125-179">The default blob name is *{app-name}{timestamp}/yyyy/mm/dd/hh/{guid}-applicationLog.txt*.</span></span>

<span data-ttu-id="55125-180">只有當專案在 Azure 環境中執行時，此提供者才會記錄。</span><span class="sxs-lookup"><span data-stu-id="55125-180">This provider only logs when the project runs in the Azure environment.</span></span>

#### <a name="azure-log-streaming"></a><span data-ttu-id="55125-181">Azure 記錄資料流</span><span class="sxs-lookup"><span data-stu-id="55125-181">Azure log streaming</span></span>

<span data-ttu-id="55125-182">Azure 記錄串流支援即時查看記錄活動：</span><span class="sxs-lookup"><span data-stu-id="55125-182">Azure log streaming supports viewing log activity in real time from:</span></span>

- <span data-ttu-id="55125-183">應用程式伺服器</span><span class="sxs-lookup"><span data-stu-id="55125-183">The app server</span></span>
- <span data-ttu-id="55125-184">網頁伺服器</span><span class="sxs-lookup"><span data-stu-id="55125-184">The web server</span></span>
- <span data-ttu-id="55125-185">失敗的要求追蹤</span><span class="sxs-lookup"><span data-stu-id="55125-185">Failed request tracing</span></span>

<span data-ttu-id="55125-186">若要設定 Azure 記錄資料流：</span><span class="sxs-lookup"><span data-stu-id="55125-186">To configure Azure log streaming:</span></span>

- <span data-ttu-id="55125-187">從應用程式的入口網站頁面流覽至 [ **App Service 記錄** ] 頁面。</span><span class="sxs-lookup"><span data-stu-id="55125-187">Navigate to the **App Service logs** page from the app's portal page.</span></span>
- <span data-ttu-id="55125-188">將 [應用程式記錄 (檔案系統)]\*\*\*\* 設定為 [開啟]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="55125-188">Set **Application Logging (Filesystem)** to **On**.</span></span>
- <span data-ttu-id="55125-189">選擇記錄 [層級]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="55125-189">Choose the log **Level**.</span></span> <span data-ttu-id="55125-190">此設定僅適用于 Azure 記錄串流。</span><span class="sxs-lookup"><span data-stu-id="55125-190">This setting only applies to Azure log streaming.</span></span>

<span data-ttu-id="55125-191">流覽至 [ **記錄資料流程** ] 頁面以查看記錄。</span><span class="sxs-lookup"><span data-stu-id="55125-191">Navigate to the **Log Stream** page to view logs.</span></span> <span data-ttu-id="55125-192">記錄的訊息會與介面一起記錄 `ILogger` 。</span><span class="sxs-lookup"><span data-stu-id="55125-192">The logged messages are logged with the `ILogger` interface.</span></span>

### <a name="azure-application-insights"></a><span data-ttu-id="55125-193">Azure Application Insights</span><span class="sxs-lookup"><span data-stu-id="55125-193">Azure Application Insights</span></span>

<span data-ttu-id="55125-194">[ApplicationInsights](https://www.nuget.org/packages/Microsoft.Extensions.Logging.ApplicationInsights)提供者套件會將記錄寫入[Azure 應用程式見解](/azure/azure-monitor/app/cloudservices)。</span><span class="sxs-lookup"><span data-stu-id="55125-194">The [Microsoft.Extensions.Logging.ApplicationInsights](https://www.nuget.org/packages/Microsoft.Extensions.Logging.ApplicationInsights) provider package writes logs to [Azure Application Insights](/azure/azure-monitor/app/cloudservices).</span></span> <span data-ttu-id="55125-195">Application Insights 是可監視 Web 應用程式的服務，並提供可用來查詢及分析遙測資料的工具。</span><span class="sxs-lookup"><span data-stu-id="55125-195">Application Insights is a service that monitors a web app and provides tools for querying and analyzing the telemetry data.</span></span> <span data-ttu-id="55125-196">如果您使用此提供者，就可以使用 Application Insights 工具來查詢及分析記錄。</span><span class="sxs-lookup"><span data-stu-id="55125-196">If you use this provider, you can query and analyze your logs by using the Application Insights tools.</span></span>

<span data-ttu-id="55125-197">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="55125-197">For more information, see the following resources:</span></span>

- [<span data-ttu-id="55125-198">Application Insights 概觀</span><span class="sxs-lookup"><span data-stu-id="55125-198">Application Insights overview</span></span>](/azure/application-insights/app-insights-overview)
- <span data-ttu-id="55125-199">[適用於 .NET Core ILogger 記錄的 ApplicationInsightsLoggerProvider](/azure/azure-monitor/app/ilogger)：如果您想要實作記錄提供者，而不需要 Application Insights 遙測的其餘部分，請從這裡開始。</span><span class="sxs-lookup"><span data-stu-id="55125-199">[ApplicationInsightsLoggerProvider for .NET Core ILogger logs](/azure/azure-monitor/app/ilogger) - Start here if you want to implement the logging provider without the rest of Application Insights telemetry.</span></span>
- <span data-ttu-id="55125-200">[Application Insights logging adapters](/azure/azure-monitor/app/asp-net-trace-logs) (Application Insights 記錄配接器)。</span><span class="sxs-lookup"><span data-stu-id="55125-200">[Application Insights logging adapters](/azure/azure-monitor/app/asp-net-trace-logs).</span></span>
- <span data-ttu-id="55125-201">[安裝、設定及初始化 Application Insights SDK](/learn/modules/instrument-web-app-code-with-application-insights)：Microsoft Learn 網站上的互動式教學課程。</span><span class="sxs-lookup"><span data-stu-id="55125-201">[Install, configure, and initialize the Application Insights SDK](/learn/modules/instrument-web-app-code-with-application-insights) - Interactive tutorial on the Microsoft Learn site.</span></span>

## <a name="third-party-logging-providers"></a><span data-ttu-id="55125-202">協力廠商記錄提供者</span><span class="sxs-lookup"><span data-stu-id="55125-202">Third-party logging providers</span></span>

<span data-ttu-id="55125-203">以下是一些可搭配各種 .NET 工作負載使用的協力廠商記錄架構：</span><span class="sxs-lookup"><span data-stu-id="55125-203">Here are some third-party logging frameworks that work with various .NET workloads:</span></span>

- <span data-ttu-id="55125-204">[elmah.io](https://elmah.io) ([GitHub 存放庫](https://github.com/elmahio/Elmah.Io.Extensions.Logging))</span><span class="sxs-lookup"><span data-stu-id="55125-204">[elmah.io](https://elmah.io) ([GitHub repo](https://github.com/elmahio/Elmah.Io.Extensions.Logging))</span></span>
- <span data-ttu-id="55125-205">[Gelf](https://docs.graylog.org/en/2.3/pages/gelf.html) ([GitHub 存放庫](https://github.com/mattwcole/gelf-extensions-logging))</span><span class="sxs-lookup"><span data-stu-id="55125-205">[Gelf](https://docs.graylog.org/en/2.3/pages/gelf.html) ([GitHub repo](https://github.com/mattwcole/gelf-extensions-logging))</span></span>
- <span data-ttu-id="55125-206">[JSNLog](https://jsnlog.com) ([GitHub 存放庫](https://github.com/mperdeck/jsnlog))</span><span class="sxs-lookup"><span data-stu-id="55125-206">[JSNLog](https://jsnlog.com) ([GitHub repo](https://github.com/mperdeck/jsnlog))</span></span>
- <span data-ttu-id="55125-207">[KissLog.net](https://kisslog.net) ([GitHub 存放庫](https://github.com/catalingavan/KissLog-net))</span><span class="sxs-lookup"><span data-stu-id="55125-207">[KissLog.net](https://kisslog.net) ([GitHub repo](https://github.com/catalingavan/KissLog-net))</span></span>
- <span data-ttu-id="55125-208">[Log4Net](https://logging.apache.org/log4net) ([GitHub](https://github.com/apache/logging-log4net) 存放庫) </span><span class="sxs-lookup"><span data-stu-id="55125-208">[Log4Net](https://logging.apache.org/log4net) ([GitHub repo](https://github.com/apache/logging-log4net))</span></span>
- <span data-ttu-id="55125-209">[Loggr](https://loggr.net) ([GitHub 存放庫](https://github.com/imobile3/Loggr.Extensions.Logging))</span><span class="sxs-lookup"><span data-stu-id="55125-209">[Loggr](https://loggr.net) ([GitHub repo](https://github.com/imobile3/Loggr.Extensions.Logging))</span></span>
- <span data-ttu-id="55125-210">[NLog](https://nlog-project.org) ([GitHub 存放庫](https://github.com/NLog/NLog.Extensions.Logging))</span><span class="sxs-lookup"><span data-stu-id="55125-210">[NLog](https://nlog-project.org) ([GitHub repo](https://github.com/NLog/NLog.Extensions.Logging))</span></span>
- <span data-ttu-id="55125-211">[Sentry](https://sentry.io/welcome) ([GitHub 存放庫](https://github.com/getsentry/sentry-dotnet))</span><span class="sxs-lookup"><span data-stu-id="55125-211">[Sentry](https://sentry.io/welcome) ([GitHub repo](https://github.com/getsentry/sentry-dotnet))</span></span>
- <span data-ttu-id="55125-212">[Serilog](https://serilog.net) ([GitHub 存放庫](https://github.com/serilog/serilog-sinks-console))</span><span class="sxs-lookup"><span data-stu-id="55125-212">[Serilog](https://serilog.net) ([GitHub repo](https://github.com/serilog/serilog-sinks-console))</span></span>
- <span data-ttu-id="55125-213">[Stackdriver](https://cloud.google.com/dotnet/docs/stackdriver#logging) ([GitHub](https://github.com/googleapis/google-cloud-dotnet) 存放庫) </span><span class="sxs-lookup"><span data-stu-id="55125-213">[Stackdriver](https://cloud.google.com/dotnet/docs/stackdriver#logging) ([GitHub repo](https://github.com/googleapis/google-cloud-dotnet))</span></span>

<span data-ttu-id="55125-214">某些協力廠商架構可以執行[語意記錄 (也稱為結構化記錄)](https://softwareengineering.stackexchange.com/questions/312197/benefits-of-structured-logging-vs-basic-logging) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="55125-214">Some third-party frameworks can perform [semantic logging, also known as structured logging](https://softwareengineering.stackexchange.com/questions/312197/benefits-of-structured-logging-vs-basic-logging).</span></span>

<span data-ttu-id="55125-215">使用協力廠商架構類似於使用內建的提供者之一：</span><span class="sxs-lookup"><span data-stu-id="55125-215">Using a third-party framework is similar to using one of the built-in providers:</span></span>

1. <span data-ttu-id="55125-216">將 NuGet 套件新增至專案。</span><span class="sxs-lookup"><span data-stu-id="55125-216">Add a NuGet package to your project.</span></span>
1. <span data-ttu-id="55125-217">呼叫 `ILoggerFactory` `ILoggingBuilder` 記錄架構所提供的或擴充方法。</span><span class="sxs-lookup"><span data-stu-id="55125-217">Call an `ILoggerFactory` or `ILoggingBuilder` extension method provided by the logging framework.</span></span>

<span data-ttu-id="55125-218">如需詳細資訊，請參閱每個提供者的文件。</span><span class="sxs-lookup"><span data-stu-id="55125-218">For more information, see each provider's documentation.</span></span> <span data-ttu-id="55125-219">Microsoft 不支援第三方記錄提供者。</span><span class="sxs-lookup"><span data-stu-id="55125-219">Third-party logging providers aren't supported by Microsoft.</span></span>

## <a name="see-also"></a><span data-ttu-id="55125-220">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55125-220">See also</span></span>

- <span data-ttu-id="55125-221">[在 .net 中記錄](logging.md)。</span><span class="sxs-lookup"><span data-stu-id="55125-221">[Logging in .NET](logging.md).</span></span>
- <span data-ttu-id="55125-222">[在 .net 中執行自訂記錄提供者](custom-logging-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="55125-222">[Implement a custom logging provider in .NET](custom-logging-provider.md).</span></span>
- <span data-ttu-id="55125-223">[.Net 中的高效能記錄](high-performance-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="55125-223">[High-performance logging in .NET](high-performance-logging.md).</span></span>
