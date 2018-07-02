---
title: 使用 Web API 實作微服務應用程式層
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 使用 Web API 實作微服務應用程式層
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.openlocfilehash: 1af8d0290eea26d57f4744bbd6d9819d886d4db4
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106550"
---
# <a name="implementing-the-microservice-application-layer-using-the-web-api"></a><span data-ttu-id="cdb17-103">使用 Web API 實作微服務應用程式層</span><span class="sxs-lookup"><span data-stu-id="cdb17-103">Implementing the microservice application layer using the Web API</span></span>

## <a name="using-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a><span data-ttu-id="cdb17-104">使用相依性插入將基礎結構物件插入至應用程式層</span><span class="sxs-lookup"><span data-stu-id="cdb17-104">Using Dependency Injection to inject infrastructure objects into your application layer</span></span>

<span data-ttu-id="cdb17-105">如前所述，應用程式層可以實作為所建置成品的一部分，例如在 Web API 專案或 MVC Web 應用程式專案內。</span><span class="sxs-lookup"><span data-stu-id="cdb17-105">As mentioned previously, the application layer can be implemented as part of the artifact you are building, such as within a Web API project or an MVC web app project.</span></span> <span data-ttu-id="cdb17-106">如果是使用 ASP.NET Core 所建置的微服務，則應用程式層通常會是 Web API 程式庫。</span><span class="sxs-lookup"><span data-stu-id="cdb17-106">In the case of a microservice built with ASP.NET Core, the application layer will usually be your Web API library.</span></span> <span data-ttu-id="cdb17-107">如果您想要區隔來自 ASP.NET Core 的內容 (其基礎結構和您的控制站) 與自訂應用程式層程式碼，則也可以將應用程式層放在個別的類別庫中，但這是選擇性。</span><span class="sxs-lookup"><span data-stu-id="cdb17-107">If you want to separate what is coming from ASP.NET Core (its infrastructure plus your controllers) from your custom application layer code, you could also place your application layer in a separate class library, but that is optional.</span></span>

<span data-ttu-id="cdb17-108">例如，訂購微服務的應用程式層程式碼直接實作為 **Ordering.API** 專案 (ASP.NET Core Web API 專案) 的一部分，如圖 9-23 所示。</span><span class="sxs-lookup"><span data-stu-id="cdb17-108">For instance, the application layer code of the ordering microservice is directly implemented as part of the **Ordering.API** project (an ASP.NET Core Web API project), as shown in Figure 9-23.</span></span>

![](./media/image20.png)

<span data-ttu-id="cdb17-109">**圖 9-23**.</span><span class="sxs-lookup"><span data-stu-id="cdb17-109">**Figure 9-23**.</span></span> <span data-ttu-id="cdb17-110">Ordering.API ASP.NET Core Web API 專案中的應用程式層</span><span class="sxs-lookup"><span data-stu-id="cdb17-110">The application layer in the Ordering.API ASP.NET Core Web API project</span></span>

