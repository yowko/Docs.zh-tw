---
title: 應用程式設定
description: 瞭解如何在 Blazor 不使用 ConfigurationManager 的情況下設定應用程式。
author: csharpfritz
ms.author: jefritz
no-loc:
- Blazor
ms.date: 04/01/2020
ms.openlocfilehash: a13f663c2c6908ba906e42cb939c3b8707b8cccd
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173311"
---
# <a name="app-configuration"></a>應用程式設定

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

在 Web form 中載入應用程式設定的主要方式，是在伺服器上的*web.config*檔案中的專案， &mdash; 或是*web.config*所參考的相關設定檔案。您可以使用靜態 `ConfigurationManager` 物件來與應用程式設定、資料存放庫連接字串，以及其他新增至應用程式的擴充設定提供者互動。 通常會看到與應用程式設定的互動，如下列程式碼所示：

```csharp
var configurationValue = ConfigurationManager.AppSettings["ConfigurationSettingName"];
var connectionString = ConfigurationManager.ConnectionStrings["MyDatabaseConnectionName"].ConnectionString;
```

使用 ASP.NET Core 和伺服器端時 Blazor ，如果您的應用程式是裝載在 WINDOWS IIS 伺服器上，則可能會出現*web.config*檔案。 不過， `ConfigurationManager` 這種設定並不會與此設定互動，您可以從其他來源接收更多結構化的應用程式設定。 讓我們看看如何收集設定，以及您仍然可以如何從*web.config*檔案存取設定資訊。

## <a name="configuration-sources"></a>組態來源

ASP.NET Core 可以辨識您的應用程式可能會使用的設定來源有許多種。 根據預設，架構會嘗試為您提供最佳的功能。 ASP.NET Core，會從這些不同的來源讀取和匯總設定。 之後，針對相同設定金鑰載入的值會優先于先前的值。

ASP.NET Core 是設計成可感知雲端，並讓操作員和開發人員更輕鬆地設定應用程式。 ASP.NET Core 可感知環境，並知道它是否正在您的 `Production` 或環境中執行 `Development` 。 環境指標是在 `ASPNETCORE_ENVIRONMENT` 系統內容變數中設定。 如果未設定任何值，應用程式預設會在環境中執行 `Production` 。

您的應用程式可以根據環境的名稱，觸發並新增數個來源的設定。 根據預設，會依照列出的順序從下列資源載入設定：

1. *appsettings.js*檔案（如果有的話）
1. *appsettings。{ENVIRONMENT_NAME}. json*檔案（如果有的話）
1. 磁片上的使用者秘密檔案（如果有的話）
1. 環境變數
1. 命令列引數

## <a name="appsettingsjson-format-and-access"></a>appsettings.js格式和存取

檔案*上的appsettings.js*可以與結構化的值（如下列 JSON）進行階層處理：

```json
{
  "section0": {
    "key0": "value",
    "key1": "value"
  },
  "section1": {
    "key0": "value",
    "key1": "value"
  }
}
```

當出現先前的 JSON 時，設定系統會將子值壓平合併，並參考其完整的階層式路徑。 冒號 (`:`) 字元，用來分隔階層中的每個屬性。 例如，設定金鑰會 `section1:key0` 存取 `section1` 物件常 `key0` 值的值。

## <a name="user-secrets"></a>使用者秘密

使用者秘密包括：

* 儲存在開發人員工作站的 JSON 檔案中的設定值，位於應用程式開發資料夾之外。
* 只有在環境中執行時才會載入 `Development` 。
* 與特定應用程式相關聯。
* 使用 .NET Core CLI 的命令進行管理 `user-secrets` 。

執行下列命令，為您的應用程式設定秘密儲存 `user-secrets` ：

```dotnetcli
dotnet user-secrets init
```

上述命令會將 `UserSecretsId` 元素加入至專案檔。 元素包含 GUID，用來將秘密與應用程式建立關聯。 接著，您可以使用命令來定義秘密 `set` 。 例如︰

```dotnetcli
dotnet user-secrets set "Parent:ApiKey" "12345"
```

上述命令會在 `Parent:ApiKey` 開發人員的工作站上提供設定金鑰，其值為 `12345` 。

如需有關建立、儲存和管理使用者秘密的詳細資訊，請參閱[ASP.NET Core 檔中的開發中的應用程式秘密安全儲存](/aspnet/core/security/app-secrets)。

## <a name="environment-variables"></a>環境變數

下一組載入至您應用程式設定的值是系統的環境變數。 您現在可以透過設定 API 來存取您的所有系統內容變數設定。 在您的應用程式中讀取時，階層值會壓平合併，並以冒號字元分隔。 不過，有些作業系統不允許冒號字元環境變數名稱。 ASP.NET Core 會藉由將具有雙底線的值 () 轉換 `__` 成冒號（當存取時）來解決這項限制。 您 `Parent:ApiKey` 可以使用環境變數來覆寫上述 [使用者密碼] 區段中的值 `Parent__ApiKey` 。

## <a name="command-line-arguments"></a>命令列引數

