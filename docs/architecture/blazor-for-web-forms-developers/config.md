---
title: 應用程式設定
description: 瞭解如何配置 Blazor 應用而不使用配置管理員。
author: csharpfritz
ms.author: jefritz
ms.date: 04/01/2020
ms.openlocfilehash: c780a395f72e2520af86c20c7f6618953a528ff7
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588239"
---
# <a name="app-configuration"></a>應用程式設定

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

在 Web 窗體中載入應用配置的主要方法是在伺服器上使用*Web.config*&mdash;檔中的項目或*Web.config*引用的相關設定檔。可以使用靜態`ConfigurationManager`物件與應用設定、數據存儲庫連接字串以及添加到應用的其他擴展配置提供程式進行交互。 通常可以看到與應用配置的交互,如以下代碼所示:

```csharp
var configurationValue = ConfigurationManager.AppSettings["ConfigurationSettingName"];
var connectionString = ConfigurationManager.ConnectionStrings["MyDatabaseConnectionName"].ConnectionString;
```

對於ASP.NET核心和伺服器端 Blazor,如果你的應用託管在 Windows IIS 伺服器上,則*Web.config*檔可能會存在。 但是,沒有`ConfigurationManager`使用此配置的交互,並且可以從其他源接收更結構化的應用配置。 讓我們來看看如何收集配置以及如何仍然可以從*Web.config*檔訪問配置資訊。

## <a name="configuration-sources"></a>組態來源

ASP.NET Core 認識到許多配置源可能要用於你的應用。 默認情況下,框架嘗試為您提供這些功能中的最佳功能。 配置由ASP.NET核心從這些不同來源讀取和聚合。 以後為同一配置鍵載入的值優先於以前的值。

ASP.NET Core 設計為具有雲端感知功能,並使操作員和開發人員更輕鬆地配置應用。 ASP.NET核心是環境感知,知道它是否運行在你的`Production``Development`或環境中。 環境指示器設置在系統環境變數`ASPNETCORE_ENVIRONMENT`中。 如果未配置任何值,則應用預設在`Production`環境中運行。

你的應用可以根據環境的名稱觸發和添加來自多個源的配置。 預設情況下,設定按列出的順序從以下資源載入:

1. *應用程式設定.json*檔,如果存在
1. *應用設置。{ENVIRONMENT_NAME}.json*檔,如果存在
1. 使用者機密檔案磁碟上,如果存在
1. 環境變數
1. 命令列引數

## <a name="appsettingsjson-format-and-access"></a>應用程式設定.json 格式與存取

*appvalue.json*檔可以分層,其值結構如下 JSON:

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

當提供前面的 JSON 時,配置系統會平展子值並引用其完全限定的分層路徑。 冒號`:`( ) 字元分隔層次結構中的每個屬性。 例如,配置鍵`section1:key0``section1`訪問`key0`物件文本的值。

## <a name="user-secrets"></a>使用者機密

使用者機密包括:

* 存儲在開發人員工作站上的 JSON 檔中的配置值,在應用開發資料夾之外。
* 僅在`Development`環境中運行時載入。
* 與特定應用關聯。
* 使用 .NET 核心`user-secrets`CLI 的命令進行管理。

透過執行`user-secrets`指令為機密儲存配置應用:

```dotnetcli
dotnet user-secrets init
```

前面的命令向專案檔`UserSecretsId`添加一個元素。 該元素包含一個 GUID,用於將機密與應用相關聯。 然後,您可以使用 指令定義機`set`密 。 例如：

```dotnetcli
dotnet user-secrets set "Parent:ApiKey" "12345"
```

前面的命令使`Parent:ApiKey`配置金鑰在具有`12345`值的開發人員工作站上可用。

有關建立、儲存和管理使用者機密的詳細資訊,請參閱[ASP.NET 核心文件中開發中應用機密的安全儲存](/aspnet/core/security/app-secrets)。

## <a name="environment-variables"></a>環境變數

