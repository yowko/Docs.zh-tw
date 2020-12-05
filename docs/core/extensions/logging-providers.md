---
title: .NET 中的記錄提供者
description: 瞭解如何在 .NET 應用程式中使用記錄提供者 API。
author: IEvangelist
ms.author: dapine
ms.date: 12/04/2020
ms.openlocfilehash: fdec9018e58c6038b5589c01e775bbb5f10b6b10
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740087"
---
# <a name="logging-providers-in-net"></a>.NET 中的記錄提供者

除了提供者之外，記錄提供者會保存記錄，只會將 `Console` 記錄顯示為標準輸出。 例如，Azure 應用程式 Insights 提供者會將記錄儲存在 Azure 應用程式深入解析中。 可以啟用多個提供者。

預設的 .NET 背景工作應用程式範本：

- 使用 [一般主機](generic-host.md)。
- 呼叫 <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder%2A> ，這會新增下列記錄提供者：
  - [主控台](#console)
  - [偵錯](#debug)
  - [EventSource](#event-source)
  - [EventLog](#windows-eventlog)：僅限 Windows

:::code language="csharp" source="snippets/configuration/console/Program.cs" highlight="18":::

上述程式碼顯示 `Program` 使用 .net 背景工作應用程式範本所建立的類別。 接下來的幾節會根據使用一般主機的 .NET 背景工作應用程式範本提供範例。

若要覆寫所加入的預設記錄提供者集合 `Host.CreateDefaultBuilder` ，請呼叫 `ClearProviders` 並加入您想要的記錄提供者。 例如，下列程式碼：

- 從產生器 <xref:Microsoft.Extensions.Logging.LoggingBuilderExtensions.ClearProviders%2A> 中移除所有實例的呼叫 <xref:Microsoft.Extensions.Logging.ILoggerProvider> 。
- 新增 [主控台](#console) 記錄提供者。

```csharp
static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureLogging(logging =>
        {
            logging.ClearProviders();
            logging.AddConsole();
        });
```

如需其他提供者，請參閱：

- [內建的記錄提供者](#built-in-logging-providers)。
- [協力廠商記錄提供者](#third-party-logging-providers)。

## <a name="configure-a-service-that-depends-on-ilogger"></a>設定相依于 ILogger 的服務

若要設定相依的服務 `ILogger<T>` ，請使用函式插入或提供 factory 方法。 只有在沒有其他選項時，才建議使用 Factory 方法。 例如，假設有一個服務需要 `ILogger<T>` DI 提供的實例：

```csharp
.ConfigureServices(services =>
    services.AddSingleton<IExampleService>(container =>
        new DefaultExampleService
        {
            Logger = container.GetRequiredService<ILogger<IExampleService>>()
        }));
```

上述程式碼是 [Func<IServiceProvider，IExampleService>](/dotnet/api/system.func-2) ，它會在 DI 容器第一次需要建立的實例時執行 `IExampleService` 。 您可以用此方式存取任何已註冊的服務。

## <a name="built-in-logging-providers"></a>內建記錄提供者

Microsoft 擴充功能包含下列記錄提供者，作為執行時間程式庫的一部分：

- [主控台](#console)
- [偵錯](#debug)
- [EventSource](#event-source)
- [EventLog](#windows-eventlog)

下列記錄提供者是由 Microsoft 所提供，但不是執行時間程式庫的一部分。 它們必須安裝為其他 NuGet 套件。

- [AzureAppServicesFile 和 AzureAppServicesBlob](#azure-app-service)
- [ApplicationInsights](#azure-application-insights)

### <a name="console"></a>主控台

`Console`提供者會將輸出記錄到主控台。

### <a name="debug"></a>偵錯

`Debug`提供者會使用 system.servicemodel 類別來寫入[System.Diagnostics.Debug](/dotnet/api/system.diagnostics.debug)記錄檔輸出。 要 `System.Diagnostics.Debug.WriteLine` 寫入 `Debug` 提供者的呼叫。

在 Linux 上， `Debug` 提供者記錄檔位置是散發相依的，可能是下列其中一項：

- */var/log/message*
- */var/log/syslog*

### <a name="event-source"></a>事件來源

`EventSource`提供者會以名稱寫入跨平臺事件來源 `Microsoft-Extensions-Logging` 。 在 Windows 上，提供者會使用 [ETW](/windows/win32/etw/event-tracing-portal)。

#### <a name="dotnet-trace-tooling"></a>dotnet 追蹤工具

[Dotnet 追蹤](../diagnostics/dotnet-trace.md)工具是一種跨平臺 CLI 全域工具，可讓您收集正在執行之進程的 .net Core 追蹤。 此工具會 <xref:Microsoft.Extensions.Logging.EventSource> 使用來收集提供者資料 <xref:Microsoft.Extensions.Logging.EventSource.LoggingEventSource> 。

如需安裝指示，請參閱 [dotnet](../diagnostics/dotnet-trace.md) 。 如需使用的診斷教學課程 `dotnet-trace` ，請參閱 [.net Core 中的高 CPU 使用率的調試](../diagnostics/debug-highcpu.md)程式。

### <a name="windows-eventlog"></a>Windows EventLog

此 `EventLog` 提供者會將記錄輸出傳送至 Windows 事件記錄檔。 不同于其他提供者， `EventLog` 提供者不 **not** 會繼承預設的非提供者設定。 如果 `EventLog` 未指定記錄檔設定，則預設為 `LogLevel.Warning` 。

若要記錄低於 <xref:Microsoft.Extensions.Logging.LogLevel.Warning?displayProperty=nameWithType> 的事件，請明確設定記錄層級。 下列範例會將事件記錄檔的預設記錄層級設定為 <xref:Microsoft.Extensions.Logging.LogLevel.Information?displayProperty=nameWithType> ：

```json
"Logging": {
  "EventLog": {
    "LogLevel": {
      "Default": "Information"
    }
  }
}
```

[AddEventLog](xref:Microsoft.Extensions.Logging.EventLoggerFactoryExtensions) 多載可傳入 <xref:Microsoft.Extensions.Logging.EventLog.EventLogSettings> 。 如果 `null` 未指定，則會使用下列預設設定：

- `LogName`：「應用程式」
- `SourceName`：「.NET 執行時間」
- `MachineName`：使用本機電腦名稱稱。

下列程式碼會將的 `SourceName` 預設值從變更 `".NET Runtime"` 為 `CustomLogs` ：

```csharp
public class Program
{
    static async Task Main(string[] args)
    {
        using IHost host = CreateHostBuilder(args).Build();

        // Application code should start here.

        await host.RunAsync();
    }

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging =>
                logging.AddEventLog(configuration =>
                    configuration.SourceName = "CustomLogs"));
}
```

### <a name="azure-app-service"></a>Azure App Service

[Microsoft.Extensions.Logging.AzureAppServices](https://www.nuget.org/packages/Microsoft.Extensions.Logging.AzureAppServices) 提供者套件會將記錄寫入至 Azure App Service 應用程式檔案系統中的文字檔，並寫入至 Azure 儲存體帳戶中的 [Blob 儲存體](/azure/storage/blobs/storage-quickstart-blobs-dotnet#what-is-blob-storage)。

提供者套件未包含在執行時間程式庫中。 若要使用提供者，請將提供者套件新增至專案。

如果要進行提供者設定，請使用 <xref:Microsoft.Extensions.Logging.AzureAppServices.AzureFileLoggerOptions> 和 <xref:Microsoft.Extensions.Logging.AzureAppServices.AzureBlobLoggerOptions>，如以下範例中所示：

```csharp
class Program
{
    static async Task Main(string[] args)
    {
        using IHost host = CreateHostBuilder(args).Build();

        // Application code should start here.

        await host.RunAsync();
    }

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging =>
                logging.AddAzureWebAppDiagnostics())
            .ConfigureServices(services =>
                services.Configure<AzureFileLoggerOptions>(options =>
                {
                    options.FileName = "azure-diagnostics-";
                    options.FileSizeLimit = 50 _ 1024;
                    options.RetainedFileCountLimit = 5;
                })
                .Configure<AzureBlobLoggerOptions>(options =>
                {
                    options.BlobName = "log.txt";
                }));
}
```

當部署到 Azure App Service 時，應用程式會使用 Azure 入口網站之 **App Service** 頁面的 [ [App Service 記錄](/azure/app-service/web-sites-enable-diagnostic-log/#enable-application-logging-windows)] 區段中的設定。 當下列設定更新時，變更會立即生效，而不需要重新啟動或重新部署應用程式。

- **應用程式記錄 (檔案系統)**
- **應用程式記錄 (Blob)**

記錄檔的預設位置為 *D:\\home\\LogFiles\\Application* 資料夾，而預設檔案名稱為 *diagnostics-yyyymmdd.txt*。 預設檔案大小限制為 10 MB，而預設保留的檔案數目上限為 2。 預設 Blob 名稱為 *{app-name}{timestamp}/yyyy/mm/dd/hh/{guid}-applicationLog.txt*。

只有當專案在 Azure 環境中執行時，此提供者才會記錄。

#### <a name="azure-log-streaming"></a>Azure 記錄資料流

Azure 記錄串流支援即時查看記錄活動：

- 應用程式伺服器
- 網頁伺服器
- 失敗的要求追蹤

若要設定 Azure 記錄資料流：

- 從應用程式的入口網站頁面流覽至 [ **App Service 記錄** ] 頁面。
- 將 [應用程式記錄 (檔案系統)] 設定為 [開啟]。
- 選擇記錄 [層級]。 此設定僅適用于 Azure 記錄串流。

流覽至 [ **記錄資料流程** ] 頁面以查看記錄。 記錄的訊息會與介面一起記錄 `ILogger` 。

### <a name="azure-application-insights"></a>Azure Application Insights

[ApplicationInsights](https://www.nuget.org/packages/Microsoft.Extensions.Logging.ApplicationInsights)提供者套件會將記錄寫入[Azure 應用程式見解](/azure/azure-monitor/app/cloudservices)。 Application Insights 是可監視 Web 應用程式的服務，並提供可用來查詢及分析遙測資料的工具。 如果您使用此提供者，就可以使用 Application Insights 工具來查詢及分析記錄。

如需詳細資訊，請參閱下列資源：

- [Application Insights 概觀](/azure/application-insights/app-insights-overview)
- [適用於 .NET Core ILogger 記錄的 ApplicationInsightsLoggerProvider](/azure/azure-monitor/app/ilogger)：如果您想要實作記錄提供者，而不需要 Application Insights 遙測的其餘部分，請從這裡開始。
- [Application Insights logging adapters](/azure/azure-monitor/app/asp-net-trace-logs) (Application Insights 記錄配接器)。
- [安裝、設定及初始化 Application Insights SDK](/learn/modules/instrument-web-app-code-with-application-insights)：Microsoft Learn 網站上的互動式教學課程。

## <a name="third-party-logging-providers"></a>協力廠商記錄提供者

以下是一些可搭配各種 .NET 工作負載使用的協力廠商記錄架構：

- [elmah.io](https://elmah.io) ([GitHub 存放庫](https://github.com/elmahio/Elmah.Io.Extensions.Logging))
- [Gelf](https://docs.graylog.org/en/2.3/pages/gelf.html) ([GitHub 存放庫](https://github.com/mattwcole/gelf-extensions-logging))
- [JSNLog](http://jsnlog.com) ([GitHub 存放庫](https://github.com/mperdeck/jsnlog))
- [KissLog.net](https://kisslog.net) ([GitHub 存放庫](https://github.com/catalingavan/KissLog-net))
- [Log4Net](https://logging.apache.org/log4net) ([GitHub](https://github.com/apache/logging-log4net) 存放庫) 
- [Loggr](https://loggr.net) ([GitHub 存放庫](https://github.com/imobile3/Loggr.Extensions.Logging))
- [NLog](https://nlog-project.org) ([GitHub 存放庫](https://github.com/NLog/NLog.Extensions.Logging))
- [Sentry](https://sentry.io/welcome) ([GitHub 存放庫](https://github.com/getsentry/sentry-dotnet))
- [Serilog](https://serilog.net) ([GitHub 存放庫](https://github.com/serilog/serilog-sinks-console))
- [Stackdriver](https://cloud.google.com/dotnet/docs/stackdriver#logging) ([GitHub](https://github.com/googleapis/google-cloud-dotnet) 存放庫) 

某些協力廠商架構可以執行[語意記錄 (也稱為結構化記錄)](https://softwareengineering.stackexchange.com/questions/312197/benefits-of-structured-logging-vs-basic-logging) \(英文\)。

使用協力廠商架構類似於使用內建的提供者之一：

1. 將 NuGet 套件新增至專案。
1. 呼叫 `ILoggerFactory` `ILoggingBuilder` 記錄架構所提供的或擴充方法。

如需詳細資訊，請參閱每個提供者的文件。 Microsoft 不支援第三方記錄提供者。

## <a name="see-also"></a>另請參閱

- [在 .net 中記錄](logging.md)。
- [在 .net 中執行自訂記錄提供者](custom-logging-provider.md)。
- [.Net 中的高效能記錄](high-performance-logging.md)。
