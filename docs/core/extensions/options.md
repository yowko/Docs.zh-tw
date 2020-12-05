---
title: .NET 中的選項模式
author: IEvangelist
description: 瞭解如何使用選項模式來代表 .NET 應用程式中的相關設定群組。
ms.author: dapine
ms.date: 12/04/2020
ms.openlocfilehash: 76d99337c51920115a38c400daca1649d0e74a99
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740015"
---
# <a name="options-pattern-in-net"></a><span data-ttu-id="60ec5-103">.NET 中的選項模式</span><span class="sxs-lookup"><span data-stu-id="60ec5-103">Options pattern in .NET</span></span>

<span data-ttu-id="60ec5-104">選項模式使用類別來提供相關設定群組的強型別存取。</span><span class="sxs-lookup"><span data-stu-id="60ec5-104">The options pattern uses classes to provide strongly-typed access to groups of related settings.</span></span> <span data-ttu-id="60ec5-105">當[組態設定](configuration.md)依案例隔離到不同的類別時，應用程式會遵守兩個重要的軟體工程準則：</span><span class="sxs-lookup"><span data-stu-id="60ec5-105">When [configuration settings](configuration.md) are isolated by scenario into separate classes, the app adheres to two important software engineering principles:</span></span>

- <span data-ttu-id="60ec5-106">[介面隔離原則 (ISP) 或封裝](../../architecture/modern-web-apps-azure/architectural-principles.md#encapsulation)：相依于設定的案例 (類別) 取決於所使用的設定。</span><span class="sxs-lookup"><span data-stu-id="60ec5-106">The [Interface Segregation Principle (ISP) or Encapsulation](../../architecture/modern-web-apps-azure/architectural-principles.md#encapsulation): Scenarios (classes) that depend on configuration settings depend only on the configuration settings that they use.</span></span>
- <span data-ttu-id="60ec5-107">[關注點分離](../../architecture/modern-web-apps-azure/architectural-principles.md#separation-of-concerns) (不同考量)：應用程式不同部分的設定不會彼此相依或結合。</span><span class="sxs-lookup"><span data-stu-id="60ec5-107">[Separation of Concerns](../../architecture/modern-web-apps-azure/architectural-principles.md#separation-of-concerns): Settings for different parts of the app aren't dependent or coupled to one another.</span></span>

<span data-ttu-id="60ec5-108">選項也提供驗證設定資料的機制。</span><span class="sxs-lookup"><span data-stu-id="60ec5-108">Options also provide a mechanism to validate configuration data.</span></span> <span data-ttu-id="60ec5-109">如需詳細資訊，請參閱[選項驗證](#options-validation)一節。</span><span class="sxs-lookup"><span data-stu-id="60ec5-109">For more information, see the [Options validation](#options-validation) section.</span></span>

## <a name="bind-hierarchical-configuration"></a><span data-ttu-id="60ec5-110">系結階層式設定</span><span class="sxs-lookup"><span data-stu-id="60ec5-110">Bind hierarchical configuration</span></span>

<span data-ttu-id="60ec5-111">讀取相關設定值的慣用方式是使用選項模式。</span><span class="sxs-lookup"><span data-stu-id="60ec5-111">The preferred way to read related configuration values is using the options pattern.</span></span> <span data-ttu-id="60ec5-112">例如，若要讀取下列設定值：</span><span class="sxs-lookup"><span data-stu-id="60ec5-112">For example, to read the following configuration values:</span></span>

:::code language="json" source="snippets/configuration/console-json/appsettings.json" range="3-6":::

<span data-ttu-id="60ec5-113">建立下列 `TransientFaultHandlingOptions` 類別：</span><span class="sxs-lookup"><span data-stu-id="60ec5-113">Create the following `TransientFaultHandlingOptions` class:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/TransientFaultHandlingOptions.cs" range="5-6":::

<span data-ttu-id="60ec5-114">Options 類別：</span><span class="sxs-lookup"><span data-stu-id="60ec5-114">An options class:</span></span>

* <span data-ttu-id="60ec5-115">必須是具有公用無參數函數的非抽象</span><span class="sxs-lookup"><span data-stu-id="60ec5-115">Must be non-abstract with a public parameterless constructor</span></span>
* <span data-ttu-id="60ec5-116">包含用來系結的公用讀寫屬性 (欄位為 \***not** _ 系結) </span><span class="sxs-lookup"><span data-stu-id="60ec5-116">Contain public read-write properties to bind (fields are \***not** _ bound)</span></span>

<span data-ttu-id="60ec5-117">下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="60ec5-117">The following code:</span></span>

<span data-ttu-id="60ec5-118">_ 呼叫 [ConfigurationBinder](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Bind%2A) ，將類別系結至 `TransientFaultHandlingOptions` `"TransientFaultHandlingOptions"` 區段。</span><span class="sxs-lookup"><span data-stu-id="60ec5-118">_ Calls [ConfigurationBinder.Bind](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Bind%2A) to bind the `TransientFaultHandlingOptions` class to the `"TransientFaultHandlingOptions"` section.</span></span>
* <span data-ttu-id="60ec5-119">顯示設定資料。</span><span class="sxs-lookup"><span data-stu-id="60ec5-119">Displays the configuration data.</span></span>

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="31-38":::

<span data-ttu-id="60ec5-120">在上述程式碼中，會讀取應用程式啟動後的 JSON 設定檔變更。</span><span class="sxs-lookup"><span data-stu-id="60ec5-120">In the preceding code, changes to the JSON configuration file after the app has started are read.</span></span>

<span data-ttu-id="60ec5-121">[`ConfigurationBinder.Get<T>`](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Get%2A) 系結並傳回指定的型別。</span><span class="sxs-lookup"><span data-stu-id="60ec5-121">[`ConfigurationBinder.Get<T>`](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Get%2A) binds and returns the specified type.</span></span> <span data-ttu-id="60ec5-122">`ConfigurationBinder.Get<T>` 可能比使用更方便 `ConfigurationBinder.Bind` 。</span><span class="sxs-lookup"><span data-stu-id="60ec5-122">`ConfigurationBinder.Get<T>` may be more convenient than using `ConfigurationBinder.Bind`.</span></span> <span data-ttu-id="60ec5-123">下列程式碼顯示如何搭配 `ConfigurationBinder.Get<T>` `TransientFaultHandlingOptions` 類別使用：</span><span class="sxs-lookup"><span data-stu-id="60ec5-123">The following code shows how to use `ConfigurationBinder.Get<T>` with the `TransientFaultHandlingOptions` class:</span></span>

```csharp
IConfigurationRoot configurationRoot = configuration.Build();

var options =
    configurationRoot.GetSection(nameof(TransientFaultHandlingOptions))
        .Get<TransientFaultHandlingOptions>();

Console.WriteLine($"TransientFaultHandlingOptions.Enabled={options.Enabled}");
Console.WriteLine($"TransientFaultHandlingOptions.AutoRetryDelay={options.AutoRetryDelay}");
```

<span data-ttu-id="60ec5-124">在上述程式碼中，會讀取應用程式啟動後的 JSON 設定檔變更。</span><span class="sxs-lookup"><span data-stu-id="60ec5-124">In the preceding code, changes to the JSON configuration file after the app has started are read.</span></span>

<span data-ttu-id="60ec5-125">使用選項模式時的替代方法是系結 `"TransientFaultHandlingOptions"` 區段，並將它加入至相依性 [插入服務容器](dependency-injection.md)。</span><span class="sxs-lookup"><span data-stu-id="60ec5-125">An alternative approach when using the options pattern is to bind the `"TransientFaultHandlingOptions"` section and add it to the [dependency injection service container](dependency-injection.md).</span></span> <span data-ttu-id="60ec5-126">在下列程式碼中， `TransientFaultHandlingOptions` 會新增至服務容器， <xref:Microsoft.Extensions.DependencyInjection.OptionsConfigurationServiceCollectionExtensions.Configure%2A> 並系結至設定：</span><span class="sxs-lookup"><span data-stu-id="60ec5-126">In the following code, `TransientFaultHandlingOptions` is added to the service container with <xref:Microsoft.Extensions.DependencyInjection.OptionsConfigurationServiceCollectionExtensions.Configure%2A> and bound to configuration:</span></span>

```csharp
services.Configure<TransientFaultHandlingOptions>(
    configurationRoot.GetSection(
        key: nameof(TransientFaultHandlingOptions)));
```

> [!TIP]
> <span data-ttu-id="60ec5-127">`key`參數是要搜尋之設定區段的名稱。</span><span class="sxs-lookup"><span data-stu-id="60ec5-127">The `key` parameter is the name of the configuration section to search for.</span></span> <span data-ttu-id="60ec5-128">它 *不* 需要與代表它的型別名稱相符。</span><span class="sxs-lookup"><span data-stu-id="60ec5-128">It does *not* have to match the name of the type that represents it.</span></span> <span data-ttu-id="60ec5-129">例如，您可能會有一個名為的區段 `"FaultHandling"` ，而且可以由 `TransientFaultHandlingOptions` 類別表示。</span><span class="sxs-lookup"><span data-stu-id="60ec5-129">For example, you could have a section named `"FaultHandling"` and it could be represented by the `TransientFaultHandlingOptions` class.</span></span> <span data-ttu-id="60ec5-130">在此情況下，您會 `"FaultHandling"` 改為傳遞給 <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> 函數。</span><span class="sxs-lookup"><span data-stu-id="60ec5-130">In this instance, you'd pass `"FaultHandling"` to the <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> function instead.</span></span> <span data-ttu-id="60ec5-131">`nameof`當已命名的區段符合其對應的型別時，就會使用運算子作為便利性。</span><span class="sxs-lookup"><span data-stu-id="60ec5-131">The `nameof` operator is used as a convenience when the named section matches the type it corresponds to.</span></span>

<span data-ttu-id="60ec5-132">使用上述程式碼，下列程式碼會讀取位置選項：</span><span class="sxs-lookup"><span data-stu-id="60ec5-132">Using the preceding code, the following code reads the position options:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/ExampleService.cs":::

<span data-ttu-id="60ec5-133">在上述程式碼中，應用程式啟動後的 JSON 設定檔變更為 \***not** _ read。</span><span class="sxs-lookup"><span data-stu-id="60ec5-133">In the preceding code, changes to the JSON configuration file after the app has started are \***not** _ read.</span></span> <span data-ttu-id="60ec5-134">若要讀取應用程式啟動後的變更，請使用 [IOptionsSnapshot](#use-ioptionssnapshot-to-read-updated-data)。</span><span class="sxs-lookup"><span data-stu-id="60ec5-134">To read changes after the app has started, use [IOptionsSnapshot](#use-ioptionssnapshot-to-read-updated-data).</span></span>

## <a name="options-interfaces"></a><span data-ttu-id="60ec5-135">選項介面</span><span class="sxs-lookup"><span data-stu-id="60ec5-135">Options interfaces</span></span>

<span data-ttu-id="60ec5-136"><xref:Microsoft.Extensions.Options.IOptions%601>:</span><span class="sxs-lookup"><span data-stu-id="60ec5-136"><xref:Microsoft.Extensions.Options.IOptions%601>:</span></span>

- <span data-ttu-id="60ec5-137">不 _\*_支援：_\*_</span><span class="sxs-lookup"><span data-stu-id="60ec5-137">Does _*_not_*_ support:</span></span>
  - <span data-ttu-id="60ec5-138">在應用程式啟動後讀取設定資料。</span><span class="sxs-lookup"><span data-stu-id="60ec5-138">Reading of configuration data after the app has started.</span></span>
  - [<span data-ttu-id="60ec5-139">具名選項</span><span class="sxs-lookup"><span data-stu-id="60ec5-139">Named options</span></span>](#named-options-support-using-iconfigurenamedoptions)
- <span data-ttu-id="60ec5-140">註冊為 [Singleton](dependency-injection.md#singleton) ，並且可以插入至任何 [服務存留期](dependency-injection.md#service-lifetimes)。</span><span class="sxs-lookup"><span data-stu-id="60ec5-140">Is registered as a [Singleton](dependency-injection.md#singleton) and can be injected into any [service lifetime](dependency-injection.md#service-lifetimes).</span></span>

<span data-ttu-id="60ec5-141"><xref:Microsoft.Extensions.Options.IOptionsSnapshot%601>:</span><span class="sxs-lookup"><span data-stu-id="60ec5-141"><xref:Microsoft.Extensions.Options.IOptionsSnapshot%601>:</span></span>

- <span data-ttu-id="60ec5-142">適用于應在 [範圍或暫時性存留期](dependency-injection.md#service-lifetimes)內，于每次插入解析時重新計算選項的情況。</span><span class="sxs-lookup"><span data-stu-id="60ec5-142">Is useful in scenarios where options should be recomputed on every injection resolution, in [scoped or transient lifetimes](dependency-injection.md#service-lifetimes).</span></span> <span data-ttu-id="60ec5-143">如需詳細資訊，請參閱 [使用 IOptionsSnapshot 讀取更新的資料](#use-ioptionssnapshot-to-read-updated-data)。</span><span class="sxs-lookup"><span data-stu-id="60ec5-143">For more information, see [Use IOptionsSnapshot to read updated data](#use-ioptionssnapshot-to-read-updated-data).</span></span>
- <span data-ttu-id="60ec5-144">註冊為 [範圍](dependency-injection.md#scoped) ，因此無法插入至單一服務。</span><span class="sxs-lookup"><span data-stu-id="60ec5-144">Is registered as [Scoped](dependency-injection.md#scoped) and therefore cannot be injected into a Singleton service.</span></span>
- <span data-ttu-id="60ec5-145">支援 [已命名的選項](#named-options-support-using-iconfigurenamedoptions)</span><span class="sxs-lookup"><span data-stu-id="60ec5-145">Supports [named options](#named-options-support-using-iconfigurenamedoptions)</span></span>

<span data-ttu-id="60ec5-146"><xref:Microsoft.Extensions.Options.IOptionsMonitor%601>:</span><span class="sxs-lookup"><span data-stu-id="60ec5-146"><xref:Microsoft.Extensions.Options.IOptionsMonitor%601>:</span></span>

- <span data-ttu-id="60ec5-147">用來取得實例的選項和管理選項通知 `TOptions` 。</span><span class="sxs-lookup"><span data-stu-id="60ec5-147">Is used to retrieve options and manage options notifications for `TOptions` instances.</span></span>
- <span data-ttu-id="60ec5-148">註冊為 [Singleton](dependency-injection.md#singleton) ，並且可以插入至任何 [服務存留期](dependency-injection.md#service-lifetimes)。</span><span class="sxs-lookup"><span data-stu-id="60ec5-148">Is registered as a [Singleton](dependency-injection.md#singleton) and can be injected into any [service lifetime](dependency-injection.md#service-lifetimes).</span></span>
- <span data-ttu-id="60ec5-149">支援：</span><span class="sxs-lookup"><span data-stu-id="60ec5-149">Supports:</span></span>
  - <span data-ttu-id="60ec5-150">變更通知</span><span class="sxs-lookup"><span data-stu-id="60ec5-150">Change notifications</span></span>
  - [<span data-ttu-id="60ec5-151">具名選項</span><span class="sxs-lookup"><span data-stu-id="60ec5-151">Named options</span></span>](#named-options-support-using-iconfigurenamedoptions)
  - [<span data-ttu-id="60ec5-152">可重新載入的設定</span><span class="sxs-lookup"><span data-stu-id="60ec5-152">Reloadable configuration</span></span>](#use-ioptionssnapshot-to-read-updated-data)
  - <span data-ttu-id="60ec5-153">選擇性選項無效判定 (<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601>)</span><span class="sxs-lookup"><span data-stu-id="60ec5-153">Selective options invalidation (<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601>)</span></span>
  
<span data-ttu-id="60ec5-154"><xref:Microsoft.Extensions.Options.IOptionsFactory%601> 負責建立新的選項執行個體。</span><span class="sxs-lookup"><span data-stu-id="60ec5-154"><xref:Microsoft.Extensions.Options.IOptionsFactory%601> is responsible for creating new options instances.</span></span> <span data-ttu-id="60ec5-155">它有單一 <xref:Microsoft.Extensions.Options.IOptionsFactory%601.Create%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="60ec5-155">It has a single <xref:Microsoft.Extensions.Options.IOptionsFactory%601.Create%2A> method.</span></span> <span data-ttu-id="60ec5-156">預設實作會接受所有已註冊的 <xref:Microsoft.Extensions.Options.IConfigureOptions%601> 與 <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601>，並先執行所有設定，接著執行設定後作業。</span><span class="sxs-lookup"><span data-stu-id="60ec5-156">The default implementation takes all registered <xref:Microsoft.Extensions.Options.IConfigureOptions%601> and <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601> and runs all the configurations first, followed by the post-configuration.</span></span> <span data-ttu-id="60ec5-157">它會區別 <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> 和 <xref:Microsoft.Extensions.Options.IConfigureOptions%601>，且只會呼叫適當的介面。</span><span class="sxs-lookup"><span data-stu-id="60ec5-157">It distinguishes between <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> and <xref:Microsoft.Extensions.Options.IConfigureOptions%601> and only calls the appropriate interface.</span></span>

<span data-ttu-id="60ec5-158"><xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> 會由 <xref:Microsoft.Extensions.Options.IOptionsMonitor%601> 用來快取 `TOptions` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="60ec5-158"><xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> is used by <xref:Microsoft.Extensions.Options.IOptionsMonitor%601> to cache `TOptions` instances.</span></span> <span data-ttu-id="60ec5-159"><xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> 會使監視器中的選項執行個體失效，以便重新計算值 (<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryRemove%2A>)。</span><span class="sxs-lookup"><span data-stu-id="60ec5-159">The <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> invalidates options instances in the monitor so that the value is recomputed (<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryRemove%2A>).</span></span> <span data-ttu-id="60ec5-160">值可以使用 <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryAdd%2A> 手動導入。</span><span class="sxs-lookup"><span data-stu-id="60ec5-160">Values can be manually introduced with <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryAdd%2A>.</span></span> <span data-ttu-id="60ec5-161"><xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.Clear%2A> 方法用於應該視需要重新建立所有具名執行個體時。</span><span class="sxs-lookup"><span data-stu-id="60ec5-161">The <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.Clear%2A> method is used when all named instances should be recreated on demand.</span></span>

## <a name="use-ioptionssnapshot-to-read-updated-data"></a><span data-ttu-id="60ec5-162">使用 IOptionsSnapshot 讀取更新的資料</span><span class="sxs-lookup"><span data-stu-id="60ec5-162">Use IOptionsSnapshot to read updated data</span></span>

<span data-ttu-id="60ec5-163">當您使用時 <xref:Microsoft.Extensions.Options.IOptionsSnapshot%601> ，每個要求的選項會在存取時計算一次，而且會在要求的存留期內快取。</span><span class="sxs-lookup"><span data-stu-id="60ec5-163">when you use <xref:Microsoft.Extensions.Options.IOptionsSnapshot%601>, options are computed once per request when accessed and are cached for the lifetime of the request.</span></span> <span data-ttu-id="60ec5-164">使用支援讀取已更新設定值的設定提供者時，會在應用程式啟動後讀取設定的變更。</span><span class="sxs-lookup"><span data-stu-id="60ec5-164">Changes to the configuration are read after the app starts when using configuration providers that support reading updated configuration values.</span></span>

<span data-ttu-id="60ec5-165">和之間的差異在於 `IOptionsMonitor` `IOptionsSnapshot` ：</span><span class="sxs-lookup"><span data-stu-id="60ec5-165">The difference between `IOptionsMonitor` and `IOptionsSnapshot` is that:</span></span>

- <span data-ttu-id="60ec5-166">`IOptionsMonitor` 是 [單一服務](dependency-injection.md#singleton) ，可隨時抓取目前的選項值，這在單一相依性中特別有用。</span><span class="sxs-lookup"><span data-stu-id="60ec5-166">`IOptionsMonitor` is a [singleton service](dependency-injection.md#singleton) that retrieves current option values at any time, which is especially useful in singleton dependencies.</span></span>
- <span data-ttu-id="60ec5-167">`IOptionsSnapshot` 是限 [域的服務](dependency-injection.md#scoped) ，會在建立物件時提供選項的快照 `IOptionsSnapshot<T>` 。</span><span class="sxs-lookup"><span data-stu-id="60ec5-167">`IOptionsSnapshot` is a [scoped service](dependency-injection.md#scoped) and provides a snapshot of the options at the time the `IOptionsSnapshot<T>` object is constructed.</span></span> <span data-ttu-id="60ec5-168">選項快照集的設計目的是要搭配使用暫時性和限定範圍的相依性。</span><span class="sxs-lookup"><span data-stu-id="60ec5-168">Options snapshots are designed for use with transient and scoped dependencies.</span></span>

<span data-ttu-id="60ec5-169">下列程式碼使用 <xref:Microsoft.Extensions.Options.IOptionsSnapshot%601> 。</span><span class="sxs-lookup"><span data-stu-id="60ec5-169">The following code uses <xref:Microsoft.Extensions.Options.IOptionsSnapshot%601>.</span></span>

:::code language="csharp" source="snippets/configuration/console-json/ScopedService.cs":::

<span data-ttu-id="60ec5-170">下列程式碼會註冊系結的設定實例 `TransientFaultHandlingOptions` ：</span><span class="sxs-lookup"><span data-stu-id="60ec5-170">The following code registers a configuration instance which `TransientFaultHandlingOptions` binds against:</span></span>

```csharp
services.Configure<TransientFaultHandlingOptions>(
    configurationRoot.GetSection(
        nameof(TransientFaultHandlingOptions)));
```

<span data-ttu-id="60ec5-171">在上述程式碼中，會讀取應用程式啟動後的 JSON 設定檔變更。</span><span class="sxs-lookup"><span data-stu-id="60ec5-171">In the preceding code, changes to the JSON configuration file after the app has started are read.</span></span>

## <a name="ioptionsmonitor"></a><span data-ttu-id="60ec5-172">IOptionsMonitor</span><span class="sxs-lookup"><span data-stu-id="60ec5-172">IOptionsMonitor</span></span>

<span data-ttu-id="60ec5-173">下列程式碼會註冊針對系結的設定實例 `TransientFaultHandlingOptions` 。</span><span class="sxs-lookup"><span data-stu-id="60ec5-173">The following code registers a configuration instance which `TransientFaultHandlingOptions` binds against.</span></span>

```csharp
services.Configure<TransientFaultHandlingOptions>(
    configurationRoot.GetSection(
        nameof(TransientFaultHandlingOptions)));
```

<span data-ttu-id="60ec5-174">下列範例會使用 <xref:Microsoft.Extensions.Options.IOptionsMonitor%601>：</span><span class="sxs-lookup"><span data-stu-id="60ec5-174">The following example uses <xref:Microsoft.Extensions.Options.IOptionsMonitor%601>:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/MonitorService.cs":::

<span data-ttu-id="60ec5-175">在上述程式碼中，會讀取應用程式啟動後的 JSON 設定檔變更。</span><span class="sxs-lookup"><span data-stu-id="60ec5-175">In the preceding code, changes to the JSON configuration file after the app has started are read.</span></span>

## <a name="named-options-support-using-iconfigurenamedoptions"></a><span data-ttu-id="60ec5-176">使用 IConfigureNamedOptions 的命名選項支援</span><span class="sxs-lookup"><span data-stu-id="60ec5-176">Named options support using IConfigureNamedOptions</span></span>

<span data-ttu-id="60ec5-177">命名選項：</span><span class="sxs-lookup"><span data-stu-id="60ec5-177">Named options:</span></span>

- <span data-ttu-id="60ec5-178">當多個設定區段系結至相同的屬性時，會很有用。</span><span class="sxs-lookup"><span data-stu-id="60ec5-178">Are useful when multiple configuration sections bind to the same properties.</span></span>
- <span data-ttu-id="60ec5-179">會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="60ec5-179">Are case-sensitive.</span></span>

<span data-ttu-id="60ec5-180">請考慮 \* file 上的下列 _appsettings.js：</span><span class="sxs-lookup"><span data-stu-id="60ec5-180">Consider the following _appsettings.json\* file:</span></span>

```json
{
  "Features": {
    "Personalize": {
      "Enabled": true,
      "ApiKey": "aGEgaGEgeW91IHRob3VnaHQgdGhhdCB3YXMgcmVhbGx5IHNvbWV0aGluZw=="
    },
    "WeatherStation": {
      "Enabled": true,
      "ApiKey": "QXJlIHlvdSBhdHRlbXB0aW5nIHRvIGhhY2sgdXM/"
    }
  }
}
```

<span data-ttu-id="60ec5-181">`Features:Personalize` `Features:WeatherStation` 下列類別可用於每個區段，而不是建立兩個類別來系結和：</span><span class="sxs-lookup"><span data-stu-id="60ec5-181">Rather than creating two classes to bind `Features:Personalize` and `Features:WeatherStation`, the following class is used for each section:</span></span>

```csharp
public class Features
{
    public const string Personalize = nameof(Personalize);
    public const string WeatherStation = nameof(WeatherStation);

    public bool Enabled { get; set; }
    public string ApiKey { get; set; }
}
```

<span data-ttu-id="60ec5-182">下列程式碼會設定命名選項：</span><span class="sxs-lookup"><span data-stu-id="60ec5-182">The following code configures the named options:</span></span>

```csharp
ConfigureServices(services =>
{
    services.Configure<Features>(
        Features.Personalize,
        Configuration.GetSection("Features:Personalize"));

    services.Configure<Features>(
        Features.WeatherStation,
        Configuration.GetSection("Features:WeatherStation"));
});
```

<span data-ttu-id="60ec5-183">下列程式碼會顯示已命名的選項：</span><span class="sxs-lookup"><span data-stu-id="60ec5-183">The following code displays the named options:</span></span>

```csharp
public class Service
{
    private readonly Features _personalizeFeature;
    private readonly Features _weatherStationFeature;

    public Service(IOptionsSnapshot<Features> namedOptionsAccessor)
    {
        _personalizeFeature = namedOptionsAccessor.Get(Features.Personalize);
        _weatherStationFeature = namedOptionsAccessor.Get(Features.WeatherStation);
    }
}
```

<span data-ttu-id="60ec5-184">所有選項都是具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="60ec5-184">All options are named instances.</span></span> <span data-ttu-id="60ec5-185"><xref:Microsoft.Extensions.Options.IConfigureOptions%601> 系統會將實例視為目標 `Options.DefaultName` 實例，也就是 `string.Empty` 。</span><span class="sxs-lookup"><span data-stu-id="60ec5-185"><xref:Microsoft.Extensions.Options.IConfigureOptions%601> instances are treated as targeting the `Options.DefaultName` instance, which is `string.Empty`.</span></span> <span data-ttu-id="60ec5-186"><xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> 也會實作 <xref:Microsoft.Extensions.Options.IConfigureOptions%601>。</span><span class="sxs-lookup"><span data-stu-id="60ec5-186"><xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> also implements <xref:Microsoft.Extensions.Options.IConfigureOptions%601>.</span></span> <span data-ttu-id="60ec5-187"><xref:Microsoft.Extensions.Options.IOptionsFactory%601> 的預設實作有邏輯可以適當地使用每個項目。</span><span class="sxs-lookup"><span data-stu-id="60ec5-187">The default implementation of the <xref:Microsoft.Extensions.Options.IOptionsFactory%601> has logic to use each appropriately.</span></span> <span data-ttu-id="60ec5-188">此 `null` 命名選項用來以所有已命名的實例為目標，而不是特定的已命名實例。</span><span class="sxs-lookup"><span data-stu-id="60ec5-188">The `null` named option is used to target all of the named instances instead of a specific named instance.</span></span> <span data-ttu-id="60ec5-189"><xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.ConfigureAll%2A> 並 <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A> 使用此慣例。</span><span class="sxs-lookup"><span data-stu-id="60ec5-189"><xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.ConfigureAll%2A> and <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A> use this convention.</span></span>

## <a name="optionsbuilder-api"></a><span data-ttu-id="60ec5-190">OptionsBuilder API</span><span class="sxs-lookup"><span data-stu-id="60ec5-190">OptionsBuilder API</span></span>

<span data-ttu-id="60ec5-191"><xref:Microsoft.Extensions.Options.OptionsBuilder%601> 會用於設定 `TOptions` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="60ec5-191"><xref:Microsoft.Extensions.Options.OptionsBuilder%601> is used to configure `TOptions` instances.</span></span> <span data-ttu-id="60ec5-192">因為 `OptionsBuilder` 僅為初始 `AddOptions<TOptions>(string optionsName)` 呼叫的單一參數，而不是出現在所有後續呼叫的參數，所以其可簡化建立具名選項的程序。</span><span class="sxs-lookup"><span data-stu-id="60ec5-192">`OptionsBuilder` streamlines creating named options as it's only a single parameter to the initial `AddOptions<TOptions>(string optionsName)` call instead of appearing in all of the subsequent calls.</span></span> <span data-ttu-id="60ec5-193">選項驗證及接受服務依存性的 `ConfigureOptions` 多載，只可透過 `OptionsBuilder` 使用。</span><span class="sxs-lookup"><span data-stu-id="60ec5-193">Options validation and the `ConfigureOptions` overloads that accept service dependencies are only available via `OptionsBuilder`.</span></span>

<span data-ttu-id="60ec5-194">`OptionsBuilder` 在 [ [選項驗證](#options-validation) ] 區段中使用。</span><span class="sxs-lookup"><span data-stu-id="60ec5-194">`OptionsBuilder` is used in the [Options validation](#options-validation) section.</span></span>

## <a name="use-di-services-to-configure-options"></a><span data-ttu-id="60ec5-195">使用 DI 服務來設定選項</span><span class="sxs-lookup"><span data-stu-id="60ec5-195">Use DI services to configure options</span></span>

<span data-ttu-id="60ec5-196">您可以透過下列兩種方式，從相依性插入來存取服務：</span><span class="sxs-lookup"><span data-stu-id="60ec5-196">Services can be accessed from dependency injection while configuring options in two ways:</span></span>

- <span data-ttu-id="60ec5-197">傳遞設定委派以[設定](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) [OptionsBuilder \<TOptions> ](xref:Microsoft.Extensions.Options.OptionsBuilder%601)。</span><span class="sxs-lookup"><span data-stu-id="60ec5-197">Pass a configuration delegate to [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) on [OptionsBuilder\<TOptions>](xref:Microsoft.Extensions.Options.OptionsBuilder%601).</span></span> <span data-ttu-id="60ec5-198">`OptionsBuilder<TOptions>` 提供 [設定的多載，可](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) 讓您使用最多五個服務來設定選項：</span><span class="sxs-lookup"><span data-stu-id="60ec5-198">`OptionsBuilder<TOptions>` provides overloads of [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) that allow use of up to five services to configure options:</span></span>

  ```csharp
  services.AddOptions<MyOptions>("optionalName")
      .Configure<ExampleService, ScopedService, MonitorService>(
          (options, es, ss, ms) =>
              options.Property = DoSomethingWith(es, ss, ms));
  ```

- <span data-ttu-id="60ec5-199">建立實作為型別 <xref:Microsoft.Extensions.Options.IConfigureOptions%601> <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> 並將其註冊為服務的型別。</span><span class="sxs-lookup"><span data-stu-id="60ec5-199">Create a type that implements <xref:Microsoft.Extensions.Options.IConfigureOptions%601> or <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> and register the type as a service.</span></span>

<span data-ttu-id="60ec5-200">我們建議您將設定委派傳遞到 [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A)，因為建立服務更複雜。</span><span class="sxs-lookup"><span data-stu-id="60ec5-200">We recommend passing a configuration delegate to [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A), since creating a service is more complex.</span></span> <span data-ttu-id="60ec5-201">建立類型相當於呼叫 [設定](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A)時的架構。</span><span class="sxs-lookup"><span data-stu-id="60ec5-201">Creating a type is equivalent to what the framework does when calling [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A).</span></span> <span data-ttu-id="60ec5-202">呼叫 [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) 會註冊暫時性泛型 <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601>，其具有會接受所指定泛型服務類型的建構函式。</span><span class="sxs-lookup"><span data-stu-id="60ec5-202">Calling [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) registers a transient generic <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601>, which has a constructor that accepts the generic service types specified.</span></span>

## <a name="options-validation"></a><span data-ttu-id="60ec5-203">選項驗證</span><span class="sxs-lookup"><span data-stu-id="60ec5-203">Options validation</span></span>

<span data-ttu-id="60ec5-204">選項驗證可讓您驗證選項值。</span><span class="sxs-lookup"><span data-stu-id="60ec5-204">Options validation enables option values to be validated.</span></span>

<span data-ttu-id="60ec5-205">請考慮下列 *appsettings.json* file：</span><span class="sxs-lookup"><span data-stu-id="60ec5-205">Consider the following *appsettings.json* file:</span></span>

```json
{
  "Settings": {
    "SiteTitle": "Amazing docs from Awesome people!",
    "Scale": 10,
    "VerbosityLevel": 32
  }
}
```

<span data-ttu-id="60ec5-206">下列類別會系結至設定 `"Settings"` 區段，並套用一些 `DataAnnotations` 規則：</span><span class="sxs-lookup"><span data-stu-id="60ec5-206">The following class binds to the `"Settings"` configuration section and applies a couple of `DataAnnotations` rules:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/SettingsOptions.cs":::

<span data-ttu-id="60ec5-207">下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="60ec5-207">The following code:</span></span>

- <span data-ttu-id="60ec5-208">呼叫 <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A> 以取得系結至類別的[OptionsBuilder \<TOptions> ](xref:Microsoft.Extensions.Options.OptionsBuilder%601) `SettingsOptions` 。</span><span class="sxs-lookup"><span data-stu-id="60ec5-208">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A> to get an [OptionsBuilder\<TOptions>](xref:Microsoft.Extensions.Options.OptionsBuilder%601) that binds to the `SettingsOptions` class.</span></span>
- <span data-ttu-id="60ec5-209"><xref:Microsoft.Extensions.DependencyInjection.OptionsBuilderDataAnnotationsExtensions.ValidateDataAnnotations%2A>使用呼叫來啟用驗證 `DataAnnotations` 。</span><span class="sxs-lookup"><span data-stu-id="60ec5-209">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsBuilderDataAnnotationsExtensions.ValidateDataAnnotations%2A> to enable validation using `DataAnnotations`.</span></span>

```csharp
services.AddOptions<SettingsOptions>()
    .Bind(Configuration.GetSection(SettingsOptions.Settings))
    .ValidateDataAnnotations();
```

<span data-ttu-id="60ec5-210">`ValidateDataAnnotations`擴充方法定義于[DataAnnotations](https://www.nuget.org/packages/Microsoft.Extensions.Options.DataAnnotations) NuGet 套件中。</span><span class="sxs-lookup"><span data-stu-id="60ec5-210">The `ValidateDataAnnotations` extension method is defined in the [Microsoft.Extensions.Options.DataAnnotations](https://www.nuget.org/packages/Microsoft.Extensions.Options.DataAnnotations) NuGet package.</span></span>

<span data-ttu-id="60ec5-211">下列程式碼顯示設定值或驗證錯誤：</span><span class="sxs-lookup"><span data-stu-id="60ec5-211">The following code displays the configuration values or the validation errors:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/ValidationService.cs":::

<span data-ttu-id="60ec5-212">下列程式碼會使用委派來套用更複雜的驗證規則：</span><span class="sxs-lookup"><span data-stu-id="60ec5-212">The following code applies a more complex validation rule using a delegate:</span></span>

```csharp
services.AddOptions<SettingsOptions>()
    .Bind(Configuration.GetSection(SettingsOptions.Settings))
    .ValidateDataAnnotations()
    .Validate(config =>
    {
        if (config.Scale != 0)
        {
            return config.VerbosityLevel > config.Scale;
        }

        return true;
    }, "VerbosityLevel must be > than Scale.");
```

### <a name="ivalidateoptions-for-complex-validation"></a><span data-ttu-id="60ec5-213">複雜驗證的 IValidateOptions</span><span class="sxs-lookup"><span data-stu-id="60ec5-213">IValidateOptions for complex validation</span></span>

<span data-ttu-id="60ec5-214">下列類別會實行 <xref:Microsoft.Extensions.Options.IValidateOptions%601> ：</span><span class="sxs-lookup"><span data-stu-id="60ec5-214">The following class implements <xref:Microsoft.Extensions.Options.IValidateOptions%601>:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/ValidateSettingsOptions.cs":::

<span data-ttu-id="60ec5-215">`IValidateOptions` 可將驗證程式代碼移至類別。</span><span class="sxs-lookup"><span data-stu-id="60ec5-215">`IValidateOptions` enables moving the validation code into a class.</span></span>

<span data-ttu-id="60ec5-216">使用上述程式碼，即可在中使用下列程式碼來啟用驗證 `ConfigureServices` ：</span><span class="sxs-lookup"><span data-stu-id="60ec5-216">Using the preceding code, validation is enabled in `ConfigureServices` with the following code:</span></span>

```csharp
services.Configure<SettingsOptions>(
    Configuration.GetSection(
        SettingsOptions.Settings));
services.TryAddEnumerable(
    ServiceDescriptor.Singleton
        <IValidateOptions<SettingsOptions>, ValidateSettingsOptions>());
```

## <a name="options-post-configuration"></a><span data-ttu-id="60ec5-217">選項設定後作業</span><span class="sxs-lookup"><span data-stu-id="60ec5-217">Options post-configuration</span></span>

<span data-ttu-id="60ec5-218">使用 <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601> 來設定設定後作業。</span><span class="sxs-lookup"><span data-stu-id="60ec5-218">Set post-configuration with <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601>.</span></span> <span data-ttu-id="60ec5-219">後續設定會在所有設定都發生之後執行 <xref:Microsoft.Extensions.Options.IConfigureOptions%601> ，而且在您需要覆寫設定的案例中很有用：</span><span class="sxs-lookup"><span data-stu-id="60ec5-219">Post-configuration runs after all <xref:Microsoft.Extensions.Options.IConfigureOptions%601> configuration occurs, and can be useful in scenarios when you need to override configuration:</span></span>

```csharp
services.PostConfigure<CustomOptions>(customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

<span data-ttu-id="60ec5-220"><xref:Microsoft.Extensions.Options.IPostConfigureOptions%601.PostConfigure%2A> 可用來後置設定具名選項：</span><span class="sxs-lookup"><span data-stu-id="60ec5-220"><xref:Microsoft.Extensions.Options.IPostConfigureOptions%601.PostConfigure%2A> is available to post-configure named options:</span></span>

```csharp
services.PostConfigure<CustomOptions>("named_options_1", customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

<span data-ttu-id="60ec5-221">使用 <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A> 後置設定所有設定執行個體：</span><span class="sxs-lookup"><span data-stu-id="60ec5-221">Use <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A> to post-configure all configuration instances:</span></span>

```csharp
services.PostConfigureAll<CustomOptions>(customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

## <a name="see-also"></a><span data-ttu-id="60ec5-222">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60ec5-222">See also</span></span>

- [<span data-ttu-id="60ec5-223">.NET 中的設定</span><span class="sxs-lookup"><span data-stu-id="60ec5-223">Configuration in .NET</span></span>](configuration.md)
