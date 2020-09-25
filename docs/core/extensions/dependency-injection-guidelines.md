---
title: 相依性插入方針
description: 瞭解各種相依性插入指導方針和 .NET 應用程式開發的最佳做法。
author: IEvangelist
ms.author: dapine
ms.date: 09/23/2020
ms.topic: guide
ms.openlocfilehash: a8d52642b9217c7340db69494624d8ab85ea6c92
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2020
ms.locfileid: "91247888"
---
# <a name="dependency-injection-guidelines"></a><span data-ttu-id="d54a2-103">相依性插入方針</span><span class="sxs-lookup"><span data-stu-id="d54a2-103">Dependency injection guidelines</span></span>

<span data-ttu-id="d54a2-104">本文提供在 .NET 應用程式中執行相依性插入的一般指導方針和最佳作法。</span><span class="sxs-lookup"><span data-stu-id="d54a2-104">This article provides general guidelines and best practices for implementing dependency injection in .NET applications.</span></span>

## <a name="design-services-for-dependency-injection"></a><span data-ttu-id="d54a2-105">針對相依性插入設計服務</span><span class="sxs-lookup"><span data-stu-id="d54a2-105">Design services for dependency injection</span></span>

<span data-ttu-id="d54a2-106">針對相依性插入設計服務時：</span><span class="sxs-lookup"><span data-stu-id="d54a2-106">When designing services for dependency injection:</span></span>

- <span data-ttu-id="d54a2-107">避免具狀態、靜態類別和成員。</span><span class="sxs-lookup"><span data-stu-id="d54a2-107">Avoid stateful, static classes and members.</span></span> <span data-ttu-id="d54a2-108">請改為使用單一服務來設計應用程式，以避免建立全域狀態。</span><span class="sxs-lookup"><span data-stu-id="d54a2-108">Avoid creating global state by designing apps to use singleton services instead.</span></span>
- <span data-ttu-id="d54a2-109">避免直接在服務內具現化相依類別。</span><span class="sxs-lookup"><span data-stu-id="d54a2-109">Avoid direct instantiation of dependent classes within services.</span></span> <span data-ttu-id="d54a2-110">直接具現化會將程式碼耦合到特定實作。</span><span class="sxs-lookup"><span data-stu-id="d54a2-110">Direct instantiation couples the code to a particular implementation.</span></span>
- <span data-ttu-id="d54a2-111">使服務更小、妥善組成且輕鬆地進行測試。</span><span class="sxs-lookup"><span data-stu-id="d54a2-111">Make services small, well-factored, and easily tested.</span></span>

