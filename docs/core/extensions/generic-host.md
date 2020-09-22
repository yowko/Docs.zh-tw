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
# <a name="net-generic-host"></a>.NET 泛型主機

背景工作服務範本會建立 .NET 泛型主機 <xref:Microsoft.Extensions.Hosting.HostBuilder> 。 泛型主機可以與其他類型的 .NET 應用程式搭配使用，例如主控台應用程式。

「主機」** 是封裝所有應用程式資源的物件，例如：

- 相依性插入 (DI)
- 記錄
- 設定
- `IHostedService` 實作

當主機啟動時，它會呼叫 <xref:Microsoft.Extensions.Hosting.IHostedService.StartAsync%2A?displayProperty=nameWithType> <xref:Microsoft.Extensions.Hosting.IHostedService> 服務容器的託管服務集合中註冊的每個執行。 在背景工作服務應用程式中， `IHostedService` 包含實例的所有 <xref:Microsoft.Extensions.Hosting.BackgroundService> 實例都會 <xref:Microsoft.Extensions.Hosting.BackgroundService.ExecuteAsync%2A?displayProperty=nameWithType> 呼叫其方法。

在單一物件中包含所有應用程式相互依存資源的主要理由便是生命週期管理：控制應用程式的啟動及順利關機。 這可透過 Microsoft 擴充功能來達成 [。裝載](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) NuGet 套件。

## <a name="set-up-a-host"></a>設定主機

主機通常由 `Program` 類別的程式碼來設定、建置並執行。 `Main` 方法：

- 呼叫 <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder> 方法來建立及設定建立器物件。
- 呼叫 <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> 以建立 <xref:Microsoft.Extensions.Hosting.IHost> 實例。
- <xref:Microsoft.Extensions.Hosting.HostingAbstractionsHostExtensions.Run%2A> <xref:Microsoft.Extensions.Hosting.HostingAbstractionsHostExtensions.RunAsync%2A> 在主機物件上呼叫或方法。

.NET 背景工作服務範本會產生下列程式碼來建立泛型主機：

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

## <a name="default-builder-settings"></a>預設建立器設定

<xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder%2A> 方法：

- 設定 <xref:System.IO.Directory.GetCurrentDirectory> 所傳回路徑的內容根目錄。
- 從下列項目載入[主機組態](#host-configuration)：
  - 前面加上的環境變數 `DOTNET_` 。
  - 命令列引數。
- 從下列項目載入應用程式組態：
  - *appsettings.js開啟*。
  - *appsettings.{Environment}.json*
  - 應用程式在  環境中執行時的`Development`祕密管理員。
  - 環境變數。
  - 命令列引數。
- 新增下列記錄提供者：
  - 主控台
  - 偵錯
  - EventSource
  - EventLog (僅當在 Windows 上執行時)
- 當環境為時，可啟用範圍驗證和相依性 [驗證](xref:Microsoft.Extensions.DependencyInjection.ServiceProviderOptions.ValidateOnBuild) `Development` 。

`ConfigureServices`方法會公開將服務加入至實例的功能 <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection?displayProperty=nameWithType> 。 之後，這些服務可以從相依性插入中取得。

## <a name="framework-provided-services"></a>架構提供的服務

下列服務會自動註冊：

- [IHostApplicationLifetime](#ihostapplicationlifetime)
- [IHostLifetime](#ihostlifetime)
- [IHostEnvironment](#ihostenvironment)

## <a name="ihostapplicationlifetime"></a>IHostApplicationLifetime

將 <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime> 服務插入任何類別，以處理啟動後和正常關機工作。 介面上的三個屬性是用於註冊應用程式啟動和應用程式關閉事件處理程序方法的取消語彙基元。 介面也包括 <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime.StopApplication> 方法。

下列範例是 `IHostedService` 註冊事件的實作為 `IHostApplicationLifetime` ：

:::code language="csharp" source="snippets/configuration/app-lifetime/ExampleHostedService.cs" highlight="18-20":::

您可以修改背景工作服務範本以新增 `ExampleHostedService` 實作為：

:::code language="csharp" source="snippets/configuration/app-lifetime/Program.cs" range="1-16,36" highlight="15":::

應用程式會寫入下列範例輸出：

:::code language="csharp" source="snippets/configuration/app-lifetime/Program.cs" range="17-35":::

## <a name="ihostlifetime"></a>IHostLifetime

<xref:Microsoft.Extensions.Hosting.IHostLifetime> 實作會控制主機啟動及停止的時機。 會使用最後一個註冊的實作。

`Microsoft.Extensions.Hosting.Internal.ConsoleLifetime` 是預設的 `IHostLifetime` 實作。 `ConsoleLifetime`:

- 接聽<kbd>Ctrl</kbd> + <kbd>C</kbd>、 [SIGINT](https://en.wikipedia.org/wiki/Signal_(IPC)#SIGINT)或[SIGTERM](https://en.wikipedia.org/wiki/Signal_(IPC)#SIGTERM) ，並呼叫 <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime.StopApplication%2A> 以啟動關機程式。
- 解除封鎖擴充功能 `RunAsync` ，例如和 `WaitForShutdownAsync` 。

## <a name="ihostenvironment"></a>IHostEnvironment

將服務插入至 <xref:Microsoft.Extensions.Hosting.IHostEnvironment> 類別，以取得下列設定的相關資訊：

- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.ApplicationName?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.ContentRootFileProvider?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.ContentRootPath?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.EnvironmentName?displayProperty=nameWithType>

## <a name="host-configuration"></a>主機組態

主機組態用於 <xref:Microsoft.Extensions.Hosting.IHostEnvironment> 實作的屬性。

主機組態位於 <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureAppConfiguration%2A> 內的 [HostBuilderContext.Configuration](xref:Microsoft.Extensions.Hosting.HostBuilderContext.Configuration)。 在 `ConfigureAppConfiguration` 之後，應用程式組態會取代 `HostBuilderContext.Configuration`。

若要新增主機組態，請呼叫 `IHostBuilder` 上的 <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureHostConfiguration%2A>。 `ConfigureHostConfiguration` 可以多次呼叫，其結果是累加的。 主機會使用指定索引鍵上最後設定值的任何選項。

下列範例會建立主機組態：

:::code language="csharp" source="snippets/configuration/console-host/Program.cs" highlight="13-19":::

## <a name="app-configuration"></a>應用程式設定

應用程式組態的建立方式是在 `IHostBuilder` 上呼叫 <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureAppConfiguration%2A>。 `ConfigureAppConfiguration` 可以多次呼叫，其結果是累加的。 應用程式會使用指定索引鍵上最後設定值的任何選項。

由 `ConfigureAppConfiguration` 建立的組態位於 [HostBuilderContext.Configuration](xref:Microsoft.Extensions.Hosting.HostBuilderContext.Configuration%2A)，可用於後續作業並用作 DI 中的服務。 主機組態也會新增至應用程式組態。

如需詳細資訊，請參閱 [.net 中](configuration.md)的設定。

## <a name="see-also"></a>另請參閱

- [.NET 中的設定](configuration.md)
- [ASP.NET Core Web 主機](/aspnet/core/fundamentals/host/web-host)
