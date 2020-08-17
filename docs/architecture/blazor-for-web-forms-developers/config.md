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
# <a name="app-configuration"></a><span data-ttu-id="3f19c-103">應用程式設定</span><span class="sxs-lookup"><span data-stu-id="3f19c-103">App configuration</span></span>

<span data-ttu-id="3f19c-104">在 Web Form 中載入應用程式設定的主要方式，是在伺服器上 *web.config* 檔案中的專案， &mdash; 或 *web.config*所參考的相關設定檔案。您可以使用靜態 `ConfigurationManager` 物件來與應用程式設定、資料存放庫連接字串，以及新增到應用程式中的其他擴充設定提供者互動。</span><span class="sxs-lookup"><span data-stu-id="3f19c-104">The primary way to load app configuration in Web Forms is with entries in the *web.config* file&mdash;either on the server or a related configuration file referenced by *web.config*. You can use the static `ConfigurationManager` object to interact with app settings, data repository connection strings, and other extended configuration providers that are added into the app.</span></span> <span data-ttu-id="3f19c-105">通常會查看與應用程式設定的互動，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="3f19c-105">It's typical to see interactions with app configuration as seen in the following code:</span></span>

```csharp
var configurationValue = ConfigurationManager.AppSettings["ConfigurationSettingName"];
var connectionString = ConfigurationManager.ConnectionStrings["MyDatabaseConnectionName"].ConnectionString;
```

<span data-ttu-id="3f19c-106">Blazor如果您的應用程式是裝載在 WINDOWS IIS 伺服器上，使用 ASP.NET Core 和伺服器端時，可能會出現*web.config*檔案。</span><span class="sxs-lookup"><span data-stu-id="3f19c-106">With ASP.NET Core and server-side Blazor, the *web.config* file MAY be present if your app is hosted on a Windows IIS server.</span></span> <span data-ttu-id="3f19c-107">但是，不 `ConfigurationManager` 會與此設定互動，而且您可以從其他來源接收更多結構化的應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="3f19c-107">However, there's no `ConfigurationManager` interaction with this configuration, and you can receive more structured app configuration from other sources.</span></span> <span data-ttu-id="3f19c-108">讓我們看看如何收集設定，以及您如何仍可以從 *web.config* 檔案存取設定資訊。</span><span class="sxs-lookup"><span data-stu-id="3f19c-108">Let's take a look at how configuration is gathered and how you can still access configuration information from a *web.config* file.</span></span>

## <a name="configuration-sources"></a><span data-ttu-id="3f19c-109">組態來源</span><span class="sxs-lookup"><span data-stu-id="3f19c-109">Configuration sources</span></span>

<span data-ttu-id="3f19c-110">ASP.NET Core 辨識您的應用程式有許多設定來源可供使用。</span><span class="sxs-lookup"><span data-stu-id="3f19c-110">ASP.NET Core recognizes there are many configuration sources you may want to use for your app.</span></span> <span data-ttu-id="3f19c-111">根據預設，架構會嘗試為您提供這些功能的最佳功能。</span><span class="sxs-lookup"><span data-stu-id="3f19c-111">The framework attempts to offer you the best of these features by default.</span></span> <span data-ttu-id="3f19c-112">ASP.NET Core 會從這些不同的來源讀取和匯總設定。</span><span class="sxs-lookup"><span data-stu-id="3f19c-112">Configuration is read and aggregated from these various sources by ASP.NET Core.</span></span> <span data-ttu-id="3f19c-113">針對相同設定索引鍵，稍後載入的值會優先于較早的值。</span><span class="sxs-lookup"><span data-stu-id="3f19c-113">Later loaded values for the same configuration key take precedence over earlier values.</span></span>

