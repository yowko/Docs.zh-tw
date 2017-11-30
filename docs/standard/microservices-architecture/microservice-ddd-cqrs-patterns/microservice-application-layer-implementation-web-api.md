---
title: "實作微服務應用程式層使用 Web API"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |實作微服務應用程式層使用 Web API"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: d505a2561ae9b8dee05e803fd639387b63b28b70
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-the-microservice-application-layer-using-the-web-api"></a><span data-ttu-id="8e6cb-104">實作微服務應用程式層使用 Web API</span><span class="sxs-lookup"><span data-stu-id="8e6cb-104">Implementing the microservice application layer using the Web API</span></span>

## <a name="using-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a><span data-ttu-id="8e6cb-105">將應用程式層級插入的基礎結構物件使用相依性插入</span><span class="sxs-lookup"><span data-stu-id="8e6cb-105">Using Dependency Injection to inject infrastructure objects into your application layer</span></span>

<span data-ttu-id="8e6cb-106">如先前所述，就可以實作應用程式層的成品，您要建置，例如在 Web API 專案或 MVC web 應用程式專案的一部分。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-106">As mentioned previously, the application layer can be implemented as part of the artifact you are building, such as within a Web API project or an MVC web app project.</span></span> <span data-ttu-id="8e6cb-107">如果是使用 ASP.NET Core 建置微服務，應用程式層通常將為您的 Web 應用程式開發介面程式庫。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-107">In the case of a microservice built with ASP.NET Core, the application layer will usually be your Web API library.</span></span> <span data-ttu-id="8e6cb-108">如果您想要個別功能從您的自訂應用程式層程式碼來自 ASP.NET Core （它的基礎結構，加上您的控制站），您也可以將應用程式層級放在個別的類別庫中，但這是選擇性。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-108">If you want to separate what is coming from ASP.NET Core (its infrastructure plus your controllers) from your custom application layer code, you could also place your application layer in a separate class library, but that is optional.</span></span>

<span data-ttu-id="8e6cb-109">比方說，如果應用程式層的順序的微服務程式碼直接實作的一部分**Ordering.API**專案 （ASP.NET Core Web API 專案），以顯示圖 9-19 版。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-109">For instance, the application layer code of the ordering microservice is directly implemented as part of the **Ordering.API** project (an ASP.NET Core Web API project), as shown in Figure 9-19.</span></span>

![](./media/image20.png)

<span data-ttu-id="8e6cb-110">**圖 9-19**。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-110">**Figure 9-19**.</span></span> <span data-ttu-id="8e6cb-111">應用程式中的圖層 Ordering.API ASP.NET Core Web API 專案</span><span class="sxs-lookup"><span data-stu-id="8e6cb-111">The application layer in the Ordering.API ASP.NET Core Web API project</span></span>

<span data-ttu-id="8e6cb-112">ASP.NET Core 包含簡單[內建 IoC 容器](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)（由的 IServiceProvider 介面） 根據預設，支援建構函式插入並 ASP.NET 的特定服務提供透過 DI。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-112">ASP.NET Core includes a simple [built-in IoC container](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (represented by the IServiceProvider interface) that supports constructor injection by default, and ASP.NET makes certain services available through DI.</span></span> <span data-ttu-id="8e6cb-113">ASP.NET Core 會使用詞彙*服務*任何您註冊將會透過 DI 插入類型。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-113">ASP.NET Core uses the term *service* for any of the types you register that will be injected through DI.</span></span> <span data-ttu-id="8e6cb-114">您可以設定的內建的容器服務 ConfigureServices 類別方法中您的應用程式啟動。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-114">You configure the built-in container's services in the ConfigureServices method in your application's Startup class.</span></span> <span data-ttu-id="8e6cb-115">相依性會實作類型需要的服務。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-115">Your dependencies are implemented in the services that a type needs.</span></span>

<span data-ttu-id="8e6cb-116">一般而言，您會想要插入實作的基礎結構物件的相依性。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-116">Typically, you want to inject dependencies that implement infrastructure objects.</span></span> <span data-ttu-id="8e6cb-117">很常見的相依性，將會是儲存機制。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-117">A very typical dependency to inject is a repository.</span></span> <span data-ttu-id="8e6cb-118">但是，您會將您可能會有任何其他基礎結構相依性。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-118">But you could inject any other infrastructure dependency that you may have.</span></span> <span data-ttu-id="8e6cb-119">針對簡單的實作，您無法直接將插入您的工作單位的模式物件 （EF DbContext 物件），因為 DBContext 也是您基礎結構的持續性物件的實作。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-119">For simpler implementations, you could directly inject your Unit of Work pattern object (the EF DbContext object), because the DBContext is also the implementation of your infrastructure persistence objects.</span></span>

<span data-ttu-id="8e6cb-120">在下列範例中，您可以查看如何.NET Core 正在插入所需的儲存機制物件，透過建構函式。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-120">In the following example, you can see how .NET Core is injecting the required repository objects through the constructor.</span></span> <span data-ttu-id="8e6cb-121">此類別是命令處理常式，我們將在下一節中討論。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-121">The class is a command handler, which we will cover in the next section.</span></span>

```csharp
// Sample command handler
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;

    // Constructor where Dependencies are injected
    public CreateOrderCommandHandler(IOrderRepository orderRepository)
    {
        if (orderRepository == null)
        {
            throw new ArgumentNullException(nameof(orderRepository));
        }
        _orderRepository = orderRepository;
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        //
        // ... Additional code
        //
        // Create the Order AggregateRoot
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State,
            message.Country, message.ZipCode);
        var order = new Order(address, message.CardTypeId, message.CardNumber,
            message.CardSecurityNumber,
            message.CardHolderName,
            message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                item.Discount, item.PictureUrl, item.Units);
        }

        //Persist the Order through the Repository
        _orderRepository.Add(order);
        var result = await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
        return result > 0;
    }
}
```

<span data-ttu-id="8e6cb-122">類別會使用插入的儲存機制來執行交易，並將保存的狀態變更。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-122">The class uses the injected repositories to execute the transaction and persist the state changes.</span></span> <span data-ttu-id="8e6cb-123">並不重要的命令處理常式，ASP.NET Core Web API 控制器方法，該類別是否或[DDD 應用程式服務](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/)。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-123">It does not matter whether that class is a command handler, an ASP.NET Core Web API controller method, or a [DDD Application Service](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/).</span></span> <span data-ttu-id="8e6cb-124">最終仍是簡單的類別以類似的命令處理常式的方式使用儲存機制、 網域實體和其他應用程式的協調。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-124">It is ultimately a simple class that uses repositories, domain entities, and other application coordination in a fashion similar to a command handler.</span></span> <span data-ttu-id="8e6cb-125">相依性插入適用於所有提及的類別，如使用 DI 範例所示相同的方式根據建構函式。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-125">Dependency Injection works the same way for all the mentioned classes, as in the example using DI based on the constructor.</span></span>

### <a name="registering-the-dependency-implementation-types-and-interfaces-or-abstractions"></a><span data-ttu-id="8e6cb-126">正在註冊相依性的實作類型和介面或抽象物件</span><span class="sxs-lookup"><span data-stu-id="8e6cb-126">Registering the dependency implementation types and interfaces or abstractions</span></span>

<span data-ttu-id="8e6cb-127">您使用透過建構函式插入的物件之前，您需要知道去哪裡註冊介面和類別，會產生插入 DI 透過您的應用程式類別的物件。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-127">Before you use the objects injected through constructors, you need to know where to register the interfaces and classes that produce the objects injected into your application classes through DI.</span></span> <span data-ttu-id="8e6cb-128">（例如 DI 依據建構函式，如先前所示）。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-128">(Like DI based on the constructor, as shown previously.)</span></span>

#### <a name="using-the-built-in-ioc-container-provided-by-aspnet-core"></a><span data-ttu-id="8e6cb-129">使用 ASP.NET Core 所提供的內建 IoC 容器</span><span class="sxs-lookup"><span data-stu-id="8e6cb-129">Using the built-in IoC container provided by ASP.NET Core</span></span>

<span data-ttu-id="8e6cb-130">當您使用 ASP.NET Core 所提供的內建 IoC 容器時，您會註冊您想要插入 ConfigureServices 方法，在 Startup.cs 檔案中，例如下列程式碼中的類型：</span><span class="sxs-lookup"><span data-stu-id="8e6cb-130">When you use the built-in IoC container provided by ASP.NET Core, you register the types you want to inject in the ConfigureServices method in the Startup.cs file, as in the following code:</span></span>

```csharp
// Registration of types into ASP.NET Core built-in container
public void ConfigureServices(IServiceCollection services)
{
    // Register out-of-the-box framework services.
    services.AddDbContext<CatalogContext>(c =>
    {
        c.UseSqlServer(Configuration["ConnectionString"]);
    },
    ServiceLifetime.Scoped
    );
    services.AddMvc();
    // Register custom application dependencies.
    services.AddScoped<IMyCustomRepository, MyCustomSQLRepository>();
}
```

<span data-ttu-id="8e6cb-131">最常見的模式時註冊 IoC 容器中的型別是註冊一組類型 — 介面和其相關的實作類別。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-131">The most common pattern when registering types in an IoC container is to register a pair of types—an interface and its related implementation class.</span></span> <span data-ttu-id="8e6cb-132">然後當您從 IoC 容器透過任何建構函式要求物件，您可以要求介面的特定類型的物件。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-132">Then when you request an object from the IoC container through any constructor, you request an object of a certain type of interface.</span></span> <span data-ttu-id="8e6cb-133">比方說，在上述範例中，最後一行會指出當您建構函式的任何有相依性 IMyCustomRepository （介面或抽象） 時，IoC 容器會插入 MyCustomSQLServerRepository 實作的執行個體類別。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-133">For instance, in the previous example, the last line states that when any of your constructors have a dependency on IMyCustomRepository (interface or abstraction), the IoC container will inject an instance of the MyCustomSQLServerRepository implementation class.</span></span>

