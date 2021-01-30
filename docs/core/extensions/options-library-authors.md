---
title: .NET 程式庫作者的選項模式指引
author: IEvangelist
description: 瞭解如何在 .NET 中以程式庫作者的形式公開選項模式。
ms.author: dapine
ms.date: 01/28/2021
ms.openlocfilehash: d0da94a8f25c9e5aba6093fab07ccca6a0a7c345
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99217210"
---
# <a name="options-pattern-guidance-for-net-library-authors"></a><span data-ttu-id="fc6ff-103">.NET 程式庫作者的選項模式指引</span><span class="sxs-lookup"><span data-stu-id="fc6ff-103">Options pattern guidance for .NET library authors</span></span>

<span data-ttu-id="fc6ff-104">在相依性插入的協助下，註冊您的服務及其對應的設定，就可以利用 *選項模式*。</span><span class="sxs-lookup"><span data-stu-id="fc6ff-104">With the help of dependency injection, registering your services and their corresponding configurations can make use of the *options pattern*.</span></span> <span data-ttu-id="fc6ff-105">選項模式可讓您程式庫 (的取用者和您的服務) 要求 [選項介面](options.md#options-interfaces) 的實例，其中 `TOptions` 是您的 options 類別。</span><span class="sxs-lookup"><span data-stu-id="fc6ff-105">The options pattern enables consumers of your library (and your services) to require instances of [options interfaces](options.md#options-interfaces) where `TOptions` is your options class.</span></span> <span data-ttu-id="fc6ff-106">透過強型別物件取用設定選項有助於確保一致的值表示，並移除手動剖析字串值的負擔。</span><span class="sxs-lookup"><span data-stu-id="fc6ff-106">Consuming configuration options through strongly-typed objects helps to ensure consistent value representation, and removes the burden of manually parsing string values.</span></span> <span data-ttu-id="fc6ff-107">您的程式庫取用者有許多設定 [提供者](configuration-providers.md) 可供使用。</span><span class="sxs-lookup"><span data-stu-id="fc6ff-107">There are many [configuration providers](configuration-providers.md) for consumers of your library to use.</span></span> <span data-ttu-id="fc6ff-108">透過這些提供者，取用者可以透過許多方式來設定您的程式庫。</span><span class="sxs-lookup"><span data-stu-id="fc6ff-108">With these providers, consumers can configure your library in many ways.</span></span>

<span data-ttu-id="fc6ff-109">作為 .NET 程式庫作者，您將瞭解如何正確地將選項模式公開給媒體櫃取用者的一般指引。</span><span class="sxs-lookup"><span data-stu-id="fc6ff-109">As a .NET library author, you'll learn general guidance on how to correctly expose the options pattern to consumers of your library.</span></span> <span data-ttu-id="fc6ff-110">有各種不同的方式可以達成相同的內容，以及進行幾項考慮。</span><span class="sxs-lookup"><span data-stu-id="fc6ff-110">There are various ways to achieve the same thing, and several considerations to make.</span></span>

## <a name="naming-conventions"></a><span data-ttu-id="fc6ff-111">命名規範</span><span class="sxs-lookup"><span data-stu-id="fc6ff-111">Naming conventions</span></span>

<span data-ttu-id="fc6ff-112">依照慣例，負責註冊服務的擴充方法會命名為 `Add{Service}` ，其中 `{Service}` 是有意義且描述性的名稱。</span><span class="sxs-lookup"><span data-stu-id="fc6ff-112">By convention, extension methods responsible for registering services are named `Add{Service}`, where `{Service}` is a meaningful and descriptive name.</span></span> <span data-ttu-id="fc6ff-113">根據套件的不同，服務的註冊可能會伴隨 `Use{Service}` 擴充方法。</span><span class="sxs-lookup"><span data-stu-id="fc6ff-113">Depending on the package, the registration of services may be accompanied by `Use{Service}` extension methods.</span></span> <span data-ttu-id="fc6ff-114">`Use{Service}`擴充方法在[ASP.NET Core](/aspnet)中很常見。</span><span class="sxs-lookup"><span data-stu-id="fc6ff-114">The `Use{Service}` extension methods are commonplace in [ASP.NET Core](/aspnet).</span></span>

<span data-ttu-id="fc6ff-115">✔️考慮可讓您的服務與其他供應專案區分的名稱。</span><span class="sxs-lookup"><span data-stu-id="fc6ff-115">✔️ CONSIDER names that disambiguate your service from other offerings.</span></span>

<span data-ttu-id="fc6ff-116">❌ 請勿使用已是官方 Microsoft 套件的 .NET 生態系統一部分的名稱。</span><span class="sxs-lookup"><span data-stu-id="fc6ff-116">❌ DO NOT use names that are already part of the .NET ecosystem from official Microsoft packages.</span></span>

<span data-ttu-id="fc6ff-117">✔️考慮將公開擴充方法的靜態類別命名為 `{Type}Extensions` ，其中 `{Type}` 是您要延伸的型別。</span><span class="sxs-lookup"><span data-stu-id="fc6ff-117">✔️ CONSIDER naming static classes that expose extension methods as `{Type}Extensions`, where `{Type}` is the type that you're extending.</span></span>

### <a name="namespace-guidance"></a><span data-ttu-id="fc6ff-118">命名空間指引</span><span class="sxs-lookup"><span data-stu-id="fc6ff-118">Namespace guidance</span></span>

<span data-ttu-id="fc6ff-119">Microsoft 套件會利用 `Microsoft.Extensions.DependencyInjection` 命名空間來統一註冊各種服務供應專案。</span><span class="sxs-lookup"><span data-stu-id="fc6ff-119">Microsoft packages make use of the `Microsoft.Extensions.DependencyInjection` namespace to unify the registration of various service offerings.</span></span>

<span data-ttu-id="fc6ff-120">✔️考慮清楚識別套件供應專案的命名空間。</span><span class="sxs-lookup"><span data-stu-id="fc6ff-120">✔️ CONSIDER a namespace that clearly identifies your package offering.</span></span>

<span data-ttu-id="fc6ff-121">❌ 請勿將 `Microsoft.Extensions.DependencyInjection` 命名空間用於非官方 Microsoft 套件。</span><span class="sxs-lookup"><span data-stu-id="fc6ff-121">❌ DO NOT use the `Microsoft.Extensions.DependencyInjection` namespace for non-official Microsoft packages.</span></span>

## <a name="parameterless"></a><span data-ttu-id="fc6ff-122">依據</span><span class="sxs-lookup"><span data-stu-id="fc6ff-122">Parameterless</span></span>

<span data-ttu-id="fc6ff-123">如果您的服務可以使用最少量或沒有明確的設定，請考慮使用無參數的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="fc6ff-123">If your service can work with minimal or no explicit configuration, consider a parameterless extension method.</span></span>

:::code language="csharp" source="snippets/configuration/options-noparams/ServiceCollectionExtensions.cs" highlight="10-14":::

<span data-ttu-id="fc6ff-124">在上述程式碼中， `AddMyLibraryService` ：</span><span class="sxs-lookup"><span data-stu-id="fc6ff-124">In the preceding code, the `AddMyLibraryService`:</span></span>

- <span data-ttu-id="fc6ff-125">擴充的實例 <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span><span class="sxs-lookup"><span data-stu-id="fc6ff-125">Extends an instance of <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span></span>
- <span data-ttu-id="fc6ff-126"><xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection)?displayProperty=nameWithType>使用型別參數的呼叫`LibraryOptions`</span><span class="sxs-lookup"><span data-stu-id="fc6ff-126">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection)?displayProperty=nameWithType> with the type parameter of `LibraryOptions`</span></span>
- <span data-ttu-id="fc6ff-127">將呼叫連結至 <xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A> ，以指定預設選項值</span><span class="sxs-lookup"><span data-stu-id="fc6ff-127">Chains a call to <xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A>, which specifies the default option values</span></span>

