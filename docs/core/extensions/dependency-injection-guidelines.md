---
title: 相依性插入指導方針
description: 瞭解各種相依性插入指導方針和 .NET 應用程式開發的最佳做法。
author: IEvangelist
ms.author: dapine
ms.date: 10/29/2020
ms.topic: guide
ms.openlocfilehash: 6b12d0d607dc0aed8f281943cecf3afa69b0575a
ms.sourcegitcommit: 88fbb019b84c2d044d11fb4f6004aec07f2b25b1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97899437"
---
# <a name="dependency-injection-guidelines"></a>相依性插入指導方針

本文提供在 .NET 應用程式中執行相依性插入的一般指導方針和最佳作法。

## <a name="design-services-for-dependency-injection"></a>針對相依性插入設計服務

針對相依性插入設計服務時：

- 避免具狀態、靜態類別和成員。 請改為使用單一服務來設計應用程式，以避免建立全域狀態。
- 避免直接在服務內具現化相依類別。 直接具現化會將程式碼耦合到特定實作。
- 使服務更小、妥善組成且輕鬆地進行測試。

如果類別有許多插入的相依性，可能是因為類別具有太多責任，而且違反了 [單一責任原則 (SRP) ](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#single-responsibility)。 嘗試將其部分責任移至新的類別，以重構類別。

### <a name="disposal-of-services"></a>處置服務

容器會負責清除其所建立的類型，並 <xref:System.IDisposable.Dispose%2A> 在實例上呼叫 <xref:System.IDisposable> 。 從容器解析的服務絕對不能由開發人員處置。 如果類型或 factory 註冊為 singleton，則容器會自動處置 singleton。

在下列範例中，服務是由服務容器建立並自動處置：

:::code language="csharp" source="snippets/configuration/console-di-disposable/TransientDisposable.cs":::

先前的可處置是為了具有暫時性存留期。

:::code language="csharp" source="snippets/configuration/console-di-disposable/ScopedDisposable.cs":::

上述可處置的目的是要有限定範圍的存留期。

:::code language="csharp" source="snippets/configuration/console-di-disposable/SingletonDisposable.cs":::

先前的可處置是為了具有單一存留期。

:::code language="csharp" source="snippets/configuration/console-di-disposable/Program.cs" range="1-21,41-60" highlight="":::

在執行之後，debug 主控台會顯示下列範例輸出：

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

### <a name="services-not-created-by-the-service-container"></a>服務容器未建立的服務

請考慮下列程式碼：

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddSingleton(new ExampleService());

    // ...
}
```

在上述程式碼中：

- 此 `ExampleService` 實例不是由服務容器所建立。
- 架構 **不會自動處置服務** 。
- 開發人員負責處置服務。

### <a name="idisposable-guidance-for-transient-and-shared-instances"></a>暫時性和共用實例的 IDisposable 指引

#### <a name="transient-limited-lifetime"></a>暫時性、有限存留期

**案例**

應用程式需要在 <xref:System.IDisposable> 下列任一案例中具有暫時性存留期的實例：

-  (根容器) 的根範圍中解析實例。
- 實例應該在範圍結束之前處置。

**解決方案**

使用 factory 模式，在父範圍之外建立實例。 在這種情況下，應用程式通常會有 `Create` 方法可直接呼叫最終型別的函式。 如果最終類型有其他相依性，factory 可以：

- <xref:System.IServiceProvider>在其函式中接收。
- 使用 <xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities.CreateInstance%2A?displayProperty=nameWithType> 可在容器外部具現化實例，同時使用容器作為其相依性。

#### <a name="shared-instance-limited-lifetime"></a>共用實例，有限存留期

**案例**

應用程式需要 <xref:System.IDisposable> 跨多個服務的共用實例，但 <xref:System.IDisposable> 實例的存留期應受限。

**解決方案**

註冊具有範圍存留期的實例。 使用 <xref:Microsoft.Extensions.DependencyInjection.IServiceScopeFactory.CreateScope%2A?displayProperty=nameWithType> 建立新的 <xref:Microsoft.Extensions.DependencyInjection.IServiceScope> 。 使用範圍 <xref:System.IServiceProvider> 來取得所需的服務。 不再需要時處置範圍。

#### <a name="general-idisposable-guidelines"></a>一般 `IDisposable` 指導方針

- 請勿 <xref:System.IDisposable> 在暫時性的存留期內註冊實例。 請改用 factory 模式。
- 請勿 <xref:System.IDisposable> 在根範圍中解析具有暫時性或範圍存留期的實例。 唯一的例外是應用程式建立/重新建立和處置 <xref:System.IServiceProvider> ，但這不是理想的模式。
- 透過 DI 接收相依性 <xref:System.IDisposable> 不需要接收者 <xref:System.IDisposable> 自行執行。 相依性的接收者不 <xref:System.IDisposable> 應呼叫 <xref:System.IDisposable.Dispose%2A> 該相依性。
- 使用範圍來控制服務的存留期。 範圍不是階層式，而且範圍之間沒有特殊連接。

如需資源清除的詳細資訊，請參閱 [執行 `Dispose` 方法](../../standard/garbage-collection/implementing-dispose.md)或 [執行 `DisposeAsync` 方法](../../standard/garbage-collection/implementing-disposeasync.md)。 此外，請考慮容器案例所捕捉的可 [處置暫時性服務](#disposable-transient-services-captured-by-container) ，因為它與資源清理相關。

## <a name="default-service-container-replacement"></a>預設服務容器取代

內建的服務容器是設計來滿足架構和大部分消費者應用程式的需求。 除非您需要不支援的特定功能，否則建議使用內建容器，例如：

- 屬性插入
- 根據名稱插入
- 子容器
- 自訂生命週期管理
- `Func<T>` 支援延遲初始設定
- 以慣例為基礎的註冊

下列協力廠商容器可搭配 ASP.NET Core apps 使用：

- [Autofac](https://autofac.readthedocs.io/en/latest/integration/aspnetcore.html)
- [DryIoc](https://www.nuget.org/packages/DryIoc.Microsoft.DependencyInjection)
- [Grace](https://www.nuget.org/packages/Grace.DependencyInjection.Extensions)
- [LightInject](https://github.com/seesharper/LightInject.Microsoft.DependencyInjection)
- [拉馬爾](https://jasperfx.github.io/lamar/)
- [Stashbox](https://github.com/z4kn4fein/stashbox-extensions-dependencyinjection)
- [Unity](https://www.nuget.org/packages/Unity.Microsoft.DependencyInjection)

## <a name="thread-safety"></a>執行緒安全

建立具備執行緒安全性的 singleton 服務。 如果單一服務相依于暫時性服務，暫時性服務可能也需要執行緒安全性，取決於 singleton 使用它的方式。

單一服務的 factory 方法（例如 >addsingleton 的第二個引數 [ \<TService> (IServiceCollection、Func \<IServiceProvider,TService>) ](xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A)）不需要是安全線程。 如同型別 () 的函式 `static` ，它保證只能由單一線程呼叫一次。

## <a name="recommendations"></a>建議

- `async/await` 並 `Task` 不支援以服務為基礎的服務解析。 因為 c # 不支援非同步函式，所以請在以同步方式解析服務後使用非同步方法。
- 避免直接在服務容器中儲存資料與設定。 例如，使用者的購物車通常不應該新增至服務容器。 組態應該使用選項模式。 同樣地，請避免只存在於允許存取另一個物件的「資料持有者」物件。 最好是透過 DI 要求實際項目。
- 避免靜態存取服務。 例如，請避免將 [IApplicationBuilder >iapplicationbuilder.applicationservices](xref:Microsoft.AspNetCore.Builder.IApplicationBuilder.ApplicationServices) 為靜態欄位或屬性，以便在其他地方使用。
- 讓 [DI](#async-di-factories-can-cause-deadlocks) factory 保持快速且同步。
- 請避免使用 [*服務定位器模式*](#scoped-service-as-singleton)。 例如，當您可以改用 DI 時，請勿叫用 <xref:System.IServiceProvider.GetService%2A> 來取得服務執行個體。
- 另一個要避免的服務定位器變化是插入在執行階段解析相依性的處理站。 這兩種做法都會混用[控制反轉](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#dependency-inversion)策略。
- 避免 <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> 在中呼叫 `ConfigureServices` 。 呼叫 `BuildServiceProvider` 通常會在開發人員想要解析中的服務時發生 `ConfigureServices` 。
- 容器[會捕獲可處置的暫時性服務](#disposable-transient-services-captured-by-container)以供處置。 如果從最上層容器解析，這可能會導致記憶體流失。
- 啟用範圍驗證，以確定應用程式沒有可捕獲範圍服務的 singleton。 如需詳細資訊，請參閱[範圍驗證](dependency-injection.md#scope-validation)。

就像所有的建議集，您可能會遇到需要忽略建議的情況。 例外狀況很罕見，大多是架構本身內的特殊案例。

DI 是靜態/全域物件存取模式的「替代」選項。 如果您將 DI 與靜態物件存取混合，則可能無法實現 DI 的優點。

## <a name="example-anti-patterns"></a>範例反模式

除了本文中的指導方針之外，還有數個 ***應該** 避免* 的反模式。 其中有些反模式是從開發執行時間本身學習而來的。

> [!WARNING]
> 這些是範例的反模式， *不會複製程式* 代碼、 *不使用這些* 模式，並以所有成本來避免這些模式。

### <a name="disposable-transient-services-captured-by-container"></a>容器所捕獲的可處置暫時性服務

當您註冊執行的 *暫時性* 服務時 <xref:System.IDisposable> ，DI 容器預設會保留這些參考，而不會保存到 <xref:System.IDisposable.Dispose> 應用程式停止之前。 如果從層級容器解析，這可能會導致記憶體流失。

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="18-30":::

在上述的反模式中，1000 `ExampleDisposable` 物件具現化和根目錄。 在實例處置之前，它們將不會被處置 `serviceProvider` 。

如需有關偵錯工具記憶體流失的詳細資訊，請參閱 [在 .net 中偵測記憶體](../diagnostics/debug-memory-leak.md)流失。

### <a name="async-di-factories-can-cause-deadlocks"></a>非同步 DI 處理站可能會造成鎖死

「DI factory」一詞是指呼叫時存在的多載方法 `Add{LIFETIME}` 。 有多載接受 `Func<IServiceProvider, T>` where `T` 是註冊的服務，並具名引數 `implementationFactory` 。 `implementationFactory`可以做為 lambda 運算式、區域函數或方法來提供。 如果 factory 是非同步，而且您使用 <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> ，這會造成鎖死。

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="32-45" highlight="4-8":::

在上述程式碼中， `implementationFactory` 會指定 lambda 運算式，其中主體會在傳回的 <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> 方法上呼叫 `Task<Bar>` 。 這 ***會造成鎖死***。 `GetBarAsync`方法只會使用來模擬非同步作業作業 <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> ，然後再呼叫 <xref:Microsoft.Extensions.DependencyInjection.ServiceProviderServiceExtensions.GetRequiredService%60%601(System.IServiceProvider)> 。

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="47-53":::

如需非同步指引的詳細資訊，請參閱 [非同步程式設計：重要資訊和建議](../../csharp/async.md#important-info-and-advice)。 如需偵錯工具鎖死的詳細資訊，請參閱 [在 .net 中偵測鎖死](../diagnostics/debug-deadlock.md)。

當您執行此反模式且發生鎖死時，您可以從 Visual Studio 的 [平行堆疊] 視窗查看兩個等候的執行緒。 如需詳細資訊，請參閱 [[平行堆疊] 視窗中的 [視圖執行緒和工作]](/visualstudio/debugger/using-the-parallel-stacks-window)。

### <a name="captive-dependency"></a>相關性

「驗證相依性」一詞是由[Mark Seeman](https://blog.ploeh.dk/about)所創造，並指的是服務存留期的設定不正確，[其中長期的](https://blog.ploeh.dk/2014/06/02/captive-dependency)服務會保留較短的服務。

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="55-65":::

在上述程式碼中， `Foo` 是以 singleton 的形式註冊，而且 `Bar` 範圍限定在表面上看起來是有效的。 但是，請考慮執行的 `Foo` 。

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Foo.cs" highlight="5":::

`Foo`物件需要 `Bar` 物件，因為 `Foo` 是 singleton，且 `Bar` 已設定範圍-這是設定錯誤的。 同樣地， `Foo` 它只會具現化一次，而且它會保留在 `Bar` 其存留期內（長度超過預期的範圍存留期） `Bar` 。 您應該考慮透過傳遞 `validateScopes: true` 給來驗證範圍 <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Boolean)> 。 當您驗證範圍時，您會收到一個 <xref:System.InvalidOperationException> 訊息，類似于「無法從單一 ' Foo ' 取用範圍服務 ' Bar '」。

如需詳細資訊，請參閱[範圍驗證](dependency-injection.md#scope-validation)。

### <a name="scoped-service-as-singleton"></a>範圍服務為 singleton

使用已設定範圍的服務時，如果您不是在現有的範圍內建立範圍，服務會變成 singleton。

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="68-82" highlight="13-14":::

在上述程式碼中， `Bar` 是在中的 <xref:Microsoft.Extensions.DependencyInjection.IServiceScope> ，它是正確的。 反模式是在範圍外的抓取 `Bar` ，並命名變數 `avoid` 以顯示不正確的範例抓取。

## <a name="see-also"></a>請參閱

- [.NET 中的相依性插入](dependency-injection.md)
- [教學課程：在 .NET 中使用相依性插入](dependency-injection-usage.md)