載入應用配置中的下一組值是系統的環境變數。 現在,您可以通過配置 API 存取系統的所有環境變數設定。 在應用內讀取時,分層值被拼平並由冒號字元分隔。 但是,某些操作系統不允許冒號字元環境變數名稱。 ASP.NET Core 通過在存取具有雙下`__`劃線 ( ) 的值時將值轉換為冒號來解決此限制。 上面`Parent:ApiKey`用戶機密部分中的值可以使用環境變數`Parent__ApiKey`覆蓋。

## <a name="command-line-arguments"></a>命令列引數

當應用啟動時,也可以作為命令列參數提供配置。 使用雙虛線`--`( )`/`或前斜 杠 ( ) 表示法來指示要設定的設定值的名稱和要配置的值。 語法類似於以下指令:

```dotnetcli
dotnet run CommandLineKey1=value1 --CommandLineKey2=value2 /CommandLineKey3=value3
dotnet run --CommandLineKey1 value1 /CommandLineKey2 value2
dotnet run Parent:ApiKey=67890
```

## <a name="the-return-of-webconfig"></a>Web.config 的回歸

如果您將應用部署到 IIS 上的 Windows,則*Web.config*檔仍會配置 IIS 來管理你的應用。 默認情況下,IIS會添加對 ASP.NET核心模組 (ANCM) 的引用。 ANCM 是一個本機 IIS 模組,用於託管您的應用,以代替 Kestrel Web 伺服器。 此*Web.config*部份類似於以下 XML 標籤:

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

可以通過嵌`environmentVariables`套 元素中的元素來定義特定於`aspNetCore`應用的 配置。 本節中定義的值作為環境變數呈現給ASP.NET核心應用。 環境變數在應用啟動期間適當載入。

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

ASP.NET核心透過<xref:Microsoft.Extensions.Configuration.IConfiguration>介面提供應用配置。 此配置介面應由 Blazor 元件、Blazor 頁面以及需要存取配置的任何其他ASP.NET Core 託管類請求。 ASP.NET核心框架將自動填充此介面,並配置了前面配置的已解決配置。 在 Blazor 頁或元件的 Razor 標記`IConfiguration`上,可以在 *.razor*檔案`@inject`頂部向物件注入指令,如下所示:

```razor
@inject IConfiguration Configuration
```

在前面的語句使`IConfiguration`該物件`Configuration`作為 變數在整個 Razor 範本的其餘部分中可用。

可以通過指定為索引器參數尋求的設定設定層次結構來讀取各個配置設定:

```csharp
var mySetting = Configuration["section1:key0"];
```

可以使用方法<xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A>檢索特定位置的密鑰集合,其語法類似`GetSection("section1")`於從前面的示例中檢索第 1 節的配置,從而獲取整個配置部分。

## <a name="strongly-typed-configuration"></a>強類型設定

使用 Web 窗體,可以<xref:System.Configuration.ConfigurationSection>建立從 類型和相關類型繼承的強類型配置類型。 A`ConfigurationSection`允許您為這些配置值配置某些業務規則和處理。

在ASP.NET Core 中,您可以指定將接收配置值的類層次結構。 這些類:

* 不需要從父類繼承。
* 應包含`public`與要捕獲的配置結構的屬性匹配的屬性和類型引用的屬性。

對於前面的*appsettings.json*範例,您可以定義以下類來擷取這些值:

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

可以通過將以下行添加`Startup.ConfigureServices`到 方法來填充此類層次結構:

```csharp
services.Configure<MyConfig>(Configuration);
```

在應用的其餘部分中,您可以將輸入參數添加到類或類型`@inject``IOptions<MyConfig>`Razor 範本中的指令,以接收強類型配置設置。 該`IOptions<MyConfig>.Value`屬性將生成`MyConfig`從 配置設置填充的值。

```razor
@inject IOptions<MyConfig> options
@code {
    var MyConfiguration = options.Value;
    var theSetting = MyConfiguration.section1.key0;
}
```

關於選項功能的詳細資訊,請參考[ASP.NET 核心文件中的選項模式](/aspnet/core/fundamentals/configuration/options#options-interfaces)。

>[!div class="step-by-step"]
>[前一個](middleware.md)
>[下一個](security-authentication-authorization.md)
