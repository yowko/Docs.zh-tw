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
# <a name="logging-with-the-azure-sdk-for-net"></a><span data-ttu-id="38a81-103">使用 .NET 的 Azure SDK 進行紀錄記錄</span><span class="sxs-lookup"><span data-stu-id="38a81-103">Logging with the Azure SDK for .NET</span></span>

<span data-ttu-id="38a81-104">.NET 用戶端庫的[Azure SDK](https://azure.microsoft.com/downloads/)包括記錄用戶端庫操作的能力。</span><span class="sxs-lookup"><span data-stu-id="38a81-104">The [Azure SDK](https://azure.microsoft.com/downloads/) for .NET client libraries includes the ability to log client library operations.</span></span> <span data-ttu-id="38a81-105">這允許您監視用戶端庫對 Azure 服務執行的 I/O 請求和回應。</span><span class="sxs-lookup"><span data-stu-id="38a81-105">This allows you to monitor I/O requests and responses that client libraries are making to Azure services.</span></span> <span data-ttu-id="38a81-106">通常,日誌用於調試或診斷通信問題。</span><span class="sxs-lookup"><span data-stu-id="38a81-106">Typically, the logs are used to debug or diagnose communication issues.</span></span> <span data-ttu-id="38a81-107">本文介紹了使用 .NET 的 Azure SDK 啟用日誌記錄的三種方法:</span><span class="sxs-lookup"><span data-stu-id="38a81-107">This article describes three approaches to enable logging with the Azure SDK for .NET:</span></span>

- <span data-ttu-id="38a81-108">登入主控台視窗</span><span class="sxs-lookup"><span data-stu-id="38a81-108">Log to the console window</span></span>
- <span data-ttu-id="38a81-109">登入到 .NET 診斷追蹤</span><span class="sxs-lookup"><span data-stu-id="38a81-109">Log to .NET diagnostics traces</span></span>
- <span data-ttu-id="38a81-110">設定自訂紀錄記錄</span><span class="sxs-lookup"><span data-stu-id="38a81-110">Configure custom logging</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38a81-111">本文適用於使用最新版本的 Azure SDK 的用戶端庫。</span><span class="sxs-lookup"><span data-stu-id="38a81-111">This article applies to client libraries that use the most recent versions of the Azure SDK for .NET.</span></span> <span data-ttu-id="38a81-112">要查看是否支援庫,請參閱[Azure SDK 最新版本](https://azure.github.io/azure-sdk/releases/latest/index.html)的清單。</span><span class="sxs-lookup"><span data-stu-id="38a81-112">To see if a library is supported, refer to the list of [Azure SDK latest releases](https://azure.github.io/azure-sdk/releases/latest/index.html).</span></span> <span data-ttu-id="38a81-113">如果應用程式使用的是 Azure SDK 用戶端庫的舊版本,請參閱適用的服務文檔中的特定說明。</span><span class="sxs-lookup"><span data-stu-id="38a81-113">If your application is using an older version of the Azure SDK client libraries, refer to specific instructions in the applicable service documentation.</span></span>

## <a name="log-information"></a><span data-ttu-id="38a81-114">記錄資訊</span><span class="sxs-lookup"><span data-stu-id="38a81-114">Log information</span></span>

<span data-ttu-id="38a81-115">SDK 會記錄以下資訊,對參數查詢和標頭值進行清理以刪除個人數據。</span><span class="sxs-lookup"><span data-stu-id="38a81-115">The SDK logs the following information, sanitizing parameter query and header values to remove personal data.</span></span>

<span data-ttu-id="38a81-116">HTTP 要求紀錄項目:</span><span class="sxs-lookup"><span data-stu-id="38a81-116">HTTP request log entry:</span></span>

- <span data-ttu-id="38a81-117">唯一識別碼</span><span class="sxs-lookup"><span data-stu-id="38a81-117">Unique ID</span></span>
- <span data-ttu-id="38a81-118">HTTP method</span><span class="sxs-lookup"><span data-stu-id="38a81-118">HTTP method</span></span>
- <span data-ttu-id="38a81-119">URI</span><span class="sxs-lookup"><span data-stu-id="38a81-119">URI</span></span>
- <span data-ttu-id="38a81-120">傳出要求標頭</span><span class="sxs-lookup"><span data-stu-id="38a81-120">Outgoing request headers</span></span>

<span data-ttu-id="38a81-121">HTTP 回應紀錄項目:</span><span class="sxs-lookup"><span data-stu-id="38a81-121">HTTP response log entry:</span></span>

- <span data-ttu-id="38a81-122">I/O 操作的持續時間(已過的時間)</span><span class="sxs-lookup"><span data-stu-id="38a81-122">Duration of I/O operation (time elapsed)</span></span>
- <span data-ttu-id="38a81-123">要求 ID</span><span class="sxs-lookup"><span data-stu-id="38a81-123">Request ID</span></span>
- <span data-ttu-id="38a81-124">HTTP 狀態碼</span><span class="sxs-lookup"><span data-stu-id="38a81-124">HTTP status code</span></span>
- <span data-ttu-id="38a81-125">HTTP 原因短語</span><span class="sxs-lookup"><span data-stu-id="38a81-125">HTTP reason phrase</span></span>
- <span data-ttu-id="38a81-126">回應標頭</span><span class="sxs-lookup"><span data-stu-id="38a81-126">Response headers</span></span>
- <span data-ttu-id="38a81-127">錯誤資訊(如果適用)</span><span class="sxs-lookup"><span data-stu-id="38a81-127">Error information, when applicable</span></span>

<span data-ttu-id="38a81-128">對於要求與回應內容:</span><span class="sxs-lookup"><span data-stu-id="38a81-128">For request and response content:</span></span>

- <span data-ttu-id="38a81-129">內容流作為文本或位元組,具體取決於內容類型標頭。</span><span class="sxs-lookup"><span data-stu-id="38a81-129">Content stream as text or bytes depending on the Content-Type header.</span></span>
     > <span data-ttu-id="38a81-130">[!注\* 預設情況下禁用內容日誌記錄。</span><span class="sxs-lookup"><span data-stu-id="38a81-130">[!NOTE} Content logging is disabled by default.</span></span> <span data-ttu-id="38a81-131">要開啟它,在`Diagnostics.IsLoggingContentEnabled``true`中`ClientOptions`設定為 。</span><span class="sxs-lookup"><span data-stu-id="38a81-131">To enable it, set `Diagnostics.IsLoggingContentEnabled` to `true` in `ClientOptions`.</span></span>

<span data-ttu-id="38a81-132">事件紀錄通常以以下三個等級之一輸出:</span><span class="sxs-lookup"><span data-stu-id="38a81-132">Event logs are output usually at one of these three levels:</span></span>

- <span data-ttu-id="38a81-133">要求與回應事件的資訊</span><span class="sxs-lookup"><span data-stu-id="38a81-133">Informational for request and response events</span></span>
- <span data-ttu-id="38a81-134">錯誤警告</span><span class="sxs-lookup"><span data-stu-id="38a81-134">Warning for errors</span></span>
- <span data-ttu-id="38a81-135">詳細郵件與內容紀錄記錄的冗長</span><span class="sxs-lookup"><span data-stu-id="38a81-135">Verbose for detailed messages and content logging</span></span>

## <a name="enable-logging-with-built-in-methods"></a><span data-ttu-id="38a81-136">使用內建方法啟用紀錄記錄</span><span class="sxs-lookup"><span data-stu-id="38a81-136">Enable logging with built-in methods</span></span>

<span data-ttu-id="38a81-137">.NET 用戶端的 Azure SDK 通過[`EventSource`類](/dotnet/api/system.diagnostics.tracing.eventsource)將事件記錄到 Windows 事件追蹤 (ETW),這是 .NET 的典型情況。</span><span class="sxs-lookup"><span data-stu-id="38a81-137">The Azure SDK for .NET client libraries log events to Event Tracing for Windows (ETW) via the [`EventSource` class](/dotnet/api/system.diagnostics.tracing.eventsource), which is typical for .NET.</span></span> <span data-ttu-id="38a81-138">事件源允許您在應用程式代碼中使用結構化日誌記錄,但性能開銷最小。</span><span class="sxs-lookup"><span data-stu-id="38a81-138">Event sources allow you to use structured logging in your application code with a minimal performance overhead.</span></span> <span data-ttu-id="38a81-139">要訪問這些事件日誌,您需要註冊事件偵聽器。</span><span class="sxs-lookup"><span data-stu-id="38a81-139">To gain access to these event logs, you need to register event listeners.</span></span>

<span data-ttu-id="38a81-140">SDK`Azure.Core.Diagnostics.AzureEventSourceListener`包括類別(在 Azure.Core NuGet 套件中定義),其中包含兩個靜態方法,可簡化 .NET 應用程式的全面`CreateConsoleLogger`紀錄記錄`CreateTraceLogger`:和 。</span><span class="sxs-lookup"><span data-stu-id="38a81-140">The SDK includes the `Azure.Core.Diagnostics.AzureEventSourceListener` class (defined in the Azure.Core NuGet package), which contains two static methods that simplify comprehensive logging for your .NET application: `CreateConsoleLogger` and `CreateTraceLogger`.</span></span> <span data-ttu-id="38a81-141">這些方法採用指定日誌級別的可選參數。</span><span class="sxs-lookup"><span data-stu-id="38a81-141">These methods take an optional parameter that specifies a log level.</span></span>

### <a name="log-to-the-console-window"></a><span data-ttu-id="38a81-142">登入主控台視窗</span><span class="sxs-lookup"><span data-stu-id="38a81-142">Log to the console window</span></span>

<span data-ttu-id="38a81-143">.NET 用戶端庫的 Azure SDK 的核心原則是簡化即時查看全面日誌的能力。</span><span class="sxs-lookup"><span data-stu-id="38a81-143">A core tenet of the Azure SDK for .NET client libraries is to simplify the ability to view comprehensive logs in real time.</span></span> <span data-ttu-id="38a81-144">此方法`CreateConsoleLogger`允許您使用一行代碼將紀錄傳送到主控台視窗:</span><span class="sxs-lookup"><span data-stu-id="38a81-144">The `CreateConsoleLogger` method allows you to send logs to the console window with a single line of code:</span></span>

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateConsoleLogger();
```

### <a name="log-to-diagnostic-traces"></a><span data-ttu-id="38a81-145">登入診斷追蹤</span><span class="sxs-lookup"><span data-stu-id="38a81-145">Log to diagnostic traces</span></span>

<span data-ttu-id="38a81-146">如果實現跟蹤偵聽器,則可以使用方法`CreateTraceLogger`登錄到標準 .NET 事件追蹤機制[`System.Diagnostics.Tracing`](https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing)()。</span><span class="sxs-lookup"><span data-stu-id="38a81-146">If you implement trace listeners, you can use the `CreateTraceLogger` method to log to the standard .NET event tracing mechanism ([`System.Diagnostics.Tracing`](https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing)).</span></span> <span data-ttu-id="38a81-147">有關 .NET 中事件追蹤的詳細資訊,請參閱[追蹤偵聽器](https://docs.microsoft.com/dotnet/framework/debug-trace-profile/trace-listeners)。</span><span class="sxs-lookup"><span data-stu-id="38a81-147">For more information on event tracing in .NET, see [Trace Listeners](https://docs.microsoft.com/dotnet/framework/debug-trace-profile/trace-listeners).</span></span> <span data-ttu-id="38a81-148">此範例指定詳細紀錄等級:</span><span class="sxs-lookup"><span data-stu-id="38a81-148">This example specifies a log level of verbose:</span></span>

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateTraceLogger(EventLevel.Verbose);
```

## <a name="configure-custom-logging"></a><span data-ttu-id="38a81-149">設定自訂紀錄記錄</span><span class="sxs-lookup"><span data-stu-id="38a81-149">Configure custom logging</span></span>

<span data-ttu-id="38a81-150">如上所述,您需要註冊事件偵聽器才能從 .NET 的 Azure SDK 接收日誌消息。</span><span class="sxs-lookup"><span data-stu-id="38a81-150">As mentioned above, you need to register event listeners to receive log messages from the Azure SDK for .NET.</span></span> <span data-ttu-id="38a81-151">如果不想使用上面簡化的方法實現全面日誌記錄,則可以構造`AzureEventSourceListener`類的實例,並傳遞您編寫的回調函數。</span><span class="sxs-lookup"><span data-stu-id="38a81-151">If you don’t want to implement comprehensive logging using one the simplified methods above, you can construct an instance of the `AzureEventSourceListener` class and pass it a callback function that you write.</span></span> <span data-ttu-id="38a81-152">此方法將收到日誌消息,您可以處理所需的日誌消息。</span><span class="sxs-lookup"><span data-stu-id="38a81-152">This method will receive log messages that you can process however you need to.</span></span> <span data-ttu-id="38a81-153">此外,在構造實例時,可以指定要包括的日誌級別。</span><span class="sxs-lookup"><span data-stu-id="38a81-153">In addition, when you construct the instance, you can specify the log levels to include.</span></span>

<span data-ttu-id="38a81-154">下面的範例創建一個事件偵聽器,該偵聽器使用自定義消息登錄到主控台,並篩選到級別詳細內容的 Azure 核心事件。</span><span class="sxs-lookup"><span data-stu-id="38a81-154">The following example creates an event listener that logs to the console with a custom message, and is filtered to Azure core events of the level verbose.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="38a81-155">後續步驟</span><span class="sxs-lookup"><span data-stu-id="38a81-155">Next steps</span></span>

- [<span data-ttu-id="38a81-156">為 Azure 應用服務中的應用程式啟用診斷紀錄記錄</span><span class="sxs-lookup"><span data-stu-id="38a81-156">Enable diagnostics logging for apps in Azure App Service</span></span>](https://docs.microsoft.com/azure/app-service/troubleshoot-diagnostic-logs)
- <span data-ttu-id="38a81-157">檢視[Azure 安全紀錄記錄與審核](https://docs.microsoft.com/azure/security/fundamentals/log-audit)選項</span><span class="sxs-lookup"><span data-stu-id="38a81-157">Review [Azure security logging and auditing](https://docs.microsoft.com/azure/security/fundamentals/log-audit) options</span></span>
- <span data-ttu-id="38a81-158">瞭解如何使用 Azure[平台紀錄](https://docs.microsoft.com/azure/azure-monitor/platform/platform-logs-overview)</span><span class="sxs-lookup"><span data-stu-id="38a81-158">Learn how to work with [Azure platform logs](https://docs.microsoft.com/azure/azure-monitor/platform/platform-logs-overview)</span></span>
- <span data-ttu-id="38a81-159">閱讀有關[.NET 核心紀錄記錄並追蹤的更多內容](https://docs.microsoft.com/dotnet/core/diagnostics/logging-tracing)</span><span class="sxs-lookup"><span data-stu-id="38a81-159">Read more about [.NET Core logging and tracing](https://docs.microsoft.com/dotnet/core/diagnostics/logging-tracing)</span></span>
