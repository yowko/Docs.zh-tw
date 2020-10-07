---
title: .NET 中的高效能記錄
author: IEvangelist
description: 了解如何使用 LoggerMessage 來建立可快取的委派，其對於高效能記錄案例需要較少的物件配置。
ms.author: dapine
ms.date: 09/25/2020
ms.openlocfilehash: 9111b9553c913cff2937b574250b65e633250f4f
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2020
ms.locfileid: "91804758"
---
# <a name="high-performance-logging-in-net"></a><span data-ttu-id="a9873-103">.NET 中的高效能記錄</span><span class="sxs-lookup"><span data-stu-id="a9873-103">High-performance logging in .NET</span></span>

<span data-ttu-id="a9873-104"><xref:Microsoft.Extensions.Logging.LoggerMessage>類別會公開功能來建立可快取的委派，相較于[記錄器擴充方法](xref:Microsoft.Extensions.Logging.LoggerExtensions)（例如和），其需要的物件配置較少且計算額外負荷較低 <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogInformation%2A> <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogDebug%2A> 。</span><span class="sxs-lookup"><span data-stu-id="a9873-104">The <xref:Microsoft.Extensions.Logging.LoggerMessage> class exposes functionality to create cacheable delegates that require fewer object allocations and reduced computational overhead compared to [logger extension methods](xref:Microsoft.Extensions.Logging.LoggerExtensions), such as <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogInformation%2A> and <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogDebug%2A>.</span></span> <span data-ttu-id="a9873-105">對於高效能記錄的案例，請使用 <xref:Microsoft.Extensions.Logging.LoggerMessage> 模式。</span><span class="sxs-lookup"><span data-stu-id="a9873-105">For high-performance logging scenarios, use the <xref:Microsoft.Extensions.Logging.LoggerMessage> pattern.</span></span>

<span data-ttu-id="a9873-106">相較於記錄器擴充方法，<xref:Microsoft.Extensions.Logging.LoggerMessage> 提供下列效能優勢：</span><span class="sxs-lookup"><span data-stu-id="a9873-106"><xref:Microsoft.Extensions.Logging.LoggerMessage> provides the following performance advantages over Logger extension methods:</span></span>

- <span data-ttu-id="a9873-107">記錄器擴充方法需要 "boxing" (轉換) 實值型別，例如將 `int` 轉換為 `object`。</span><span class="sxs-lookup"><span data-stu-id="a9873-107">Logger extension methods require "boxing" (converting) value types, such as `int`, into `object`.</span></span> <span data-ttu-id="a9873-108"><xref:Microsoft.Extensions.Logging.LoggerMessage> 模式可使用靜態 <xref:System.Action> 欄位和擴充方法搭配強型別參數來避免 boxing。</span><span class="sxs-lookup"><span data-stu-id="a9873-108">The <xref:Microsoft.Extensions.Logging.LoggerMessage> pattern avoids boxing by using static <xref:System.Action> fields and extension methods with strongly-typed parameters.</span></span>
- <span data-ttu-id="a9873-109">記錄器擴充方法在每次寫入記錄訊息時，都必須剖析訊息範本 (具名格式字串)。</span><span class="sxs-lookup"><span data-stu-id="a9873-109">Logger extension methods must parse the message template (named format string) every time a log message is written.</span></span> <span data-ttu-id="a9873-110"><xref:Microsoft.Extensions.Logging.LoggerMessage> 只需在定義訊息時剖析範本一次。</span><span class="sxs-lookup"><span data-stu-id="a9873-110"><xref:Microsoft.Extensions.Logging.LoggerMessage> only requires parsing a template once when the message is defined.</span></span>

<span data-ttu-id="a9873-111">範例應用程式會示範 <xref:Microsoft.Extensions.Logging.LoggerMessage> 具有優先權佇列處理背景工作服務的功能。</span><span class="sxs-lookup"><span data-stu-id="a9873-111">The sample app demonstrates <xref:Microsoft.Extensions.Logging.LoggerMessage> features with a priority queue processing worker service.</span></span> <span data-ttu-id="a9873-112">應用程式會依優先權連續處理工作專案。</span><span class="sxs-lookup"><span data-stu-id="a9873-112">The app processes work items in priority order.</span></span> <span data-ttu-id="a9873-113">在進行這些作業時，將會使用 <xref:Microsoft.Extensions.Logging.LoggerMessage> 模式來產生記錄訊息。</span><span class="sxs-lookup"><span data-stu-id="a9873-113">As these operations occur, log messages are generated using the <xref:Microsoft.Extensions.Logging.LoggerMessage> pattern.</span></span>

