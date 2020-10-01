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
# <a name="implement-a-custom-logging-provider-in-net"></a>在 .NET 中執行自訂記錄提供者

有許多 [記錄提供者](logging-providers.md) 可用於一般記錄需求。 <xref:Microsoft.Extensions.Logging.ILoggerProvider>當其中一個可用的提供者不符合您的應用程式需求時，您可能需要執行自訂。 在本文中，您將瞭解如何執行自訂記錄提供者，以用來在主控台中為記錄著色。

### <a name="sample-custom-logger-configuration"></a>自訂記錄器設定範例

此範例會使用下列設定類型，針對每個記錄層級和事件識別碼建立不同的色彩主控台專案：

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLoggerConfiguration.cs":::

上述程式碼會將預設層級設定為、將色彩設定為 `Information` `Green` ，以及 `EventId` 隱含 `0` 。

### <a name="create-the-custom-logger"></a>建立自訂記錄器

「 `ILogger` 執行」類別目錄名稱通常是記錄來源。 例如，建立記錄器的類型：

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLogger.cs":::

上述程式碼：

- 建立每個類別目錄名稱的記錄器實例。
- 簽 `logLevel == _config.LogLevel` 入 `IsEnabled` ，因此每個 `logLevel` 都有唯一的記錄器。 您也應該針對所有較高的記錄層級啟用記錄器：

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLogger.cs" range="16-17":::

## <a name="custom-logger-provider"></a>自訂記錄器提供者

`ILoggerProvider`物件負責建立記錄器實例。 或許不需要為每個類別建立記錄器實例，但這對某些記錄器而言很有意義，例如 NLog 或 log4net。 如此一來，您也可以視需要選擇每個類別的不同記錄輸出目標：

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLoggerProvider.cs":::

在上述程式碼中， <xref:Microsoft.Build.Logging.LoggerDescription.CreateLogger%2A> `ColorConsoleLogger` 會建立每個類別目錄名稱的單一實例，並將它儲存在中 [`ConcurrentDictionary<TKey,TValue>`](/dotnet/api/system.collections.concurrent.concurrentdictionary-2) 。

## <a name="usage-and-registration-of-the-custom-logger"></a>自訂記錄器的使用和註冊

若要加入自訂記錄提供者和對應的記錄器，請 <xref:Microsoft.Extensions.Logging.ILoggerProvider> <xref:Microsoft.Extensions.Logging.ILoggingBuilder> 從新增 <xref:Microsoft.Extensions.Hosting.HostingHostBuilderExtensions.ConfigureLogging(Microsoft.Extensions.Hosting.IHostBuilder,System.Action{Microsoft.Extensions.Logging.ILoggingBuilder})?displayProperty=nameWithType> ：

:::code language="csharp" source="snippets/configuration/console-custom-logging/Program.cs" range="23-39":::

會 `ILoggingBuilder` 建立一個或多個 `ILogger` 實例。 `ILogger`架構會使用這些實例來記錄資訊。

在上述程式碼中，至少為下列各項提供一個擴充方法 `ILoggerFactory` ：

:::code language="csharp" source="snippets/configuration/console-custom-logging/Extensions/ColorConsoleLoggerExtensions.cs":::

執行這個簡單的應用程式將會轉譯如下的主控台視窗：

:::image type="content" source="media/color-console-logger.png" alt-text="色彩主控台記錄器範例輸出":::

## <a name="see-also"></a>另請參閱

- [在 .net 中記錄](logging.md)。
- [.Net 中的記錄提供者](logging-providers.md)。
- [.Net 中的高效能記錄](high-performance-logging.md)。