## <a name="iconfiguration-parameter"></a><span data-ttu-id="fc6ff-128">`IConfiguration` 參數</span><span class="sxs-lookup"><span data-stu-id="fc6ff-128">`IConfiguration` parameter</span></span>

<span data-ttu-id="fc6ff-129">當您撰寫可向取用者公開許多選項的程式庫時，您可能會想要考慮要求 `IConfiguration` 參數擴充方法。</span><span class="sxs-lookup"><span data-stu-id="fc6ff-129">When you author a library that exposes many options to consumers, you may want to consider requiring an `IConfiguration` parameter extension method.</span></span> <span data-ttu-id="fc6ff-130">預期的 `IConfiguration` 實例應該使用函數，將範圍設定為設定的命名區段 <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="fc6ff-130">The expected `IConfiguration` instance should be scoped to a named section of the configuration by using the <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A?displayProperty=nameWithType> function.</span></span>

:::code language="csharp" source="snippets/configuration/options-configparam/ServiceCollectionExtensions.cs" highlight="10,12-16":::

<span data-ttu-id="fc6ff-131">在上述程式碼中， `AddMyLibraryService` ：</span><span class="sxs-lookup"><span data-stu-id="fc6ff-131">In the preceding code, the `AddMyLibraryService`:</span></span>

