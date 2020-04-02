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
# <a name="app-configuration"></a><span data-ttu-id="18638-103">應用程式設定</span><span class="sxs-lookup"><span data-stu-id="18638-103">App configuration</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="18638-104">在 Web 窗體中載入應用配置的主要方法是在伺服器上使用*Web.config*&mdash;檔中的項目或*Web.config*引用的相關設定檔。可以使用靜態`ConfigurationManager`物件與應用設定、數據存儲庫連接字串以及添加到應用的其他擴展配置提供程式進行交互。</span><span class="sxs-lookup"><span data-stu-id="18638-104">The primary way to load app configuration in Web Forms is with entries in the *web.config* file&mdash;either on the server or a related configuration file referenced by *web.config*. You can use the static `ConfigurationManager` object to interact with app settings, data repository connection strings, and other extended configuration providers that are added into the app.</span></span> <span data-ttu-id="18638-105">通常可以看到與應用配置的交互,如以下代碼所示:</span><span class="sxs-lookup"><span data-stu-id="18638-105">It's typical to see interactions with app configuration as seen in the following code:</span></span>

```csharp
var configurationValue = ConfigurationManager.AppSettings["ConfigurationSettingName"];
var connectionString = ConfigurationManager.ConnectionStrings["MyDatabaseConnectionName"].ConnectionString;
```

<span data-ttu-id="18638-106">對於ASP.NET核心和伺服器端 Blazor,如果你的應用託管在 Windows IIS 伺服器上,則*Web.config*檔可能會存在。</span><span class="sxs-lookup"><span data-stu-id="18638-106">With ASP.NET Core and server-side Blazor, the *web.config* file MAY be present if your app is hosted on a Windows IIS server.</span></span> <span data-ttu-id="18638-107">但是,沒有`ConfigurationManager`使用此配置的交互,並且可以從其他源接收更結構化的應用配置。</span><span class="sxs-lookup"><span data-stu-id="18638-107">However, there's no `ConfigurationManager` interaction with this configuration, and you can receive more structured app configuration from other sources.</span></span> <span data-ttu-id="18638-108">讓我們來看看如何收集配置以及如何仍然可以從*Web.config*檔訪問配置資訊。</span><span class="sxs-lookup"><span data-stu-id="18638-108">Let's take a look at how configuration is gathered and how you can still access configuration information from a *web.config* file.</span></span>

## <a name="configuration-sources"></a><span data-ttu-id="18638-109">組態來源</span><span class="sxs-lookup"><span data-stu-id="18638-109">Configuration sources</span></span>

<span data-ttu-id="18638-110">ASP.NET Core 認識到許多配置源可能要用於你的應用。</span><span class="sxs-lookup"><span data-stu-id="18638-110">ASP.NET Core recognizes there are many configuration sources you may want to use for your app.</span></span> <span data-ttu-id="18638-111">默認情況下,框架嘗試為您提供這些功能中的最佳功能。</span><span class="sxs-lookup"><span data-stu-id="18638-111">The framework attempts to offer you the best of these features by default.</span></span> <span data-ttu-id="18638-112">配置由ASP.NET核心從這些不同來源讀取和聚合。</span><span class="sxs-lookup"><span data-stu-id="18638-112">Configuration is read and aggregated from these various sources by ASP.NET Core.</span></span> <span data-ttu-id="18638-113">以後為同一配置鍵載入的值優先於以前的值。</span><span class="sxs-lookup"><span data-stu-id="18638-113">Later loaded values for the same configuration key take precedence over earlier values.</span></span>

<span data-ttu-id="18638-114">ASP.NET Core 設計為具有雲端感知功能,並使操作員和開發人員更輕鬆地配置應用。</span><span class="sxs-lookup"><span data-stu-id="18638-114">ASP.NET Core was designed to be cloud-aware and to make configuration of apps easier for both operators and developers.</span></span> <span data-ttu-id="18638-115">ASP.NET核心是環境感知,知道它是否運行在你的`Production``Development`或環境中。</span><span class="sxs-lookup"><span data-stu-id="18638-115">ASP.NET Core is environment-aware and knows if it's running in your `Production` or `Development` environment.</span></span> <span data-ttu-id="18638-116">環境指示器設置在系統環境變數`ASPNETCORE_ENVIRONMENT`中。</span><span class="sxs-lookup"><span data-stu-id="18638-116">The environment indicator is set in the `ASPNETCORE_ENVIRONMENT` system environment variable.</span></span> <span data-ttu-id="18638-117">如果未配置任何值,則應用預設在`Production`環境中運行。</span><span class="sxs-lookup"><span data-stu-id="18638-117">If no value is configured, the app defaults to running in the `Production` environment.</span></span>

