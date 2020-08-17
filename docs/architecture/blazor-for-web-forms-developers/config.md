---
title: 應用程式設定
description: 瞭解如何在 Blazor 不使用 ConfigurationManager 的情況下設定應用程式。
author: csharpfritz
ms.author: jefritz
no-loc:
- Blazor
ms.date: 04/01/2020
ms.openlocfilehash: 6154b4f8c7a5bff42e603b12d5ef85468b80224e
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267499"
---
# <a name="app-configuration"></a>應用程式設定

在 Web Form 中載入應用程式設定的主要方式，是在伺服器上 *web.config* 檔案中的專案， &mdash; 或 *web.config*所參考的相關設定檔案。您可以使用靜態 `ConfigurationManager` 物件來與應用程式設定、資料存放庫連接字串，以及新增到應用程式中的其他擴充設定提供者互動。 通常會查看與應用程式設定的互動，如下列程式碼所示：

```csharp
var configurationValue = ConfigurationManager.AppSettings["ConfigurationSettingName"];
var connectionString = ConfigurationManager.ConnectionStrings["MyDatabaseConnectionName"].ConnectionString;
```

Blazor如果您的應用程式是裝載在 WINDOWS IIS 伺服器上，使用 ASP.NET Core 和伺服器端時，可能會出現*web.config*檔案。 但是，不 `ConfigurationManager` 會與此設定互動，而且您可以從其他來源接收更多結構化的應用程式設定。 讓我們看看如何收集設定，以及您如何仍可以從 *web.config* 檔案存取設定資訊。

## <a name="configuration-sources"></a>組態來源

ASP.NET Core 辨識您的應用程式有許多設定來源可供使用。 根據預設，架構會嘗試為您提供這些功能的最佳功能。 ASP.NET Core 會從這些不同的來源讀取和匯總設定。 針對相同設定索引鍵，稍後載入的值會優先于較早的值。

ASP.NET Core 是專為雲端感知而設計，可讓操作員和開發人員更輕鬆地設定應用程式。 ASP.NET Core 可感知環境，並知道它是否正在您的 `Production` 或環境中執行 `Development` 。 環境指標是在 `ASPNETCORE_ENVIRONMENT` 系統內容變數中設定。 如果未設定任何值，則應用程式會預設為在 `Production` 環境中執行。

您的應用程式可以根據環境的名稱，從數個來源觸發和新增設定。 依預設，會依列出的順序從下列資源載入設定：

1. 檔案*上的appsettings.js* （如果有的話）
1. *appsettings。{ENVIRONMENT_NAME}. json* 檔案（如果有的話）
1. 磁片上的使用者秘密檔案（如果有的話）
1. 環境變數
1. 命令列引數

## <a name="appsettingsjson-format-and-access"></a>格式和存取 appsettings.js

檔案 * 上的appsettings.js* 可以使用結構化的值（如下列 JSON）進行階層處理：

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

當您看到上述的 JSON 時，設定系統會將子值壓平合併，並參考其完整階層式路徑。 冒號 (`:`) 字元分隔階層中的每個屬性。 例如，設定索引鍵會 `section1:key0` 存取 `section1` 物件常值的 `key0` 值。

## <a name="user-secrets"></a>使用者秘密

使用者密碼為：

* 儲存在開發人員工作站上的 JSON 檔案中，位於應用程式開發資料夾外部的設定值。
* 只有在環境中執行時才會載入 `Development` 。
* 與特定應用程式相關聯。
* 使用 .NET Core CLI 的命令來管理 `user-secrets` 。

藉由執行下列命令，為您的應用程式設定秘密儲存體 `user-secrets` ：

```dotnetcli
dotnet user-secrets init
```

上述命令會將 `UserSecretsId` 元素新增至專案檔。 元素包含 GUID，用來將秘密與應用程式產生關聯。 然後，您可以使用命令來定義秘密 `set` 。 例如：

```dotnetcli
dotnet user-secrets set "Parent:ApiKey" "12345"
```

上述命令可讓 `Parent:ApiKey` 開發人員工作站上的設定金鑰具有值 `12345` 。

如需有關建立、儲存和管理使用者密碼的詳細資訊，請參閱 [ASP.NET Core 檔中的開發應用程式秘密的安全儲存](/aspnet/core/security/app-secrets) 。

## <a name="environment-variables"></a>環境變數