## <a name="define-a-logger-message"></a><span data-ttu-id="a9873-114">定義記錄器訊息</span><span class="sxs-lookup"><span data-stu-id="a9873-114">Define a logger message</span></span>

<span data-ttu-id="a9873-115">使用 [Define (LogLevel、EventId、String) ](xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A) 來建立 <xref:System.Action> 用來記錄訊息的委派。</span><span class="sxs-lookup"><span data-stu-id="a9873-115">Use [Define(LogLevel, EventId, String)](xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A) to create an <xref:System.Action> delegate for logging a message.</span></span> <span data-ttu-id="a9873-116"><xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> 多載允許最多將六個型別參數傳遞至具名格式字串 (範本)。</span><span class="sxs-lookup"><span data-stu-id="a9873-116"><xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> overloads permit passing up to six type parameters to a named format string (template).</span></span>

<span data-ttu-id="a9873-117">提供給 <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> 方法的字串是範本，而不是內插字串。</span><span class="sxs-lookup"><span data-stu-id="a9873-117">The string provided to the <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> method is a template and not an interpolated string.</span></span> <span data-ttu-id="a9873-118">預留位置會依照指定類型的順序填入。</span><span class="sxs-lookup"><span data-stu-id="a9873-118">Placeholders are filled in the order that the types are specified.</span></span> <span data-ttu-id="a9873-119">範本中的預留位置名稱應該是描述性名稱，而且在範本之間應該保持一致。</span><span class="sxs-lookup"><span data-stu-id="a9873-119">Placeholder names in the template should be descriptive and consistent across templates.</span></span> <span data-ttu-id="a9873-120">它們將作為結構化記錄資料內的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="a9873-120">They serve as property names within structured log data.</span></span> <span data-ttu-id="a9873-121">建議您針對預留位置名稱使用 [Pascal 大小寫](../../standard/design-guidelines/capitalization-conventions.md)。</span><span class="sxs-lookup"><span data-stu-id="a9873-121">We recommend [Pascal casing](../../standard/design-guidelines/capitalization-conventions.md) for placeholder names.</span></span> <span data-ttu-id="a9873-122">例如，`{Item}`、`{DateTime}`。</span><span class="sxs-lookup"><span data-stu-id="a9873-122">For example, `{Item}`, `{DateTime}`.</span></span>

<span data-ttu-id="a9873-123">每個記錄訊息都是 [LoggerMessage.Define](xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A) 所建立之靜態欄位中保存的 <xref:System.Action>。</span><span class="sxs-lookup"><span data-stu-id="a9873-123">Each log message is an <xref:System.Action> held in a static field created by [LoggerMessage.Define](xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A).</span></span> <span data-ttu-id="a9873-124">例如，範例應用程式會建立一個欄位來描述處理工作專案的記錄訊息：</span><span class="sxs-lookup"><span data-stu-id="a9873-124">For example, the sample app creates a field to describe a log message for the processing of work items:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkField":::

<span data-ttu-id="a9873-125">針對 <xref:System.Action>，請指定：</span><span class="sxs-lookup"><span data-stu-id="a9873-125">For the <xref:System.Action>, specify:</span></span>

- <span data-ttu-id="a9873-126">記錄層級。</span><span class="sxs-lookup"><span data-stu-id="a9873-126">The log level.</span></span>
- <span data-ttu-id="a9873-127">含有靜態擴充方法名稱的唯一事件識別碼 (<xref:Microsoft.Extensions.Logging.EventId>)。</span><span class="sxs-lookup"><span data-stu-id="a9873-127">A unique event identifier (<xref:Microsoft.Extensions.Logging.EventId>) with the name of the static extension method.</span></span>
- <span data-ttu-id="a9873-128">訊息範本 (具名格式字串)。</span><span class="sxs-lookup"><span data-stu-id="a9873-128">The message template (named format string).</span></span>

<span data-ttu-id="a9873-129">當工作專案被清除佇列來處理背景工作服務應用程式時，會將下列專案設定為：</span><span class="sxs-lookup"><span data-stu-id="a9873-129">As work items are dequeued for processing the worker service app sets the:</span></span>