- <span data-ttu-id="fc6ff-132">擴充的實例 <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span><span class="sxs-lookup"><span data-stu-id="fc6ff-132">Extends an instance of <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span></span>
- <span data-ttu-id="fc6ff-133">定義 <xref:Microsoft.Extensions.Configuration.IConfiguration> 參數 `namedConfigurationSection`</span><span class="sxs-lookup"><span data-stu-id="fc6ff-133">Defines an <xref:Microsoft.Extensions.Configuration.IConfiguration> parameter `namedConfigurationSection`</span></span>
- <span data-ttu-id="fc6ff-134">傳遞設定所系結之 <xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Bind(Microsoft.Extensions.Configuration.IConfiguration,System.Object)> 選項實例的呼叫</span><span class="sxs-lookup"><span data-stu-id="fc6ff-134">Calls <xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Bind(Microsoft.Extensions.Configuration.IConfiguration,System.Object)> passing an options instance that the configuration binds to</span></span>

<span data-ttu-id="fc6ff-135">這種模式的取用者會提供 `IConfiguration` 已命名之區段的範圍實例：</span><span class="sxs-lookup"><span data-stu-id="fc6ff-135">Consumers in this pattern provide the scoped `IConfiguration` instance of the named section:</span></span>

:::code language="csharp" source="snippets/configuration/options-configparam/Program.cs" highlight="22-23":::

<span data-ttu-id="fc6ff-136">呼叫 `.AddMyLibraryService` 會在方法中進行 <xref:Microsoft.Extensions.Hosting.IHostBuilder.ConfigureServices%2A> 。</span><span class="sxs-lookup"><span data-stu-id="fc6ff-136">The call to `.AddMyLibraryService` is made in the <xref:Microsoft.Extensions.Hosting.IHostBuilder.ConfigureServices%2A> method.</span></span> <span data-ttu-id="fc6ff-137">使用類別時也是如此 `Startup` ，註冊的服務也會在中進行 `ConfigureServices` 。</span><span class="sxs-lookup"><span data-stu-id="fc6ff-137">The same is true when using a `Startup` class, the addition of services being registered occurs in `ConfigureServices`.</span></span>

<span data-ttu-id="fc6ff-138">以程式庫作者來說，指定預設值是由您負責。</span><span class="sxs-lookup"><span data-stu-id="fc6ff-138">As the library author, specifying default values is up to you.</span></span>

