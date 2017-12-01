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
# <a name="implementing-the-microservice-application-layer-using-the-web-api"></a>實作微服務應用程式層使用 Web API

## <a name="using-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a>將應用程式層級插入的基礎結構物件使用相依性插入

如先前所述，就可以實作應用程式層的成品，您要建置，例如在 Web API 專案或 MVC web 應用程式專案的一部分。 如果是使用 ASP.NET Core 建置微服務，應用程式層通常將為您的 Web 應用程式開發介面程式庫。 如果您想要個別功能從您的自訂應用程式層程式碼來自 ASP.NET Core （它的基礎結構，加上您的控制站），您也可以將應用程式層級放在個別的類別庫中，但這是選擇性。

比方說，如果應用程式層的順序的微服務程式碼直接實作的一部分**Ordering.API**專案 （ASP.NET Core Web API 專案），以顯示圖 9-19 版。

![](./media/image20.png)

**圖 9-19**。 應用程式中的圖層 Ordering.API ASP.NET Core Web API 專案

ASP.NET Core 包含簡單[內建 IoC 容器](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)（由的 IServiceProvider 介面） 根據預設，支援建構函式插入並 ASP.NET 的特定服務提供透過 DI。 ASP.NET Core 會使用詞彙*服務*任何您註冊將會透過 DI 插入類型。 您可以設定的內建的容器服務 ConfigureServices 類別方法中您的應用程式啟動。 相依性會實作類型需要的服務。

一般而言，您會想要插入實作的基礎結構物件的相依性。 很常見的相依性，將會是儲存機制。 但是，您會將您可能會有任何其他基礎結構相依性。 針對簡單的實作，您無法直接將插入您的工作單位的模式物件 （EF DbContext 物件），因為 DBContext 也是您基礎結構的持續性物件的實作。

在下列範例中，您可以查看如何.NET Core 正在插入所需的儲存機制物件，透過建構函式。 此類別是命令處理常式，我們將在下一節中討論。

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

類別會使用插入的儲存機制來執行交易，並將保存的狀態變更。 並不重要的命令處理常式，ASP.NET Core Web API 控制器方法，該類別是否或[DDD 應用程式服務](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/)。 最終仍是簡單的類別以類似的命令處理常式的方式使用儲存機制、 網域實體和其他應用程式的協調。 相依性插入適用於所有提及的類別，如使用 DI 範例所示相同的方式根據建構函式。

### <a name="registering-the-dependency-implementation-types-and-interfaces-or-abstractions"></a>正在註冊相依性的實作類型和介面或抽象物件

您使用透過建構函式插入的物件之前，您需要知道去哪裡註冊介面和類別，會產生插入 DI 透過您的應用程式類別的物件。 （例如 DI 依據建構函式，如先前所示）。

#### <a name="using-the-built-in-ioc-container-provided-by-aspnet-core"></a>使用 ASP.NET Core 所提供的內建 IoC 容器

當您使用 ASP.NET Core 所提供的內建 IoC 容器時，您會註冊您想要插入 ConfigureServices 方法，在 Startup.cs 檔案中，例如下列程式碼中的類型：

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

最常見的模式時註冊 IoC 容器中的型別是註冊一組類型 — 介面和其相關的實作類別。 然後當您從 IoC 容器透過任何建構函式要求物件，您可以要求介面的特定類型的物件。 比方說，在上述範例中，最後一行會指出當您建構函式的任何有相依性 IMyCustomRepository （介面或抽象） 時，IoC 容器會插入 MyCustomSQLServerRepository 實作的執行個體類別。

#### <a name="using-the-scrutor-library-for-automatic-types-registration"></a>使用自動類型註冊 Scrutor 程式庫