#### <a name="using-the-scrutor-library-for-automatic-types-registration"></a><span data-ttu-id="8e6cb-134">使用自動類型註冊 Scrutor 程式庫</span><span class="sxs-lookup"><span data-stu-id="8e6cb-134">Using the Scrutor library for automatic types registration</span></span>

<span data-ttu-id="8e6cb-135">中使用時 DI.NET Core，您可能想要掃描組件，並自動註冊它的類型依慣例。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-135">When using DI in .NET Core, you might want to be able to scan an assembly and automatically register its types by convention.</span></span> <span data-ttu-id="8e6cb-136">這項功能目前不提供在 ASP.NET Core。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-136">This feature is not currently available in ASP.NET Core.</span></span> <span data-ttu-id="8e6cb-137">不過，您可以使用[Scrutor](https://github.com/khellang/Scrutor)該程式庫。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-137">However, you can use the [Scrutor](https://github.com/khellang/Scrutor) library for that.</span></span> <span data-ttu-id="8e6cb-138">當您有數十個需要註冊 IoC 容器中的類型，則這個方法會很方便。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-138">This approach is convenient when you have dozens of types that need to be registered in your IoC container.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="8e6cb-139">其他資源</span><span class="sxs-lookup"><span data-stu-id="8e6cb-139">Additional resources</span></span>

-   <span data-ttu-id="8e6cb-140">**Matthew 國王。服務登錄 Scrutor**
    [*https://mking.io/blog/registering-services-with-scrutor*](https://mking.io/blog/registering-services-with-scrutor)</span><span class="sxs-lookup"><span data-stu-id="8e6cb-140">**Matthew King. Registering services with Scrutor**
[*https://mking.io/blog/registering-services-with-scrutor*](https://mking.io/blog/registering-services-with-scrutor)</span></span>

<!-- -->

-   <span data-ttu-id="8e6cb-141">**Kristian Hellang。Scrutor。**</span><span class="sxs-lookup"><span data-stu-id="8e6cb-141">**Kristian Hellang. Scrutor.**</span></span> <span data-ttu-id="8e6cb-142">GitHub 儲存機制。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-142">GitHub repo.</span></span>
    [<span data-ttu-id="8e6cb-143">*https://github.com/khellang/Scrutor*</span><span class="sxs-lookup"><span data-stu-id="8e6cb-143">*https://github.com/khellang/Scrutor*</span></span>](https://github.com/khellang/Scrutor)

#### <a name="using-autofac-as-an-ioc-container"></a><span data-ttu-id="8e6cb-144">使用 Autofac IoC 容器</span><span class="sxs-lookup"><span data-stu-id="8e6cb-144">Using Autofac as an IoC container</span></span>

<span data-ttu-id="8e6cb-145">您也可以使用其他 IoC 容器，並插入 ASP.NET Core 管線，如同在 eShopOnContainers，會使用排序的微服務[Autofac](https://autofac.org/)。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-145">You can also use additional IoC containers and plug them into the ASP.NET Core pipeline, as in the ordering microservice in eShopOnContainers, which uses [Autofac](https://autofac.org/).</span></span> <span data-ttu-id="8e6cb-146">當使用 Autofac 通常會註冊透過模組，可讓您將根據您的型別所處，就像您可能會分散到多個類別程式庫的應用程式類型的多個檔案之間的註冊型別類型。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-146">When using Autofac you typically register the types via modules, which allow you to split the registration types between multiple files depending on where your types are, just as you could have the application types distributed across multiple class libraries.</span></span>

<span data-ttu-id="8e6cb-147">例如，下列是[Autofac 應用程式模組](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs)如[Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API)專案，您會想要插入的型別。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-147">For example, the following is the [Autofac application module](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) for the [Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) project with the types you will want to inject.</span></span>

```csharp
public class ApplicationModule
    :Autofac.Module
{
    public string QueriesConnectionString { get; }
    public ApplicationModule(string qconstr)
    {
        QueriesConnectionString = qconstr;
    }

    protected override void Load(ContainerBuilder builder)
    {
        builder.Register(c => new OrderQueries(QueriesConnectionString))
            .As<IOrderQueries>()
            .InstancePerLifetimeScope();
        builder.RegisterType<BuyerRepository>()
            .As<IBuyerRepository>()
            .InstancePerLifetimeScope();
        builder.RegisterType<OrderRepository>()
            .As<IOrderRepository>()
            .InstancePerLifetimeScope();
        builder.RegisterType<RequestManager>()
            .As<IRequestManager>()
            .InstancePerLifetimeScope();
   }
}
```

<span data-ttu-id="8e6cb-148">註冊程序和概念是您可以使用內建 ASP.NET Core iOS 容器註冊類型的方式非常類似，但語法使用 Autofac 時稍有不同。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-148">The registration process and concepts are very similar to the way you can register types with the built-in ASP.NET Core iOS container, but the syntax when using Autofac is a bit different.</span></span>

<span data-ttu-id="8e6cb-149">在範例程式碼，以及實作類別 OrderRepository 註冊抽象 IOrderRepository。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-149">In the example code, the abstraction IOrderRepository is registered along with the implementation class OrderRepository.</span></span> <span data-ttu-id="8e6cb-150">這表示每當建構函式會宣告透過 IOrderRepository 抽象或介面的相依性，IoC 容器會插入 OrderRepository 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-150">This means that whenever a constructor is declaring a dependency through the IOrderRepository abstraction or interface, the IoC container will inject an instance of the OrderRepository class.</span></span>

<span data-ttu-id="8e6cb-151">執行個體範圍類型會決定執行個體共用相同的服務或相依性的要求之間的方式。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-151">The instance scope type determines how an instance is shared between requests for the same service or dependency.</span></span> <span data-ttu-id="8e6cb-152">當提出要求的相依性 IoC 容器可以傳回下列結果：</span><span class="sxs-lookup"><span data-stu-id="8e6cb-152">When a request is made for a dependency, the IoC container can return the following:</span></span>

-   <span data-ttu-id="8e6cb-153">每個存留期範圍的單一執行個體 (做為 ASP.NET Core IoC 容器所指*範圍*)。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-153">A single instance per lifetime scope (referred to in the ASP.NET Core IoC container as *scoped*).</span></span>

-   <span data-ttu-id="8e6cb-154">每個相依性的新執行個體 (做為 ASP.NET Core IoC 容器所指*暫時性*)。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-154">A new instance per dependency (referred to in the ASP.NET Core IoC container as *transient*).</span></span>

-   <span data-ttu-id="8e6cb-155">在使用 IoC 容器的所有物件共用的單一執行個體 (做為 ASP.NET Core IoC 容器所指*單一*)。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-155">A single instance shared across all objects using the IoC container (referred to in the ASP.NET Core IoC container as *singleton*).</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="8e6cb-156">其他資源</span><span class="sxs-lookup"><span data-stu-id="8e6cb-156">Additional resources</span></span>

-   <span data-ttu-id="8e6cb-157">**相依性插入在 ASP.NET Core 簡介**
    [*https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection*](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)</span><span class="sxs-lookup"><span data-stu-id="8e6cb-157">**Introduction to Dependency Injection in ASP.NET Core**
[*https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection*](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)</span></span>

-   <span data-ttu-id="8e6cb-158">**Autofac。**</span><span class="sxs-lookup"><span data-stu-id="8e6cb-158">**Autofac.**</span></span> <span data-ttu-id="8e6cb-159">官方文件集。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-159">Official documentation.</span></span>
    [<span data-ttu-id="8e6cb-160">*http://docs.autofac.org/en/latest/*</span><span class="sxs-lookup"><span data-stu-id="8e6cb-160">*http://docs.autofac.org/en/latest/*</span></span>](http://docs.autofac.org/en/latest/)

-   <span data-ttu-id="8e6cb-161">**Cesar de la Torre：比較 ASP.NET Core IoC 容器服務存留期與 Autofac IoC 容器執行個體範圍**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span><span class="sxs-lookup"><span data-stu-id="8e6cb-161">**Cesar de la Torre. Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes**
[*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span></span>

## <a name="implementing-the-command-and-command-handler-patterns"></a><span data-ttu-id="8e6cb-162">實作的命令和命令處理常式模式</span><span class="sxs-lookup"><span data-stu-id="8e6cb-162">Implementing the Command and Command Handler patterns</span></span>

<span data-ttu-id="8e6cb-163">DI 透過建構函式所示範例中上一節，IoC 容器所插入的儲存機制，透過在類別中的建構函式。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-163">In the DI-through-constructor example shown in the previous section, the IoC container was injecting repositories through a constructor in a class.</span></span> <span data-ttu-id="8e6cb-164">不過，完全其中被它們插入嗎？</span><span class="sxs-lookup"><span data-stu-id="8e6cb-164">But exactly where were they injected?</span></span> <span data-ttu-id="8e6cb-165">在簡單 Web API （例如，目錄微服務中 eShopOnContainers） 中，您將它們插入在 MVC 控制器層級，控制站的建構函式中。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-165">In a simple Web API (for example, the catalog microservice in eShopOnContainers), you inject them at the MVC controllers level, in a controller constructor.</span></span> <span data-ttu-id="8e6cb-166">不過，在此區段之初始程式碼 ( [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) eShopOnContainers Ordering.API 服務類別)，資料隱碼的相依性透過特定命令的建構函式處理常式。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-166">However, in the initial code of this section (the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) class from the Ordering.API service in eShopOnContainers), the injection of dependencies is done through the constructor of a particular command handler.</span></span> <span data-ttu-id="8e6cb-167">讓我們將說明什麼是命令處理常式，且您會想要使用它。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-167">Let us explain what a command handler is and why you would want to use it.</span></span>

<span data-ttu-id="8e6cb-168">稍早在本指南中引進的 CQRS 模式在本質上與命令模式。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-168">The Command pattern is intrinsically related to the CQRS pattern that was introduced earlier in this guide.</span></span> <span data-ttu-id="8e6cb-169">CQRS 有兩個邊。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-169">CQRS has two sides.</span></span> <span data-ttu-id="8e6cb-170">第一個區域是使用簡化的查詢與查詢[Dapper](https://github.com/StackExchange/dapper-dot-net)微 ORM，先前所述。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-170">The first area is queries, using simplified queries with the [Dapper](https://github.com/StackExchange/dapper-dot-net) micro ORM, which was explained previously.</span></span> <span data-ttu-id="8e6cb-171">第二個區域是命令，也就是交易的起始點和從服務外部輸入的通道。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-171">The second area is commands, which are the starting point for transactions, and the input channel from outside the service.</span></span>

<span data-ttu-id="8e6cb-172">這個模式所示圖 9-20，根據接受來自用戶端的命令處理根據網域模型的規則，以及最後保存與交易的狀態。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-172">As shown in Figure 9-20, the pattern is based on accepting commands from the client side, processing them based on the domain model rules, and finally persisting the states with transactions.</span></span>

![](./media/image21.png)

<span data-ttu-id="8e6cb-173">**圖 9-20**。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-173">**Figure 9-20**.</span></span> <span data-ttu-id="8e6cb-174">命令或 CQRS 模式中的 「 交易式端 」 的高階檢視</span><span class="sxs-lookup"><span data-stu-id="8e6cb-174">High-level view of the commands or “transactional side” in a CQRS pattern</span></span>

### <a name="the-command-class"></a><span data-ttu-id="8e6cb-175">命令類別</span><span class="sxs-lookup"><span data-stu-id="8e6cb-175">The command class</span></span>

<span data-ttu-id="8e6cb-176">命令會為系統執行的動作會變更系統狀態的要求。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-176">A command is a request for the system to perform an action that changes the state of the system.</span></span> <span data-ttu-id="8e6cb-177">命令是必要的工作，，，應該就可以一次處理。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-177">Commands are imperative, and should be processed just once.</span></span>

<span data-ttu-id="8e6cb-178">由於命令全面，通常名為具有動詞命令命令式消遣 （例如，「 建立 」 或 「 更新 」），而且它們可能包含的彙總類型，例如 CreateOrderCommand。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-178">Since commands are imperatives, they are typically named with a verb in the imperative mood (for example, "create" or "update"), and they might include the aggregate type, such as CreateOrderCommand.</span></span> <span data-ttu-id="8e6cb-179">與事件時，命令不是從過去; 事實它只是要求，並因此可能會被拒絕。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-179">Unlike an event, a command is not a fact from the past; it is only a request, and thus may be refused.</span></span>

<span data-ttu-id="8e6cb-180">程序管理員導向彙總來執行動作時，從使用者起始要求，因為 UI 或程序管理員可以產生命令。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-180">Commands can originate from the UI as a result of a user initiating a request, or from a process manager when the process manager is directing an aggregate to perform an action.</span></span>

<span data-ttu-id="8e6cb-181">命令的重要特性是，它應該只有一次由單一接收者。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-181">An important characteristic of a command is that it should be processed just once by a single receiver.</span></span> <span data-ttu-id="8e6cb-182">這是因為命令是單一動作或您想要執行應用程式中的交易。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-182">This is because a command is a single action or transaction you want to perform in the application.</span></span> <span data-ttu-id="8e6cb-183">例如，相同的順序建立命令不應處理一次以上。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-183">For example, the same order creation command should not be processed more than once.</span></span> <span data-ttu-id="8e6cb-184">這是一項重要差異之間命令和事件。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-184">This is an important difference between commands and events.</span></span> <span data-ttu-id="8e6cb-185">事件可能會處理許多次，因為許多系統或 microservices 可能感興趣的事件。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-185">Events may be processed multiple times, because many systems or microservices might be interested in the event.</span></span>

<span data-ttu-id="8e6cb-186">此外，很重要，命令會只處理一次此命令不是等冪。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-186">In addition, it is important that a command be processed only once in case the command is not idempotent.</span></span> <span data-ttu-id="8e6cb-187">如果執行多次而不會變更結果中，由於本質之故命令，或因為系統會處理命令的方式，命令會為等冪。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-187">A command is idempotent if it can be executed multiple times without changing the result, either because of the nature of the command, or because of the way the system handles the command.</span></span>

<span data-ttu-id="8e6cb-188">最好的作法是讓命令，並在您網域的商務規則和非變異值意義時更新具有等冪性。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-188">It is a good practice to make your commands and updates idempotent when it makes sense under your domain’s business rules and invariants.</span></span> <span data-ttu-id="8e6cb-189">比方說，如果基於任何原因 （重試邏輯，駭客等） 相同的 CreateOrder 命令達到您的系統多次使用相同的範例，您應該能夠識別它，並確保不會建立多個訂單。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-189">For instance, to use the same example, if for any reason (retry logic, hacking, etc.) the same CreateOrder command reaches your system multiple times, you should be able to identify it and ensure that you do not create multiple orders.</span></span> <span data-ttu-id="8e6cb-190">若要這樣做，您需要附加某種類型的作業中的身分識別是否已經處理的命令或更新。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-190">To do so, you need to attach some kind of identity in the operations and identify whether the command or update was already processed.</span></span>

<span data-ttu-id="8e6cb-191">您將命令傳送到單一接收者;請勿發行命令。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-191">You send a command to a single receiver; you do not publish a command.</span></span> <span data-ttu-id="8e6cb-192">發行適用於該狀態的事實整合事件 — 某項目發生，而且可能會有興趣的事件接收器。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-192">Publishing is for integration events that state a fact—that something has happened and might be interesting for event receivers.</span></span> <span data-ttu-id="8e6cb-193">事件，在 「 發行者 」 有哪些接收器事件或取得它們的功用它沒有問題。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-193">In the case of events, the publisher has no concerns about which receivers get the event or what they do it.</span></span> <span data-ttu-id="8e6cb-194">但是整合事件不同的劇本，已經導入上一節。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-194">But integration events are a different story already introduced in previous sections.</span></span>

<span data-ttu-id="8e6cb-195">命令是使用包含資料欄位或具有所有所需的資訊才能執行該命令的集合類別實作。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-195">A command is implemented with a class that contains data fields or collections with all the information that is needed in order to execute that command.</span></span> <span data-ttu-id="8e6cb-196">命令是一種特殊的資料傳輸物件 (DTO)，專門用來要求變更或交易的其中一個。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-196">A command is a special kind of Data Transfer Object (DTO), one that is specifically used to request changes or transactions.</span></span> <span data-ttu-id="8e6cb-197">命令本身根據完全處理命令，而無其他所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-197">The command itself is based on exactly the information that is needed for processing the command, and nothing more.</span></span>

<span data-ttu-id="8e6cb-198">下列範例示範簡化的 CreateOrderCommand 類別。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-198">The following example shows the simplified CreateOrderCommand class.</span></span> <span data-ttu-id="8e6cb-199">這是用於排序的微服務 eShopOnContainers 中不可變命令。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-199">This is an immutable command that is used in the ordering microservice in eShopOnContainers.</span></span>

```csharp
// DDD and CQRS patterns comment
// Note that it is recommended that yuo implement immutable commands
// In this case, immutability is achieved by having all the setters as private
// plus being able to update the data just once, when creating the object
// through the constructor.
// References on immutable commands:
// http://cqrs.nu/Faq
// https://docs.spine3.org/motivation/immutability.html
// http://blog.gauffin.org/2012/06/griffin-container-introducing-command-support/
// https://msdn.microsoft.com/en-us/library/bb383979.aspx
[DataContract]
public class CreateOrderCommand
    :IAsyncRequest<bool>
{
    [DataMember]
    private readonly List<OrderItemDTO> _orderItems;

    [DataMember]
    public string City { get; private set; }

    [DataMember]
    public string Street { get; private set; }

    [DataMember]
    public string State { get; private set; }

    [DataMember]
    public string Country { get; private set; }

    [DataMember]
    public string ZipCode { get; private set; }

    [DataMember]
    public string CardNumber { get; private set; }

    [DataMember]
    public string CardHolderName { get; private set; }

    [DataMember]
    public DateTime CardExpiration { get; private set; }

    [DataMember]
    public string CardSecurityNumber { get; private set; }

    [DataMember]
    public int CardTypeId { get; private set; }

    [DataMember]
    public IEnumerable<OrderItemDTO> OrderItems => _orderItems;

    public CreateOrderCommand()
    {
        _orderItems = new List<OrderItemDTO>();
    }

    public CreateOrderCommand(List<OrderItemDTO> orderItems, string city,
        string street,
        string state, string country, string zipcode,
        string cardNumber, string cardHolderName, DateTime cardExpiration,
        string cardSecurityNumber, int cardTypeId) : this()
    {
        _orderItems = orderItems;
        City = city;
        Street = street;
        State = state;
        Country = country;
        ZipCode = zipcode;
        CardNumber = cardNumber;
        CardHolderName = cardHolderName;
        CardSecurityNumber = cardSecurityNumber;
        CardTypeId = cardTypeId;
        CardExpiration = cardExpiration;
    }

    public class OrderItemDTO
    {
        public int ProductId { get; set; }
        public string ProductName { get; set; }
        public decimal UnitPrice { get; set; }
        public decimal Discount { get; set; }
        public int Units { get; set; }
        public string PictureUrl { get; set; }
    }
}
```

<span data-ttu-id="8e6cb-200">基本上，命令類別包含您需要執行了商務交易使用的網域模型物件的所有資料。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-200">Basically, the command class contains all the data you need for performing a business transaction by using the domain model objects.</span></span> <span data-ttu-id="8e6cb-201">因此，命令會只是資料結構，其中包含唯讀的資料，以及任何行為。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-201">Thus, commands are simply data structures that contain read-only data, and no behavior.</span></span> <span data-ttu-id="8e6cb-202">命令的名稱會表示其用途。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-202">The command’s name indicates its purpose.</span></span> <span data-ttu-id="8e6cb-203">在許多語言如 C\#，命令會表示為類別，但它們不是真正的物件導向的意義上，則為 true 的類別。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-203">In many languages like C\#, commands are represented as classes, but they are not true classes in the real object-oriented sense.</span></span>

<span data-ttu-id="8e6cb-204">為其他的特性，命令是不可變的因為預期的用法是，它們會處理由網域模型直接。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-204">As an additional characteristic, commands are immutable, because the expected usage is that they are processed directly by the domain model.</span></span> <span data-ttu-id="8e6cb-205">它們不需要變更其投影的存留期間。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-205">They do not need to change during their projected lifetime.</span></span> <span data-ttu-id="8e6cb-206">在 C 中\#類別，不變性可藉由沒有任何 setter 或其他方法的內部狀態變更。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-206">In a C\# class, immutability can be achieved by not having any setters or other methods that change internal state.</span></span>

<span data-ttu-id="8e6cb-207">例如，建立訂單的命令類別可能很類似以資料為您想要建立的順序，但您可能不需要相同的屬性。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-207">For example, the command class for creating an order is probably similar in terms of data to the order you want to create, but you probably do not need the same attributes.</span></span> <span data-ttu-id="8e6cb-208">比方說，CreateOrderCommand 沒有訂單 ID，因為順序尚未建立。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-208">For instance, CreateOrderCommand does not have an order ID, because the order has not been created yet.</span></span>

<span data-ttu-id="8e6cb-209">許多命令類別可以很簡單，需要幾個欄位只需要變更某些狀態相關的。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-209">Many command classes can be simple, requiring only a few fields about some state that needs to be changed.</span></span> <span data-ttu-id="8e6cb-210">也就是使用案例如果您只變更從 「 進行中 」 至訂單狀態 」 付費 」 或 「 出貨 」 使用與下列類似的命令：</span><span class="sxs-lookup"><span data-stu-id="8e6cb-210">That would be the case if you are just changing the status of an order from “in process” to “paid” or “shipped” by using a command similar to the following:</span></span>

```csharp
[DataContract]
public class UpdateOrderStatusCommand
    :IAsyncRequest<bool>
{
    [DataMember]
    public string Status { get; private set; }

    [DataMember]
    public string OrderId { get; private set; }

    [DataMember]
    public string BuyerIdentityGuid { get; private set; }
}
```

<span data-ttu-id="8e6cb-211">有些開發人員建立其 UI 要求物件從其命令 DTOs，分離，但這就只不過喜好設定。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-211">Some developers make their UI request objects separate from their command DTOs, but that is just a matter of preference.</span></span> <span data-ttu-id="8e6cb-212">它是冗長的分隔，與不太加入的值，而且物件幾乎完全相同的圖形。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-212">It is a tedious separation with not much added value, and the objects are almost exactly the same shape.</span></span> <span data-ttu-id="8e6cb-213">比方說，在 eShopOnContainers，命令直接來自用戶端。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-213">For instance, in eShopOnContainers, the commands come directly from the client side.</span></span>

### <a name="the-command-handler-class"></a><span data-ttu-id="8e6cb-214">命令處理常式類別</span><span class="sxs-lookup"><span data-stu-id="8e6cb-214">The Command Handler class</span></span>

<span data-ttu-id="8e6cb-215">您應該實作每個命令的特定命令處理常式類別。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-215">You should implement a specific command handler class for each command.</span></span> <span data-ttu-id="8e6cb-216">這是模式的運作方式，而且您將在其中使用的命令物件、 網域物件和基礎結構的儲存機制物件。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-216">That is how the pattern works, and it is where you will use the command object, the domain objects, and the infrastructure repository objects.</span></span> <span data-ttu-id="8e6cb-217">命令處理常式事實上是 CQRS 和 DDD 方面的應用程式層的中心。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-217">The command handler is in fact the heart of the application layer in terms of CQRS and DDD.</span></span> <span data-ttu-id="8e6cb-218">不過，所有網域邏輯應該都包含在網域類別 — 彙總根 （root 實體） 內子實體或[網域服務](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/)，但不是在的命令處理常式，這是從應用程式類別圖層。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-218">However, all the domain logic should be contained within the domain classes—within the aggregate roots (root entities), child entities, or [domain services](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), but not within the command handler, which is a class from the application layer.</span></span>

<span data-ttu-id="8e6cb-219">命令處理常式收到命令，並取得使用彙總的結果。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-219">A command handler receives a command and obtains a result from the aggregate that is used.</span></span> <span data-ttu-id="8e6cb-220">結果應該是命令執行成功或是發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-220">The result should be either successful execution of the command, or an exception.</span></span> <span data-ttu-id="8e6cb-221">例外狀況，在系統狀態應該維持不變。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-221">In the case of an exception, the system state should be unchanged.</span></span>

<span data-ttu-id="8e6cb-222">命令處理常式通常會採取下列步驟：</span><span class="sxs-lookup"><span data-stu-id="8e6cb-222">The command handler usually takes the following steps:</span></span>

-   <span data-ttu-id="8e6cb-223">它接收的命令物件，例如 DTO (從[暫留處理器](https://en.wikipedia.org/wiki/Mediator_pattern)或其他基礎結構物件)。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-223">It receives the command object, like a DTO (from the [mediator](https://en.wikipedia.org/wiki/Mediator_pattern) or other infrastructure object).</span></span>

-   <span data-ttu-id="8e6cb-224">它會驗證命令有效 （如果未經過暫留處理器）。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-224">It validates that the command is valid (if not validated by the mediator).</span></span>

-   <span data-ttu-id="8e6cb-225">它會具現化的目前命令目標的彙總的根執行個體。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-225">It instantiates the aggregate root instance that is the target of the current command.</span></span>

-   <span data-ttu-id="8e6cb-226">它會在彙總根執行個體，從命令取得所需的資料執行方法。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-226">It executes the method on the aggregate root instance, getting the required data from the command.</span></span>

-   <span data-ttu-id="8e6cb-227">它會保存在彙總至其相關資料庫的新狀態。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-227">It persists the new state of the aggregate to its related database.</span></span> <span data-ttu-id="8e6cb-228">這最後一項作業是實際的交易。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-228">This last operation is the actual transaction.</span></span>

<span data-ttu-id="8e6cb-229">一般而言，是命令處理常式會處理由其彙總根 (root entity) 的單一彙總。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-229">Typically, a command handler deals with a single aggregate driven by its aggregate root (root entity).</span></span> <span data-ttu-id="8e6cb-230">如果多個彙總應該受到接收單一命令，您可以使用網域事件狀態或動作散佈在多個彙總</span><span class="sxs-lookup"><span data-stu-id="8e6cb-230">If multiple aggregates should be impacted by the reception of a single command, you could use domain events to propagate states or actions across multiple aggregates</span></span>

<span data-ttu-id="8e6cb-231">此處的重點是處理命令時，所有網域邏輯都應在網域模型內 （彙總），全部封裝，且可供單元測試。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-231">The important point here is that when a command is being processed, all the domain logic should be inside the domain model (the aggregates), fully encapsulated and ready for unit testing.</span></span> <span data-ttu-id="8e6cb-232">命令處理常式只可作為從資料庫取得網域模型的方法和最後一個步驟，通知基礎結構層級 （儲存機制），來保存變更的模式變更。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-232">The command handler just acts as a way to get the domain model from the database, and as the final step, to tell the infrastructure layer (repositories) to persist the changes when the model is changed.</span></span> <span data-ttu-id="8e6cb-233">這種方法的優點是您可以不需要變更基礎結構的圖層，是連接層級 （命令處理常式，Web API 的應用程式中的程式碼重構網域中的邏輯隔離、 完整封裝、 豐富、 行為網域模型儲存機制等等）。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-233">The advantage of this approach is that you can refactor the domain logic in an isolated, fully encapsulated, rich, behavioral domain model without changing code in the application or infrastructure layers, which are the plumbing level (command handlers, Web API, repositories, etc.).</span></span>

<span data-ttu-id="8e6cb-234">當命令處理常式收到複雜，太多邏輯，可能是程式碼的氣味。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-234">When command handlers get complex, with too much logic, that can be a code smell.</span></span> <span data-ttu-id="8e6cb-235">檢閱其內容，和如果您發現網域邏輯，重構程式碼將該網域行為移至網域物件 （彙總根及子實體） 的方法。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-235">Review them, and if you find domain logic, refactor the code to move that domain behavior to the methods of the domain objects (the aggregate root and child entity).</span></span>

<span data-ttu-id="8e6cb-236">例如命令處理常式類別中，下列程式碼會顯示您所見的相同 CreateOrderCommandHandler 類別在本指南的開頭。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-236">As an example of a command handler class, the following code shows the same CreateOrderCommandHandler class that you saw at the beginning of this chapter.</span></span> <span data-ttu-id="8e6cb-237">在此情況下我們所反白顯示的控制代碼方法並搭配網域模型物件/彙總作業。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-237">In this case we have highlighted the Handle method and the operations with the domain model objects/aggregates.</span></span>

```csharp
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IBuyerRepository _buyerRepository;
    private readonly IOrderRepository _orderRepository;

    public CreateOrderCommandHandler(IBuyerRepository buyerRepository,
        IOrderRepository orderRepository)
    {
        if (buyerRepository == null)
        {
            throw new ArgumentNullException(nameof(buyerRepository));
        }
        if (orderRepository == null)
        {
            throw new ArgumentNullException(nameof(orderRepository));
        }

        _buyerRepository = buyerRepository;
        _orderRepository = orderRepository;
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        //
        // Additional code ...
        //
        // Create the Order aggregate root
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var order = new Order(buyer.Id, payment.Id,
            new Address(message.Street,
            message.City, message.State,
            message.Country, message.ZipCode));

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                item.Discount, item.PictureUrl, item.Units);
        }

        // Persist the Order through the aggregate's repository
        _orderRepository.Add(order);
        return await _orderRepository.UnitOfWork.SaveChangesAsync();
    }
}
```

<span data-ttu-id="8e6cb-238">以下是命令處理常式應該採取的額外步驟：</span><span class="sxs-lookup"><span data-stu-id="8e6cb-238">These are additional steps a command handler should take:</span></span>

-   <span data-ttu-id="8e6cb-239">使用命令的資料操作與彙總根方法行為。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-239">Use the command’s data to operate with the aggregate root’s methods and behavior.</span></span>

-   <span data-ttu-id="8e6cb-240">在內部網域的物件內引發網域事件時執行的交易，但是，這是透明化的命令處理常式的觀點。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-240">Internally within the domain objects, raise domain events while the transaction is executed, but that is transparent from a command handler point of view.</span></span>

-   <span data-ttu-id="8e6cb-241">如果成功的彙總作業結果和在交易完成之後，會引發整合事件命令處理常式。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-241">If the aggregate’s operation result is successful and after the transaction is finished, raise integration events command handler.</span></span> <span data-ttu-id="8e6cb-242">（這些可能也會引發由像儲存機制的基礎結構類別。）</span><span class="sxs-lookup"><span data-stu-id="8e6cb-242">(These might also be raised by infrastructure classes like repositories.)</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="8e6cb-243">其他資源</span><span class="sxs-lookup"><span data-stu-id="8e6cb-243">Additional resources</span></span>

-   <span data-ttu-id="8e6cb-244">**標記 Seemann。在界限，應用程式是不是物件導向**
    [*http://blog.ploeh.dk/2011/05/31/AttheBoundaries，ApplicationsareNotObject 導向 /*](http://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/)</span><span class="sxs-lookup"><span data-stu-id="8e6cb-244">**Mark Seemann. At the Boundaries, Applications are Not Object-Oriented**
[*http://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/*](http://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/)</span></span>

-   <span data-ttu-id="8e6cb-245">**命令和事件**
    [*http://cqrs.nu/Faq/commands-and-events*](http://cqrs.nu/Faq/commands-and-events)</span><span class="sxs-lookup"><span data-stu-id="8e6cb-245">**Commands and events**
[*http://cqrs.nu/Faq/commands-and-events*](http://cqrs.nu/Faq/commands-and-events)</span></span>

-   <span data-ttu-id="8e6cb-246">**命令處理常式有何作用？** 
     [ *http://cqrs.nu/Faq/command-handlers*](http://cqrs.nu/Faq/command-handlers)</span><span class="sxs-lookup"><span data-stu-id="8e6cb-246">**What does a command handler do?**
[*http://cqrs.nu/Faq/command-handlers*](http://cqrs.nu/Faq/command-handlers)</span></span>

-   <span data-ttu-id="8e6cb-247">**Jimmy Bogard：網域命令模式 – 處理常式**
    [*https://jimmybogard.com/domain-command-patterns-handlers/*](https://jimmybogard.com/domain-command-patterns-handlers/)</span><span class="sxs-lookup"><span data-stu-id="8e6cb-247">**Jimmy Bogard. Domain Command Patterns – Handlers**
[*https://jimmybogard.com/domain-command-patterns-handlers/*](https://jimmybogard.com/domain-command-patterns-handlers/)</span></span>

-   <span data-ttu-id="8e6cb-248">**Jimmy Bogard：網域命令模式 – 驗證**
    [*https://jimmybogard.com/domain-command-patterns-validation/*](https://jimmybogard.com/domain-command-patterns-validation/)</span><span class="sxs-lookup"><span data-stu-id="8e6cb-248">**Jimmy Bogard. Domain Command Patterns – Validation**
[*https://jimmybogard.com/domain-command-patterns-validation/*](https://jimmybogard.com/domain-command-patterns-validation/)</span></span>

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a><span data-ttu-id="8e6cb-249">命令處理程序管線： 如何觸發命令處理常式</span><span class="sxs-lookup"><span data-stu-id="8e6cb-249">The Command process pipeline: how to trigger a command handler</span></span>

<span data-ttu-id="8e6cb-250">下一個問題是如何叫用的命令處理常式。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-250">The next question is how to invoke a command handler.</span></span> <span data-ttu-id="8e6cb-251">您可以手動呼叫從每個相關的 ASP.NET Core 控制站。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-251">You could manually call it from each related ASP.NET Core controller.</span></span> <span data-ttu-id="8e6cb-252">不過，方法會太結合，並不理想。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-252">However, that approach would be too coupled and is not ideal.</span></span>

<span data-ttu-id="8e6cb-253">其他兩個主要選項，也就是建議的選項，包括：</span><span class="sxs-lookup"><span data-stu-id="8e6cb-253">The other two main options, which are the recommended options, are:</span></span>

-   <span data-ttu-id="8e6cb-254">透過記憶體中的暫留處理器模式成品。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-254">Through an in-memory Mediator pattern artifact.</span></span>

-   <span data-ttu-id="8e6cb-255">使用非同步的訊息佇列，控制站和處理常式之間。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-255">With an asynchronous message queue, in between controllers and handlers.</span></span>

### <a name="using-the-mediator-pattern-in-memory-in-the-command-pipeline"></a><span data-ttu-id="8e6cb-256">在命令管線中使用的傳遞模式 （記憶體）</span><span class="sxs-lookup"><span data-stu-id="8e6cb-256">Using the Mediator pattern (in-memory) in the command pipeline</span></span>

<span data-ttu-id="8e6cb-257">所示圖 9-21，CQRS 方法在您使用智慧型物，類似於記憶體中匯流排，也就是聰明，可以重新導向至正確的命令處理常式根據 DTO 所接收之命令的類型。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-257">As shown in Figure 9-21, in a CQRS approach you use an intelligent mediator, similar to an in-memory bus, which is smart enough to redirect to the right command handler based on the type of the command or DTO being received.</span></span> <span data-ttu-id="8e6cb-258">元件之間的單一黑色箭號代表物件 （在許多情況下，插入透過 DI） 之間的相依性，使用相關的互動。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-258">The single black arrows between components represent the dependencies between objects (in many cases, injected through DI) with their related interactions.</span></span>

![](./media/image22.png)

<span data-ttu-id="8e6cb-259">**圖 9-21**。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-259">**Figure 9-21**.</span></span> <span data-ttu-id="8e6cb-260">在單一的 CQRS 微服務的過程中使用的暫留處理器模式</span><span class="sxs-lookup"><span data-stu-id="8e6cb-260">Using the Mediator pattern in process in a single CQRS microservice</span></span>

<span data-ttu-id="8e6cb-261">使用暫留處理器模式合理的原因是，在企業應用程式處理要求變得複雜。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-261">The reason that using the Mediator pattern makes sense is that in enterprise applications, the processing requests can get complicated.</span></span> <span data-ttu-id="8e6cb-262">要加入跨領域像記錄、 驗證、 稽核及安全性的考量中開啟的數目。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-262">You want to be able to add an open number of cross-cutting concerns like logging, validations, audit, and security.</span></span> <span data-ttu-id="8e6cb-263">在這些情況下，您可以依賴暫留處理器管線 (請參閱[暫留處理器模式](https://en.wikipedia.org/wiki/Mediator_pattern)) 提供方法，針對這些額外的行為或跨碼橫切入顧慮。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-263">In these cases, you can rely on a mediator pipeline (see [Mediator pattern](https://en.wikipedia.org/wiki/Mediator_pattern)) to provide a means for these extra behaviors or cross-cutting concerns.</span></span>

<span data-ttu-id="8e6cb-264">暫留處理器是封裝 「 如何 」 在此程序的物件： 它會協調執行根據狀態、 叫用方式是命令處理常式時，或裝載您提供給此處理常式。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-264">A mediator is an object that encapsulates the “how” of this process: it coordinates execution based on state, the way a command handler is invoked, or the payload you provide to the handler.</span></span> <span data-ttu-id="8e6cb-265">暫留處理器元件您可以使用套用跨碼橫切入顧慮集中式和透明的方式套用裝飾項目 (或[管線行為](https://github.com/jbogard/MediatR/wiki/Behaviors)自暫留處理器 v3)。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-265">With a mediator component you can apply cross-cutting concerns in a centralized and transparent way by applying decorators (or [pipeline behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) since Mediator v3).</span></span> <span data-ttu-id="8e6cb-266">(如需詳細資訊，請參閱[裝飾項目的模式](https://en.wikipedia.org/wiki/Decorator_pattern)。)</span><span class="sxs-lookup"><span data-stu-id="8e6cb-266">(For more information, see the [Decorator pattern](https://en.wikipedia.org/wiki/Decorator_pattern).)</span></span>

<span data-ttu-id="8e6cb-267">裝飾項目和表現方式，類似[外觀導向程式設計 (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming)、 僅套用至受暫留處理器元件的特定處理序管線。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-267">Decorators and behaviors are similar to [Aspect Oriented Programming (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming), only applied to a specific process pipeline managed by the mediator component.</span></span> <span data-ttu-id="8e6cb-268">會根據套用在 AOP 可實作跨碼橫切入顧慮方面*外觀 weavers*插入在編譯時期，或根據物件呼叫攔截。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-268">Aspects in AOP that implement cross-cutting concerns are applied based on *aspect weavers* injected at compilation time or based on object call interception.</span></span> <span data-ttu-id="8e6cb-269">這兩種典型的 AOP 方法有時稱為一樣"magic"，所以不容易看到 AOP 方式執行其工作。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-269">Both typical AOP approaches are sometimes said to work "like magic," because it is not easy to see how AOP does its work.</span></span> <span data-ttu-id="8e6cb-270">當處理嚴重的問題或 bug，AOP 很難進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-270">When dealing with serious issues or bugs, AOP can be difficult to debug.</span></span> <span data-ttu-id="8e6cb-271">相反地，這些裝飾項目/這些行為屬於明確和套用暫留處理器，內容中，才是偵錯更可預測且容易。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-271">On the other hand, these decorators/behaviors are explicit and applied only in the context of the mediator, so debugging is much more predictable and easy.</span></span>

<span data-ttu-id="8e6cb-272">例如，在排序微服務 eShopOnContainers，我們實作兩個範例裝飾項目， [LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs)類別和[ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs)類別。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-272">For example, in the eShopOnContainers ordering microservice, we implemented two sample decorators, a [LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs) class and a [ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs) class.</span></span> <span data-ttu-id="8e6cb-273">下一節中說明的 decorator 實作。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-273">The decorator’s implementation is explained in the next section.</span></span> <span data-ttu-id="8e6cb-274">請注意，在未來版本中，eShopOnContainers 會將移轉至[MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)並移至[行為](https://github.com/jbogard/MediatR/wiki/Behaviors)而不是使用裝飾項目。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-274">Note that in a future version, eShopOnContainers will migrate to [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) and move to [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) instead of using decorators.</span></span>

### <a name="using-message-queues-out-of-proc-in-the-commands-pipeline"></a><span data-ttu-id="8e6cb-275">在命令管線中使用訊息佇列 （跨處理序）</span><span class="sxs-lookup"><span data-stu-id="8e6cb-275">Using message queues (out-of-proc) in the command’s pipeline</span></span>

<span data-ttu-id="8e6cb-276">另一個選擇是使用非同步示圖 9-22，根據代理程式 」 或 「 訊息佇列的訊息。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-276">Another choice is to use asynchronous messages based on brokers or message queues, as shown in Figure 9-22.</span></span> <span data-ttu-id="8e6cb-277">該選項也可以結合的命令處理常式的權限之前，暫留處理器元件。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-277">That option could also be combined with the mediator component right before the command handler.</span></span>

![](./media/image23.png)

<span data-ttu-id="8e6cb-278">**圖 9 22**。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-278">**Figure 9-22**.</span></span> <span data-ttu-id="8e6cb-279">使用 CQRS 命令的訊息佇列 （現成可用的處理程序和處理序間通訊）</span><span class="sxs-lookup"><span data-stu-id="8e6cb-279">Using message queues (out of process and inter-process communication) with CQRS commands</span></span>

<span data-ttu-id="8e6cb-280">使用訊息佇列以接受命令可進一步複雜命令的管線，因為您可能需要將管線拆解成兩個處理序連接到外部訊息佇列。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-280">Using message queues to accept the commands can further complicate your command’s pipeline, because you will probably need to split the pipeline into two processes connected through the external message queue.</span></span> <span data-ttu-id="8e6cb-281">儘管如此，則應如果您需要已改善延展性和效能根據非同步訊息。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-281">Still, it should be used if you need to have improved scalability and performance based on asynchronous messaging.</span></span> <span data-ttu-id="8e6cb-282">請考慮在圖 9-22，控制器只會將命令訊息排入佇列，並傳回。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-282">Consider that in the case of Figure 9-22, the controller just posts the command message into the queue and returns.</span></span> <span data-ttu-id="8e6cb-283">然後命令處理常式會處理自己的步調的訊息。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-283">Then the command handlers process the messages at their own pace.</span></span> <span data-ttu-id="8e6cb-284">也就是最大佇列的好處，訊息佇列可以做為案例的緩衝區上，hyper-v 延展性時所需，例如股票或任何其他輸入資料量很高的案例中。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-284">That is a great benefit of queues—the message queue can act as a buffer in cases when hyper scalability is needed, such as for stocks or any other scenario with a high volume of ingress data.</span></span>

<span data-ttu-id="8e6cb-285">不過，由於訊息佇列的非同步本質，您需要找出有關成功或失敗的命令的處理序用戶端應用程式的通訊方式。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-285">However, because of the asynchronous nature of message queues, you need to figure out how to communicate with the client application about the success or failure of the command’s process.</span></span> <span data-ttu-id="8e6cb-286">一般而言，您應該永遠不會使用"fire and forget"命令。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-286">As a rule, you should never use “fire and forget” commands.</span></span> <span data-ttu-id="8e6cb-287">每個商務應用程式必須知道是否命令已處理成功，或至少驗證和接受。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-287">Every business application needs to know if a command was processed successfully, or at least validated and accepted.</span></span>

<span data-ttu-id="8e6cb-288">因此，能夠以回應至用戶端驗證命令訊息送出至非同步的佇列之後會增加複雜性您的系統，相較於同處理序的命令處理程序執行交易後傳回作業的結果。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-288">Thus, being able to respond to the client after validating a command message that was submitted to an asynchronous queue adds complexity to your system, as compared to an in-process command process that returns the operation’s result after running the transaction.</span></span> <span data-ttu-id="8e6cb-289">使用佇列，您可能需要返回命令處理，透過其他作業結果訊息，就會需要額外的元件和自訂通訊系統中的結果。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-289">Using queues, you might need to return the result of the command process through other operation result messages, which will require additional components and custom communication in your system.</span></span>

<span data-ttu-id="8e6cb-290">此外，非同步命令是單向的命令，這在許多情況下可能不需要如下列的有趣 exchange Burtsev Alexey 之間 Greg Young 中所述[線上交談](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):</span><span class="sxs-lookup"><span data-stu-id="8e6cb-290">Additionally, async commands are one-way commands, which in many cases might not be needed, as is explained in the following interesting exchange between Burtsev Alexey and Greg Young in an [online conversation](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):</span></span>

<span data-ttu-id="8e6cb-291">\[Burtsev Alexey\]找到許多程式碼的人，使用非同步命令處理或訊息沒有任何原因，若要這樣做的其中一種方式命令 （它們不會進行某些長時間作業，它們不會執行外部非同步程式碼，它們不甚至會跨越應用程式界限是使用訊息匯流排）。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-291">\[Burtsev Alexey\] I find lots of code where people use async command handling or one way command messaging without any reason to do so (they are not doing some long operation, they are not executing external async code, they do not even cross application boundary to be using message bus).</span></span> <span data-ttu-id="8e6cb-292">這些原因會造成這種不必要的複雜性？</span><span class="sxs-lookup"><span data-stu-id="8e6cb-292">Why do they introduce this unnecessary complexity?</span></span> <span data-ttu-id="8e6cb-293">事實上，我還沒看過 CQRS 為止，封鎖命令處理常式程式碼範例雖然它會在大部分情況下正常運作。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-293">And actually, I haven't seen a CQRS code example with blocking command handlers so far, though it will work just fine in most cases.</span></span>

<span data-ttu-id="8e6cb-294">\[Greg Young\] \[...\]非同步命令不存在，則可以實際另一個事件。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-294">\[Greg Young\] \[...\] an asynchronous command doesn't exist; it's actually another event.</span></span> <span data-ttu-id="8e6cb-295">如果我必須接受您傳送給我，並引發事件，如果我不同意，就無法再您告訴我執行一些動作。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-295">If I must accept what you send me and raise an event if I disagree, it's no longer you telling me to do something.</span></span> <span data-ttu-id="8e6cb-296">它是您告知我已完成的項目。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-296">It's you telling me something has been done.</span></span> <span data-ttu-id="8e6cb-297">這看起來像是在一開始，有些微的差異，但有許多影響。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-297">This seems like a slight difference at first, but it has many implications.</span></span>

<span data-ttu-id="8e6cb-298">非同步命令會大幅增加系統的複雜性，因為沒有任何簡易方式可表示失敗。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-298">Asynchronous commands greatly increase the complexity of a system, because there is no simple way to indicate failures.</span></span> <span data-ttu-id="8e6cb-299">因此，非同步命令不建議您使用以外需要調整需求時，或在特殊情況下通訊透過訊息內部的 microservices 時。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-299">Therefore, asynchronous commands are not recommended other than when scaling requirements are needed or in special cases when communicating the internal microservices through messaging.</span></span> <span data-ttu-id="8e6cb-300">在這些情況下，您必須設計個別的報告和復原系統失敗。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-300">In those cases, you must design a separate reporting and recovery system for failures.</span></span>

<span data-ttu-id="8e6cb-301">在 eShopOnContainers 初始版本中，我們決定將使用同步命令處理，從 HTTP 要求啟動和暫留處理器模式所驅動。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-301">In the initial version of eShopOnContainers, we decided to use synchronous command processing, started from HTTP requests and driven by the Mediator pattern.</span></span> <span data-ttu-id="8e6cb-302">可輕鬆地讓您傳回成功或失敗的處理程序中[CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs)實作。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-302">That easily allows you to return the success or failure of the process, as in the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) implementation.</span></span>

<span data-ttu-id="8e6cb-303">在任何情況下，這應該是根據您應用程式 」 或 「 微服務的業務決策。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-303">In any case, this should be a decision based on your application’s or microservice’s business requirements.</span></span>

## <a name="implementing-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a><span data-ttu-id="8e6cb-304">實作命令處理程序管線，與傳遞模式 (MediatR)</span><span class="sxs-lookup"><span data-stu-id="8e6cb-304">Implementing the command process pipeline with a mediator pattern (MediatR)</span></span>

<span data-ttu-id="8e6cb-305">當做範例實作，本指南所建議使用同處理序管線根據磁碟機命令擷取的暫留處理器模式和路由，在記憶體中，加入正確的命令處理常式。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-305">As a sample implementation, this guide proposes using the in-process pipeline based on the Mediator pattern to drive command ingestion and routing them, in memory, to the right command handlers.</span></span> <span data-ttu-id="8e6cb-306">本指南也建議套用裝飾項目或[行為](https://github.com/jbogard/MediatR/wiki/Behaviors)以便將跨領域重點分開。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-306">The guide also proposes applying decorators or [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) in order to separate cross-cutting concerns.</span></span>

<span data-ttu-id="8e6cb-307">如需在.NET Core 的實作，有多個開放原始碼程式庫提供實作暫留處理器模式。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-307">For implementation in .NET Core, there are multiple open-source libraries available that implement the Mediator pattern.</span></span> <span data-ttu-id="8e6cb-308">使用本指南中的程式庫是[MediatR](https://github.com/jbogard/MediatR)開放原始碼程式庫 （Jimmy Bogard 所建立），但是您無法使用另一種方法。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-308">The library used in this guide is the [MediatR](https://github.com/jbogard/MediatR) open-source library (created by Jimmy Bogard), but you could use another approach.</span></span> <span data-ttu-id="8e6cb-309">MediatR 是小型且簡單的程式庫，可讓您處理命令，例如，記憶體中訊息時套用裝飾項目或行為。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-309">MediatR is a small and simple library that allows you to process in-memory messages like a command, while applying decorators or behaviors.</span></span>

<span data-ttu-id="8e6cb-310">使用暫留處理器模式可協助您減少結合，並找出要求的工作，自動連接到執行該工作的處理常式時的考量，在此情況下，加入命令處理常式。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-310">Using the Mediator pattern helps you to reduce coupling and to isolate the concerns of the requested work, while automatically connecting to the handler that performs that work—in this case, to command handlers.</span></span>

<span data-ttu-id="8e6cb-311">檢閱本指南時，已由 Jimmy Bogard 說明另一個使用暫留處理器模式的好理由：</span><span class="sxs-lookup"><span data-stu-id="8e6cb-311">Another good reason to use the Mediator pattern was explained by Jimmy Bogard when reviewing this guide:</span></span>

<span data-ttu-id="8e6cb-312">我認為值得您注意以下測試可能是 – 不錯的一致視窗提供到您的系統行為。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-312">I think it might be worth mentioning testing here – it provides a nice consistent window into the behavior of your system.</span></span> <span data-ttu-id="8e6cb-313">要求中，回應外。我們找到這個部分中建置以一致的方式運作的測試很有價值。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-313">Request-in, response-out. We’ve found that aspect quite valuable in building consistently behaving tests.</span></span>

<span data-ttu-id="8e6cb-314">首先，讓我們看控制器程式碼，您實際上會使用暫留處理器物件。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-314">First, let us take a look to the controller code where you actually would use the mediator object.</span></span> <span data-ttu-id="8e6cb-315">如果您不使用暫留處理器物件，您必須將所有的相依性該控制站，例如記錄器物件與其他人。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-315">If you were not using the mediator object, you would need to inject all the dependencies for that controller, things like a logger object and others.</span></span> <span data-ttu-id="8e6cb-316">因此，建構函式會變得相當複雜。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-316">Therefore, the constructor would be quite complicated.</span></span> <span data-ttu-id="8e6cb-317">相反地，如果您使用的暫留處理器物件，您的控制站的建構函式可以是簡單許多，具有少數的相依性，而不是，如果您在其中每個跨領域作業，如下列範例所示，您會有許多相依性：</span><span class="sxs-lookup"><span data-stu-id="8e6cb-317">On the other hand, if you use the mediator object, the constructor of your controller can be a lot simpler, with just a few dependencies instead of many dependencies that you would have if you had one per cross-cutting operation, as in the following example:</span></span>

```csharp
public class OrdersController : Controller
{
    public OrdersController(IMediator mediator,
        IOrderQueries orderQueries)
    // ...
```

<span data-ttu-id="8e6cb-318">您可以看到暫留處理器提供全新和簡式 Web API 控制器建構函式。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-318">You can see that the mediator provides a clean and lean Web API controller constructor.</span></span> <span data-ttu-id="8e6cb-319">此外，在控制器方法中，將命令傳送到的暫留處理器物件的程式碼會幾乎一行：</span><span class="sxs-lookup"><span data-stu-id="8e6cb-319">In addition, within the controller methods, the code to send a command to the mediator object is almost one line:</span></span>

```csharp
[Route("new")]
[HttpPost]
public async Task<IActionResult> CreateOrder([FromBody]CreateOrderCommand
    createOrderCommand)
{
    var commandResult = await _mediator.SendAsync(createOrderCommand);
    return commandResult ? (IActionResult)Ok() : (IActionResult)BadRequest();
}
```

<span data-ttu-id="8e6cb-320">為了讓 MediatR 知道您的命令處理常式類別，您需要註冊 IoC 容器中的暫留處理器類別和命令處理常式類別。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-320">In order for MediatR to be aware of your command handler classes, you need to register the mediator classes and the command handler classes in your IoC container.</span></span> <span data-ttu-id="8e6cb-321">根據預設，MediatR 使用 Autofac 與 IoC 容器，但是您也可以使用內建 ASP.NET Core IoC 容器或 MediatR 所支援的其他任何容器。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-321">By default, MediatR uses Autofac as the IoC container, but you can also use the built-in ASP.NET Core IoC container or any other container supported by MediatR.</span></span>

<span data-ttu-id="8e6cb-322">下列程式碼會示範如何使用 Autofac 模組時，註冊暫留處理器的類型和命令。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-322">The following code shows how to register Mediator’s types and commands when using Autofac modules.</span></span>

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();
        builder.RegisterAssemblyTypes(typeof(CreateOrderCommand)
            .GetTypeInfo().Assembly)
            .As(o => o.GetInterfaces()
            .Where(i => i.IsClosedTypeOf(typeof(IAsyncRequestHandler<,>)))
            .Select(i => new KeyedService("IAsyncRequestHandler", i)));
        builder.RegisterGenericDecorator(typeof(LogDecorator<,>),
            typeof(IAsyncRequestHandler<,>), "IAsyncRequestHandler");

        // Other types registration
    }
}
```

<span data-ttu-id="8e6cb-323">因為每個命令處理常式實作具有泛型 IAsyncRequestHandler 介面&lt;T&gt;並接著檢查 RegisteredAssemblyTypes 物件，因為在處理常式所能夠與使用其命令處理常式中，每個命令，關聯性所述的 CommandHandler 類別，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8e6cb-323">Because each command handler implements the interface with generic IAsyncRequestHandler&lt;T&gt; and then inspects the RegisteredAssemblyTypes object, the handler is able to relate each command with its command handler, because that relationship is stated in the CommandHandler class, as in the following example:</span></span>

```csharp
public class CreateOrderCommandHandler
  : IAsyncRequestHandler<CreateOrderCommand, bool>
{
```

<span data-ttu-id="8e6cb-324">這是與命令相關聯的命令處理常式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-324">This is the code that correlates commands with command handlers.</span></span> <span data-ttu-id="8e6cb-325">此處理常式是只簡單的類別，但它繼承自 RequestHandler&lt;T&gt;，並且 MediatR 讓它取得用來叫用正確的裝載。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-325">The handler is just a simple class, but it inherits from RequestHandler&lt;T&gt;, and MediatR makes sure it gets invoked with the correct payload.</span></span>

## <a name="applying-cross-cutting-concerns-when-processing-commands-with-the-mediator-and-decorator-patterns"></a><span data-ttu-id="8e6cb-326">處理具有暫留處理器和裝飾項目模式的命令時，套用交互碼橫切入顧慮</span><span class="sxs-lookup"><span data-stu-id="8e6cb-326">Applying cross-cutting concerns when processing commands with the Mediator and Decorator patterns</span></span>

<span data-ttu-id="8e6cb-327">沒有一件事： 無法暫留處理器管線套用跨碼橫切入顧慮。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-327">There is one more thing: being able to apply cross-cutting concerns to the mediator pipeline.</span></span> <span data-ttu-id="8e6cb-328">您也可以查看 Autofac 註冊模組程式碼的結尾如何註冊裝飾項目類型，具體來說，自訂 LogDecorator 類別。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-328">You can also see at the end of the Autofac registration module code how it is registering a decorator type, specifically, a custom LogDecorator class.</span></span>

<span data-ttu-id="8e6cb-329">同樣地，請注意，未來版本的 eShopOnContainers 它會將移轉至[MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)並移至[行為](https://github.com/jbogard/MediatR/wiki/Behaviors)而不是使用裝飾項目。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-329">Again, note that a future version of eShopOnContainers it will migrate to [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) and move to [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) instead of using decorators.</span></span>

<span data-ttu-id="8e6cb-330">確認[LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs)類別可以實作下列程式碼記錄正在執行的命令處理常式以及它是否成功與否的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-330">That [LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs) class can be implemented as the following code, which logs information about the command handler being executed and whether it was successful or not.</span></span>

```csharp
public class LogDecorator<TRequest, TResponse>
    : IAsyncRequestHandler<TRequest, TResponse>
    where TRequest : IAsyncRequest<TResponse>
{
    private readonly IAsyncRequestHandler<TRequest, TResponse> _inner;
    private readonly ILogger<LogDecorator<TRequest, TResponse>> _logger;

    public LogDecorator(
        IAsyncRequestHandler<TRequest, TResponse> inner,
        ILogger<LogDecorator<TRequest, TResponse>> logger)
    {
        _inner = inner;
        _logger = logger;
    }

    public async Task<TResponse> Handle(TRequest message)
    {
        _logger.LogInformation($"Executing command {_inner.GetType().FullName}");
        var response = await _inner.Handle(message);
        _logger.LogInformation($"Succeeded executed command{_inner.GetType().FullName}");
        return response;
    }
}
```

<span data-ttu-id="8e6cb-331">只要實作這個裝飾項目類別，而它使用管線將透過 MediatR 處理的所有命令將會都記錄執行的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-331">Just by implementing this decorator class and by decorating the pipeline with it, all the commands processed through MediatR will be logging information about the execution.</span></span>

<span data-ttu-id="8e6cb-332">排序微服務 」 也適用於針對基本驗證，第二個 decorator eShopOnContainers [ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs)類別依賴[FluentValidation](https://github.com/JeremySkinner/FluentValidation)程式庫中所示下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="8e6cb-332">The eShopOnContainers ordering microservice also applies a second decorator for basic validations, the [ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs) class that relies on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, as shown in the following code:</span></span>

```csharp
public class ValidatorDecorator<TRequest, TResponse>
    : IAsyncRequestHandler<TRequest, TResponse>
    where TRequest : IAsyncRequest<TResponse>
{
    private readonly IAsyncRequestHandler<TRequest, TResponse> _inner;
    private readonly IValidator<TRequest>[] _validators;

    public ValidatorDecorator(
        IAsyncRequestHandler<TRequest, TResponse> inner,
        IValidator<TRequest>[] validators)
    {
        _inner = inner;
        _validators = validators;
    }

    public async Task<TResponse> Handle(TRequest message)
    {
        var failures = _validators
            .Select(v => v.Validate(message))
            .SelectMany(result => result.Errors)
            .Where(error => error != null)
            .ToList();
            if (failures.Any())
            {
                throw new OrderingDomainException(
                $"Command Validation Errors for type {typeof(TRequest).Name}",
                new ValidationException("Validation exception", failures));
            }
            var response = await _inner.Handle(message);
        return response;
    }
}
```

<span data-ttu-id="8e6cb-333">然後，根據[FluentValidation](https://github.com/JeremySkinner/FluentValidation)程式庫，我們建立驗證資料隨 CreateOrderCommand，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="8e6cb-333">Then, based on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, we created validation for the data passed with CreateOrderCommand, as in the following code:</span></span>

```csharp
public class CreateOrderCommandValidator : AbstractValidator<CreateOrderCommand>
{
    public CreateOrderCommandValidator()
    {
        RuleFor(command => command.City).NotEmpty();
        RuleFor(command => command.Street).NotEmpty();
        RuleFor(command => command.State).NotEmpty();
        RuleFor(command => command.Country).NotEmpty();
        RuleFor(command => command.ZipCode).NotEmpty();
        RuleFor(command => command.CardNumber).NotEmpty().Length(12, 19);
        RuleFor(command => command.CardHolderName).NotEmpty();
        RuleFor(command => command.CardExpiration).NotEmpty().Must(BeValidExpirationDate).
            WithMessage("Please specify a valid card expiration date");
        RuleFor(command => command.CardSecurityNumber).NotEmpty().Length(3);
        RuleFor(command => command.CardTypeId).NotEmpty();
        RuleFor(command => command.OrderItems).
            Must(ContainOrderItems).WithMessage("No order items found");
    }

    private bool BeValidExpirationDate(DateTime dateTime)
    {
        return dateTime >= DateTime.UtcNow;
    }

    private bool ContainOrderItems(IEnumerable<OrderItemDTO> orderItems)
    {
        return orderItems.Any();
    }
}
```

<span data-ttu-id="8e6cb-334">您可以建立額外的驗證。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-334">You could create additional validations.</span></span> <span data-ttu-id="8e6cb-335">這是非常簡潔且更簡潔的方式來實作命令驗證。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-335">This is a very clean and elegant way to implement your command validations.</span></span>

<span data-ttu-id="8e6cb-336">類似的方式，您可以實作其他裝飾項目，其他部分為跨領域考量您想要處理它們時，套用至命令。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-336">In a similar way, you could implement other decorators for additional aspects or cross-cutting concerns that you want to apply to commands when handling them.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="8e6cb-337">其他資源</span><span class="sxs-lookup"><span data-stu-id="8e6cb-337">Additional resources</span></span>

##### <a name="the-mediator-pattern"></a><span data-ttu-id="8e6cb-338">暫留處理器模式</span><span class="sxs-lookup"><span data-stu-id="8e6cb-338">The mediator pattern</span></span>

-   <span data-ttu-id="8e6cb-339">**暫留處理器模式**
    [*https://en.wikipedia.org/wiki/Mediator\_模式*](https://en.wikipedia.org/wiki/Mediator_pattern)</span><span class="sxs-lookup"><span data-stu-id="8e6cb-339">**Mediator pattern**
[*https://en.wikipedia.org/wiki/Mediator\_pattern*](https://en.wikipedia.org/wiki/Mediator_pattern)</span></span>

##### <a name="the-decorator-pattern"></a><span data-ttu-id="8e6cb-340">裝飾項目模式</span><span class="sxs-lookup"><span data-stu-id="8e6cb-340">The decorator pattern</span></span>

-   <span data-ttu-id="8e6cb-341">**裝飾項目模式**
    [*https://en.wikipedia.org/wiki/Decorator\_模式*](https://en.wikipedia.org/wiki/Decorator_pattern)</span><span class="sxs-lookup"><span data-stu-id="8e6cb-341">**Decorator pattern**
[*https://en.wikipedia.org/wiki/Decorator\_pattern*](https://en.wikipedia.org/wiki/Decorator_pattern)</span></span>

##### <a name="mediatr-jimmy-bogard"></a><span data-ttu-id="8e6cb-342">MediatR (Jimmy Bogard)</span><span class="sxs-lookup"><span data-stu-id="8e6cb-342">MediatR (Jimmy Bogard)</span></span>

-   <span data-ttu-id="8e6cb-343">**MediatR。**</span><span class="sxs-lookup"><span data-stu-id="8e6cb-343">**MediatR.**</span></span> <span data-ttu-id="8e6cb-344">GitHub 儲存機制。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-344">GitHub repo.</span></span>
    [<span data-ttu-id="8e6cb-345">*https://github.com/jbogard/MediatR*</span><span class="sxs-lookup"><span data-stu-id="8e6cb-345">*https://github.com/jbogard/MediatR*</span></span>](https://github.com/jbogard/MediatR)

-   <span data-ttu-id="8e6cb-346">**CQRS MediatR 與 AutoMapper**
    [*https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/*](https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/)</span><span class="sxs-lookup"><span data-stu-id="8e6cb-346">**CQRS with MediatR and AutoMapper**
[*https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/*](https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/)</span></span>

-   <span data-ttu-id="8e6cb-347">**將您的控制站上食物： 文章和命令。** 
     [ *https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/*](https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/)</span><span class="sxs-lookup"><span data-stu-id="8e6cb-347">**Put your controllers on a diet: POSTs and commands.**
[*https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/*](https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/)</span></span>

-   <span data-ttu-id="8e6cb-348">**處理跨領域顧慮暫留處理器管線**
    [*https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/*](https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/)</span><span class="sxs-lookup"><span data-stu-id="8e6cb-348">**Tackling cross-cutting concerns with a mediator pipeline**
[*https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/*](https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/)</span></span>

-   <span data-ttu-id="8e6cb-349">**CQRS 和 REST： 完美的相符項**
    [*https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/*](https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/)</span><span class="sxs-lookup"><span data-stu-id="8e6cb-349">**CQRS and REST: the perfect match**
[*https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/*](https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/)</span></span>

-   <span data-ttu-id="8e6cb-350">**MediatR 管線範例**
    [*https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/*](https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/)</span><span class="sxs-lookup"><span data-stu-id="8e6cb-350">**MediatR Pipeline Examples**
[*https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/*](https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/)</span></span>

-   <span data-ttu-id="8e6cb-351">**垂直配量測試設備 MediatR 和 ASP.NET Core**
    *<https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/>*</span><span class="sxs-lookup"><span data-stu-id="8e6cb-351">**Vertical Slice Test Fixtures for MediatR and ASP.NET Core**
*<https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/> *</span></span>

-   <span data-ttu-id="8e6cb-352">**Microsoft 相依性插入發行 MediatR 延伸**
    [*https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/*](https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/)</span><span class="sxs-lookup"><span data-stu-id="8e6cb-352">**MediatR Extensions for Microsoft Dependency Injection Released**
[*https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/*](https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/)</span></span>

##### <a name="fluent-validation"></a><span data-ttu-id="8e6cb-353">Fluent 應用程式開發的驗證</span><span class="sxs-lookup"><span data-stu-id="8e6cb-353">Fluent validation</span></span>

-   <span data-ttu-id="8e6cb-354">**Jeremy Skinner。FluentValidation。**</span><span class="sxs-lookup"><span data-stu-id="8e6cb-354">**Jeremy Skinner. FluentValidation.**</span></span> <span data-ttu-id="8e6cb-355">GitHub 儲存機制。</span><span class="sxs-lookup"><span data-stu-id="8e6cb-355">GitHub repo.</span></span>
    [<span data-ttu-id="8e6cb-356">*https://github.com/JeremySkinner/FluentValidation*</span><span class="sxs-lookup"><span data-stu-id="8e6cb-356">*https://github.com/JeremySkinner/FluentValidation*</span></span>](https://github.com/JeremySkinner/FluentValidation)

>[!div class="step-by-step"]
<span data-ttu-id="8e6cb-357">[上一個](microservice-application-layer-web-api-design.md) [下一步] (.../implement-resilient-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="8e6cb-357">[Previous] (microservice-application-layer-web-api-design.md) [Next] (../implement-resilient-applications/index.md)</span></span>
