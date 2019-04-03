---
title: 使用 Web API 實作微服務應用程式層
description: .NET 微服務：容器化 .NET 應用程式的架構 | 了解相依性插入和中繼程序模式，以及它們在 Web API 應用程式層的實作詳細資料。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: 72ed265284db9d112a0b1e3b966d206dd7f3d1cc
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2019
ms.locfileid: "58464888"
---
# <a name="implement-the-microservice-application-layer-using-the-web-api"></a>使用 Web API 實作微服務應用程式層

## <a name="use-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a>使用相依性插入將基礎結構物件插入至應用程式層

如前所述，應用程式層可以實作為要建置成品 (組件) 的一部分，例如在 Web API 專案或 MVC Web 應用程式專案內。 如果是使用 ASP.NET Core 所建置的微服務，則應用程式層通常會是 Web API 程式庫。 如果您想要區隔來自 ASP.NET Core 的內容 (其基礎結構和您的控制站) 與自訂應用程式層程式碼，則也可以將應用程式層放在個別的類別庫中，但這是選擇性。

例如，訂購微服務的應用程式層程式碼可直接實作為 **Ordering.API** 專案 (ASP.NET Core Web API 專案) 的一部分，如圖 7-23 所示。

![Ordering.API 微服務的 [方案總管] 檢視，顯示 Application 資料夾下的子資料夾：Behaviors、Commands、DomainEventHandlers、IntegrationEvents、Models、Queries 和 Validations。](./media/image20.png)

**圖 7-23**。 Ordering.API ASP.NET Core Web API 專案中的應用程式層

