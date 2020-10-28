---
title: 主控台記錄格式
description: 瞭解如何使用可用的主控台記錄格式，或為您的 .NET 應用程式執行自訂的記錄格式。
author: IEvangelist
ms.author: dapine
ms.date: 10/22/2020
ms.openlocfilehash: 28a3de833b759e043ec3e2cb5016852f9a861cee
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2020
ms.locfileid: "92897651"
---
# <a name="console-log-formatting"></a>主控台記錄格式

在 .NET 5 中，自訂格式的支援已新增至命名空間中的主控台記錄 `Microsoft.Extensions.Logging.Console` 。 有三個預先定義的格式化選項可用： [`Simple`](#simple) 、 [`Systemd`](#systemd) 和 [`Json`](#json) 。

> [!IMPORTANT]
> 先前， <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat> 列舉可讓您選取所需的記錄格式，也就是人類看得懂的，也 `Default` 就是也稱為的單行 `Systemd` 。 不過，這些 **無法** 自訂，而且現在已被取代。

在本文中，您將瞭解主控台記錄格式器。 範例原始程式碼示範如何：

- 註冊新的格式器
- 選取已註冊的格式器以使用
  - 透過程式 [代碼或設定](configuration.md)
- 執行自訂格式器
  - 更新 configuration via <xref:Microsoft.Extensions.Options.IOptionsMonitor%601>
  - 啟用自訂色彩格式

## <a name="register-formatter"></a>註冊格式器

[ `Console` 記錄提供者](logging-providers.md#console)有數個預先定義的格式器，並公開撰寫您自己自訂格式器的能力。 若要註冊任何可用的格式器，請使用對應的 `Add{Type}Console` 擴充方法：

| 可用的類型 | 註冊類型的方法 |
|--|--|
| <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Json?displayProperty=nameWithType> | <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddJsonConsole%2A?displayProperty=nameWithType> |
| <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Simple?displayProperty=nameWithType> | <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddSimpleConsole%2A?displayProperty=nameWithType> |
| <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Systemd?displayProperty=nameWithType> | <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddSystemdConsole%2A?displayProperty=nameWithType> |

### <a name="simple"></a>簡單

若要使用 `Simple` 主控台格式器，請使用下列程式來註冊 `AddSimpleConsole` ：

:::code language="csharp" source="snippets/logging/console-formatter-simple/Program.cs" highlight="11-16":::

在前面的範例程式碼中，已 <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Simple?displayProperty=nameWithType> 註冊格式器。 它提供的記錄功能，不僅能夠在每個記錄訊息中包裝資訊（例如時間和記錄層級），還允許使用 ANSI 色彩內嵌和訊息縮排。

### <a name="systemd"></a>Systemd

<xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Systemd?displayProperty=nameWithType>主控台記錄器：

- 使用「Syslog」記錄層級格式和嚴重性
- 不 **格式化具有** 色彩的訊息
- 一律在同一行中記錄訊息

這通常適用于通常會利用 `Systemd` 主控台記錄的容器。 使用 .NET 5 時， `Simple` 主控台記錄器也會啟用以單一行登入的 compact 版本，也允許停用色彩，如先前範例中所示。

:::code language="csharp" source="snippets/logging/console-formatter-systemd/Program.cs" highlight="11-15":::

### <a name="json"></a>Json

若要以 JSON 格式寫入記錄，請 `Json` 使用主控台格式器。 範例原始程式碼會顯示 ASP.NET Core 應用程式如何進行註冊。 使用 `webapp` 範本，使用 [dotnet new](../tools/dotnet-new.md) 命令建立新的 ASP.NET Core 應用程式：

```dotnetcli
dotnet new webapp -o Console.ExampleFormatters.Json
```

使用範本程式碼執行應用程式時，您會取得下列預設的記錄格式：

```
info: Microsoft.Hosting.Lifetime[0]
      Now listening on: https://localhost:5001
```

依預設， `Simple` 會使用預設設定來選取主控台記錄格式器。 您可以 `AddJsonConsole` 在 *Program.cs* 中呼叫來變更此項：

:::code language="csharp" source="snippets/logging/console-formatter-json/Program.cs" highlight="17-26":::

重新執行應用程式，而在上述變更中，記錄訊息現在會格式化為 JSON：

:::code language="json" source="snippets/logging/console-formatter-json/example-output.json":::

> [!TIP]
> `Json`主控台格式器預設會將每個訊息記錄在同一行。 為了在設定格式器時讓它更容易閱讀，請將設定 <xref:System.Text.Json.JsonWriterOptions.Indented?displayProperty=nameWithType> 為 `true` 。

## <a name="set-formatter-with-configuration"></a>使用設定設定格式器

先前的範例顯示如何以程式設計方式註冊格式器。 或者，您也 [可以使用設定](configuration.md)來完成此操作。 請考慮先前的 web 應用程式範例原始程式碼，如果您更新檔案 *上的appsettings.js* ，而不是 `ConfigureLogging` 在 *Program.cs* 檔中呼叫，您可能會得到相同的結果。 更新後的檔案會設定格式器，如下所示 `appsettings.json` ：

:::code language="json" source="snippets/logging/console-formatter-json/appsettings.json" highlight="14-23":::

需要設定的兩個索引鍵值為 `"FormatterName"` 和 `"FormatterOptions"` 。 如果設定為的值的格式器 `"FormatterName"` 已經註冊，則會選取該格式器，而且只要在節點內以索引鍵的形式提供屬性，就可以設定其屬性 `"FormatterOptions"` 。 預先定義的格式器名稱會保留在 <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames> ：

- <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Json?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Simple?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Systemd?displayProperty=nameWithType>

## <a name="implement-a-custom-formatter"></a>執行自訂格式器

若要執行自訂格式器，您需要：

- 建立的子類別 <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatter> ，這表示您的自訂格式器
- 註冊您的自訂格式器
  - <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddConsole%2A?displayProperty=nameWithType>
  - <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddConsoleFormatter%60%602(Microsoft.Extensions.Logging.ILoggingBuilder,System.Action{%60%601})?displayProperty=nameWithType>

建立擴充方法來為您處理此動作：

:::code language="csharp" source="snippets/logging/console-formatter-custom/ConsoleLoggerExtensions.cs" highlight="11-12":::

的 `CustomOptions` 定義如下：

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomOptions.cs":::

在上述程式碼中，選項是的子類別 <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterOptions> 。

`AddConsoleFormatter`API：

- 註冊的子類別 `ConsoleFormatter`
- 處理設定：
  - 使用變更權杖來同步處理更新（根據 [選項模式](options.md)和 [IOptionsMonitor](xref:Microsoft.Extensions.Options.IOptionsMonitor%601) 介面）

:::code language="csharp" source="snippets/logging/console-formatter-custom/Program.cs" highlight="11-12":::

定義的子 `CustomerFormatter` 類別 `ConsoleFormatter` ：

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomFormatter.cs" highlight="24-45":::

上述 API 會指定 `CustomFormatter.Write<TState>` 哪些文字會包裝在每個記錄訊息周圍。 標準 `ConsoleFormatter` 應該能夠以最少的時間範圍、時間戳記和嚴重性層級的記錄來包裝。 此外，您可以在記錄檔訊息中編碼 ANSI 色彩，也可以提供所需的縮排。 的執行 `CustomFormatter.Write<TState>` 缺乏這些功能。

如需進一步自訂格式的靈感，請參閱命名空間中的現有實作為 `Microsoft.Extensions.Logging.Console` ：

- [SimpleConsoleFormatter](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.Extensions.Logging.Console/src/SimpleConsoleFormatter.cs)。
- [SystemdConsoleFormatter](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.Extensions.Logging.Console/src/SystemdConsoleFormatter.cs)
- [JsonConsoleFormatter](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.Extensions.Logging.Console/src/JsonConsoleFormatter.cs)

## <a name="implement-custom-color-formatting"></a>執行自訂色彩格式化

為了在您的自訂記錄格式器中適當地啟用色彩功能，您可以擴充， <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions> 因為它具有 <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions.ColorBehavior?displayProperty=nameWithType> 可在記錄檔中啟用色彩的屬性。

建立 `CustomColorOptions` 衍生自的 `SimpleConsoleFormatterOptions` ：

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomColorOptions.cs" highlight="5":::

接下來，在類別中撰寫一些延伸方法， `TextWriterExtensions` 讓您可以在格式化的記錄檔訊息中方便地內嵌 ANSI 編碼色彩：

:::code language="csharp" source="snippets/logging/console-formatter-custom/TextWriterExtensions.cs":::

可以定義處理套用自訂色彩的自訂色彩格式器，如下所示：

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomColorFormatter.cs" highlight="15-18,52-65":::

當您執行應用程式時，記錄檔會 `CustomPrefix` 在為時以綠色顯示訊息 `FormatterOptions.ColorBehavior` `Enabled` 。

## <a name="see-also"></a>請參閱

- [.NET 中的記錄](logging.md)
- [在 .NET 中執行自訂記錄提供者](custom-logging-provider.md)
- [.NET 中的高效能記錄](high-performance-logging.md)