<span data-ttu-id="d54a2-112">如果類別有許多插入的相依性，可能是因為類別具有太多責任，而且違反了 [單一責任原則 (SRP) ](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#single-responsibility)。</span><span class="sxs-lookup"><span data-stu-id="d54a2-112">If a class has many injected dependencies, it might be a sign that the class has too many responsibilities and violates the [Single Responsibility Principle (SRP)](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#single-responsibility).</span></span> <span data-ttu-id="d54a2-113">嘗試將其部分責任移至新的類別，以重構類別。</span><span class="sxs-lookup"><span data-stu-id="d54a2-113">Attempt to refactor the class by moving some of its responsibilities into new classes.</span></span>

### <a name="disposal-of-services"></a><span data-ttu-id="d54a2-114">處置服務</span><span class="sxs-lookup"><span data-stu-id="d54a2-114">Disposal of services</span></span>

<span data-ttu-id="d54a2-115">容器會負責清除其所建立的類型，並 <xref:System.IDisposable.Dispose%2A> 在實例上呼叫 <xref:System.IDisposable> 。</span><span class="sxs-lookup"><span data-stu-id="d54a2-115">The container is responsible for cleanup of types it creates, and calls <xref:System.IDisposable.Dispose%2A> on <xref:System.IDisposable> instances.</span></span> <span data-ttu-id="d54a2-116">從容器解析的服務絕對不能由開發人員處置。</span><span class="sxs-lookup"><span data-stu-id="d54a2-116">Services resolved from the container should never be disposed by the developer.</span></span> <span data-ttu-id="d54a2-117">如果類型或 factory 註冊為 singleton，則容器會自動處置 singleton。</span><span class="sxs-lookup"><span data-stu-id="d54a2-117">If a type or factory is registered as a singleton, the container disposes the singleton automatically.</span></span>

<span data-ttu-id="d54a2-118">在下列範例中，服務是由服務容器建立並自動處置：</span><span class="sxs-lookup"><span data-stu-id="d54a2-118">In the following example, the services are created by the service container and disposed automatically:</span></span>

:::code language="csharp" source="snippets/configuration/console-di-disposable/TransientDisposable.cs":::

:::code language="csharp" source="snippets/configuration/console-di-disposable/ScopedDisposable.cs":::

:::code language="csharp" source="snippets/configuration/console-di-disposable/SingletonDisposable.cs":::

:::code language="csharp" source="snippets/configuration/console-di-disposable/Program.cs" range="1-21,41-60":::

<span data-ttu-id="d54a2-119">在執行之後，debug 主控台會顯示下列範例輸出：</span><span class="sxs-lookup"><span data-stu-id="d54a2-119">The debug console shows the following sample output after running:</span></span>

```console
Scope 1...
ScopedDisposable.Dispose()
TransientDisposable.Dispose()

Scope 2...
ScopedDisposable.Dispose()
TransientDisposable.Dispose()

info: Microsoft.Hosting.Lifetime[0]
      Application started.Press Ctrl+C to shut down.
info: Microsoft.Hosting.Lifetime[0]
     Hosting environment: Production
info: Microsoft.Hosting.Lifetime[0]
     Content root path: .\configuration\console-di-disposable\bin\Debug\net5.0
info: Microsoft.Hosting.Lifetime[0]
     Application is shutting down...
SingletonDisposable.Dispose()
```

### <a name="services-not-created-by-the-service-container"></a><span data-ttu-id="d54a2-120">服務容器未建立的服務</span><span class="sxs-lookup"><span data-stu-id="d54a2-120">Services not created by the service container</span></span>

<span data-ttu-id="d54a2-121">請考慮下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="d54a2-121">Consider the following code:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddSingleton(new ExampleService());

    // ...
}
```

<span data-ttu-id="d54a2-122">在上述程式碼中：</span><span class="sxs-lookup"><span data-stu-id="d54a2-122">In the preceding code:</span></span>

- <span data-ttu-id="d54a2-123">此 `ExampleService` 實例不**not**是由服務容器所建立。</span><span class="sxs-lookup"><span data-stu-id="d54a2-123">The `ExampleService` instance is **not** created by the service container.</span></span>
- <span data-ttu-id="d54a2-124">架構 **不會自動處置服務** 。</span><span class="sxs-lookup"><span data-stu-id="d54a2-124">The framework does **not** dispose of the services automatically.</span></span>
- <span data-ttu-id="d54a2-125">開發人員負責處置服務。</span><span class="sxs-lookup"><span data-stu-id="d54a2-125">The developer is responsible for disposing the services.</span></span>

### <a name="idisposable-guidance-for-transient-and-shared-instances"></a><span data-ttu-id="d54a2-126">暫時性和共用實例的 IDisposable 指引</span><span class="sxs-lookup"><span data-stu-id="d54a2-126">IDisposable guidance for Transient and shared instances</span></span>

#### <a name="transient-limited-lifetime"></a><span data-ttu-id="d54a2-127">暫時性、有限存留期</span><span class="sxs-lookup"><span data-stu-id="d54a2-127">Transient, limited lifetime</span></span>

<span data-ttu-id="d54a2-128">**案例**</span><span class="sxs-lookup"><span data-stu-id="d54a2-128">**Scenario**</span></span>

<span data-ttu-id="d54a2-129">應用程式需要在 <xref:System.IDisposable> 下列任一案例中具有暫時性存留期的實例：</span><span class="sxs-lookup"><span data-stu-id="d54a2-129">The app requires an <xref:System.IDisposable> instance with a transient lifetime for either of the following scenarios:</span></span>

- <span data-ttu-id="d54a2-130"> (根容器) 的根範圍中解析實例。</span><span class="sxs-lookup"><span data-stu-id="d54a2-130">The instance is resolved in the root scope (root container).</span></span>
- <span data-ttu-id="d54a2-131">實例應該在範圍結束之前處置。</span><span class="sxs-lookup"><span data-stu-id="d54a2-131">The instance should be disposed before the scope ends.</span></span>

<span data-ttu-id="d54a2-132">**方案**</span><span class="sxs-lookup"><span data-stu-id="d54a2-132">**Solution**</span></span>

<span data-ttu-id="d54a2-133">使用 factory 模式，在父範圍之外建立實例。</span><span class="sxs-lookup"><span data-stu-id="d54a2-133">Use the factory pattern to create an instance outside of the parent scope.</span></span> <span data-ttu-id="d54a2-134">在這種情況下，應用程式通常會有 `Create` 方法可直接呼叫最終型別的函式。</span><span class="sxs-lookup"><span data-stu-id="d54a2-134">In this situation, the app would generally have a `Create` method that calls the final type's constructor directly.</span></span> <span data-ttu-id="d54a2-135">如果最終類型有其他相依性，factory 可以：</span><span class="sxs-lookup"><span data-stu-id="d54a2-135">If the final type has other dependencies, the factory can:</span></span>

- <span data-ttu-id="d54a2-136"><xref:System.IServiceProvider>在其函式中接收。</span><span class="sxs-lookup"><span data-stu-id="d54a2-136">Receive an <xref:System.IServiceProvider> in its constructor.</span></span>
- <span data-ttu-id="d54a2-137">使用 <xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities.CreateInstance%2A?displayProperty=nameWithType> 可在容器外部具現化實例，同時使用容器作為其相依性。</span><span class="sxs-lookup"><span data-stu-id="d54a2-137">Use <xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities.CreateInstance%2A?displayProperty=nameWithType> to instantiate the instance outside of the container, while using the container for its dependencies.</span></span>

#### <a name="shared-instance-limited-lifetime"></a><span data-ttu-id="d54a2-138">共用實例，有限存留期</span><span class="sxs-lookup"><span data-stu-id="d54a2-138">Shared instance, limited lifetime</span></span>

<span data-ttu-id="d54a2-139">**案例**</span><span class="sxs-lookup"><span data-stu-id="d54a2-139">**Scenario**</span></span>

<span data-ttu-id="d54a2-140">應用程式需要 <xref:System.IDisposable> 跨多個服務的共用實例，但 <xref:System.IDisposable> 實例的存留期應受限。</span><span class="sxs-lookup"><span data-stu-id="d54a2-140">The app requires a shared <xref:System.IDisposable> instance across multiple services, but the <xref:System.IDisposable> instance should have a limited lifetime.</span></span>

<span data-ttu-id="d54a2-141">**方案**</span><span class="sxs-lookup"><span data-stu-id="d54a2-141">**Solution**</span></span>

<span data-ttu-id="d54a2-142">註冊具有範圍存留期的實例。</span><span class="sxs-lookup"><span data-stu-id="d54a2-142">Register the instance with a scoped lifetime.</span></span> <span data-ttu-id="d54a2-143">使用 <xref:Microsoft.Extensions.DependencyInjection.IServiceScopeFactory.CreateScope%2A?displayProperty=nameWithType> 建立新的 <xref:Microsoft.Extensions.DependencyInjection.IServiceScope> 。</span><span class="sxs-lookup"><span data-stu-id="d54a2-143">Use <xref:Microsoft.Extensions.DependencyInjection.IServiceScopeFactory.CreateScope%2A?displayProperty=nameWithType> to create a new <xref:Microsoft.Extensions.DependencyInjection.IServiceScope>.</span></span> <span data-ttu-id="d54a2-144">使用範圍 <xref:System.IServiceProvider> 來取得所需的服務。</span><span class="sxs-lookup"><span data-stu-id="d54a2-144">Use the scope's <xref:System.IServiceProvider> to get required services.</span></span> <span data-ttu-id="d54a2-145">不再需要時處置範圍。</span><span class="sxs-lookup"><span data-stu-id="d54a2-145">Dispose the scope when it's no longer needed.</span></span>

#### <a name="general-idisposable-guidelines"></a><span data-ttu-id="d54a2-146">一般 `IDisposable` 指導方針</span><span class="sxs-lookup"><span data-stu-id="d54a2-146">General `IDisposable` guidelines</span></span>

- <span data-ttu-id="d54a2-147">請勿 <xref:System.IDisposable> 在暫時性的存留期內註冊實例。</span><span class="sxs-lookup"><span data-stu-id="d54a2-147">Don't register <xref:System.IDisposable> instances with a transient lifetime.</span></span> <span data-ttu-id="d54a2-148">請改用 factory 模式。</span><span class="sxs-lookup"><span data-stu-id="d54a2-148">Use the factory pattern instead.</span></span>
- <span data-ttu-id="d54a2-149">請勿 <xref:System.IDisposable> 在根範圍中解析具有暫時性或範圍存留期的實例。</span><span class="sxs-lookup"><span data-stu-id="d54a2-149">Don't resolve <xref:System.IDisposable> instances with a transient or scoped lifetime in the root scope.</span></span> <span data-ttu-id="d54a2-150">唯一的例外是應用程式建立/重新建立和處置 <xref:System.IServiceProvider> ，但這不是理想的模式。</span><span class="sxs-lookup"><span data-stu-id="d54a2-150">The only exception to this is if the app creates/recreates and disposes <xref:System.IServiceProvider>, but this isn't an ideal pattern.</span></span>
- <span data-ttu-id="d54a2-151">透過 DI 接收相依性 <xref:System.IDisposable> 不需要接收者 <xref:System.IDisposable> 自行執行。</span><span class="sxs-lookup"><span data-stu-id="d54a2-151">Receiving an <xref:System.IDisposable> dependency via DI doesn't require that the receiver implement <xref:System.IDisposable> itself.</span></span> <span data-ttu-id="d54a2-152">相依性的接收者不 <xref:System.IDisposable> 應呼叫 <xref:System.IDisposable.Dispose%2A> 該相依性。</span><span class="sxs-lookup"><span data-stu-id="d54a2-152">The receiver of the <xref:System.IDisposable> dependency shouldn't call <xref:System.IDisposable.Dispose%2A> on that dependency.</span></span>
- <span data-ttu-id="d54a2-153">使用範圍來控制服務的存留期。</span><span class="sxs-lookup"><span data-stu-id="d54a2-153">Use scopes to control the lifetimes of services.</span></span> <span data-ttu-id="d54a2-154">範圍不是階層式，而且範圍之間沒有特殊連接。</span><span class="sxs-lookup"><span data-stu-id="d54a2-154">Scopes aren't hierarchical, and there's no special connection among scopes.</span></span>

<span data-ttu-id="d54a2-155">如需資源清除的詳細資訊，請參閱實 [作為處置方法](../../standard/garbage-collection/implementing-dispose.md)</span><span class="sxs-lookup"><span data-stu-id="d54a2-155">For more information on resource cleanup, see [Implement a Dispose method](../../standard/garbage-collection/implementing-dispose.md)</span></span>

## <a name="default-service-container-replacement"></a><span data-ttu-id="d54a2-156">預設服務容器取代</span><span class="sxs-lookup"><span data-stu-id="d54a2-156">Default service container replacement</span></span>

<span data-ttu-id="d54a2-157">內建的服務容器是設計來滿足架構和大部分消費者應用程式的需求。</span><span class="sxs-lookup"><span data-stu-id="d54a2-157">The built-in service container is designed to serve the needs of the framework and most consumer apps.</span></span> <span data-ttu-id="d54a2-158">除非您需要不支援的特定功能，否則建議使用內建容器，例如：</span><span class="sxs-lookup"><span data-stu-id="d54a2-158">We recommend using the built-in container unless you need a specific feature that it doesn't support, such as:</span></span>

- <span data-ttu-id="d54a2-159">屬性插入</span><span class="sxs-lookup"><span data-stu-id="d54a2-159">Property injection</span></span>
- <span data-ttu-id="d54a2-160">根據名稱插入</span><span class="sxs-lookup"><span data-stu-id="d54a2-160">Injection based on name</span></span>
- <span data-ttu-id="d54a2-161">子容器</span><span class="sxs-lookup"><span data-stu-id="d54a2-161">Child containers</span></span>
- <span data-ttu-id="d54a2-162">自訂生命週期管理</span><span class="sxs-lookup"><span data-stu-id="d54a2-162">Custom lifetime management</span></span>
- <span data-ttu-id="d54a2-163">`Func<T>` 支援延遲初始設定</span><span class="sxs-lookup"><span data-stu-id="d54a2-163">`Func<T>` support for lazy initialization</span></span>
- <span data-ttu-id="d54a2-164">以慣例為基礎的註冊</span><span class="sxs-lookup"><span data-stu-id="d54a2-164">Convention-based registration</span></span>

<span data-ttu-id="d54a2-165">下列協力廠商容器可搭配 ASP.NET Core apps 使用：</span><span class="sxs-lookup"><span data-stu-id="d54a2-165">The following third-party containers can be used with ASP.NET Core apps:</span></span>

- [<span data-ttu-id="d54a2-166">Autofac</span><span class="sxs-lookup"><span data-stu-id="d54a2-166">Autofac</span></span>](https://autofac.readthedocs.io/en/latest/integration/aspnetcore.html)
- [<span data-ttu-id="d54a2-167">DryIoc</span><span class="sxs-lookup"><span data-stu-id="d54a2-167">DryIoc</span></span>](https://www.nuget.org/packages/DryIoc.Microsoft.DependencyInjection)
- [<span data-ttu-id="d54a2-168">Grace</span><span class="sxs-lookup"><span data-stu-id="d54a2-168">Grace</span></span>](https://www.nuget.org/packages/Grace.DependencyInjection.Extensions)
- [<span data-ttu-id="d54a2-169">LightInject</span><span class="sxs-lookup"><span data-stu-id="d54a2-169">LightInject</span></span>](https://github.com/seesharper/LightInject.Microsoft.DependencyInjection)
- [<span data-ttu-id="d54a2-170">拉馬爾</span><span class="sxs-lookup"><span data-stu-id="d54a2-170">Lamar</span></span>](https://jasperfx.github.io/lamar/)
- [<span data-ttu-id="d54a2-171">Stashbox</span><span class="sxs-lookup"><span data-stu-id="d54a2-171">Stashbox</span></span>](https://github.com/z4kn4fein/stashbox-extensions-dependencyinjection)
- [<span data-ttu-id="d54a2-172">Unity</span><span class="sxs-lookup"><span data-stu-id="d54a2-172">Unity</span></span>](https://www.nuget.org/packages/Unity.Microsoft.DependencyInjection)

## <a name="thread-safety"></a><span data-ttu-id="d54a2-173">執行緒安全</span><span class="sxs-lookup"><span data-stu-id="d54a2-173">Thread safety</span></span>

<span data-ttu-id="d54a2-174">建立具備執行緒安全性的 singleton 服務。</span><span class="sxs-lookup"><span data-stu-id="d54a2-174">Create thread-safe singleton services.</span></span> <span data-ttu-id="d54a2-175">如果單一服務相依于暫時性服務，暫時性服務可能也需要執行緒安全性，取決於 singleton 使用它的方式。</span><span class="sxs-lookup"><span data-stu-id="d54a2-175">If a singleton service has a dependency on a transient service, the transient service may also require thread safety depending on how it's used by the singleton.</span></span>

<span data-ttu-id="d54a2-176">單一服務的 factory 方法（例如 >addsingleton 的第二個自 [變數 \<TService> (IServiceCollection、Func \<IServiceProvider,TService>) ](xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A)）不需要是安全線程。</span><span class="sxs-lookup"><span data-stu-id="d54a2-176">The factory method of single service, such as the second argument to [AddSingleton\<TService>(IServiceCollection, Func\<IServiceProvider,TService>)](xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A), doesn't need to be thread-safe.</span></span> <span data-ttu-id="d54a2-177">如同型別 () 的函式 `static` ，它保證只能由單一線程呼叫一次。</span><span class="sxs-lookup"><span data-stu-id="d54a2-177">Like a type (`static`) constructor, it's guaranteed to be called only once by a single thread.</span></span>

## <a name="recommendations"></a><span data-ttu-id="d54a2-178">建議</span><span class="sxs-lookup"><span data-stu-id="d54a2-178">Recommendations</span></span>

- <span data-ttu-id="d54a2-179">`async/await` 並 `Task` 不支援以服務為基礎的服務解析。</span><span class="sxs-lookup"><span data-stu-id="d54a2-179">`async/await` and `Task` based service resolution isn't supported.</span></span> <span data-ttu-id="d54a2-180">因為 c # 不支援非同步函式，所以請在以同步方式解析服務後使用非同步方法。</span><span class="sxs-lookup"><span data-stu-id="d54a2-180">Because C# doesn't support asynchronous constructors, use asynchronous methods after synchronously resolving the service.</span></span>
- <span data-ttu-id="d54a2-181">避免直接在服務容器中儲存資料與設定。</span><span class="sxs-lookup"><span data-stu-id="d54a2-181">Avoid storing data and configuration directly in the service container.</span></span> <span data-ttu-id="d54a2-182">例如，使用者的購物車通常不應該新增至服務容器。</span><span class="sxs-lookup"><span data-stu-id="d54a2-182">For example, a user's shopping cart shouldn't typically be added to the service container.</span></span> <span data-ttu-id="d54a2-183">組態應該使用選項模式。</span><span class="sxs-lookup"><span data-stu-id="d54a2-183">Configuration should use the options pattern.</span></span> <span data-ttu-id="d54a2-184">同樣地，請避免只存在於允許存取另一個物件的「資料持有者」物件。</span><span class="sxs-lookup"><span data-stu-id="d54a2-184">Similarly, avoid "data holder" objects that only exist to allow access to another object.</span></span> <span data-ttu-id="d54a2-185">最好是透過 DI 要求實際項目。</span><span class="sxs-lookup"><span data-stu-id="d54a2-185">It's better to request the actual item via DI.</span></span>
- <span data-ttu-id="d54a2-186">避免靜態存取服務。</span><span class="sxs-lookup"><span data-stu-id="d54a2-186">Avoid static access to services.</span></span> <span data-ttu-id="d54a2-187">例如，請避免將 [IApplicationBuilder >iapplicationbuilder.applicationservices](xref:Microsoft.AspNetCore.Builder.IApplicationBuilder.ApplicationServices) 為靜態欄位或屬性，以便在其他地方使用。</span><span class="sxs-lookup"><span data-stu-id="d54a2-187">For example, avoid capturing [IApplicationBuilder.ApplicationServices](xref:Microsoft.AspNetCore.Builder.IApplicationBuilder.ApplicationServices) as a static field or property for use elsewhere.</span></span>
- <span data-ttu-id="d54a2-188">讓 DI factory 保持快速且同步。</span><span class="sxs-lookup"><span data-stu-id="d54a2-188">Keep DI factories fast and synchronous.</span></span>
- <span data-ttu-id="d54a2-189">避免使用「服務定位器模式」\*\*。</span><span class="sxs-lookup"><span data-stu-id="d54a2-189">Avoid using the *service locator pattern*.</span></span> <span data-ttu-id="d54a2-190">例如，當您可以改用 DI 時，請勿叫用 <xref:System.IServiceProvider.GetService%2A> 來取得服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="d54a2-190">For example, don't invoke <xref:System.IServiceProvider.GetService%2A> to obtain a service instance when you can use DI instead.</span></span>
- <span data-ttu-id="d54a2-191">另一個要避免的服務定位器變化是插入在執行階段解析相依性的處理站。</span><span class="sxs-lookup"><span data-stu-id="d54a2-191">Another service locator variation to avoid is injecting a factory that resolves dependencies at runtime.</span></span> <span data-ttu-id="d54a2-192">這兩種做法都會混用[控制反轉](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#dependency-inversion)策略。</span><span class="sxs-lookup"><span data-stu-id="d54a2-192">Both of these practices mix [Inversion of Control](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#dependency-inversion) strategies.</span></span>
- <span data-ttu-id="d54a2-193">避免 <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> 在中呼叫 `ConfigureServices` 。</span><span class="sxs-lookup"><span data-stu-id="d54a2-193">Avoid calls to <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> in `ConfigureServices`.</span></span> <span data-ttu-id="d54a2-194">呼叫 `BuildServiceProvider` 通常會在開發人員想要解析中的服務時發生 `ConfigureServices` 。</span><span class="sxs-lookup"><span data-stu-id="d54a2-194">Calling `BuildServiceProvider` typically happens when the developer wants to resolve a service in `ConfigureServices`.</span></span>
- <span data-ttu-id="d54a2-195">容器會捕獲可處置的暫時性服務以供處置。</span><span class="sxs-lookup"><span data-stu-id="d54a2-195">Disposable transient services are captured by the container for disposal.</span></span> <span data-ttu-id="d54a2-196">如果從最上層容器解析，這可能會導致記憶體流失。</span><span class="sxs-lookup"><span data-stu-id="d54a2-196">This can turn into a memory leak if resolved from the top-level container.</span></span>
- <span data-ttu-id="d54a2-197">啟用範圍驗證，以確定應用程式沒有可捕獲範圍服務的 singleton。</span><span class="sxs-lookup"><span data-stu-id="d54a2-197">Enable scope validation to make sure the app doesn't have singletons that capture scoped services.</span></span> <span data-ttu-id="d54a2-198">如需詳細資訊，請參閱[範圍驗證](dependency-injection.md#scope-validation)。</span><span class="sxs-lookup"><span data-stu-id="d54a2-198">For more information, see [Scope validation](dependency-injection.md#scope-validation).</span></span>

<span data-ttu-id="d54a2-199">就像所有的建議集，您可能會遇到需要忽略建議的情況。</span><span class="sxs-lookup"><span data-stu-id="d54a2-199">Like all sets of recommendations, you may encounter situations where ignoring a recommendation is required.</span></span> <span data-ttu-id="d54a2-200">例外狀況很罕見，大多是架構本身內的特殊案例。</span><span class="sxs-lookup"><span data-stu-id="d54a2-200">Exceptions are rare, mostly special cases within the framework itself.</span></span>

<span data-ttu-id="d54a2-201">DI 是靜態/全域物件存取模式的「替代」\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="d54a2-201">DI is an *alternative* to static/global object access patterns.</span></span> <span data-ttu-id="d54a2-202">如果您將 DI 與靜態物件存取混合，則可能無法實現 DI 的優點。</span><span class="sxs-lookup"><span data-stu-id="d54a2-202">You may not be able to realize the benefits of DI if you mix it with static object access.</span></span>

## <a name="see-also"></a><span data-ttu-id="d54a2-203">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d54a2-203">See also</span></span>

- [<span data-ttu-id="d54a2-204">.NET 中的相依性插入</span><span class="sxs-lookup"><span data-stu-id="d54a2-204">Dependency injection in .NET</span></span>](dependency-injection.md)