ASP.NET Core 包含簡單[內建 IoC 容器](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (由 IServiceProvider 介面代表)，它預設會支援建構函式插入，ASP.NET 則是透過 DI 提供特定服務。 ASP.NET Core 會將「服務」詞彙用於透過 DI 插入的任何已註冊類型。 您可以在應用程式 Startup 類別的 ConfigureServices 方法中設定內建容器服務。 相依性實作所在之服務為類型所需且以 IoC 容器註冊的服務。

一般而言，您會想要插入可實作基礎結構物件的相依性。 要插入的極典型相依性是存放庫。 但是，您可以插入可能會有的任何其他基礎結構相依性。 為求更簡單的實作，您可以直接插入工作單元模式物件 (EF DbContext 物件)，因為 DBContext 也是您基礎結構持續性物件的實作。

在下列範例中，您可以查看 .NET Core 如何透過建構函式插入所需的存放庫物件。 此類別是命令處理常式，我們將在下節中討論。

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

此類別會使用已插入的存放庫來執行交易，並持續保存狀態變更。 不論該類別是命令處理常式、ASP.NET Core Web API 控制器方法還是 [DDD 應用程式服務](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/)。 它最終會是使用存放庫、領域實體和其他應用程式協調的簡單類別，其形式與命令處理常式類似。 所有提及類別的相依性插入運作方式都相同，如根據建構函式使用 DI 的範例所示。

### <a name="register-the-dependency-implementation-types-and-interfaces-or-abstractions"></a>註冊相依性實作類型和介面或抽象物件

您需要先知道在哪裡註冊介面和類別，以產生透過 DI 插入至 應用程式類別的物件，才能使用透過建構函式所插入的物件  (例如根據建構函式的 DI，如前所述)。

#### <a name="use-the-built-in-ioc-container-provided-by-aspnet-core"></a>使用 ASP.NET Core 所提供的內建 IoC 容器

當您使用 ASP.NET Core 所提供的內建 IoC 容器時，會註冊您想要在 Startup.cs 檔案的 ConfigureServices 方法中插入的類型，如下列程式碼所示：

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

在 IoC 容器中註冊類型時的最常見模式是註冊一組類型：介面和其相關實作類別。 然後，當您透過任何建構函式從 IoC 容器要求物件時，會要求特定類型之介面的物件。 例如，在上述範例中，最後一行指出有任何建構函式與 IMyCustomRepository (介面或抽象) 相依時，IoC 容器將會插入 MyCustomSQLServerRepository 實作類別的執行個體。

#### <a name="use-the-scrutor-library-for-automatic-types-registration"></a>使用 Scrutor 程式庫進行自動類型註冊

在 .NET Core 中使用 DI 時，您可能想要可以掃描組件，並依照慣例自動註冊其類型。 ASP.NET Core 目前未提供此功能。 不過，您可以使用 [Scrutor](https://github.com/khellang/Scrutor) 程式庫來進行這項作業。 當您有數個需要在 IoC 容器中註冊的類型時，這種方法十分方便。

#### <a name="additional-resources"></a>其他資源

- **Matthew King：使用 Scrutor 註冊服務** \
  [https://www.mking.net/blog/registering-services-with-scrutor](https://www.mking.net/blog/registering-services-with-scrutor)

- **Kristian Hellang：Scrutor.** GitHub 存放庫。 \
  [https://github.com/khellang/Scrutor](https://github.com/khellang/Scrutor)

#### <a name="use-autofac-as-an-ioc-container"></a>使用 Autofac 作為 IoC 容器

您也可以使用其他 IoC 容器，並將它們插入至 ASP.NET Core 管道，就像 eShopOnContainers 中的訂購微服務一樣，而訂購微服務使用 [Autofac](https://autofac.org/)。 使用 Autofac 時，通常會透過模組來註冊類型，以讓您根據類型位置來分割多個檔案之間的註冊類型，就像您將應用程式類型分散到多個類別程式庫一樣。

例如，下列 [Autofac 應用程式模組](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs)適用於具有您想要插入之類型的 [Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) 專案。

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

Autofac 也有功能可[掃描組件以及按命名慣例註冊類型](https://autofac.readthedocs.io/en/latest/register/scanning.html)。

註冊程序和概念與您可向內建 ASP.NET Core IoC 容器註冊類型的方式極為類似，但使用 Autofac 時的語法略為不同。

在範例程式碼中，會一起註冊抽象 IOrderRepository 與實作類別 OrderRepository。 這表示只要建構函式透過 IOrderRepository 抽象或介面來宣告相依性，IoC 容器就會插入 OrderRepository 類別的執行個體。

執行個體範圍類型決定如何在相同服務或相依性的要求之間共用執行個體。 提出相依性要求時，IoC 容器可以傳回下列結果：

- 一個存留期範圍有單一執行個體 (在 ASP.NET Core IoC 容器中稱為「範圍」)。

- 一個相依性有新的執行個體 (在 ASP.NET Core IoC 容器中稱為「暫時性」)。

- 跨所有使用 IoC 容器的物件所共用的單一執行個體 (在 ASP.NET Core IoC 容器中稱為「單一」).

#### <a name="additional-resources"></a>其他資源

- **ASP.NET Core 中的相依性插入簡介** \
  [https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)

- **Autofac.** 正式文件。 \
  [http://docs.autofac.org/en/latest/](http://docs.autofac.org/en/latest/)

- **比較 ASP.NET Core IoC 容器服務存留期與 Autofac IoC 容器執行個體範圍 - Cesar de la Torre。** \
  [https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)

## <a name="implement-the-command-and-command-handler-patterns"></a>實作命令和命令處理常式模式

在上節所顯示的透過建構函式的 DI 範例中，IoC 容器將會透過類別中的建構函式來插入存放庫。 但，其確切插入位置為何？ 在簡單的 Web API 中 (例如，eShopOnContainers 的目錄微服務)，您是使用控制器建構函式在 MVC 控制器層級插入它們，當成 ASP.NET Core 要求管線的一部分。 不過，在此區段的初始程式碼中 (eShopOnContainers 的 Ordering.API 服務中的 [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) 類別)，是透過特定命令處理常式的建構函式來插入相依性。 讓我們說明什麼是命令處理常式以及您想要使用它的原因。

命令模式本質上與本指南稍早介紹的 CQRS 模式有關。 CQRS 有兩端。 第一個區域是搭配使用簡化查詢與 [Dapper](https://github.com/StackExchange/dapper-dot-net) 微 ORM (先前已說明過) 的查詢。 第二個區域是命令，這是交易的起點以及服務外部的輸入通道。

如圖 7-24 所示，模式的基礎是接受來自用戶端的命令，然後根據領域模型規則處理它們，最後保持交易狀態。

![CQRS 的寫入端高層級檢視：UI 應用程式透過連接到 CommandHandler 的 API 來傳送命令，這依賴領域模型和基礎結構來更新資料庫。](./media/image21.png)

**圖 7-24**. CQRS 模式中命令或「交易端」的高階檢視

### <a name="the-command-class"></a>命令類別

命令是一種要求，讓系統執行可變更系統狀態的動作。 命令是命令式的，而且只應該處理一次。

因為命令是命令式的，所以通常是透過命令式方式使用動詞進行命名 (例如，"create" 或 "update")，而且可能包含彙總類型 (例如 CreateOrderCommand)。 與事件不同，命令不是過去的事實；它只是要求，因此可能會遭拒絕。

程序管理員指示彙總來執行動作時，命令可能因起始要求的使用者而源自 UI，或源自程序管理員。

命令的重要特性是單一接收者只應該處理它一次。 原因是命令是您想要在應用程式中執行的單一動作或交易。 例如，相同的訂單建立命令只應該處理一次。 這是命令與事件之間的重要差異。 可能會多次處理事件，因為許多系統或微服務可能都會對事件感興趣。

此外，如果命令不是等冪，則命令務必只處理一次。 如果基於命令本質或系統處理命令的方式，命令可以執行多次，而不變更結果，則命令為等冪。

透過領域商務規則和非變異值而變得有意義時，最好讓命令和更新設為等冪。 例如，若要使用相同的範例，如果基於任何原因 (重試邏輯、駭客等等) 相同的 CreateOrder 命令到達您的系統多次，則您應該可以識別它，並確保未建立多個訂單。 若要這樣做，您需要在作業中附加某種類型的身分識別，並識別是否已處理命令或更新。

您將命令傳送給單一接收者；請不要發行命令。 發佈適用於指出事實的事件：發生了某事，而事件接收者可能對此感興趣。 如果是事件，則發行者不會關心哪些接收器收到事件或其處理方式。 但是先前各節中已介紹過的網域或整合事件則不同。

命令是使用類別進行實作，而類別包含資料欄位或具有執行該命令所需之所有資訊的集合。 命令是一種特殊的資料轉送物件 (DTO)，專門用來要求變更或交易。 命令本身只根據處理命令所需的資訊，而不需要其他資訊。

下列範例示範簡化 CreateOrderCommand 類別。 這是 eShopOnContainers 訂購微服務中所使用的不可變命令。

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

    public CreateOrderCommand(List<BasketItem> basketItems, string city,
        string street,
        string state, string country, string zipcode,
        string cardNumber, string cardHolderName, DateTime cardExpiration,
        string cardSecurityNumber, int cardTypeId) : this()
    {
        _orderItems = MapToOrderItems(basketItems);
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

基本上，此命令類別包含您使用領域模型物件來執行商務交易所需的所有資料。 因此，命令只是包含唯讀資料但沒有行為的資料結構。 命令的名稱會指出其用途。 在許多 C# 這類語言中，命令會呈現為類別，但就實際物件導向意義而言，它們不是真正的類別。

作為其他特性，命令是不可變的，因為預期的用法是領域模型會直接處理它們。 它們在其預測存留期間不需要變更。 在 C# 類別中，沒有任何 setter 或變更內部狀態的其他方法，可以達到不變性。

請記住，如果您打算或希望讓命令經過序列化/還原序列化程序，則屬性必須具有私用 setter 和 `[DataMember]` (或 `[JsonProperty]`) 屬性，否則還原序列化程式無法在目的地使用必要值重新建構物件。

例如，建立訂單的命令類別可能類似您想要建立之訂單的資料，但您可能不需要相同的屬性。 例如，因為尚未建立訂單，所以 CreateOrderCommand 沒有訂單識別碼。

許多命令類別都可以簡單，只需要某個需要變更之狀態的幾個欄位。 就是，如果您使用與下列類似的命令，只將訂單的狀態從「處理中」變更為「已付款」或「已出貨」：

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

有些開發人員會區隔其 UI 要求物件與其命令 DTO，但這只是喜好設定。 這是沒有附加價值的冗長區隔，而且物件的形狀幾乎完全相同。 例如，在 eShopOnContainers 中，有些命令直接來自用戶端。

### <a name="the-command-handler-class"></a>命令處理常式類別

您應該為每個命令實作特定命令處理常式類別。 這是模式運作方式，而且它是您將在其中使用命令物件、領域物件和基礎結構存放庫物件的位置。 命令處理常式實際上是 CQRS 和 DDD 的應用程式層中心。 不過，所有領域邏輯都應該包含在領域類別內，即彙總根 (根實體)、子實體或[領域服務](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/)內，但不在本身為應用程式層中類別的命令處理常式內。

命令處理常式類別提供強式的墊腳石來達成前節中所述的單一職責原則 (SRP)。

命令處理常式會收到命令，並取得所使用彙總的結果。 結果應該是命令執行成功或是發生例外狀況。 如果是例外狀況，則系統狀態應該會維持不變。

命令處理常式通常會採取下列步驟：

- 接收命令物件，例如 DTO (從[中繼程序](https://en.wikipedia.org/wiki/Mediator_pattern)或其他基礎結構物件)。

- 驗證命令有效 (如果未經中繼程序驗證)。

- 具現化為目前命令目標的彙總根執行個體。

- 對彙總根執行個體執行方法，以透過命令取得必要資料。

- 它會將彙總的新狀態持續保存至其相關資料庫。 這個最後一項作業是實際交易。

一般而言，命令處理常式會處理其彙總根 (根實體) 所驅動的單一彙總。 如果接收單一命令會影響多個彙總，則您可以使用領域事件將狀態或動作散佈到多個彙總。

這裡的重點是處理命令時，所有領域邏輯都應該位在領域模型 (彙總) 內、全部進行封裝，而且可進行單元測試。 命令處理常式只是作為從資料庫取得領域模型的方法以及最後一個步驟，以告知基礎結構層級 (存放庫) 在模型變更時持續保存變更。 這種方法的優點是您不需要變更應用程式或基礎結構層中的程式碼，即可在隔離、完整封裝且豐富的行為領域模型中重構領域邏輯，而這些層級是連接層級 (命令處理常式、Web API、存放庫等等)。

命令處理常式因太多邏輯而變得複雜時，就會像程式碼。 檢閱其內容，而且，如果您發現領域邏輯，請重構程式碼，以將該領域行為移至領域物件 (彙總根和子實體) 的方法。

作為命令處理常式類別範例，下列程式碼會示範您在本章開頭看到的相同 CreateOrderCommandHandler 類別。 在此情況下，我們想要反白顯示 Handle 方法以及具有領域模型物件/彙總的作業。

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

下列是命令處理常式應該採取的額外步驟：

- 使用命令的資料來操作彙總根方法和行為。

- 在領域物件內部，於執行交易時引發領域事件，但這從命令處理常式觀點是透明的。

- 如果彙總的作業結果為成功，則在交易完成後，會引發整合事件。 (這些可能也是由存放庫這類基礎結構類別所引發)。

#### <a name="additional-resources"></a>其他資源

- **Mark Seemann：應用程式在界限不是物件導向的** \
  [https://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/](https://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/)

- **命令和事件** \
  [http://cqrs.nu/Faq/commands-and-events](http://cqrs.nu/Faq/commands-and-events)

- **命令處理常式有何作用？** \
  [http://cqrs.nu/Faq/command-handlers](http://cqrs.nu/Faq/command-handlers)

- **Jimmy Bogard：網域命令模式 – 處理常式** \
  [https://jimmybogard.com/domain-command-patterns-handlers/](https://jimmybogard.com/domain-command-patterns-handlers/)

- **Jimmy Bogard：網域命令模式 – 驗證** \
  [https://jimmybogard.com/domain-command-patterns-validation/](https://jimmybogard.com/domain-command-patterns-validation/)

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a>命令處理序管道：如何觸發命令處理常式

下一個問題是如何叫用命令處理常式。 您可以從每個相關 ASP.NET Core 控制器中手動呼叫它。 不過，該方法結合太多，並不理想。

另兩個主要選項是建議的選項，包括：

- 透過記憶體內部中繼程序模式成品。

- 在控制器與處理常式之間使用非同步訊息佇列。

### <a name="use-the-mediator-pattern-in-memory-in-the-command-pipeline"></a>在命令管線中使用中繼程序模式 (記憶體內部)

如圖 7-25 所示，在 CQRS 方法中，您使用與記憶體內部匯流排類似的智慧型中繼程序，而它聰明到可以根據所收到的命令或 DTO 類型，重新導向至正確的命令處理常式。 元件之間的單一黑色箭號代表物件 (在許多情況下，是透過 DI 插入) 與其相關互動之間的相依性。

![放大前一個映像：ASP.NET Core 控制器會將命令傳送給 MediatR 的命令管線，讓它們取得適當的處理常式。](./media/image22.png)

**圖 7-25**。 在單一 CQRS 微服務過程中使用中繼程序模式

使用中繼程序模式的合理原因是，在企業應用程式中，處理要求會變得複雜。 您想要可以新增已開啟數目的跨領域關注，例如記錄、驗證、稽核和安全性。 在這些情況下，您可以依賴中繼程序管道 (請參閱[中繼程序模式](https://en.wikipedia.org/wiki/Mediator_pattern)) 提供這些額外行為或跨領域關注的方法。

中繼程序是封裝此處理序「作法」的物件：它會根據狀態、命令處理常式叫用方式或您提供給處理常式的承載來協調執行。 使用中繼程序元件，即可套用裝飾項目 (或自 [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) 以來的[管道行為](https://github.com/jbogard/MediatR/wiki/Behaviors))，以透過集中且透明的方式套用跨領域關注。 如需詳細資訊，請參閱[裝飾項目模式](https://en.wikipedia.org/wiki/Decorator_pattern)。

裝飾項目和行為類似[層面導向程式設計 (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming)，僅套用至中繼程序元件所管理的特定處理序管線。 根據在編譯期間插入的「層面編織程序」或根據物件呼叫攔截，套用 AOP 中實作跨領域關注的層面。 這兩種典型 AOP 方法的運作有時稱為「就像變魔術一樣」，因為不容易看到 AOP 的運作工作。 處理嚴重問題或 Bug 時，AOP 很難進行偵錯。 另一方面，這些裝飾項目/行為十分明確，而且只會套用至中繼程序內容，因此，偵錯更容易預測且更為輕鬆。

例如，在 eShopOnContainers 訂購微服務中，我們已實作兩個範例行為：[LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) 類別和 [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) 類別。 下節示範 eShopOnContainers 如何使用 [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) [行為](https://github.com/jbogard/MediatR/wiki/Behaviors)來說明行為的實作。

### <a name="use-message-queues-out-of-proc-in-the-commands-pipeline"></a>在命令管線中使用訊息佇列 (跨處理序)

另一個選擇是根據訊息代理程式或訊息佇列來使用非同步訊息，如圖 7-26 所示。 該選項也可以與命令處理常式正前方的中繼程序一起使用。

![命令的管線也可以由高可用性訊息佇列處理，將命令傳遞給適當的處理常式。](./media/image23.png)

**圖 7-26**。 搭配使用訊息佇列 (跨處理序和處理序間通訊) 與 CQRS 命令

使用訊息佇列接受命令可能會讓命令管道更為複雜，因為您可能需要將管道分割成透過外部訊息佇列所連接的兩個處理序。 儘管如此，如果您需要擁有根據非同步訊息的已改善延展性和效能，則應該使用它。 請考慮在圖 7-26 的情況下，控制器只會將命令訊息公佈至佇列並傳回。 命令處理常式接著會依自己的步調來處理訊息。 這是佇列的最大好處：訊息佇列可以作為需要超級延展性時的緩衝區，例如針對股票或任何其他具有大量輸入資料的案例。

不過，因為訊息佇列的非同步本質，所以您需要找出與用戶端應用程式溝通命令處理序成功或失敗的方式。 一般而言，您應該永遠不會使用「發動就忘記」命令。 每個商務應用程式都需要知道是否已成功處理命令，或至少已驗證和接受命令。

因此，與在執行交易之後傳回作業結果的同處理序命令處理序相較之下，可以在驗證已提交給非同步佇列的命令訊息之後回應用戶端，可能會增加系統的複雜性。 使用佇列，您可能需要透過其他作業結果訊息來傳回命令處理序結果，而這需要系統中的額外元件和自訂通訊。

此外，非同步命令是單向命令，而這在許多情況下可能不需要，如 Burtsev Alexey 與 Greg Young 在[線上對話](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ)中的下列有趣交流所述：

> \[Burtsev Alexey\] 我發現人員在許多程式碼中沒有任何原因地使用非同步命令處理或單向命令訊息 (他們不會執行某個長時間作業、不會執行外部非同步程式碼，甚至不會跨應用程式界限使用訊息匯流排)。 為什麼它們會造成這種不必要的複雜性？ 實際上，我到目前為止還沒有看過具有封鎖命令處理常式的 CQRS 程式碼範例，雖然它只會在大部分情況下正常運作。
>
> \[Greg Young\] \[...\] 非同步命令不存在；它實際上是另一個事件。 如果我必須接受您傳送給我的內容，並在不同意時引發事件，您就不需要告訴我該做什麼\[亦即，它不是命令\]。 而是告訴我已完成哪項作業。 這在一開始略為不同，但有許多影響。

非同步命令可大幅增加系統複雜性，因為沒有任何簡單的方式可以指出失敗。 因此，不建議使用非同步命令，除非需要調整需求時，或在特殊情況下，透過訊息溝通內部微服務時。 在這些情況下，您必須針對失敗設計不同的報告和復原系統。

在 eShopOnContainers 初始版本中，我們決定使用從 HTTP 要求啟動並由中繼程序模式所驅動的同步命令處理。 這可輕鬆地讓您傳回處理序的成功或失敗，如同 [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) 實作一樣。

在任何情況下，這應該都是根據您應用程式或微服務商務需求的決策。

## <a name="implement-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a>使用中繼程序模式 (MediatR) 實作命令處理序管線

作為範例實作，本指南建議根據中繼程序模式來使用同處理序管道，在記憶體內部將命令擷取和路由命令驅動到正確命令處理常式。 本指南也會建議套用[行為](https://github.com/jbogard/MediatR/wiki/Behaviors)以區隔跨領域關注。

針對 .NET Core 中的實作，有多個開放原始碼程式庫可用來實作中繼程序模式。 本指南中所使用的程式庫是 [MediatR](https://github.com/jbogard/MediatR) 開放原始碼程式庫 (由 Jimmy Bogard 所建立)，但您可以使用另一種方法。 MediatR 是小型且簡單的程式庫，可讓您處理命令這類記憶體內部訊息，同時套用裝飾項目或行為。

使用中繼程序模式可協助您減少結合，並找出所要求工作的關注，同時自動連接至執行該工作的處理常式，在此情況下，是連接至命令處理常式。

檢閱本指南時，Jimmy Bogard 會說明另一個使用中繼程序模式的好理由：

> 我認為您可能需要注意這裡的測試 - 它提供不錯的一致窗口，讓您查看系統的行為。 要求進，回應出。我們發現層面在建置行為一致的測試時相當重要。

首先，讓我們看一下您實際使用中繼程序物件的範例 WebAPI 控制器。 如果您不是使用中繼程序物件，則需要插入該控制站的所有相依性，例如記錄器物件和其他項目。 因此，建構函式可能會相當複雜。 另一方面，如果您使用中繼程序物件，則控制器的建構函式可能會較為簡單，即只有一些相依性而不是許多相依性 (如果一個跨領域作業有一個相依性)，如下列範例所示：

```csharp
public class MyMicroserviceController : Controller
{
    public MyMicroserviceController(IMediator mediator,
                                    IMyMicroserviceQueries microserviceQueries)
    // ...
```

您可以看到中繼程序提供全新和簡式 Web API 控制器建構函式。 此外，在控制器方法內，將命令傳送至中繼程序物件的程式碼幾乎就是一行：

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

### <a name="implement-idempotent-commands"></a>實作等冪命令

在 **eShopOnContainers** 中，比上述更進階的範例是從訂購微服務提交 CreateOrderCommand 物件。 但因為訂購商務程序比較複雜 (在我們的案例中，實際上是在 Basket 微服務中啟動它)，所以會從名為 >UserCheckoutAcceptedIntegrationEvent.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) 的整合事件處理常式中執行這個提交 CreateOrderCommand 物件的動作，而不是像上述較簡單的範例，從用戶端應用程式呼叫簡單的 WebAPI 控制器。

不過，將命令提交給 MediatR 的動作相當類似，如下列程式碼所示。

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

但是，此情況也略為更進階，因為我們也會實作等冪命令。 CreateOrderCommand 處理序應該是等冪，因此，如果相同的訊息因任何原因 (例如重試) 而透過網路進行複製，則相同的商務訂單只會處理一次。

實作方式是包裝商務命令 (在本例中是 CreateOrderCommand)，並將它內嵌到泛型 IdentifiedCommand，而這是透過來自網路且必須為等冪的每個訊息識別碼所追蹤。

在下列程式碼中，您可以看到 IdentifiedCommand 就只是具有識別碼和已包裝商務命令物件的 DTO。

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

然後，IdentifiedCommand 的 CommandHandler (名為 [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs)) 基本上會檢查資料表中是否已有為訊息一部分的識別碼。 如果已經存在，則不會再次處理該命令，因此它是等冪命令。 該基礎結構程式碼是透過下面所呼叫的 `_requestManager.ExistAsync` 方法來執行。

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

            // Send the embedded business command to mediator
            // so it runs its related CommandHandler
            var result = await _mediator.Send(message.Command);

            return result;
        }
    }
}
```

因為 IdentifiedCommand 就像是商務命令的信封，所以因不是重複識別碼而需要處理商務命令時，會採用該內部商務命令，並在從 [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) 執行 `_mediator.Send(message.Command)` 時，將它重新提交給中繼程序，如同上述程式碼的最後一個部分。

這樣一來，它會連結並執行商務命令處理常式，在本例中，是對 Ordering 資料庫執行交易的 [ CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs)，如下列程式碼所示。

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

### <a name="register-the-types-used-by-mediatr"></a>註冊 MediatR 所使用的類型

為了讓 MediatR 知道您的命令處理常式類別，您需要在 IoC 容器中註冊中繼程序類別和命令處理常式類別。 MediatR 預設會使用 Autofac 作為 IoC 容器，但您也可以使用內建 ASP.NET Core IoC 容器或 MediatR 所支援的任何其他容器。

下列程式碼示範在使用 Autofac 模組時，如何註冊中繼程序的類型和命令。

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

這是 MediatR 顯現魔力的地方。

因為每個命令處理常式都會實作泛型 `IAsyncRequestHandler<T>` 介面，所以註冊組件時，程式碼會使用 `RegisteredAssemblyTypes` 註冊所有標記為 `IAsyncRequestHandler` 的類型，同時基於 `CommandHandler` 類別所指出的關聯性而建立 `CommandHandlers` 與其 `Commands` 的關聯，如下列範例所示：

```csharp
public class CreateOrderCommandHandler
  : IAsyncRequestHandler<CreateOrderCommand, bool>
{
```

這是建立命令與命令處理常式之關聯的程式碼。 處理常式只是簡單類別，但它繼承自 `RequestHandler<T>`，其中 T 為命令類型，而且 MediatR 確定它是使用正確承載 (命令) 所叫用。

## <a name="apply-cross-cutting-concerns-when-processing-commands-with-the-behaviors-in-mediatr"></a>使用 MediatR 中的行為處理命令時會套用跨領域關注

還有一件事：可以將跨領域關注套用至中繼程序管道。 您也可以查看 Autofac 註冊模組程式碼結尾，了解如何註冊行為類型，特別是自訂 LoggingBehavior 類別和 ValidatorBehavior 類別。 但是，您也可以新增其他自訂行為。

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

該 [LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) 類別可以實作為下列程式碼，以記錄所執行命令處理常式的相關資訊以及是否成功。

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

只要實作此行為類別，以及在管線 (上文的 MediatorModule) 中登錄它，透過 MediatR 處理的所有命令都會記錄執行相關資訊。

eShopOnContainers 訂購微服務也會套用第二個行為來進行基本驗證，即依賴 [FluentValidation](https://github.com/JeremySkinner/FluentValidation) 程式庫的 [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) 類別，如下列程式碼所示：

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

如果驗證失敗，這裡的行為會引發例外狀況，但您也可以傳回結果物件，成功則包含命令結果，失敗則包含驗證訊息。 這樣可能更容易向使用者顯示驗證結果。

然後，根據 [FluentValidation](https://github.com/JeremySkinner/FluentValidation) 程式庫，我們建立使用 CreateOrderCommand 所傳遞之資料的驗證，如下列程式碼所示：

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

您可以建立額外驗證。 這是實作命令驗證的全新且更簡潔的方式。

使用類似的方式，您可以實作想要在處理命令時套用至命令之其他層面或跨領域關注的其他行為。

#### <a name="additional-resources"></a>其他資源

##### <a name="the-mediator-pattern"></a>中繼程序模式

- **中繼程序模式** \
  [https://en.wikipedia.org/wiki/Mediator\_pattern](https://en.wikipedia.org/wiki/Mediator_pattern)

##### <a name="the-decorator-pattern"></a>裝飾項目模式

- **裝飾項目模式** \
  [https://en.wikipedia.org/wiki/Decorator\_pattern](https://en.wikipedia.org/wiki/Decorator_pattern)

##### <a name="mediatr-jimmy-bogard"></a>MediatR (Jimmy Bogard)

- **MediatR.** GitHub 存放庫。 \
  [https://github.com/jbogard/MediatR](https://github.com/jbogard/MediatR)

- **CQRS 搭配 MediatR 和 AutoMapper** \
  [https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/](https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/)

- **讓您的控制項瘦身：POST 和命令。** \
  [https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/](https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/)

- **使用中繼程序管線處理跨領域關注** \
  [https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/](https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/)

- **CQRS 和 REST：完美搭配** \
  [https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/](https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/)

- **MediatR 管線範例** \
  [https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/](https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/)

- **MediatR 和 ASP.NET Core 的垂直配量測試固件** \
  [https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/](https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/)

- **適用於已發行之 Microsoft 相依性插入的 MediatR 延伸模組** \
  [https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/](https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/)

##### <a name="fluent-validation"></a>Fluent 驗證

- **Jeremy Skinner：FluentValidation.** GitHub 存放庫。 \
  [https://github.com/JeremySkinner/FluentValidation](https://github.com/JeremySkinner/FluentValidation)

> [!div class="step-by-step"]
> [上一頁](microservice-application-layer-web-api-design.md)
> [下一頁](../implement-resilient-applications/index.md)