> [!NOTE]
> <span data-ttu-id="fc6ff-139">您可以將設定系結至選項實例。</span><span class="sxs-lookup"><span data-stu-id="fc6ff-139">It is possible to bind configuration to an options instance.</span></span> <span data-ttu-id="fc6ff-140">不過，有名稱衝突的風險，這會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="fc6ff-140">However, there is a risk of name collisions - which will cause errors.</span></span> <span data-ttu-id="fc6ff-141">此外，當以這種方式手動系結時，您可以將選項模式的耗用量限制為唯讀。</span><span class="sxs-lookup"><span data-stu-id="fc6ff-141">Additionally, when manually binding in this way, you limit the consumption of your options pattern to read-once.</span></span> <span data-ttu-id="fc6ff-142">設定的變更不會重新系結，因為這類取用者將無法使用 [IOptionsMonitor](options.md#ioptionsmonitor) 介面。</span><span class="sxs-lookup"><span data-stu-id="fc6ff-142">Changes to settings will not be re-bound, as such consumers will not be able to use the [IOptionsMonitor](options.md#ioptionsmonitor) interface.</span></span>
>
> ```csharp
> services.AddOptions<LibraryOptions>()
>     .Configure<IConfiguration>(
>         (options, configuration) =>
>             configuration.GetSection("LibraryOptions").Bind(options));
> ```

## <a name="actiontoptions-parameter"></a><span data-ttu-id="fc6ff-143">`Action<TOptions>` 參數</span><span class="sxs-lookup"><span data-stu-id="fc6ff-143">`Action<TOptions>` parameter</span></span>

<span data-ttu-id="fc6ff-144">您程式庫的取用者可能會想要提供 lambda 運算式來產生 options 類別的實例。</span><span class="sxs-lookup"><span data-stu-id="fc6ff-144">Consumers of your library may be interested in providing a lambda expression that yields an instance of your options class.</span></span> <span data-ttu-id="fc6ff-145">在此案例中，您會 `Action<LibraryOptions>` 在擴充方法中定義參數。</span><span class="sxs-lookup"><span data-stu-id="fc6ff-145">In this scenario, you define an `Action<LibraryOptions>` parameter in your extension method.</span></span>

:::code language="csharp" source="snippets/configuration/options-action/ServiceCollectionExtensions.cs" highlight="10,12":::

<span data-ttu-id="fc6ff-146">在上述程式碼中， `AddMyLibraryService` ：</span><span class="sxs-lookup"><span data-stu-id="fc6ff-146">In the preceding code, the `AddMyLibraryService`:</span></span>

- <span data-ttu-id="fc6ff-147">擴充的實例 <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span><span class="sxs-lookup"><span data-stu-id="fc6ff-147">Extends an instance of <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span></span>
- <span data-ttu-id="fc6ff-148">定義 <xref:System.Action%601> where `T` 是 `LibraryOptions` 參數 `configureOptions`</span><span class="sxs-lookup"><span data-stu-id="fc6ff-148">Defines an <xref:System.Action%601> where `T` is `LibraryOptions` parameter `configureOptions`</span></span>
- <span data-ttu-id="fc6ff-149"><xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.Configure%2A>指定動作的 `configureOptions` 呼叫</span><span class="sxs-lookup"><span data-stu-id="fc6ff-149">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.Configure%2A> given the `configureOptions` action</span></span>

<span data-ttu-id="fc6ff-150">這種模式的取用者會提供 lambda 運算式 (或符合 `Action<LibraryOptions>` 參數) 的委派：</span><span class="sxs-lookup"><span data-stu-id="fc6ff-150">Consumers in this pattern provide a lambda expression (or a delegate that satisfies the `Action<LibraryOptions>` parameter):</span></span>

:::code language="csharp" source="snippets/configuration/options-action/Program.cs" highlight="22-26":::

## <a name="options-instance-parameter"></a><span data-ttu-id="fc6ff-151">選項實例參數</span><span class="sxs-lookup"><span data-stu-id="fc6ff-151">Options instance parameter</span></span>

<span data-ttu-id="fc6ff-152">您程式庫的取用者可能會想要提供內嵌的選項實例。</span><span class="sxs-lookup"><span data-stu-id="fc6ff-152">Consumers of your library might prefer to provide an inlined options instance.</span></span> <span data-ttu-id="fc6ff-153">在此案例中，您會公開擴充方法，以接受選項物件的實例 `LibraryOptions` 。</span><span class="sxs-lookup"><span data-stu-id="fc6ff-153">In this scenario, you expose an extension method that takes an instance of your options object, `LibraryOptions`.</span></span>

:::code language="csharp" source="snippets/configuration/options-object/ServiceCollectionExtensions.cs" highlight="9,11-17":::

<span data-ttu-id="fc6ff-154">在上述程式碼中， `AddMyLibraryService` ：</span><span class="sxs-lookup"><span data-stu-id="fc6ff-154">In the preceding code, the `AddMyLibraryService`:</span></span>

- <span data-ttu-id="fc6ff-155">擴充的實例 <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span><span class="sxs-lookup"><span data-stu-id="fc6ff-155">Extends an instance of <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span></span>
- <span data-ttu-id="fc6ff-156"><xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection)?displayProperty=nameWithType>使用型別參數的呼叫`LibraryOptions`</span><span class="sxs-lookup"><span data-stu-id="fc6ff-156">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection)?displayProperty=nameWithType> with the type parameter of `LibraryOptions`</span></span>
- <span data-ttu-id="fc6ff-157">將呼叫連結到 <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.Configure%2A> ，指定可以從指定的實例覆寫的預設選項值 `userOptions`</span><span class="sxs-lookup"><span data-stu-id="fc6ff-157">Chains a call to <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.Configure%2A>, which specifies default option values that can be overridden from the given `userOptions` instance</span></span>