<span data-ttu-id="3f19c-114">ASP.NET Core 是專為雲端感知而設計，可讓操作員和開發人員更輕鬆地設定應用程式。</span><span class="sxs-lookup"><span data-stu-id="3f19c-114">ASP.NET Core was designed to be cloud-aware and to make configuration of apps easier for both operators and developers.</span></span> <span data-ttu-id="3f19c-115">ASP.NET Core 可感知環境，並知道它是否正在您的 `Production` 或環境中執行 `Development` 。</span><span class="sxs-lookup"><span data-stu-id="3f19c-115">ASP.NET Core is environment-aware and knows if it's running in your `Production` or `Development` environment.</span></span> <span data-ttu-id="3f19c-116">環境指標是在 `ASPNETCORE_ENVIRONMENT` 系統內容變數中設定。</span><span class="sxs-lookup"><span data-stu-id="3f19c-116">The environment indicator is set in the `ASPNETCORE_ENVIRONMENT` system environment variable.</span></span> <span data-ttu-id="3f19c-117">如果未設定任何值，則應用程式會預設為在 `Production` 環境中執行。</span><span class="sxs-lookup"><span data-stu-id="3f19c-117">If no value is configured, the app defaults to running in the `Production` environment.</span></span>

<span data-ttu-id="3f19c-118">您的應用程式可以根據環境的名稱，從數個來源觸發和新增設定。</span><span class="sxs-lookup"><span data-stu-id="3f19c-118">Your app can trigger and add configuration from several sources based on the environment's name.</span></span> <span data-ttu-id="3f19c-119">依預設，會依列出的順序從下列資源載入設定：</span><span class="sxs-lookup"><span data-stu-id="3f19c-119">By default, configuration is loaded from the following resources in the order listed:</span></span>

1. <span data-ttu-id="3f19c-120">檔案*上的appsettings.js* （如果有的話）</span><span class="sxs-lookup"><span data-stu-id="3f19c-120">*appsettings.json* file, if present</span></span>
1. <span data-ttu-id="3f19c-121">*appsettings。{ENVIRONMENT_NAME}. json* 檔案（如果有的話）</span><span class="sxs-lookup"><span data-stu-id="3f19c-121">*appsettings.{ENVIRONMENT_NAME}.json* file, if present</span></span>
1. <span data-ttu-id="3f19c-122">磁片上的使用者秘密檔案（如果有的話）</span><span class="sxs-lookup"><span data-stu-id="3f19c-122">User secrets file on disk, if present</span></span>
1. <span data-ttu-id="3f19c-123">環境變數</span><span class="sxs-lookup"><span data-stu-id="3f19c-123">Environment variables</span></span>
1. <span data-ttu-id="3f19c-124">命令列引數</span><span class="sxs-lookup"><span data-stu-id="3f19c-124">Command-line arguments</span></span>

## <a name="appsettingsjson-format-and-access"></a><span data-ttu-id="3f19c-125">格式和存取 appsettings.js</span><span class="sxs-lookup"><span data-stu-id="3f19c-125">appsettings.json format and access</span></span>

<span data-ttu-id="3f19c-126">檔案 \* 上的appsettings.js\* 可以使用結構化的值（如下列 JSON）進行階層處理：</span><span class="sxs-lookup"><span data-stu-id="3f19c-126">The *appsettings.json* file can be hierarchical with values structured like the following JSON:</span></span>

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

<span data-ttu-id="3f19c-127">當您看到上述的 JSON 時，設定系統會將子值壓平合併，並參考其完整階層式路徑。</span><span class="sxs-lookup"><span data-stu-id="3f19c-127">When presented with the preceding JSON, the configuration system flattens child values and references their fully qualified hierarchical paths.</span></span> <span data-ttu-id="3f19c-128">冒號 (`:`) 字元分隔階層中的每個屬性。</span><span class="sxs-lookup"><span data-stu-id="3f19c-128">A colon (`:`) character separates each property in the hierarchy.</span></span> <span data-ttu-id="3f19c-129">例如，設定索引鍵會 `section1:key0` 存取 `section1` 物件常值的 `key0` 值。</span><span class="sxs-lookup"><span data-stu-id="3f19c-129">For example, the configuration key `section1:key0` accesses the `section1` object literal's `key0` value.</span></span>

