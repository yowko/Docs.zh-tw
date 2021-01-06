---
title: .NET 中的設定提供者
description: 瞭解如何使用設定提供者 API 來設定 .NET 應用程式。
author: IEvangelist
ms.author: dapine
ms.date: 12/04/2020
ms.openlocfilehash: 036eb403318200bc0ae1d93e2c7cf9d074cb0bfb
ms.sourcegitcommit: 88fbb019b84c2d044d11fb4f6004aec07f2b25b1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97899444"
---
# <a name="configuration-providers-in-net"></a><span data-ttu-id="4e026-103">.NET 中的設定提供者</span><span class="sxs-lookup"><span data-stu-id="4e026-103">Configuration providers in .NET</span></span>

<span data-ttu-id="4e026-104">您可以使用設定提供者，在 .NET 中進行設定。</span><span class="sxs-lookup"><span data-stu-id="4e026-104">Configuration in .NET is possible with configuration providers.</span></span> <span data-ttu-id="4e026-105">有數種類型的提供者依賴不同的設定來源。</span><span class="sxs-lookup"><span data-stu-id="4e026-105">There are several types of providers that rely on various configuration sources.</span></span> <span data-ttu-id="4e026-106">本文將詳細說明所有不同的設定提供者及其對應的來源。</span><span class="sxs-lookup"><span data-stu-id="4e026-106">This article details all of the different configuration providers and their corresponding sources.</span></span>