<span data-ttu-id="18638-118">你的應用可以根據環境的名稱觸發和添加來自多個源的配置。</span><span class="sxs-lookup"><span data-stu-id="18638-118">Your app can trigger and add configuration from several sources based on the environment's name.</span></span> <span data-ttu-id="18638-119">預設情況下,設定按列出的順序從以下資源載入:</span><span class="sxs-lookup"><span data-stu-id="18638-119">By default, configuration is loaded from the following resources in the order listed:</span></span>

1. <span data-ttu-id="18638-120">*應用程式設定.json*檔,如果存在</span><span class="sxs-lookup"><span data-stu-id="18638-120">*appsettings.json* file, if present</span></span>
1. <span data-ttu-id="18638-121">*應用設置。{ENVIRONMENT_NAME}.json*檔,如果存在</span><span class="sxs-lookup"><span data-stu-id="18638-121">*appsettings.{ENVIRONMENT_NAME}.json* file, if present</span></span>
1. <span data-ttu-id="18638-122">使用者機密檔案磁碟上,如果存在</span><span class="sxs-lookup"><span data-stu-id="18638-122">User secrets file on disk, if present</span></span>
1. <span data-ttu-id="18638-123">環境變數</span><span class="sxs-lookup"><span data-stu-id="18638-123">Environment variables</span></span>
1. <span data-ttu-id="18638-124">命令列引數</span><span class="sxs-lookup"><span data-stu-id="18638-124">Command-line arguments</span></span>

## <a name="appsettingsjson-format-and-access"></a><span data-ttu-id="18638-125">應用程式設定.json 格式與存取</span><span class="sxs-lookup"><span data-stu-id="18638-125">appsettings.json format and access</span></span>

<span data-ttu-id="18638-126">*appvalue.json*檔可以分層,其值結構如下 JSON:</span><span class="sxs-lookup"><span data-stu-id="18638-126">The *appsettings.json* file can be hierarchical with values structured like the following JSON:</span></span>

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

<span data-ttu-id="18638-127">當提供前面的 JSON 時,配置系統會平展子值並引用其完全限定的分層路徑。</span><span class="sxs-lookup"><span data-stu-id="18638-127">When presented with the preceding JSON, the configuration system flattens child values and references their fully qualified hierarchical paths.</span></span> <span data-ttu-id="18638-128">冒號`:`( ) 字元分隔層次結構中的每個屬性。</span><span class="sxs-lookup"><span data-stu-id="18638-128">A colon (`:`) character separates each property in the hierarchy.</span></span> <span data-ttu-id="18638-129">例如,配置鍵`section1:key0``section1`訪問`key0`物件文本的值。</span><span class="sxs-lookup"><span data-stu-id="18638-129">For example, the configuration key `section1:key0` accesses the `section1` object literal's `key0` value.</span></span>

## <a name="user-secrets"></a><span data-ttu-id="18638-130">使用者機密</span><span class="sxs-lookup"><span data-stu-id="18638-130">User secrets</span></span>

<span data-ttu-id="18638-131">使用者機密包括:</span><span class="sxs-lookup"><span data-stu-id="18638-131">User secrets are:</span></span>

* <span data-ttu-id="18638-132">存儲在開發人員工作站上的 JSON 檔中的配置值,在應用開發資料夾之外。</span><span class="sxs-lookup"><span data-stu-id="18638-132">Configuration values that are stored in a JSON file on the developer's workstation, outside of the app development folder.</span></span>
* <span data-ttu-id="18638-133">僅在`Development`環境中運行時載入。</span><span class="sxs-lookup"><span data-stu-id="18638-133">Only loaded when running in the `Development` environment.</span></span>
* <span data-ttu-id="18638-134">與特定應用關聯。</span><span class="sxs-lookup"><span data-stu-id="18638-134">Associated with a specific app.</span></span>
* <span data-ttu-id="18638-135">使用 .NET 核心`user-secrets`CLI 的命令進行管理。</span><span class="sxs-lookup"><span data-stu-id="18638-135">Managed with the .NET Core CLI's `user-secrets` command.</span></span>

<span data-ttu-id="18638-136">透過執行`user-secrets`指令為機密儲存配置應用:</span><span class="sxs-lookup"><span data-stu-id="18638-136">Configure your app for secrets storage by executing the `user-secrets` command:</span></span>

```dotnetcli
dotnet user-secrets init
```

