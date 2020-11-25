---
title: 重大變更： ConsoleLoggerOptions 上的過時屬性
description: 瞭解核心 .NET 程式庫中的 .NET 5.0 重大變更，其中 ConsoleLoggerFormat 型別和 ConsoleLoggerOptions 上的一些屬性現在已過時。
ms.date: 11/01/2020
ms.openlocfilehash: e38ba3bda371c713a8b2cb4cda8b4c585dac29f5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760752"
---
# <a name="obsolete-properties-on-consoleloggeroptions"></a><span data-ttu-id="7b26b-103">ConsoleLoggerOptions 上的過時屬性</span><span class="sxs-lookup"><span data-stu-id="7b26b-103">Obsolete properties on ConsoleLoggerOptions</span></span>

<span data-ttu-id="7b26b-104"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType>類型和上的一些屬性 <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> 現在已過時。</span><span class="sxs-lookup"><span data-stu-id="7b26b-104">The <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> type and some properties on <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> are now obsolete.</span></span>

## <a name="change-description"></a><span data-ttu-id="7b26b-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="7b26b-105">Change description</span></span>

<span data-ttu-id="7b26b-106">從 .NET 5.0 開始，中的 <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> 型別和數個屬性 <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> 已過時。</span><span class="sxs-lookup"><span data-stu-id="7b26b-106">Starting in .NET 5.0, the <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> type and several properties on <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> are obsolete.</span></span> <span data-ttu-id="7b26b-107">過時的屬性為：</span><span class="sxs-lookup"><span data-stu-id="7b26b-107">The obsolete properties are:</span></span>

- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=nameWithType>

<span data-ttu-id="7b26b-108">由於引進了新的格式器，因此這些屬性現在可用於個別的格式器。</span><span class="sxs-lookup"><span data-stu-id="7b26b-108">With the introduction of new formatters, these properties are now available on the individual formatters.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="7b26b-109">變更的原因</span><span class="sxs-lookup"><span data-stu-id="7b26b-109">Reason for change</span></span>

<span data-ttu-id="7b26b-110"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format>屬性是列舉類型，無法表示自訂格式器。</span><span class="sxs-lookup"><span data-stu-id="7b26b-110">The <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> property is an enumeration type, which cannot represent a custom formatter.</span></span>

<span data-ttu-id="7b26b-111">其餘的屬性會設定為 on <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> ，並套用至主控台記錄的這兩個內建格式。</span><span class="sxs-lookup"><span data-stu-id="7b26b-111">The remaining properties were set on <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> and applied to both of the built-in formats for console logs.</span></span> <span data-ttu-id="7b26b-112">不過，隨著引入新的格式器 API，在格式器專用的選項上表示格式會更有意義。</span><span class="sxs-lookup"><span data-stu-id="7b26b-112">However, with the introduction of a new formatter API, it makes more sense for formatting to be represented on the formatter-specific options.</span></span> <span data-ttu-id="7b26b-113">這種變更可讓記錄器和記錄器格式器之間有更好的分隔。</span><span class="sxs-lookup"><span data-stu-id="7b26b-113">This change provides better separation between the logger and logger formatters.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="7b26b-114">引進的版本</span><span class="sxs-lookup"><span data-stu-id="7b26b-114">Version introduced</span></span>

<span data-ttu-id="7b26b-115">5.0</span><span class="sxs-lookup"><span data-stu-id="7b26b-115">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="7b26b-116">建議的動作</span><span class="sxs-lookup"><span data-stu-id="7b26b-116">Recommended action</span></span>

- <span data-ttu-id="7b26b-117">使用新 <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName?displayProperty=nameWithType> 屬性取代 <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="7b26b-117">Use the new <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName?displayProperty=nameWithType> property in place of the <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="7b26b-118">例如：</span><span class="sxs-lookup"><span data-stu-id="7b26b-118">For example:</span></span>

  ```csharp
  loggingBuilder.AddConsole(options =>
  {
    options.FormatterName = ConsoleFormatterNames.Systemd;
  });
  ```

  <span data-ttu-id="7b26b-119">和之間有幾項 <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> 差異 <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> ：</span><span class="sxs-lookup"><span data-stu-id="7b26b-119">There are several differences between <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> and <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format>:</span></span>

  - <span data-ttu-id="7b26b-120"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> 只有兩個可能的選項： `Default` 和 `Systemd` 。</span><span class="sxs-lookup"><span data-stu-id="7b26b-120"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> has only two possible options: `Default` and `Systemd`.</span></span>
  - <span data-ttu-id="7b26b-121"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> 不區分大小寫，而且可以是任何字串。</span><span class="sxs-lookup"><span data-stu-id="7b26b-121"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> is case insensitive and can be any string.</span></span> <span data-ttu-id="7b26b-122">保留的內建名稱是 `Simple` 、 `Systemd` 和 `Json` ( .net 5.0 和更新版本的) 。</span><span class="sxs-lookup"><span data-stu-id="7b26b-122">The reserved, built-in names are `Simple`, `Systemd`, and `Json` (.NET 5.0 and later).</span></span>
  - <span data-ttu-id="7b26b-123">`"Format": "Systemd"` 對應至 `"FormatterName": "Systemd"`。</span><span class="sxs-lookup"><span data-stu-id="7b26b-123">`"Format": "Systemd"` maps to `"FormatterName": "Systemd"`.</span></span>
  - <span data-ttu-id="7b26b-124">`"Format": "Default"` 對應至 `"FormatterName": "Simple"`。</span><span class="sxs-lookup"><span data-stu-id="7b26b-124">`"Format": "Default"` maps to `"FormatterName": "Simple"`.</span></span>

- <span data-ttu-id="7b26b-125">針對 <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors> 、、 <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes> <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat> 和 <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp> 屬性，請改為使用新的 <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterOptions> 、或類型上的對應屬性 <xref:Microsoft.Extensions.Logging.Console.JsonConsoleFormatterOptions> <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions> 。</span><span class="sxs-lookup"><span data-stu-id="7b26b-125">For the <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors>, <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes>, <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat>, and <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp> properties, use the corresponding property on the new <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterOptions>, <xref:Microsoft.Extensions.Logging.Console.JsonConsoleFormatterOptions>, or <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions> types instead.</span></span> <span data-ttu-id="7b26b-126">例如：</span><span class="sxs-lookup"><span data-stu-id="7b26b-126">For example:</span></span>

  ```csharp
  loggingBuilder.AddSimpleConsole(options =>
  {
      options.DisableColors = true;
  });
  ```

<span data-ttu-id="7b26b-127">下列兩個 JSON 程式碼片段顯示設定檔變更的方式。</span><span class="sxs-lookup"><span data-stu-id="7b26b-127">The following two JSON snippets show how the configuration file changes.</span></span> <span data-ttu-id="7b26b-128">舊的設定檔：</span><span class="sxs-lookup"><span data-stu-id="7b26b-128">Old configuration file:</span></span>

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

<span data-ttu-id="7b26b-129">新的設定檔：</span><span class="sxs-lookup"><span data-stu-id="7b26b-129">New configuration file:</span></span>

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

## <a name="affected-apis"></a><span data-ttu-id="7b26b-130">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="7b26b-130">Affected APIs</span></span>

- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=fullName>

<!--

#### Category

- Core .NET libraries
- ASP.NET

### Affected APIs

- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format`

-->