<span data-ttu-id="cdb17-111">ASP.NET Core 包含簡單[內建 IoC 容器](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (由 IServiceProvider 介面代表)，它預設會支援建構函式插入，ASP.NET 則是透過 DI 提供特定服務。</span><span class="sxs-lookup"><span data-stu-id="cdb17-111">ASP.NET Core includes a simple [built-in IoC container](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (represented by the IServiceProvider interface) that supports constructor injection by default, and ASP.NET makes certain services available through DI.</span></span> <span data-ttu-id="cdb17-112">ASP.NET Core 會將「服務」詞彙用於透過 DI 插入的任何已註冊類型。</span><span class="sxs-lookup"><span data-stu-id="cdb17-112">ASP.NET Core uses the term *service* for any of the types you register that will be injected through DI.</span></span> <span data-ttu-id="cdb17-113">您可以在應用程式 Startup 類別的 ConfigureServices 方法中設定內建容器服務。</span><span class="sxs-lookup"><span data-stu-id="cdb17-113">You configure the built-in container's services in the ConfigureServices method in your application's Startup class.</span></span> <span data-ttu-id="cdb17-114">相依性是在類型所需的服務中實作。</span><span class="sxs-lookup"><span data-stu-id="cdb17-114">Your dependencies are implemented in the services that a type needs.</span></span>

<span data-ttu-id="cdb17-115">一般而言，您會想要插入可實作基礎結構物件的相依性。</span><span class="sxs-lookup"><span data-stu-id="cdb17-115">Typically, you want to inject dependencies that implement infrastructure objects.</span></span> <span data-ttu-id="cdb17-116">要插入的極典型相依性是存放庫。</span><span class="sxs-lookup"><span data-stu-id="cdb17-116">A very typical dependency to inject is a repository.</span></span> <span data-ttu-id="cdb17-117">但是，您可以插入可能會有的任何其他基礎結構相依性。</span><span class="sxs-lookup"><span data-stu-id="cdb17-117">But you could inject any other infrastructure dependency that you may have.</span></span> <span data-ttu-id="cdb17-118">為求更簡單的實作，您可以直接插入工作單元模式物件 (EF DbContext 物件)，因為 DBContext 也是您基礎結構持續性物件的實作。</span><span class="sxs-lookup"><span data-stu-id="cdb17-118">For simpler implementations, you could directly inject your Unit of Work pattern object (the EF DbContext object), because the DBContext is also the implementation of your infrastructure persistence objects.</span></span>

<span data-ttu-id="cdb17-119">在下列範例中，您可以查看 .NET Core 如何透過建構函式插入所需的存放庫物件。</span><span class="sxs-lookup"><span data-stu-id="cdb17-119">In the following example, you can see how .NET Core is injecting the required repository objects through the constructor.</span></span> <span data-ttu-id="cdb17-120">此類別是命令處理常式，我們將在下節中討論。</span><span class="sxs-lookup"><span data-stu-id="cdb17-120">The class is a command handler, which we will cover in the next section.</span></span>

```csharp
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator, 
                                     IOrderRepository orderRepository, 
                                     IIdentityService identityService)
    {
        _orderRepository = orderRepository ?? 
                          throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ?? 
                          throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ?? 
                                 throw new ArgumentNullException(nameof(mediator));
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        // Create the Order AggregateRoot
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic 
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State, 
                                  message.Country, message.ZipCode);
        var order = new Order(message.UserId, address, message.CardTypeId, 
                              message.CardNumber, message.CardSecurityNumber, 
                              message.CardHolderName, message.CardExpiration);
            
        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                               item.Discount, item.PictureUrl, item.Units);
        }

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
    }
}
```

<span data-ttu-id="cdb17-121">此類別會使用已插入的存放庫來執行交易，並持續保存狀態變更。</span><span class="sxs-lookup"><span data-stu-id="cdb17-121">The class uses the injected repositories to execute the transaction and persist the state changes.</span></span> <span data-ttu-id="cdb17-122">不論該類別是命令處理常式、ASP.NET Core Web API 控制器方法還是 [DDD 應用程式服務](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/)。</span><span class="sxs-lookup"><span data-stu-id="cdb17-122">It does not matter whether that class is a command handler, an ASP.NET Core Web API controller method, or a [DDD Application Service](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/).</span></span> <span data-ttu-id="cdb17-123">它最終會是使用存放庫、領域實體和其他應用程式協調的簡單類別，其形式與命令處理常式類似。</span><span class="sxs-lookup"><span data-stu-id="cdb17-123">It is ultimately a simple class that uses repositories, domain entities, and other application coordination in a fashion similar to a command handler.</span></span> <span data-ttu-id="cdb17-124">所有提及類別的相依性插入運作方式都相同，如根據建構函式使用 DI 的範例所示。</span><span class="sxs-lookup"><span data-stu-id="cdb17-124">Dependency Injection works the same way for all the mentioned classes, as in the example using DI based on the constructor.</span></span>

### <a name="registering-the-dependency-implementation-types-and-interfaces-or-abstractions"></a><span data-ttu-id="cdb17-125">註冊相依性實作類型和介面或抽象物件</span><span class="sxs-lookup"><span data-stu-id="cdb17-125">Registering the dependency implementation types and interfaces or abstractions</span></span>

<span data-ttu-id="cdb17-126">您需要先知道在哪裡註冊介面和類別，以產生透過 DI 插入至 應用程式類別的物件，才能使用透過建構函式所插入的物件 </span><span class="sxs-lookup"><span data-stu-id="cdb17-126">Before you use the objects injected through constructors, you need to know where to register the interfaces and classes that produce the objects injected into your application classes through DI.</span></span> <span data-ttu-id="cdb17-127">(例如根據建構函式的 DI，如前所述)。</span><span class="sxs-lookup"><span data-stu-id="cdb17-127">(Like DI based on the constructor, as shown previously.)</span></span>

#### <a name="using-the-built-in-ioc-container-provided-by-aspnet-core"></a><span data-ttu-id="cdb17-128">使用 ASP.NET Core 所提供的內建 IoC 容器</span><span class="sxs-lookup"><span data-stu-id="cdb17-128">Using the built-in IoC container provided by ASP.NET Core</span></span>

<span data-ttu-id="cdb17-129">當您使用 ASP.NET Core 所提供的內建 IoC 容器時，會註冊您想要在 Startup.cs 檔案的 ConfigureServices 方法中插入的類型，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="cdb17-129">When you use the built-in IoC container provided by ASP.NET Core, you register the types you want to inject in the ConfigureServices method in the Startup.cs file, as in the following code:</span></span>

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

<span data-ttu-id="cdb17-130">在 IoC 容器中註冊類型時的最常見模式是註冊一組類型：介面和其相關實作類別。</span><span class="sxs-lookup"><span data-stu-id="cdb17-130">The most common pattern when registering types in an IoC container is to register a pair of types—an interface and its related implementation class.</span></span> <span data-ttu-id="cdb17-131">然後，當您透過任何建構函式從 IoC 容器要求物件時，會要求特定類型之介面的物件。</span><span class="sxs-lookup"><span data-stu-id="cdb17-131">Then when you request an object from the IoC container through any constructor, you request an object of a certain type of interface.</span></span> <span data-ttu-id="cdb17-132">例如，在上述範例中，最後一行指出有任何建構函式與 IMyCustomRepository (介面或抽象) 相依時，IoC 容器將會插入 MyCustomSQLServerRepository 實作類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="cdb17-132">For instance, in the previous example, the last line states that when any of your constructors have a dependency on IMyCustomRepository (interface or abstraction), the IoC container will inject an instance of the MyCustomSQLServerRepository implementation class.</span></span>

#### <a name="using-the-scrutor-library-for-automatic-types-registration"></a><span data-ttu-id="cdb17-133">使用 Scrutor 程式庫進行自動類型註冊</span><span class="sxs-lookup"><span data-stu-id="cdb17-133">Using the Scrutor library for automatic types registration</span></span>

<span data-ttu-id="cdb17-134">在 .NET Core 中使用 DI 時，您可能想要可以掃描組件，並依照慣例自動註冊其類型。</span><span class="sxs-lookup"><span data-stu-id="cdb17-134">When using DI in .NET Core, you might want to be able to scan an assembly and automatically register its types by convention.</span></span> <span data-ttu-id="cdb17-135">ASP.NET Core 目前未提供此功能。</span><span class="sxs-lookup"><span data-stu-id="cdb17-135">This feature is not currently available in ASP.NET Core.</span></span> <span data-ttu-id="cdb17-136">不過，您可以使用 [Scrutor](https://github.com/khellang/Scrutor) 程式庫來進行這項作業。</span><span class="sxs-lookup"><span data-stu-id="cdb17-136">However, you can use the [Scrutor](https://github.com/khellang/Scrutor) library for that.</span></span> <span data-ttu-id="cdb17-137">當您有數個需要在 IoC 容器中註冊的類型時，這種方法十分方便。</span><span class="sxs-lookup"><span data-stu-id="cdb17-137">This approach is convenient when you have dozens of types that need to be registered in your IoC container.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="cdb17-138">其他資源</span><span class="sxs-lookup"><span data-stu-id="cdb17-138">Additional resources</span></span>

-   <span data-ttu-id="cdb17-139">**Matthew King：使用 Scrutor 註冊服務**
    [*https://mking.net/blog/registering-services-with-scrutor*](https://mking.net/blog/registering-services-with-scrutor)</span><span class="sxs-lookup"><span data-stu-id="cdb17-139">**Matthew King. Registering services with Scrutor**
[*https://mking.net/blog/registering-services-with-scrutor*](https://mking.net/blog/registering-services-with-scrutor)</span></span>

<!-- -->

-   <span data-ttu-id="cdb17-140">**Kristian Hellang：Scrutor.**</span><span class="sxs-lookup"><span data-stu-id="cdb17-140">**Kristian Hellang. Scrutor.**</span></span> <span data-ttu-id="cdb17-141">GitHub 存放庫。</span><span class="sxs-lookup"><span data-stu-id="cdb17-141">GitHub repo.</span></span>
    [*https://github.com/khellang/Scrutor*](https://github.com/khellang/Scrutor)

#### <a name="using-autofac-as-an-ioc-container"></a><span data-ttu-id="cdb17-142">使用 Autofac 作為 IoC 容器</span><span class="sxs-lookup"><span data-stu-id="cdb17-142">Using Autofac as an IoC container</span></span>

<span data-ttu-id="cdb17-143">您也可以使用其他 IoC 容器，並將它們插入至 ASP.NET Core 管道，就像 eShopOnContainers 中的訂購微服務一樣，而訂購微服務使用 [Autofac](https://autofac.org/)。</span><span class="sxs-lookup"><span data-stu-id="cdb17-143">You can also use additional IoC containers and plug them into the ASP.NET Core pipeline, as in the ordering microservice in eShopOnContainers, which uses [Autofac](https://autofac.org/).</span></span> <span data-ttu-id="cdb17-144">使用 Autofac 時，通常會透過模組來註冊類型，以讓您根據類型位置來分割多個檔案之間的註冊類型，就像您將應用程式類型分散到多個類別程式庫一樣。</span><span class="sxs-lookup"><span data-stu-id="cdb17-144">When using Autofac you typically register the types via modules, which allow you to split the registration types between multiple files depending on where your types are, just as you could have the application types distributed across multiple class libraries.</span></span>

<span data-ttu-id="cdb17-145">例如，下列 [Autofac 應用程式模組](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs)適用於具有您想要插入之類型的 [Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) 專案。</span><span class="sxs-lookup"><span data-stu-id="cdb17-145">For example, the following is the [Autofac application module](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) for the [Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) project with the types you will want to inject.</span></span>

```csharp
public class ApplicationModule : Autofac.Module
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

<span data-ttu-id="cdb17-146">註冊程序和概念與您可向內建 ASP.NET Core IoC 容器註冊類型的方式極為類似，但使用 Autofac 時的語法略為不同。</span><span class="sxs-lookup"><span data-stu-id="cdb17-146">The registration process and concepts are very similar to the way you can register types with the built-in ASP.NET Core IoC container, but the syntax when using Autofac is a bit different.</span></span>

<span data-ttu-id="cdb17-147">在範例程式碼中，會一起註冊抽象 IOrderRepository 與實作類別 OrderRepository。</span><span class="sxs-lookup"><span data-stu-id="cdb17-147">In the example code, the abstraction IOrderRepository is registered along with the implementation class OrderRepository.</span></span> <span data-ttu-id="cdb17-148">這表示只要建構函式透過 IOrderRepository 抽象或介面來宣告相依性，IoC 容器就會插入 OrderRepository 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="cdb17-148">This means that whenever a constructor is declaring a dependency through the IOrderRepository abstraction or interface, the IoC container will inject an instance of the OrderRepository class.</span></span>

<span data-ttu-id="cdb17-149">執行個體範圍類型決定如何在相同服務或相依性的要求之間共用執行個體。</span><span class="sxs-lookup"><span data-stu-id="cdb17-149">The instance scope type determines how an instance is shared between requests for the same service or dependency.</span></span> <span data-ttu-id="cdb17-150">提出相依性要求時，IoC 容器可以傳回下列結果：</span><span class="sxs-lookup"><span data-stu-id="cdb17-150">When a request is made for a dependency, the IoC container can return the following:</span></span>

-   <span data-ttu-id="cdb17-151">一個存留期範圍有單一執行個體 (在 ASP.NET Core IoC 容器中稱為「範圍」)。</span><span class="sxs-lookup"><span data-stu-id="cdb17-151">A single instance per lifetime scope (referred to in the ASP.NET Core IoC container as *scoped*).</span></span>

-   <span data-ttu-id="cdb17-152">一個相依性有新的執行個體 (在 ASP.NET Core IoC 容器中稱為「暫時性」)。</span><span class="sxs-lookup"><span data-stu-id="cdb17-152">A new instance per dependency (referred to in the ASP.NET Core IoC container as *transient*).</span></span>

-   <span data-ttu-id="cdb17-153">跨所有使用 IoC 容器的物件所共用的單一執行個體 (在 ASP.NET Core IoC 容器中稱為「單一」).</span><span class="sxs-lookup"><span data-stu-id="cdb17-153">A single instance shared across all objects using the IoC container (referred to in the ASP.NET Core IoC container as *singleton*).</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="cdb17-154">其他資源</span><span class="sxs-lookup"><span data-stu-id="cdb17-154">Additional resources</span></span>

-   <span data-ttu-id="cdb17-155">**ASP.NET Core 中的相依性插入簡介**
    [*https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection*](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)</span><span class="sxs-lookup"><span data-stu-id="cdb17-155">**Introduction to Dependency Injection in ASP.NET Core**
[*https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection*](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)</span></span>

-   <span data-ttu-id="cdb17-156">**Autofac.**</span><span class="sxs-lookup"><span data-stu-id="cdb17-156">**Autofac.**</span></span> <span data-ttu-id="cdb17-157">正式文件。</span><span class="sxs-lookup"><span data-stu-id="cdb17-157">Official documentation.</span></span>
    [*http://docs.autofac.org/en/latest/*](http://docs.autofac.org/en/latest/)

-   <span data-ttu-id="cdb17-158">**比較 ASP.NET Core IoC 容器服務生命週期與 Autofac IoC 容器執行個體範圍 - Cesar de la Torre。**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span><span class="sxs-lookup"><span data-stu-id="cdb17-158">**Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes - Cesar de la Torre.**
[*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span></span>

## <a name="implementing-the-command-and-command-handler-patterns"></a><span data-ttu-id="cdb17-159">實作命令和命令處理常式模式</span><span class="sxs-lookup"><span data-stu-id="cdb17-159">Implementing the Command and Command Handler patterns</span></span>

<span data-ttu-id="cdb17-160">在上節所顯示的透過建構函式的 DI 範例中，IoC 容器將會透過類別中的建構函式來插入存放庫。</span><span class="sxs-lookup"><span data-stu-id="cdb17-160">In the DI-through-constructor example shown in the previous section, the IoC container was injecting repositories through a constructor in a class.</span></span> <span data-ttu-id="cdb17-161">但，其確切插入位置為何？</span><span class="sxs-lookup"><span data-stu-id="cdb17-161">But exactly where were they injected?</span></span> <span data-ttu-id="cdb17-162">在簡單 Web API 中 (例如，eShopOnContainers 中的目錄微服務)，您是在控制器建構函式的 MVC 控制器層級插入它們。</span><span class="sxs-lookup"><span data-stu-id="cdb17-162">In a simple Web API (for example, the catalog microservice in eShopOnContainers), you inject them at the MVC controllers level, in a controller constructor.</span></span> <span data-ttu-id="cdb17-163">不過，在此區段的初始程式碼中 (eShopOnContainers 的 Ordering.API 服務中的 [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) 類別)，是透過特定命令處理常式的建構函式來插入相依性。</span><span class="sxs-lookup"><span data-stu-id="cdb17-163">However, in the initial code of this section (the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) class from the Ordering.API service in eShopOnContainers), the injection of dependencies is done through the constructor of a particular command handler.</span></span> <span data-ttu-id="cdb17-164">讓我們說明什麼是命令處理常式以及您想要使用它的原因。</span><span class="sxs-lookup"><span data-stu-id="cdb17-164">Let us explain what a command handler is and why you would want to use it.</span></span>

<span data-ttu-id="cdb17-165">命令模式本質上與本指南稍早介紹的 CQRS 模式有關。</span><span class="sxs-lookup"><span data-stu-id="cdb17-165">The Command pattern is intrinsically related to the CQRS pattern that was introduced earlier in this guide.</span></span> <span data-ttu-id="cdb17-166">CQRS 有兩端。</span><span class="sxs-lookup"><span data-stu-id="cdb17-166">CQRS has two sides.</span></span> <span data-ttu-id="cdb17-167">第一個區域是搭配使用簡化查詢與 [Dapper](https://github.com/StackExchange/dapper-dot-net) 微 ORM (先前已說明過) 的查詢。</span><span class="sxs-lookup"><span data-stu-id="cdb17-167">The first area is queries, using simplified queries with the [Dapper](https://github.com/StackExchange/dapper-dot-net) micro ORM, which was explained previously.</span></span> <span data-ttu-id="cdb17-168">第二個區域是命令，這是交易的起點以及服務外部的輸入通道。</span><span class="sxs-lookup"><span data-stu-id="cdb17-168">The second area is commands, which are the starting point for transactions, and the input channel from outside the service.</span></span>

<span data-ttu-id="cdb17-169">如圖 9-24 所示，模式是根據接受來自用戶端的命令，然後根據領域模型規則處理它們，最後持續保存與交易的狀態。</span><span class="sxs-lookup"><span data-stu-id="cdb17-169">As shown in Figure 9-24, the pattern is based on accepting commands from the client side, processing them based on the domain model rules, and finally persisting the states with transactions.</span></span>

![](./media/image21.png)

<span data-ttu-id="cdb17-170">**圖 9-24**.</span><span class="sxs-lookup"><span data-stu-id="cdb17-170">**Figure 9-24**.</span></span> <span data-ttu-id="cdb17-171">CQRS 模式中命令或「交易端」的高階檢視</span><span class="sxs-lookup"><span data-stu-id="cdb17-171">High-level view of the commands or “transactional side” in a CQRS pattern</span></span>

### <a name="the-command-class"></a><span data-ttu-id="cdb17-172">命令類別</span><span class="sxs-lookup"><span data-stu-id="cdb17-172">The command class</span></span>

<span data-ttu-id="cdb17-173">命令是一種要求，讓系統執行可變更系統狀態的動作。</span><span class="sxs-lookup"><span data-stu-id="cdb17-173">A command is a request for the system to perform an action that changes the state of the system.</span></span> <span data-ttu-id="cdb17-174">命令是命令式的，而且只應該處理一次。</span><span class="sxs-lookup"><span data-stu-id="cdb17-174">Commands are imperative, and should be processed just once.</span></span>

<span data-ttu-id="cdb17-175">因為命令是命令式的，所以通常是透過命令式方式使用動詞進行命名 (例如，"create" 或 "update")，而且可能包含彙總類型 (例如 CreateOrderCommand)。</span><span class="sxs-lookup"><span data-stu-id="cdb17-175">Since commands are imperatives, they are typically named with a verb in the imperative mood (for example, "create" or "update"), and they might include the aggregate type, such as CreateOrderCommand.</span></span> <span data-ttu-id="cdb17-176">與事件不同，命令不是過去的事實；它只是要求，因此可能會遭拒絕。</span><span class="sxs-lookup"><span data-stu-id="cdb17-176">Unlike an event, a command is not a fact from the past; it is only a request, and thus may be refused.</span></span>

<span data-ttu-id="cdb17-177">程序管理員指示彙總來執行動作時，命令可能因起始要求的使用者而源自 UI，或源自程序管理員。</span><span class="sxs-lookup"><span data-stu-id="cdb17-177">Commands can originate from the UI as a result of a user initiating a request, or from a process manager when the process manager is directing an aggregate to perform an action.</span></span>

<span data-ttu-id="cdb17-178">命令的重要特性是單一接收者只應該處理它一次。</span><span class="sxs-lookup"><span data-stu-id="cdb17-178">An important characteristic of a command is that it should be processed just once by a single receiver.</span></span> <span data-ttu-id="cdb17-179">原因是命令是您想要在應用程式中執行的單一動作或交易。</span><span class="sxs-lookup"><span data-stu-id="cdb17-179">This is because a command is a single action or transaction you want to perform in the application.</span></span> <span data-ttu-id="cdb17-180">例如，相同的訂單建立命令只應該處理一次。</span><span class="sxs-lookup"><span data-stu-id="cdb17-180">For example, the same order creation command should not be processed more than once.</span></span> <span data-ttu-id="cdb17-181">這是命令與事件之間的重要差異。</span><span class="sxs-lookup"><span data-stu-id="cdb17-181">This is an important difference between commands and events.</span></span> <span data-ttu-id="cdb17-182">可能會多次處理事件，因為許多系統或微服務可能都會對事件感興趣。</span><span class="sxs-lookup"><span data-stu-id="cdb17-182">Events may be processed multiple times, because many systems or microservices might be interested in the event.</span></span>

<span data-ttu-id="cdb17-183">此外，如果命令不是等冪，則命令務必只處理一次。</span><span class="sxs-lookup"><span data-stu-id="cdb17-183">In addition, it is important that a command be processed only once in case the command is not idempotent.</span></span> <span data-ttu-id="cdb17-184">如果基於命令本質或系統處理命令的方式，命令可以執行多次，而不變更結果，則命令為等冪。</span><span class="sxs-lookup"><span data-stu-id="cdb17-184">A command is idempotent if it can be executed multiple times without changing the result, either because of the nature of the command, or because of the way the system handles the command.</span></span>

<span data-ttu-id="cdb17-185">透過領域商務規則和非變異值而變得有意義時，最好讓命令和更新設為等冪。</span><span class="sxs-lookup"><span data-stu-id="cdb17-185">It is a good practice to make your commands and updates idempotent when it makes sense under your domain’s business rules and invariants.</span></span> <span data-ttu-id="cdb17-186">例如，若要使用相同的範例，如果基於任何原因 (重試邏輯、駭客等等) 相同的 CreateOrder 命令到達您的系統多次，則您應該可以識別它，並確保未建立多個訂單。</span><span class="sxs-lookup"><span data-stu-id="cdb17-186">For instance, to use the same example, if for any reason (retry logic, hacking, etc.) the same CreateOrder command reaches your system multiple times, you should be able to identify it and ensure that you do not create multiple orders.</span></span> <span data-ttu-id="cdb17-187">若要這樣做，您需要在作業中附加某種類型的身分識別，並識別是否已處理命令或更新。</span><span class="sxs-lookup"><span data-stu-id="cdb17-187">To do so, you need to attach some kind of identity in the operations and identify whether the command or update was already processed.</span></span>

<span data-ttu-id="cdb17-188">您將命令傳送給單一接收者；請不要發行命令。</span><span class="sxs-lookup"><span data-stu-id="cdb17-188">You send a command to a single receiver; you do not publish a command.</span></span> <span data-ttu-id="cdb17-189">發行適用於指出事實的整合事件，而事實是發生某個情況，而且事件接收者可能會感興趣。</span><span class="sxs-lookup"><span data-stu-id="cdb17-189">Publishing is for integration events that state a fact—that something has happened and might be interesting for event receivers.</span></span> <span data-ttu-id="cdb17-190">如果是事件，則發行者不會關心哪些接收器收到事件或其處理方式。</span><span class="sxs-lookup"><span data-stu-id="cdb17-190">In the case of events, the publisher has no concerns about which receivers get the event or what they do it.</span></span> <span data-ttu-id="cdb17-191">但是整合事件是先前各節中已介紹的不同劇本。</span><span class="sxs-lookup"><span data-stu-id="cdb17-191">But integration events are a different story already introduced in previous sections.</span></span>

<span data-ttu-id="cdb17-192">命令是使用類別進行實作，而類別包含資料欄位或具有執行該命令所需之所有資訊的集合。</span><span class="sxs-lookup"><span data-stu-id="cdb17-192">A command is implemented with a class that contains data fields or collections with all the information that is needed in order to execute that command.</span></span> <span data-ttu-id="cdb17-193">命令是一種特殊的資料轉送物件 (DTO)，專門用來要求變更或交易。</span><span class="sxs-lookup"><span data-stu-id="cdb17-193">A command is a special kind of Data Transfer Object (DTO), one that is specifically used to request changes or transactions.</span></span> <span data-ttu-id="cdb17-194">命令本身只根據處理命令所需的資訊，而不需要其他資訊。</span><span class="sxs-lookup"><span data-stu-id="cdb17-194">The command itself is based on exactly the information that is needed for processing the command, and nothing more.</span></span>

<span data-ttu-id="cdb17-195">下列範例示範簡化 CreateOrderCommand 類別。</span><span class="sxs-lookup"><span data-stu-id="cdb17-195">The following example shows the simplified CreateOrderCommand class.</span></span> <span data-ttu-id="cdb17-196">這是 eShopOnContainers 訂購微服務中所使用的不可變命令。</span><span class="sxs-lookup"><span data-stu-id="cdb17-196">This is an immutable command that is used in the ordering microservice in eShopOnContainers.</span></span>

```csharp
// DDD and CQRS patterns comment
// Note that we recommend that you implement immutable commands
// In this case, immutability is achieved by having all the setters as private
// plus being able to update the data just once, when creating the object
// through the constructor.
// References on immutable commands:
// http://cqrs.nu/Faq
// https://docs.spine3.org/motivation/immutability.html
// http://blog.gauffin.org/2012/06/griffin-container-introducing-command-support/
// https://msdn.microsoft.com/library/bb383979.aspx
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

<span data-ttu-id="cdb17-197">基本上，此命令類別包含您使用領域模型物件來執行商務交易所需的所有資料。</span><span class="sxs-lookup"><span data-stu-id="cdb17-197">Basically, the command class contains all the data you need for performing a business transaction by using the domain model objects.</span></span> <span data-ttu-id="cdb17-198">因此，命令只是包含唯讀資料而沒有行為的資料結構。</span><span class="sxs-lookup"><span data-stu-id="cdb17-198">Thus, commands are simply data structures that contain read-only data, and no behavior.</span></span> <span data-ttu-id="cdb17-199">命令的名稱會指出其用途。</span><span class="sxs-lookup"><span data-stu-id="cdb17-199">The command’s name indicates its purpose.</span></span> <span data-ttu-id="cdb17-200">在許多 C\# 這類語言中，命令會呈現為類別，但就實際物件導向意義而言，它們不是真正的類別。</span><span class="sxs-lookup"><span data-stu-id="cdb17-200">In many languages like C\#, commands are represented as classes, but they are not true classes in the real object-oriented sense.</span></span>

<span data-ttu-id="cdb17-201">作為其他特性，命令是不可變的，因為預期的用法是領域模型會直接處理它們。</span><span class="sxs-lookup"><span data-stu-id="cdb17-201">As an additional characteristic, commands are immutable, because the expected usage is that they are processed directly by the domain model.</span></span> <span data-ttu-id="cdb17-202">它們在其預測存留期間不需要變更。</span><span class="sxs-lookup"><span data-stu-id="cdb17-202">They do not need to change during their projected lifetime.</span></span> <span data-ttu-id="cdb17-203">在 C\# 類別中，沒有任何 setter 或變更內部狀態的其他方法，可以達到不變性。</span><span class="sxs-lookup"><span data-stu-id="cdb17-203">In a C\# class, immutability can be achieved by not having any setters or other methods that change internal state.</span></span>

<span data-ttu-id="cdb17-204">例如，建立訂單的命令類別可能類似您想要建立之訂單的資料，但您可能不需要相同的屬性。</span><span class="sxs-lookup"><span data-stu-id="cdb17-204">For example, the command class for creating an order is probably similar in terms of data to the order you want to create, but you probably do not need the same attributes.</span></span> <span data-ttu-id="cdb17-205">例如，因為尚未建立訂單，所以 CreateOrderCommand 沒有訂單識別碼。</span><span class="sxs-lookup"><span data-stu-id="cdb17-205">For instance, CreateOrderCommand does not have an order ID, because the order has not been created yet.</span></span>

<span data-ttu-id="cdb17-206">許多命令類別都可以簡單，只需要某個需要變更之狀態的幾個欄位。</span><span class="sxs-lookup"><span data-stu-id="cdb17-206">Many command classes can be simple, requiring only a few fields about some state that needs to be changed.</span></span> <span data-ttu-id="cdb17-207">就是，如果您使用與下列類似的命令，只將訂單的狀態從「處理中」變更為「已付款」或「已出貨」：</span><span class="sxs-lookup"><span data-stu-id="cdb17-207">That would be the case if you are just changing the status of an order from “in process” to “paid” or “shipped” by using a command similar to the following:</span></span>

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

<span data-ttu-id="cdb17-208">有些開發人員會區隔其 UI 要求物件與其命令 DTO，但這只是喜好設定。</span><span class="sxs-lookup"><span data-stu-id="cdb17-208">Some developers make their UI request objects separate from their command DTOs, but that is just a matter of preference.</span></span> <span data-ttu-id="cdb17-209">這是沒有附加價值的冗長區隔，而且物件的形狀幾乎完全相同。</span><span class="sxs-lookup"><span data-stu-id="cdb17-209">It is a tedious separation with not much added value, and the objects are almost exactly the same shape.</span></span> <span data-ttu-id="cdb17-210">例如，在 eShopOnContainers 中，有些命令直接來自用戶端。</span><span class="sxs-lookup"><span data-stu-id="cdb17-210">For instance, in eShopOnContainers, some commands come directly from the client side.</span></span>

### <a name="the-command-handler-class"></a><span data-ttu-id="cdb17-211">命令處理常式類別</span><span class="sxs-lookup"><span data-stu-id="cdb17-211">The Command Handler class</span></span>

<span data-ttu-id="cdb17-212">您應該為每個命令實作特定命令處理常式類別。</span><span class="sxs-lookup"><span data-stu-id="cdb17-212">You should implement a specific command handler class for each command.</span></span> <span data-ttu-id="cdb17-213">這是模式運作方式，而且它是您將在其中使用命令物件、領域物件和基礎結構存放庫物件的位置。</span><span class="sxs-lookup"><span data-stu-id="cdb17-213">That is how the pattern works, and it is where you will use the command object, the domain objects, and the infrastructure repository objects.</span></span> <span data-ttu-id="cdb17-214">命令處理常式實際上是 CQRS 和 DDD 的應用程式層中心。</span><span class="sxs-lookup"><span data-stu-id="cdb17-214">The command handler is in fact the heart of the application layer in terms of CQRS and DDD.</span></span> <span data-ttu-id="cdb17-215">不過，所有領域邏輯都應該包含在領域類別內，即彙總根 (根實體)、子實體或[領域服務](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/)內，但不在本身為應用程式層中類別的命令處理常式內。</span><span class="sxs-lookup"><span data-stu-id="cdb17-215">However, all the domain logic should be contained within the domain classes—within the aggregate roots (root entities), child entities, or [domain services](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), but not within the command handler, which is a class from the application layer.</span></span>

<span data-ttu-id="cdb17-216">命令處理常式會收到命令，並取得所使用彙總的結果。</span><span class="sxs-lookup"><span data-stu-id="cdb17-216">A command handler receives a command and obtains a result from the aggregate that is used.</span></span> <span data-ttu-id="cdb17-217">結果應該是命令執行成功或是發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="cdb17-217">The result should be either successful execution of the command, or an exception.</span></span> <span data-ttu-id="cdb17-218">如果是例外狀況，則系統狀態應該會維持不變。</span><span class="sxs-lookup"><span data-stu-id="cdb17-218">In the case of an exception, the system state should be unchanged.</span></span>

<span data-ttu-id="cdb17-219">命令處理常式通常會採取下列步驟：</span><span class="sxs-lookup"><span data-stu-id="cdb17-219">The command handler usually takes the following steps:</span></span>

-   <span data-ttu-id="cdb17-220">接收命令物件，例如 DTO (從[中繼程序](https://en.wikipedia.org/wiki/Mediator_pattern)或其他基礎結構物件)。</span><span class="sxs-lookup"><span data-stu-id="cdb17-220">It receives the command object, like a DTO (from the [mediator](https://en.wikipedia.org/wiki/Mediator_pattern) or other infrastructure object).</span></span>

-   <span data-ttu-id="cdb17-221">驗證命令有效 (如果未經中繼程序驗證)。</span><span class="sxs-lookup"><span data-stu-id="cdb17-221">It validates that the command is valid (if not validated by the mediator).</span></span>

-   <span data-ttu-id="cdb17-222">具現化為目前命令目標的彙總根執行個體。</span><span class="sxs-lookup"><span data-stu-id="cdb17-222">It instantiates the aggregate root instance that is the target of the current command.</span></span>

-   <span data-ttu-id="cdb17-223">對彙總根執行個體執行方法，以透過命令取得必要資料。</span><span class="sxs-lookup"><span data-stu-id="cdb17-223">It executes the method on the aggregate root instance, getting the required data from the command.</span></span>

-   <span data-ttu-id="cdb17-224">它會將彙總的新狀態持續保存至其相關資料庫。</span><span class="sxs-lookup"><span data-stu-id="cdb17-224">It persists the new state of the aggregate to its related database.</span></span> <span data-ttu-id="cdb17-225">這個最後一項作業是實際交易。</span><span class="sxs-lookup"><span data-stu-id="cdb17-225">This last operation is the actual transaction.</span></span>

<span data-ttu-id="cdb17-226">一般而言，命令處理常式會處理其彙總根 (根實體) 所驅動的單一彙總。</span><span class="sxs-lookup"><span data-stu-id="cdb17-226">Typically, a command handler deals with a single aggregate driven by its aggregate root (root entity).</span></span> <span data-ttu-id="cdb17-227">如果接收單一命令會影響多個彙總，則您可以使用領域事件將狀態或動作散佈到多個彙總。</span><span class="sxs-lookup"><span data-stu-id="cdb17-227">If multiple aggregates should be impacted by the reception of a single command, you could use domain events to propagate states or actions across multiple aggregates.</span></span>

<span data-ttu-id="cdb17-228">這裡的重點是處理命令時，所有領域邏輯都應該位在領域模型 (彙總) 內、全部進行封裝，而且可進行單元測試。</span><span class="sxs-lookup"><span data-stu-id="cdb17-228">The important point here is that when a command is being processed, all the domain logic should be inside the domain model (the aggregates), fully encapsulated and ready for unit testing.</span></span> <span data-ttu-id="cdb17-229">命令處理常式只是作為從資料庫取得領域模型的方法以及最後一個步驟，以告知基礎結構層級 (存放庫) 在模型變更時持續保存變更。</span><span class="sxs-lookup"><span data-stu-id="cdb17-229">The command handler just acts as a way to get the domain model from the database, and as the final step, to tell the infrastructure layer (repositories) to persist the changes when the model is changed.</span></span> <span data-ttu-id="cdb17-230">這種方法的優點是您不需要變更應用程式或基礎結構層中的程式碼，即可在隔離、完整封裝且豐富的行為領域模型中重構領域邏輯，而這些層級是連接層級 (命令處理常式、Web API、存放庫等等)。</span><span class="sxs-lookup"><span data-stu-id="cdb17-230">The advantage of this approach is that you can refactor the domain logic in an isolated, fully encapsulated, rich, behavioral domain model without changing code in the application or infrastructure layers, which are the plumbing level (command handlers, Web API, repositories, etc.).</span></span>

<span data-ttu-id="cdb17-231">命令處理常式因太多邏輯而變得複雜時，就會像程式碼。</span><span class="sxs-lookup"><span data-stu-id="cdb17-231">When command handlers get complex, with too much logic, that can be a code smell.</span></span> <span data-ttu-id="cdb17-232">檢閱其內容，而且，如果您發現領域邏輯，請重構程式碼，以將該領域行為移至領域物件 (彙總根和子實體) 的方法。</span><span class="sxs-lookup"><span data-stu-id="cdb17-232">Review them, and if you find domain logic, refactor the code to move that domain behavior to the methods of the domain objects (the aggregate root and child entity).</span></span>

<span data-ttu-id="cdb17-233">作為命令處理常式類別範例，下列程式碼會示範您在本章開頭看到的相同 CreateOrderCommandHandler 類別。</span><span class="sxs-lookup"><span data-stu-id="cdb17-233">As an example of a command handler class, the following code shows the same CreateOrderCommandHandler class that you saw at the beginning of this chapter.</span></span> <span data-ttu-id="cdb17-234">在此情況下，我們想要反白顯示 Handle 方法以及具有領域模型物件/彙總的作業。</span><span class="sxs-lookup"><span data-stu-id="cdb17-234">In this case, we want to highlight the Handle method and the operations with the domain model objects/aggregates.</span></span>

```csharp
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator, 
                                     IOrderRepository orderRepository, 
                                     IIdentityService identityService)
    {
        _orderRepository = orderRepository ?? 
                          throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ?? 
                          throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ?? 
                                 throw new ArgumentNullException(nameof(mediator));
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        // Create the Order AggregateRoot
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic 
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State, 
                                  message.Country, message.ZipCode);
        var order = new Order(message.UserId, address, message.CardTypeId, 
                              message.CardNumber, message.CardSecurityNumber, 
                              message.CardHolderName, message.CardExpiration);
            
        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                               item.Discount, item.PictureUrl, item.Units);
        }

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
    }
}
```

<span data-ttu-id="cdb17-235">下列是命令處理常式應該採取的額外步驟：</span><span class="sxs-lookup"><span data-stu-id="cdb17-235">These are additional steps a command handler should take:</span></span>

-   <span data-ttu-id="cdb17-236">使用命令的資料來操作彙總根方法和行為。</span><span class="sxs-lookup"><span data-stu-id="cdb17-236">Use the command’s data to operate with the aggregate root’s methods and behavior.</span></span>

-   <span data-ttu-id="cdb17-237">在領域物件內部，於執行交易時引發領域事件，但這從命令處理常式觀點是透明的。</span><span class="sxs-lookup"><span data-stu-id="cdb17-237">Internally within the domain objects, raise domain events while the transaction is executed, but that is transparent from a command handler point of view.</span></span>

-   <span data-ttu-id="cdb17-238">如果彙總的作業結果成功，而且，交易完成之後，則會引發整合事件命令處理常式 </span><span class="sxs-lookup"><span data-stu-id="cdb17-238">If the aggregate’s operation result is successful and after the transaction is finished, raise integration events command handler.</span></span> <span data-ttu-id="cdb17-239">(這些可能也是由存放庫這類基礎結構類別所引發)。</span><span class="sxs-lookup"><span data-stu-id="cdb17-239">(These might also be raised by infrastructure classes like repositories.)</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="cdb17-240">其他資源</span><span class="sxs-lookup"><span data-stu-id="cdb17-240">Additional resources</span></span>

-   <span data-ttu-id="cdb17-241">**Mark Seemann：At the Boundaries, Applications are Not Object-Oriented**
    [*http://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/*](http://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/)</span><span class="sxs-lookup"><span data-stu-id="cdb17-241">**Mark Seemann. At the Boundaries, Applications are Not Object-Oriented**
[*http://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/*](http://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/)</span></span>

-   <span data-ttu-id="cdb17-242">**命令和事件**
    [*http://cqrs.nu/Faq/commands-and-events*](http://cqrs.nu/Faq/commands-and-events)</span><span class="sxs-lookup"><span data-stu-id="cdb17-242">**Commands and events**
[*http://cqrs.nu/Faq/commands-and-events*](http://cqrs.nu/Faq/commands-and-events)</span></span>

-   <span data-ttu-id="cdb17-243">**命令處理常式有何作用？**
    [*http://cqrs.nu/Faq/command-handlers*](http://cqrs.nu/Faq/command-handlers)</span><span class="sxs-lookup"><span data-stu-id="cdb17-243">**What does a command handler do?**
[*http://cqrs.nu/Faq/command-handlers*](http://cqrs.nu/Faq/command-handlers)</span></span>

-   <span data-ttu-id="cdb17-244">**Jimmy Bogard：網域命令模式 – 處理常式**
    [*https://jimmybogard.com/domain-command-patterns-handlers/*](https://jimmybogard.com/domain-command-patterns-handlers/)</span><span class="sxs-lookup"><span data-stu-id="cdb17-244">**Jimmy Bogard. Domain Command Patterns – Handlers**
[*https://jimmybogard.com/domain-command-patterns-handlers/*](https://jimmybogard.com/domain-command-patterns-handlers/)</span></span>

-   <span data-ttu-id="cdb17-245">**Jimmy Bogard：網域命令模式 – 驗證**
    [*https://jimmybogard.com/domain-command-patterns-validation/*](https://jimmybogard.com/domain-command-patterns-validation/)</span><span class="sxs-lookup"><span data-stu-id="cdb17-245">**Jimmy Bogard. Domain Command Patterns – Validation**
[*https://jimmybogard.com/domain-command-patterns-validation/*](https://jimmybogard.com/domain-command-patterns-validation/)</span></span>

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a><span data-ttu-id="cdb17-246">命令處理序管道：如何觸發命令處理常式</span><span class="sxs-lookup"><span data-stu-id="cdb17-246">The Command process pipeline: how to trigger a command handler</span></span>

<span data-ttu-id="cdb17-247">下一個問題是如何叫用命令處理常式。</span><span class="sxs-lookup"><span data-stu-id="cdb17-247">The next question is how to invoke a command handler.</span></span> <span data-ttu-id="cdb17-248">您可以從每個相關 ASP.NET Core 控制器中手動呼叫它。</span><span class="sxs-lookup"><span data-stu-id="cdb17-248">You could manually call it from each related ASP.NET Core controller.</span></span> <span data-ttu-id="cdb17-249">不過，該方法結合太多，並不理想。</span><span class="sxs-lookup"><span data-stu-id="cdb17-249">However, that approach would be too coupled and is not ideal.</span></span>

<span data-ttu-id="cdb17-250">另兩個主要選項是建議的選項，包括：</span><span class="sxs-lookup"><span data-stu-id="cdb17-250">The other two main options, which are the recommended options, are:</span></span>

-   <span data-ttu-id="cdb17-251">透過記憶體內部中繼程序模式成品。</span><span class="sxs-lookup"><span data-stu-id="cdb17-251">Through an in-memory Mediator pattern artifact.</span></span>

-   <span data-ttu-id="cdb17-252">在控制器與處理常式之間使用非同步訊息佇列。</span><span class="sxs-lookup"><span data-stu-id="cdb17-252">With an asynchronous message queue, in between controllers and handlers.</span></span>

### <a name="using-the-mediator-pattern-in-memory-in-the-command-pipeline"></a><span data-ttu-id="cdb17-253">在命令管道中使用中繼程序模式 (記憶體內部)</span><span class="sxs-lookup"><span data-stu-id="cdb17-253">Using the Mediator pattern (in-memory) in the command pipeline</span></span>

<span data-ttu-id="cdb17-254">如圖 9-25 所示，在 CQRS 方法中，您使用與記憶體內部匯流排類似的智慧型中繼程序，而這夠聰明可以根據所收到的命令或 DTO 類型來重新導向至正確的命令處理常式。</span><span class="sxs-lookup"><span data-stu-id="cdb17-254">As shown in Figure 9-25, in a CQRS approach you use an intelligent mediator, similar to an in-memory bus, which is smart enough to redirect to the right command handler based on the type of the command or DTO being received.</span></span> <span data-ttu-id="cdb17-255">元件之間的單一黑色箭號代表物件 (在許多情況下，是透過 DI 插入) 與其相關互動之間的相依性。</span><span class="sxs-lookup"><span data-stu-id="cdb17-255">The single black arrows between components represent the dependencies between objects (in many cases, injected through DI) with their related interactions.</span></span>

![](./media/image22.png)

<span data-ttu-id="cdb17-256">**圖 9-25**.</span><span class="sxs-lookup"><span data-stu-id="cdb17-256">**Figure 9-25**.</span></span> <span data-ttu-id="cdb17-257">在單一 CQRS 微服務過程中使用中繼程序模式</span><span class="sxs-lookup"><span data-stu-id="cdb17-257">Using the Mediator pattern in process in a single CQRS microservice</span></span>

<span data-ttu-id="cdb17-258">使用中繼程序模式的合理原因是，在企業應用程式中，處理要求會變得複雜。</span><span class="sxs-lookup"><span data-stu-id="cdb17-258">The reason that using the Mediator pattern makes sense is that in enterprise applications, the processing requests can get complicated.</span></span> <span data-ttu-id="cdb17-259">您想要可以新增已開啟數目的跨領域關注，例如記錄、驗證、稽核和安全性。</span><span class="sxs-lookup"><span data-stu-id="cdb17-259">You want to be able to add an open number of cross-cutting concerns like logging, validations, audit, and security.</span></span> <span data-ttu-id="cdb17-260">在這些情況下，您可以依賴中繼程序管道 (請參閱[中繼程序模式](https://en.wikipedia.org/wiki/Mediator_pattern)) 提供這些額外行為或跨領域關注的方法。</span><span class="sxs-lookup"><span data-stu-id="cdb17-260">In these cases, you can rely on a mediator pipeline (see [Mediator pattern](https://en.wikipedia.org/wiki/Mediator_pattern)) to provide a means for these extra behaviors or cross-cutting concerns.</span></span>

<span data-ttu-id="cdb17-261">中繼程序是封裝此處理序「作法」的物件：它會根據狀態、命令處理常式叫用方式或您提供給處理常式的承載來協調執行。</span><span class="sxs-lookup"><span data-stu-id="cdb17-261">A mediator is an object that encapsulates the “how” of this process: it coordinates execution based on state, the way a command handler is invoked, or the payload you provide to the handler.</span></span> <span data-ttu-id="cdb17-262">使用中繼程序元件，即可套用裝飾項目 (或自 [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) 以來的[管道行為](https://github.com/jbogard/MediatR/wiki/Behaviors))，以透過集中且透明的方式套用跨領域關注。</span><span class="sxs-lookup"><span data-stu-id="cdb17-262">With a mediator component you can apply cross-cutting concerns in a centralized and transparent way by applying decorators (or [pipeline behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) since [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)).</span></span> <span data-ttu-id="cdb17-263">如需詳細資訊，請參閱[裝飾項目模式](https://en.wikipedia.org/wiki/Decorator_pattern)。</span><span class="sxs-lookup"><span data-stu-id="cdb17-263">For more information, see the [Decorator pattern](https://en.wikipedia.org/wiki/Decorator_pattern).</span></span>

<span data-ttu-id="cdb17-264">裝飾項目和行為類似[層面導向程式設計 (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming)，僅套用至中繼程序元件所管理的特定處理序管線。</span><span class="sxs-lookup"><span data-stu-id="cdb17-264">Decorators and behaviors are similar to [Aspect Oriented Programming (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming), only applied to a specific process pipeline managed by the mediator component.</span></span> <span data-ttu-id="cdb17-265">根據在編譯期間插入的「層面編織程序」或根據物件呼叫攔截，套用 AOP 中實作跨領域關注的層面。</span><span class="sxs-lookup"><span data-stu-id="cdb17-265">Aspects in AOP that implement cross-cutting concerns are applied based on *aspect weavers* injected at compilation time or based on object call interception.</span></span> <span data-ttu-id="cdb17-266">這兩種典型 AOP 方法的運作有時稱為「就像變魔術一樣」，因為不容易看到 AOP 的運作工作。</span><span class="sxs-lookup"><span data-stu-id="cdb17-266">Both typical AOP approaches are sometimes said to work "like magic," because it is not easy to see how AOP does its work.</span></span> <span data-ttu-id="cdb17-267">處理嚴重問題或 Bug 時，AOP 很難進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="cdb17-267">When dealing with serious issues or bugs, AOP can be difficult to debug.</span></span> <span data-ttu-id="cdb17-268">另一方面，這些裝飾項目/行為十分明確，而且只會套用至中繼程序內容，因此，偵錯更容易預測且更為輕鬆。</span><span class="sxs-lookup"><span data-stu-id="cdb17-268">On the other hand, these decorators/behaviors are explicit and applied only in the context of the mediator, so debugging is much more predictable and easy.</span></span>

<span data-ttu-id="cdb17-269">例如，在 eShopOnContainers 訂購微服務中，我們已實作兩個範例行為：[LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) 類別和 [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) 類別。</span><span class="sxs-lookup"><span data-stu-id="cdb17-269">For example, in the eShopOnContainers ordering microservice, we implemented two sample behaviors, a [LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) class and a [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) class.</span></span> <span data-ttu-id="cdb17-270">下節透過示範 eShopOnContainers 如何實作 [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) [行為](https://github.com/jbogard/MediatR/wiki/Behaviors)來說明行為的實作。</span><span class="sxs-lookup"><span data-stu-id="cdb17-270">The implementation of the behaviors is explained in the next section by showing how eShopOnContainers implements [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors).</span></span>

### <a name="using-message-queues-out-of-proc-in-the-commands-pipeline"></a><span data-ttu-id="cdb17-271">在命令管道中使用訊息佇列 (跨處理序)</span><span class="sxs-lookup"><span data-stu-id="cdb17-271">Using message queues (out-of-proc) in the command’s pipeline</span></span>

<span data-ttu-id="cdb17-272">另一個選擇是根據訊息代理程式或訊息佇列來使用非同步訊息，如圖 9-26 所示。</span><span class="sxs-lookup"><span data-stu-id="cdb17-272">Another choice is to use asynchronous messages based on brokers or message queues, as shown in Figure 9-26.</span></span> <span data-ttu-id="cdb17-273">該選項也可以與命令處理常式正前方的中繼程序一起使用。</span><span class="sxs-lookup"><span data-stu-id="cdb17-273">That option could also be combined with the mediator component right before the command handler.</span></span>

![](./media/image23.png)

<span data-ttu-id="cdb17-274">**圖 9-26**.</span><span class="sxs-lookup"><span data-stu-id="cdb17-274">**Figure 9-26**.</span></span> <span data-ttu-id="cdb17-275">搭配使用訊息佇列 (跨處理序和處理序間通訊) 與 CQRS 命令</span><span class="sxs-lookup"><span data-stu-id="cdb17-275">Using message queues (out of process and inter-process communication) with CQRS commands</span></span>

<span data-ttu-id="cdb17-276">使用訊息佇列接受命令可能會讓命令管道更為複雜，因為您可能需要將管道分割成透過外部訊息佇列所連接的兩個處理序。</span><span class="sxs-lookup"><span data-stu-id="cdb17-276">Using message queues to accept the commands can further complicate your command’s pipeline, because you will probably need to split the pipeline into two processes connected through the external message queue.</span></span> <span data-ttu-id="cdb17-277">儘管如此，如果您需要擁有根據非同步訊息的已改善延展性和效能，則應該使用它。</span><span class="sxs-lookup"><span data-stu-id="cdb17-277">Still, it should be used if you need to have improved scalability and performance based on asynchronous messaging.</span></span> <span data-ttu-id="cdb17-278">請考慮，如果是圖 9-26，則控制器只會將命令訊息公佈至佇列並傳回。</span><span class="sxs-lookup"><span data-stu-id="cdb17-278">Consider that in the case of Figure 9-26, the controller just posts the command message into the queue and returns.</span></span> <span data-ttu-id="cdb17-279">命令處理常式接著會依自己的步調來處理訊息。</span><span class="sxs-lookup"><span data-stu-id="cdb17-279">Then the command handlers process the messages at their own pace.</span></span> <span data-ttu-id="cdb17-280">這是佇列的最大好處：訊息佇列可以作為需要超級延展性時的緩衝區，例如針對股票或任何其他具有大量輸入資料的案例。</span><span class="sxs-lookup"><span data-stu-id="cdb17-280">That is a great benefit of queues: the message queue can act as a buffer in cases when hyper scalability is needed, such as for stocks or any other scenario with a high volume of ingress data.</span></span>

<span data-ttu-id="cdb17-281">不過，因為訊息佇列的非同步本質，所以您需要找出與用戶端應用程式溝通命令處理序成功或失敗的方式。</span><span class="sxs-lookup"><span data-stu-id="cdb17-281">However, because of the asynchronous nature of message queues, you need to figure out how to communicate with the client application about the success or failure of the command’s process.</span></span> <span data-ttu-id="cdb17-282">一般而言，您應該永遠不會使用「發動就忘記」命令。</span><span class="sxs-lookup"><span data-stu-id="cdb17-282">As a rule, you should never use “fire and forget” commands.</span></span> <span data-ttu-id="cdb17-283">每個商務應用程式都需要知道是否已成功處理命令，或至少已驗證和接受命令。</span><span class="sxs-lookup"><span data-stu-id="cdb17-283">Every business application needs to know if a command was processed successfully, or at least validated and accepted.</span></span>

<span data-ttu-id="cdb17-284">因此，與在執行交易之後傳回作業結果的同處理序命令處理序相較之下，可以在驗證已提交給非同步佇列的命令訊息之後回應用戶端，可能會增加系統的複雜性。</span><span class="sxs-lookup"><span data-stu-id="cdb17-284">Thus, being able to respond to the client after validating a command message that was submitted to an asynchronous queue adds complexity to your system, as compared to an in-process command process that returns the operation’s result after running the transaction.</span></span> <span data-ttu-id="cdb17-285">使用佇列，您可能需要透過其他作業結果訊息來傳回命令處理序結果，而這需要系統中的額外元件和自訂通訊。</span><span class="sxs-lookup"><span data-stu-id="cdb17-285">Using queues, you might need to return the result of the command process through other operation result messages, which will require additional components and custom communication in your system.</span></span>

<span data-ttu-id="cdb17-286">此外，非同步命令是單向命令，而這在許多情況下可能不需要，如 Burtsev Alexey 與 Greg Young 在[線上對話](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ)中的下列有趣交流所述：</span><span class="sxs-lookup"><span data-stu-id="cdb17-286">Additionally, async commands are one-way commands, which in many cases might not be needed, as is explained in the following interesting exchange between Burtsev Alexey and Greg Young in an [online conversation](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):</span></span>

<span data-ttu-id="cdb17-287">\[Burtsev Alexey\] 我發現人員在許多程式碼中沒有任何原因地使用非同步命令處理或單向命令訊息 (他們不會執行某個長時間作業、不會執行外部非同步程式碼，甚至不會跨應用程式界限使用訊息匯流排)。</span><span class="sxs-lookup"><span data-stu-id="cdb17-287">\[Burtsev Alexey\] I find lots of code where people use async command handling or one way command messaging without any reason to do so (they are not doing some long operation, they are not executing external async code, they do not even cross application boundary to be using message bus).</span></span> <span data-ttu-id="cdb17-288">為什麼它們會造成這種不必要的複雜性？</span><span class="sxs-lookup"><span data-stu-id="cdb17-288">Why do they introduce this unnecessary complexity?</span></span> <span data-ttu-id="cdb17-289">實際上，我到目前為止還沒有看過具有封鎖命令處理常式的 CQRS 程式碼範例，雖然它只會在大部分情況下正常運作。</span><span class="sxs-lookup"><span data-stu-id="cdb17-289">And actually, I haven't seen a CQRS code example with blocking command handlers so far, though it will work just fine in most cases.</span></span>

<span data-ttu-id="cdb17-290">\[Greg Young\] \[...\] 非同步命令不存在；它實際上是另一個事件。</span><span class="sxs-lookup"><span data-stu-id="cdb17-290">\[Greg Young\] \[...\] an asynchronous command doesn't exist; it's actually another event.</span></span> <span data-ttu-id="cdb17-291">如果我必須接受您傳送給我的內容，並在我不同意時引發事件，則您不需要再告訴我執行哪項動作。</span><span class="sxs-lookup"><span data-stu-id="cdb17-291">If I must accept what you send me and raise an event if I disagree, it's no longer you telling me to do something.</span></span> <span data-ttu-id="cdb17-292">而是告訴我已完成哪項作業。</span><span class="sxs-lookup"><span data-stu-id="cdb17-292">It's you telling me something has been done.</span></span> <span data-ttu-id="cdb17-293">這在一開始略為不同，但有許多影響。</span><span class="sxs-lookup"><span data-stu-id="cdb17-293">This seems like a slight difference at first, but it has many implications.</span></span>

<span data-ttu-id="cdb17-294">非同步命令可大幅增加系統複雜性，因為沒有任何簡單的方式可以指出失敗。</span><span class="sxs-lookup"><span data-stu-id="cdb17-294">Asynchronous commands greatly increase the complexity of a system, because there is no simple way to indicate failures.</span></span> <span data-ttu-id="cdb17-295">因此，不建議使用非同步命令，除非需要調整需求時，或在特殊情況下，透過訊息溝通內部微服務時。</span><span class="sxs-lookup"><span data-stu-id="cdb17-295">Therefore, asynchronous commands are not recommended other than when scaling requirements are needed or in special cases when communicating the internal microservices through messaging.</span></span> <span data-ttu-id="cdb17-296">在這些情況下，您必須針對失敗設計不同的報告和復原系統。</span><span class="sxs-lookup"><span data-stu-id="cdb17-296">In those cases, you must design a separate reporting and recovery system for failures.</span></span>

<span data-ttu-id="cdb17-297">在 eShopOnContainers 初始版本中，我們決定使用從 HTTP 要求啟動並由中繼程序模式所驅動的同步命令處理。</span><span class="sxs-lookup"><span data-stu-id="cdb17-297">In the initial version of eShopOnContainers, we decided to use synchronous command processing, started from HTTP requests and driven by the Mediator pattern.</span></span> <span data-ttu-id="cdb17-298">這可輕鬆地讓您傳回處理序的成功或失敗，如同 [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) 實作一樣。</span><span class="sxs-lookup"><span data-stu-id="cdb17-298">That easily allows you to return the success or failure of the process, as in the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) implementation.</span></span>

<span data-ttu-id="cdb17-299">在任何情況下，這應該都是根據您應用程式或微服務商務需求的決策。</span><span class="sxs-lookup"><span data-stu-id="cdb17-299">In any case, this should be a decision based on your application’s or microservice’s business requirements.</span></span>

## <a name="implementing-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a><span data-ttu-id="cdb17-300">使用中繼程序模式 (MediatR) 實作命令處理序管道</span><span class="sxs-lookup"><span data-stu-id="cdb17-300">Implementing the command process pipeline with a mediator pattern (MediatR)</span></span>

<span data-ttu-id="cdb17-301">作為範例實作，本指南建議根據中繼程序模式來使用同處理序管道，在記憶體內部將命令擷取和路由命令驅動到正確命令處理常式。</span><span class="sxs-lookup"><span data-stu-id="cdb17-301">As a sample implementation, this guide proposes using the in-process pipeline based on the Mediator pattern to drive command ingestion and route commands, in memory, to the right command handlers.</span></span> <span data-ttu-id="cdb17-302">本指南也會建議套用[行為](https://github.com/jbogard/MediatR/wiki/Behaviors)以區隔跨領域關注。</span><span class="sxs-lookup"><span data-stu-id="cdb17-302">The guide also proposes applying [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) in order to separate cross-cutting concerns.</span></span>

<span data-ttu-id="cdb17-303">針對 .NET Core 中的實作，有多個開放原始碼程式庫可用來實作中繼程序模式。</span><span class="sxs-lookup"><span data-stu-id="cdb17-303">For implementation in .NET Core, there are multiple open-source libraries available that implement the Mediator pattern.</span></span> <span data-ttu-id="cdb17-304">本指南中所使用的程式庫是 [MediatR](https://github.com/jbogard/MediatR) 開放原始碼程式庫 (由 Jimmy Bogard 所建立)，但您可以使用另一種方法。</span><span class="sxs-lookup"><span data-stu-id="cdb17-304">The library used in this guide is the [MediatR](https://github.com/jbogard/MediatR) open-source library (created by Jimmy Bogard), but you could use another approach.</span></span> <span data-ttu-id="cdb17-305">MediatR 是小型且簡單的程式庫，可讓您處理命令這類記憶體內部訊息，同時套用裝飾項目或行為。</span><span class="sxs-lookup"><span data-stu-id="cdb17-305">MediatR is a small and simple library that allows you to process in-memory messages like a command, while applying decorators or behaviors.</span></span>

<span data-ttu-id="cdb17-306">使用中繼程序模式可協助您減少結合，並找出所要求工作的關注，同時自動連接至執行該工作的處理常式，在此情況下，是連接至命令處理常式。</span><span class="sxs-lookup"><span data-stu-id="cdb17-306">Using the Mediator pattern helps you to reduce coupling and to isolate the concerns of the requested work, while automatically connecting to the handler that performs that work—in this case, to command handlers.</span></span>

<span data-ttu-id="cdb17-307">檢閱本指南時，Jimmy Bogard 會說明另一個使用中繼程序模式的好理由：</span><span class="sxs-lookup"><span data-stu-id="cdb17-307">Another good reason to use the Mediator pattern was explained by Jimmy Bogard when reviewing this guide:</span></span>

<span data-ttu-id="cdb17-308">我認為您可能需要注意這裡的測試 - 它提供不錯的一致窗口，讓您查看系統的行為。</span><span class="sxs-lookup"><span data-stu-id="cdb17-308">I think it might be worth mentioning testing here – it provides a nice consistent window into the behavior of your system.</span></span> <span data-ttu-id="cdb17-309">要求進，回應出。我們發現層面在建置行為一致的測試時相當重要。</span><span class="sxs-lookup"><span data-stu-id="cdb17-309">Request-in, response-out. We’ve found that aspect quite valuable in building consistently behaving tests.</span></span>

<span data-ttu-id="cdb17-310">首先，讓我們看一下您實際使用中繼程序物件的範例 WebAPI 控制器。</span><span class="sxs-lookup"><span data-stu-id="cdb17-310">First, let’s look at a sample WebAPI controller where you actually would use the mediator object.</span></span> <span data-ttu-id="cdb17-311">如果您不是使用中繼程序物件，則需要插入該控制站的所有相依性，例如記錄器物件和其他項目。</span><span class="sxs-lookup"><span data-stu-id="cdb17-311">If you were not using the mediator object, you would need to inject all the dependencies for that controller, things like a logger object and others.</span></span> <span data-ttu-id="cdb17-312">因此，建構函式可能會相當複雜。</span><span class="sxs-lookup"><span data-stu-id="cdb17-312">Therefore, the constructor would be quite complicated.</span></span> <span data-ttu-id="cdb17-313">另一方面，如果您使用中繼程序物件，則控制器的建構函式可能會較為簡單，即只有一些相依性而不是許多相依性 (如果一個跨領域作業有一個相依性)，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="cdb17-313">On the other hand, if you use the mediator object, the constructor of your controller can be a lot simpler, with just a few dependencies instead of many dependencies if you had one per cross-cutting operation, as in the following example:</span></span>

```csharp
public class MyMicroserviceController : Controller
{
    public MyMicroserviceController(IMediator mediator, 
                                    IMyMicroserviceQueries microserviceQueries)
    // ...
```

<span data-ttu-id="cdb17-314">您可以看到中繼程序提供全新和簡式 Web API 控制器建構函式。</span><span class="sxs-lookup"><span data-stu-id="cdb17-314">You can see that the mediator provides a clean and lean Web API controller constructor.</span></span> <span data-ttu-id="cdb17-315">此外，在控制器方法內，將命令傳送至中繼程序物件的程式碼幾乎就是一行：</span><span class="sxs-lookup"><span data-stu-id="cdb17-315">In addition, within the controller methods, the code to send a command to the mediator object is almost one line:</span></span>

```csharp
[Route("new")]
[HttpPost] 
public async Task<IActionResult> ExecuteBusinessOperation([FromBody]RunOpCommand 
                                                               runOperationCommand) 
{
    var commandResult = await _mediator.SendAsync(runOperationCommand); 

    return commandResult ? (IActionResult)Ok() : (IActionResult)BadRequest();
}
```

### <a name="implementing-idempotent-commands"></a><span data-ttu-id="cdb17-316">實作等冪命令</span><span class="sxs-lookup"><span data-stu-id="cdb17-316">Implementing idempotent Commands</span></span>

<span data-ttu-id="cdb17-317">在 eShopOnContainers 中，比上述更進階的範例是從訂購微服務提交 CreateOrderCommand 物件。</span><span class="sxs-lookup"><span data-stu-id="cdb17-317">In eShopOnContainers, a more advanced example than the above is submitting a CreateOrderCommand object from the Ordering microservice.</span></span> <span data-ttu-id="cdb17-318">但因為訂購商務程序比較複雜 (在此情況下，實際上是在 Basket 微服務中啟動它)，所以會從名為 [UserCheckoutAcceptedIntegrationEvent.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) 的整合事件處理常式中執行這個提交 CreateOrderCommand 物件的動作，而不是從用戶端應用程式呼叫的簡單 WebAPI 控制器，如上述較簡單範例所示。</span><span class="sxs-lookup"><span data-stu-id="cdb17-318">But since the Ordering business process is a bit more complex and, in our case, it actually starts in the Basket microservice, this action of submitting the CreateOrderCommand object is performed from an integration-event handler named [UserCheckoutAcceptedIntegrationEvent.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) instead of a simple WebAPI controller called from the client App as in the previous simpler example.</span></span> 

<span data-ttu-id="cdb17-319">不過，將命令提交給 MediatR 的動作相當類似，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="cdb17-319">Nevertheless, the action of submitting the Command to MediatR is pretty similar, as shown in the following code.</span></span>

```csharp
var createOrderCommand = new CreateOrderCommand(eventMsg.Basket.Items,     
                                                eventMsg.UserId, eventMsg.City, 
                                                eventMsg.Street, eventMsg.State,
                                                eventMsg.Country, eventMsg.ZipCode,
                                                eventMsg.CardNumber, 
                                                eventMsg.CardHolderName, 
                                                eventMsg.CardExpiration,
                                                eventMsg.CardSecurityNumber,  
                                                eventMsg.CardTypeId);

var requestCreateOrder = new IdentifiedCommand<CreateOrderCommand,bool>(createOrderCommand, 
                                                                        eventMsg.RequestId);
result = await _mediator.Send(requestCreateOrder);
```

<span data-ttu-id="cdb17-320">但是，此情況也略為更進階，因為我們也會實作等冪命令。</span><span class="sxs-lookup"><span data-stu-id="cdb17-320">However, this case is also a little bit more advanced because we’re also implementing idempotent commands.</span></span> <span data-ttu-id="cdb17-321">CreateOrderCommand 處理序應該是等冪，因此，如果相同的訊息因任何原因 (例如重試) 而透過網路進行複製，則相同的商務訂單只會處理一次。</span><span class="sxs-lookup"><span data-stu-id="cdb17-321">The CreateOrderCommand process should be idempotent, so if the same message comes duplicated through the network, because of any reason, like retries, the same business order will be processed just once.</span></span>

<span data-ttu-id="cdb17-322">實作方式是包裝商務命令 (在此情況下是 CreateOrderCommand)，並將它內嵌到泛型 IdentifiedCommand，而這是透過來自網路且必須為等冪的每個訊息識別碼所追蹤。</span><span class="sxs-lookup"><span data-stu-id="cdb17-322">This is implemented by wrapping the business command (in this case CreateOrderCommand) and embeding it into a generic IdentifiedCommand which is tracked by an ID of every message coming through the network that has to be idempotent.</span></span>

<span data-ttu-id="cdb17-323">在下列程式碼中，您可以看到 IdentifiedCommand 就只是具有識別碼和已包裝商務命令物件的 DTO。</span><span class="sxs-lookup"><span data-stu-id="cdb17-323">In the code below, you can see that the IdentifiedCommand is nothing more than a DTO with and ID plus the wrapped business command object.</span></span>

```csharp
public class IdentifiedCommand<T, R> : IRequest<R>
    where T : IRequest<R>
{
    public T Command { get; }
    public Guid Id { get; }
    public IdentifiedCommand(T command, Guid id)
    {
        Command = command;
        Id = id;
    }
}
```

<span data-ttu-id="cdb17-324">然後，IdentifiedCommand 的 CommandHandler (名為 [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs)) 基本上會檢查資料表中是否已有為訊息一部分的識別碼。</span><span class="sxs-lookup"><span data-stu-id="cdb17-324">Then the CommandHandler for the IdentifiedCommand named [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) will basically check if the ID coming as part of the message already exists in a table.</span></span> <span data-ttu-id="cdb17-325">如果已經存在，則不會再次處理該命令，因此它是等冪命令。</span><span class="sxs-lookup"><span data-stu-id="cdb17-325">If it already exists, that command won’t be processed again, so it behaves as an idempotent command.</span></span> <span data-ttu-id="cdb17-326">該基礎結構程式碼是透過下面所呼叫的 `_requestManager.ExistAsync` 方法來執行。</span><span class="sxs-lookup"><span data-stu-id="cdb17-326">That infrastructure code is performed by the `_requestManager.ExistAsync` method call below.</span></span>

```csharp
// IdentifiedCommandHandler.cs
public class IdentifiedCommandHandler<T, R> : 
                                   IAsyncRequestHandler<IdentifiedCommand<T, R>, R>
                                   where T : IRequest<R>
{
    private readonly IMediator _mediator;
    private readonly IRequestManager _requestManager;

    public IdentifiedCommandHandler(IMediator mediator, 
                                    IRequestManager requestManager)
    {
        _mediator = mediator;
        _requestManager = requestManager;
    }

    protected virtual R CreateResultForDuplicateRequest()
    {
        return default(R);
    }

    public async Task<R> Handle(IdentifiedCommand<T, R> message)
    {
        var alreadyExists = await _requestManager.ExistAsync(message.Id);
        if (alreadyExists)
        {
            return CreateResultForDuplicateRequest();
        }
        else
        {
            await _requestManager.CreateRequestForCommandAsync<T>(message.Id);

            // Send the embeded business command to mediator 
            // so it runs its related CommandHandler 
            var result = await _mediator.Send(message.Command);
                
            return result;
        }
    }
}
```

<span data-ttu-id="cdb17-327">因為 IdentifiedCommand 就像是商務命令的信封，所以因不是重複識別碼而需要處理商務命令時，會採用該內部商務命令，並在從 [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) 執行 `_mediator.Send(message.Command)` 時，將它重新提交給中繼程序，如同上述程式碼的最後一個部分。</span><span class="sxs-lookup"><span data-stu-id="cdb17-327">Since the IdentifiedCommand acts like a business command’s envelope, when the business command needs to be processed because it is not a repeated Id, then it takes that inner business command and re-submits it to Mediator, as in the last part of the code shown above when running `_mediator.Send(message.Command)`, from the [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs).</span></span>

<span data-ttu-id="cdb17-328">這樣一來，它會連結並執行商務命令處理常式，在此情況下，是對 Ordering 資料庫執行交易的 CreateOrderCommandHandler，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="cdb17-328">When doing that, it will link and run the business command handler, in this case, the CreateOrderCommandHandler which is running transactions against the Ordering database, as shown in the following code.</span></span>

```csharp
// CreateOrderCommandHandler.cs
public class CreateOrderCommandHandler
                                   : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator, 
                                     IOrderRepository orderRepository, 
                                     IIdentityService identityService)
    {
        _orderRepository = orderRepository ?? 
                          throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ?? 
                          throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ?? 
                                 throw new ArgumentNullException(nameof(mediator));
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        // Add/Update the Buyer AggregateRoot
        var address = new Address(message.Street, message.City, message.State,
                                  message.Country, message.ZipCode);
        var order = new Order(message.UserId, address, message.CardTypeId,  
                              message.CardNumber, message.CardSecurityNumber, 
                              message.CardHolderName, message.CardExpiration);
            
        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                               item.Discount, item.PictureUrl, item.Units);
        }

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
    }
}
```

### <a name="registering-the-types-used-by-mediatr"></a><span data-ttu-id="cdb17-329">註冊 MediatR 所使用的類型</span><span class="sxs-lookup"><span data-stu-id="cdb17-329">Registering the types used by MediatR</span></span>

<span data-ttu-id="cdb17-330">為了讓 MediatR 知道您的命令處理常式類別，您需要在 IoC 容器中註冊中繼程序類別和命令處理常式類別。</span><span class="sxs-lookup"><span data-stu-id="cdb17-330">In order for MediatR to be aware of your command handler classes, you need to register the mediator classes and the command handler classes in your IoC container.</span></span> <span data-ttu-id="cdb17-331">MediatR 預設會使用 Autofac 作為 IoC 容器，但您也可以使用內建 ASP.NET Core IoC 容器或 MediatR 所支援的任何其他容器。</span><span class="sxs-lookup"><span data-stu-id="cdb17-331">By default, MediatR uses Autofac as the IoC container, but you can also use the built-in ASP.NET Core IoC container or any other container supported by MediatR.</span></span>

<span data-ttu-id="cdb17-332">下列程式碼示範在使用 Autofac 模組時，如何註冊中繼程序的類型和命令。</span><span class="sxs-lookup"><span data-stu-id="cdb17-332">The following code shows how to register Mediator’s types and commands when using Autofac modules.</span></span>

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();

        // Register all the Command classes (they implement IAsyncRequestHandler)
        // in assembly holding the Commands
        builder.RegisterAssemblyTypes(
                              typeof(CreateOrderCommand).GetTypeInfo().Assembly).
                                   AsClosedTypesOf(typeof(IAsyncRequestHandler<,>));
        // Other types registration
        //...
    }
}
```

<span data-ttu-id="cdb17-333">這是 MediatR 顯現魔力的地方。</span><span class="sxs-lookup"><span data-stu-id="cdb17-333">This is where “the magic happens” with MediatR.</span></span> 

<span data-ttu-id="cdb17-334">因為每個命令處理常式都會實作泛型 IAsyncRequestHandler&lt;T&gt; 介面，所以註冊組件時，程式碼會使用 RegisteredAssemblyTypes 註冊所有標記為 RequestHandlers 的類型，同時基於 CommandHandler 類別所指出的關聯性而建立 CommandHandlers 與其 Commands 的關聯，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="cdb17-334">Because each command handler implements the generic IAsyncRequestHandler&lt;T&gt; interface, when registering the assemblies, the code registers with RegisteredAssemblyTypes all the types maked as RequestHandlers while relating the CommandHandlers with their Commands, thanks to the relationship stated at the CommandHandler class, as in the following example:</span></span>

```csharp
public class CreateOrderCommandHandler
  : IAsyncRequestHandler<CreateOrderCommand, bool>
{
```

<span data-ttu-id="cdb17-335">這是建立命令與命令處理常式之關聯的程式碼。</span><span class="sxs-lookup"><span data-stu-id="cdb17-335">That is the code that correlates commands with command handlers.</span></span> <span data-ttu-id="cdb17-336">處理常式只是簡單類別，但它繼承自 RequestHandler&lt;T&gt;，而且 MediatR 確定它是使用正確承載所叫用。</span><span class="sxs-lookup"><span data-stu-id="cdb17-336">The handler is just a simple class, but it inherits from RequestHandler&lt;T&gt;, and MediatR makes sure it is invoked with the correct payload.</span></span>

## <a name="applying-cross-cutting-concerns-when-processing-commands-with-the-behaviors-in-mediatr"></a><span data-ttu-id="cdb17-337">在 MediatR 中使用行為處理命令時套用跨領域關注</span><span class="sxs-lookup"><span data-stu-id="cdb17-337">Applying cross-cutting concerns when processing commands with the Behaviors in MediatR</span></span>

<span data-ttu-id="cdb17-338">還有一件事：可以將跨領域關注套用至中繼程序管道。</span><span class="sxs-lookup"><span data-stu-id="cdb17-338">There is one more thing: being able to apply cross-cutting concerns to the mediator pipeline.</span></span> <span data-ttu-id="cdb17-339">您也可以查看 Autofac 註冊模組程式碼結尾，了解如何註冊行為類型，特別是自訂 LoggingBehavior 類別和 ValidatorBehavior 類別。</span><span class="sxs-lookup"><span data-stu-id="cdb17-339">You can also see at the end of the Autofac registration module code how it registers a behavior type, specifically, a custom LoggingBehavior class and a ValidatorBehavior class.</span></span> <span data-ttu-id="cdb17-340">但是，您也可以新增其他自訂行為。</span><span class="sxs-lookup"><span data-stu-id="cdb17-340">But you could add other custom behaviours, too.</span></span>

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();

        // Register all the Command classes (they implement IAsyncRequestHandler)
        // in assembly holding the Commands
        builder.RegisterAssemblyTypes(
                              typeof(CreateOrderCommand).GetTypeInfo().Assembly).
                                   AsClosedTypesOf(typeof(IAsyncRequestHandler<,>));
        // Other types registration
        //...        
        builder.RegisterGeneric(typeof(LoggingBehavior<,>)).
                                                   As(typeof(IPipelineBehavior<,>));
        builder.RegisterGeneric(typeof(ValidatorBehavior<,>)).
                                                   As(typeof(IPipelineBehavior<,>));
    }
}
```

<span data-ttu-id="cdb17-341">該 [LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) 類別可以實作為下列程式碼，以記錄所執行命令處理常式的相關資訊以及是否成功。</span><span class="sxs-lookup"><span data-stu-id="cdb17-341">That [LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) class can be implemented as the following code, which logs information about the command handler being executed and whether it was successful or not.</span></span>

```csharp
public class LoggingBehavior<TRequest, TResponse> 
         : IPipelineBehavior<TRequest, TResponse>
{
    private readonly ILogger<LoggingBehavior<TRequest, TResponse>> _logger;
    public LoggingBehavior(ILogger<LoggingBehavior<TRequest, TResponse>> logger) =>
                                                                  _logger = logger;

    public async Task<TResponse> Handle(TRequest request,
                                        RequestHandlerDelegate<TResponse> next)
    {
        _logger.LogInformation($"Handling {typeof(TRequest).Name}");
        var response = await next();
        _logger.LogInformation($"Handled {typeof(TResponse).Name}");
        return response;
    }
}
```

<span data-ttu-id="cdb17-342">只要實作這個裝飾項目類別，以及使用它來裝飾管道，透過 MediatR 處理的所有命令都會記錄執行相關資訊。</span><span class="sxs-lookup"><span data-stu-id="cdb17-342">Just by implementing this decorator class and by decorating the pipeline with it, all the commands processed through MediatR will be logging information about the execution.</span></span>

<span data-ttu-id="cdb17-343">eShopOnContainers 訂購微服務也會套用第二個行為來進行基本驗證，即依賴 [FluentValidation](https://github.com/JeremySkinner/FluentValidation) 程式庫的 [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) 類別，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="cdb17-343">The eShopOnContainers ordering microservice also applies a second behavior for basic validations, the [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) class that relies on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, as shown in the following code:</span></span>

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

<span data-ttu-id="cdb17-344">然後，根據 [FluentValidation](https://github.com/JeremySkinner/FluentValidation) 程式庫，我們建立使用 CreateOrderCommand 所傳遞之資料的驗證，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="cdb17-344">Then, based on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, we created validation for the data passed with CreateOrderCommand, as in the following code:</span></span>

```csharp
public class ValidatorBehavior<TRequest, TResponse> 
         : IPipelineBehavior<TRequest, TResponse>
{
    private readonly IValidator<TRequest>[] _validators;
    public ValidatorBehavior(IValidator<TRequest>[] validators) =>
                                                         _validators = validators;

    public async Task<TResponse> Handle(TRequest request,
                                        RequestHandlerDelegate<TResponse> next)
    {
        var failures = _validators
            .Select(v => v.Validate(request))
            .SelectMany(result => result.Errors)
            .Where(error => error != null)
            .ToList();

        if (failures.Any())
        {
            throw new OrderingDomainException(
                $"Command Validation Errors for type {typeof(TRequest).Name}",
                        new ValidationException("Validation exception", failures));
        }

        var response = await next();
        return response;
    }
}
```

<span data-ttu-id="cdb17-345">然後，根據 FluentValidation 程式庫，我們建立使用 CreateOrderCommand 所傳遞之資料的驗證，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="cdb17-345">Then, based on the FluentValidation library, we created validation for the data passed with CreateOrderCommand, as in the following code:</span></span>

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
        RuleFor(command => command.CardExpiration).NotEmpty().Must(BeValidExpirationDate).WithMessage("Please specify a valid card expiration date"); 
        RuleFor(command => command.CardSecurityNumber).NotEmpty().Length(3); 
        RuleFor(command => command.CardTypeId).NotEmpty();
        RuleFor(command => command.OrderItems).Must(ContainOrderItems).WithMessage("No order items found"); 
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

<span data-ttu-id="cdb17-346">您可以建立額外驗證。</span><span class="sxs-lookup"><span data-stu-id="cdb17-346">You could create additional validations.</span></span> <span data-ttu-id="cdb17-347">這是實作命令驗證的全新且更簡潔的方式。</span><span class="sxs-lookup"><span data-stu-id="cdb17-347">This is a very clean and elegant way to implement your command validations.</span></span>

<span data-ttu-id="cdb17-348">使用類似的方式，您可以實作想要在處理命令時套用至命令之其他層面或跨領域關注的其他行為。</span><span class="sxs-lookup"><span data-stu-id="cdb17-348">In a similar way, you could implement other behaviors for additional aspects or cross-cutting concerns that you want to apply to commands when handling them.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="cdb17-349">其他資源</span><span class="sxs-lookup"><span data-stu-id="cdb17-349">Additional resources</span></span>

##### <a name="the-mediator-pattern"></a><span data-ttu-id="cdb17-350">中繼程序模式</span><span class="sxs-lookup"><span data-stu-id="cdb17-350">The mediator pattern</span></span>

-   <span data-ttu-id="cdb17-351">**Mediator pattern**
    [*https://en.wikipedia.org/wiki/Mediator\_pattern*](https://en.wikipedia.org/wiki/Mediator_pattern) (中繼程序模式)</span><span class="sxs-lookup"><span data-stu-id="cdb17-351">**Mediator pattern**
[*https://en.wikipedia.org/wiki/Mediator\_pattern*](https://en.wikipedia.org/wiki/Mediator_pattern)</span></span>

##### <a name="the-decorator-pattern"></a><span data-ttu-id="cdb17-352">裝飾項目模式</span><span class="sxs-lookup"><span data-stu-id="cdb17-352">The decorator pattern</span></span>

-   <span data-ttu-id="cdb17-353">**Decorator pattern**
    [*https://en.wikipedia.org/wiki/Decorator\_pattern*](https://en.wikipedia.org/wiki/Decorator_pattern) (裝飾項目模式)</span><span class="sxs-lookup"><span data-stu-id="cdb17-353">**Decorator pattern**
[*https://en.wikipedia.org/wiki/Decorator\_pattern*](https://en.wikipedia.org/wiki/Decorator_pattern)</span></span>

##### <a name="mediatr-jimmy-bogard"></a><span data-ttu-id="cdb17-354">MediatR (Jimmy Bogard)</span><span class="sxs-lookup"><span data-stu-id="cdb17-354">MediatR (Jimmy Bogard)</span></span>

-   <span data-ttu-id="cdb17-355">**MediatR.**</span><span class="sxs-lookup"><span data-stu-id="cdb17-355">**MediatR.**</span></span> <span data-ttu-id="cdb17-356">GitHub 存放庫。</span><span class="sxs-lookup"><span data-stu-id="cdb17-356">GitHub repo.</span></span>
    [*https://github.com/jbogard/MediatR*](https://github.com/jbogard/MediatR)

-   <span data-ttu-id="cdb17-357">**CQRS 搭配 MediatR 和 AutoMapper**
    [*https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/*](https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/)</span><span class="sxs-lookup"><span data-stu-id="cdb17-357">**CQRS with MediatR and AutoMapper**
[*https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/*](https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/)</span></span>

-   <span data-ttu-id="cdb17-358">**讓您的控制項瘦身：POST 和命令。**
    [*https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/*](https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/)</span><span class="sxs-lookup"><span data-stu-id="cdb17-358">**Put your controllers on a diet: POSTs and commands.**
[*https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/*](https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/)</span></span>

-   <span data-ttu-id="cdb17-359">**使用中繼管線處理跨領域關注**
    [*https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/*](https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/)</span><span class="sxs-lookup"><span data-stu-id="cdb17-359">**Tackling cross-cutting concerns with a mediator pipeline**
[*https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/*](https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/)</span></span>

-   <span data-ttu-id="cdb17-360">**CQRS 和 REST：完美搭配**
    [*https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/*](https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/)</span><span class="sxs-lookup"><span data-stu-id="cdb17-360">**CQRS and REST: the perfect match**
[*https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/*](https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/)</span></span>

-   <span data-ttu-id="cdb17-361">**MediatR 管線範例**
    [*https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/*](https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/)</span><span class="sxs-lookup"><span data-stu-id="cdb17-361">**MediatR Pipeline Examples**
[*https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/*](https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/)</span></span>

-   <span data-ttu-id="cdb17-362">**MediatR 和 ASP.NET Core 的垂直配量測試裝置**
    *<https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/> *</span><span class="sxs-lookup"><span data-stu-id="cdb17-362">**Vertical Slice Test Fixtures for MediatR and ASP.NET Core**
*<https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/> *</span></span>

-   <span data-ttu-id="cdb17-363">**已發行適用於 Microsoft 相依性插入的 MediatR 延伸模組**
    [*https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/*](https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/)</span><span class="sxs-lookup"><span data-stu-id="cdb17-363">**MediatR Extensions for Microsoft Dependency Injection Released**
[*https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/*](https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/)</span></span>

##### <a name="fluent-validation"></a><span data-ttu-id="cdb17-364">Fluent 驗證</span><span class="sxs-lookup"><span data-stu-id="cdb17-364">Fluent validation</span></span>

-   <span data-ttu-id="cdb17-365">**Jeremy Skinner：FluentValidation.**</span><span class="sxs-lookup"><span data-stu-id="cdb17-365">**Jeremy Skinner. FluentValidation.**</span></span> <span data-ttu-id="cdb17-366">GitHub 存放庫。</span><span class="sxs-lookup"><span data-stu-id="cdb17-366">GitHub repo.</span></span>
    [*https://github.com/JeremySkinner/FluentValidation*](https://github.com/JeremySkinner/FluentValidation)

>[!div class="step-by-step"]
<span data-ttu-id="cdb17-367">[上一頁](microservice-application-layer-web-api-design.md)
[下一頁](../implement-resilient-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="cdb17-367">[Previous](microservice-application-layer-web-api-design.md)
[Next](../implement-resilient-applications/index.md)</span></span>