<span data-ttu-id="18638-137">前面的命令向專案檔`UserSecretsId`添加一個元素。</span><span class="sxs-lookup"><span data-stu-id="18638-137">The preceding command adds a `UserSecretsId` element to the project file.</span></span> <span data-ttu-id="18638-138">該元素包含一個 GUID,用於將機密與應用相關聯。</span><span class="sxs-lookup"><span data-stu-id="18638-138">The element contains a GUID, which is used to associate secrets with the app.</span></span> <span data-ttu-id="18638-139">然後,您可以使用 指令定義機`set`密 。</span><span class="sxs-lookup"><span data-stu-id="18638-139">You can then define a secret with the `set` command.</span></span> <span data-ttu-id="18638-140">例如：</span><span class="sxs-lookup"><span data-stu-id="18638-140">For example:</span></span>

```dotnetcli
dotnet user-secrets set "Parent:ApiKey" "12345"
```

<span data-ttu-id="18638-141">前面的命令使`Parent:ApiKey`配置金鑰在具有`12345`值的開發人員工作站上可用。</span><span class="sxs-lookup"><span data-stu-id="18638-141">The preceding command makes the `Parent:ApiKey` configuration key available on a developer's workstation with the value `12345`.</span></span>

<span data-ttu-id="18638-142">有關建立、儲存和管理使用者機密的詳細資訊,請參閱[ASP.NET 核心文件中開發中應用機密的安全儲存](/aspnet/core/security/app-secrets)。</span><span class="sxs-lookup"><span data-stu-id="18638-142">For more information about creating, storing, and managing user secrets, see the [Safe storage of app secrets in development in ASP.NET Core](/aspnet/core/security/app-secrets) document.</span></span>

## <a name="environment-variables"></a><span data-ttu-id="18638-143">環境變數</span><span class="sxs-lookup"><span data-stu-id="18638-143">Environment variables</span></span>

<span data-ttu-id="18638-144">載入應用配置中的下一組值是系統的環境變數。</span><span class="sxs-lookup"><span data-stu-id="18638-144">The next set of values loaded into your app configuration is the system's environment variables.</span></span> <span data-ttu-id="18638-145">現在,您可以通過配置 API 存取系統的所有環境變數設定。</span><span class="sxs-lookup"><span data-stu-id="18638-145">All of your system's environment variable settings are now accessible to you through the configuration API.</span></span> <span data-ttu-id="18638-146">在應用內讀取時,分層值被拼平並由冒號字元分隔。</span><span class="sxs-lookup"><span data-stu-id="18638-146">Hierarchical values are flattened and separated by colon characters when read inside your app.</span></span> <span data-ttu-id="18638-147">但是,某些操作系統不允許冒號字元環境變數名稱。</span><span class="sxs-lookup"><span data-stu-id="18638-147">However, some operating systems don't allow the colon character environment variable names.</span></span> <span data-ttu-id="18638-148">ASP.NET Core 通過在存取具有雙下`__`劃線 ( ) 的值時將值轉換為冒號來解決此限制。</span><span class="sxs-lookup"><span data-stu-id="18638-148">ASP.NET Core addresses this limitation by converting values that have double-underscores (`__`) into a colon when they're accessed.</span></span> <span data-ttu-id="18638-149">上面`Parent:ApiKey`用戶機密部分中的值可以使用環境變數`Parent__ApiKey`覆蓋。</span><span class="sxs-lookup"><span data-stu-id="18638-149">The `Parent:ApiKey` value from the user secrets section above can be overridden with the environment variable `Parent__ApiKey`.</span></span>

## <a name="command-line-arguments"></a><span data-ttu-id="18638-150">命令列引數</span><span class="sxs-lookup"><span data-stu-id="18638-150">Command-line arguments</span></span>

<span data-ttu-id="18638-151">當應用啟動時,也可以作為命令列參數提供配置。</span><span class="sxs-lookup"><span data-stu-id="18638-151">Configuration can also be provided as command-line arguments when your app is started.</span></span> <span data-ttu-id="18638-152">使用雙虛線`--`( )`/`或前斜 杠 ( ) 表示法來指示要設定的設定值的名稱和要配置的值。</span><span class="sxs-lookup"><span data-stu-id="18638-152">Use the double-dash (`--`) or forward-slash (`/`) notation to indicate the name of the configuration value to set and the value to be configured.</span></span> <span data-ttu-id="18638-153">語法類似於以下指令:</span><span class="sxs-lookup"><span data-stu-id="18638-153">The syntax resembles the following commands:</span></span>

```dotnetcli
dotnet run CommandLineKey1=value1 --CommandLineKey2=value2 /CommandLineKey3=value3
dotnet run --CommandLineKey1 value1 /CommandLineKey2 value2
dotnet run Parent:ApiKey=67890
```

