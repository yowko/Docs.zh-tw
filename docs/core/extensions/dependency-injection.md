---
title: .NET 中的相依性插入
description: 瞭解 .NET 如何實行相依性插入，以及如何使用它。
author: IEvangelist
ms.author: dapine
ms.date: 09/23/2020
ms.topic: overview
ms.openlocfilehash: 2aaa24e54dad7b765781bf7c790890a57a77af14
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608349"
---
# <a name="dependency-injection-in-net"></a>.NET 中的相依性插入

.NET 支援 (DI) 軟體設計模式中的相依性插入，這項技術可讓您在類別與其相依性之間進行反向 [控制 (IoC) ](../../architecture/modern-web-apps-azure/architectural-principles.md#dependency-inversion) 。 .NET 中的相依性插入是一流的 [公民](https://en.wikipedia.org/wiki/First-class_citizen)，以及設定、記錄和選項模式。

相依 *性是另* 一個物件所依存的物件。 `MessageWriter`使用其他類別所依存的方法檢查下列類別 `Write` ：

```csharp
public class MessageWriter
{
    public void Write(string message)
    {
        Console.WriteLine($"MessageWriter.Write(message: \"{message}\")");
    }
}
```

類別可以建立類別的實例 `MessageWriter` ，以使用其 `Write` 方法。 在下列範例中， `MessageWriter` 類別是類別的相依性 `Worker` ：

```csharp
public class Worker : BackgroundService
{
    private readonly MessageWriter _messageWriter = new MessageWriter();

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        while (!stoppingToken.IsCancellationRequested)
        {
            _messageWriter.Write($"Worker running at: {DateTimeOffset.Now}");
            await Task.Delay(1000, stoppingToken);
        }
    }
}
```

類別會建立和直接相依于 `MessageWriter` 類別。 硬式編碼的相依性（例如在先前的範例中）有問題，因此應該避免因下列原因：

- 若要以 `MessageWriter` 不同的實作為取代， `MessageService` 必須修改該類別。
- 如果 `MessageWriter` 有相依性，則也必須由類別設定 `MessageService` 。 在具有多個相依於 `MessageWriter` 之多個類別的大型專案中，設定程式碼在不同的應用程式之間會變得鬆散。
- 此實作難以進行單元測試。 應用程式應該使用模擬 (Mock) 或虛設常式 (Stub) `MessageWriter` 類別，這在使用此方法時無法使用。

相依性插入可透過下列方式解決這些問題：

- 使用介面或基底類別來將相依性資訊抽象化。
- 在服務容器中註冊相依性。 .NET 提供內建的服務容器 <xref:System.IServiceProvider> 。 服務通常會在應用程式啟動時註冊，並附加至 <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> 。 新增所有服務之後，您就可以使用 <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> 來建立服務容器。
- 將服務「插入」** 到服務使用位置之類別的建構函式。 架構會負責建立相依性的執行個體，並在不再需要時將它捨棄。

例如， `IMessageWriter` 介面會定義 `Write` 方法：

:::code language="csharp" source="snippets/configuration/dependency-injection/IMessageWriter.cs":::

這個介面是由具象型別 `MessageWriter` 所實作：

:::code language="csharp" source="snippets/configuration/dependency-injection/MessageWriter.cs":::

範例程式碼會 `IMessageWriter` 使用具象類型來註冊服務 `MessageWriter` 。 <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A>方法會使用範圍存留期（單一要求的存留期）來註冊服務。 將在此主題稍後將說明[服務存留期](#service-lifetimes)。

:::code language="csharp" source="snippets/configuration/dependency-injection/Program.cs" highlight="16":::

在範例應用程式中， `IMessageWriter` 會要求服務並用來呼叫 `Write` 方法：

:::code language="csharp" source="snippets/configuration/dependency-injection/Worker.cs":::

使用 DI 模式時，背景工作角色服務：

- 不會使用具象型別 `MessageWriter` ，而只會使用實作為的 `IMessageWriter` 介面。 這可讓您輕鬆地變更控制器所使用的執行，而不需要修改控制器。
- 不會建立的實例 `MessageWriter` ，而是由 DI 容器所建立。

您 `IMessageWriter` 可以使用內建的記錄 API 來改善介面的實作為：

:::code language="csharp" source="snippets/configuration/dependency-injection/LoggingMessageWriter.cs":::

更新的 `ConfigureServices` 方法會註冊新的 `IMessageWriter` 實作為：

```csharp
static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureServices((_, services) =>
            services.AddHostedService<Worker>()
                    .AddScoped<IMessageWriter, LoggingMessageWriter>());
```

`LoggingMessageWriter` 相依于 <xref:Microsoft.Extensions.Logging.ILogger%601> 它在函式中要求的。 `ILogger<TCategoryName>` 是 [架構提供的服務](#framework-provided-services)。

以鏈結方式使用相依性插入並非不尋常。 每個要求的相依性接著會要求其自己的相依性。 容器會解決圖形中的相依性，並傳回完全解析的服務。 必須先解析的相依性集合組通常稱為「相依性樹狀結構」**、「相依性圖形」** 或「物件圖形」**。

容器會 `ILogger<TCategoryName>` 利用 [ (泛型) 開放式](/dotnet/csharp/language-reference/language-specification/types#open-and-closed-types)型別來解析，因此不需要註冊每個 [ (泛型) 結構類型](/dotnet/csharp/language-reference/language-specification/types#constructed-types)。

在相依性插入術語中，服務：

- 通常是為其他物件（例如服務）提供服務的物件 `IMessageWriter` 。
- 與 web 服務無關，但服務可能會使用 web 服務。

架構會提供健全的記錄系統。 `IMessageWriter`上述範例中所示的執行是為了示範基本 DI 而撰寫的，而不是用來執行記錄。 大部分的應用程式都不需要撰寫記錄器。 下列程式碼示範如何使用預設記錄，這只需要在 `Worker` 中註冊 `ConfigureServices` 為託管服務 <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A> ：

```csharp
public class Worker : BackgroundService
{
    private readonly ILogger<Worker> _logger;

    public Worker(ILogger<Worker> logger) =>
        _logger = logger;

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        while (!stoppingToken.IsCancellationRequested)
        {
            _logger.LogInformation("Worker running at: {time}", DateTimeOffset.Now);
            await Task.Delay(1000, stoppingToken);
        }
    }
}
```

使用上述程式碼不需要更新 `ConfigureServices` ，因為記錄是由架構提供。

## <a name="register-groups-of-services-with-extension-methods"></a>使用擴充方法來註冊服務群組

Microsoft 延伸模組使用註冊一組相關服務的慣例。 慣例是使用單一 `Add{GROUP_NAME}` 擴充方法來註冊架構功能所需的所有服務。 例如， <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A> 擴充方法會註冊使用選項所需的所有服務。

## <a name="framework-provided-services"></a>架構提供的服務

`ConfigureServices`方法會註冊應用程式所使用的服務，包括平臺功能。 一開始， `IServiceCollection` 提供給的是 `ConfigureServices` 由架構定義的服務，視 [主機的設定方式](generic-host.md#host-configuration)而定。 針對以 .NET 範本為基礎的應用程式，架構會註冊數百項服務。

下表列出這些架構註冊服務的小型範例：

| 服務類型                                                                       | 存留期  |
|------------------------------------------------------------------------------------|-----------|
| <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime>                       | 單一 |
| <xref:Microsoft.Extensions.Logging.ILogger%601?displayProperty=fullName>           | 單一 |
| <xref:Microsoft.Extensions.Logging.ILoggerFactory?displayProperty=fullName>        | 單一 |
| <xref:Microsoft.Extensions.ObjectPool.ObjectPoolProvider?displayProperty=fullName> | 單一 |
| <xref:Microsoft.Extensions.Options.IConfigureOptions%601?displayProperty=fullName> | 暫時性 |
| <xref:Microsoft.Extensions.Options.IOptions%601?displayProperty=fullName>          | 單一 |
| <xref:System.Diagnostics.DiagnosticListener?displayProperty=fullName>              | 單一 |
| <xref:System.Diagnostics.DiagnosticSource?displayProperty=fullName>                | 單一 |

## <a name="service-lifetimes"></a>服務存留期

您可以使用下列其中一種存留期來註冊服務：

- 暫時性
- 具範圍
- 單一

下列各節將說明每個先前的存留期。 為每個已註冊的服務選擇適當的存留期。

### <a name="transient"></a>暫時性

每次從服務容器要求暫時性存留期服務時都會建立它們。 此存留期最適合用於輕量型的無狀態服務。 使用註冊暫時性服務 <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddTransient%2A> 。

在處理要求的應用程式中，會在要求結束時處置暫時性服務。

### <a name="scoped"></a>具範圍

針對 web 應用程式，限域存留期表示每個用戶端要求都會建立服務一次， (連接) 。 使用註冊已設定範圍的服務 <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A> 。

在處理要求的應用程式中，會在要求結束時處置範圍服務。

使用 Entity Framework Core 時， <xref:Microsoft.Extensions.DependencyInjection.EntityFrameworkServiceCollectionExtensions.AddDbContext%2A> 擴充方法預設會註冊 `DbContext` 具有範圍存留期的類型。

> [!NOTE]
> 請勿 ***從 singleton 解析已*** 設定範圍的服務。 處理後續要求時，它可能會導致服務有不正確的狀態。 您可以：
>
> - 從範圍或暫時性服務解析單一服務。
> - 從另一個範圍或暫時性服務解析已設定範圍的服務。

根據預設，在開發環境中，從較長存留期的另一個服務解析服務，會擲回例外狀況。 如需詳細資訊，請參閱[範圍驗證](#scope-validation)。

### <a name="singleton"></a>單一

系統會建立單一存留期服務：

- 第一次要求時。
- 由開發人員直接將實實例提供給容器。 這種方法很少需要。

從相依性插入容器每個後續的服務執行要求都會使用相同的實例。 如果應用程式需要單一行為，請允許服務容器管理服務的存留期。 請勿實行 singleton 設計模式，並提供程式碼來處置 singleton。 服務絕對不能由從容器解析服務的程式碼處置。 如果類型或 factory 註冊為 singleton，則容器會自動處置 singleton。

使用註冊單一服務 <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A> 。 單一服務必須是安全線程，而且通常用於無狀態服務。

在處理要求的應用程式中，會在應用程式關閉時處置單一服務 <xref:Microsoft.Extensions.DependencyInjection.ServiceProvider> 。 因為在關閉應用程式之前不會釋出記憶體，請考慮使用單一服務的記憶體。

> [!WARNING]
> 請勿 ***從 singleton 解析已*** 設定範圍的服務。 處理後續要求時，它可能會導致服務有不正確的狀態。 從範圍或暫時性服務解析單一服務是很好的。

## <a name="service-registration-methods"></a>服務註冊方法

此架構提供適用于特定案例的服務註冊延伸方法：

| 方法 | 自動<br>物件 (object)<br>處置 | 多個<br>實作 | 傳遞引數 |
|--|:-:|:-:|:-:|
| `Add{LIFETIME}<{SERVICE}, {IMPLEMENTATION}>()`<br><br>範例：<br><br>`services.AddSingleton<IMyDep, MyDep>();` | 是 | 是 | 否 |
| `Add{LIFETIME}<{SERVICE}>(sp => new {IMPLEMENTATION})`<br><br>範例：<br><br>`services.AddSingleton<IMyDep>(sp => new MyDep());`<br>`services.AddSingleton<IMyDep>(sp => new MyDep(99));` | 是 | 是 | 是 |
| `Add{LIFETIME}<{IMPLEMENTATION}>()`<br><br>範例：<br><br>`services.AddSingleton<MyDep>();` | 是 | 否 | 否 |
| `AddSingleton<{SERVICE}>(new {IMPLEMENTATION})`<br><br>範例：<br><br>`services.AddSingleton<IMyDep>(new MyDep());`<br>`services.AddSingleton<IMyDep>(new MyDep(99));` | 否 | 是 | 是 |
| `AddSingleton(new {IMPLEMENTATION})`<br><br>範例：<br><br>`services.AddSingleton(new MyDep());`<br>`services.AddSingleton(new MyDep(99));` | 否 | 否 | 是 |

如需類型處置的詳細資訊，請參閱[＜服務處置＞](dependency-injection-guidelines.md#disposal-of-services)一節。

此架構也會提供 `TryAdd{LIFETIME}` 擴充方法，只有在尚未註冊任何執行時，才會註冊服務。

在下列範例中，呼叫以註冊為的 `AddSingleton` `MessageWriter` 實作為的 `IMessageWriter` 。 的呼叫 `TryAddSingleton` 沒有任何作用，因為 `IMessageWriter` 已經有已註冊的實作為：

```csharp
services.AddSingleton<IMessageWriter, MessageWriter>();
services.TryAddSingleton<IMessageWriter, DifferentMessageWriter>();
```

沒有 `TryAddSingleton` 任何作用，因為它已經加入，而且 "try" 將會失敗。

如需詳細資訊，請參閱

- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAdd%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddTransient%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddScoped%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddSingleton%2A>

只有在尚未有*相同類型*的執行時， [TryAddEnumerable (ServiceDescriptor) ](xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddEnumerable%2A)方法才會註冊服務。 多個服務會透過 `IEnumerable<{SERVICE}>` 解析。 註冊服務時，如果尚未加入相同類型的實例，請新增實例。 程式庫作者會使用 `TryAddEnumerable` 來避免在容器中註冊多個執行複本。

在下列範例中，第一次呼叫 `TryAddEnumerable` 註冊為的 `MessageWriter` 實作為 `IMessageWriter1` 。 第二個呼叫會註冊 `MessageWriter` `IMessageWriter2` 。 第三個呼叫沒有任何作用，因為 `IMessageWriter1` 已註冊的實作為 `MessageWriter` ：

```csharp
public interface IMessageWriter1 { }
public interface IMessageWriter2 { }

public class MessageWriter : IMessageWriter1, IMessageWriter2
{
}

services.TryAddEnumerable(ServiceDescriptor.Singleton<IMessageWriter1, MessageWriter>());
services.TryAddEnumerable(ServiceDescriptor.Singleton<IMessageWriter2, MessageWriter>());
services.TryAddEnumerable(ServiceDescriptor.Singleton<IMessageWriter1, MessageWriter>());
```

除非註冊相同類型的多個執行，否則服務註冊通常會獨立排序。

`IServiceCollection` 是物件的集合 <xref:Microsoft.Extensions.DependencyInjection.ServiceDescriptor> 。 下列範例顯示如何藉由建立和新增來註冊服務 `ServiceDescriptor` ：

```csharp
string secretKey = Configuration["SecretKey"];
var descriptor = new ServiceDescriptor(
    typeof(IMessageWriter),
    _ => new DefaultMessageWriter(secretKey),
    ServiceLifetime.Transient);

services.Add(descriptor);
```

內建方法會 `Add{LIFETIME}` 使用相同的方法。 例如，請參閱 [AddScoped 來源程式碼](https://github.com/dotnet/extensions/blob/v3.1.8/src/DependencyInjection/DI.Abstractions/src/ServiceCollectionServiceExtensions.cs#L216-L237)。

### <a name="constructor-injection-behavior"></a>建構函式插入行為

您可以使用下列方法來解析服務：

- <xref:System.IServiceProvider>
- <xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities>:
  - 建立未在容器中註冊的物件。
  - 搭配一些架構功能使用。

建構函式可以接受不是由相依性插入提供的引數，但引數必須指派預設值。

當服務由 `IServiceProvider` 或 `ActivatorUtilities` 解析時，建構函式插入會要求 *public*建構函式。

當服務由 `ActivatorUtilities` 解析時，建構函式插入只要求只能有一個適用的建構函式存在。 支援建構函式多載，但只能有一個多載存在，其引數可以藉由相依性插入而完成。

## <a name="scope-validation"></a>範圍驗證

當應用程式在環境中執行 `Development` 並呼叫 [>createdefaultbuilder](generic-host.md#default-builder-settings) 來建立主機時，預設服務提供者會執行檢查，以確認：

- 範圍服務無法從根服務提供者解析。
- 範圍服務不會插入 singleton 中。

根服務提供者會在呼叫 <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> 時建立。 當提供者啟動應用程式時，根服務提供者的存留期會對應到應用程式的存留期，並在應用程式關閉時處置。

範圍服務會由建立這些服務的容器處置。 如果在根容器中建立範圍服務，服務的存留期會有效地升階為 singleton，因為它只會在應用程式關閉時由根容器處置。 當呼叫 `BuildServiceProvider` 時，驗證服務範圍會攔截到這些情況。

## <a name="see-also"></a>另請參閱

- [使用 .NET 中的相依性插入](dependency-injection-usage.md)
- [相依性插入指導方針](dependency-injection-guidelines.md)
- [適用于 DI 應用程式開發的 NDC 會議模式](https://www.youtube.com/watch?v=x-C-CNBVTaY)
- [明確相依性準則](../../architecture/modern-web-apps-azure/architectural-principles.md#explicit-dependencies)
- [控制的容器和相依性插入模式的反轉 (聖馬丁 Fowler) ](https://www.martinfowler.com/articles/injection.html)
- 應該在 [github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues) 存放庫中建立 DI bug