## <a name="user-secrets"></a><span data-ttu-id="3f19c-130">使用者秘密</span><span class="sxs-lookup"><span data-stu-id="3f19c-130">User secrets</span></span>

<span data-ttu-id="3f19c-131">使用者密碼為：</span><span class="sxs-lookup"><span data-stu-id="3f19c-131">User secrets are:</span></span>

* <span data-ttu-id="3f19c-132">儲存在開發人員工作站上的 JSON 檔案中，位於應用程式開發資料夾外部的設定值。</span><span class="sxs-lookup"><span data-stu-id="3f19c-132">Configuration values that are stored in a JSON file on the developer's workstation, outside of the app development folder.</span></span>
* <span data-ttu-id="3f19c-133">只有在環境中執行時才會載入 `Development` 。</span><span class="sxs-lookup"><span data-stu-id="3f19c-133">Only loaded when running in the `Development` environment.</span></span>
* <span data-ttu-id="3f19c-134">與特定應用程式相關聯。</span><span class="sxs-lookup"><span data-stu-id="3f19c-134">Associated with a specific app.</span></span>
* <span data-ttu-id="3f19c-135">使用 .NET Core CLI 的命令來管理 `user-secrets` 。</span><span class="sxs-lookup"><span data-stu-id="3f19c-135">Managed with the .NET Core CLI's `user-secrets` command.</span></span>

<span data-ttu-id="3f19c-136">藉由執行下列命令，為您的應用程式設定秘密儲存體 `user-secrets` ：</span><span class="sxs-lookup"><span data-stu-id="3f19c-136">Configure your app for secrets storage by executing the `user-secrets` command:</span></span>

```dotnetcli
dotnet user-secrets init
```

<span data-ttu-id="3f19c-137">上述命令會將 `UserSecretsId` 元素新增至專案檔。</span><span class="sxs-lookup"><span data-stu-id="3f19c-137">The preceding command adds a `UserSecretsId` element to the project file.</span></span> <span data-ttu-id="3f19c-138">元素包含 GUID，用來將秘密與應用程式產生關聯。</span><span class="sxs-lookup"><span data-stu-id="3f19c-138">The element contains a GUID, which is used to associate secrets with the app.</span></span> <span data-ttu-id="3f19c-139">然後，您可以使用命令來定義秘密 `set` 。</span><span class="sxs-lookup"><span data-stu-id="3f19c-139">You can then define a secret with the `set` command.</span></span> <span data-ttu-id="3f19c-140">例如：</span><span class="sxs-lookup"><span data-stu-id="3f19c-140">For example:</span></span>

```dotnetcli
dotnet user-secrets set "Parent:ApiKey" "12345"
```

<span data-ttu-id="3f19c-141">上述命令可讓 `Parent:ApiKey` 開發人員工作站上的設定金鑰具有值 `12345` 。</span><span class="sxs-lookup"><span data-stu-id="3f19c-141">The preceding command makes the `Parent:ApiKey` configuration key available on a developer's workstation with the value `12345`.</span></span>

<span data-ttu-id="3f19c-142">如需有關建立、儲存和管理使用者密碼的詳細資訊，請參閱 [ASP.NET Core 檔中的開發應用程式秘密的安全儲存](/aspnet/core/security/app-secrets) 。</span><span class="sxs-lookup"><span data-stu-id="3f19c-142">For more information about creating, storing, and managing user secrets, see the [Safe storage of app secrets in development in ASP.NET Core](/aspnet/core/security/app-secrets) document.</span></span>

## <a name="environment-variables"></a><span data-ttu-id="3f19c-143">環境變數</span><span class="sxs-lookup"><span data-stu-id="3f19c-143">Environment variables</span></span>

