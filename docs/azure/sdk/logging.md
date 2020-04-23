---
title: 使用 .NET 的 Azure SDK 進行紀錄記錄
description: 瞭解如何使用 .NET 用戶端函式庫的 Azure SDK 啟用紀錄記錄
ms.date: 03/20/2020
ms.custom: azure-sdk-dotnet
ms.author: casoper
author: camsoper
ms.openlocfilehash: b277045a60ef5cc065d77dad84878872dedc963e
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "82071987"
---
# <a name="logging-with-the-azure-sdk-for-net"></a>使用 .NET 的 Azure SDK 進行紀錄記錄

.NET 用戶端庫的[Azure SDK](https://azure.microsoft.com/downloads/)包括記錄用戶端庫操作的能力。 這允許您監視用戶端庫對 Azure 服務執行的 I/O 請求和回應。 通常,日誌用於調試或診斷通信問題。 本文介紹了使用 .NET 的 Azure SDK 啟用日誌記錄的三種方法:

- 登入主控台視窗
- 登入到 .NET 診斷追蹤
- 設定自訂紀錄記錄

> [!IMPORTANT]
> 本文適用於使用最新版本的 Azure SDK 的用戶端庫。 要查看是否支援庫,請參閱[Azure SDK 最新版本](https://azure.github.io/azure-sdk/releases/latest/index.html)的清單。 如果應用程式使用的是 Azure SDK 用戶端庫的舊版本,請參閱適用的服務文檔中的特定說明。

## <a name="log-information"></a>記錄資訊

SDK 會記錄以下資訊,對參數查詢和標頭值進行清理以刪除個人數據。

HTTP 要求紀錄項目:

- 唯一識別碼
- HTTP method
- URI
- 傳出要求標頭

HTTP 回應紀錄項目:

- I/O 操作的持續時間(已過的時間)
- 要求 ID
- HTTP 狀態碼
- HTTP 原因短語
- 回應標頭
- 錯誤資訊(如果適用)

對於要求與回應內容:

- 內容流作為文本或位元組,具體取決於內容類型標頭。
     > [!注* 預設情況下禁用內容日誌記錄。 要開啟它,在`Diagnostics.IsLoggingContentEnabled``true`中`ClientOptions`設定為 。

事件紀錄通常以以下三個等級之一輸出:

- 要求與回應事件的資訊
- 錯誤警告
- 詳細郵件與內容紀錄記錄的冗長

## <a name="enable-logging-with-built-in-methods"></a>使用內建方法啟用紀錄記錄

.NET 用戶端的 Azure SDK 通過[`EventSource`類](/dotnet/api/system.diagnostics.tracing.eventsource)將事件記錄到 Windows 事件追蹤 (ETW),這是 .NET 的典型情況。 事件源允許您在應用程式代碼中使用結構化日誌記錄,但性能開銷最小。 要訪問這些事件日誌,您需要註冊事件偵聽器。

SDK`Azure.Core.Diagnostics.AzureEventSourceListener`包括類別(在 Azure.Core NuGet 套件中定義),其中包含兩個靜態方法,可簡化 .NET 應用程式的全面`CreateConsoleLogger`紀錄記錄`CreateTraceLogger`:和 。 這些方法採用指定日誌級別的可選參數。

### <a name="log-to-the-console-window"></a>登入主控台視窗

.NET 用戶端庫的 Azure SDK 的核心原則是簡化即時查看全面日誌的能力。 此方法`CreateConsoleLogger`允許您使用一行代碼將紀錄傳送到主控台視窗:

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateConsoleLogger();
```

### <a name="log-to-diagnostic-traces"></a>登入診斷追蹤

如果實現跟蹤偵聽器,則可以使用方法`CreateTraceLogger`登錄到標準 .NET 事件追蹤機制[`System.Diagnostics.Tracing`](https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing)()。 有關 .NET 中事件追蹤的詳細資訊,請參閱[追蹤偵聽器](https://docs.microsoft.com/dotnet/framework/debug-trace-profile/trace-listeners)。 此範例指定詳細紀錄等級:

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateTraceLogger(EventLevel.Verbose);
```

## <a name="configure-custom-logging"></a>設定自訂紀錄記錄

如上所述,您需要註冊事件偵聽器才能從 .NET 的 Azure SDK 接收日誌消息。 如果不想使用上面簡化的方法實現全面日誌記錄,則可以構造`AzureEventSourceListener`類的實例,並傳遞您編寫的回調函數。 此方法將收到日誌消息,您可以處理所需的日誌消息。 此外,在構造實例時,可以指定要包括的日誌級別。

下面的範例創建一個事件偵聽器,該偵聽器使用自定義消息登錄到主控台,並篩選到級別詳細內容的 Azure 核心事件。

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

## <a name="next-steps"></a>後續步驟

- [為 Azure 應用服務中的應用程式啟用診斷紀錄記錄](https://docs.microsoft.com/azure/app-service/troubleshoot-diagnostic-logs)
- 檢視[Azure 安全紀錄記錄與審核](https://docs.microsoft.com/azure/security/fundamentals/log-audit)選項
- 瞭解如何使用 Azure[平台紀錄](https://docs.microsoft.com/azure/azure-monitor/platform/platform-logs-overview)
- 閱讀有關[.NET 核心紀錄記錄並追蹤的更多內容](https://docs.microsoft.com/dotnet/core/diagnostics/logging-tracing)
