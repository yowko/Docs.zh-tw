---
title: "實作.NET Core 的微服務網域模型"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |實作.NET Core 的微服務網域模型"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 26c480a82ad7bb806734decebdfbe5b4a07998e6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-a-microservice-domain-model-with-net-core"></a>實作.NET Core 的微服務網域模型 

上一節所說明的基本設計原則和設計網域模型的模式。 現在就可以瀏覽使用.NET 核心實作網域模型的可能方式 (一般 C\#程式碼) 和 EF 核心。 請注意，您的網域模型將由只是您的程式碼。 它會有 EF EF 核心模型需求，但不是實際的相依性。 網域模型中，您應該不需要硬式相依性或 EF 核心或任何其他 ORM 的參考。

## <a name="domain-model-structure-in-a-custom-net-standard-library"></a>自訂的.NET 標準文件庫中的網域模型結構

EShopOnContainers 參考應用程式使用資料夾組織示範 DDD 模型應用程式。 您可能會發現不同的資料夾組織更清楚地進行通訊的應用程式的設計選擇。 您可以看到圖 9-10，排序網域模型中有兩個彙總、 順序彙總和買方彙總。 雖然您可能會有彙總以及組成的單一網域實體 （彙總根或根實體），每個彙總是網域實體和值物件的群組。

![](./media/image11.png)

**圖 9 10**。 EShopOnContainers 中順序的微服務的網域模型結構

此外，網域模型層會包含您的網域模型的基礎結構需求的儲存機制合約 （介面）。 換句話說，這些介面 express 哪些基礎結構層級必須實作的儲存機制和方式。 請務必儲存機制的實作會位於外部網域模型中的圖層，基礎結構層文件庫，讓網域模型層不"contaminated 」 應用程式開發介面或從基礎結構技術，例如 Entity Framework 的類別。

您也可以查看[SeedWork](https://martinfowler.com/bliki/Seedwork.html)資料夾包含自訂的基底類別，您可以使用您的網域實體和值做為基底物件，因此每個網域的物件類別中沒有多餘的程式碼。

## <a name="structuring-aggregates-in-a-custom-net-standard-library"></a>建構自訂的.NET 標準程式庫中的彙總

彙總是指叢集的網域物件群組在一起以符合交易一致性。 這些物件可能是的實體 （其中是彙總根或根實體） 的執行個體，再加上任何其他值的物件。

交易一致性表示彙總，就一定可以一致且結尾商務動作的最新狀態。 例如，順序彙總從順序微服務網域模型 eShopOnContainers 組成示圖 9-11。

![](./media/image12.png)

**圖 9 11**。 Visual Studio 方案中的彙總順序

如果您開啟的任何檔案在彙總的資料夾中，您可以看到如何標示為自訂的基底類別或介面，像實體或值的物件，以實作[Seedwork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork)資料夾。

## <a name="implementing-domain-entities-as-poco-classes"></a>POCO 類別以及實作網域實體

您實作網域模型，您可以在.NET 中建立 POCO 類別可實作網域實體。 在下列範例中，Order 類別被定義為實體和為彙總的根。 因為 Order 類別衍生自該實體的基底類別，它可以重複使用與實體相關的通用程式碼。 請記住，這些基底類別和介面會由您在網域模型專案中，因此您的程式碼，不像 EF ORM 從基礎結構程式碼。

```csharp
// COMPATIBLE WITH ENTITY FRAMEWORK CORE 1.0
// Entity is a custom base class with the ID
public class Order : Entity, IAggregateRoot
{
    public int BuyerId { get; private set; }
    public DateTime OrderDate { get; private set; }
    public int StatusId { get; private set; }
    public ICollection<OrderItem> OrderItems { get; private set; }
    public Address ShippingAddress { get; private set; }
    public int PaymentId { get; private set; }
    protected Order() { } //Design constraint needed only by EF Core
    public Order(int buyerId, int paymentId)
    {
        BuyerId = buyerId;
        PaymentId = paymentId;
        StatusId = OrderStatus.InProcess.Id;
        OrderDate = DateTime.UtcNow;
        OrderItems = new List<OrderItem>();
    }

    public void AddOrderItem(productName,
        pictureUrl,
        unitPrice,
        discount,
        units)
    {
        //...
        // Domain rules/logic for adding the OrderItem to the order
        // ...
        OrderItem item = new OrderItem(this.Id, ProductId, productName,
            pictureUrl, unitPrice, discount, units);
  
        OrderItems.Add(item);
    }
    // ...
    // Additional methods with domain rules/logic related to the Order aggregate
    // ...
}
```

請務必注意，這會是做 POCO 類別實作一個網域實體。 它並沒有直接的相依性 Entity Framework Core 上或任何其他基礎結構架構。 這個實作是正確的只要 C\#實作網域模型的程式碼。

此外，使用名為 IAggregateRoot 介面裝飾類別。 該介面是空的介面，有時也稱為*標記介面*，也就是只用於表示此實體類別也是彙總的根。

是標記介面有時會被視為反面模式;但是，它也會標示類別，尤其是該介面可能會發展出簡潔的方法。 屬性可以是標記的其他選擇，但較快旁邊 IAggregate 介面，而不是讓上述類別彙總屬性標記，請參閱基底類別 （實體）。 在任何情況下，它是 metter 的喜好設定。

具有彙總根表示大部分的程式碼相關的一致性，而且應該為 Order 彙總根類別 (例如，AddOrderItem 彙總將 OrderItem 物件時) 中的方法實作的彙總的實體的商務規則. 您不應該建立或更新 OrderItems 物件，獨立或直接;控制項和它的子實體的任何更新作業的一致性，必須保持 AggregateRoot 類別。

例如，您應該*不*執行任何命令處理常式方法或應用程式層的類別從下列動作：

```csharp
// WRONG ACCORDING TO DDD PATTERNS – CODE AT THE APPLICATION LAYER OR
// COMMAND HANDLERS
// Code in command handler methods or Web API controllers
//... (WRONG) Some code with business logic out of the domain classes ...
OrderItem myNewOrderItem = new OrderItem(orderId, productId, productName,
    pictureUrl, unitPrice, discount, units);

//... (WRONG) Accessing the OrderItems colletion directly from the application layer // or command handlers
myOrder.OrderItems.Add(myNewOrderItem);
//...
```

在此情況下，加入方法是完全加入資料、 直接存取 OrderItems 集合作業。 因此，大部分的網域邏輯、 規則或驗證相關的子實體的作業會分散應用程式層 （命令處理常式和 Web API 控制器）。

如果您移周圍彙總根，彙總根無法保證其非變異項目、 其有效性或其一致性。 最後將有之程式碼或交易式的指令碼。

若要依照 DDD 模式，實體必須沒有公用 setter 中的任何實體屬性。 在實體中的變更應該重點的明確方法以明確的通用語言與變更相關的實體中的執行。

此外，實體 （例如訂單項目） 中的集合應該是唯讀屬性 （稍後說明 AsReadOnly 方法）。 您應該能夠加以只能從更新彙總根類別方法或子實體方法內。

您可以看到在程式碼順序的彙總根，所有 setter 應該都是私用或至少唯讀外部使用，以便透過實體類別的方法都來執行對實體的資料或它的子實體的任何作業。 受控制和物件導向的方式，而不是實作交易式的指令碼以維護一致性。

下列程式碼片段會顯示程式碼新增 OrderItem 物件順序彙總的工作的正確方式。

```csharp
// RIGHT ACCORDING TO DDD--CODE AT THE APPLICATION LAYER OR COMMAND HANDLERS
// The code in command handlers or WebAPI controllers, related only to application stuff
// There is NO code here related to OrderItem object’s business logic
myOrder.AddOrderItem(productId, productName, pictureUrl, unitPrice, discount, units);

// The code related to OrderItem params validations or domain rules should
// be WITHIN the AddOrderItem method.

//...
```

在此片段中，大部分的驗證或 OrderItem 物件建立相關的邏輯會控制的順序彙總根 — AddOrderItem 方法中，特別是 「 驗證 」 和 「 邏輯相關的其他項目的彙總。 比方說，您可能會收到相同的產品項目為 AddOrderItem 多次呼叫的結果。 在該方法中，您無法檢查產品項目，並將相同的產品項目合併成單一 OrderItem 物件具有數個單位。 此外，如果不同折扣量，但產品識別碼都相同，您可能會套用更高的折扣。 此原則適用於任何其他網域邏輯 OrderItem 物件。

此外，新 OrderItem(params) 作業也會是控制並從順序彙總根 AddOrderItem 方法所執行。 因此，大部分的邏輯或驗證相關作業 （特別是任何會影響其他子實體之間的一致性） 會在彙總的根目錄中的單一位置。 這是最終的彙總根模式的目的。

當您使用 Entity Framework 1.1 時，DDD 實體可以進一步表示因為 Entity Framework Core 1.1 的新功能之一是它可讓[將對應到欄位](https://docs.microsoft.com/ef/core/modeling/backing-field)除了屬性之外。 保護子實體或值物件的集合時，這非常有用。 這項增強功能，您可以使用簡單的私用欄位，而非屬性，您可以在公用方法中實作的欄位集合的任何更新，並透過 AsReadOnly 方法提供唯讀存取。

因此在您想要更新之實體中之實體 （或建構函式） 以控制任何非變異值和資料的一致性方法只能透過 DDD，屬性會定義只能與 get 存取子。 屬性被支援私用欄位。 只有從在類別中存取私用成員。 不過，那里一個例外狀況： EF 核心，必須先設定這些欄位。

```csharp
// ENTITY FRAMEWORK CORE 1.1 OR LATER
// Entity is a custom base class with the ID
public class Order : Entity, IAggregateRoot
{
    // DDD Patterns comment
    // Using private fields, allowed since EF Core 1.1, is a much better
    // encapsulation aligned with DDD aggregates and domain entities (instead of
    // properties and property collections)
    private bool _someOrderInternalState;
    private DateTime _orderDate;
    public Address Address { get; private set; }
    public Buyer Buyer { get; private set; }
    private int _buyerId;
    public OrderStatus OrderStatus { get; private set; }
    private int _orderStatusId;

    // DDD patterns comment
    // Using a private collection field is better for DDD aggregate encapsulation.
    // OrderItem objects cannot be added from outside the aggregate root
    // directly to the collection, but only through the
    // OrderAggrergateRoot.AddOrderItem method, which includes behavior.
    private readonly List<OrderItem> _orderItems;
    public IEnumerable<OrderItem> OrderItems => _orderItems.AsReadOnly();
    // Using List<>.AsReadOnly()
    // This will create a read-only wrapper around the private list so it is
    // protected against external updates. It's much cheaper than .ToList(),
    // because it will not have to copy all items in a new collection.
    // (Just one heap alloc for the wrapper instance)
    // https://msdn.microsoft.com/en-us/library/e78dcd75(v=vs.110).aspx
    public PaymentMethod PaymentMethod { get; private set; }
    private int _paymentMethodId;

    protected Order() { }

    public Order(int buyerId, int paymentMethodId, Address address)
    {
        _orderItems = new List<OrderItem>();
        _buyerId = buyerId;
        _paymentMethodId = paymentMethodId;
        _orderStatusId = OrderStatus.InProcess.Id;
        _orderDate = DateTime.UtcNow;
        Address = address;
    }

    // DDD patterns comment
    // The Order aggregate root method AddOrderitem() should be the only way
    // to add items to the Order object, so that any behavior (discounts, etc.)
    // and validations are controlled by the aggregate root in order to
    // maintain consistency within the whole aggregate.
    public void AddOrderItem(int productId, string productName, decimal unitPrice,
        decimal discount, string pictureUrl, int units = 1)
    {
        // ...
        // Domain rules/logic here for adding OrderItem objects to the order
        // ...
        OrderItem item = new OrderItem(this.Id, productId, productName,
            pictureUrl, unitPrice, discount, units);
        OrderItems.Add(item);
    }

    // ...
    // Additional methods with domain rules/logic related to the Order aggregate
    // ...
}
```

### <a name="mapping-properties-with-only-get-accessors-to-the-fields-in-the-database-table"></a>對應屬性只在資料庫資料表中的欄位 get 存取子

對應至資料庫資料表資料行的內容不是網域的責任，而層基礎結構與持續性的一部分。 讓您了解如何建立模型實體與相關的 EF 1.1 中的新功能，我們曾經提到這裡只。 本主題中的其他詳細資料會由基礎結構與持續性 」 一節所述。

當您使用 EF 1.0 時，DbContext 內您要將屬性所定義的 getter 資料庫資料表中的實際欄位只能對應。 做法是使用 HasField PropertyBuilder 類別方法。

### <a name="mapping-fields-without-properties"></a>沒有內容的對應欄位

使用 EF 核心 1.1，做為資料行對應至欄位中的新功能，所以也可以不使用屬性。 相反地，您可以對應至欄位的資料表中的資料行。 常見的使用案例，這是私用欄位的一不需要從外部實體存取的內部狀態。

例如，在上述程式碼範例中， \_someOrderInternalState 欄位具有不相關的屬性 setter 或 getter。 也會計算訂單的商務邏輯中並使用順序的方法，從該欄位，但是它必須保存在資料庫中以及。 因此，在 EF 1.1 會有不相關的屬性將欄位對應到資料庫中的資料行的方法。 這也會說明在[基礎結構層](#the-infrastructure-layer)一節。

### <a name="additional-resources"></a>其他資源

-   **Vaughn Vernon：模型化 DDD 與 Entity Framework 的彙總。** 請注意，這是*不*Entity Framework Core。
    [*https://vaughnvernon.co/?p=879*](https://vaughnvernon.co/?p=879)

-   **Julie Lerman。網域導向設計撰寫程式碼： 資料已取得焦點的開發人員的秘訣**
    [*https://msdn.microsoft.com/en-us/magazine/dn342868.aspx*](https://msdn.microsoft.com/en-us/magazine/dn342868.aspx)

-   **Udi Dahan。如何建立完整封裝網域模型**
    [*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)


>[!div class="step-by-step"]
[上一個](微服務-網域-model.md) [下一步] (seedwork-domain-model-base-classes-interfaces.md)