<span data-ttu-id="3f19c-144">下一組載入您應用程式設定的值是系統的環境變數。</span><span class="sxs-lookup"><span data-stu-id="3f19c-144">The next set of values loaded into your app configuration is the system's environment variables.</span></span> <span data-ttu-id="3f19c-145">您現在可以透過設定 API 存取所有系統的環境變數設定。</span><span class="sxs-lookup"><span data-stu-id="3f19c-145">All of your system's environment variable settings are now accessible to you through the configuration API.</span></span> <span data-ttu-id="3f19c-146">在您的應用程式內讀取時，階層值會簡維並以冒號字元分隔。</span><span class="sxs-lookup"><span data-stu-id="3f19c-146">Hierarchical values are flattened and separated by colon characters when read inside your app.</span></span> <span data-ttu-id="3f19c-147">不過，某些作業系統不允許冒號字元環境變數名稱。</span><span class="sxs-lookup"><span data-stu-id="3f19c-147">However, some operating systems don't allow the colon character environment variable names.</span></span> <span data-ttu-id="3f19c-148">ASP.NET Core 藉由將具有雙底線 () 的值，轉換為存取時的冒號，來解決這項限制 `__` 。</span><span class="sxs-lookup"><span data-stu-id="3f19c-148">ASP.NET Core addresses this limitation by converting values that have double-underscores (`__`) into a colon when they're accessed.</span></span> <span data-ttu-id="3f19c-149">您 `Parent:ApiKey` 可以使用環境變數來覆寫上述使用者秘密區段中的值 `Parent__ApiKey` 。</span><span class="sxs-lookup"><span data-stu-id="3f19c-149">The `Parent:ApiKey` value from the user secrets section above can be overridden with the environment variable `Parent__ApiKey`.</span></span>

## <a name="command-line-arguments"></a><span data-ttu-id="3f19c-150">命令列引數</span><span class="sxs-lookup"><span data-stu-id="3f19c-150">Command-line arguments</span></span>

<span data-ttu-id="3f19c-151">當您的應用程式啟動時，也可以將設定提供為命令列引數。</span><span class="sxs-lookup"><span data-stu-id="3f19c-151">Configuration can also be provided as command-line arguments when your app is started.</span></span> <span data-ttu-id="3f19c-152">使用雙虛線 (`--`) 或斜線 (`/`) 標記法來表示要設定的設定值名稱以及要設定的值。</span><span class="sxs-lookup"><span data-stu-id="3f19c-152">Use the double-dash (`--`) or forward-slash (`/`) notation to indicate the name of the configuration value to set and the value to be configured.</span></span> <span data-ttu-id="3f19c-153">語法類似于下列命令：</span><span class="sxs-lookup"><span data-stu-id="3f19c-153">The syntax resembles the following commands:</span></span>

```dotnetcli
dotnet run CommandLineKey1=value1 --CommandLineKey2=value2 /CommandLineKey3=value3
dotnet run --CommandLineKey1 value1 /CommandLineKey2 value2
dotnet run Parent:ApiKey=67890
```

## <a name="the-return-of-webconfig"></a><span data-ttu-id="3f19c-154">傳回 web.config</span><span class="sxs-lookup"><span data-stu-id="3f19c-154">The return of web.config</span></span>

<span data-ttu-id="3f19c-155">如果您已在 IIS 上將應用程式部署至 Windows， *web.config* 檔案仍會設定 iis 來管理您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="3f19c-155">If you've deployed your app to Windows on IIS, the *web.config* file still configures IIS to manage your app.</span></span> <span data-ttu-id="3f19c-156">根據預設，IIS 會將參考新增至 ASP.NET Core 模組 (ANCM) 。</span><span class="sxs-lookup"><span data-stu-id="3f19c-156">By default, IIS adds a reference to the ASP.NET Core Module (ANCM).</span></span> <span data-ttu-id="3f19c-157">ANCM 是原生 IIS 模組，可裝載您的應用程式來取代 Kestrel web 伺服器。</span><span class="sxs-lookup"><span data-stu-id="3f19c-157">ANCM is a native IIS module that hosts your app in place of the Kestrel web server.</span></span> <span data-ttu-id="3f19c-158">此 *web.config* 區段類似下列 XML 標記：</span><span class="sxs-lookup"><span data-stu-id="3f19c-158">This *web.config* section resembles the following XML markup:</span></span>

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

