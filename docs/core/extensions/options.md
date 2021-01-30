---
title: .NET 中的選項模式
author: IEvangelist
description: 瞭解如何使用選項模式來代表 .NET 應用程式中的相關設定群組。
ms.author: dapine
ms.date: 01/21/2021
ms.openlocfilehash: 413f731337a6012bb1e29f1f38c2df6da7525867
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216026"
---
# <a name="options-pattern-in-net"></a>.NET 中的選項模式

選項模式使用類別來提供相關設定群組的強型別存取。 當[組態設定](configuration.md)依案例隔離到不同的類別時，應用程式會遵守兩個重要的軟體工程準則：

- [介面隔離原則 (ISP) 或封裝](../../architecture/modern-web-apps-azure/architectural-principles.md#encapsulation)：相依于設定的案例 (類別) 取決於所使用的設定。
- [關注點分離](../../architecture/modern-web-apps-azure/architectural-principles.md#separation-of-concerns) (不同考量)：應用程式不同部分的設定不會彼此相依或結合。

選項也提供驗證設定資料的機制。 如需詳細資訊，請參閱[選項驗證](#options-validation)一節。

## <a name="bind-hierarchical-configuration"></a>系結階層式設定

讀取相關設定值的慣用方式是使用選項模式。 您可以透過 <xref:Microsoft.Extensions.Options.IOptions%601> 介面（泛型型別參數受限於）來使用選項模式 `TOptions` `class` 。 `IOptions<TOptions>`之後可透過相依性插入來提供。 如需詳細資訊，請參閱 [.net 中](dependency-injection.md)的相依性插入。

例如，若要讀取下列設定值：

:::code language="json" source="snippets/configuration/console-json/appsettings.json" range="3-6":::

建立下列 `TransientFaultHandlingOptions` 類別：

:::code language="csharp" source="snippets/configuration/console-json/TransientFaultHandlingOptions.cs" range="5-9":::

<span id="options-class"></span> 使用選項模式時，選項類別：

- 必須是具有公用無參數函數的非抽象
- 包含用來系結的公用讀寫屬性 (欄位為 ***not** _ 系結) 

下列程式碼：

_ 呼叫 [ConfigurationBinder](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Bind%2A) ，將類別系結至 `TransientFaultHandlingOptions` `"TransientFaultHandlingOptions"` 區段。
* 顯示設定資料。

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="31-38":::

在上述程式碼中，會讀取應用程式啟動後的 JSON 設定檔變更。

[`ConfigurationBinder.Get<T>`](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Get%2A) 系結並傳回指定的型別。 `ConfigurationBinder.Get<T>` 可能比使用更方便 `ConfigurationBinder.Bind` 。 下列程式碼顯示如何搭配 `ConfigurationBinder.Get<T>` `TransientFaultHandlingOptions` 類別使用：

```csharp
IConfigurationRoot configurationRoot = configuration.Build();

var options =
    configurationRoot.GetSection(nameof(TransientFaultHandlingOptions))
                     .Get<TransientFaultHandlingOptions>();

Console.WriteLine($"TransientFaultHandlingOptions.Enabled={options.Enabled}");
Console.WriteLine($"TransientFaultHandlingOptions.AutoRetryDelay={options.AutoRetryDelay}");
```

在上述程式碼中，會讀取應用程式啟動後的 JSON 設定檔變更。

> [!IMPORTANT]
> <xref:Microsoft.Extensions.Configuration.ConfigurationBinder>類別會公開數個 api （例如和），這些 api 不 `.Bind(object instance)` `.Get<T>()` 會受限於 `class` 。 使用任何 [選項介面](#options-interfaces)時，您必須遵守上述的 [選項類別條件約束](#options-class)。

使用選項模式時的替代方法是系結 `"TransientFaultHandlingOptions"` 區段，並將它加入至相依性 [插入服務容器](dependency-injection.md)。 在下列程式碼中， `TransientFaultHandlingOptions` 會新增至服務容器， <xref:Microsoft.Extensions.DependencyInjection.OptionsConfigurationServiceCollectionExtensions.Configure%2A> 並系結至設定：

```csharp
services.Configure<TransientFaultHandlingOptions>(
    configurationRoot.GetSection(
        key: nameof(TransientFaultHandlingOptions)));
```

> [!TIP]
> `key`參數是要搜尋之設定區段的名稱。 _Not * 必須符合代表它的型別名稱。 例如，您可能會有一個名為的區段 `"FaultHandling"` ，而且可以由 `TransientFaultHandlingOptions` 類別表示。 在此情況下，您會 `"FaultHandling"` 改為傳遞給 <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> 函數。 `nameof`當已命名的區段符合其對應的型別時，就會使用運算子作為便利性。

使用上述程式碼，下列程式碼會讀取位置選項：

:::code language="csharp" source="snippets/configuration/console-json/ExampleService.cs":::

在上述程式碼中，應用程式啟動後的 JSON 設定檔變更為 ***not** _ read。 若要讀取應用程式啟動後的變更，請使用 [IOptionsSnapshot](#use-ioptionssnapshot-to-read-updated-data)。

## <a name="options-interfaces"></a>選項介面

<xref:Microsoft.Extensions.Options.IOptions%601>:

- 不 _*_支援：_*_
  - 在應用程式啟動後讀取設定資料。
  - [具名選項](#named-options-support-using-iconfigurenamedoptions)
- 註冊為 [Singleton](dependency-injection.md#singleton) ，並且可以插入至任何 [服務存留期](dependency-injection.md#service-lifetimes)。

<xref:Microsoft.Extensions.Options.IOptionsSnapshot%601>:

- 適用于應在 [範圍或暫時性存留期](dependency-injection.md#service-lifetimes)內，于每次插入解析時重新計算選項的情況。 如需詳細資訊，請參閱 [使用 IOptionsSnapshot 讀取更新的資料](#use-ioptionssnapshot-to-read-updated-data)。
- 註冊為 [範圍](dependency-injection.md#scoped) ，因此無法插入至單一服務。
- 支援 [已命名的選項](#named-options-support-using-iconfigurenamedoptions)

<xref:Microsoft.Extensions.Options.IOptionsMonitor%601>:

- 用來取得實例的選項和管理選項通知 `TOptions` 。
- 註冊為 [Singleton](dependency-injection.md#singleton) ，並且可以插入至任何 [服務存留期](dependency-injection.md#service-lifetimes)。
- 支援：
  - 變更通知
  - [具名選項](#named-options-support-using-iconfigurenamedoptions)
  - [可重新載入的設定](#use-ioptionssnapshot-to-read-updated-data)
  - 選擇性選項無效判定 (<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601>)
  
<xref:Microsoft.Extensions.Options.IOptionsFactory%601> 負責建立新的選項執行個體。 它有單一 <xref:Microsoft.Extensions.Options.IOptionsFactory%601.Create%2A> 方法。 預設實作會接受所有已註冊的 <xref:Microsoft.Extensions.Options.IConfigureOptions%601> 與 <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601>，並先執行所有設定，接著執行設定後作業。 它會區別 <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> 和 <xref:Microsoft.Extensions.Options.IConfigureOptions%601>，且只會呼叫適當的介面。

<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> 會由 <xref:Microsoft.Extensions.Options.IOptionsMonitor%601> 用來快取 `TOptions` 執行個體。 <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> 會使監視器中的選項執行個體失效，以便重新計算值 (<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryRemove%2A>)。 值可以使用 <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryAdd%2A> 手動導入。 <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.Clear%2A> 方法用於應該視需要重新建立所有具名執行個體時。

## <a name="use-ioptionssnapshot-to-read-updated-data"></a>使用 IOptionsSnapshot 讀取更新的資料

當您使用時 <xref:Microsoft.Extensions.Options.IOptionsSnapshot%601> ，每個要求的選項會在存取時計算一次，而且會在要求的存留期內快取。 使用支援讀取已更新設定值的設定提供者時，會在應用程式啟動後讀取設定的變更。

和之間的差異在於 `IOptionsMonitor` `IOptionsSnapshot` ：

- `IOptionsMonitor` 是 [單一服務](dependency-injection.md#singleton) ，可隨時抓取目前的選項值，這在單一相依性中特別有用。
- `IOptionsSnapshot` 是限 [域的服務](dependency-injection.md#scoped) ，會在建立物件時提供選項的快照 `IOptionsSnapshot<T>` 。 選項快照集的設計目的是要搭配使用暫時性和限定範圍的相依性。

下列程式碼使用 <xref:Microsoft.Extensions.Options.IOptionsSnapshot%601> 。

:::code language="csharp" source="snippets/configuration/console-json/ScopedService.cs":::

下列程式碼會註冊系結的設定實例 `TransientFaultHandlingOptions` ：

```csharp
services.Configure<TransientFaultHandlingOptions>(
    configurationRoot.GetSection(
        nameof(TransientFaultHandlingOptions)));
```

在上述程式碼中，會讀取應用程式啟動後的 JSON 設定檔變更。

## <a name="ioptionsmonitor"></a>IOptionsMonitor

下列程式碼會註冊針對系結的設定實例 `TransientFaultHandlingOptions` 。

```csharp
services.Configure<TransientFaultHandlingOptions>(
    configurationRoot.GetSection(
        nameof(TransientFaultHandlingOptions)));
```

下列範例會使用 <xref:Microsoft.Extensions.Options.IOptionsMonitor%601>：

:::code language="csharp" source="snippets/configuration/console-json/MonitorService.cs":::

在上述程式碼中，會讀取應用程式啟動後的 JSON 設定檔變更。

## <a name="named-options-support-using-iconfigurenamedoptions"></a>使用 IConfigureNamedOptions 的命名選項支援

命名選項：

- 當多個設定區段系結至相同的屬性時，會很有用。
- 會區分大小寫。

請考慮 * file 上的下列 _appsettings.js：

```json
{
  "Features": {
    "Personalize": {
      "Enabled": true,
      "ApiKey": "aGEgaGEgeW91IHRob3VnaHQgdGhhdCB3YXMgcmVhbGx5IHNvbWV0aGluZw=="
    },
    "WeatherStation": {
      "Enabled": true,
      "ApiKey": "QXJlIHlvdSBhdHRlbXB0aW5nIHRvIGhhY2sgdXM/"
    }
  }
}
```

`Features:Personalize` `Features:WeatherStation` 下列類別可用於每個區段，而不是建立兩個類別來系結和：

```csharp
public class Features
{
    public const string Personalize = nameof(Personalize);
    public const string WeatherStation = nameof(WeatherStation);

    public bool Enabled { get; set; }
    public string ApiKey { get; set; }
}
```

下列程式碼會設定命名選項：

```csharp
ConfigureServices(services =>
{
    services.Configure<Features>(
        Features.Personalize,
        Configuration.GetSection("Features:Personalize"));

    services.Configure<Features>(
        Features.WeatherStation,
        Configuration.GetSection("Features:WeatherStation"));
});
```

下列程式碼會顯示已命名的選項：

```csharp
public class Service
{
    private readonly Features _personalizeFeature;
    private readonly Features _weatherStationFeature;

    public Service(IOptionsSnapshot<Features> namedOptionsAccessor)
    {
        _personalizeFeature = namedOptionsAccessor.Get(Features.Personalize);
        _weatherStationFeature = namedOptionsAccessor.Get(Features.WeatherStation);
    }
}
```

所有選項都是具名執行個體。 <xref:Microsoft.Extensions.Options.IConfigureOptions%601> 系統會將實例視為目標 `Options.DefaultName` 實例，也就是 `string.Empty` 。 <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> 也會實作 <xref:Microsoft.Extensions.Options.IConfigureOptions%601>。 <xref:Microsoft.Extensions.Options.IOptionsFactory%601> 的預設實作有邏輯可以適當地使用每個項目。 此 `null` 命名選項用來以所有已命名的實例為目標，而不是特定的已命名實例。 <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.ConfigureAll%2A> 並 <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A> 使用此慣例。

## <a name="optionsbuilder-api"></a>OptionsBuilder API

<xref:Microsoft.Extensions.Options.OptionsBuilder%601> 會用於設定 `TOptions` 執行個體。 因為 `OptionsBuilder` 僅為初始 `AddOptions<TOptions>(string optionsName)` 呼叫的單一參數，而不是出現在所有後續呼叫的參數，所以其可簡化建立具名選項的程序。 選項驗證及接受服務依存性的 `ConfigureOptions` 多載，只可透過 `OptionsBuilder` 使用。

`OptionsBuilder` 在 [ [選項驗證](#options-validation) ] 區段中使用。

## <a name="use-di-services-to-configure-options"></a>使用 DI 服務來設定選項

您可以透過下列兩種方式，從相依性插入來存取服務：

- 傳遞設定委派以[設定](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) [OptionsBuilder \<TOptions> ](xref:Microsoft.Extensions.Options.OptionsBuilder%601)。 `OptionsBuilder<TOptions>` 提供 [設定的多載，可](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) 讓您使用最多五個服務來設定選項：

  ```csharp
  services.AddOptions<MyOptions>("optionalName")
      .Configure<ExampleService, ScopedService, MonitorService>(
          (options, es, ss, ms) =>
              options.Property = DoSomethingWith(es, ss, ms));
  ```

- 建立實作為型別 <xref:Microsoft.Extensions.Options.IConfigureOptions%601> <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> 並將其註冊為服務的型別。

我們建議您將設定委派傳遞到 [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A)，因為建立服務更複雜。 建立類型相當於呼叫 [設定](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A)時的架構。 呼叫 [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) 會註冊暫時性泛型 <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601>，其具有會接受所指定泛型服務類型的建構函式。

## <a name="options-validation"></a>選項驗證

選項驗證可讓您驗證選項值。

請考慮下列 *appsettings.json* file：

```json
{
  "Settings": {
    "SiteTitle": "Amazing docs from Awesome people!",
    "Scale": 10,
    "VerbosityLevel": 32
  }
}
```

下列類別會系結至設定 `"Settings"` 區段，並套用一些 `DataAnnotations` 規則：

:::code language="csharp" source="snippets/configuration/console-json/SettingsOptions.cs":::

下列程式碼：

- 呼叫 <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A> 以取得系結至類別的[OptionsBuilder \<TOptions> ](xref:Microsoft.Extensions.Options.OptionsBuilder%601) `SettingsOptions` 。
- <xref:Microsoft.Extensions.DependencyInjection.OptionsBuilderDataAnnotationsExtensions.ValidateDataAnnotations%2A>使用呼叫來啟用驗證 `DataAnnotations` 。

```csharp
services.AddOptions<SettingsOptions>()
    .Bind(Configuration.GetSection(SettingsOptions.Settings))
    .ValidateDataAnnotations();
```

`ValidateDataAnnotations`擴充方法定義于[DataAnnotations](https://www.nuget.org/packages/Microsoft.Extensions.Options.DataAnnotations) NuGet 套件中。

下列程式碼顯示設定值或驗證錯誤：

:::code language="csharp" source="snippets/configuration/console-json/ValidationService.cs":::

下列程式碼會使用委派來套用更複雜的驗證規則：

```csharp
services.AddOptions<SettingsOptions>()
    .Bind(Configuration.GetSection(SettingsOptions.Settings))
    .ValidateDataAnnotations()
    .Validate(config =>
    {
        if (config.Scale != 0)
        {
            return config.VerbosityLevel > config.Scale;
        }

        return true;
    }, "VerbosityLevel must be > than Scale.");
```

### <a name="ivalidateoptions-for-complex-validation"></a>複雜驗證的 IValidateOptions

下列類別會實行 <xref:Microsoft.Extensions.Options.IValidateOptions%601> ：

:::code language="csharp" source="snippets/configuration/console-json/ValidateSettingsOptions.cs":::

`IValidateOptions` 可將驗證程式代碼移至類別。

使用上述程式碼，即可在中使用下列程式碼來啟用驗證 `ConfigureServices` ：

```csharp
services.Configure<SettingsOptions>(
    Configuration.GetSection(
        SettingsOptions.Settings));
services.TryAddEnumerable(
    ServiceDescriptor.Singleton
        <IValidateOptions<SettingsOptions>, ValidateSettingsOptions>());
```

## <a name="options-post-configuration"></a>選項設定後作業

使用 <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601> 來設定設定後作業。 後續設定會在所有設定都發生之後執行 <xref:Microsoft.Extensions.Options.IConfigureOptions%601> ，而且在您需要覆寫設定的案例中很有用：

```csharp
services.PostConfigure<CustomOptions>(customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

<xref:Microsoft.Extensions.Options.IPostConfigureOptions%601.PostConfigure%2A> 可用來後置設定具名選項：

```csharp
services.PostConfigure<CustomOptions>("named_options_1", customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

使用 <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A> 後置設定所有設定執行個體：

```csharp
services.PostConfigureAll<CustomOptions>(customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

## <a name="see-also"></a>另請參閱

- [.NET 中的設定](configuration.md)
- [.NET 程式庫作者的選項模式指引](options-library-authors.md)