- <span data-ttu-id="a9873-130">將記錄層級設定為 `Critical`。</span><span class="sxs-lookup"><span data-stu-id="a9873-130">Log level to `Critical`.</span></span>
- <span data-ttu-id="a9873-131">將事件識別碼設定為含有 `FailedToProcessWorkItem` 方法名稱的 `13`。</span><span class="sxs-lookup"><span data-stu-id="a9873-131">Event id to `13` with the name of the `FailedToProcessWorkItem` method.</span></span>
- <span data-ttu-id="a9873-132">將訊息範本 (具名格式字串) 設定為字串。</span><span class="sxs-lookup"><span data-stu-id="a9873-132">Message template (named format string) to a string.</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkAssignment":::

<span data-ttu-id="a9873-133">結構化的記錄存放區提供事件識別碼來加強記錄時，可以使用事件名稱。</span><span class="sxs-lookup"><span data-stu-id="a9873-133">Structured logging stores may use the event name when it's supplied with the event id to enrich logging.</span></span> <span data-ttu-id="a9873-134">例如，[Serilog](https://github.com/serilog/serilog-extensions-logging) 會使用事件名稱。</span><span class="sxs-lookup"><span data-stu-id="a9873-134">For example, [Serilog](https://github.com/serilog/serilog-extensions-logging) uses the event name.</span></span>

<span data-ttu-id="a9873-135"><xref:System.Action> 是透過強型別擴充方法叫用。</span><span class="sxs-lookup"><span data-stu-id="a9873-135">The <xref:System.Action> is invoked through a strongly-typed extension method.</span></span> <span data-ttu-id="a9873-136">`FailedToProcessWorkItem`方法會在每次處理工作專案時記錄訊息：</span><span class="sxs-lookup"><span data-stu-id="a9873-136">The `FailedToProcessWorkItem` method logs a message every time a work item is being processed:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkMethod":::

<span data-ttu-id="a9873-137">`FailedToProcessWorkItem``ExecuteAsync`當發生錯誤時，會在*Worker.cs*中方法的記錄器上呼叫：</span><span class="sxs-lookup"><span data-stu-id="a9873-137">`FailedToProcessWorkItem` is called on the logger in the `ExecuteAsync` method in *Worker.cs* when an error occurs:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Worker.cs" range="18-39" highlight="15-18":::

<span data-ttu-id="a9873-138">檢查應用程式的主控台輸出：</span><span class="sxs-lookup"><span data-stu-id="a9873-138">Inspect the app's console output:</span></span>

```console
crit: WorkerServiceOptions.Example.Worker[13]
      Epic failure processing item!
      System.Exception: Failed to verify communications.
         at WorkerServiceOptions.Example.Worker.ExecuteAsync(CancellationToken stoppingToken) in
         ..\Worker.cs:line 27
```

<span data-ttu-id="a9873-139">若要將參數傳遞至記錄訊息，請在建立靜態欄位時定義最多六個型別。</span><span class="sxs-lookup"><span data-stu-id="a9873-139">To pass parameters to a log message, define up to six types when creating the static field.</span></span> <span data-ttu-id="a9873-140">範例應用程式會在處理專案時，藉由定義欄位的類型來記錄工作專案的詳細資料 `WorkItem` <xref:System.Action> ：</span><span class="sxs-lookup"><span data-stu-id="a9873-140">The sample app logs the work item details when processing items by defining a `WorkItem` type for the <xref:System.Action> field:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingItemField":::

<span data-ttu-id="a9873-141">委派的記錄訊息範本會從所提供的類型接收其預留位置值。</span><span class="sxs-lookup"><span data-stu-id="a9873-141">The delegate's log message template receives its placeholder values from the types provided.</span></span> <span data-ttu-id="a9873-142">範例應用程式會定義新增引述的委派，其中的引述參數是 `WorkItem`：</span><span class="sxs-lookup"><span data-stu-id="a9873-142">The sample app defines a delegate for adding a quote where the quote parameter is a `WorkItem`:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingItemAssignment":::

<span data-ttu-id="a9873-143">用於記錄正在處理工作專案的靜態擴充方法，會 `PriorityItemProcessed` 接收工作專案引數值，並將它傳遞給 <xref:System.Action> 委派：</span><span class="sxs-lookup"><span data-stu-id="a9873-143">The static extension method for logging that a work item is being processed, `PriorityItemProcessed`, receives the work item argument value and passes it to the <xref:System.Action> delegate:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingItemMethod":::

<span data-ttu-id="a9873-144">在背景工作服務的 `ExecuteAsync` 方法中， `PriorityItemProcessed` 會呼叫來記錄訊息：</span><span class="sxs-lookup"><span data-stu-id="a9873-144">In the worker service's `ExecuteAsync` method, `PriorityItemProcessed` is called to log the message:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Worker.cs" range="18-39" highlight="12":::