<span data-ttu-id="3f19c-159">您可以藉由將專案中的元素嵌套來定義應用程式特定的設定 `environmentVariables` `aspNetCore` 。</span><span class="sxs-lookup"><span data-stu-id="3f19c-159">App-specific configuration can be defined by nesting an `environmentVariables` element in the `aspNetCore` element.</span></span> <span data-ttu-id="3f19c-160">此區段中定義的值會以環境變數的形式呈現給 ASP.NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="3f19c-160">The values defined in this section are presented to the ASP.NET Core app as environment variables.</span></span> <span data-ttu-id="3f19c-161">環境變數會在應用程式啟動的那段期間適當地載入。</span><span class="sxs-lookup"><span data-stu-id="3f19c-161">The environment variables load appropriately during that segment of app startup.</span></span>

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

## <a name="read-configuration-in-the-app"></a><span data-ttu-id="3f19c-162">讀取應用程式中的設定</span><span class="sxs-lookup"><span data-stu-id="3f19c-162">Read configuration in the app</span></span>

<span data-ttu-id="3f19c-163">ASP.NET Core 透過介面提供應用程式設定 <xref:Microsoft.Extensions.Configuration.IConfiguration> 。</span><span class="sxs-lookup"><span data-stu-id="3f19c-163">ASP.NET Core provides app configuration through the <xref:Microsoft.Extensions.Configuration.IConfiguration> interface.</span></span> <span data-ttu-id="3f19c-164">Blazor需要存取設定的元件、 Blazor 頁面以及任何其他 ASP.NET Core 管理的類別，都應要求此設定介面。</span><span class="sxs-lookup"><span data-stu-id="3f19c-164">This configuration interface should be requested by your Blazor components, Blazor pages, and any other ASP.NET Core-managed class that needs access to configuration.</span></span> <span data-ttu-id="3f19c-165">ASP.NET Core framework 會自動將先前設定的已解決設定填入此介面。</span><span class="sxs-lookup"><span data-stu-id="3f19c-165">The ASP.NET Core framework will automatically populate this interface with the resolved configuration configured earlier.</span></span> <span data-ttu-id="3f19c-166">在 Blazor 頁面或元件的 razor 標記上，您可以在 razor 檔案 `IConfiguration` 的頂端插入具有指示詞的物件，如下所 `@inject` 示： *.razor*</span><span class="sxs-lookup"><span data-stu-id="3f19c-166">On a Blazor page or a component's Razor markup, you can inject the `IConfiguration` object with an `@inject` directive at the top of the *.razor* file like this:</span></span>

```razor
@inject IConfiguration Configuration
```

<span data-ttu-id="3f19c-167">上述語句可讓 `IConfiguration` 物件在 `Configuration` Razor 範本的其餘部分都可作為變數使用。</span><span class="sxs-lookup"><span data-stu-id="3f19c-167">This preceding statement makes the `IConfiguration` object available as the `Configuration` variable throughout the rest of the Razor template.</span></span>

<span data-ttu-id="3f19c-168">您可以藉由指定搜尋為索引子參數的設定設定階層，來讀取個別的設定設定：</span><span class="sxs-lookup"><span data-stu-id="3f19c-168">Individual configuration settings can be read by specifying the configuration setting hierarchy sought as an indexer parameter:</span></span>

```csharp
var mySetting = Configuration["section1:key0"];
```

<span data-ttu-id="3f19c-169">您可以使用方法來提取整個設定區段，方法是使用 <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> 類似的語法， `GetSection("section1")` 從先前的範例中取出 section1 的設定，以取得特定位置的索引鍵集合。</span><span class="sxs-lookup"><span data-stu-id="3f19c-169">You can fetch entire configuration sections by using the <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> method to retrieve a collection of keys at a specific location with a syntax similar to `GetSection("section1")` to retrieve the configuration for section1 from the earlier example.</span></span>

## <a name="strongly-typed-configuration"></a><span data-ttu-id="3f19c-170">強型別設定</span><span class="sxs-lookup"><span data-stu-id="3f19c-170">Strongly typed configuration</span></span>

