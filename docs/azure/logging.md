---
title: 使用 Azure SDK for .NET 進行記錄
description: 瞭解如何使用 Azure SDK for .NET 用戶端程式庫啟用記錄
ms.date: 03/20/2020
ms.custom: devx-track-dotnet
ms.author: casoper
author: camsoper
ms.openlocfilehash: 6adc485867e9bad401a15da19e6cb4424d2ddb13
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2020
ms.locfileid: "97700706"
---
# <a name="logging-with-the-azure-sdk-for-net"></a><span data-ttu-id="88aa1-103">使用 Azure SDK for .NET 進行記錄</span><span class="sxs-lookup"><span data-stu-id="88aa1-103">Logging with the Azure SDK for .NET</span></span>

<span data-ttu-id="88aa1-104">適用于 .NET 的 [AZURE SDK](https://azure.microsoft.com/downloads/) 用戶端程式庫包含記錄用戶端程式庫作業的功能。</span><span class="sxs-lookup"><span data-stu-id="88aa1-104">The [Azure SDK](https://azure.microsoft.com/downloads/) for .NET client libraries includes the ability to log client library operations.</span></span> <span data-ttu-id="88aa1-105">這可讓您監視用戶端程式庫對 Azure 服務進行的 i/o 要求和回應。</span><span class="sxs-lookup"><span data-stu-id="88aa1-105">This allows you to monitor I/O requests and responses that client libraries are making to Azure services.</span></span> <span data-ttu-id="88aa1-106">通常，記錄會用來偵測或診斷通訊問題。</span><span class="sxs-lookup"><span data-stu-id="88aa1-106">Typically, the logs are used to debug or diagnose communication issues.</span></span> <span data-ttu-id="88aa1-107">本文說明使用 Azure SDK for .NET 來啟用記錄的三種方法：</span><span class="sxs-lookup"><span data-stu-id="88aa1-107">This article describes three approaches to enable logging with the Azure SDK for .NET:</span></span>

- <span data-ttu-id="88aa1-108">記錄到主控台視窗</span><span class="sxs-lookup"><span data-stu-id="88aa1-108">Log to the console window</span></span>
- <span data-ttu-id="88aa1-109">記錄至 .NET 診斷追蹤</span><span class="sxs-lookup"><span data-stu-id="88aa1-109">Log to .NET diagnostics traces</span></span>
- <span data-ttu-id="88aa1-110">設定自訂記錄</span><span class="sxs-lookup"><span data-stu-id="88aa1-110">Configure custom logging</span></span>

> [!IMPORTANT]
> <span data-ttu-id="88aa1-111">本文適用于使用 Azure SDK for .NET 最新版本的用戶端程式庫。</span><span class="sxs-lookup"><span data-stu-id="88aa1-111">This article applies to client libraries that use the most recent versions of the Azure SDK for .NET.</span></span> <span data-ttu-id="88aa1-112">若要查看是否支援程式庫，請參閱 [Azure SDK 最新版本清單](https://azure.github.io/azure-sdk/releases/latest/index.html)。</span><span class="sxs-lookup"><span data-stu-id="88aa1-112">To see if a library is supported, refer to the list of [Azure SDK latest releases](https://azure.github.io/azure-sdk/releases/latest/index.html).</span></span> <span data-ttu-id="88aa1-113">如果您的應用程式使用較舊版本的 Azure SDK 用戶端程式庫，請參閱適用的服務文件中的特定指示。</span><span class="sxs-lookup"><span data-stu-id="88aa1-113">If your application is using an older version of the Azure SDK client libraries, refer to specific instructions in the applicable service documentation.</span></span>

## <a name="log-information"></a><span data-ttu-id="88aa1-114">記錄資訊</span><span class="sxs-lookup"><span data-stu-id="88aa1-114">Log information</span></span>

<span data-ttu-id="88aa1-115">SDK 會記錄下列資訊、淨化參數查詢和標頭值，以移除個人資料。</span><span class="sxs-lookup"><span data-stu-id="88aa1-115">The SDK logs the following information, sanitizing parameter query and header values to remove personal data.</span></span>

<span data-ttu-id="88aa1-116">HTTP 要求記錄專案：</span><span class="sxs-lookup"><span data-stu-id="88aa1-116">HTTP request log entry:</span></span>

- <span data-ttu-id="88aa1-117">唯一識別碼</span><span class="sxs-lookup"><span data-stu-id="88aa1-117">Unique ID</span></span>
- <span data-ttu-id="88aa1-118">HTTP method</span><span class="sxs-lookup"><span data-stu-id="88aa1-118">HTTP method</span></span>
- <span data-ttu-id="88aa1-119">URI</span><span class="sxs-lookup"><span data-stu-id="88aa1-119">URI</span></span>
- <span data-ttu-id="88aa1-120">連出要求標頭</span><span class="sxs-lookup"><span data-stu-id="88aa1-120">Outgoing request headers</span></span>

<span data-ttu-id="88aa1-121">HTTP 回應記錄專案：</span><span class="sxs-lookup"><span data-stu-id="88aa1-121">HTTP response log entry:</span></span>

- <span data-ttu-id="88aa1-122">I/o 作業的持續時間 (經過的時間) </span><span class="sxs-lookup"><span data-stu-id="88aa1-122">Duration of I/O operation (time elapsed)</span></span>
- <span data-ttu-id="88aa1-123">要求識別碼</span><span class="sxs-lookup"><span data-stu-id="88aa1-123">Request ID</span></span>
- <span data-ttu-id="88aa1-124">HTTP 狀態碼</span><span class="sxs-lookup"><span data-stu-id="88aa1-124">HTTP status code</span></span>
- <span data-ttu-id="88aa1-125">HTTP 原因片語</span><span class="sxs-lookup"><span data-stu-id="88aa1-125">HTTP reason phrase</span></span>
- <span data-ttu-id="88aa1-126">回應標頭</span><span class="sxs-lookup"><span data-stu-id="88aa1-126">Response headers</span></span>
- <span data-ttu-id="88aa1-127">錯誤資訊（若適用）</span><span class="sxs-lookup"><span data-stu-id="88aa1-127">Error information, when applicable</span></span>

<span data-ttu-id="88aa1-128">針對要求和回應內容：</span><span class="sxs-lookup"><span data-stu-id="88aa1-128">For request and response content:</span></span>

- <span data-ttu-id="88aa1-129">根據 Content-type 標頭，以文字或位元組為依據的內容資料流程。</span><span class="sxs-lookup"><span data-stu-id="88aa1-129">Content stream as text or bytes depending on the Content-Type header.</span></span>
     > <span data-ttu-id="88aa1-130">[!注意} 預設會停用內容記錄。</span><span class="sxs-lookup"><span data-stu-id="88aa1-130">[!NOTE} Content logging is disabled by default.</span></span> <span data-ttu-id="88aa1-131">若要啟用它， `Diagnostics.IsLoggingContentEnabled` 請 `true` 在中將設定為 `ClientOptions` 。</span><span class="sxs-lookup"><span data-stu-id="88aa1-131">To enable it, set `Diagnostics.IsLoggingContentEnabled` to `true` in `ClientOptions`.</span></span>

<span data-ttu-id="88aa1-132">事件記錄檔的輸出通常是下列三個層級的其中一種：</span><span class="sxs-lookup"><span data-stu-id="88aa1-132">Event logs are output usually at one of these three levels:</span></span>

- <span data-ttu-id="88aa1-133">要求和回應事件的資訊</span><span class="sxs-lookup"><span data-stu-id="88aa1-133">Informational for request and response events</span></span>
- <span data-ttu-id="88aa1-134">錯誤的警告</span><span class="sxs-lookup"><span data-stu-id="88aa1-134">Warning for errors</span></span>
- <span data-ttu-id="88aa1-135">詳細訊息和內容記錄的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="88aa1-135">Verbose for detailed messages and content logging</span></span>

## <a name="enable-logging-with-built-in-methods"></a><span data-ttu-id="88aa1-136">使用內建方法啟用記錄</span><span class="sxs-lookup"><span data-stu-id="88aa1-136">Enable logging with built-in methods</span></span>

<span data-ttu-id="88aa1-137">Azure SDK for .NET 用戶端程式庫會透過[ `EventSource` 類別](/dotnet/api/system.diagnostics.tracing.eventsource)（通常是 .net）將事件記錄到 Windows 的事件追蹤 (ETW) 。</span><span class="sxs-lookup"><span data-stu-id="88aa1-137">The Azure SDK for .NET client libraries log events to Event Tracing for Windows (ETW) via the [`EventSource` class](/dotnet/api/system.diagnostics.tracing.eventsource), which is typical for .NET.</span></span> <span data-ttu-id="88aa1-138">事件來源可讓您在應用程式程式碼中使用結構化記錄，並提供極低的效能額外負荷。</span><span class="sxs-lookup"><span data-stu-id="88aa1-138">Event sources allow you to use structured logging in your application code with a minimal performance overhead.</span></span> <span data-ttu-id="88aa1-139">若要取得這些事件記錄檔的存取權，您必須註冊事件接聽程式。</span><span class="sxs-lookup"><span data-stu-id="88aa1-139">To gain access to these event logs, you need to register event listeners.</span></span>

<span data-ttu-id="88aa1-140">SDK 包含 `Azure.Core.Diagnostics.AzureEventSourceListener` (定義于 Azure Core NuGet 套件) 中的類別，其中包含兩個可簡化 .net 應用程式完整記錄的靜態方法： `CreateConsoleLogger` 和 `CreateTraceLogger` 。</span><span class="sxs-lookup"><span data-stu-id="88aa1-140">The SDK includes the `Azure.Core.Diagnostics.AzureEventSourceListener` class (defined in the Azure.Core NuGet package), which contains two static methods that simplify comprehensive logging for your .NET application: `CreateConsoleLogger` and `CreateTraceLogger`.</span></span> <span data-ttu-id="88aa1-141">這些方法會採用指定記錄層級的選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="88aa1-141">These methods take an optional parameter that specifies a log level.</span></span>

### <a name="log-to-the-console-window"></a><span data-ttu-id="88aa1-142">記錄到主控台視窗</span><span class="sxs-lookup"><span data-stu-id="88aa1-142">Log to the console window</span></span>

<span data-ttu-id="88aa1-143">Azure SDK for .NET 用戶端程式庫的核心原則是簡化即時查看完整記錄的功能。</span><span class="sxs-lookup"><span data-stu-id="88aa1-143">A core tenet of the Azure SDK for .NET client libraries is to simplify the ability to view comprehensive logs in real time.</span></span> <span data-ttu-id="88aa1-144">`CreateConsoleLogger`方法可讓您使用一行程式碼將記錄傳送至主控台視窗：</span><span class="sxs-lookup"><span data-stu-id="88aa1-144">The `CreateConsoleLogger` method allows you to send logs to the console window with a single line of code:</span></span>

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateConsoleLogger();
```

### <a name="log-to-diagnostic-traces"></a><span data-ttu-id="88aa1-145">記錄到診斷追蹤</span><span class="sxs-lookup"><span data-stu-id="88aa1-145">Log to diagnostic traces</span></span>

<span data-ttu-id="88aa1-146">如果您執行追蹤接聽程式，您可以使用 `CreateTraceLogger` 方法來記錄至標準的 .net 事件追蹤機制， ([`System.Diagnostics.Tracing`](/dotnet/api/system.diagnostics.tracing)) 。</span><span class="sxs-lookup"><span data-stu-id="88aa1-146">If you implement trace listeners, you can use the `CreateTraceLogger` method to log to the standard .NET event tracing mechanism ([`System.Diagnostics.Tracing`](/dotnet/api/system.diagnostics.tracing)).</span></span> <span data-ttu-id="88aa1-147">如需 .NET 中事件追蹤的詳細資訊，請參閱 [追蹤](../framework/debug-trace-profile/trace-listeners.md)接聽程式。</span><span class="sxs-lookup"><span data-stu-id="88aa1-147">For more information on event tracing in .NET, see [Trace Listeners](../framework/debug-trace-profile/trace-listeners.md).</span></span> <span data-ttu-id="88aa1-148">此範例會指定詳細資訊的記錄層級：</span><span class="sxs-lookup"><span data-stu-id="88aa1-148">This example specifies a log level of verbose:</span></span>

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateTraceLogger(EventLevel.Verbose);
```

## <a name="configure-custom-logging"></a><span data-ttu-id="88aa1-149">設定自訂記錄</span><span class="sxs-lookup"><span data-stu-id="88aa1-149">Configure custom logging</span></span>

<span data-ttu-id="88aa1-150">如先前所述，您必須註冊事件接聽程式，以從 Azure SDK for .NET 接收記錄訊息。</span><span class="sxs-lookup"><span data-stu-id="88aa1-150">As mentioned above, you need to register event listeners to receive log messages from the Azure SDK for .NET.</span></span> <span data-ttu-id="88aa1-151">如果您不想要使用上述簡化的方法來執行完整的記錄，您可以建立類別的實例 `AzureEventSourceListener` ，並將您撰寫的回呼函數傳遞給它。</span><span class="sxs-lookup"><span data-stu-id="88aa1-151">If you don’t want to implement comprehensive logging using one the simplified methods above, you can construct an instance of the `AzureEventSourceListener` class and pass it a callback function that you write.</span></span> <span data-ttu-id="88aa1-152">這個方法會接收您可以處理的記錄檔訊息，不過您必須這樣做。</span><span class="sxs-lookup"><span data-stu-id="88aa1-152">This method will receive log messages that you can process however you need to.</span></span> <span data-ttu-id="88aa1-153">此外，當您建立實例時，您可以指定要包含的記錄層級。</span><span class="sxs-lookup"><span data-stu-id="88aa1-153">In addition, when you construct the instance, you can specify the log levels to include.</span></span>

<span data-ttu-id="88aa1-154">下列範例會建立事件接聽程式，以使用自訂訊息來記錄至主控台，並篩選為層級詳細資訊的 Azure 核心事件。</span><span class="sxs-lookup"><span data-stu-id="88aa1-154">The following example creates an event listener that logs to the console with a custom message, and is filtered to Azure core events of the level verbose.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="88aa1-155">後續步驟</span><span class="sxs-lookup"><span data-stu-id="88aa1-155">Next steps</span></span>

- [<span data-ttu-id="88aa1-156">在 Azure App Service 中針對應用程式啟用診斷記錄</span><span class="sxs-lookup"><span data-stu-id="88aa1-156">Enable diagnostics logging for apps in Azure App Service</span></span>](/azure/app-service/troubleshoot-diagnostic-logs)
- <span data-ttu-id="88aa1-157">查看 [Azure 安全性記錄和審核](/azure/security/fundamentals/log-audit) 選項</span><span class="sxs-lookup"><span data-stu-id="88aa1-157">Review [Azure security logging and auditing](/azure/security/fundamentals/log-audit) options</span></span>
- <span data-ttu-id="88aa1-158">瞭解如何使用 [Azure 平臺記錄](/azure/azure-monitor/platform/platform-logs-overview)</span><span class="sxs-lookup"><span data-stu-id="88aa1-158">Learn how to work with [Azure platform logs](/azure/azure-monitor/platform/platform-logs-overview)</span></span>
- <span data-ttu-id="88aa1-159">深入瞭解 [.Net Core 記錄和追蹤](../core/diagnostics/logging-tracing.md)</span><span class="sxs-lookup"><span data-stu-id="88aa1-159">Read more about [.NET Core logging and tracing](../core/diagnostics/logging-tracing.md)</span></span>