## <a name="the-return-of-webconfig"></a><span data-ttu-id="18638-154">Web.config 的回歸</span><span class="sxs-lookup"><span data-stu-id="18638-154">The return of web.config</span></span>

<span data-ttu-id="18638-155">如果您將應用部署到 IIS 上的 Windows,則*Web.config*檔仍會配置 IIS 來管理你的應用。</span><span class="sxs-lookup"><span data-stu-id="18638-155">If you've deployed your app to Windows on IIS, the *web.config* file still configures IIS to manage your app.</span></span> <span data-ttu-id="18638-156">默認情況下,IIS會添加對 ASP.NET核心模組 (ANCM) 的引用。</span><span class="sxs-lookup"><span data-stu-id="18638-156">By default, IIS adds a reference to the ASP.NET Core Module (ANCM).</span></span> <span data-ttu-id="18638-157">ANCM 是一個本機 IIS 模組,用於託管您的應用,以代替 Kestrel Web 伺服器。</span><span class="sxs-lookup"><span data-stu-id="18638-157">ANCM is a native IIS module that hosts your app in place of the Kestrel web server.</span></span> <span data-ttu-id="18638-158">此*Web.config*部份類似於以下 XML 標籤:</span><span class="sxs-lookup"><span data-stu-id="18638-158">This *web.config* section resembles the following XML markup:</span></span>

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

<span data-ttu-id="18638-159">可以通過嵌`environmentVariables`套 元素中的元素來定義特定於`aspNetCore`應用的 配置。</span><span class="sxs-lookup"><span data-stu-id="18638-159">App-specific configuration can be defined by nesting an `environmentVariables` element in the `aspNetCore` element.</span></span> <span data-ttu-id="18638-160">本節中定義的值作為環境變數呈現給ASP.NET核心應用。</span><span class="sxs-lookup"><span data-stu-id="18638-160">The values defined in this section are presented to the ASP.NET Core app as environment variables.</span></span> <span data-ttu-id="18638-161">環境變數在應用啟動期間適當載入。</span><span class="sxs-lookup"><span data-stu-id="18638-161">The environment variables load appropriately during that segment of app startup.</span></span>

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

## <a name="read-configuration-in-the-app"></a><span data-ttu-id="18638-162">讀取應用程式中的設定</span><span class="sxs-lookup"><span data-stu-id="18638-162">Read configuration in the app</span></span>

<span data-ttu-id="18638-163">ASP.NET核心透過<xref:Microsoft.Extensions.Configuration.IConfiguration>介面提供應用配置。</span><span class="sxs-lookup"><span data-stu-id="18638-163">ASP.NET Core provides app configuration through the <xref:Microsoft.Extensions.Configuration.IConfiguration> interface.</span></span> <span data-ttu-id="18638-164">此配置介面應由 Blazor 元件、Blazor 頁面以及需要存取配置的任何其他ASP.NET Core 託管類請求。</span><span class="sxs-lookup"><span data-stu-id="18638-164">This configuration interface should be requested by your Blazor components, Blazor pages, and any other ASP.NET Core-managed class that needs access to configuration.</span></span> <span data-ttu-id="18638-165">ASP.NET核心框架將自動填充此介面,並配置了前面配置的已解決配置。</span><span class="sxs-lookup"><span data-stu-id="18638-165">The ASP.NET Core framework will automatically populate this interface with the resolved configuration configured earlier.</span></span> <span data-ttu-id="18638-166">在 Blazor 頁或元件的 Razor 標記`IConfiguration`上,可以在 *.razor*檔案`@inject`頂部向物件注入指令,如下所示:</span><span class="sxs-lookup"><span data-stu-id="18638-166">On a Blazor page or a component's Razor markup, you can inject the `IConfiguration` object with an `@inject` directive at the top of the *.razor* file like this:</span></span>

```razor
@inject IConfiguration Configuration
```

<span data-ttu-id="18638-167">在前面的語句使`IConfiguration`該物件`Configuration`作為 變數在整個 Razor 範本的其餘部分中可用。</span><span class="sxs-lookup"><span data-stu-id="18638-167">This preceding statement makes the `IConfiguration` object available as the `Configuration` variable throughout the rest of the Razor template.</span></span>

<span data-ttu-id="18638-168">可以通過指定為索引器參數尋求的設定設定層次結構來讀取各個配置設定:</span><span class="sxs-lookup"><span data-stu-id="18638-168">Individual configuration settings can be read by specifying the configuration setting hierarchy sought as an indexer parameter:</span></span>