<span data-ttu-id="a9873-145">檢查應用程式的主控台輸出：</span><span class="sxs-lookup"><span data-stu-id="a9873-145">Inspect the app's console output:</span></span>

```console
info: WorkerServiceOptions.Example.Worker[1]
      Processing priority item: Priority-Extreme (50db062a-9732-4418-936d-110549ad79e4): 'Verify communications'
```

## <a name="define-logger-message-scope"></a><span data-ttu-id="a9873-146">定義記錄器訊息範圍</span><span class="sxs-lookup"><span data-stu-id="a9873-146">Define logger message scope</span></span>

<span data-ttu-id="a9873-147">[DefineScope (string) ](xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A)方法會建立用 <xref:System.Func%601> 來定義[記錄範圍](logging.md#log-scopes)的委派。</span><span class="sxs-lookup"><span data-stu-id="a9873-147">The [DefineScope(string)](xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A) method creates a <xref:System.Func%601> delegate for defining a [log scope](logging.md#log-scopes).</span></span> <span data-ttu-id="a9873-148"><xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> 多載允許最多將三個型別參數傳遞至具名格式字串 (範本)。</span><span class="sxs-lookup"><span data-stu-id="a9873-148"><xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> overloads permit passing up to three type parameters to a named format string (template).</span></span>

<span data-ttu-id="a9873-149">就像 <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> 方法的情況一樣，提供給 <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> 方法的字串是範本，而不是內插字串。</span><span class="sxs-lookup"><span data-stu-id="a9873-149">As is the case with the <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> method, the string provided to the <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> method is a template and not an interpolated string.</span></span> <span data-ttu-id="a9873-150">預留位置會依照指定類型的順序填入。</span><span class="sxs-lookup"><span data-stu-id="a9873-150">Placeholders are filled in the order that the types are specified.</span></span> <span data-ttu-id="a9873-151">範本中的預留位置名稱應該是描述性名稱，而且在範本之間應該保持一致。</span><span class="sxs-lookup"><span data-stu-id="a9873-151">Placeholder names in the template should be descriptive and consistent across templates.</span></span> <span data-ttu-id="a9873-152">它們將作為結構化記錄資料內的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="a9873-152">They serve as property names within structured log data.</span></span> <span data-ttu-id="a9873-153">建議您針對預留位置名稱使用 [Pascal 大小寫](../../standard/design-guidelines/capitalization-conventions.md)。</span><span class="sxs-lookup"><span data-stu-id="a9873-153">We recommend [Pascal casing](../../standard/design-guidelines/capitalization-conventions.md) for placeholder names.</span></span> <span data-ttu-id="a9873-154">例如，`{Item}`、`{DateTime}`。</span><span class="sxs-lookup"><span data-stu-id="a9873-154">For example, `{Item}`, `{DateTime}`.</span></span>

<span data-ttu-id="a9873-155">使用 <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> 方法，定義要套用至一系列記錄訊息的[記錄範圍](logging.md#log-scopes)。</span><span class="sxs-lookup"><span data-stu-id="a9873-155">Define a [log scope](logging.md#log-scopes) to apply to a series of log messages using the <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> method.</span></span>

<span data-ttu-id="a9873-156">範例應用程式具有 [全部清除]\*\*\*\* 按鈕，可用來刪除資料庫中的所有引述。</span><span class="sxs-lookup"><span data-stu-id="a9873-156">The sample app has a **Clear All** button for deleting all of the quotes in the database.</span></span> <span data-ttu-id="a9873-157">也可透過逐一移除引述來刪除它們。</span><span class="sxs-lookup"><span data-stu-id="a9873-157">The quotes are deleted by removing them one at a time.</span></span> <span data-ttu-id="a9873-158">每次刪除引述時，就會在記錄器上呼叫 `QuoteDeleted` 方法。</span><span class="sxs-lookup"><span data-stu-id="a9873-158">Each time a quote is deleted, the `QuoteDeleted` method is called on the logger.</span></span> <span data-ttu-id="a9873-159">記錄範圍會新增至這些記錄訊息。</span><span class="sxs-lookup"><span data-stu-id="a9873-159">A log scope is added to these log messages.</span></span>

<span data-ttu-id="a9873-160">在 *appsettings.json* 的主控台記錄器區段中啟用 `IncludeScopes`：</span><span class="sxs-lookup"><span data-stu-id="a9873-160">Enable `IncludeScopes` in the console logger section of *appsettings.json*:</span></span>

:::code language="json" source="snippets/configuration/worker-service-options/appsettings.json" highlight="3-5":::

<span data-ttu-id="a9873-161">若要建立記錄範圍，請新增欄位以保留該範圍的 <xref:System.Func%601> 委派。</span><span class="sxs-lookup"><span data-stu-id="a9873-161">To create a log scope, add a field to hold a <xref:System.Func%601> delegate for the scope.</span></span> <span data-ttu-id="a9873-162">範例應用程式會建立稱為 `_allQuotesDeletedScope` (*Internal/LoggerExtensions.cs*) 的欄位：</span><span class="sxs-lookup"><span data-stu-id="a9873-162">The sample app creates a field called `_allQuotesDeletedScope` (*Internal/LoggerExtensions.cs*):</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkField":::

<span data-ttu-id="a9873-163">請使用 <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> 來建立委派。</span><span class="sxs-lookup"><span data-stu-id="a9873-163">Use <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> to create the delegate.</span></span> <span data-ttu-id="a9873-164">叫用委派時，最多可以指定三種類型作為範本引數。</span><span class="sxs-lookup"><span data-stu-id="a9873-164">Up to three types can be specified for use as template arguments when the delegate is invoked.</span></span> <span data-ttu-id="a9873-165">範例應用程式會使用包含已刪除引述數目 (`int` 類型) 的訊息範本：</span><span class="sxs-lookup"><span data-stu-id="a9873-165">The sample app uses a message template that includes the number of deleted quotes (an `int` type):</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkAssignment":::

<span data-ttu-id="a9873-166">提供記錄訊息的靜態擴充方法。</span><span class="sxs-lookup"><span data-stu-id="a9873-166">Provide a static extension method for the log message.</span></span> <span data-ttu-id="a9873-167">包含訊息範本中出現之具名屬性的任何型別參數。</span><span class="sxs-lookup"><span data-stu-id="a9873-167">Include any type parameters for named properties that appear in the message template.</span></span> <span data-ttu-id="a9873-168">範例應用程式會使用，以取得 `DateTime` 自訂時間戳記來記錄並傳回 `_processingWorkScope` ：</span><span class="sxs-lookup"><span data-stu-id="a9873-168">The sample app takes in a `DateTime` for a custom time stamp to log and returns `_processingWorkScope`:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkMethod":::

<span data-ttu-id="a9873-169">此範圍會將記錄擴充呼叫包裝在 [using](../../csharp/language-reference/keywords/using-statement.md) 區塊中：</span><span class="sxs-lookup"><span data-stu-id="a9873-169">The scope wraps the logging extension calls in a [using](../../csharp/language-reference/keywords/using-statement.md) block:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Worker.cs" range="18-39" highlight="4":::

<span data-ttu-id="a9873-170">檢查應用程式主控台輸出中的記錄訊息。</span><span class="sxs-lookup"><span data-stu-id="a9873-170">Inspect the log messages in the app's console output.</span></span> <span data-ttu-id="a9873-171">下列結果顯示包含記錄範圍訊息的三個刪除引述：</span><span class="sxs-lookup"><span data-stu-id="a9873-171">The following result shows three quotes deleted with the log scope message included:</span></span>

```console
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Extreme (f5090ede-a337-4041-b914-f6bc0db5ae64): 'Verify communications'
info: Microsoft.Hosting.Lifetime[0]
      Application started. Press Ctrl+C to shut down.
info: Microsoft.Hosting.Lifetime[0]
      Hosting environment: Development
info: Microsoft.Hosting.Lifetime[0]
      Content root path: ..\worker-service-options
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-High (496d440f-2007-4391-b179-09d75ab52373): 'Validate collection'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Medium (dea9e3f4-d7df-46d2-b7cd-5e0232eb98a5): 'Propagate selections'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Medium (089d7f0d-da72-4b55-92fe-57b147838056): 'Enter pooling [contention]'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Low (6e68c4be-089f-4450-9080-1ea63fcbb686): 'Health check network'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Deferred (6f324134-6bb6-455f-81d4-553ab307c421): 'Ping weather service'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Deferred (37bf736c-7a26-4a2a-9e56-e89bcf3b8f35): 'Set process state'
```

## <a name="see-also"></a><span data-ttu-id="a9873-172">請參閱</span><span class="sxs-lookup"><span data-stu-id="a9873-172">See also</span></span>

- [<span data-ttu-id="a9873-173">.NET 中的記錄</span><span class="sxs-lookup"><span data-stu-id="a9873-173">Logging in .NET</span></span>](logging.md)
