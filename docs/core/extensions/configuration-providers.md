---
title: .NET 中的設定提供者
description: 瞭解如何使用設定提供者 API 來設定 .NET 應用程式。
author: IEvangelist
ms.author: dapine
ms.date: 09/16/2020
ms.openlocfilehash: fe90ba9aee08ec9c1316335a5b3fd8dd6e90a811
ms.sourcegitcommit: fe8877e564deb68d77fa4b79f55584ac8d7e8997
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90720782"
---
# <a name="configuration-providers-in-net"></a>.NET 中的設定提供者

您可以使用設定提供者，在 .NET 中進行設定。 有數種類型的提供者依賴不同的設定來源。 本文將詳細說明所有不同的設定提供者及其對應的來源。

- [檔案設定提供者](#file-configuration-provider)
- [環境變數設定提供者](#environment-variable-configuration-provider)
- [命令列設定提供者](#command-line-configuration-provider)
- [每個檔案的金鑰配置提供者](#key-per-file-configuration-provider)
- [記憶體設定提供者](#memory-configuration-provider)

## <a name="file-configuration-provider"></a>檔案設定提供者

<xref:Microsoft.Extensions.Configuration.FileConfigurationProvider> 是用於從檔案系統載入設定的基底類別。 以下是衍生自的設定提供者 `FileConfigurationProvider` ：

- [JSON 設定提供者](#json-configuration-provider)
- [XML 設定提供者](#xml-configuration-provider)
- [INI 設定提供者](#ini-configuration-provider)

### <a name="json-configuration-provider"></a>JSON 設定提供者

<xref:Microsoft.Extensions.Configuration.Json.JsonConfigurationProvider>類別會從 JSON 檔案載入設定。 安裝 [`Microsoft.Extensions.Configuration.Json`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Json) NuGet 套件。

多載可以指定：

- 檔案是否為選擇性
- 檔案變更時是否要重載設定

請考慮下列程式碼：

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="1-33,37-38" highlight="17-23":::

上述程式碼：

- 清除方法中預設新增的所有現有設定提供者 <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])> 。
- 設定 JSON 設定提供者，以將 *appsettings.js* 載入和  *appsettings*。 `Environment`具有下列選項的*json* 檔案：
  - `optional: true`：檔案是選擇性的。
  - `reloadOnChange: true` ：儲存變更時，會重載該檔案。

JSON 設定會由 [環境變數設定提供者](#environment-variable-configuration-provider) 和 [命令列設定提供者](#command-line-configuration-provider)中的設定覆寫。

具有各種設定的檔案範例 *appsettings.js* 如下所示：

:::code language="json" source="snippets/configuration/console-json/appsettings.json":::

從 <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder> 實例，加入設定提供者之後，您可以呼叫 <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder.Build?displayProperty=nameWithType> 以取得 <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> 物件。 設定根目錄表示設定階層的根。 設定中的區段可以系結至 .NET 物件的實例，並在稍後透過相依性插入來提供 <xref:Microsoft.Extensions.Options.IOptions%601> 。

請考慮 `TransientFaultHandlingOptions` 定義如下的記錄類型：

:::code language="csharp" source="snippets/configuration/console-json/TransientFaultHandlingOptions.cs":::

如需記錄類型的詳細資訊，請參閱 [c # 9 中的記錄類型](../../csharp/whats-new/csharp-9.md#record-types)。

下列程式碼會建立設定根目錄、將區段系結至 `TransientFaultHandlingOptions` 記錄類型，以及將系結值列印到主控台視窗：

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="25-32":::

應用程式會寫入下列範例輸出：

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="34-36":::

### <a name="xml-configuration-provider"></a>XML 設定提供者

<xref:Microsoft.Extensions.Configuration.Xml.XmlConfigurationProvider>類別會在執行時間從 XML 檔案載入設定。 安裝 [`Microsoft.Extensions.Configuration.Xml`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Xml) NuGet 套件。

下列程式碼示範如何使用 XML 設定提供者來設定 XML 檔案。

:::code language="csharp" source="snippets/configuration/console-xml/Program.cs" range="1-28,46,52-53" highlight="17-28":::

上述程式碼：

- 清除方法中預設新增的所有現有設定提供者 <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])> 。
- 設定 XML 設定提供者，以使用下列選項載入 *appsettings.xml* 和 *repeating-example.xml* 檔案：
  - `optional: true`：檔案是選擇性的。
  - `reloadOnChange: true` ：儲存變更時，會重載該檔案。
- 設定環境變數設定提供者。
- 如果指定的包含引數，則設定命令列設定提供者 `args` 。

[環境變數設定提供者](#environment-variable-configuration-provider)和[命令列設定提供者](#command-line-configuration-provider)中的設定會覆寫 XML 設定。

具有各種設定的範例 *appsettings.xml* 檔案如下：

:::code language="xml" source="snippets/configuration/console-xml/appsettings.xml":::

若 `name` 屬性是用來區別元素，則可以重複那些使用相同元素名稱的元素：

:::code language="xml" source="snippets/configuration/console-xml/repeating-example.xml":::

下列程式碼會讀取先前的設定檔，並顯示金鑰和值：

:::code language="csharp" source="snippets/configuration/console-xml/Program.cs" range="30-45":::

應用程式會寫入下列範例輸出：

:::code language="csharp" source="snippets/configuration/console-xml/Program.cs" range="47-51":::

屬性可用來提供值：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
  <key attribute="value" />
  <section>
    <key attribute="value" />
  </section>
</configuration>
```

先前的設定檔會使用 `value` 載入下列機碼：

- `key:attribute`
- `section:key:attribute`

### <a name="ini-configuration-provider"></a>INI 設定提供者

<xref:Microsoft.Extensions.Configuration.Ini.IniConfigurationProvider>類別會在執行時間從 INI 檔案載入設定。 安裝 [`Microsoft.Extensions.Configuration.Ini`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Ini)  NuGet 套件。

下列程式碼會清除所有設定提供者，並新增 `IniConfigurationProvider` 包含兩個 INI 檔案的作為來源：

:::code language="csharp" source="snippets/configuration/console-ini/Program.cs" range="1-31,38-39" highlight="18-24":::

具有各種設定的範例 *appsettings.ini* 檔案如下：

:::code language="ini" source="snippets/configuration/console-ini/appsettings.ini":::

下列程式碼會藉由將上述設定寫入主控台視窗來顯示上述設定：

:::code language="csharp" source="snippets/configuration/console-ini/Program.cs" range="26-30":::

應用程式會寫入下列範例輸出：

:::code language="csharp" source="snippets/configuration/console-ini/Program.cs" range="32-37":::

## <a name="environment-variable-configuration-provider"></a>環境變數設定提供者

使用預設設定時，會 <xref:Microsoft.Extensions.Configuration.EnvironmentVariables.EnvironmentVariablesConfigurationProvider> 從環境變數機碼值組載入設定，在讀取*appsettings.js* *appsettings 之後。* `Environment`*. json*和秘密管理員。 因此，從環境讀取的索引鍵值會覆寫 appsettings*上從appsettings.js*讀取的值 *。* `Environment`*. json*和秘密管理員。

`:`分隔符號不適用於所有平臺上的環境變數階層式索引鍵。 雙底線 (`__`) 會自動由所取代 `:` ，而且所有平臺都支援此功能。 例如， `:` [Bash](https://linuxhint.com/bash-environment-variables)不支援分隔符號，但 `__` 為。

下列 `set` 命令：

- 在 Windows 上設定上述範例的環境索引鍵和值。
- 變更設定的預設值來進行測試。 `dotnet run`命令必須在專案目錄中執行。

```dotnetcli
set SecretKey="Secret key from environment"
set TransientFaultHandlingOptions__Enabled="true"
set TransientFaultHandlingOptions__AutoRetryDelay="00:00:13"

dotnet run
```

先前的環境設定：

- 只會在從其設定的命令視窗啟動的進程中設定。
- 使用 Visual Studio 啟動的 web 應用程式將無法讀取。

您可以使用下列的 [setx](/windows-server/administration/windows-commands/setx) 命令，在 Windows 上設定環境機碼和值。 與不同 `set` 的 `setx` 是，設定會持續保存。 `/M` 設定系統內容中的變數。 如果 `/M` 未使用此參數，則會設定使用者環境變數。

```dotnetcli
setx SecretKey "Secret key from setx environment" /M
setx TransientFaultHandlingOptions__Enabled "true" /M
setx TransientFaultHandlingOptions__AutoRetryDelay "00:00:05" /M

dotnet run
```

若要測試上述命令是否覆寫*appsettings.json*和*appsettings。* `Environment`*. json*：

- 使用 Visual Studio： Exit 並重新啟動 Visual Studio。
- 使用 CLI：啟動新的命令視窗，然後輸入 `dotnet run` 。

<xref:Microsoft.Extensions.Configuration.EnvironmentVariablesExtensions.AddEnvironmentVariables%2A>使用字串呼叫以指定環境變數的前置詞：

:::code language="csharp" source="snippets/configuration/console-env/Program.cs" highlight="15-16":::

在上述程式碼中：

- `config.AddEnvironmentVariables(prefix: "CustomPrefix_")` 會在預設設定提供者之後加入。 如需排序設定提供者的範例，請參閱 [XML 設定提供者](#xml-configuration-provider)。
- 具有前置詞的環境變數會覆 `CustomPrefix_` 寫預設的設定提供者。 這包括沒有前置詞的環境變數。

讀取設定機碼值組時，會移除前置詞。

下列命令會測試自訂前置詞：

```dotnetcli
set CustomPrefix__SecretKey="Secret key with CustomPrefix_ environment"
set CustomPrefix_TransientFaultHandlingOptions__Enabled=true
set CustomPrefix_TransientFaultHandlingOptions__AutoRetryDelay=00:00:21

dotnet run
```

預設設定會載入前面加上的環境變數和命令列引數 `DOTNET_` 。 `DOTNET_`.Net 會使用前置詞來進行主機和應用程式設定，但不會用於使用者設定。
<!-- For more information on host and app configuration, see .NET Generic Host. -->

在[Azure App Service](https://azure.microsoft.com/services/app-service)上，選取 [**設定 > 設定**] 頁面上的 [**新增應用程式設定**]。 Azure App Service 的應用程式設定如下：

- 靜態加密，並透過加密通道傳輸。
- 公開為環境變數。

### <a name="connection-string-prefixes"></a>連接字串前置詞

設定 API 有四個連接字串環境變數的特殊處理規則。 這些連接字串涉及設定應用程式環境的 Azure 連接字串。 具有資料表中所顯示前置詞的環境變數會以預設設定載入至應用程式，或不提供任何前置詞 `AddEnvironmentVariables` 。

| 連接字串前置詞 | 提供者                                                                |
|--------------------------|-------------------------------------------------------------------------|
| `CUSTOMCONNSTR_`         | 自訂提供者                                                         |
| `MYSQLCONNSTR_`          | [MySQL](https://www.mysql.com)                                          |
| `SQLAZURECONNSTR_`       | [Azure SQL Database](https://azure.microsoft.com/services/sql-database) |
| `SQLCONNSTR_`            | [SQL Server](https://www.microsoft.com/sql-server)                      |

當探索到具有下表所顯示之任何四個前置詞的環境變數並將其載入到設定中時：

- 會透過移除環境變數前置詞並新增設定機碼區段 (`ConnectionStrings`) 來移除具有下表顯示之前置詞的環境變數。
- 會建立新的設定機碼值組以代表資料庫連線提供者 (`CUSTOMCONNSTR_` 除外，這沒有所述提供者)。

| 環境變數機碼 | 已轉換的設定機碼 | 提供者設定項目                                                    |
|--------------------------|-----------------------------|---------------------------------------------------------------------------------|
| `CUSTOMCONNSTR_{KEY}`    | `ConnectionStrings:{KEY}`   | 設定項目未建立。                                                |
| `MYSQLCONNSTR_{KEY}`     | `ConnectionStrings:{KEY}`   | 機碼：`ConnectionStrings:{KEY}_ProviderName`：<br>值：`MySql.Data.MySqlClient` |
| `SQLAZURECONNSTR_{KEY}`  | `ConnectionStrings:{KEY}`   | 機碼：`ConnectionStrings:{KEY}_ProviderName`：<br>值：`System.Data.SqlClient`  |
| `SQLCONNSTR_{KEY}`       | `ConnectionStrings:{KEY}`   | 機碼：`ConnectionStrings:{KEY}_ProviderName`：<br>值：`System.Data.SqlClient`  |

### <a name="environment-variables-set-in-launchsettingsjson"></a>在 launchSettings.js中設定的環境變數

在 *launchSettings.js* 中設定的環境變數會覆寫系統內容中所設定的環境變數。

## <a name="command-line-configuration-provider"></a>命令列設定提供者

使用預設設定時，會 <xref:Microsoft.Extensions.Configuration.CommandLine.CommandLineConfigurationProvider> 從命令列引數索引鍵/值組在下列設定來源之後載入設定：

- *appsettings.json*和*appsettings*。 `Environment`*json*檔案。
- 環境中 (Secret Manager) 的應用程式秘密 `Development` 。
- 環境變數。

根據預設，在命令列上設定的設定值會覆寫設定值，以及所有其他設定提供者的設定值。

### <a name="command-line-arguments"></a>命令列引數

下列命令會使用下列命令來設定索引鍵和值 `=` ：

```dotnetcli
dotnet run SecretKey="Secret key from command line"
```

下列命令會使用下列命令來設定索引鍵和值 `/` ：

```dotnetcli
dotnet run /SecretKey "Secret key set from forward slash"
```

下列命令會使用下列命令來設定索引鍵和值 `--` ：

```dotnetcli
dotnet run --SecretKey "Secret key set from double hyphen"
```

索引鍵值：

- 必須遵循 `=` ，或者 `--` `/` 當值在空格後面時，索引鍵必須有或的前置詞。
- 如果 `=` 使用，則不需要。 例如： `SomeKey=` 。

在相同的命令中，不要混用 `=` 與使用空格的索引鍵/值組搭配使用的命令列引數索引鍵/值配對。

## <a name="key-per-file-configuration-provider"></a>每個檔案的金鑰配置提供者

<xref:Microsoft.Extensions.Configuration.KeyPerFile.KeyPerFileConfigurationProvider> 使用目錄的檔案做為設定機碼值組。 機碼是檔案名稱。 此值為檔案的內容。 每個檔案的每個檔案設定提供者都是在 Docker 裝載案例中使用。

若要啟用每個檔案機碼設定，請在 <xref:Microsoft.Extensions.Configuration.ConfigurationBuilder> 的執行個體上呼叫 <xref:Microsoft.Extensions.Configuration.KeyPerFileConfigurationBuilderExtensions.AddKeyPerFile%2A> 延伸模組方法。 檔案的 `directoryPath` 必須是絕對路徑。

多載允許指定：

- 設定來源的 `Action<KeyPerFileConfigurationSource>` 委派。
- 目錄是否為選擇性與目錄的路徑。

雙底線 (`__`) 是做為檔案名稱中的設定金鑰分隔符號使用。 例如，檔案名稱 `Logging__LogLevel__System` 會產生設定金鑰 `Logging:LogLevel:System`。

建置主機時呼叫 `ConfigureAppConfiguration` 以指定應用程式的設定：

```csharp
.ConfigureAppConfiguration((_, configuration) =>
{
    var path = Path.Combine(
        Directory.GetCurrentDirectory(), "path/to/files");

    configuration.AddKeyPerFile(directoryPath: path, optional: true);
})
```

## <a name="memory-configuration-provider"></a>記憶體設定提供者

<xref:Microsoft.Extensions.Configuration.Memory.MemoryConfigurationProvider> 使用記憶體內集合做為設定機碼值組。

下列程式碼會將記憶體集合新增至設定系統：

:::code language="csharp" source="snippets/configuration/console-memory/Program.cs" highlight="16-23":::

在上述程式碼中，會在 <xref:Microsoft.Extensions.Configuration.MemoryConfigurationBuilderExtensions.AddInMemoryCollection(Microsoft.Extensions.Configuration.IConfigurationBuilder,System.Collections.Generic.IEnumerable{System.Collections.Generic.KeyValuePair{System.String,System.String}})?displayProperty=nameWithType> 預設設定提供者之後新增記憶體提供者。 如需排序設定提供者的範例，請參閱 [XML 設定提供者](#xml-configuration-provider)。

## <a name="see-also"></a>另請參閱

- [.NET 中的設定](configuration.md)
- [執行自訂設定提供者](custom-configuration-provider.md)