- [<span data-ttu-id="4e026-107">檔案設定提供者</span><span class="sxs-lookup"><span data-stu-id="4e026-107">File configuration provider</span></span>](#file-configuration-provider)
- [<span data-ttu-id="4e026-108">環境變數設定提供者</span><span class="sxs-lookup"><span data-stu-id="4e026-108">Environment variable configuration provider</span></span>](#environment-variable-configuration-provider)
- [<span data-ttu-id="4e026-109">命令列設定提供者</span><span class="sxs-lookup"><span data-stu-id="4e026-109">Command-line configuration provider</span></span>](#command-line-configuration-provider)
- [<span data-ttu-id="4e026-110">每個檔案的金鑰配置提供者</span><span class="sxs-lookup"><span data-stu-id="4e026-110">Key-per-file configuration provider</span></span>](#key-per-file-configuration-provider)
- [<span data-ttu-id="4e026-111">記憶體設定提供者</span><span class="sxs-lookup"><span data-stu-id="4e026-111">Memory configuration provider</span></span>](#memory-configuration-provider)

## <a name="file-configuration-provider"></a><span data-ttu-id="4e026-112">檔案設定提供者</span><span class="sxs-lookup"><span data-stu-id="4e026-112">File configuration provider</span></span>

<span data-ttu-id="4e026-113"><xref:Microsoft.Extensions.Configuration.FileConfigurationProvider> 是用於從檔案系統載入設定的基底類別。</span><span class="sxs-lookup"><span data-stu-id="4e026-113"><xref:Microsoft.Extensions.Configuration.FileConfigurationProvider> is the base class for loading configuration from the file system.</span></span> <span data-ttu-id="4e026-114">以下是衍生自的設定提供者 `FileConfigurationProvider` ：</span><span class="sxs-lookup"><span data-stu-id="4e026-114">The following configuration providers derive from `FileConfigurationProvider`:</span></span>

- [<span data-ttu-id="4e026-115">JSON 設定提供者</span><span class="sxs-lookup"><span data-stu-id="4e026-115">JSON configuration provider</span></span>](#json-configuration-provider)
- [<span data-ttu-id="4e026-116">XML 設定提供者</span><span class="sxs-lookup"><span data-stu-id="4e026-116">XML configuration provider</span></span>](#xml-configuration-provider)
- [<span data-ttu-id="4e026-117">INI 設定提供者</span><span class="sxs-lookup"><span data-stu-id="4e026-117">INI configuration provider</span></span>](#ini-configuration-provider)

### <a name="json-configuration-provider"></a><span data-ttu-id="4e026-118">JSON 設定提供者</span><span class="sxs-lookup"><span data-stu-id="4e026-118">JSON configuration provider</span></span>

<span data-ttu-id="4e026-119"><xref:Microsoft.Extensions.Configuration.Json.JsonConfigurationProvider>類別會從 JSON 檔案載入設定。</span><span class="sxs-lookup"><span data-stu-id="4e026-119">The <xref:Microsoft.Extensions.Configuration.Json.JsonConfigurationProvider> class loads configuration from a JSON file.</span></span> <span data-ttu-id="4e026-120">安裝 [`Microsoft.Extensions.Configuration.Json`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Json) NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="4e026-120">Install the [`Microsoft.Extensions.Configuration.Json`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Json) NuGet package.</span></span>

<span data-ttu-id="4e026-121">多載可以指定：</span><span class="sxs-lookup"><span data-stu-id="4e026-121">Overloads can specify:</span></span>

- <span data-ttu-id="4e026-122">檔案是否為選擇性</span><span class="sxs-lookup"><span data-stu-id="4e026-122">Whether the file is optional</span></span>
- <span data-ttu-id="4e026-123">檔案變更時是否要重載設定</span><span class="sxs-lookup"><span data-stu-id="4e026-123">Whether the configuration is reloaded if the file changes</span></span>

<span data-ttu-id="4e026-124">請考慮下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="4e026-124">Consider the following code:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="1-39,43-44" highlight="23-29":::

<span data-ttu-id="4e026-125">上述程式碼：</span><span class="sxs-lookup"><span data-stu-id="4e026-125">The preceding code:</span></span>

- <span data-ttu-id="4e026-126">清除方法中預設新增的所有現有設定提供者 <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])> 。</span><span class="sxs-lookup"><span data-stu-id="4e026-126">Clears all existing configuration providers that were added by default in the <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])> method.</span></span>
- <span data-ttu-id="4e026-127">設定 JSON 設定提供者，以將 *appsettings.js* 載入和  *appsettings*。 `Environment`具有下列選項的 *json* 檔案：</span><span class="sxs-lookup"><span data-stu-id="4e026-127">Configures the JSON configuration provider to load the *appsettings.json* and  *appsettings*.`Environment`.*json* files with the following options:</span></span>
  - <span data-ttu-id="4e026-128">`optional: true`：檔案是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="4e026-128">`optional: true`: The file is optional.</span></span>
  - <span data-ttu-id="4e026-129">`reloadOnChange: true` ：儲存變更時，會重載該檔案。</span><span class="sxs-lookup"><span data-stu-id="4e026-129">`reloadOnChange: true` : The file is reloaded when changes are saved.</span></span>

<span data-ttu-id="4e026-130">JSON 設定會由 [環境變數設定提供者](#environment-variable-configuration-provider) 和 [命令列設定提供者](#command-line-configuration-provider)中的設定覆寫。</span><span class="sxs-lookup"><span data-stu-id="4e026-130">The JSON settings are overridden by settings in the [Environment variables configuration provider](#environment-variable-configuration-provider) and the [Command-line configuration provider](#command-line-configuration-provider).</span></span>

<span data-ttu-id="4e026-131">具有各種設定的檔案範例 *appsettings.js* 如下所示：</span><span class="sxs-lookup"><span data-stu-id="4e026-131">An example *appsettings.json* file with various configuration settings follows:</span></span>

:::code language="json" source="snippets/configuration/console-json/appsettings.json":::

<span data-ttu-id="4e026-132">從 <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder> 實例，加入設定提供者之後，您可以呼叫 <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder.Build?displayProperty=nameWithType> 以取得 <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> 物件。</span><span class="sxs-lookup"><span data-stu-id="4e026-132">From the <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder> instance, after configuration providers have been added you can call <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder.Build?displayProperty=nameWithType> to get the <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> object.</span></span> <span data-ttu-id="4e026-133">設定根目錄表示設定階層的根。</span><span class="sxs-lookup"><span data-stu-id="4e026-133">The configuration root represents the root of a configuration hierarchy.</span></span> <span data-ttu-id="4e026-134">設定中的區段可以系結至 .NET 物件的實例，並在稍後透過相依性插入來提供 <xref:Microsoft.Extensions.Options.IOptions%601> 。</span><span class="sxs-lookup"><span data-stu-id="4e026-134">Sections from the configuration can be bound to instances of .NET objects, and later provided as <xref:Microsoft.Extensions.Options.IOptions%601> through dependency injection.</span></span>

<span data-ttu-id="4e026-135">請考慮 `TransientFaultHandlingOptions` 定義如下的記錄類型：</span><span class="sxs-lookup"><span data-stu-id="4e026-135">Consider the `TransientFaultHandlingOptions` record type defined as follows:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/TransientFaultHandlingOptions.cs":::

<span data-ttu-id="4e026-136">如需記錄類型的詳細資訊，請參閱 [c # 9 中的記錄類型](../../csharp/whats-new/csharp-9.md#record-types)。</span><span class="sxs-lookup"><span data-stu-id="4e026-136">For information on record types, see [Record types in C# 9](../../csharp/whats-new/csharp-9.md#record-types).</span></span>

<span data-ttu-id="4e026-137">下列程式碼會建立設定根目錄、將區段系結至 `TransientFaultHandlingOptions` 記錄類型，以及將系結值列印到主控台視窗：</span><span class="sxs-lookup"><span data-stu-id="4e026-137">The following code builds the configuration root, binds a section to the `TransientFaultHandlingOptions` record type, and prints the bound values to the console window:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="31-38":::

<span data-ttu-id="4e026-138">應用程式會寫入下列範例輸出：</span><span class="sxs-lookup"><span data-stu-id="4e026-138">The application would write the following sample output:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="40-42":::

### <a name="xml-configuration-provider"></a><span data-ttu-id="4e026-139">XML 設定提供者</span><span class="sxs-lookup"><span data-stu-id="4e026-139">XML configuration provider</span></span>

<span data-ttu-id="4e026-140"><xref:Microsoft.Extensions.Configuration.Xml.XmlConfigurationProvider>類別會在執行時間從 XML 檔案載入設定。</span><span class="sxs-lookup"><span data-stu-id="4e026-140">The <xref:Microsoft.Extensions.Configuration.Xml.XmlConfigurationProvider> class loads configuration from an XML file at runtime.</span></span> <span data-ttu-id="4e026-141">安裝 [`Microsoft.Extensions.Configuration.Xml`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Xml) NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="4e026-141">Install the [`Microsoft.Extensions.Configuration.Xml`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Xml) NuGet package.</span></span>

<span data-ttu-id="4e026-142">下列程式碼示範如何使用 XML 設定提供者來設定 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="4e026-142">The following code demonstrates configuration of XML files using the XML configuration provider.</span></span>

:::code language="csharp" source="snippets/configuration/console-xml/Program.cs" range="1-34,52,58-59" highlight="23-34":::

<span data-ttu-id="4e026-143">上述程式碼：</span><span class="sxs-lookup"><span data-stu-id="4e026-143">The preceding code:</span></span>

- <span data-ttu-id="4e026-144">清除方法中預設新增的所有現有設定提供者 <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])> 。</span><span class="sxs-lookup"><span data-stu-id="4e026-144">Clears all existing configuration providers that were added by default in the <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])> method.</span></span>
- <span data-ttu-id="4e026-145">設定 XML 設定提供者，以使用下列選項載入 *appsettings.xml* 和 *repeating-example.xml* 檔案：</span><span class="sxs-lookup"><span data-stu-id="4e026-145">Configures the XML configuration provider to load the *appsettings.xml* and *repeating-example.xml* files with the following options:</span></span>
  - <span data-ttu-id="4e026-146">`optional: true`：檔案是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="4e026-146">`optional: true`: The file is optional.</span></span>
  - <span data-ttu-id="4e026-147">`reloadOnChange: true` ：儲存變更時，會重載該檔案。</span><span class="sxs-lookup"><span data-stu-id="4e026-147">`reloadOnChange: true` : The file is reloaded when changes are saved.</span></span>
- <span data-ttu-id="4e026-148">設定環境變數設定提供者。</span><span class="sxs-lookup"><span data-stu-id="4e026-148">Configures the environment variables configuration provider.</span></span>
- <span data-ttu-id="4e026-149">如果指定的包含引數，則設定命令列設定提供者 `args` 。</span><span class="sxs-lookup"><span data-stu-id="4e026-149">Configures the command-line configuration provider if the given `args` contains arguments.</span></span>

<span data-ttu-id="4e026-150">[環境變數設定提供者](#environment-variable-configuration-provider)和[命令列設定提供者](#command-line-configuration-provider)中的設定會覆寫 XML 設定。</span><span class="sxs-lookup"><span data-stu-id="4e026-150">The XML settings are overridden by settings in the [Environment variables configuration provider](#environment-variable-configuration-provider) and the [Command-line configuration provider](#command-line-configuration-provider).</span></span>

<span data-ttu-id="4e026-151">具有各種設定的範例 *appsettings.xml* 檔案如下：</span><span class="sxs-lookup"><span data-stu-id="4e026-151">An example *appsettings.xml* file with various configuration settings follows:</span></span>

:::code language="xml" source="snippets/configuration/console-xml/appsettings.xml":::

<span data-ttu-id="4e026-152">若 `name` 屬性是用來區別元素，則可以重複那些使用相同元素名稱的元素：</span><span class="sxs-lookup"><span data-stu-id="4e026-152">Repeating elements that use the same element name work if the `name` attribute is used to distinguish the elements:</span></span>

:::code language="xml" source="snippets/configuration/console-xml/repeating-example.xml":::

<span data-ttu-id="4e026-153">下列程式碼會讀取先前的設定檔，並顯示金鑰和值：</span><span class="sxs-lookup"><span data-stu-id="4e026-153">The following code reads the previous configuration file and displays the keys and values:</span></span>

:::code language="csharp" source="snippets/configuration/console-xml/Program.cs" range="36-51":::

<span data-ttu-id="4e026-154">應用程式會寫入下列範例輸出：</span><span class="sxs-lookup"><span data-stu-id="4e026-154">The application would write the following sample output:</span></span>

:::code language="csharp" source="snippets/configuration/console-xml/Program.cs" range="53-57":::

<span data-ttu-id="4e026-155">屬性可用來提供值：</span><span class="sxs-lookup"><span data-stu-id="4e026-155">Attributes can be used to supply values:</span></span>

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
  <key attribute="value" />
  <section>
    <key attribute="value" />
  </section>
</configuration>
```

<span data-ttu-id="4e026-156">先前的設定檔會使用 `value` 載入下列機碼：</span><span class="sxs-lookup"><span data-stu-id="4e026-156">The previous configuration file loads the following keys with `value`:</span></span>

- `key:attribute`
- `section:key:attribute`

### <a name="ini-configuration-provider"></a><span data-ttu-id="4e026-157">INI 設定提供者</span><span class="sxs-lookup"><span data-stu-id="4e026-157">INI configuration provider</span></span>

<span data-ttu-id="4e026-158"><xref:Microsoft.Extensions.Configuration.Ini.IniConfigurationProvider>類別會在執行時間從 INI 檔案載入設定。</span><span class="sxs-lookup"><span data-stu-id="4e026-158">The <xref:Microsoft.Extensions.Configuration.Ini.IniConfigurationProvider> class loads configuration from an INI file at runtime.</span></span> <span data-ttu-id="4e026-159">安裝 [`Microsoft.Extensions.Configuration.Ini`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Ini)  NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="4e026-159">Install the [`Microsoft.Extensions.Configuration.Ini`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Ini)  NuGet package.</span></span>

<span data-ttu-id="4e026-160">下列程式碼會清除所有設定提供者，並新增 `IniConfigurationProvider` 包含兩個 INI 檔案的作為來源：</span><span class="sxs-lookup"><span data-stu-id="4e026-160">The following code clears all the configuration providers and adds the `IniConfigurationProvider` with two INI files as the source:</span></span>

:::code language="csharp" source="snippets/configuration/console-ini/Program.cs" range="1-37,44-45" highlight="24-30":::

<span data-ttu-id="4e026-161">具有各種設定的範例 *appsettings.ini* 檔案如下：</span><span class="sxs-lookup"><span data-stu-id="4e026-161">An example *appsettings.ini* file with various configuration settings follows:</span></span>

:::code language="ini" source="snippets/configuration/console-ini/appsettings.ini":::

<span data-ttu-id="4e026-162">下列程式碼會藉由將上述設定寫入主控台視窗來顯示上述設定：</span><span class="sxs-lookup"><span data-stu-id="4e026-162">The following code displays the preceding configuration settings by writing them to the console window:</span></span>

:::code language="csharp" source="snippets/configuration/console-ini/Program.cs" range="32-36":::

<span data-ttu-id="4e026-163">應用程式會寫入下列範例輸出：</span><span class="sxs-lookup"><span data-stu-id="4e026-163">The application would write the following sample output:</span></span>

:::code language="csharp" source="snippets/configuration/console-ini/Program.cs" range="38-43":::

## <a name="environment-variable-configuration-provider"></a><span data-ttu-id="4e026-164">環境變數設定提供者</span><span class="sxs-lookup"><span data-stu-id="4e026-164">Environment variable configuration provider</span></span>

<span data-ttu-id="4e026-165">使用預設設定時，會 <xref:Microsoft.Extensions.Configuration.EnvironmentVariables.EnvironmentVariablesConfigurationProvider> 從環境變數機碼值組載入設定，在讀取 *appsettings.js* *appsettings 之後。* `Environment`*. json* 和秘密管理員。</span><span class="sxs-lookup"><span data-stu-id="4e026-165">Using the default configuration, the <xref:Microsoft.Extensions.Configuration.EnvironmentVariables.EnvironmentVariablesConfigurationProvider> loads configuration from environment variable key-value pairs after reading *appsettings.json*, *appsettings.*`Environment`*.json*, and Secret manager.</span></span> <span data-ttu-id="4e026-166">因此，從環境讀取的索引鍵值會覆寫 appsettings *上從appsettings.js* 讀取的值 *。* `Environment`*. json* 和秘密管理員。</span><span class="sxs-lookup"><span data-stu-id="4e026-166">Therefore, key values read from the environment override values read from *appsettings.json*, *appsettings.*`Environment`*.json*, and Secret manager.</span></span>

<span data-ttu-id="4e026-167">`:`分隔符號不適用於所有平臺上的環境變數階層式索引鍵。</span><span class="sxs-lookup"><span data-stu-id="4e026-167">The `:` separator doesn't work with environment variable hierarchical keys on all platforms.</span></span> <span data-ttu-id="4e026-168">雙底線 (`__`) 會自動由所取代 `:` ，而且所有平臺都支援此功能。</span><span class="sxs-lookup"><span data-stu-id="4e026-168">The double underscore (`__`) is automatically replaced by a `:` and is supported by all platforms.</span></span> <span data-ttu-id="4e026-169">例如， `:` [Bash](https://linuxhint.com/bash-environment-variables)不支援分隔符號，但 `__` 為。</span><span class="sxs-lookup"><span data-stu-id="4e026-169">For example, the `:` separator is not supported by [Bash](https://linuxhint.com/bash-environment-variables), but `__` is.</span></span>

<span data-ttu-id="4e026-170">下列 `set` 命令：</span><span class="sxs-lookup"><span data-stu-id="4e026-170">The following `set` commands:</span></span>

- <span data-ttu-id="4e026-171">在 Windows 上設定上述範例的環境索引鍵和值。</span><span class="sxs-lookup"><span data-stu-id="4e026-171">Set the environment keys and values of the preceding example on Windows.</span></span>
- <span data-ttu-id="4e026-172">變更設定的預設值來進行測試。</span><span class="sxs-lookup"><span data-stu-id="4e026-172">Test the settings by changing them from their default values.</span></span> <span data-ttu-id="4e026-173">`dotnet run`命令必須在專案目錄中執行。</span><span class="sxs-lookup"><span data-stu-id="4e026-173">The `dotnet run` command must be run in the project directory.</span></span>

```dotnetcli
set SecretKey="Secret key from environment"
set TransientFaultHandlingOptions__Enabled="true"
set TransientFaultHandlingOptions__AutoRetryDelay="00:00:13"

dotnet run
```

<span data-ttu-id="4e026-174">先前的環境設定：</span><span class="sxs-lookup"><span data-stu-id="4e026-174">The preceding environment settings:</span></span>

- <span data-ttu-id="4e026-175">只會在從其設定的命令視窗啟動的進程中設定。</span><span class="sxs-lookup"><span data-stu-id="4e026-175">Are only set in processes launched from the command window they were set in.</span></span>
- <span data-ttu-id="4e026-176">使用 Visual Studio 啟動的 web 應用程式將無法讀取。</span><span class="sxs-lookup"><span data-stu-id="4e026-176">Won't be read by web apps launched with Visual Studio.</span></span>

<span data-ttu-id="4e026-177">您可以使用下列的 [setx](/windows-server/administration/windows-commands/setx) 命令，在 Windows 上設定環境機碼和值。</span><span class="sxs-lookup"><span data-stu-id="4e026-177">The following [setx](/windows-server/administration/windows-commands/setx) commands can be used to set the environment keys and values on Windows.</span></span> <span data-ttu-id="4e026-178">與不同 `set` 的 `setx` 是，設定會持續保存。</span><span class="sxs-lookup"><span data-stu-id="4e026-178">Unlike `set`, `setx` settings are persisted.</span></span> <span data-ttu-id="4e026-179">`/M` 設定系統內容中的變數。</span><span class="sxs-lookup"><span data-stu-id="4e026-179">`/M` sets the variable in the system environment.</span></span> <span data-ttu-id="4e026-180">如果 `/M` 未使用此參數，則會設定使用者環境變數。</span><span class="sxs-lookup"><span data-stu-id="4e026-180">If the `/M` switch isn't used, a user environment variable is set.</span></span>

```dotnetcli
setx SecretKey "Secret key from setx environment" /M
setx TransientFaultHandlingOptions__Enabled "true" /M
setx TransientFaultHandlingOptions__AutoRetryDelay "00:00:05" /M

dotnet run
```

<span data-ttu-id="4e026-181">若要測試上述命令是否覆寫 *appsettings.json* 和 *appsettings。* `Environment`*. json*：</span><span class="sxs-lookup"><span data-stu-id="4e026-181">To test that the preceding commands override *appsettings.json* and *appsettings.*`Environment`*.json*:</span></span>

- <span data-ttu-id="4e026-182">使用 Visual Studio： Exit 並重新啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="4e026-182">With Visual Studio: Exit and restart Visual Studio.</span></span>
- <span data-ttu-id="4e026-183">使用 CLI：啟動新的命令視窗，然後輸入 `dotnet run` 。</span><span class="sxs-lookup"><span data-stu-id="4e026-183">With the CLI: Start a new command window and enter `dotnet run`.</span></span>

<span data-ttu-id="4e026-184"><xref:Microsoft.Extensions.Configuration.EnvironmentVariablesExtensions.AddEnvironmentVariables%2A>使用字串呼叫以指定環境變數的前置詞：</span><span class="sxs-lookup"><span data-stu-id="4e026-184">Call <xref:Microsoft.Extensions.Configuration.EnvironmentVariablesExtensions.AddEnvironmentVariables%2A> with a string to specify a prefix for environment variables:</span></span>

:::code language="csharp" source="snippets/configuration/console-env/Program.cs" highlight="21-22":::

<span data-ttu-id="4e026-185">在上述程式碼中：</span><span class="sxs-lookup"><span data-stu-id="4e026-185">In the preceding code:</span></span>

- <span data-ttu-id="4e026-186">`config.AddEnvironmentVariables(prefix: "CustomPrefix_")` 會在預設設定提供者之後加入。</span><span class="sxs-lookup"><span data-stu-id="4e026-186">`config.AddEnvironmentVariables(prefix: "CustomPrefix_")` is added after the default configuration providers.</span></span> <span data-ttu-id="4e026-187">如需排序設定提供者的範例，請參閱 [XML 設定提供者](#xml-configuration-provider)。</span><span class="sxs-lookup"><span data-stu-id="4e026-187">For an example of ordering the configuration providers, see [XML configuration provider](#xml-configuration-provider).</span></span>
- <span data-ttu-id="4e026-188">具有前置詞的環境變數會覆 `CustomPrefix_` 寫預設的設定提供者。</span><span class="sxs-lookup"><span data-stu-id="4e026-188">Environment variables set with the `CustomPrefix_` prefix override the default configuration providers.</span></span> <span data-ttu-id="4e026-189">這包括沒有前置詞的環境變數。</span><span class="sxs-lookup"><span data-stu-id="4e026-189">This includes environment variables without the prefix.</span></span>

<span data-ttu-id="4e026-190">讀取設定機碼值組時，會移除前置詞。</span><span class="sxs-lookup"><span data-stu-id="4e026-190">The prefix is stripped off when the configuration key-value pairs are read.</span></span>

<span data-ttu-id="4e026-191">下列命令會測試自訂前置詞：</span><span class="sxs-lookup"><span data-stu-id="4e026-191">The following commands test the custom prefix:</span></span>

```dotnetcli
set CustomPrefix__SecretKey="Secret key with CustomPrefix_ environment"
set CustomPrefix__TransientFaultHandlingOptions__Enabled=true
set CustomPrefix__TransientFaultHandlingOptions__AutoRetryDelay=00:00:21

dotnet run
```

<span data-ttu-id="4e026-192">預設設定會載入前面加上的環境變數和命令列引數 `DOTNET_` 。</span><span class="sxs-lookup"><span data-stu-id="4e026-192">The default configuration loads environment variables and command-line arguments prefixed with `DOTNET_`.</span></span> <span data-ttu-id="4e026-193">`DOTNET_`.Net 會使用前置詞來進行[主機](generic-host.md#host-configuration)和[應用程式](generic-host.md#app-configuration)設定，但不會用於使用者設定。</span><span class="sxs-lookup"><span data-stu-id="4e026-193">The `DOTNET_` prefix is used by .NET for [host](generic-host.md#host-configuration) and [app configuration](generic-host.md#app-configuration), but not for user configuration.</span></span>

<span data-ttu-id="4e026-194">如需有關主機和應用程式設定的詳細資訊，請參閱 [.Net 泛型主機](generic-host.md)。</span><span class="sxs-lookup"><span data-stu-id="4e026-194">For more information on host and app configuration, see [.NET Generic Host](generic-host.md).</span></span>

<span data-ttu-id="4e026-195">在 [Azure App Service](https://azure.microsoft.com/services/app-service)上，選取 [**設定 > 設定**] 頁面上的 [**新增應用程式設定**]。</span><span class="sxs-lookup"><span data-stu-id="4e026-195">On [Azure App Service](https://azure.microsoft.com/services/app-service), select **New application setting** on the **Settings > Configuration** page.</span></span> <span data-ttu-id="4e026-196">Azure App Service 的應用程式設定如下：</span><span class="sxs-lookup"><span data-stu-id="4e026-196">Azure App Service application settings are:</span></span>

- <span data-ttu-id="4e026-197">靜態加密，並透過加密通道傳輸。</span><span class="sxs-lookup"><span data-stu-id="4e026-197">Encrypted at rest and transmitted over an encrypted channel.</span></span>
- <span data-ttu-id="4e026-198">公開為環境變數。</span><span class="sxs-lookup"><span data-stu-id="4e026-198">Exposed as environment variables.</span></span>

### <a name="connection-string-prefixes"></a><span data-ttu-id="4e026-199">連接字串前置詞</span><span class="sxs-lookup"><span data-stu-id="4e026-199">Connection string prefixes</span></span>

<span data-ttu-id="4e026-200">設定 API 有四個連接字串環境變數的特殊處理規則。</span><span class="sxs-lookup"><span data-stu-id="4e026-200">The Configuration API has special processing rules for four connection string environment variables.</span></span> <span data-ttu-id="4e026-201">這些連接字串涉及設定應用程式環境的 Azure 連接字串。</span><span class="sxs-lookup"><span data-stu-id="4e026-201">These connection strings are involved in configuring Azure connection strings for the app environment.</span></span> <span data-ttu-id="4e026-202">具有資料表中所顯示前置詞的環境變數會以預設設定載入至應用程式，或不提供任何前置詞 `AddEnvironmentVariables` 。</span><span class="sxs-lookup"><span data-stu-id="4e026-202">Environment variables with the prefixes shown in the table are loaded into the app with the default configuration or when no prefix is supplied to `AddEnvironmentVariables`.</span></span>

| <span data-ttu-id="4e026-203">連接字串前置詞</span><span class="sxs-lookup"><span data-stu-id="4e026-203">Connection string prefix</span></span> | <span data-ttu-id="4e026-204">提供者</span><span class="sxs-lookup"><span data-stu-id="4e026-204">Provider</span></span>                                                                |
|--------------------------|-------------------------------------------------------------------------|
| `CUSTOMCONNSTR_`         | <span data-ttu-id="4e026-205">自訂提供者</span><span class="sxs-lookup"><span data-stu-id="4e026-205">Custom provider</span></span>                                                         |
| `MYSQLCONNSTR_`          | [<span data-ttu-id="4e026-206">MySQL</span><span class="sxs-lookup"><span data-stu-id="4e026-206">MySQL</span></span>](https://www.mysql.com)                                          |
| `SQLAZURECONNSTR_`       | [<span data-ttu-id="4e026-207">Azure SQL Database</span><span class="sxs-lookup"><span data-stu-id="4e026-207">Azure SQL Database</span></span>](https://azure.microsoft.com/services/sql-database) |
| `SQLCONNSTR_`            | [<span data-ttu-id="4e026-208">SQL Server</span><span class="sxs-lookup"><span data-stu-id="4e026-208">SQL Server</span></span>](https://www.microsoft.com/sql-server)                      |

<span data-ttu-id="4e026-209">當探索到具有下表所顯示之任何四個前置詞的環境變數並將其載入到設定中時：</span><span class="sxs-lookup"><span data-stu-id="4e026-209">When an environment variable is discovered and loaded into configuration with any of the four prefixes shown in the table:</span></span>

- <span data-ttu-id="4e026-210">會透過移除環境變數前置詞並新增設定機碼區段 (`ConnectionStrings`) 來移除具有下表顯示之前置詞的環境變數。</span><span class="sxs-lookup"><span data-stu-id="4e026-210">The configuration key is created by removing the environment variable prefix and adding a configuration key section (`ConnectionStrings`).</span></span>
- <span data-ttu-id="4e026-211">會建立新的設定機碼值組以代表資料庫連線提供者 (`CUSTOMCONNSTR_` 除外，這沒有所述提供者)。</span><span class="sxs-lookup"><span data-stu-id="4e026-211">A new configuration key-value pair is created that represents the database connection provider (except for `CUSTOMCONNSTR_`, which has no stated provider).</span></span>

| <span data-ttu-id="4e026-212">環境變數機碼</span><span class="sxs-lookup"><span data-stu-id="4e026-212">Environment variable key</span></span> | <span data-ttu-id="4e026-213">已轉換的設定機碼</span><span class="sxs-lookup"><span data-stu-id="4e026-213">Converted configuration key</span></span> | <span data-ttu-id="4e026-214">提供者設定項目</span><span class="sxs-lookup"><span data-stu-id="4e026-214">Provider configuration entry</span></span>                                                    |
|--------------------------|-----------------------------|---------------------------------------------------------------------------------|
| `CUSTOMCONNSTR_{KEY}`    | `ConnectionStrings:{KEY}`   | <span data-ttu-id="4e026-215">設定項目未建立。</span><span class="sxs-lookup"><span data-stu-id="4e026-215">Configuration entry not created.</span></span>                                                |
| `MYSQLCONNSTR_{KEY}`     | `ConnectionStrings:{KEY}`   | <span data-ttu-id="4e026-216">機碼：`ConnectionStrings:{KEY}_ProviderName`：</span><span class="sxs-lookup"><span data-stu-id="4e026-216">Key: `ConnectionStrings:{KEY}_ProviderName`:</span></span><br><span data-ttu-id="4e026-217">值：`MySql.Data.MySqlClient`</span><span class="sxs-lookup"><span data-stu-id="4e026-217">Value: `MySql.Data.MySqlClient`</span></span> |
| `SQLAZURECONNSTR_{KEY}`  | `ConnectionStrings:{KEY}`   | <span data-ttu-id="4e026-218">機碼：`ConnectionStrings:{KEY}_ProviderName`：</span><span class="sxs-lookup"><span data-stu-id="4e026-218">Key: `ConnectionStrings:{KEY}_ProviderName`:</span></span><br><span data-ttu-id="4e026-219">值：`System.Data.SqlClient`</span><span class="sxs-lookup"><span data-stu-id="4e026-219">Value: `System.Data.SqlClient`</span></span>  |
| `SQLCONNSTR_{KEY}`       | `ConnectionStrings:{KEY}`   | <span data-ttu-id="4e026-220">機碼：`ConnectionStrings:{KEY}_ProviderName`：</span><span class="sxs-lookup"><span data-stu-id="4e026-220">Key: `ConnectionStrings:{KEY}_ProviderName`:</span></span><br><span data-ttu-id="4e026-221">值：`System.Data.SqlClient`</span><span class="sxs-lookup"><span data-stu-id="4e026-221">Value: `System.Data.SqlClient`</span></span>  |

### <a name="environment-variables-set-in-launchsettingsjson"></a><span data-ttu-id="4e026-222">在 launchSettings.js中設定的環境變數</span><span class="sxs-lookup"><span data-stu-id="4e026-222">Environment variables set in launchSettings.json</span></span>

<span data-ttu-id="4e026-223">在 *launchSettings.js* 中設定的環境變數會覆寫系統內容中所設定的環境變數。</span><span class="sxs-lookup"><span data-stu-id="4e026-223">Environment variables set in *launchSettings.json* override those set in the system environment.</span></span>

## <a name="command-line-configuration-provider"></a><span data-ttu-id="4e026-224">命令列設定提供者</span><span class="sxs-lookup"><span data-stu-id="4e026-224">Command-line configuration provider</span></span>

<span data-ttu-id="4e026-225">使用預設設定時，會 <xref:Microsoft.Extensions.Configuration.CommandLine.CommandLineConfigurationProvider> 從命令列引數索引鍵/值組在下列設定來源之後載入設定：</span><span class="sxs-lookup"><span data-stu-id="4e026-225">Using the default configuration, the <xref:Microsoft.Extensions.Configuration.CommandLine.CommandLineConfigurationProvider> loads configuration from command-line argument key-value pairs after the following configuration sources:</span></span>

- <span data-ttu-id="4e026-226">*appsettings.json* 和 *appsettings*。 `Environment`*json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="4e026-226">*appsettings.json* and *appsettings*.`Environment`.*json* files.</span></span>
- <span data-ttu-id="4e026-227">環境中 (Secret Manager) 的應用程式秘密 `Development` 。</span><span class="sxs-lookup"><span data-stu-id="4e026-227">App secrets (Secret Manager) in the `Development` environment.</span></span>
- <span data-ttu-id="4e026-228">環境變數。</span><span class="sxs-lookup"><span data-stu-id="4e026-228">Environment variables.</span></span>

<span data-ttu-id="4e026-229">根據預設，在命令列上設定的設定值會覆寫設定值，以及所有其他設定提供者的設定值。</span><span class="sxs-lookup"><span data-stu-id="4e026-229">By default, configuration values set on the command line override configuration values set with all the other configuration providers.</span></span>

### <a name="command-line-arguments"></a><span data-ttu-id="4e026-230">命令列引數</span><span class="sxs-lookup"><span data-stu-id="4e026-230">Command-line arguments</span></span>

<span data-ttu-id="4e026-231">下列命令會使用下列命令來設定索引鍵和值 `=` ：</span><span class="sxs-lookup"><span data-stu-id="4e026-231">The following command sets keys and values using `=`:</span></span>

```dotnetcli
dotnet run SecretKey="Secret key from command line"
```

<span data-ttu-id="4e026-232">下列命令會使用下列命令來設定索引鍵和值 `/` ：</span><span class="sxs-lookup"><span data-stu-id="4e026-232">The following command sets keys and values using `/`:</span></span>

```dotnetcli
dotnet run /SecretKey "Secret key set from forward slash"
```

<span data-ttu-id="4e026-233">下列命令會使用下列命令來設定索引鍵和值 `--` ：</span><span class="sxs-lookup"><span data-stu-id="4e026-233">The following command sets keys and values using `--`:</span></span>

```dotnetcli
dotnet run --SecretKey "Secret key set from double hyphen"
```

<span data-ttu-id="4e026-234">索引鍵值：</span><span class="sxs-lookup"><span data-stu-id="4e026-234">The key value:</span></span>

- <span data-ttu-id="4e026-235">必須遵循 `=` ，或者 `--` `/` 當值在空格後面時，索引鍵必須有或的前置詞。</span><span class="sxs-lookup"><span data-stu-id="4e026-235">Must follow `=`, or the key must have a prefix of `--` or `/` when the value follows a space.</span></span>
- <span data-ttu-id="4e026-236">如果 `=` 使用，則不需要。</span><span class="sxs-lookup"><span data-stu-id="4e026-236">Isn't required if `=` is used.</span></span> <span data-ttu-id="4e026-237">例如： `SomeKey=` 。</span><span class="sxs-lookup"><span data-stu-id="4e026-237">For example, `SomeKey=`.</span></span>

<span data-ttu-id="4e026-238">在相同的命令中，不要混用 `=` 與使用空格的索引鍵/值組搭配使用的命令列引數索引鍵/值配對。</span><span class="sxs-lookup"><span data-stu-id="4e026-238">Within the same command, don't mix command-line argument key-value pairs that use `=` with key-value pairs that use a space.</span></span>

## <a name="key-per-file-configuration-provider"></a><span data-ttu-id="4e026-239">每個檔案的金鑰配置提供者</span><span class="sxs-lookup"><span data-stu-id="4e026-239">Key-per-file configuration provider</span></span>

<span data-ttu-id="4e026-240"><xref:Microsoft.Extensions.Configuration.KeyPerFile.KeyPerFileConfigurationProvider> 使用目錄的檔案做為設定機碼值組。</span><span class="sxs-lookup"><span data-stu-id="4e026-240">The <xref:Microsoft.Extensions.Configuration.KeyPerFile.KeyPerFileConfigurationProvider> uses a directory's files as configuration key-value pairs.</span></span> <span data-ttu-id="4e026-241">機碼是檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="4e026-241">The key is the file name.</span></span> <span data-ttu-id="4e026-242">此值為檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="4e026-242">The value is the file's contents.</span></span> <span data-ttu-id="4e026-243">每個檔案的每個檔案設定提供者都是在 Docker 裝載案例中使用。</span><span class="sxs-lookup"><span data-stu-id="4e026-243">The Key-per-file configuration provider is used in Docker hosting scenarios.</span></span>

<span data-ttu-id="4e026-244">若要啟用每個檔案機碼設定，請在 <xref:Microsoft.Extensions.Configuration.ConfigurationBuilder> 的執行個體上呼叫 <xref:Microsoft.Extensions.Configuration.KeyPerFileConfigurationBuilderExtensions.AddKeyPerFile%2A> 延伸模組方法。</span><span class="sxs-lookup"><span data-stu-id="4e026-244">To activate key-per-file configuration, call the <xref:Microsoft.Extensions.Configuration.KeyPerFileConfigurationBuilderExtensions.AddKeyPerFile%2A> extension method on an instance of <xref:Microsoft.Extensions.Configuration.ConfigurationBuilder>.</span></span> <span data-ttu-id="4e026-245">檔案的 `directoryPath` 必須是絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="4e026-245">The `directoryPath` to the files must be an absolute path.</span></span>

<span data-ttu-id="4e026-246">多載允許指定：</span><span class="sxs-lookup"><span data-stu-id="4e026-246">Overloads permit specifying:</span></span>

- <span data-ttu-id="4e026-247">設定來源的 `Action<KeyPerFileConfigurationSource>` 委派。</span><span class="sxs-lookup"><span data-stu-id="4e026-247">An `Action<KeyPerFileConfigurationSource>` delegate that configures the source.</span></span>
- <span data-ttu-id="4e026-248">目錄是否為選擇性與目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="4e026-248">Whether the directory is optional and the path to the directory.</span></span>

<span data-ttu-id="4e026-249">雙底線 (`__`) 是做為檔案名稱中的設定金鑰分隔符號使用。</span><span class="sxs-lookup"><span data-stu-id="4e026-249">The double-underscore (`__`) is used as a configuration key delimiter in file names.</span></span> <span data-ttu-id="4e026-250">例如，檔案名稱 `Logging__LogLevel__System` 會產生設定金鑰 `Logging:LogLevel:System`。</span><span class="sxs-lookup"><span data-stu-id="4e026-250">For example, the file name `Logging__LogLevel__System` produces the configuration key `Logging:LogLevel:System`.</span></span>

<span data-ttu-id="4e026-251">建置主機時呼叫 `ConfigureAppConfiguration` 以指定應用程式的設定：</span><span class="sxs-lookup"><span data-stu-id="4e026-251">Call `ConfigureAppConfiguration` when building the host to specify the app's configuration:</span></span>

```csharp
.ConfigureAppConfiguration((_, configuration) =>
{
    var path = Path.Combine(
        Directory.GetCurrentDirectory(), "path/to/files");

    configuration.AddKeyPerFile(directoryPath: path, optional: true);
})
```

## <a name="memory-configuration-provider"></a><span data-ttu-id="4e026-252">記憶體設定提供者</span><span class="sxs-lookup"><span data-stu-id="4e026-252">Memory configuration provider</span></span>

<span data-ttu-id="4e026-253"><xref:Microsoft.Extensions.Configuration.Memory.MemoryConfigurationProvider> 使用記憶體內集合做為設定機碼值組。</span><span class="sxs-lookup"><span data-stu-id="4e026-253">The <xref:Microsoft.Extensions.Configuration.Memory.MemoryConfigurationProvider> uses an in-memory collection as configuration key-value pairs.</span></span>

<span data-ttu-id="4e026-254">下列程式碼會將記憶體集合新增至設定系統：</span><span class="sxs-lookup"><span data-stu-id="4e026-254">The following code adds a memory collection to the configuration system:</span></span>

:::code language="csharp" source="snippets/configuration/console-memory/Program.cs" highlight="22-29":::

<span data-ttu-id="4e026-255">在上述程式碼中，會在 <xref:Microsoft.Extensions.Configuration.MemoryConfigurationBuilderExtensions.AddInMemoryCollection(Microsoft.Extensions.Configuration.IConfigurationBuilder,System.Collections.Generic.IEnumerable{System.Collections.Generic.KeyValuePair{System.String,System.String}})?displayProperty=nameWithType> 預設設定提供者之後新增記憶體提供者。</span><span class="sxs-lookup"><span data-stu-id="4e026-255">In the preceding code, <xref:Microsoft.Extensions.Configuration.MemoryConfigurationBuilderExtensions.AddInMemoryCollection(Microsoft.Extensions.Configuration.IConfigurationBuilder,System.Collections.Generic.IEnumerable{System.Collections.Generic.KeyValuePair{System.String,System.String}})?displayProperty=nameWithType> adds the memory provider after the default configuration providers.</span></span> <span data-ttu-id="4e026-256">如需排序設定提供者的範例，請參閱 [XML 設定提供者](#xml-configuration-provider)。</span><span class="sxs-lookup"><span data-stu-id="4e026-256">For an example of ordering the configuration providers, see [XML configuration provider](#xml-configuration-provider).</span></span>

## <a name="see-also"></a><span data-ttu-id="4e026-257">請參閱</span><span class="sxs-lookup"><span data-stu-id="4e026-257">See also</span></span>

- [<span data-ttu-id="4e026-258">.NET 中的設定</span><span class="sxs-lookup"><span data-stu-id="4e026-258">Configuration in .NET</span></span>](configuration.md)
- [<span data-ttu-id="4e026-259">.NET 泛型主機</span><span class="sxs-lookup"><span data-stu-id="4e026-259">.NET Generic Host</span></span>](generic-host.md)
- [<span data-ttu-id="4e026-260">實作自訂組態提供者</span><span class="sxs-lookup"><span data-stu-id="4e026-260">Implement a custom configuration provider</span></span>](custom-configuration-provider.md)