<span data-ttu-id="3f19c-171">有了 Web Form，就可以建立繼承自 <xref:System.Configuration.ConfigurationSection> 型別和相關聯類型的強型別設定型別。</span><span class="sxs-lookup"><span data-stu-id="3f19c-171">With Web Forms, it was possible to create a strongly typed configuration type that inherited from the <xref:System.Configuration.ConfigurationSection> type and associated types.</span></span> <span data-ttu-id="3f19c-172">`ConfigurationSection`允許您設定某些商務規則，以及處理這些設定值。</span><span class="sxs-lookup"><span data-stu-id="3f19c-172">A `ConfigurationSection` allowed you to configure some business rules and processing for those configuration values.</span></span>

<span data-ttu-id="3f19c-173">在 ASP.NET Core 中，您可以指定將接收設定值的類別階層。</span><span class="sxs-lookup"><span data-stu-id="3f19c-173">In ASP.NET Core, you can specify a class hierarchy that will receive the configuration values.</span></span> <span data-ttu-id="3f19c-174">這些類別：</span><span class="sxs-lookup"><span data-stu-id="3f19c-174">These classes:</span></span>

* <span data-ttu-id="3f19c-175">不需要繼承自父類別。</span><span class="sxs-lookup"><span data-stu-id="3f19c-175">Don't need to inherit from a parent class.</span></span>
* <span data-ttu-id="3f19c-176">應包含 `public` 符合您想要捕捉的設定結構之屬性和類型參考的屬性。</span><span class="sxs-lookup"><span data-stu-id="3f19c-176">Should include `public` properties that match the properties and type references for the configuration structure you wish to capture.</span></span>

<span data-ttu-id="3f19c-177">針對先前的 *appsettings.js* 範例，您可以定義下列類別來捕捉值：</span><span class="sxs-lookup"><span data-stu-id="3f19c-177">For the earlier *appsettings.json* sample, you could define the following classes to capture the values:</span></span>

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

<span data-ttu-id="3f19c-178">您可以藉由將下列程式程式碼加入至方法來填入這個類別階層 `Startup.ConfigureServices` ：</span><span class="sxs-lookup"><span data-stu-id="3f19c-178">This class hierarchy can be populated by adding the following line to the `Startup.ConfigureServices` method:</span></span>

```csharp
services.Configure<MyConfig>(Configuration);
```

<span data-ttu-id="3f19c-179">在應用程式的其餘部分，您可以在類型的 Razor 範本中，將輸入參數加入至類別或指示 `@inject` `IOptions<MyConfig>` 詞，以接收強型別設定。</span><span class="sxs-lookup"><span data-stu-id="3f19c-179">In the rest of the app, you can add an input parameter to classes or an `@inject` directive in Razor templates of type `IOptions<MyConfig>` to receive the strongly typed configuration settings.</span></span> <span data-ttu-id="3f19c-180">`IOptions<MyConfig>.Value`屬性將會產生 `MyConfig` 從設定中填入的值。</span><span class="sxs-lookup"><span data-stu-id="3f19c-180">The `IOptions<MyConfig>.Value` property will yield the `MyConfig` value populated from the configuration settings.</span></span>

```razor
@inject IOptions<MyConfig> options
@code {
    var MyConfiguration = options.Value;
    var theSetting = MyConfiguration.section1.key0;
}
```

<span data-ttu-id="3f19c-181">您可以在 ASP.NET Core 檔的 [選項模式](/aspnet/core/fundamentals/configuration/options#options-interfaces) 中找到選項功能的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="3f19c-181">More information about the Options feature can be found in the [Options pattern in ASP.NET Core](/aspnet/core/fundamentals/configuration/options#options-interfaces) document.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="3f19c-182">[上一個](middleware.md) 
>[下一步](security-authentication-authorization.md)</span><span class="sxs-lookup"><span data-stu-id="3f19c-182">[Previous](middleware.md)
[Next](security-authentication-authorization.md)</span></span>
