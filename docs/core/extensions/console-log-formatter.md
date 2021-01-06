---
title: 主控台記錄格式
description: 瞭解如何使用可用的主控台記錄格式，或為您的 .NET 應用程式執行自訂的記錄格式。
author: IEvangelist
ms.author: dapine
ms.date: 12/17/2020
ms.openlocfilehash: 0ec8fc2018febe4273aa646d1682be197933f925
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2020
ms.locfileid: "97700816"
---
# <a name="console-log-formatting"></a><span data-ttu-id="bf8ea-103">主控台記錄格式</span><span class="sxs-lookup"><span data-stu-id="bf8ea-103">Console log formatting</span></span>

<span data-ttu-id="bf8ea-104">在 .NET 5 中，自訂格式的支援已新增至命名空間中的主控台記錄 `Microsoft.Extensions.Logging.Console` 。</span><span class="sxs-lookup"><span data-stu-id="bf8ea-104">In .NET 5, support for custom formatting was added to console logs in the `Microsoft.Extensions.Logging.Console` namespace.</span></span> <span data-ttu-id="bf8ea-105">有三個預先定義的格式化選項可用： [`Simple`](#simple) 、 [`Systemd`](#systemd) 和 [`Json`](#json) 。</span><span class="sxs-lookup"><span data-stu-id="bf8ea-105">There are three predefined formatting options available: [`Simple`](#simple), [`Systemd`](#systemd), and [`Json`](#json).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bf8ea-106">先前， <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat> 列舉可讓您選取所需的記錄格式，也就是人類看得懂的，也 `Default` 就是也稱為的單行 `Systemd` 。</span><span class="sxs-lookup"><span data-stu-id="bf8ea-106">Previously, the <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat> enum allowed for selecting the desired log format, either human readable which was the `Default`, or single line which is also known as `Systemd`.</span></span> <span data-ttu-id="bf8ea-107">不過，這些 **無法** 自訂，而且現在已被取代。</span><span class="sxs-lookup"><span data-stu-id="bf8ea-107">However, these were **not** customizable, and are now deprecated.</span></span>

<span data-ttu-id="bf8ea-108">在本文中，您將瞭解主控台記錄格式器。</span><span class="sxs-lookup"><span data-stu-id="bf8ea-108">In this article, you will learn about console log formatters.</span></span> <span data-ttu-id="bf8ea-109">範例原始程式碼示範如何：</span><span class="sxs-lookup"><span data-stu-id="bf8ea-109">The sample source code demonstrates how to:</span></span>

- <span data-ttu-id="bf8ea-110">註冊新的格式器</span><span class="sxs-lookup"><span data-stu-id="bf8ea-110">Register a new formatter</span></span>
- <span data-ttu-id="bf8ea-111">選取已註冊的格式器以使用</span><span class="sxs-lookup"><span data-stu-id="bf8ea-111">Select a registered formatter to use</span></span>
  - <span data-ttu-id="bf8ea-112">透過程式 [代碼或設定](configuration.md)</span><span class="sxs-lookup"><span data-stu-id="bf8ea-112">Either through code, or [configuration](configuration.md)</span></span>
- <span data-ttu-id="bf8ea-113">執行自訂格式器</span><span class="sxs-lookup"><span data-stu-id="bf8ea-113">Implement a custom formatter</span></span>
  - <span data-ttu-id="bf8ea-114">更新 configuration via <xref:Microsoft.Extensions.Options.IOptionsMonitor%601></span><span class="sxs-lookup"><span data-stu-id="bf8ea-114">Update configuration via <xref:Microsoft.Extensions.Options.IOptionsMonitor%601></span></span>
  - <span data-ttu-id="bf8ea-115">啟用自訂色彩格式</span><span class="sxs-lookup"><span data-stu-id="bf8ea-115">Enable custom color formatting</span></span>

## <a name="register-formatter"></a><span data-ttu-id="bf8ea-116">註冊格式器</span><span class="sxs-lookup"><span data-stu-id="bf8ea-116">Register formatter</span></span>

<span data-ttu-id="bf8ea-117">[ `Console` 記錄提供者](logging-providers.md#console)有數個預先定義的格式器，並公開撰寫您自己自訂格式器的能力。</span><span class="sxs-lookup"><span data-stu-id="bf8ea-117">The [`Console` logging provider](logging-providers.md#console) has several predefined formatters, and exposes the ability to author your own custom formatter.</span></span> <span data-ttu-id="bf8ea-118">若要註冊任何可用的格式器，請使用對應的 `Add{Type}Console` 擴充方法：</span><span class="sxs-lookup"><span data-stu-id="bf8ea-118">To register any of the available formatters, use the corresponding `Add{Type}Console` extension method:</span></span>

| <span data-ttu-id="bf8ea-119">可用的類型</span><span class="sxs-lookup"><span data-stu-id="bf8ea-119">Available types</span></span> | <span data-ttu-id="bf8ea-120">註冊類型的方法</span><span class="sxs-lookup"><span data-stu-id="bf8ea-120">Method to register type</span></span> |
|--|--|
| <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Json?displayProperty=nameWithType> | <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddJsonConsole%2A?displayProperty=nameWithType> |
| <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Simple?displayProperty=nameWithType> | <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddSimpleConsole%2A?displayProperty=nameWithType> |
| <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Systemd?displayProperty=nameWithType> | <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddSystemdConsole%2A?displayProperty=nameWithType> |

### <a name="simple"></a><span data-ttu-id="bf8ea-121">簡單</span><span class="sxs-lookup"><span data-stu-id="bf8ea-121">Simple</span></span>

<span data-ttu-id="bf8ea-122">若要使用 `Simple` 主控台格式器，請使用下列程式來註冊 `AddSimpleConsole` ：</span><span class="sxs-lookup"><span data-stu-id="bf8ea-122">To use the `Simple` console formatter, register it with `AddSimpleConsole`:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-simple/Program.cs" highlight="11-16":::

<span data-ttu-id="bf8ea-123">在前面的範例程式碼中，已 <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Simple?displayProperty=nameWithType> 註冊格式器。</span><span class="sxs-lookup"><span data-stu-id="bf8ea-123">In the preceding sample source code, the <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Simple?displayProperty=nameWithType> formatter was registered.</span></span> <span data-ttu-id="bf8ea-124">它提供的記錄功能，不僅能夠在每個記錄訊息中包裝資訊（例如時間和記錄層級），還允許使用 ANSI 色彩內嵌和訊息縮排。</span><span class="sxs-lookup"><span data-stu-id="bf8ea-124">It provides logs with the ability to not only wrap information such as time and log level in each log message, but also allows for ANSI color embedding and indentation of messages.</span></span>

### <a name="systemd"></a><span data-ttu-id="bf8ea-125">Systemd</span><span class="sxs-lookup"><span data-stu-id="bf8ea-125">Systemd</span></span>

<span data-ttu-id="bf8ea-126"><xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Systemd?displayProperty=nameWithType>主控台記錄器：</span><span class="sxs-lookup"><span data-stu-id="bf8ea-126">The <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Systemd?displayProperty=nameWithType> console logger:</span></span>

- <span data-ttu-id="bf8ea-127">使用「Syslog」記錄層級格式和嚴重性</span><span class="sxs-lookup"><span data-stu-id="bf8ea-127">Uses the "Syslog" log level format and severities</span></span>
- <span data-ttu-id="bf8ea-128">不 **格式化具有** 色彩的訊息</span><span class="sxs-lookup"><span data-stu-id="bf8ea-128">Does **not** format messages with colors</span></span>
- <span data-ttu-id="bf8ea-129">一律在同一行中記錄訊息</span><span class="sxs-lookup"><span data-stu-id="bf8ea-129">Always logs messages in a single line</span></span>

<span data-ttu-id="bf8ea-130">這通常適用于通常會利用 `Systemd` 主控台記錄的容器。</span><span class="sxs-lookup"><span data-stu-id="bf8ea-130">This is commonly useful for containers, which often make use of `Systemd` console logging.</span></span> <span data-ttu-id="bf8ea-131">使用 .NET 5 時， `Simple` 主控台記錄器也會啟用以單一行登入的 compact 版本，也允許停用色彩，如先前範例中所示。</span><span class="sxs-lookup"><span data-stu-id="bf8ea-131">With .NET 5, the `Simple` console logger also enables a compact version that logs in a single line, and also allows for disabling colors as shown in an earlier sample.</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-systemd/Program.cs" highlight="11-15":::

### <a name="json"></a><span data-ttu-id="bf8ea-132">Json</span><span class="sxs-lookup"><span data-stu-id="bf8ea-132">Json</span></span>

<span data-ttu-id="bf8ea-133">若要以 JSON 格式寫入記錄，請 `Json` 使用主控台格式器。</span><span class="sxs-lookup"><span data-stu-id="bf8ea-133">To write logs in a JSON format, the `Json` console formatter is used.</span></span> <span data-ttu-id="bf8ea-134">範例原始程式碼會顯示 ASP.NET Core 應用程式如何進行註冊。</span><span class="sxs-lookup"><span data-stu-id="bf8ea-134">The sample source code shows how an ASP.NET Core app might register it.</span></span> <span data-ttu-id="bf8ea-135">使用 `webapp` 範本，使用 [dotnet new](../tools/dotnet-new.md) 命令建立新的 ASP.NET Core 應用程式：</span><span class="sxs-lookup"><span data-stu-id="bf8ea-135">Using the `webapp` template, create a new ASP.NET Core app with the [dotnet new](../tools/dotnet-new.md) command:</span></span>

```dotnetcli
dotnet new webapp -o Console.ExampleFormatters.Json
```

<span data-ttu-id="bf8ea-136">使用範本程式碼執行應用程式時，您會取得下列預設的記錄格式：</span><span class="sxs-lookup"><span data-stu-id="bf8ea-136">When running the app, using the template code, you get the default log format below:</span></span>

```
info: Microsoft.Hosting.Lifetime[0]
      Now listening on: https://localhost:5001
```

<span data-ttu-id="bf8ea-137">依預設， `Simple` 會使用預設設定來選取主控台記錄格式器。</span><span class="sxs-lookup"><span data-stu-id="bf8ea-137">By default, the `Simple` console log formatter is selected with default configuration.</span></span> <span data-ttu-id="bf8ea-138">您可以 `AddJsonConsole` 在 *Program.cs* 中呼叫來變更此項：</span><span class="sxs-lookup"><span data-stu-id="bf8ea-138">You change this by calling `AddJsonConsole` in the *Program.cs*:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-json/Program.cs" highlight="17-26":::

<span data-ttu-id="bf8ea-139">重新執行應用程式，而在上述變更中，記錄訊息現在會格式化為 JSON：</span><span class="sxs-lookup"><span data-stu-id="bf8ea-139">Run the app again, with the above change, the log message is now formatted as JSON:</span></span>

:::code language="json" source="snippets/logging/console-formatter-json/example-output.json":::

> [!TIP]
> <span data-ttu-id="bf8ea-140">`Json`主控台格式器預設會將每個訊息記錄在同一行。</span><span class="sxs-lookup"><span data-stu-id="bf8ea-140">The `Json` console formatter, by default, logs each message in a single line.</span></span> <span data-ttu-id="bf8ea-141">為了在設定格式器時讓它更容易閱讀，請將設定 <xref:System.Text.Json.JsonWriterOptions.Indented?displayProperty=nameWithType> 為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="bf8ea-141">In order to make it more readable while configuring the formatter, set <xref:System.Text.Json.JsonWriterOptions.Indented?displayProperty=nameWithType> to `true`.</span></span>

## <a name="set-formatter-with-configuration"></a><span data-ttu-id="bf8ea-142">使用設定設定格式器</span><span class="sxs-lookup"><span data-stu-id="bf8ea-142">Set formatter with configuration</span></span>

<span data-ttu-id="bf8ea-143">先前的範例顯示如何以程式設計方式註冊格式器。</span><span class="sxs-lookup"><span data-stu-id="bf8ea-143">The previous samples have shown how to register a formatter programmatically.</span></span> <span data-ttu-id="bf8ea-144">或者，您也 [可以使用設定](configuration.md)來完成此操作。</span><span class="sxs-lookup"><span data-stu-id="bf8ea-144">Alternatively, this can be done with [configuration](configuration.md).</span></span> <span data-ttu-id="bf8ea-145">請考慮先前的 web 應用程式範例原始程式碼，如果您更新檔案 *上的appsettings.js* ，而不是 `ConfigureLogging` 在 *Program.cs* 檔中呼叫，您可能會得到相同的結果。</span><span class="sxs-lookup"><span data-stu-id="bf8ea-145">Consider the previous web application sample source code, if you update the *appsettings.json* file rather than calling `ConfigureLogging` in the *Program.cs* file, you could get the same outcome.</span></span> <span data-ttu-id="bf8ea-146">更新後的檔案會設定格式器，如下所示 `appsettings.json` ：</span><span class="sxs-lookup"><span data-stu-id="bf8ea-146">The updated `appsettings.json` file would configure the formatter as follows:</span></span>

:::code language="json" source="snippets/logging/console-formatter-json/appsettings.json" highlight="14-23":::

<span data-ttu-id="bf8ea-147">需要設定的兩個索引鍵值為 `"FormatterName"` 和 `"FormatterOptions"` 。</span><span class="sxs-lookup"><span data-stu-id="bf8ea-147">The two key values that need to be set are `"FormatterName"` and `"FormatterOptions"`.</span></span> <span data-ttu-id="bf8ea-148">如果設定為的值的格式器 `"FormatterName"` 已經註冊，則會選取該格式器，而且只要在節點內以索引鍵的形式提供屬性，就可以設定其屬性 `"FormatterOptions"` 。</span><span class="sxs-lookup"><span data-stu-id="bf8ea-148">If a formatter with the value set for `"FormatterName"` is already registered, that formatter is selected, and its properties can be configured as long as they are provided as a key inside the `"FormatterOptions"` node.</span></span> <span data-ttu-id="bf8ea-149">預先定義的格式器名稱會保留在 <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames> ：</span><span class="sxs-lookup"><span data-stu-id="bf8ea-149">The predefined formatter names are reserved under <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames>:</span></span>

- <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Json?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Simple?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Systemd?displayProperty=nameWithType>

## <a name="implement-a-custom-formatter"></a><span data-ttu-id="bf8ea-150">執行自訂格式器</span><span class="sxs-lookup"><span data-stu-id="bf8ea-150">Implement a custom formatter</span></span>

<span data-ttu-id="bf8ea-151">若要執行自訂格式器，您需要：</span><span class="sxs-lookup"><span data-stu-id="bf8ea-151">To implement a custom formatter, you need to:</span></span>

- <span data-ttu-id="bf8ea-152">建立的子類別 <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatter> ，這表示您的自訂格式器</span><span class="sxs-lookup"><span data-stu-id="bf8ea-152">Create a subclass of <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatter>, this represents your custom formatter</span></span>
- <span data-ttu-id="bf8ea-153">註冊您的自訂格式器</span><span class="sxs-lookup"><span data-stu-id="bf8ea-153">Register your custom formatter with</span></span>
  - <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddConsole%2A?displayProperty=nameWithType>
  - <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddConsoleFormatter%60%602(Microsoft.Extensions.Logging.ILoggingBuilder,System.Action{%60%601})?displayProperty=nameWithType>

<span data-ttu-id="bf8ea-154">建立擴充方法來為您處理此動作：</span><span class="sxs-lookup"><span data-stu-id="bf8ea-154">Create an extension method to handle this for you:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-custom/ConsoleLoggerExtensions.cs" highlight="11-12":::

<span data-ttu-id="bf8ea-155">的 `CustomOptions` 定義如下：</span><span class="sxs-lookup"><span data-stu-id="bf8ea-155">The `CustomOptions` are defined as follows:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomOptions.cs":::

<span data-ttu-id="bf8ea-156">在上述程式碼中，選項是的子類別 <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterOptions> 。</span><span class="sxs-lookup"><span data-stu-id="bf8ea-156">In the preceding code, the options are a subclass of <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterOptions>.</span></span>

<span data-ttu-id="bf8ea-157">`AddConsoleFormatter`API：</span><span class="sxs-lookup"><span data-stu-id="bf8ea-157">The `AddConsoleFormatter` API:</span></span>

- <span data-ttu-id="bf8ea-158">註冊的子類別 `ConsoleFormatter`</span><span class="sxs-lookup"><span data-stu-id="bf8ea-158">Registers a subclass of `ConsoleFormatter`</span></span>
- <span data-ttu-id="bf8ea-159">處理設定：</span><span class="sxs-lookup"><span data-stu-id="bf8ea-159">Handles configuration:</span></span>
  - <span data-ttu-id="bf8ea-160">使用變更權杖來同步處理更新（根據 [選項模式](options.md)和 [IOptionsMonitor](xref:Microsoft.Extensions.Options.IOptionsMonitor%601) 介面）</span><span class="sxs-lookup"><span data-stu-id="bf8ea-160">Uses a change token to synchronize updates, based on the [options pattern](options.md), and the [IOptionsMonitor](xref:Microsoft.Extensions.Options.IOptionsMonitor%601) interface</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-custom/Program.cs" highlight="11-12":::

<span data-ttu-id="bf8ea-161">定義的子 `CustomerFormatter` 類別 `ConsoleFormatter` ：</span><span class="sxs-lookup"><span data-stu-id="bf8ea-161">Define a `CustomerFormatter` subclass of `ConsoleFormatter`:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomFormatter.cs" highlight="24-45":::

<span data-ttu-id="bf8ea-162">上述 API 會指定 `CustomFormatter.Write<TState>` 哪些文字會包裝在每個記錄訊息周圍。</span><span class="sxs-lookup"><span data-stu-id="bf8ea-162">The preceding `CustomFormatter.Write<TState>` API dictates what text gets wrapped around each log message.</span></span> <span data-ttu-id="bf8ea-163">標準 `ConsoleFormatter` 應該能夠以最少的時間範圍、時間戳記和嚴重性層級的記錄來包裝。</span><span class="sxs-lookup"><span data-stu-id="bf8ea-163">A standard `ConsoleFormatter` should be able to wrap around scopes, time stamps, and severity level of logs at a minimum.</span></span> <span data-ttu-id="bf8ea-164">此外，您可以在記錄檔訊息中編碼 ANSI 色彩，也可以提供所需的縮排。</span><span class="sxs-lookup"><span data-stu-id="bf8ea-164">Additionally, you can encode ANSI colors in the log messages, and provide desired indentations as well.</span></span> <span data-ttu-id="bf8ea-165">的執行 `CustomFormatter.Write<TState>` 缺乏這些功能。</span><span class="sxs-lookup"><span data-stu-id="bf8ea-165">The implementation of the `CustomFormatter.Write<TState>` lacks these capabilities.</span></span>

<span data-ttu-id="bf8ea-166">如需進一步自訂格式的靈感，請參閱命名空間中的現有實作為 `Microsoft.Extensions.Logging.Console` ：</span><span class="sxs-lookup"><span data-stu-id="bf8ea-166">For inspiration on further customizing formatting, see the existing implementations in the `Microsoft.Extensions.Logging.Console` namespace:</span></span>

- <span data-ttu-id="bf8ea-167">[SimpleConsoleFormatter](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.Extensions.Logging.Console/src/SimpleConsoleFormatter.cs)。</span><span class="sxs-lookup"><span data-stu-id="bf8ea-167">[SimpleConsoleFormatter](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.Extensions.Logging.Console/src/SimpleConsoleFormatter.cs).</span></span>
- [<span data-ttu-id="bf8ea-168">SystemdConsoleFormatter</span><span class="sxs-lookup"><span data-stu-id="bf8ea-168">SystemdConsoleFormatter</span></span>](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.Extensions.Logging.Console/src/SystemdConsoleFormatter.cs)
- [<span data-ttu-id="bf8ea-169">JsonConsoleFormatter</span><span class="sxs-lookup"><span data-stu-id="bf8ea-169">JsonConsoleFormatter</span></span>](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.Extensions.Logging.Console/src/JsonConsoleFormatter.cs)

## <a name="implement-custom-color-formatting"></a><span data-ttu-id="bf8ea-170">執行自訂色彩格式化</span><span class="sxs-lookup"><span data-stu-id="bf8ea-170">Implement custom color formatting</span></span>

<span data-ttu-id="bf8ea-171">為了在您的自訂記錄格式器中適當地啟用色彩功能，您可以擴充， <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions> 因為它具有 <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions.ColorBehavior?displayProperty=nameWithType> 可在記錄檔中啟用色彩的屬性。</span><span class="sxs-lookup"><span data-stu-id="bf8ea-171">In order to properly enable color capabilities in your custom logging formatter, you can extend the <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions> as it has a <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions.ColorBehavior?displayProperty=nameWithType> property that can be useful for enabling colors in logs.</span></span>

<span data-ttu-id="bf8ea-172">建立 `CustomColorOptions` 衍生自的 `SimpleConsoleFormatterOptions` ：</span><span class="sxs-lookup"><span data-stu-id="bf8ea-172">Create a `CustomColorOptions` that derives from `SimpleConsoleFormatterOptions`:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomColorOptions.cs" highlight="5":::

<span data-ttu-id="bf8ea-173">接下來，在類別中撰寫一些延伸方法， `TextWriterExtensions` 讓您可以在格式化的記錄檔訊息中方便地內嵌 ANSI 編碼色彩：</span><span class="sxs-lookup"><span data-stu-id="bf8ea-173">Next, write some extension methods in a `TextWriterExtensions` class that allow for conveniently embedding ANSI coded colors within formatted log messages:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-custom/TextWriterExtensions.cs":::

<span data-ttu-id="bf8ea-174">可以定義處理套用自訂色彩的自訂色彩格式器，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bf8ea-174">A custom color formatter that handles applying custom colors could be defined as follows:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomColorFormatter.cs" highlight="15-18,52-65":::

<span data-ttu-id="bf8ea-175">當您執行應用程式時，記錄檔會 `CustomPrefix` 在為時以綠色顯示訊息 `FormatterOptions.ColorBehavior` `Enabled` 。</span><span class="sxs-lookup"><span data-stu-id="bf8ea-175">When you run the application, the logs will show the `CustomPrefix` message in the color green when `FormatterOptions.ColorBehavior` is `Enabled`.</span></span>

> [!NOTE]
> <span data-ttu-id="bf8ea-176">當 <xref:Microsoft.Extensions.Logging.Console.LoggerColorBehavior> 為時 `Disabled` ，記錄訊息 _不會_ 解讀記錄訊息內內嵌的 ANSI 色彩代碼。</span><span class="sxs-lookup"><span data-stu-id="bf8ea-176">When <xref:Microsoft.Extensions.Logging.Console.LoggerColorBehavior> is `Disabled`, log messages do _not_ interpret embedded ANSI color codes within log messages.</span></span> <span data-ttu-id="bf8ea-177">相反地，它們會輸出原始訊息。</span><span class="sxs-lookup"><span data-stu-id="bf8ea-177">Instead, they output the raw message.</span></span> <span data-ttu-id="bf8ea-178">例如，設想下列情況：</span><span class="sxs-lookup"><span data-stu-id="bf8ea-178">For example, consider the following:</span></span>
>
> ```csharp
> logger.LogInformation("Random log \x1B[42mwith green background\x1B[49m message");
> ```
>
> <span data-ttu-id="bf8ea-179">這會輸出逐字字串，而且 _不_ 會以色彩標示。</span><span class="sxs-lookup"><span data-stu-id="bf8ea-179">This would output the verbatim string, and it is _not_ colorized.</span></span>
>
> ```output
> Random log \x1B[42mwith green background\x1B[49m message
> ```

## <a name="see-also"></a><span data-ttu-id="bf8ea-180">請參閱</span><span class="sxs-lookup"><span data-stu-id="bf8ea-180">See also</span></span>

- [<span data-ttu-id="bf8ea-181">.NET 中的記錄</span><span class="sxs-lookup"><span data-stu-id="bf8ea-181">Logging in .NET</span></span>](logging.md)
- [<span data-ttu-id="bf8ea-182">在 .NET 中執行自訂記錄提供者</span><span class="sxs-lookup"><span data-stu-id="bf8ea-182">Implement a custom logging provider in .NET</span></span>](custom-logging-provider.md)
- [<span data-ttu-id="bf8ea-183">.NET 中的高效能記錄</span><span class="sxs-lookup"><span data-stu-id="bf8ea-183">High-performance logging in .NET</span></span>](high-performance-logging.md)
