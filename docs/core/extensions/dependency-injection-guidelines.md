---
title: 相依性插入指導方針
description: 瞭解各種相依性插入指導方針和 .NET 應用程式開發的最佳做法。
author: IEvangelist
ms.author: dapine
ms.date: 10/29/2020
ms.topic: guide
ms.openlocfilehash: 092fdc70bd5d6bae82c4c1da96db4d5ac08df452
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93063164"
---
# <a name="dependency-injection-guidelines"></a><span data-ttu-id="6927a-103">相依性插入指導方針</span><span class="sxs-lookup"><span data-stu-id="6927a-103">Dependency injection guidelines</span></span>

<span data-ttu-id="6927a-104">本文提供在 .NET 應用程式中執行相依性插入的一般指導方針和最佳作法。</span><span class="sxs-lookup"><span data-stu-id="6927a-104">This article provides general guidelines and best practices for implementing dependency injection in .NET applications.</span></span>

## <a name="design-services-for-dependency-injection"></a><span data-ttu-id="6927a-105">針對相依性插入設計服務</span><span class="sxs-lookup"><span data-stu-id="6927a-105">Design services for dependency injection</span></span>

<span data-ttu-id="6927a-106">針對相依性插入設計服務時：</span><span class="sxs-lookup"><span data-stu-id="6927a-106">When designing services for dependency injection:</span></span>

- <span data-ttu-id="6927a-107">避免具狀態、靜態類別和成員。</span><span class="sxs-lookup"><span data-stu-id="6927a-107">Avoid stateful, static classes and members.</span></span> <span data-ttu-id="6927a-108">請改為使用單一服務來設計應用程式，以避免建立全域狀態。</span><span class="sxs-lookup"><span data-stu-id="6927a-108">Avoid creating global state by designing apps to use singleton services instead.</span></span>
- <span data-ttu-id="6927a-109">避免直接在服務內具現化相依類別。</span><span class="sxs-lookup"><span data-stu-id="6927a-109">Avoid direct instantiation of dependent classes within services.</span></span> <span data-ttu-id="6927a-110">直接具現化會將程式碼耦合到特定實作。</span><span class="sxs-lookup"><span data-stu-id="6927a-110">Direct instantiation couples the code to a particular implementation.</span></span>
- <span data-ttu-id="6927a-111">使服務更小、妥善組成且輕鬆地進行測試。</span><span class="sxs-lookup"><span data-stu-id="6927a-111">Make services small, well-factored, and easily tested.</span></span>

