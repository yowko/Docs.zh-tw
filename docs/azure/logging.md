---
title: 使用 Azure SDK for .NET 進行記錄
description: 瞭解如何使用 Azure SDK for .NET 用戶端程式庫來啟用記錄
ms.date: 03/20/2020
ms.custom: azure-sdk-dotnet
ms.author: casoper
author: camsoper
ms.openlocfilehash: 0b255713bc9c13e0cbdaeb25a3d0fe46e91e815d
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416033"
---
# <a name="logging-with-the-azure-sdk-for-net"></a><span data-ttu-id="ca6b1-103">使用 Azure SDK for .NET 進行記錄</span><span class="sxs-lookup"><span data-stu-id="ca6b1-103">Logging with the Azure SDK for .NET</span></span>

<span data-ttu-id="ca6b1-104">[AZURE SDK](https://azure.microsoft.com/downloads/) for .net 用戶端程式庫包含記錄用戶端程式庫作業的功能。</span><span class="sxs-lookup"><span data-stu-id="ca6b1-104">The [Azure SDK](https://azure.microsoft.com/downloads/) for .NET client libraries includes the ability to log client library operations.</span></span> <span data-ttu-id="ca6b1-105">這可讓您監視用戶端程式庫對 Azure 服務所做的 i/o 要求和回應。</span><span class="sxs-lookup"><span data-stu-id="ca6b1-105">This allows you to monitor I/O requests and responses that client libraries are making to Azure services.</span></span> <span data-ttu-id="ca6b1-106">一般來說，記錄是用來偵測或診斷通訊問題。</span><span class="sxs-lookup"><span data-stu-id="ca6b1-106">Typically, the logs are used to debug or diagnose communication issues.</span></span> <span data-ttu-id="ca6b1-107">本文說明使用 Azure SDK for .NET 來啟用記錄的三種方法：</span><span class="sxs-lookup"><span data-stu-id="ca6b1-107">This article describes three approaches to enable logging with the Azure SDK for .NET:</span></span>

- <span data-ttu-id="ca6b1-108">登入主控台視窗</span><span class="sxs-lookup"><span data-stu-id="ca6b1-108">Log to the console window</span></span>
- <span data-ttu-id="ca6b1-109">記錄至 .NET 診斷追蹤</span><span class="sxs-lookup"><span data-stu-id="ca6b1-109">Log to .NET diagnostics traces</span></span>
- <span data-ttu-id="ca6b1-110">設定自訂記錄</span><span class="sxs-lookup"><span data-stu-id="ca6b1-110">Configure custom logging</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ca6b1-111">本文適用于使用最新版本的 Azure SDK for .NET 的用戶端程式庫。</span><span class="sxs-lookup"><span data-stu-id="ca6b1-111">This article applies to client libraries that use the most recent versions of the Azure SDK for .NET.</span></span> <span data-ttu-id="ca6b1-112">若要查看是否支援程式庫，請參閱[AZURE SDK 最新版本](https://azure.github.io/azure-sdk/releases/latest/index.html)清單。</span><span class="sxs-lookup"><span data-stu-id="ca6b1-112">To see if a library is supported, refer to the list of [Azure SDK latest releases](https://azure.github.io/azure-sdk/releases/latest/index.html).</span></span> <span data-ttu-id="ca6b1-113">如果您的應用程式使用較舊版本的 Azure SDK 用戶端程式庫，請參閱適用的服務檔中的特定指示。</span><span class="sxs-lookup"><span data-stu-id="ca6b1-113">If your application is using an older version of the Azure SDK client libraries, refer to specific instructions in the applicable service documentation.</span></span>

## <a name="log-information"></a><span data-ttu-id="ca6b1-114">記錄資訊</span><span class="sxs-lookup"><span data-stu-id="ca6b1-114">Log information</span></span>

<span data-ttu-id="ca6b1-115">SDK 會記錄下列資訊、淨化參數查詢和標頭值，以移除個人資料。</span><span class="sxs-lookup"><span data-stu-id="ca6b1-115">The SDK logs the following information, sanitizing parameter query and header values to remove personal data.</span></span>

<span data-ttu-id="ca6b1-116">HTTP 要求記錄專案：</span><span class="sxs-lookup"><span data-stu-id="ca6b1-116">HTTP request log entry:</span></span>

- <span data-ttu-id="ca6b1-117">唯一識別碼</span><span class="sxs-lookup"><span data-stu-id="ca6b1-117">Unique ID</span></span>
- <span data-ttu-id="ca6b1-118">HTTP method</span><span class="sxs-lookup"><span data-stu-id="ca6b1-118">HTTP method</span></span>
- <span data-ttu-id="ca6b1-119">URI</span><span class="sxs-lookup"><span data-stu-id="ca6b1-119">URI</span></span>
- <span data-ttu-id="ca6b1-120">傳出要求標頭</span><span class="sxs-lookup"><span data-stu-id="ca6b1-120">Outgoing request headers</span></span>

<span data-ttu-id="ca6b1-121">HTTP 回應記錄專案：</span><span class="sxs-lookup"><span data-stu-id="ca6b1-121">HTTP response log entry:</span></span>

- <span data-ttu-id="ca6b1-122">I/o 作業的持續時間（經過時間）</span><span class="sxs-lookup"><span data-stu-id="ca6b1-122">Duration of I/O operation (time elapsed)</span></span>
- <span data-ttu-id="ca6b1-123">要求識別碼</span><span class="sxs-lookup"><span data-stu-id="ca6b1-123">Request ID</span></span>
- <span data-ttu-id="ca6b1-124">HTTP 狀態碼</span><span class="sxs-lookup"><span data-stu-id="ca6b1-124">HTTP status code</span></span>
- <span data-ttu-id="ca6b1-125">HTTP 原因片語</span><span class="sxs-lookup"><span data-stu-id="ca6b1-125">HTTP reason phrase</span></span>
- <span data-ttu-id="ca6b1-126">回應標頭</span><span class="sxs-lookup"><span data-stu-id="ca6b1-126">Response headers</span></span>
- <span data-ttu-id="ca6b1-127">錯誤資訊（如果適用）</span><span class="sxs-lookup"><span data-stu-id="ca6b1-127">Error information, when applicable</span></span>

<span data-ttu-id="ca6b1-128">針對要求和回應內容：</span><span class="sxs-lookup"><span data-stu-id="ca6b1-128">For request and response content:</span></span>

- <span data-ttu-id="ca6b1-129">根據 Content-type 標頭，將內容串流為文字或位元組。</span><span class="sxs-lookup"><span data-stu-id="ca6b1-129">Content stream as text or bytes depending on the Content-Type header.</span></span>
     > <span data-ttu-id="ca6b1-130">[!注意} 預設會停用內容記錄。</span><span class="sxs-lookup"><span data-stu-id="ca6b1-130">[!NOTE} Content logging is disabled by default.</span></span> <span data-ttu-id="ca6b1-131">若要啟用它，請將設定 `Diagnostics.IsLoggingContentEnabled` 為 `true` 中的 `ClientOptions` 。</span><span class="sxs-lookup"><span data-stu-id="ca6b1-131">To enable it, set `Diagnostics.IsLoggingContentEnabled` to `true` in `ClientOptions`.</span></span>

<span data-ttu-id="ca6b1-132">事件記錄檔的輸出通常是下列三個層級的其中一種：</span><span class="sxs-lookup"><span data-stu-id="ca6b1-132">Event logs are output usually at one of these three levels:</span></span>

- <span data-ttu-id="ca6b1-133">要求和回應事件的資訊</span><span class="sxs-lookup"><span data-stu-id="ca6b1-133">Informational for request and response events</span></span>
- <span data-ttu-id="ca6b1-134">錯誤的警告</span><span class="sxs-lookup"><span data-stu-id="ca6b1-134">Warning for errors</span></span>
- <span data-ttu-id="ca6b1-135">詳細訊息和內容記錄的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="ca6b1-135">Verbose for detailed messages and content logging</span></span>

## <a name="enable-logging-with-built-in-methods"></a><span data-ttu-id="ca6b1-136">使用內建方法來啟用記錄</span><span class="sxs-lookup"><span data-stu-id="ca6b1-136">Enable logging with built-in methods</span></span>

<span data-ttu-id="ca6b1-137">Azure SDK for .NET 用戶端程式庫會透過[ `EventSource` 類別](/dotnet/api/system.diagnostics.tracing.eventsource)，將事件記錄到 Windows 事件追蹤（ETW），這通常適用于 .net。</span><span class="sxs-lookup"><span data-stu-id="ca6b1-137">The Azure SDK for .NET client libraries log events to Event Tracing for Windows (ETW) via the [`EventSource` class](/dotnet/api/system.diagnostics.tracing.eventsource), which is typical for .NET.</span></span> <span data-ttu-id="ca6b1-138">事件來源可讓您在應用程式程式碼中使用結構化記錄，以最少的效能額外負荷。</span><span class="sxs-lookup"><span data-stu-id="ca6b1-138">Event sources allow you to use structured logging in your application code with a minimal performance overhead.</span></span> <span data-ttu-id="ca6b1-139">若要取得這些事件記錄檔的存取權，您必須註冊事件接聽程式。</span><span class="sxs-lookup"><span data-stu-id="ca6b1-139">To gain access to these event logs, you need to register event listeners.</span></span>

<span data-ttu-id="ca6b1-140">SDK 包含 `Azure.Core.Diagnostics.AzureEventSourceListener` 類別（定義于 Azure Core NuGet 套件中），其中包含兩個靜態方法，可簡化 .net 應用程式的完整記錄： `CreateConsoleLogger` 和 `CreateTraceLogger` 。</span><span class="sxs-lookup"><span data-stu-id="ca6b1-140">The SDK includes the `Azure.Core.Diagnostics.AzureEventSourceListener` class (defined in the Azure.Core NuGet package), which contains two static methods that simplify comprehensive logging for your .NET application: `CreateConsoleLogger` and `CreateTraceLogger`.</span></span> <span data-ttu-id="ca6b1-141">這些方法會接受指定記錄層級的選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="ca6b1-141">These methods take an optional parameter that specifies a log level.</span></span>

### <a name="log-to-the-console-window"></a><span data-ttu-id="ca6b1-142">登入主控台視窗</span><span class="sxs-lookup"><span data-stu-id="ca6b1-142">Log to the console window</span></span>

<span data-ttu-id="ca6b1-143">Azure SDK for .NET 用戶端程式庫的核心原則，是為了簡化即時查看完整記錄的能力。</span><span class="sxs-lookup"><span data-stu-id="ca6b1-143">A core tenet of the Azure SDK for .NET client libraries is to simplify the ability to view comprehensive logs in real time.</span></span> <span data-ttu-id="ca6b1-144">`CreateConsoleLogger`方法可讓您使用一行程式碼，將記錄傳送至主控台視窗：</span><span class="sxs-lookup"><span data-stu-id="ca6b1-144">The `CreateConsoleLogger` method allows you to send logs to the console window with a single line of code:</span></span>

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateConsoleLogger();
```

### <a name="log-to-diagnostic-traces"></a><span data-ttu-id="ca6b1-145">記錄到診斷追蹤</span><span class="sxs-lookup"><span data-stu-id="ca6b1-145">Log to diagnostic traces</span></span>

<span data-ttu-id="ca6b1-146">如果您要執行追蹤接聽程式，您可以使用 `CreateTraceLogger` 方法來記錄標準 .net 事件追蹤機制（ [`System.Diagnostics.Tracing`](/dotnet/api/system.diagnostics.tracing) ）。</span><span class="sxs-lookup"><span data-stu-id="ca6b1-146">If you implement trace listeners, you can use the `CreateTraceLogger` method to log to the standard .NET event tracing mechanism ([`System.Diagnostics.Tracing`](/dotnet/api/system.diagnostics.tracing)).</span></span> <span data-ttu-id="ca6b1-147">如需 .NET 中事件追蹤的詳細資訊，請參閱[追蹤](../framework/debug-trace-profile/trace-listeners.md)接聽程式。</span><span class="sxs-lookup"><span data-stu-id="ca6b1-147">For more information on event tracing in .NET, see [Trace Listeners](../framework/debug-trace-profile/trace-listeners.md).</span></span> <span data-ttu-id="ca6b1-148">這個範例會指定詳細資訊的記錄層級：</span><span class="sxs-lookup"><span data-stu-id="ca6b1-148">This example specifies a log level of verbose:</span></span>

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateTraceLogger(EventLevel.Verbose);
```

## <a name="configure-custom-logging"></a><span data-ttu-id="ca6b1-149">設定自訂記錄</span><span class="sxs-lookup"><span data-stu-id="ca6b1-149">Configure custom logging</span></span>

<span data-ttu-id="ca6b1-150">如先前所述，您必須註冊事件接聽程式，以從 Azure SDK for .NET 接收記錄訊息。</span><span class="sxs-lookup"><span data-stu-id="ca6b1-150">As mentioned above, you need to register event listeners to receive log messages from the Azure SDK for .NET.</span></span> <span data-ttu-id="ca6b1-151">如果您不想使用上述簡化的方法來執行完整的記錄，您可以建立類別的實例， `AzureEventSourceListener` 並將您所撰寫的回呼函數傳遞給它。</span><span class="sxs-lookup"><span data-stu-id="ca6b1-151">If you don’t want to implement comprehensive logging using one the simplified methods above, you can construct an instance of the `AzureEventSourceListener` class and pass it a callback function that you write.</span></span> <span data-ttu-id="ca6b1-152">這個方法會接收您可以處理的記錄檔訊息，不過您必須這麼做。</span><span class="sxs-lookup"><span data-stu-id="ca6b1-152">This method will receive log messages that you can process however you need to.</span></span> <span data-ttu-id="ca6b1-153">此外，當您建立實例時，可以指定要包含的記錄層級。</span><span class="sxs-lookup"><span data-stu-id="ca6b1-153">In addition, when you construct the instance, you can specify the log levels to include.</span></span>

<span data-ttu-id="ca6b1-154">下列範例會建立事件接聽程式，以使用自訂訊息來登入主控台，並篩選至層級詳細資訊的 Azure 核心事件。</span><span class="sxs-lookup"><span data-stu-id="ca6b1-154">The following example creates an event listener that logs to the console with a custom message, and is filtered to Azure core events of the level verbose.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="ca6b1-155">後續步驟</span><span class="sxs-lookup"><span data-stu-id="ca6b1-155">Next steps</span></span>

- [<span data-ttu-id="ca6b1-156">在 Azure App Service 中啟用應用程式的診斷記錄功能</span><span class="sxs-lookup"><span data-stu-id="ca6b1-156">Enable diagnostics logging for apps in Azure App Service</span></span>](/azure/app-service/troubleshoot-diagnostic-logs)
- <span data-ttu-id="ca6b1-157">查看[Azure 安全性記錄和審核](/azure/security/fundamentals/log-audit)選項</span><span class="sxs-lookup"><span data-stu-id="ca6b1-157">Review [Azure security logging and auditing](/azure/security/fundamentals/log-audit) options</span></span>
- <span data-ttu-id="ca6b1-158">瞭解如何使用[Azure 平臺記錄](/azure/azure-monitor/platform/platform-logs-overview)</span><span class="sxs-lookup"><span data-stu-id="ca6b1-158">Learn how to work with [Azure platform logs](/azure/azure-monitor/platform/platform-logs-overview)</span></span>
- <span data-ttu-id="ca6b1-159">深入瞭解[.Net Core 記錄和追蹤](../core/diagnostics/logging-tracing.md)</span><span class="sxs-lookup"><span data-stu-id="ca6b1-159">Read more about [.NET Core logging and tracing](../core/diagnostics/logging-tracing.md)</span></span>