下一組載入您應用程式設定的值是系統的環境變數。 您現在可以透過設定 API 存取所有系統的環境變數設定。 在您的應用程式內讀取時，階層值會簡維並以冒號字元分隔。 不過，某些作業系統不允許冒號字元環境變數名稱。 ASP.NET Core 藉由將具有雙底線 () 的值，轉換為存取時的冒號，來解決這項限制 `__` 。 您 `Parent:ApiKey` 可以使用環境變數來覆寫上述使用者秘密區段中的值 `Parent__ApiKey` 。

## <a name="command-line-arguments"></a>命令列引數

當您的應用程式啟動時，也可以將設定提供為命令列引數。 使用雙虛線 (`--`) 或斜線 (`/`) 標記法來表示要設定的設定值名稱以及要設定的值。 語法類似于下列命令：

```dotnetcli
dotnet run CommandLineKey1=value1 --CommandLineKey2=value2 /CommandLineKey3=value3
dotnet run --CommandLineKey1 value1 /CommandLineKey2 value2
dotnet run Parent:ApiKey=67890
```

## <a name="the-return-of-webconfig"></a>傳回 web.config

如果您已在 IIS 上將應用程式部署至 Windows， *web.config* 檔案仍會設定 iis 來管理您的應用程式。 根據預設，IIS 會將參考新增至 ASP.NET Core 模組 (ANCM) 。 ANCM 是原生 IIS 模組，可裝載您的應用程式來取代 Kestrel web 伺服器。 此 *web.config* 區段類似下列 XML 標記：

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

您可以藉由將專案中的元素嵌套來定義應用程式特定的設定 `environmentVariables` `aspNetCore` 。 此區段中定義的值會以環境變數的形式呈現給 ASP.NET Core 應用程式。 環境變數會在應用程式啟動的那段期間適當地載入。

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

ASP.NET Core 透過介面提供應用程式設定 <xref:Microsoft.Extensions.Configuration.IConfiguration> 。 Blazor需要存取設定的元件、 Blazor 頁面以及任何其他 ASP.NET Core 管理的類別，都應要求此設定介面。 ASP.NET Core framework 會自動將先前設定的已解決設定填入此介面。 在 Blazor 頁面或元件的 razor 標記上，您可以在 razor 檔案 `IConfiguration` 的頂端插入具有指示詞的物件，如下所 `@inject` 示： *.razor*

```razor
@inject IConfiguration Configuration
```

上述語句可讓 `IConfiguration` 物件在 `Configuration` Razor 範本的其餘部分都可作為變數使用。

您可以藉由指定搜尋為索引子參數的設定設定階層，來讀取個別的設定設定：

```csharp
var mySetting = Configuration["section1:key0"];
```

您可以使用方法來提取整個設定區段，方法是使用 <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> 類似的語法， `GetSection("section1")` 從先前的範例中取出 section1 的設定，以取得特定位置的索引鍵集合。

## <a name="strongly-typed-configuration"></a>強型別設定

有了 Web Form，就可以建立繼承自 <xref:System.Configuration.ConfigurationSection> 型別和相關聯類型的強型別設定型別。 `ConfigurationSection`允許您設定某些商務規則，以及處理這些設定值。

在 ASP.NET Core 中，您可以指定將接收設定值的類別階層。 這些類別：

* 不需要繼承自父類別。
* 應包含 `public` 符合您想要捕捉的設定結構之屬性和類型參考的屬性。

針對先前的 *appsettings.js* 範例，您可以定義下列類別來捕捉值：

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

您可以藉由將下列程式程式碼加入至方法來填入這個類別階層 `Startup.ConfigureServices` ：

```csharp
services.Configure<MyConfig>(Configuration);
```

在應用程式的其餘部分，您可以在類型的 Razor 範本中，將輸入參數加入至類別或指示 `@inject` `IOptions<MyConfig>` 詞，以接收強型別設定。 `IOptions<MyConfig>.Value`屬性將會產生 `MyConfig` 從設定中填入的值。

```razor
@inject IOptions<MyConfig> options
@code {
    var MyConfiguration = options.Value;
    var theSetting = MyConfiguration.section1.key0;
}
```

您可以在 ASP.NET Core 檔的 [選項模式](/aspnet/core/fundamentals/configuration/options#options-interfaces) 中找到選項功能的詳細資訊。

>[!div class="step-by-step"]
>[上一個](middleware.md) 
>[下一步](security-authentication-authorization.md)
