---
title: 在 .NET 中執行自訂記錄提供者
description: 瞭解如何在您的 .NET 應用程式中執行自訂記錄提供者。
author: IEvangelist
ms.author: dapine
ms.date: 09/25/2020
ms.topic: how-to
ms.openlocfilehash: 3a0af6296c2ade15ff1b75dce5a5f99bfe235ebf
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2020
ms.locfileid: "91614684"
---
# <a name="implement-a-custom-logging-provider-in-net"></a><span data-ttu-id="996e3-103">在 .NET 中執行自訂記錄提供者</span><span class="sxs-lookup"><span data-stu-id="996e3-103">Implement a custom logging provider in .NET</span></span>

<span data-ttu-id="996e3-104">有許多 [記錄提供者](logging-providers.md) 可用於一般記錄需求。</span><span class="sxs-lookup"><span data-stu-id="996e3-104">There are many [logging providers](logging-providers.md) available for common logging needs.</span></span> <span data-ttu-id="996e3-105"><xref:Microsoft.Extensions.Logging.ILoggerProvider>當其中一個可用的提供者不符合您的應用程式需求時，您可能需要執行自訂。</span><span class="sxs-lookup"><span data-stu-id="996e3-105">You may need to implement a custom <xref:Microsoft.Extensions.Logging.ILoggerProvider> when one of the available providers doesn't suit your application needs.</span></span> <span data-ttu-id="996e3-106">在本文中，您將瞭解如何執行自訂記錄提供者，以用來在主控台中為記錄著色。</span><span class="sxs-lookup"><span data-stu-id="996e3-106">In this article, you'll learn how to implement a custom logging provider that can be used to colorize logs in the console.</span></span>

### <a name="sample-custom-logger-configuration"></a><span data-ttu-id="996e3-107">自訂記錄器設定範例</span><span class="sxs-lookup"><span data-stu-id="996e3-107">Sample custom logger configuration</span></span>

<span data-ttu-id="996e3-108">此範例會使用下列設定類型，針對每個記錄層級和事件識別碼建立不同的色彩主控台專案：</span><span class="sxs-lookup"><span data-stu-id="996e3-108">The sample creates different color console entries per log level and event ID using the following configuration type:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLoggerConfiguration.cs":::

<span data-ttu-id="996e3-109">上述程式碼會將預設層級設定為、將色彩設定為 `Information` `Green` ，以及 `EventId` 隱含 `0` 。</span><span class="sxs-lookup"><span data-stu-id="996e3-109">The preceding code sets the default level to `Information`, the color to `Green`, and the `EventId` is implicitly `0`.</span></span>

### <a name="create-the-custom-logger"></a><span data-ttu-id="996e3-110">建立自訂記錄器</span><span class="sxs-lookup"><span data-stu-id="996e3-110">Create the custom logger</span></span>

<span data-ttu-id="996e3-111">「 `ILogger` 執行」類別目錄名稱通常是記錄來源。</span><span class="sxs-lookup"><span data-stu-id="996e3-111">The `ILogger` implementation category name is typically the logging source.</span></span> <span data-ttu-id="996e3-112">例如，建立記錄器的類型：</span><span class="sxs-lookup"><span data-stu-id="996e3-112">For example, the type where the logger is created:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLogger.cs":::

<span data-ttu-id="996e3-113">上述程式碼：</span><span class="sxs-lookup"><span data-stu-id="996e3-113">The preceding code:</span></span>

- <span data-ttu-id="996e3-114">建立每個類別目錄名稱的記錄器實例。</span><span class="sxs-lookup"><span data-stu-id="996e3-114">Creates a logger instance per category name.</span></span>
- <span data-ttu-id="996e3-115">簽 `logLevel == _config.LogLevel` 入 `IsEnabled` ，因此每個 `logLevel` 都有唯一的記錄器。</span><span class="sxs-lookup"><span data-stu-id="996e3-115">Checks `logLevel == _config.LogLevel` in `IsEnabled`, so each `logLevel` has a unique logger.</span></span> <span data-ttu-id="996e3-116">您也應該針對所有較高的記錄層級啟用記錄器：</span><span class="sxs-lookup"><span data-stu-id="996e3-116">Loggers should also be enabled for all higher log levels:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLogger.cs" range="16-17":::

## <a name="custom-logger-provider"></a><span data-ttu-id="996e3-117">自訂記錄器提供者</span><span class="sxs-lookup"><span data-stu-id="996e3-117">Custom logger provider</span></span>

