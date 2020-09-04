---
ms.openlocfilehash: e92fe8364800b1775f0acc31d67aef66a42d0b95
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465875"
---
### <a name="obsolete-properties-on-consoleloggeroptions"></a>ConsoleLoggerOptions 上的過時屬性

<xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType>類型和上的一些屬性 <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> 現在已過時。

#### <a name="change-description"></a>變更描述

從 .NET 5.0 開始，中的 <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> 型別和數個屬性 <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> 已過時。 過時的屬性為：

- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=nameWithType>

由於引進了新的格式器，因此這些屬性現在可用於個別的格式器。

#### <a name="reason-for-change"></a>變更的原因

<xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format>屬性是列舉類型，無法表示自訂格式器。

其餘的屬性會設定為 on <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> ，並套用至主控台記錄的這兩個內建格式。 不過，隨著引入新的格式器 API，在格式器專用的選項上表示格式會更有意義。 這種變更可讓記錄器和記錄器格式器之間有更好的分隔。

#### <a name="version-introduced"></a>引進的版本

5.0 Preview 8

#### <a name="recommended-action"></a>建議的動作

- 使用新 <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName?displayProperty=nameWithType> 屬性取代 <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=nameWithType> 屬性。 例如：

  ```csharp
  loggingBuilder.AddConsole(options =>
  {
    options.FormatterName = ConsoleFormatterNames.Systemd;
  });
  ```

  和之間有幾項 <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> 差異 <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> ：

  - <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> 只有兩個可能的選項： `Default` 和 `Systemd` 。
  - <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> 不區分大小寫，而且可以是任何字串。 保留的內建名稱是 `Simple` 、 `Systemd` 和 `Json` ( .net 5.0 和更新版本的) 。
  - `"Format": "Systemd"` 對應至 `"FormatterName": "Systemd"`。
  - `"Format": "Default"` 對應至 `"FormatterName": "Simple"`。

- 針對 <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors> 、、 <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes> <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat> 和 <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp> 屬性，請改為使用新的 <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterOptions> 、或類型上的對應屬性 <xref:Microsoft.Extensions.Logging.Console.JsonConsoleFormatterOptions> <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions> 。 例如：

  ```csharp
  loggingBuilder.AddSimpleConsole(options =>
  {
      options.DisableColors = true;
  });
  ```

下列兩個 JSON 程式碼片段顯示設定檔變更的方式。 舊的設定檔：

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "None",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    },

    "Console": {
      "LogLevel": {
        "Default": "Information"
      },
      "Format": "Systemd",
      "IncludeScopes": true,
      "TimestampFormat": "HH:mm:ss",
      "UseUtcTimestamp": true
    }
  },
  "AllowedHosts": "*"
}
```

新的設定檔：

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "None",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    },

    "Console": {
      "LogLevel": {
        "Default": "Information"
      },
      "FormatterName": "Systemd",
      "FormatterOptions": {
        "IncludeScopes": true,
        "TimestampFormat": "HH:mm:ss",
        "UseUtcTimestamp": true
      }
    }
  },
  "AllowedHosts": "*"
}
```

#### <a name="category"></a>類別

- Core .NET 程式庫
- ASP.NET

#### <a name="affected-apis"></a>受影響的 API

- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=fullName>

<!--

#### Affected APIs

- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format`

-->