當您的應用程式啟動時，也可以將設定提供為命令列引數。 使用雙虛線 (`--`) 或斜線 (`/`) 標記法來指出要設定的設定值的名稱，以及要設定的值。 語法類似下列命令：

```dotnetcli
dotnet run CommandLineKey1=value1 --CommandLineKey2=value2 /CommandLineKey3=value3
dotnet run --CommandLineKey1 value1 /CommandLineKey2 value2
dotnet run Parent:ApiKey=67890
```

## <a name="the-return-of-webconfig"></a>傳回 web.config

如果您已將應用程式部署至 IIS 上的 Windows，則*web.config*檔案仍會設定 iis 來管理您的應用程式。 根據預設，IIS 會將參考新增至 ASP.NET Core 模組 (ANCM) 。 ANCM 是原生 IIS 模組，用來裝載您的應用程式來取代 Kestrel 網頁伺服器。 這個*web.config*區段與下列 XML 標記類似：

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <location path="." inheritInChildApplications="false">
    <system.webServer>
      <handlers>
        <add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModuleV2" resourceType="Unspecified" />
      </handlers>
      <aspNetCore processPath=".\MyApp.exe"
                  stdoutLogEnabled="false"
                  stdoutLogFile=".\logs\stdout"
                  hostingModel="inprocess" />
    </system.webServer>
  </location>
</configuration>
```

應用程式特定的設定可以藉由 `environmentVariables` 在元素中嵌套元素來定義 `aspNetCore` 。 本節中定義的值會以環境變數的形式呈現給 ASP.NET Core 應用程式。 環境變數會在應用程式啟動的該區段期間適當地載入。

```xml
<aspNetCore processPath="dotnet"
      arguments=".\MyApp.dll"
      stdoutLogEnabled="false"
      stdoutLogFile=".\logs\stdout"
      hostingModel="inprocess">
  <environmentVariables>
    <environmentVariable name="ASPNETCORE_ENVIRONMENT" value="Development" />
    <environmentVariable name="Parent:ApiKey" value="67890" />
  </environmentVariables>
</aspNetCore>
```

## <a name="read-configuration-in-the-app"></a>讀取應用程式中的設定

ASP.NET Core 透過介面提供應用程式設定 <xref:Microsoft.Extensions.Configuration.IConfiguration> 。 此設定介面應由您的 Blazor 元件、 Blazor 頁面，以及需要存取設定的任何其他 ASP.NET Core 受控類別所要求。 ASP.NET Core framework 會使用稍早設定的已解決設定，自動填入此介面。 在 Blazor 頁面或元件的 razor 標記上，您可以在 razor 檔案 `IConfiguration` 的頂端插入具有指示詞的物件，如下所 `@inject` 示： *.razor*

```razor
@inject IConfiguration Configuration
```

這個先前的語句可讓 `IConfiguration` 物件在 `Configuration` Razor 範本的其餘部分以變數的形式提供。

藉由指定要做為索引子參數的設定階層，可以讀取個別的設定：

```csharp
var mySetting = Configuration["section1:key0"];
```

您可以藉由使用 <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> 方法來抓取特定位置的索引鍵集合，使用類似于 `GetSection("section1")` 從先前範例中抓取 section1 設定的語法，取得整個設定區段。

## <a name="strongly-typed-configuration"></a>強型別設定

使用 Web form，可以建立從 <xref:System.Configuration.ConfigurationSection> 類型和相關聯類型繼承的強型別設定類型。 `ConfigurationSection`可讓您設定某些商務規則，並處理這些設定值。

在 ASP.NET Core 中，您可以指定將接收設定值的類別階層。 這些類別：

* 不需要繼承自父類別。
* 應包含 `public` 符合您想要捕獲之設定結構的屬性和類型參考的屬性。

針對稍早的*appsettings.js*範例，您可以定義下列類別來捕獲值：

```csharp
public class MyConfig
{
    public MyConfigSection section0 { get; set;}

    public MyConfigSection section1 { get; set;}
}

public class MyConfigSection
{
    public string key0 { get; set; }

    public string key1 { get; set; }
}
```

此類別階層可以藉由將下列這一行加入至方法來填入 `Startup.ConfigureServices` ：

```csharp
services.Configure<MyConfig>(Configuration);
```

在應用程式的其餘部分，您可以將輸入參數新增至 `@inject` 類型的 Razor 範本中的類別或指示 `IOptions<MyConfig>` 詞，以接收強型別設定。 `IOptions<MyConfig>.Value`屬性會產生 `MyConfig` 從設定中填入的值。

```razor
@inject IOptions<MyConfig> options
@code {
    var MyConfiguration = options.Value;
    var theSetting = MyConfiguration.section1.key0;
}
```

[選項] 功能的詳細資訊可在 ASP.NET Core 檔的[選項模式](/aspnet/core/fundamentals/configuration/options#options-interfaces)中找到。

>[!div class="step-by-step"]
>[上一個](middleware.md) 
>[下一步](security-authentication-authorization.md)