<span data-ttu-id="6927a-112">如果類別有許多插入的相依性，可能是因為類別具有太多責任，而且違反了 [單一責任原則 (SRP) ](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#single-responsibility)。</span><span class="sxs-lookup"><span data-stu-id="6927a-112">If a class has many injected dependencies, it might be a sign that the class has too many responsibilities and violates the [Single Responsibility Principle (SRP)](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#single-responsibility).</span></span> <span data-ttu-id="6927a-113">嘗試將其部分責任移至新的類別，以重構類別。</span><span class="sxs-lookup"><span data-stu-id="6927a-113">Attempt to refactor the class by moving some of its responsibilities into new classes.</span></span>

### <a name="disposal-of-services"></a><span data-ttu-id="6927a-114">處置服務</span><span class="sxs-lookup"><span data-stu-id="6927a-114">Disposal of services</span></span>

<span data-ttu-id="6927a-115">容器會負責清除其所建立的類型，並 <xref:System.IDisposable.Dispose%2A> 在實例上呼叫 <xref:System.IDisposable> 。</span><span class="sxs-lookup"><span data-stu-id="6927a-115">The container is responsible for cleanup of types it creates, and calls <xref:System.IDisposable.Dispose%2A> on <xref:System.IDisposable> instances.</span></span> <span data-ttu-id="6927a-116">從容器解析的服務絕對不能由開發人員處置。</span><span class="sxs-lookup"><span data-stu-id="6927a-116">Services resolved from the container should never be disposed by the developer.</span></span> <span data-ttu-id="6927a-117">如果類型或 factory 註冊為 singleton，則容器會自動處置 singleton。</span><span class="sxs-lookup"><span data-stu-id="6927a-117">If a type or factory is registered as a singleton, the container disposes the singleton automatically.</span></span>

<span data-ttu-id="6927a-118">在下列範例中，服務是由服務容器建立並自動處置：</span><span class="sxs-lookup"><span data-stu-id="6927a-118">In the following example, the services are created by the service container and disposed automatically:</span></span>

:::code language="csharp" source="snippets/configuration/console-di-disposable/TransientDisposable.cs":::

<span data-ttu-id="6927a-119">先前的可處置是為了具有暫時性存留期。</span><span class="sxs-lookup"><span data-stu-id="6927a-119">The preceding disposable is intended to have a transient lifetime.</span></span>

:::code language="csharp" source="snippets/configuration/console-di-disposable/ScopedDisposable.cs":::

<span data-ttu-id="6927a-120">上述可處置的目的是要有限定範圍的存留期。</span><span class="sxs-lookup"><span data-stu-id="6927a-120">The preceding disposable is intended to have a scoped lifetime.</span></span>

:::code language="csharp" source="snippets/configuration/console-di-disposable/SingletonDisposable.cs":::

<span data-ttu-id="6927a-121">先前的可處置是為了具有單一存留期。</span><span class="sxs-lookup"><span data-stu-id="6927a-121">The preceding disposable is intended to have a singleton lifetime.</span></span>

:::code language="csharp" source="snippets/configuration/console-di-disposable/Program.cs" range="1-21,41-60" highlight="":::

<span data-ttu-id="6927a-122">在執行之後，debug 主控台會顯示下列範例輸出：</span><span class="sxs-lookup"><span data-stu-id="6927a-122">The debug console shows the following sample output after running:</span></span>

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

### <a name="services-not-created-by-the-service-container"></a><span data-ttu-id="6927a-123">服務容器未建立的服務</span><span class="sxs-lookup"><span data-stu-id="6927a-123">Services not created by the service container</span></span>

<span data-ttu-id="6927a-124">請考慮下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="6927a-124">Consider the following code:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddSingleton(new ExampleService());

    // ...
}
```

<span data-ttu-id="6927a-125">在上述程式碼中：</span><span class="sxs-lookup"><span data-stu-id="6927a-125">In the preceding code:</span></span>

- <span data-ttu-id="6927a-126">此 `ExampleService` 實例不 **not** 是由服務容器所建立。</span><span class="sxs-lookup"><span data-stu-id="6927a-126">The `ExampleService` instance is **not** created by the service container.</span></span>
- <span data-ttu-id="6927a-127">架構 **不會自動處置服務** 。</span><span class="sxs-lookup"><span data-stu-id="6927a-127">The framework does **not** dispose of the services automatically.</span></span>
- <span data-ttu-id="6927a-128">開發人員負責處置服務。</span><span class="sxs-lookup"><span data-stu-id="6927a-128">The developer is responsible for disposing the services.</span></span>

### <a name="idisposable-guidance-for-transient-and-shared-instances"></a><span data-ttu-id="6927a-129">暫時性和共用實例的 IDisposable 指引</span><span class="sxs-lookup"><span data-stu-id="6927a-129">IDisposable guidance for Transient and shared instances</span></span>

#### <a name="transient-limited-lifetime"></a><span data-ttu-id="6927a-130">暫時性、有限存留期</span><span class="sxs-lookup"><span data-stu-id="6927a-130">Transient, limited lifetime</span></span>

<span data-ttu-id="6927a-131">**案例**</span><span class="sxs-lookup"><span data-stu-id="6927a-131">**Scenario**</span></span>

<span data-ttu-id="6927a-132">應用程式需要在 <xref:System.IDisposable> 下列任一案例中具有暫時性存留期的實例：</span><span class="sxs-lookup"><span data-stu-id="6927a-132">The app requires an <xref:System.IDisposable> instance with a transient lifetime for either of the following scenarios:</span></span>

- <span data-ttu-id="6927a-133"> (根容器) 的根範圍中解析實例。</span><span class="sxs-lookup"><span data-stu-id="6927a-133">The instance is resolved in the root scope (root container).</span></span>
- <span data-ttu-id="6927a-134">實例應該在範圍結束之前處置。</span><span class="sxs-lookup"><span data-stu-id="6927a-134">The instance should be disposed before the scope ends.</span></span>

<span data-ttu-id="6927a-135">**方案**</span><span class="sxs-lookup"><span data-stu-id="6927a-135">**Solution**</span></span>

<span data-ttu-id="6927a-136">使用 factory 模式，在父範圍之外建立實例。</span><span class="sxs-lookup"><span data-stu-id="6927a-136">Use the factory pattern to create an instance outside of the parent scope.</span></span> <span data-ttu-id="6927a-137">在這種情況下，應用程式通常會有 `Create` 方法可直接呼叫最終型別的函式。</span><span class="sxs-lookup"><span data-stu-id="6927a-137">In this situation, the app would generally have a `Create` method that calls the final type's constructor directly.</span></span> <span data-ttu-id="6927a-138">如果最終類型有其他相依性，factory 可以：</span><span class="sxs-lookup"><span data-stu-id="6927a-138">If the final type has other dependencies, the factory can:</span></span>

- <span data-ttu-id="6927a-139"><xref:System.IServiceProvider>在其函式中接收。</span><span class="sxs-lookup"><span data-stu-id="6927a-139">Receive an <xref:System.IServiceProvider> in its constructor.</span></span>
- <span data-ttu-id="6927a-140">使用 <xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities.CreateInstance%2A?displayProperty=nameWithType> 可在容器外部具現化實例，同時使用容器作為其相依性。</span><span class="sxs-lookup"><span data-stu-id="6927a-140">Use <xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities.CreateInstance%2A?displayProperty=nameWithType> to instantiate the instance outside of the container, while using the container for its dependencies.</span></span>

#### <a name="shared-instance-limited-lifetime"></a><span data-ttu-id="6927a-141">共用實例，有限存留期</span><span class="sxs-lookup"><span data-stu-id="6927a-141">Shared instance, limited lifetime</span></span>

<span data-ttu-id="6927a-142">**案例**</span><span class="sxs-lookup"><span data-stu-id="6927a-142">**Scenario**</span></span>

<span data-ttu-id="6927a-143">應用程式需要 <xref:System.IDisposable> 跨多個服務的共用實例，但 <xref:System.IDisposable> 實例的存留期應受限。</span><span class="sxs-lookup"><span data-stu-id="6927a-143">The app requires a shared <xref:System.IDisposable> instance across multiple services, but the <xref:System.IDisposable> instance should have a limited lifetime.</span></span>

<span data-ttu-id="6927a-144">**方案**</span><span class="sxs-lookup"><span data-stu-id="6927a-144">**Solution**</span></span>

<span data-ttu-id="6927a-145">註冊具有範圍存留期的實例。</span><span class="sxs-lookup"><span data-stu-id="6927a-145">Register the instance with a scoped lifetime.</span></span> <span data-ttu-id="6927a-146">使用 <xref:Microsoft.Extensions.DependencyInjection.IServiceScopeFactory.CreateScope%2A?displayProperty=nameWithType> 建立新的 <xref:Microsoft.Extensions.DependencyInjection.IServiceScope> 。</span><span class="sxs-lookup"><span data-stu-id="6927a-146">Use <xref:Microsoft.Extensions.DependencyInjection.IServiceScopeFactory.CreateScope%2A?displayProperty=nameWithType> to create a new <xref:Microsoft.Extensions.DependencyInjection.IServiceScope>.</span></span> <span data-ttu-id="6927a-147">使用範圍 <xref:System.IServiceProvider> 來取得所需的服務。</span><span class="sxs-lookup"><span data-stu-id="6927a-147">Use the scope's <xref:System.IServiceProvider> to get required services.</span></span> <span data-ttu-id="6927a-148">不再需要時處置範圍。</span><span class="sxs-lookup"><span data-stu-id="6927a-148">Dispose the scope when it's no longer needed.</span></span>

#### <a name="general-idisposable-guidelines"></a><span data-ttu-id="6927a-149">一般 `IDisposable` 指導方針</span><span class="sxs-lookup"><span data-stu-id="6927a-149">General `IDisposable` guidelines</span></span>

- <span data-ttu-id="6927a-150">請勿 <xref:System.IDisposable> 在暫時性的存留期內註冊實例。</span><span class="sxs-lookup"><span data-stu-id="6927a-150">Don't register <xref:System.IDisposable> instances with a transient lifetime.</span></span> <span data-ttu-id="6927a-151">請改用 factory 模式。</span><span class="sxs-lookup"><span data-stu-id="6927a-151">Use the factory pattern instead.</span></span>
- <span data-ttu-id="6927a-152">請勿 <xref:System.IDisposable> 在根範圍中解析具有暫時性或範圍存留期的實例。</span><span class="sxs-lookup"><span data-stu-id="6927a-152">Don't resolve <xref:System.IDisposable> instances with a transient or scoped lifetime in the root scope.</span></span> <span data-ttu-id="6927a-153">唯一的例外是應用程式建立/重新建立和處置 <xref:System.IServiceProvider> ，但這不是理想的模式。</span><span class="sxs-lookup"><span data-stu-id="6927a-153">The only exception to this is if the app creates/recreates and disposes <xref:System.IServiceProvider>, but this isn't an ideal pattern.</span></span>
- <span data-ttu-id="6927a-154">透過 DI 接收相依性 <xref:System.IDisposable> 不需要接收者 <xref:System.IDisposable> 自行執行。</span><span class="sxs-lookup"><span data-stu-id="6927a-154">Receiving an <xref:System.IDisposable> dependency via DI doesn't require that the receiver implement <xref:System.IDisposable> itself.</span></span> <span data-ttu-id="6927a-155">相依性的接收者不 <xref:System.IDisposable> 應呼叫 <xref:System.IDisposable.Dispose%2A> 該相依性。</span><span class="sxs-lookup"><span data-stu-id="6927a-155">The receiver of the <xref:System.IDisposable> dependency shouldn't call <xref:System.IDisposable.Dispose%2A> on that dependency.</span></span>
- <span data-ttu-id="6927a-156">使用範圍來控制服務的存留期。</span><span class="sxs-lookup"><span data-stu-id="6927a-156">Use scopes to control the lifetimes of services.</span></span> <span data-ttu-id="6927a-157">範圍不是階層式，而且範圍之間沒有特殊連接。</span><span class="sxs-lookup"><span data-stu-id="6927a-157">Scopes aren't hierarchical, and there's no special connection among scopes.</span></span>

<span data-ttu-id="6927a-158">如需資源清除的詳細資訊，請參閱 [執行 `Dispose` 方法](../../standard/garbage-collection/implementing-dispose.md)或 [執行 `DisposeAsync` 方法](../../standard/garbage-collection/implementing-disposeasync.md)。</span><span class="sxs-lookup"><span data-stu-id="6927a-158">For more information on resource cleanup, see [Implement a `Dispose` method](../../standard/garbage-collection/implementing-dispose.md), or [Implement a `DisposeAsync` method](../../standard/garbage-collection/implementing-disposeasync.md).</span></span> <span data-ttu-id="6927a-159">此外，請考慮容器案例所捕捉的可 [處置暫時性服務](#disposable-transient-services-captured-by-container) ，因為它與資源清理相關。</span><span class="sxs-lookup"><span data-stu-id="6927a-159">Additionally, consider the [Disposable transient services captured by container](#disposable-transient-services-captured-by-container) scenario as it relates to resource cleanup.</span></span>

## <a name="default-service-container-replacement"></a><span data-ttu-id="6927a-160">預設服務容器取代</span><span class="sxs-lookup"><span data-stu-id="6927a-160">Default service container replacement</span></span>

<span data-ttu-id="6927a-161">內建的服務容器是設計來滿足架構和大部分消費者應用程式的需求。</span><span class="sxs-lookup"><span data-stu-id="6927a-161">The built-in service container is designed to serve the needs of the framework and most consumer apps.</span></span> <span data-ttu-id="6927a-162">除非您需要不支援的特定功能，否則建議使用內建容器，例如：</span><span class="sxs-lookup"><span data-stu-id="6927a-162">We recommend using the built-in container unless you need a specific feature that it doesn't support, such as:</span></span>

- <span data-ttu-id="6927a-163">屬性插入</span><span class="sxs-lookup"><span data-stu-id="6927a-163">Property injection</span></span>
- <span data-ttu-id="6927a-164">根據名稱插入</span><span class="sxs-lookup"><span data-stu-id="6927a-164">Injection based on name</span></span>
- <span data-ttu-id="6927a-165">子容器</span><span class="sxs-lookup"><span data-stu-id="6927a-165">Child containers</span></span>
- <span data-ttu-id="6927a-166">自訂生命週期管理</span><span class="sxs-lookup"><span data-stu-id="6927a-166">Custom lifetime management</span></span>
- <span data-ttu-id="6927a-167">`Func<T>` 支援延遲初始設定</span><span class="sxs-lookup"><span data-stu-id="6927a-167">`Func<T>` support for lazy initialization</span></span>
- <span data-ttu-id="6927a-168">以慣例為基礎的註冊</span><span class="sxs-lookup"><span data-stu-id="6927a-168">Convention-based registration</span></span>

<span data-ttu-id="6927a-169">下列協力廠商容器可搭配 ASP.NET Core apps 使用：</span><span class="sxs-lookup"><span data-stu-id="6927a-169">The following third-party containers can be used with ASP.NET Core apps:</span></span>

- [<span data-ttu-id="6927a-170">Autofac</span><span class="sxs-lookup"><span data-stu-id="6927a-170">Autofac</span></span>](https://autofac.readthedocs.io/en/latest/integration/aspnetcore.html)
- [<span data-ttu-id="6927a-171">DryIoc</span><span class="sxs-lookup"><span data-stu-id="6927a-171">DryIoc</span></span>](https://www.nuget.org/packages/DryIoc.Microsoft.DependencyInjection)
- [<span data-ttu-id="6927a-172">Grace</span><span class="sxs-lookup"><span data-stu-id="6927a-172">Grace</span></span>](https://www.nuget.org/packages/Grace.DependencyInjection.Extensions)
- [<span data-ttu-id="6927a-173">LightInject</span><span class="sxs-lookup"><span data-stu-id="6927a-173">LightInject</span></span>](https://github.com/seesharper/LightInject.Microsoft.DependencyInjection)
- [<span data-ttu-id="6927a-174">拉馬爾</span><span class="sxs-lookup"><span data-stu-id="6927a-174">Lamar</span></span>](https://jasperfx.github.io/lamar/)
- [<span data-ttu-id="6927a-175">Stashbox</span><span class="sxs-lookup"><span data-stu-id="6927a-175">Stashbox</span></span>](https://github.com/z4kn4fein/stashbox-extensions-dependencyinjection)
- [<span data-ttu-id="6927a-176">Unity</span><span class="sxs-lookup"><span data-stu-id="6927a-176">Unity</span></span>](https://www.nuget.org/packages/Unity.Microsoft.DependencyInjection)

## <a name="thread-safety"></a><span data-ttu-id="6927a-177">執行緒安全</span><span class="sxs-lookup"><span data-stu-id="6927a-177">Thread safety</span></span>

<span data-ttu-id="6927a-178">建立具備執行緒安全性的 singleton 服務。</span><span class="sxs-lookup"><span data-stu-id="6927a-178">Create thread-safe singleton services.</span></span> <span data-ttu-id="6927a-179">如果單一服務相依于暫時性服務，暫時性服務可能也需要執行緒安全性，取決於 singleton 使用它的方式。</span><span class="sxs-lookup"><span data-stu-id="6927a-179">If a singleton service has a dependency on a transient service, the transient service may also require thread safety depending on how it's used by the singleton.</span></span>

<span data-ttu-id="6927a-180">單一服務的 factory 方法（例如 >addsingleton 的第二個自 [變數 \<TService> (IServiceCollection、Func \<IServiceProvider,TService>) ](xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A)）不需要是安全線程。</span><span class="sxs-lookup"><span data-stu-id="6927a-180">The factory method of single service, such as the second argument to [AddSingleton\<TService>(IServiceCollection, Func\<IServiceProvider,TService>)](xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A), doesn't need to be thread-safe.</span></span> <span data-ttu-id="6927a-181">如同型別 () 的函式 `static` ，它保證只能由單一線程呼叫一次。</span><span class="sxs-lookup"><span data-stu-id="6927a-181">Like a type (`static`) constructor, it's guaranteed to be called only once by a single thread.</span></span>

## <a name="recommendations"></a><span data-ttu-id="6927a-182">建議</span><span class="sxs-lookup"><span data-stu-id="6927a-182">Recommendations</span></span>

- <span data-ttu-id="6927a-183">`async/await` 並 `Task` 不支援以服務為基礎的服務解析。</span><span class="sxs-lookup"><span data-stu-id="6927a-183">`async/await` and `Task` based service resolution isn't supported.</span></span> <span data-ttu-id="6927a-184">因為 c # 不支援非同步函式，所以請在以同步方式解析服務後使用非同步方法。</span><span class="sxs-lookup"><span data-stu-id="6927a-184">Because C# doesn't support asynchronous constructors, use asynchronous methods after synchronously resolving the service.</span></span>
- <span data-ttu-id="6927a-185">避免直接在服務容器中儲存資料與設定。</span><span class="sxs-lookup"><span data-stu-id="6927a-185">Avoid storing data and configuration directly in the service container.</span></span> <span data-ttu-id="6927a-186">例如，使用者的購物車通常不應該新增至服務容器。</span><span class="sxs-lookup"><span data-stu-id="6927a-186">For example, a user's shopping cart shouldn't typically be added to the service container.</span></span> <span data-ttu-id="6927a-187">組態應該使用選項模式。</span><span class="sxs-lookup"><span data-stu-id="6927a-187">Configuration should use the options pattern.</span></span> <span data-ttu-id="6927a-188">同樣地，請避免只存在於允許存取另一個物件的「資料持有者」物件。</span><span class="sxs-lookup"><span data-stu-id="6927a-188">Similarly, avoid "data holder" objects that only exist to allow access to another object.</span></span> <span data-ttu-id="6927a-189">最好是透過 DI 要求實際項目。</span><span class="sxs-lookup"><span data-stu-id="6927a-189">It's better to request the actual item via DI.</span></span>
- <span data-ttu-id="6927a-190">避免靜態存取服務。</span><span class="sxs-lookup"><span data-stu-id="6927a-190">Avoid static access to services.</span></span> <span data-ttu-id="6927a-191">例如，請避免將 [IApplicationBuilder >iapplicationbuilder.applicationservices](xref:Microsoft.AspNetCore.Builder.IApplicationBuilder.ApplicationServices) 為靜態欄位或屬性，以便在其他地方使用。</span><span class="sxs-lookup"><span data-stu-id="6927a-191">For example, avoid capturing [IApplicationBuilder.ApplicationServices](xref:Microsoft.AspNetCore.Builder.IApplicationBuilder.ApplicationServices) as a static field or property for use elsewhere.</span></span>
- <span data-ttu-id="6927a-192">讓 [DI](#async-di-factories-can-cause-deadlocks) factory 保持快速且同步。</span><span class="sxs-lookup"><span data-stu-id="6927a-192">Keep [DI factories](#async-di-factories-can-cause-deadlocks) fast and synchronous.</span></span>
- <span data-ttu-id="6927a-193">請避免使用 [*服務定位器模式*](#scoped-service-as-singleton)。</span><span class="sxs-lookup"><span data-stu-id="6927a-193">Avoid using the [*service locator pattern*](#scoped-service-as-singleton).</span></span> <span data-ttu-id="6927a-194">例如，當您可以改用 DI 時，請勿叫用 <xref:System.IServiceProvider.GetService%2A> 來取得服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="6927a-194">For example, don't invoke <xref:System.IServiceProvider.GetService%2A> to obtain a service instance when you can use DI instead.</span></span>
- <span data-ttu-id="6927a-195">另一個要避免的服務定位器變化是插入在執行階段解析相依性的處理站。</span><span class="sxs-lookup"><span data-stu-id="6927a-195">Another service locator variation to avoid is injecting a factory that resolves dependencies at runtime.</span></span> <span data-ttu-id="6927a-196">這兩種做法都會混用[控制反轉](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#dependency-inversion)策略。</span><span class="sxs-lookup"><span data-stu-id="6927a-196">Both of these practices mix [Inversion of Control](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#dependency-inversion) strategies.</span></span>
- <span data-ttu-id="6927a-197">避免 <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> 在中呼叫 `ConfigureServices` 。</span><span class="sxs-lookup"><span data-stu-id="6927a-197">Avoid calls to <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> in `ConfigureServices`.</span></span> <span data-ttu-id="6927a-198">呼叫 `BuildServiceProvider` 通常會在開發人員想要解析中的服務時發生 `ConfigureServices` 。</span><span class="sxs-lookup"><span data-stu-id="6927a-198">Calling `BuildServiceProvider` typically happens when the developer wants to resolve a service in `ConfigureServices`.</span></span>
- <span data-ttu-id="6927a-199">容器[會捕獲可處置的暫時性服務](#disposable-transient-services-captured-by-container)以供處置。</span><span class="sxs-lookup"><span data-stu-id="6927a-199">[Disposable transient services are captured](#disposable-transient-services-captured-by-container) by the container for disposal.</span></span> <span data-ttu-id="6927a-200">如果從最上層容器解析，這可能會導致記憶體流失。</span><span class="sxs-lookup"><span data-stu-id="6927a-200">This can turn into a memory leak if resolved from the top-level container.</span></span>
- <span data-ttu-id="6927a-201">啟用範圍驗證，以確定應用程式沒有可捕獲範圍服務的 singleton。</span><span class="sxs-lookup"><span data-stu-id="6927a-201">Enable scope validation to make sure the app doesn't have singletons that capture scoped services.</span></span> <span data-ttu-id="6927a-202">如需詳細資訊，請參閱[範圍驗證](dependency-injection.md#scope-validation)。</span><span class="sxs-lookup"><span data-stu-id="6927a-202">For more information, see [Scope validation](dependency-injection.md#scope-validation).</span></span>

<span data-ttu-id="6927a-203">就像所有的建議集，您可能會遇到需要忽略建議的情況。</span><span class="sxs-lookup"><span data-stu-id="6927a-203">Like all sets of recommendations, you may encounter situations where ignoring a recommendation is required.</span></span> <span data-ttu-id="6927a-204">例外狀況很罕見，大多是架構本身內的特殊案例。</span><span class="sxs-lookup"><span data-stu-id="6927a-204">Exceptions are rare, mostly special cases within the framework itself.</span></span>

<span data-ttu-id="6927a-205">DI 是靜態/全域物件存取模式的「替代」  選項。</span><span class="sxs-lookup"><span data-stu-id="6927a-205">DI is an *alternative* to static/global object access patterns.</span></span> <span data-ttu-id="6927a-206">如果您將 DI 與靜態物件存取混合，則可能無法實現 DI 的優點。</span><span class="sxs-lookup"><span data-stu-id="6927a-206">You may not be able to realize the benefits of DI if you mix it with static object access.</span></span>

## <a name="example-anti-patterns"></a><span data-ttu-id="6927a-207">範例反模式</span><span class="sxs-lookup"><span data-stu-id="6927a-207">Example anti-patterns</span></span>

<span data-ttu-id="6927a-208">除了本文中的指導方針之外，還有數個 ***應該** 避免* 的反模式。</span><span class="sxs-lookup"><span data-stu-id="6927a-208">In addition to the guidelines in this article, there are several anti-patterns *you **should** avoid* .</span></span> <span data-ttu-id="6927a-209">其中有些反模式是從開發執行時間本身學習而來的。</span><span class="sxs-lookup"><span data-stu-id="6927a-209">Some of these anti-patterns are learnings from developing the runtimes themselves.</span></span>

> [!WARNING]
> <span data-ttu-id="6927a-210">這些是範例的反模式， *不會複製程式* 代碼、 *不使用這些* 模式，並以所有成本來避免這些模式。</span><span class="sxs-lookup"><span data-stu-id="6927a-210">These are example anti-patterns, *do not* copy the code, *do not* use these patterns, and avoid these patterns at all costs.</span></span>

### <a name="disposable-transient-services-captured-by-container"></a><span data-ttu-id="6927a-211">容器所捕獲的可處置暫時性服務</span><span class="sxs-lookup"><span data-stu-id="6927a-211">Disposable transient services captured by container</span></span>

<span data-ttu-id="6927a-212">當您註冊執行的 *暫時性* 服務時 <xref:System.IDisposable> ，DI 容器預設會保留這些參考，而不會保存到 <xref:System.IDisposable.Dispose> 應用程式停止之前。</span><span class="sxs-lookup"><span data-stu-id="6927a-212">When you register *Transient* services that implement <xref:System.IDisposable>, by default the DI container will hold onto these references, and not <xref:System.IDisposable.Dispose> of them until the application stops.</span></span> <span data-ttu-id="6927a-213">如果從層級容器解析，這可能會導致記憶體流失。</span><span class="sxs-lookup"><span data-stu-id="6927a-213">This can turn into a memory leak if resolved from the level container.</span></span>

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="18-30":::

<span data-ttu-id="6927a-214">在上述的反模式中，1000 `ExampleDisposable` 物件具現化和根目錄。</span><span class="sxs-lookup"><span data-stu-id="6927a-214">In the preceding anti-pattern, 1,000 `ExampleDisposable` objects are instantiated and rooted.</span></span> <span data-ttu-id="6927a-215">在實例處置之前，它們將不會被處置 `serviceProvider` 。</span><span class="sxs-lookup"><span data-stu-id="6927a-215">They will not be disposed of until the `serviceProvider` instance is disposed.</span></span>

<span data-ttu-id="6927a-216">如需有關偵錯工具記憶體流失的詳細資訊，請參閱 [在 .net 中偵測記憶體](../diagnostics/debug-memory-leak.md)流失。</span><span class="sxs-lookup"><span data-stu-id="6927a-216">For more information on debugging memory leaks, see [Debug a memory leak in .NET](../diagnostics/debug-memory-leak.md).</span></span>

### <a name="async-di-factories-can-cause-deadlocks"></a><span data-ttu-id="6927a-217">非同步 DI 處理站可能會造成鎖死</span><span class="sxs-lookup"><span data-stu-id="6927a-217">Async DI factories can cause deadlocks</span></span>

<span data-ttu-id="6927a-218">「DI factory」一詞是指呼叫時存在的多載方法 `Add{LIFETIME}` 。</span><span class="sxs-lookup"><span data-stu-id="6927a-218">The term "DI factories" refers to the overload methods that exist when calling `Add{LIFETIME}`.</span></span> <span data-ttu-id="6927a-219">有多載接受 `Func<IServiceProvider, T>` where `T` 是註冊的服務，並具名引數 `implementationFactory` 。</span><span class="sxs-lookup"><span data-stu-id="6927a-219">There are overloads accepting a `Func<IServiceProvider, T>` where `T` is the service being registered, and the parameter is named `implementationFactory`.</span></span> <span data-ttu-id="6927a-220">`implementationFactory`可以做為 lambda 運算式、區域函數或方法來提供。</span><span class="sxs-lookup"><span data-stu-id="6927a-220">The `implementationFactory` can be provided as a lambda expression, local function, or method.</span></span> <span data-ttu-id="6927a-221">如果 factory 是非同步，而且您使用 <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> ，這會造成鎖死。</span><span class="sxs-lookup"><span data-stu-id="6927a-221">If the factory is asynchronous, and you use <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType>, this will cause a deadlock.</span></span>

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="32-45" highlight="4-8":::

<span data-ttu-id="6927a-222">在上述程式碼中， `implementationFactory` 會指定 lambda 運算式，其中主體會在傳回的 <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> 方法上呼叫 `Task<Bar>` 。</span><span class="sxs-lookup"><span data-stu-id="6927a-222">In the preceding code, the `implementationFactory` is given a lambda expression where the body calls <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> on a `Task<Bar>` returning method.</span></span> <span data-ttu-id="6927a-223">這 ***會造成鎖死*** 。</span><span class="sxs-lookup"><span data-stu-id="6927a-223">This ***causes a deadlock*** .</span></span> <span data-ttu-id="6927a-224">`GetBarAsync`方法只會使用來模擬非同步作業作業 <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> ，然後再呼叫 <xref:Microsoft.Extensions.DependencyInjection.ServiceProviderServiceExtensions.GetRequiredService%60%601(System.IServiceProvider)> 。</span><span class="sxs-lookup"><span data-stu-id="6927a-224">The `GetBarAsync` method simply emulates an asynchronous work operation with <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType>, and then calls <xref:Microsoft.Extensions.DependencyInjection.ServiceProviderServiceExtensions.GetRequiredService%60%601(System.IServiceProvider)>.</span></span>

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="47-53":::

<span data-ttu-id="6927a-225">如需非同步指引的詳細資訊，請參閱 [非同步程式設計：重要資訊和建議](../../csharp/async.md#important-info-and-advice)。</span><span class="sxs-lookup"><span data-stu-id="6927a-225">For more information on asynchronous guidance, see [Asynchronous programming: Important info and advice](../../csharp/async.md#important-info-and-advice).</span></span> <span data-ttu-id="6927a-226">如需偵錯工具鎖死的詳細資訊，請參閱 [在 .net 中偵測鎖死](../diagnostics/debug-deadlock.md)。</span><span class="sxs-lookup"><span data-stu-id="6927a-226">For more information debugging deadlocks, see [Debug a deadlock in .NET](../diagnostics/debug-deadlock.md).</span></span>

<span data-ttu-id="6927a-227">當您執行此反模式且發生鎖死時，您可以從 Visual Studio 的 [平行堆疊] 視窗查看兩個等候的執行緒。</span><span class="sxs-lookup"><span data-stu-id="6927a-227">When you're running this anti-pattern and the deadlock occurs, you can view the two threads waiting from Visual Studio's Parallel Stacks window.</span></span> <span data-ttu-id="6927a-228">如需詳細資訊，請參閱 [[平行堆疊] 視窗中的 [視圖執行緒和工作]](/visualstudio/debugger/using-the-parallel-stacks-window)。</span><span class="sxs-lookup"><span data-stu-id="6927a-228">For more information, see [View threads and tasks in the Parallel Stacks window](/visualstudio/debugger/using-the-parallel-stacks-window).</span></span>

### <a name="captive-dependency"></a><span data-ttu-id="6927a-229">相關性</span><span class="sxs-lookup"><span data-stu-id="6927a-229">Captive dependency</span></span>

<span data-ttu-id="6927a-230">「驗證相依性」一詞是由[Mark Seeman](https://blog.ploeh.dk/about)所創造，並指的是服務存留期的設定不正確，[其中長期的](https://blog.ploeh.dk/2014/06/02/captive-dependency)服務會保留較短的服務。</span><span class="sxs-lookup"><span data-stu-id="6927a-230">The term ["captive dependency"](https://blog.ploeh.dk/2014/06/02/captive-dependency) was coined by [Mark Seeman](https://blog.ploeh.dk/about), and refers to the misconfiguration of service lifetimes, where a longer-lived service holds a shorter-lived service captive.</span></span>

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="55-65":::

<span data-ttu-id="6927a-231">在上述程式碼中， `Foo` 是以 singleton 的形式註冊，而且 `Bar` 範圍限定在表面上看起來是有效的。</span><span class="sxs-lookup"><span data-stu-id="6927a-231">In the preceding code, `Foo` is registered as a singleton and `Bar` is scoped - which on the surface seems valid.</span></span> <span data-ttu-id="6927a-232">但是，請考慮執行的 `Foo` 。</span><span class="sxs-lookup"><span data-stu-id="6927a-232">However, consider the implementation of `Foo`.</span></span>

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Foo.cs" highlight="5":::

<span data-ttu-id="6927a-233">`Foo`物件需要 `Bar` 物件，因為 `Foo` 是 singleton，且 `Bar` 已設定範圍-這是設定錯誤的。</span><span class="sxs-lookup"><span data-stu-id="6927a-233">The `Foo` object requires a `Bar` object, and since `Foo` is a singleton, and `Bar` is scoped - this is a misconfiguration.</span></span> <span data-ttu-id="6927a-234">同樣地， `Foo` 它只會具現化一次，而且它會保留在 `Bar` 其存留期內（長度超過預期的範圍存留期） `Bar` 。</span><span class="sxs-lookup"><span data-stu-id="6927a-234">As is, `Foo` would only be instantiated once, and it would hold onto `Bar` for its lifetime, which is longer than the intended scoped lifetime of `Bar`.</span></span> <span data-ttu-id="6927a-235">您應該考慮透過傳遞 `validateScopes: true` 給來驗證範圍 <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Boolean)> 。</span><span class="sxs-lookup"><span data-stu-id="6927a-235">You should consider validating scopes, by passing `validateScopes: true` to the <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Boolean)>.</span></span> <span data-ttu-id="6927a-236">當您驗證範圍時，您會收到一個 <xref:System.InvalidOperationException> 訊息，類似于「無法從單一 ' Foo ' 取用範圍服務 ' Bar '」。</span><span class="sxs-lookup"><span data-stu-id="6927a-236">When you validate the scopes, you'd get an <xref:System.InvalidOperationException> with a message similar to "Cannot consume scoped service 'Bar' from singleton 'Foo'.".</span></span>

<span data-ttu-id="6927a-237">如需詳細資訊，請參閱[範圍驗證](dependency-injection.md#scope-validation)。</span><span class="sxs-lookup"><span data-stu-id="6927a-237">For more information, see [Scope validation](dependency-injection.md#scope-validation).</span></span>

### <a name="scoped-service-as-singleton"></a><span data-ttu-id="6927a-238">範圍服務為 singleton</span><span class="sxs-lookup"><span data-stu-id="6927a-238">Scoped service as singleton</span></span>

<span data-ttu-id="6927a-239">使用已設定範圍的服務時，如果您不是在現有的範圍內建立範圍，服務會變成 singleton。</span><span class="sxs-lookup"><span data-stu-id="6927a-239">When using scoped services, if you're not creating a scope or within an existing scope - the service becomes a singleton.</span></span>

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="68-82" highlight="13-14":::

<span data-ttu-id="6927a-240">在上述程式碼中， `Bar` 是在中的 <xref:Microsoft.Extensions.DependencyInjection.IServiceScope> ，它是正確的。</span><span class="sxs-lookup"><span data-stu-id="6927a-240">In the preceding code, `Bar` is retrieved within an <xref:Microsoft.Extensions.DependencyInjection.IServiceScope>, which is correct.</span></span> <span data-ttu-id="6927a-241">反模式是在範圍外的抓取 `Bar` ，並命名變數 `avoid` 以顯示不正確的範例抓取。</span><span class="sxs-lookup"><span data-stu-id="6927a-241">The anti-pattern is the retrieval of `Bar` outside of the scope, and the variable is named `avoid` to show which example retrieval is incorrect.</span></span>

## <a name="see-also"></a><span data-ttu-id="6927a-242">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6927a-242">See also</span></span>

- [<span data-ttu-id="6927a-243">.NET 中的相依性插入</span><span class="sxs-lookup"><span data-stu-id="6927a-243">Dependency injection in .NET</span></span>](dependency-injection.md)
- [<span data-ttu-id="6927a-244">教學課程：在 .NET 中使用相依性插入</span><span class="sxs-lookup"><span data-stu-id="6927a-244">Tutorial: Use dependency injection in .NET</span></span>](dependency-injection-usage.md)