<span data-ttu-id="996e3-118">`ILoggerProvider`物件負責建立記錄器實例。</span><span class="sxs-lookup"><span data-stu-id="996e3-118">The `ILoggerProvider` object is responsible for creating logger instances.</span></span> <span data-ttu-id="996e3-119">或許不需要為每個類別建立記錄器實例，但這對某些記錄器而言很有意義，例如 NLog 或 log4net。</span><span class="sxs-lookup"><span data-stu-id="996e3-119">Maybe it is not needed to create a logger instance per category, but this makes sense for some loggers, like NLog or log4net.</span></span> <span data-ttu-id="996e3-120">如此一來，您也可以視需要選擇每個類別的不同記錄輸出目標：</span><span class="sxs-lookup"><span data-stu-id="996e3-120">Doing this you are also able to choose different logging output targets per category if needed:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLoggerProvider.cs":::

<span data-ttu-id="996e3-121">在上述程式碼中， <xref:Microsoft.Build.Logging.LoggerDescription.CreateLogger%2A> `ColorConsoleLogger` 會建立每個類別目錄名稱的單一實例，並將它儲存在中 [`ConcurrentDictionary<TKey,TValue>`](/dotnet/api/system.collections.concurrent.concurrentdictionary-2) 。</span><span class="sxs-lookup"><span data-stu-id="996e3-121">In the preceding code, <xref:Microsoft.Build.Logging.LoggerDescription.CreateLogger%2A> creates a single instance of the `ColorConsoleLogger` per category name and stores it in the [`ConcurrentDictionary<TKey,TValue>`](/dotnet/api/system.collections.concurrent.concurrentdictionary-2).</span></span>

## <a name="usage-and-registration-of-the-custom-logger"></a><span data-ttu-id="996e3-122">自訂記錄器的使用和註冊</span><span class="sxs-lookup"><span data-stu-id="996e3-122">Usage and registration of the custom logger</span></span>

<span data-ttu-id="996e3-123">若要加入自訂記錄提供者和對應的記錄器，請 <xref:Microsoft.Extensions.Logging.ILoggerProvider> <xref:Microsoft.Extensions.Logging.ILoggingBuilder> 從新增 <xref:Microsoft.Extensions.Hosting.HostingHostBuilderExtensions.ConfigureLogging(Microsoft.Extensions.Hosting.IHostBuilder,System.Action{Microsoft.Extensions.Logging.ILoggingBuilder})?displayProperty=nameWithType> ：</span><span class="sxs-lookup"><span data-stu-id="996e3-123">To add the custom logging provider and corresponding logger, add an <xref:Microsoft.Extensions.Logging.ILoggerProvider> with <xref:Microsoft.Extensions.Logging.ILoggingBuilder> from the <xref:Microsoft.Extensions.Hosting.HostingHostBuilderExtensions.ConfigureLogging(Microsoft.Extensions.Hosting.IHostBuilder,System.Action{Microsoft.Extensions.Logging.ILoggingBuilder})?displayProperty=nameWithType>:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/Program.cs" range="23-39":::

<span data-ttu-id="996e3-124">會 `ILoggingBuilder` 建立一個或多個 `ILogger` 實例。</span><span class="sxs-lookup"><span data-stu-id="996e3-124">The `ILoggingBuilder` creates one or more `ILogger` instances.</span></span> <span data-ttu-id="996e3-125">`ILogger`架構會使用這些實例來記錄資訊。</span><span class="sxs-lookup"><span data-stu-id="996e3-125">The `ILogger` instances are used by the framework to log the information.</span></span>

<span data-ttu-id="996e3-126">在上述程式碼中，至少為下列各項提供一個擴充方法 `ILoggerFactory` ：</span><span class="sxs-lookup"><span data-stu-id="996e3-126">For the preceding code, provide at least one extension method for the `ILoggerFactory`:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/Extensions/ColorConsoleLoggerExtensions.cs":::

<span data-ttu-id="996e3-127">執行這個簡單的應用程式將會轉譯如下的主控台視窗：</span><span class="sxs-lookup"><span data-stu-id="996e3-127">Running this simple application will render similar to the following console window:</span></span>

:::image type="content" source="media/color-console-logger.png" alt-text="色彩主控台記錄器範例輸出":::

## <a name="see-also"></a><span data-ttu-id="996e3-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="996e3-129">See also</span></span>

- <span data-ttu-id="996e3-130">[在 .net 中記錄](logging.md)。</span><span class="sxs-lookup"><span data-stu-id="996e3-130">[Logging in .NET](logging.md).</span></span>
- <span data-ttu-id="996e3-131">[.Net 中的記錄提供者](logging-providers.md)。</span><span class="sxs-lookup"><span data-stu-id="996e3-131">[Logging providers in .NET](logging-providers.md).</span></span>
- <span data-ttu-id="996e3-132">[.Net 中的高效能記錄](high-performance-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="996e3-132">[High-performance logging in .NET](high-performance-logging.md).</span></span>