<span data-ttu-id="fc6ff-158">這種模式的取用者會提供類別的實例，並以 `LibraryOptions` 內嵌方式定義所需的屬性值：</span><span class="sxs-lookup"><span data-stu-id="fc6ff-158">Consumers in this pattern provide an instance of the `LibraryOptions` class, defining desired property values inline:</span></span>

:::code language="csharp" source="snippets/configuration/options-object/Program.cs" highlight="22-26":::

## <a name="post-configuration"></a><span data-ttu-id="fc6ff-159">設定前</span><span class="sxs-lookup"><span data-stu-id="fc6ff-159">Post configuration</span></span>

<span data-ttu-id="fc6ff-160">系結或指定所有設定選項值之後，便可使用 post 設定功能。</span><span class="sxs-lookup"><span data-stu-id="fc6ff-160">After all configuration option values are bound or specified, post configuration functionality is available.</span></span> <span data-ttu-id="fc6ff-161">如先前所述公開相同的[ `Action<TOptions>` 參數](#actiontoptions-parameter)，您可以選擇呼叫 <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigure%2A> 。</span><span class="sxs-lookup"><span data-stu-id="fc6ff-161">Exposing the same [`Action<TOptions>` parameter](#actiontoptions-parameter) detailed earlier, you could choose to call <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigure%2A>.</span></span> <span data-ttu-id="fc6ff-162">Post 設定會在所有 `.Configure` 呼叫之後執行。</span><span class="sxs-lookup"><span data-stu-id="fc6ff-162">Post configure runs after all `.Configure` calls.</span></span>

:::code language="csharp" source="snippets/configuration/options-postconfig/ServiceCollectionExtensions.cs" highlight="10,12":::

<span data-ttu-id="fc6ff-163">在上述程式碼中， `AddMyLibraryService` ：</span><span class="sxs-lookup"><span data-stu-id="fc6ff-163">In the preceding code, the `AddMyLibraryService`:</span></span>

- <span data-ttu-id="fc6ff-164">擴充的實例 <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span><span class="sxs-lookup"><span data-stu-id="fc6ff-164">Extends an instance of <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span></span>
- <span data-ttu-id="fc6ff-165">定義 <xref:System.Action%601> where `T` 是 `LibraryOptions` 參數 `configureOptions`</span><span class="sxs-lookup"><span data-stu-id="fc6ff-165">Defines an <xref:System.Action%601> where `T` is `LibraryOptions` parameter `configureOptions`</span></span>
- <span data-ttu-id="fc6ff-166"><xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigure%2A>指定動作的 `configureOptions` 呼叫</span><span class="sxs-lookup"><span data-stu-id="fc6ff-166">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigure%2A> given the `configureOptions` action</span></span>

<span data-ttu-id="fc6ff-167">這種模式的取用者會提供 lambda 運算式 (或符合 `Action<LibraryOptions>` 參數) 的委派，就像 `Action<TOptions>` 在非 post 設定案例中使用 [參數] 一樣：</span><span class="sxs-lookup"><span data-stu-id="fc6ff-167">Consumers in this pattern provide a lambda expression (or a delegate that satisfies the `Action<LibraryOptions>` parameter), just as they would with the [`Action<TOptions>` parameter] in a non-post configuration scenario:</span></span>

:::code language="csharp" source="snippets/configuration/options-postconfig/Program.cs" highlight="22-26":::

## <a name="see-also"></a><span data-ttu-id="fc6ff-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc6ff-168">See also</span></span>

- [<span data-ttu-id="fc6ff-169">.NET 中的選項模式</span><span class="sxs-lookup"><span data-stu-id="fc6ff-169">Options pattern in .NET</span></span>](options.md)
- [<span data-ttu-id="fc6ff-170">.NET 中的相依性插入</span><span class="sxs-lookup"><span data-stu-id="fc6ff-170">Dependency injection in .NET</span></span>](dependency-injection.md)
- [<span data-ttu-id="fc6ff-171">相依性插入指導方針</span><span class="sxs-lookup"><span data-stu-id="fc6ff-171">Dependency injection guidelines</span></span>](dependency-injection-guidelines.md)