中使用時 DI.NET Core，您可能想要掃描組件，並自動註冊它的類型依慣例。 這項功能目前不提供在 ASP.NET Core。 不過，您可以使用[Scrutor](https://github.com/khellang/Scrutor)該程式庫。 當您有數十個需要註冊 IoC 容器中的類型，則這個方法會很方便。

#### <a name="additional-resources"></a>其他資源

-   **Matthew 國王。服務登錄 Scrutor**
    [*https://mking.io/blog/registering-services-with-scrutor*](https://mking.io/blog/registering-services-with-scrutor)

<!-- -->

-   **Kristian Hellang。Scrutor。** GitHub 儲存機制。
    [*https://github.com/khellang/Scrutor*](https://github.com/khellang/Scrutor)

#### <a name="using-autofac-as-an-ioc-container"></a>使用 Autofac IoC 容器

您也可以使用其他 IoC 容器，並插入 ASP.NET Core 管線，如同在 eShopOnContainers，會使用排序的微服務[Autofac](https://autofac.org/)。 當使用 Autofac 通常會註冊透過模組，可讓您將根據您的型別所處，就像您可能會分散到多個類別程式庫的應用程式類型的多個檔案之間的註冊型別類型。

例如，下列是[Autofac 應用程式模組](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs)如[Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API)專案，您會想要插入的型別。

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

註冊程序和概念是您可以使用內建 ASP.NET Core iOS 容器註冊類型的方式非常類似，但語法使用 Autofac 時稍有不同。

在範例程式碼，以及實作類別 OrderRepository 註冊抽象 IOrderRepository。 這表示每當建構函式會宣告透過 IOrderRepository 抽象或介面的相依性，IoC 容器會插入 OrderRepository 類別的執行個體。

執行個體範圍類型會決定執行個體共用相同的服務或相依性的要求之間的方式。 當提出要求的相依性 IoC 容器可以傳回下列結果：

-   每個存留期範圍的單一執行個體 (做為 ASP.NET Core IoC 容器所指*範圍*)。

-   每個相依性的新執行個體 (做為 ASP.NET Core IoC 容器所指*暫時性*)。

-   在使用 IoC 容器的所有物件共用的單一執行個體 (做為 ASP.NET Core IoC 容器所指*單一*)。

#### <a name="additional-resources"></a>其他資源

-   **相依性插入在 ASP.NET Core 簡介**
    [*https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection*](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)

-   **Autofac。** 官方文件集。
    [*http://docs.autofac.org/en/latest/*](http://docs.autofac.org/en/latest/)

-   **Cesar de la Torre：比較 ASP.NET Core IoC 容器服務存留期與 Autofac IoC 容器執行個體範圍**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)

## <a name="implementing-the-command-and-command-handler-patterns"></a>實作的命令和命令處理常式模式

DI 透過建構函式所示範例中上一節，IoC 容器所插入的儲存機制，透過在類別中的建構函式。 不過，完全其中被它們插入嗎？ 在簡單 Web API （例如，目錄微服務中 eShopOnContainers） 中，您將它們插入在 MVC 控制器層級，控制站的建構函式中。 不過，在此區段之初始程式碼 ( [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) eShopOnContainers Ordering.API 服務類別)，資料隱碼的相依性透過特定命令的建構函式處理常式。 讓我們將說明什麼是命令處理常式，且您會想要使用它。

稍早在本指南中引進的 CQRS 模式在本質上與命令模式。 CQRS 有兩個邊。 第一個區域是使用簡化的查詢與查詢[Dapper](https://github.com/StackExchange/dapper-dot-net)微 ORM，先前所述。 第二個區域是命令，也就是交易的起始點和從服務外部輸入的通道。

這個模式所示圖 9-20，根據接受來自用戶端的命令處理根據網域模型的規則，以及最後保存與交易的狀態。

![](./media/image21.png)

**圖 9-20**。 命令或 CQRS 模式中的 「 交易式端 」 的高階檢視

### <a name="the-command-class"></a>命令類別

命令會為系統執行的動作會變更系統狀態的要求。 命令是必要的工作，，，應該就可以一次處理。

由於命令全面，通常名為具有動詞命令命令式消遣 （例如，「 建立 」 或 「 更新 」），而且它們可能包含的彙總類型，例如 CreateOrderCommand。 與事件時，命令不是從過去; 事實它只是要求，並因此可能會被拒絕。

程序管理員導向彙總來執行動作時，從使用者起始要求，因為 UI 或程序管理員可以產生命令。

命令的重要特性是，它應該只有一次由單一接收者。 這是因為命令是單一動作或您想要執行應用程式中的交易。 例如，相同的順序建立命令不應處理一次以上。 這是一項重要差異之間命令和事件。 事件可能會處理許多次，因為許多系統或 microservices 可能感興趣的事件。

此外，很重要，命令會只處理一次此命令不是等冪。 如果執行多次而不會變更結果中，由於本質之故命令，或因為系統會處理命令的方式，命令會為等冪。

最好的作法是讓命令，並在您網域的商務規則和非變異值意義時更新具有等冪性。 比方說，如果基於任何原因 （重試邏輯，駭客等） 相同的 CreateOrder 命令達到您的系統多次使用相同的範例，您應該能夠識別它，並確保不會建立多個訂單。 若要這樣做，您需要附加某種類型的作業中的身分識別是否已經處理的命令或更新。

您將命令傳送到單一接收者;請勿發行命令。 發行適用於該狀態的事實整合事件 — 某項目發生，而且可能會有興趣的事件接收器。 事件，在 「 發行者 」 有哪些接收器事件或取得它們的功用它沒有問題。 但是整合事件不同的劇本，已經導入上一節。

命令是使用包含資料欄位或具有所有所需的資訊才能執行該命令的集合類別實作。 命令是一種特殊的資料傳輸物件 (DTO)，專門用來要求變更或交易的其中一個。 命令本身根據完全處理命令，而無其他所需的資訊。

下列範例示範簡化的 CreateOrderCommand 類別。 這是用於排序的微服務 eShopOnContainers 中不可變命令。

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

基本上，命令類別包含您需要執行了商務交易使用的網域模型物件的所有資料。 因此，命令會只是資料結構，其中包含唯讀的資料，以及任何行為。 命令的名稱會表示其用途。 在許多語言如 C\#，命令會表示為類別，但它們不是真正的物件導向的意義上，則為 true 的類別。

為其他的特性，命令是不可變的因為預期的用法是，它們會處理由網域模型直接。 它們不需要變更其投影的存留期間。 在 C 中\#類別，不變性可藉由沒有任何 setter 或其他方法的內部狀態變更。

例如，建立訂單的命令類別可能很類似以資料為您想要建立的順序，但您可能不需要相同的屬性。 比方說，CreateOrderCommand 沒有訂單 ID，因為順序尚未建立。

許多命令類別可以很簡單，需要幾個欄位只需要變更某些狀態相關的。 也就是使用案例如果您只變更從 「 進行中 」 至訂單狀態 」 付費 」 或 「 出貨 」 使用與下列類似的命令：

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

有些開發人員建立其 UI 要求物件從其命令 DTOs，分離，但這就只不過喜好設定。 它是冗長的分隔，與不太加入的值，而且物件幾乎完全相同的圖形。 比方說，在 eShopOnContainers，命令直接來自用戶端。

### <a name="the-command-handler-class"></a>命令處理常式類別

您應該實作每個命令的特定命令處理常式類別。 這是模式的運作方式，而且您將在其中使用的命令物件、 網域物件和基礎結構的儲存機制物件。 命令處理常式事實上是 CQRS 和 DDD 方面的應用程式層的中心。 不過，所有網域邏輯應該都包含在網域類別 — 彙總根 （root 實體） 內子實體或[網域服務](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/)，但不是在的命令處理常式，這是從應用程式類別圖層。

命令處理常式收到命令，並取得使用彙總的結果。 結果應該是命令執行成功或是發生例外狀況。 例外狀況，在系統狀態應該維持不變。

命令處理常式通常會採取下列步驟：

-   它接收的命令物件，例如 DTO (從[暫留處理器](https://en.wikipedia.org/wiki/Mediator_pattern)或其他基礎結構物件)。

-   它會驗證命令有效 （如果未經過暫留處理器）。

-   它會具現化的目前命令目標的彙總的根執行個體。

-   它會在彙總根執行個體，從命令取得所需的資料執行方法。

-   它會保存在彙總至其相關資料庫的新狀態。 這最後一項作業是實際的交易。

一般而言，是命令處理常式會處理由其彙總根 (root entity) 的單一彙總。 如果多個彙總應該受到接收單一命令，您可以使用網域事件狀態或動作散佈在多個彙總

此處的重點是處理命令時，所有網域邏輯都應在網域模型內 （彙總），全部封裝，且可供單元測試。 命令處理常式只可作為從資料庫取得網域模型的方法和最後一個步驟，通知基礎結構層級 （儲存機制），來保存變更的模式變更。 這種方法的優點是您可以不需要變更基礎結構的圖層，是連接層級 （命令處理常式，Web API 的應用程式中的程式碼重構網域中的邏輯隔離、 完整封裝、 豐富、 行為網域模型儲存機制等等）。

當命令處理常式收到複雜，太多邏輯，可能是程式碼的氣味。 檢閱其內容，和如果您發現網域邏輯，重構程式碼將該網域行為移至網域物件 （彙總根及子實體） 的方法。

例如命令處理常式類別中，下列程式碼會顯示您所見的相同 CreateOrderCommandHandler 類別在本指南的開頭。 在此情況下我們所反白顯示的控制代碼方法並搭配網域模型物件/彙總作業。

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

以下是命令處理常式應該採取的額外步驟：

-   使用命令的資料操作與彙總根方法行為。

-   在內部網域的物件內引發網域事件時執行的交易，但是，這是透明化的命令處理常式的觀點。

-   如果成功的彙總作業結果和在交易完成之後，會引發整合事件命令處理常式。 （這些可能也會引發由像儲存機制的基礎結構類別。）

#### <a name="additional-resources"></a>其他資源

-   **標記 Seemann。在界限，應用程式是不是物件導向**
    [*http://blog.ploeh.dk/2011/05/31/AttheBoundaries，ApplicationsareNotObject 導向 /*](http://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/)

-   **命令和事件**
    [*http://cqrs.nu/Faq/commands-and-events*](http://cqrs.nu/Faq/commands-and-events)

-   **命令處理常式有何作用？** 
     [ *http://cqrs.nu/Faq/command-handlers*](http://cqrs.nu/Faq/command-handlers)

-   **Jimmy Bogard：網域命令模式 – 處理常式**
    [*https://jimmybogard.com/domain-command-patterns-handlers/*](https://jimmybogard.com/domain-command-patterns-handlers/)

-   **Jimmy Bogard：網域命令模式 – 驗證**
    [*https://jimmybogard.com/domain-command-patterns-validation/*](https://jimmybogard.com/domain-command-patterns-validation/)

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a>命令處理程序管線： 如何觸發命令處理常式

下一個問題是如何叫用的命令處理常式。 您可以手動呼叫從每個相關的 ASP.NET Core 控制站。 不過，方法會太結合，並不理想。

其他兩個主要選項，也就是建議的選項，包括：

-   透過記憶體中的暫留處理器模式成品。

-   使用非同步的訊息佇列，控制站和處理常式之間。

### <a name="using-the-mediator-pattern-in-memory-in-the-command-pipeline"></a>在命令管線中使用的傳遞模式 （記憶體）

所示圖 9-21，CQRS 方法在您使用智慧型物，類似於記憶體中匯流排，也就是聰明，可以重新導向至正確的命令處理常式根據 DTO 所接收之命令的類型。 元件之間的單一黑色箭號代表物件 （在許多情況下，插入透過 DI） 之間的相依性，使用相關的互動。

![](./media/image22.png)

**圖 9-21**。 在單一的 CQRS 微服務的過程中使用的暫留處理器模式

使用暫留處理器模式合理的原因是，在企業應用程式處理要求變得複雜。 要加入跨領域像記錄、 驗證、 稽核及安全性的考量中開啟的數目。 在這些情況下，您可以依賴暫留處理器管線 (請參閱[暫留處理器模式](https://en.wikipedia.org/wiki/Mediator_pattern)) 提供方法，針對這些額外的行為或跨碼橫切入顧慮。

暫留處理器是封裝 「 如何 」 在此程序的物件： 它會協調執行根據狀態、 叫用方式是命令處理常式時，或裝載您提供給此處理常式。 暫留處理器元件您可以使用套用跨碼橫切入顧慮集中式和透明的方式套用裝飾項目 (或[管線行為](https://github.com/jbogard/MediatR/wiki/Behaviors)自暫留處理器 v3)。 (如需詳細資訊，請參閱[裝飾項目的模式](https://en.wikipedia.org/wiki/Decorator_pattern)。)

裝飾項目和表現方式，類似[外觀導向程式設計 (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming)、 僅套用至受暫留處理器元件的特定處理序管線。 會根據套用在 AOP 可實作跨碼橫切入顧慮方面*外觀 weavers*插入在編譯時期，或根據物件呼叫攔截。 這兩種典型的 AOP 方法有時稱為一樣"magic"，所以不容易看到 AOP 方式執行其工作。 當處理嚴重的問題或 bug，AOP 很難進行偵錯。 相反地，這些裝飾項目/這些行為屬於明確和套用暫留處理器，內容中，才是偵錯更可預測且容易。

例如，在排序微服務 eShopOnContainers，我們實作兩個範例裝飾項目， [LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs)類別和[ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs)類別。 下一節中說明的 decorator 實作。 請注意，在未來版本中，eShopOnContainers 會將移轉至[MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)並移至[行為](https://github.com/jbogard/MediatR/wiki/Behaviors)而不是使用裝飾項目。

### <a name="using-message-queues-out-of-proc-in-the-commands-pipeline"></a>在命令管線中使用訊息佇列 （跨處理序）

另一個選擇是使用非同步示圖 9-22，根據代理程式 」 或 「 訊息佇列的訊息。 該選項也可以結合的命令處理常式的權限之前，暫留處理器元件。

![](./media/image23.png)

**圖 9 22**。 使用 CQRS 命令的訊息佇列 （現成可用的處理程序和處理序間通訊）

使用訊息佇列以接受命令可進一步複雜命令的管線，因為您可能需要將管線拆解成兩個處理序連接到外部訊息佇列。 儘管如此，則應如果您需要已改善延展性和效能根據非同步訊息。 請考慮在圖 9-22，控制器只會將命令訊息排入佇列，並傳回。 然後命令處理常式會處理自己的步調的訊息。 也就是最大佇列的好處，訊息佇列可以做為案例的緩衝區上，hyper-v 延展性時所需，例如股票或任何其他輸入資料量很高的案例中。

不過，由於訊息佇列的非同步本質，您需要找出有關成功或失敗的命令的處理序用戶端應用程式的通訊方式。 一般而言，您應該永遠不會使用"fire and forget"命令。 每個商務應用程式必須知道是否命令已處理成功，或至少驗證和接受。

因此，能夠以回應至用戶端驗證命令訊息送出至非同步的佇列之後會增加複雜性您的系統，相較於同處理序的命令處理程序執行交易後傳回作業的結果。 使用佇列，您可能需要返回命令處理，透過其他作業結果訊息，就會需要額外的元件和自訂通訊系統中的結果。

此外，非同步命令是單向的命令，這在許多情況下可能不需要如下列的有趣 exchange Burtsev Alexey 之間 Greg Young 中所述[線上交談](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):

\[Burtsev Alexey\]找到許多程式碼的人，使用非同步命令處理或訊息沒有任何原因，若要這樣做的其中一種方式命令 （它們不會進行某些長時間作業，它們不會執行外部非同步程式碼，它們不甚至會跨越應用程式界限是使用訊息匯流排）。 這些原因會造成這種不必要的複雜性？ 事實上，我還沒看過 CQRS 為止，封鎖命令處理常式程式碼範例雖然它會在大部分情況下正常運作。

\[Greg Young\] \[...\]非同步命令不存在，則可以實際另一個事件。 如果我必須接受您傳送給我，並引發事件，如果我不同意，就無法再您告訴我執行一些動作。 它是您告知我已完成的項目。 這看起來像是在一開始，有些微的差異，但有許多影響。

非同步命令會大幅增加系統的複雜性，因為沒有任何簡易方式可表示失敗。 因此，非同步命令不建議您使用以外需要調整需求時，或在特殊情況下通訊透過訊息內部的 microservices 時。 在這些情況下，您必須設計個別的報告和復原系統失敗。

在 eShopOnContainers 初始版本中，我們決定將使用同步命令處理，從 HTTP 要求啟動和暫留處理器模式所驅動。 可輕鬆地讓您傳回成功或失敗的處理程序中[CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs)實作。

在任何情況下，這應該是根據您應用程式 」 或 「 微服務的業務決策。

## <a name="implementing-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a>實作命令處理程序管線，與傳遞模式 (MediatR)

當做範例實作，本指南所建議使用同處理序管線根據磁碟機命令擷取的暫留處理器模式和路由，在記憶體中，加入正確的命令處理常式。 本指南也建議套用裝飾項目或[行為](https://github.com/jbogard/MediatR/wiki/Behaviors)以便將跨領域重點分開。

如需在.NET Core 的實作，有多個開放原始碼程式庫提供實作暫留處理器模式。 使用本指南中的程式庫是[MediatR](https://github.com/jbogard/MediatR)開放原始碼程式庫 （Jimmy Bogard 所建立），但是您無法使用另一種方法。 MediatR 是小型且簡單的程式庫，可讓您處理命令，例如，記憶體中訊息時套用裝飾項目或行為。

使用暫留處理器模式可協助您減少結合，並找出要求的工作，自動連接到執行該工作的處理常式時的考量，在此情況下，加入命令處理常式。

檢閱本指南時，已由 Jimmy Bogard 說明另一個使用暫留處理器模式的好理由：

我認為值得您注意以下測試可能是 – 不錯的一致視窗提供到您的系統行為。 要求中，回應外。我們找到這個部分中建置以一致的方式運作的測試很有價值。

首先，讓我們看控制器程式碼，您實際上會使用暫留處理器物件。 如果您不使用暫留處理器物件，您必須將所有的相依性該控制站，例如記錄器物件與其他人。 因此，建構函式會變得相當複雜。 相反地，如果您使用的暫留處理器物件，您的控制站的建構函式可以是簡單許多，具有少數的相依性，而不是，如果您在其中每個跨領域作業，如下列範例所示，您會有許多相依性：

```csharp
public class OrdersController : Controller
{
    public OrdersController(IMediator mediator,
        IOrderQueries orderQueries)
    // ...
```

您可以看到暫留處理器提供全新和簡式 Web API 控制器建構函式。 此外，在控制器方法中，將命令傳送到的暫留處理器物件的程式碼會幾乎一行：

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

為了讓 MediatR 知道您的命令處理常式類別，您需要註冊 IoC 容器中的暫留處理器類別和命令處理常式類別。 根據預設，MediatR 使用 Autofac 與 IoC 容器，但是您也可以使用內建 ASP.NET Core IoC 容器或 MediatR 所支援的其他任何容器。

下列程式碼會示範如何使用 Autofac 模組時，註冊暫留處理器的類型和命令。

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

因為每個命令處理常式實作具有泛型 IAsyncRequestHandler 介面&lt;T&gt;並接著檢查 RegisteredAssemblyTypes 物件，因為在處理常式所能夠與使用其命令處理常式中，每個命令，關聯性所述的 CommandHandler 類別，如下列範例所示：

```csharp
public class CreateOrderCommandHandler
  : IAsyncRequestHandler<CreateOrderCommand, bool>
{
```

這是與命令相關聯的命令處理常式的程式碼。 此處理常式是只簡單的類別，但它繼承自 RequestHandler&lt;T&gt;，並且 MediatR 讓它取得用來叫用正確的裝載。

## <a name="applying-cross-cutting-concerns-when-processing-commands-with-the-mediator-and-decorator-patterns"></a>處理具有暫留處理器和裝飾項目模式的命令時，套用交互碼橫切入顧慮

沒有一件事： 無法暫留處理器管線套用跨碼橫切入顧慮。 您也可以查看 Autofac 註冊模組程式碼的結尾如何註冊裝飾項目類型，具體來說，自訂 LogDecorator 類別。

同樣地，請注意，未來版本的 eShopOnContainers 它會將移轉至[MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)並移至[行為](https://github.com/jbogard/MediatR/wiki/Behaviors)而不是使用裝飾項目。

確認[LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs)類別可以實作下列程式碼記錄正在執行的命令處理常式以及它是否成功與否的相關資訊。

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

只要實作這個裝飾項目類別，而它使用管線將透過 MediatR 處理的所有命令將會都記錄執行的相關資訊。

排序微服務 」 也適用於針對基本驗證，第二個 decorator eShopOnContainers [ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs)類別依賴[FluentValidation](https://github.com/JeremySkinner/FluentValidation)程式庫中所示下列程式碼：

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

然後，根據[FluentValidation](https://github.com/JeremySkinner/FluentValidation)程式庫，我們建立驗證資料隨 CreateOrderCommand，如下列程式碼所示：

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

您可以建立額外的驗證。 這是非常簡潔且更簡潔的方式來實作命令驗證。

類似的方式，您可以實作其他裝飾項目，其他部分為跨領域考量您想要處理它們時，套用至命令。

#### <a name="additional-resources"></a>其他資源

##### <a name="the-mediator-pattern"></a>暫留處理器模式

-   **暫留處理器模式**
    [*https://en.wikipedia.org/wiki/Mediator\_模式*](https://en.wikipedia.org/wiki/Mediator_pattern)

##### <a name="the-decorator-pattern"></a>裝飾項目模式

-   **裝飾項目模式**
    [*https://en.wikipedia.org/wiki/Decorator\_模式*](https://en.wikipedia.org/wiki/Decorator_pattern)

##### <a name="mediatr-jimmy-bogard"></a>MediatR (Jimmy Bogard)

-   **MediatR。** GitHub 儲存機制。
    [*https://github.com/jbogard/MediatR*](https://github.com/jbogard/MediatR)

-   **CQRS MediatR 與 AutoMapper**
    [*https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/*](https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/)

-   **將您的控制站上食物： 文章和命令。** 
     [ *https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/*](https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/)

-   **處理跨領域顧慮暫留處理器管線**
    [*https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/*](https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/)

-   **CQRS 和 REST： 完美的相符項**
    [*https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/*](https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/)

-   **MediatR 管線範例**
    [*https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/*](https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/)

-   **垂直配量測試設備 MediatR 和 ASP.NET Core**
    *<https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/>*

-   **Microsoft 相依性插入發行 MediatR 延伸**
    [*https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/*](https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/)

##### <a name="fluent-validation"></a>Fluent 應用程式開發的驗證

-   **Jeremy Skinner。FluentValidation。** GitHub 儲存機制。
    [*https://github.com/JeremySkinner/FluentValidation*](https://github.com/JeremySkinner/FluentValidation)

>[!div class="step-by-step"]
[上一個](microservice-application-layer-web-api-design.md) [下一步] (.../implement-resilient-applications/index.md)
