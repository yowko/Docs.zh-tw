---
title: .NET 中的記錄
author: IEvangelist
description: 了解如何使用由 Microsoft.Extensions.Logging NuGet 套件提供的記錄架構。
ms.author: dapine
ms.date: 09/30/2020
ms.openlocfilehash: d409d78698e4e85eaf9f2894ee1ed00cea0c0583
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888555"
---
# <a name="logging-in-net"></a>.NET 中的記錄

.NET 支援可搭配各種內建和協力廠商記錄提供者的記錄 API。 此文章說明如何搭配內建提供者使用 API。 本文中顯示的大部分程式碼範例適用于任何使用 [一般主機](generic-host.md)的 .net 應用程式。 針對未使用一般主機的應用程式，請參閱 [非主機主控台應用程式](#non-host-console-app)。

## <a name="create-logs"></a>建立記錄

若要建立記錄，請使用相依性 <xref:Microsoft.Extensions.Logging.ILogger%601> [插入 (DI) ](dependency-injection.md)的物件。

下列範例將：

- 建立記錄器， `ILogger<Worker>` 這會使用類型完整名稱的記錄 *類別* `Worker` 。 記錄「類別」是與每個記錄關聯的字串。
- 呼叫 <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogInformation%2A> 層級的記錄 `Information` 。 記錄「層級」  指出已記錄事件的嚴重性。

:::code language="csharp" source="snippets/configuration/worker-service/Worker.cs" range="9-24" highlight="12":::

此文章稍後將詳細說明[層級](#log-level)與[類別](#log-category)。

## <a name="configure-logging"></a>設定記錄

記錄設定通常是由 appsettings 的 `Logging` 區段所 *appsettings* 提供。 `{Environment}`*. json* 檔案。 下列 *appsettings.Development.json* file 是由 .net Worker 服務範本產生：

:::code language="json" source="snippets/configuration/worker-service/appsettings.Development.json":::

在上述 JSON 中：

- `"Default"` `"Microsoft"` 已指定、和 `"Microsoft.Hosting.Lifetime"` 分類。
- `"Microsoft"`類別目錄會套用至所有以開頭的類別 `"Microsoft"` 。
- `"Microsoft"`記錄層級和更新版本的類別記錄 `Warning` 。
- `"Microsoft.Hosting.Lifetime"`類別目錄比類別更明確 `"Microsoft"` ，因此 `"Microsoft.Hosting.Lifetime"` 類別記錄檔層級的「資訊」和更高的記錄。
- 未指定特定的記錄提供者，因此會 `LogLevel` 套用至所有啟用的記錄提供者，除了 [Windows EventLog](logging-providers.md#windows-eventlog)之外。

`Logging`屬性可以具有 <xref:Microsoft.Extensions.Logging.LogLevel> 和記錄提供者屬性。 會 `LogLevel` 指定所選類別的最小 [層級](#log-level) 來記錄。 在先前的 JSON 中 `Information` ， `Warning` 會指定記錄層級。 `LogLevel` 指出記錄檔的嚴重性，範圍從0到6：

`Trace` = 0、 `Debug` = 1、 `Information` = 2、 `Warning` = 3、 `Error` = 4、 `Critical` = 5 和 `None` = 6。

當 `LogLevel` 指定時，會在指定層級及更高的訊息上啟用記錄。 在上述 JSON 中， `Default` 會針對和更新版本記錄類別 `Information` 。 例如， `Information` `Warning` 會記錄、、 `Error` 和 `Critical` 訊息。 如果未 `LogLevel` 指定，則記錄會預設為 `Information` 層級。 如需詳細資訊，請參閱 [記錄層級](#log-level)。

提供者屬性可以指定 `LogLevel` 屬性。 `LogLevel` 在提供者下，指定該提供者的記錄層級，並覆寫非提供者記錄檔設定。 請考慮下列 *appsettings.json* file：

:::code language="json" source="snippets/configuration/worker-service/appsettings.Staging.json":::

覆寫設定中的設定 `Logging.{ProviderName}.LogLevel` `Logging.LogLevel` 。 在上述 JSON 中， `Debug` 提供者的預設記錄層級設定為 `Information` ：

`Logging:Debug:LogLevel:Default:Information`

上述設定會指定 `Information` 每個類別目錄的記錄層級， `Logging:Debug:` 但除外 `Microsoft.Hosting` 。 列出特定的分類時，特定類別會覆寫預設分類。 在上述 JSON 中， `Logging:Debug:LogLevel` 類別 `"Microsoft.Hosting"` 和覆 `"Default"` 寫中的設定 `Logging:LogLevel`

您可以針對下列任一項指定最小記錄層級：

- 特定提供者：例如， `Logging:EventSource:LogLevel:Default:Information`
- 特定類別：例如， `Logging:LogLevel:Microsoft:Warning`
- 所有提供者和所有類別： `Logging:LogLevel:Default:Warning`

低於最低層級的所有記錄都是 * **而不** 是 _：

- 傳遞給提供者。
- 記錄或顯示。

若要隱藏所有記錄檔，請指定 [LogLevel。無](xref:Microsoft.Extensions.Logging.LogLevel)。 `LogLevel.None` 的值為6，高於 `LogLevel.Critical` (5) 。

如果提供者支援 [記錄範圍](#log-scopes)， `IncludeScopes` 就會指出是否已啟用。 如需詳細資訊，請參閱 [記錄範圍](#log-scopes)

下列 _appsettings.json * file 包含所有內建提供者的設定：

:::code language="json" source="snippets/configuration/worker-service/appsettings.Production.json":::

在上述範例中：

- 類別和層級不是建議的值。 提供的範例會顯示所有預設的提供者。
- 覆寫設定中的設定 `Logging.{ProviderName}.LogLevel` `Logging.LogLevel` 。 例如，中的層級會 `Debug.LogLevel.Default` 覆寫中的層級 `LogLevel.Default` 。
- 使用每個提供者的 *別名* 。 每個提供者都會定義「別名」  ，可在設定中用來取代完整類型名稱。 內建提供者的別名如下：
  - 主控台
  - 偵錯
  - EventSource
  - EventLog
  - AzureAppServicesFile
  - AzureAppServicesBlob
  - ApplicationInsights

### <a name="set-log-level-by-command-line-environment-variables-and-other-configuration"></a>依命令列、環境變數和其他設定來設定記錄層級

記錄層級可由任何設定 [提供者](configuration-providers.md)設定。

下列命令：

- 將環境金鑰設定 `Logging:LogLevel:Microsoft` 為 `Information` Windows 上的值。
- 使用以 .NET Worker 服務範本建立的應用程式時，測試設定。 `dotnet run`使用之後，必須在專案目錄中執行此命令 `set` 。

```cmd
set Logging__LogLevel__Microsoft=Information
dotnet run
```

先前的環境設定：

- 只會在從其設定的命令視窗啟動的進程中設定。
- 使用 Visual Studio 啟動的應用程式不會讀取。

下列 [setx](/windows-server/administration/windows-commands/setx) 命令也會在 Windows 上設定環境機碼和值。 與不同 `set` 的 `setx` 是，設定會持續保存。 `/M`參數會在系統內容中設定變數。 如果 `/M` 未使用，則會設定使用者環境變數。

```cmd
setx Logging__LogLevel__Microsoft=Information /M
```

在 [Azure App Service](https://azure.microsoft.com/services/app-service/)上，選取 [ **設定 > 設定** ] 頁面上的 [ **新增應用程式設定** ]。 Azure App Service 的應用程式設定如下：

- 靜態加密，並透過加密通道傳輸。
- 公開為環境變數。

如需使用環境變數來設定 .NET 設定值的詳細資訊，請參閱 [環境變數](configuration-providers.md#environment-variable-configuration-provider)。

## <a name="how-filtering-rules-are-applied"></a>如何套用篩選規則

建立 <xref:Microsoft.Extensions.Logging.ILogger%601> 物件時，<xref:Microsoft.Extensions.Logging.ILoggerFactory> 物件會針對每個提供者選取一個規則來套用到該記錄器。 由 `ILogger` 執行個體寫入的所有訊息都會根據選取的規則進行篩選。 您可以從可用的規則中選取每個提供者和類別配對的最特定規則。

當建立指定類別的 `ILogger` 時，系統會針對每個提供者使用下列演算法：

- 選取所有符合提供者或其別名的規則。 如果找不到符合的項目，請選取所有規則搭配空白提供者。
- 從上一個步驟的結果中，選取具有最長相符類別前置字元的規則。 如果找不到符合的項目，請選取未指定類別的所有規則。
- 如果選取多個規則，請使用 **最後** 一個。
- 如果未選取任何規則，請使用 <xref:Microsoft.Extensions.Logging.LoggingBuilderExtensions.SetMinimumLevel(Microsoft.Extensions.Logging.ILoggingBuilder,Microsoft.Extensions.Logging.LogLevel)?displayProperty=nameWithType> 來指定最小記錄層級。

## <a name="log-category"></a>記錄分類

`ILogger`建立物件時，會指定 *類別* 。 該類別會包含在每個由該 `ILogger` 執行個體所產生的記錄訊息中。 類別目錄字串是任意的，但慣例是使用類別名稱。 例如，在服務定義類似下列物件的應用程式中，類別目錄可能是 `"Example.DefaultService"` ：

```csharp
namespace Example
{
    public class DefaultService : IService
    {
        private readonly ILogger<DefaultService> _logger;

        public DefaultService(ILogger<DefaultService> logger) =>
            _logger = logger;

        // ...
    }
}
```

若要明確指定類別，請呼叫 <xref:Microsoft.Extensions.Logging.LoggerFactory.CreateLogger%2A?displayProperty=nameWithType>：

```csharp
namespace Example
{
    public class DefaultService : IService
    {
        private readonly ILogger _logger;

        public DefaultService(ILoggerFactory loggerFactory) =>
            _logger = logger.CreateLogger("CustomCategory");

        // ...
    }
}
```

`CreateLogger`使用固定名稱呼叫會很有用，因為在多個方法中使用時，可以依類別來組織事件。

`ILogger<T>` 相當於使用 `T`的完整類型名稱來呼叫 `CreateLogger`。

## <a name="log-level"></a>記錄層級

下表列出這些 <xref:Microsoft.Extensions.Logging.LogLevel> 值、便利的 `Log{LogLevel}` 擴充方法，以及建議的使用方式：

| LogLevel | 值 | 方法 | 描述 |
|--|--|--|--|
| [追蹤](xref:Microsoft.Extensions.Logging.LogLevel) | 0 | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogTrace%2A> | 包含最詳細的訊息。 這些訊息可能包含敏感性應用程式資料。 這些訊息預設為停用，且 **不** 應在生產環境中啟用 *。 |
| [偵錯](xref:Microsoft.Extensions.Logging.LogLevel) | 1 | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogDebug%2A> | 用於偵錯工具和開發。 在生產環境中，請謹慎使用，因為這是大量的磁片區。 |
| [資訊](xref:Microsoft.Extensions.Logging.LogLevel) | 2 | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogInformation%2A> | 追蹤應用程式的一般流程。 可能具有長期值。 |
| [警告](xref:Microsoft.Extensions.Logging.LogLevel) | 3 | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogWarning%2A> | 針對異常或非預期的事件。 通常會包含不會導致應用程式失敗的錯誤或狀況。 |
| [錯誤](xref:Microsoft.Extensions.Logging.LogLevel) | 4 | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogError%2A> | 發生無法處理的錯誤和例外狀況。 這些訊息表示目前的作業或要求失敗，而不是整個應用程式的失敗。 |
| [重大](xref:Microsoft.Extensions.Logging.LogLevel) | 5 | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogCritical%2A> | 發生需要立即注意的失敗。 範例：資料遺失情況、磁碟空間不足。 |
| [無](xref:Microsoft.Extensions.Logging.LogLevel) | 6 |  | 指定不應寫入任何訊息。 |

在上表中， `LogLevel` 是從最低到最高的嚴重性列出。

[Log](xref:Microsoft.Extensions.Logging.LoggerExtensions)方法的第一個參數， <xref:Microsoft.Extensions.Logging.LogLevel> 表示記錄檔的嚴重性。 `Log(LogLevel, ...)`大部分的開發人員都呼叫[Log {LogLevel}](xref:Microsoft.Extensions.Logging.LoggerExtensions)擴充方法，而不是呼叫。 `Log{LogLevel}`擴充方法會[通話記錄方法並指定 LogLevel](https://github.com/dotnet/extensions/blob/release/3.1/src/Logging/Logging.Abstractions/src/LoggerExtensions.cs)。 例如，下列兩個記錄呼叫在功能上相當，並且會產生相同的記錄：

```csharp
public void LogDetails()
{
    var logMessage = "Details for log.";

    _logger.Log(LogLevel.Information, AppLogEvents.Details, logMessage);
    _logger.LogInformation(AppLogEvents.Details, logMessage);
}
```

`AppLogEvents.Details` 是事件識別碼，並以常數值隱含表示 <xref:System.Int32> 。 `AppLogEvents` 類別會公開不同的命名識別碼常數，而且會顯示在 [ [記錄檔事件識別碼](#log-event-id) ] 區段中。

下列程式碼會建立 `Information` 與 `Warning` 記錄：

```csharp
public async Task<T> GetAsync<T>(string id)
{
    _logger.LogInformation(AppLogEvents.Read, "Reading value for {Id}", id);

    var result = await _repository.GetAsync(id);
    if (result is null)
    {
        _logger.LogWarning(AppLogEvents.ReadNotFound, "GetAsync({Id}) not found", id);
    }

    return result;
}
```

在上述程式碼中，第一個 `Log{LogLevel}` 參數 `AppLogEvents.Read` 是 [記錄事件識別碼](#log-event-id)。 第二個參數是訊息範本，其中的預留位置會置入其餘方法參數所提供的引數值。 方法參數將在本文稍後的「 [訊息範本](#log-message-template) 」一節中說明。

設定適當的記錄層級，並呼叫正確的 `Log{LogLevel}` 方法，以控制寫入至特定儲存媒體的記錄輸出量。 例如：

- 在生產環境中：
  - 在 `Trace` 或 `Information` 層級進行記錄會產生大量的詳細記錄訊息。 若要控制成本，而不超過資料儲存限制、記錄 `Trace` 和 `Information` 層級訊息至高容量、低成本的資料存放區。 考慮限制 `Trace` 和 `Information` 特定類別。
  - `Warning`透過 `Critical` 層級進行記錄應該會產生幾個記錄訊息。
    - 成本和儲存空間限制通常不成問題。
    - 少數記錄檔可讓您更靈活地選擇資料存放區。
- 開發中：
  - 設定為 `Warning`。
  - `Trace` `Information` 疑難排解時新增或訊息。 若要限制輸出， `Trace` 請 `Information` 針對 [調查] 下的分類進行設定。

下列 JSON 集合 `Logging:Console:LogLevel:Microsoft:Information` ：

:::code language="json" source="snippets/configuration/worker-service/appsettings.MSFT.json":::

## <a name="log-event-id"></a>記錄事件識別碼

每個記錄檔都可以指定 _event 識別碼 *， <xref:Microsoft.Extensions.Logging.EventId> 是具有 `Id` 和選擇性 `Name` readonly 屬性的結構。 範例原始程式碼會使用 `AppLogEvents` 類別來定義事件識別碼：

```csharp
internal static class AppLogEvents
{
    internal const int Create = 1000;
    internal const int Read = 1001;
    internal const int Update = 1002;
    internal const int Delete = 1003;

    internal const int Details = 3000;
    internal const int Error = 3001;

    internal const int ReadNotFound = 4000;
    internal const int UpdateNotFound = 4001;

    // ...
}
```

事件識別碼會將一組事件關聯。 例如，與從存放庫讀取值相關的所有記錄可能是 `1001` 。

記錄提供者可能會將事件識別碼記錄在識別碼欄位、記錄訊息中，或根本不記錄。 偵錯提供者不會顯示事件識別碼。 主控台提供者會在類別後面以括弧顯示事件識別碼：

```console
info: Example.DefaultService.GetAsync[1001]
      Reading value for a1b2c3
warn: Example.DefaultService.GetAsync[4000]
      GetAsync(a1b2c3) not found
```

某些記錄提供者會將事件識別碼儲存在欄位中，以允許篩選識別碼。

## <a name="log-message-template"></a>記錄訊息範本

每個記錄 API 都會使用訊息範本。 訊息範本可以包含有關提供哪個引數的預留位置。 使用名稱而非數字做為預留位置。 預留位置的順序 (而不是其名稱) 會決定使用哪些參數來提供其值。 在下列程式碼中，訊息範本中的參數名稱不是順序：

```csharp
string p1 = "param1";
string p2 = "param2";
_logger.LogInformation("Parameter values: {p2}, {p1}", p1, p2);
```

上述程式碼會依序建立具有參數值的記錄訊息：

```text
Parameter values: param1, param2
```

這種方法可讓記錄提供者執行 [語義或結構化記錄](https://github.com/NLog/NLog/wiki/How-to-use-structured-logging)。 引數本身會被傳遞到記錄系統，而不只是格式化的訊息範本。 這可讓記錄提供者將參數值儲存為欄位。 請考慮下列記錄器方法：

```csharp
_logger.LogInformation("Getting item {Id} at {RunTime}", id, DateTime.Now);
```

例如，在記錄至 Azure 資料表儲存體時：

- 每個 Azure 資料表實體都可以有 `ID` 和 `RunTime` 屬性。
- 具有屬性的資料表會簡化記錄資料的查詢。 例如，查詢可以尋找特定範圍內的所有記錄 `RunTime` ，而不需要剖析文字訊息的時間。

## <a name="log-exceptions"></a>記錄例外狀況

記錄器方法具有可採用例外狀況參數的多載：

```csharp
public void Test(string id)
{
    try
    {
        if (id == "none")
        {
            throw new Exception("Default Id detected.");
        }
    }
    catch (Exception ex)
    {
        _logger.LogWarning(
            AppLogEvents.Error, ex,
            "Failed to process iteration: {Id}", id)
    }
}
```

例外狀況記錄是提供者特定的。

### <a name="default-log-level"></a>預設記錄層級

如果未設定預設記錄層級，預設的記錄層級值為 `Information` 。

例如，請考慮下列背景工作服務應用程式：

- 使用 .NET 背景工作範本建立。
- *appsettings.json* ，並 *appsettings.Development.js* 已刪除或重新命名。

在上述設定中，流覽至隱私權或首頁會 `Trace` `Debug` `Information` `Microsoft` 在類別目錄名稱中產生許多、和訊息。

下列程式碼會在設定中未設定預設記錄層級時，設定預設的記錄層級：

```csharp
class Program
{
    static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging => logging.SetMinimumLevel(LogLevel.Warning));
}
```

### <a name="filter-function"></a>Filter 函數

針對沒有透過設定或程式碼指派規則的所有提供者和類別，會叫用篩選函數：

```csharp
class Program
{
    static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging =>
                logging.AddFilter((provider, category, logLevel) =>
                {
                    return provider.Contains("ConsoleLoggerProvider")
                        && (category.Contains("Example") || category.Contains("Microsoft"))
                        && logLevel >= LogLevel.Information;
                }));
}
```

當類別包含 `Example` 或 `Microsoft` 且記錄層級為 `Information` 或更高時，上述程式碼會顯示主控台記錄。

## <a name="log-scopes"></a>記錄範圍

 「範圍」  可用來將邏輯作業組成群組。 此分組功能可用來將相同的資料附加到已建立為集合之一部分的每個記錄。 例如，在處理邀交易時建立的每個記錄都可以包括該交易識別碼。

範圍：

- 這是 <xref:System.IDisposable> 方法傳回的型別 <xref:Microsoft.Extensions.Logging.ILogger.BeginScope%2A> 。
- 一直持續到處置為止。

下列提供者支援範圍：

- `Console`
- [AzureAppServicesFile 和 AzureAppServicesBlob](xref:Microsoft.Extensions.Logging.AzureAppServices.BatchingLoggerOptions.IncludeScopes)

透過將記錄器呼叫封裝在 `using` 區塊中以使用範圍：

```csharp
public async Task<T> GetAsync<T>(string id)
{
    T result;

    using (_logger.BeginScope("using block message"))
    {
        _logger.LogInformation(
            AppLogEvents.Read, "Reading value for {Id}", id);

        var result = await _repository.GetAsync(id);
        if (result is null)
        {
            _logger.LogWarning(
                AppLogEvents.ReadNotFound, "GetAsync({Id}) not found", id);
        }
    }

    return result;
}
```

下列 JSON 會啟用主控台提供者的範圍：

:::code language="json" source="snippets/configuration/worker-service/appsettings.IncludeScopes.json" highlight="9":::

下列程式碼會啟用主控台提供者的範圍：

```csharp
class Program
{
    static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging((_, logging) =>
                logging.ClearProviders()
                    .AddConsole(options => options.IncludeScopes = true));
}
```

## <a name="non-host-console-app"></a>非主機主控台應用程式

沒有 [泛型主機](generic-host.md) 的應用程式記錄程式碼，與 [加入提供者](logging-providers.md#built-in-logging-providers) 和 [建立記錄器](#create-logs)的方式不同。 在非主機主控台應用程式中，於建立 `LoggerFactory` 時呼叫提供者的 `Add{provider name}` 擴充方法：

```csharp
class Program
{
    static void Main(string[] args)
    {
        using var loggerFactory = LoggerFactory.Create(builder =>
        {
            builder
                .AddFilter("Microsoft", LogLevel.Warning)
                .AddFilter("System", LogLevel.Warning)
                .AddFilter("LoggingConsoleApp.Program", LogLevel.Debug)
                .AddConsole();
        });

        ILogger logger = loggerFactory.CreateLogger<Program>();
        logger.LogInformation("Example log message");
    }
}
```

`loggerFactory`物件是用來建立 <xref:Microsoft.Extensions.Logging.ILogger> 實例。

## <a name="create-logs-in-main"></a>在 Main 中建立記錄

下列程式碼會在 `Main` `ILogger` 建立主機之後，從 DI 取得實例來登入：

```csharp
using System;
using System.Threading.Tasks;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Hosting;
using Microsoft.Extensions.Logging;

class Program
{
    static Task Main(string[] args)
    {
        IHost host = Host.CreateDefaultBuilder(args).Build();

        var logger = host.Services.GetRequiredService<ILogger<Program>>();
        logger.LogInformation("Host created.");

        return host.RunAsync();
    }
}
```

### <a name="no-asynchronous-logger-methods"></a>無非同步記錄器方法

記錄速度應該很快，不值得花費非同步程式碼的效能成本來處理。 如果記錄資料存放區很慢，請不要直接寫入資料存放區。 請考慮一開始先將記錄檔訊息寫入快速存放區，然後再將它們移至慢速存放區。 例如，當記錄到 SQL Server 時，請勿直接在方法中這麼做 `Log` ，因為這些 `Log` 方法是同步的。 相反地，以同步方式將記錄訊息新增到記憶體內佇列，並讓背景工作角色提取出佇列的訊息，藉此執行推送資料到 SQL Server 的非同步工作。

## <a name="change-log-levels-in-a-running-app"></a>變更正在執行之應用程式中的記錄層級

記錄 API 不包含在應用程式執行時變更記錄層級的情節。 不過，某些設定提供者能夠重載設定，而這會對記錄設定產生立即的影響。 例如，檔案設定 [提供者](configuration-providers.md#file-configuration-provider) 預設會重載記錄設定。 如果在應用程式執行時，程式碼中的設定有所變更，應用程式可以呼叫 [IConfigurationRoot](xref:Microsoft.Extensions.Configuration.IConfigurationRoot.Reload%2A) 來更新應用程式的記錄設定。

## <a name="nuget-packages"></a>NuGet 套件

<xref:Microsoft.Extensions.Logging.ILogger%601>和 <xref:Microsoft.Extensions.Logging.ILoggerFactory> 介面和實作為包含在 .NET Core SDK 中。 它們也適用于下列 NuGet 套件：

- 這些介面位於中。 [抽象概念](https://www.nuget.org/packages/Microsoft.Extensions.Logging.Abstractions)。
- 預設的實作為 [記錄](https://www.nuget.org/packages/microsoft.extensions.logging)。

## <a name="apply-log-filter-rules-in-code"></a>在程式碼中套用記錄篩選規則

設定記錄篩選規則的慣用方法 [是使用 [](configuration.md)設定]。

下列範例說明如何在程式碼中註冊篩選規則：

```csharp
class Program
{
    static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging =>
               logging.AddFilter("System", LogLevel.Debug)
                  .AddFilter<DebugLoggerProvider>("Microsoft", LogLevel.Information)
                  .AddFilter<ConsoleLoggerProvider>("Microsoft", LogLevel.Trace));
}
```

`logging.AddFilter("System", LogLevel.Debug)` 指定 `System` 類別目錄和記錄層級 `Debug` 。 篩選會套用至所有提供者，因為未設定特定的提供者。

`AddFilter<DebugLoggerProvider>("Microsoft", LogLevel.Information)` 指定：

- `Debug`記錄提供者。
- 記錄層級 `Information` 和更新版本。
- 開頭為的所有分類 `"Microsoft"` 。

## <a name="see-also"></a>請參閱

- [.NET 中的記錄提供者](logging-providers.md)
- [在 .NET 中執行自訂記錄提供者](custom-logging-provider.md)
- [主控台記錄格式](console-log-formatter.md)
- [.NET 中的高效能記錄](high-performance-logging.md)
- 應該在 [github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues) 存放庫中建立記錄錯誤