```csharp
var mySetting = Configuration["section1:key0"];
```

<span data-ttu-id="18638-169">可以使用方法<xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A>檢索特定位置的密鑰集合,其語法類似`GetSection("section1")`於從前面的示例中檢索第 1 節的配置,從而獲取整個配置部分。</span><span class="sxs-lookup"><span data-stu-id="18638-169">You can fetch entire configuration sections by using the <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> method to retrieve a collection of keys at a specific location with a syntax similar to `GetSection("section1")` to retrieve the configuration for section1 from the earlier example.</span></span>

## <a name="strongly-typed-configuration"></a><span data-ttu-id="18638-170">強類型設定</span><span class="sxs-lookup"><span data-stu-id="18638-170">Strongly typed configuration</span></span>

<span data-ttu-id="18638-171">使用 Web 窗體,可以<xref:System.Configuration.ConfigurationSection>建立從 類型和相關類型繼承的強類型配置類型。</span><span class="sxs-lookup"><span data-stu-id="18638-171">With Web Forms, it was possible to create a strongly typed configuration type that inherited from the <xref:System.Configuration.ConfigurationSection> type and associated types.</span></span> <span data-ttu-id="18638-172">A`ConfigurationSection`允許您為這些配置值配置某些業務規則和處理。</span><span class="sxs-lookup"><span data-stu-id="18638-172">A `ConfigurationSection` allowed you to configure some business rules and processing for those configuration values.</span></span>

<span data-ttu-id="18638-173">在ASP.NET Core 中,您可以指定將接收配置值的類層次結構。</span><span class="sxs-lookup"><span data-stu-id="18638-173">In ASP.NET Core, you can specify a class hierarchy that will receive the configuration values.</span></span> <span data-ttu-id="18638-174">這些類:</span><span class="sxs-lookup"><span data-stu-id="18638-174">These classes:</span></span>

* <span data-ttu-id="18638-175">不需要從父類繼承。</span><span class="sxs-lookup"><span data-stu-id="18638-175">Don't need to inherit from a parent class.</span></span>
* <span data-ttu-id="18638-176">應包含`public`與要捕獲的配置結構的屬性匹配的屬性和類型引用的屬性。</span><span class="sxs-lookup"><span data-stu-id="18638-176">Should include `public` properties that match the properties and type references for the configuration structure you wish to capture.</span></span>

<span data-ttu-id="18638-177">對於前面的*appsettings.json*範例,您可以定義以下類來擷取這些值:</span><span class="sxs-lookup"><span data-stu-id="18638-177">For the earlier *appsettings.json* sample, you could define the following classes to capture the values:</span></span>

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

<span data-ttu-id="18638-178">可以通過將以下行添加`Startup.ConfigureServices`到 方法來填充此類層次結構:</span><span class="sxs-lookup"><span data-stu-id="18638-178">This class hierarchy can be populated by adding the following line to the `Startup.ConfigureServices` method:</span></span>

```csharp
services.Configure<MyConfig>(Configuration);
```

<span data-ttu-id="18638-179">在應用的其餘部分中,您可以將輸入參數添加到類或類型`@inject``IOptions<MyConfig>`Razor 範本中的指令,以接收強類型配置設置。</span><span class="sxs-lookup"><span data-stu-id="18638-179">In the rest of the app, you can add an input parameter to classes or an `@inject` directive in Razor templates of type `IOptions<MyConfig>` to receive the strongly typed configuration settings.</span></span> <span data-ttu-id="18638-180">該`IOptions<MyConfig>.Value`屬性將生成`MyConfig`從 配置設置填充的值。</span><span class="sxs-lookup"><span data-stu-id="18638-180">The `IOptions<MyConfig>.Value` property will yield the `MyConfig` value populated from the configuration settings.</span></span>

```razor
@inject IOptions<MyConfig> options
@code {
    var MyConfiguration = options.Value;
    var theSetting = MyConfiguration.section1.key0;
}
```

<span data-ttu-id="18638-181">關於選項功能的詳細資訊,請參考[ASP.NET 核心文件中的選項模式](/aspnet/core/fundamentals/configuration/options#options-interfaces)。</span><span class="sxs-lookup"><span data-stu-id="18638-181">More information about the Options feature can be found in the [Options pattern in ASP.NET Core](/aspnet/core/fundamentals/configuration/options#options-interfaces) document.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="18638-182">[前一個](middleware.md)
>[下一個](security-authentication-authorization.md)</span><span class="sxs-lookup"><span data-stu-id="18638-182">[Previous](middleware.md)
[Next](security-authentication-authorization.md)</span></span>
