---
title: 使用 Azure SDK for .NET 進行記錄
description: 瞭解如何使用 Azure SDK for .NET 用戶端程式庫來啟用記錄
ms.date: 03/20/2020
ms.custom: azure-sdk-dotnet
ms.author: casoper
author: camsoper
ms.openlocfilehash: 5a1fb35aeca034a7cdd1caa813a3839919a5f926
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174913"
---
# <a name="logging-with-the-azure-sdk-for-net"></a>使用 Azure SDK for .NET 進行記錄

[AZURE SDK](https://azure.microsoft.com/downloads/) for .net 用戶端程式庫包含記錄用戶端程式庫作業的功能。 這可讓您監視用戶端程式庫對 Azure 服務所做的 i/o 要求和回應。 一般來說，記錄是用來偵測或診斷通訊問題。 本文說明使用 Azure SDK for .NET 來啟用記錄的三種方法：

- 登入主控台視窗
- 記錄至 .NET 診斷追蹤
- 設定自訂記錄

> [!IMPORTANT]
> 本文適用于使用最新版本的 Azure SDK for .NET 的用戶端程式庫。 若要查看是否支援程式庫，請參閱[AZURE SDK 最新版本](https://azure.github.io/azure-sdk/releases/latest/index.html)清單。 如果您的應用程式使用較舊版本的 Azure SDK 用戶端程式庫，請參閱適用的服務檔中的特定指示。

## <a name="log-information"></a>記錄資訊

SDK 會記錄下列資訊、淨化參數查詢和標頭值，以移除個人資料。

HTTP 要求記錄專案：

- 唯一識別碼
- HTTP method
- URI
- 傳出要求標頭

HTTP 回應記錄專案：

-  (經過時間) 的 i/o 作業持續時間
- 要求識別碼
- HTTP 狀態碼
- HTTP 原因片語
- 回應標頭
- 錯誤資訊（如果適用）

針對要求和回應內容：

- 根據 Content-type 標頭，將內容串流為文字或位元組。
     > [!注意} 預設會停用內容記錄。 若要啟用它，請將設定 `Diagnostics.IsLoggingContentEnabled` 為 `true` 中的 `ClientOptions` 。

事件記錄檔的輸出通常是下列三個層級的其中一種：

- 要求和回應事件的資訊
- 錯誤的警告
- 詳細訊息和內容記錄的詳細資訊

## <a name="enable-logging-with-built-in-methods"></a>使用內建方法來啟用記錄

Azure SDK for .NET 用戶端程式庫會透過[ `EventSource` 類別](/dotnet/api/system.diagnostics.tracing.eventsource)，將事件記錄到 Windows 的事件追蹤 (ETW) ，這通常適用于 .net。 事件來源可讓您在應用程式程式碼中使用結構化記錄，以最少的效能額外負荷。 若要取得這些事件記錄檔的存取權，您必須註冊事件接聽程式。

SDK 包含在 `Azure.Core.Diagnostics.AzureEventSourceListener` Azure Core NuGet 套件) 中定義的類別 (，其中包含兩個靜態方法，可簡化 .net 應用程式的完整記錄： `CreateConsoleLogger` 和 `CreateTraceLogger` 。 這些方法會接受指定記錄層級的選擇性參數。

### <a name="log-to-the-console-window"></a>登入主控台視窗

Azure SDK for .NET 用戶端程式庫的核心原則，是為了簡化即時查看完整記錄的能力。 `CreateConsoleLogger`方法可讓您使用一行程式碼，將記錄傳送至主控台視窗：

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateConsoleLogger();
```

### <a name="log-to-diagnostic-traces"></a>記錄到診斷追蹤

如果您執行追蹤接聽程式，您可以使用 `CreateTraceLogger` 方法來記錄至標準 .net 事件追蹤機制， ([`System.Diagnostics.Tracing`](/dotnet/api/system.diagnostics.tracing)) 。 如需 .NET 中事件追蹤的詳細資訊，請參閱[追蹤](/dotnet/framework/debug-trace-profile/trace-listeners)接聽程式。 這個範例會指定詳細資訊的記錄層級：

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateTraceLogger(EventLevel.Verbose);
```

## <a name="configure-custom-logging"></a>設定自訂記錄

如先前所述，您必須註冊事件接聽程式，以從 Azure SDK for .NET 接收記錄訊息。 如果您不想使用上述簡化的方法來執行完整的記錄，您可以建立類別的實例， `AzureEventSourceListener` 並將您所撰寫的回呼函數傳遞給它。 這個方法會接收您可以處理的記錄檔訊息，不過您必須這麼做。 此外，當您建立實例時，可以指定要包含的記錄層級。

下列範例會建立事件接聽程式，以使用自訂訊息來登入主控台，並篩選至層級詳細資訊的 Azure 核心事件。

```csharp
using AzureEventSourceListener listener = new AzureEventSourceListener((e, message) =>
    {
        // Only log messages from Azure-Core event source
        if (e.EventSource.Name == "Azure-Core")
        {
            Console.WriteLine($"{DateTime.Now} {message}");
        }
    },
    level: EventLevel.Verbose);
```

## <a name="next-steps"></a>接下來的步驟

- [在 Azure App Service 中啟用應用程式的診斷記錄功能](/azure/app-service/troubleshoot-diagnostic-logs)
- 查看[Azure 安全性記錄和審核](/azure/security/fundamentals/log-audit)選項
- 瞭解如何使用[Azure 平臺記錄](/azure/azure-monitor/platform/platform-logs-overview)
- 深入瞭解[.Net Core 記錄和追蹤](/dotnet/core/diagnostics/logging-tracing)
