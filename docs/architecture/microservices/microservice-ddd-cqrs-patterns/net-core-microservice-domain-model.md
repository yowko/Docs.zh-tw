---
title: 使用 .NET Core 實作微服務領域模型
description: .NET 微服務：容器化 .NET 應用程式的架構 | 進入 DDD 導向領域模型的實作詳細資料。
ms.date: 10/08/2018
ms.openlocfilehash: b2ad62c2a16dd3993b9624ec14f0070e934ac2de
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68676585"
---
# <a name="implement-a-microservice-domain-model-with-net-core"></a>使用 .NET Core 實作微服務領域模型

上一節解釋了設計領域模型的基本設計準則及模式。 現在是探索使用 .NET Core (純 C\# 程式碼) 及 EF Core 實作領域模型之可能方式的時候了。 請注意，您的領域模型會僅由您的程式碼組成。 它只會有 EF Core 模型需求，而非真正對 EF 的相依性。 您不應該在您的領域模型中對 EF Core 或任何其他的 ORM 具有硬式相依性或參考。

## <a name="domain-model-structure-in-a-custom-net-standard-library"></a>自訂 .NET Standard 程式庫中的領域模型結構

用於 eShopOnContainers 參考應用程式的資料夾組織展示了應用程式的 DDD 模型。 您可能會發現不同的資料夾組織可以更清楚的與您為應用程式選擇的設計進行通訊。 如同您在圖 7-10 中所看到的，在訂購領域模型中有兩個彙總，即訂單彙總和購買者彙總。 每一個彙總都是一組領域實體和值物件，雖然您也可以使用單一領域實體 (彙總根或根實體) 來組成彙總。

![Ordering.Domain 專案的 [方案總管] 檢視，顯示包含 BuyerAggregate 及 OrderAggregate 資料夾的 AggregatesModel 資料夾，每一個包含它的實體類別、值物件檔案等等。 ](./media/image11.png)

**圖 7-10**。 eShopOnContainers 訂購微服務的領域模型結構

此外，領域模型層還包含了您領域模型之基礎結構需求的存放庫合約 (介面)。 換句話說，這些介面表達了基礎結構層必須實作的存放庫和方法。 將存放庫的實作放置於基礎結構層程式庫及領域模型層之外是非常重要的，這可讓領域模型層不會受到基礎結構技術 (例如 Entity Framework) API 或類別的「污染」。

您也可以查看包含了可讓您用來作為領域實體及值物件基底之自訂基底類別的 [SeedWork](https://martinfowler.com/bliki/Seedwork.html) 資料夾，以便您在每一個領域物件類別中不會有冗餘的程式碼。

## <a name="structure-aggregates-in-a-custom-net-standard-library"></a>自訂 .NET Standard 程式庫中的結構彙總

「彙總」指的是為了符合交易一致性而群組在一起的領域物件所構成的叢集。 這些物件可以是實體的執行個體 (其中一個為彙總根或根實體) 加上任何額外的值物件。

「交易一致性」表示彙總保證會在商務動作結束時維持一致及最新狀態。 例如，來自 eShopOnContainers 訂購微服務領域模型的訂單彙總是由圖 7-11 中的內容所組成。

![OrderAggregate 資料夾的詳細檢視：Address.cs 是值物件、IOrderRepository 是存放庫介面、Order.cs 是彙總根、OrderItem.cs 是子系實體，且 OrderStatus.cs 是列舉類別。](./media/image12.png)

**圖 7-11**。 Visual Studio 方案中的訂單彙總

若您在彙總資料夾中開啟了任何檔案，您可以看到其標示為自訂基底類別或介面 (例如實體或值物件) 的方式，如同在 [SeedWork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) 資料夾中所實作的。

## <a name="implement-domain-entities-as-poco-classes"></a>將領域實體實作為 POCO 類別

您可以藉由建立實作您領域實體的 POCO 類別，來在 .NET 中實作領域模型。 在下列範例中，Order 類別已定義為一個實體，同時也是彙總根。 因為 Order 類別衍生自 Entity 基底類別，它可重複使用與實體相關的常見程式碼。 請記住，這些基底類別和介面是您在領域模型物件中定義的，因此它是您的程式碼，而非來自像是 EF 之類的 ORM 的基礎結構程式碼。

```csharp
// COMPATIBLE WITH ENTITY FRAMEWORK CORE 2.0
// Entity is a custom base class with the ID
public class Order : Entity, IAggregateRoot
{
    private DateTime _orderDate;
    public Address Address { get; private set; }
    private int? _buyerId;

    public OrderStatus OrderStatus { get; private set; }
    private int _orderStatusId;

    private string _description;
    private int? _paymentMethodId;

    private readonly List<OrderItem> _orderItems;
    public IReadOnlyCollection<OrderItem> OrderItems => _orderItems;

    public Order(string userId, Address address, int cardTypeId, string cardNumber, string cardSecurityNumber,
            string cardHolderName, DateTime cardExpiration, int? buyerId = null, int? paymentMethodId = null)
    {
        _orderItems = new List<OrderItem>();
        _buyerId = buyerId;
        _paymentMethodId = paymentMethodId;
        _orderStatusId = OrderStatus.Submitted.Id;
        _orderDate = DateTime.UtcNow;
        Address = address;

        // ...Additional code ...
    }

    public void AddOrderItem(int productId, string productName,
                            decimal unitPrice, decimal discount,
                            string pictureUrl, int units = 1)
    {
        //...
        // Domain rules/logic for adding the OrderItem to the order
        // ...

        var orderItem = new OrderItem(productId, productName, unitPrice, discount, pictureUrl, units);

        _orderItems.Add(orderItem);

    }
    // ...
    // Additional methods with domain rules/logic related to the Order aggregate
    // ...
}
```

請務必注意，這是實作為 POCO 類別的領域實體。 它對 Entity Framework Core 或任何其他基礎結構架構都沒有任何直接相依性。 這項實作是以 DDD 方式進行的 (也應如此)，單純只是實作領域模型的 C\# 程式碼。

此外，類別會使用名為 IAggregateRoot 的介面裝飾。 該介面是一個空介面，有時候稱之為*標記介面 (marker interface)* ，單純用於指出此實體類別同時也是一個彙總根。

標記介面有時候會被視為「反模式 (anti-pattern)」。然而，它同時也是一種標記類別的明瞭方式，尤其是在該介面可能會進一步發展的情況下。 屬性也可以是用於標記的另外一個選擇，但通常看見 IAggregate 介面旁邊的基底類別 (Entity)，會比將 Aggregate 屬性標記放在類別上方要來得更快。 這在任何案例中都只是一種喜好設定。

擁有彙總根表示與一致性和彙總實體商務規則有關的大部分程式碼都應在 Order 彙總根類別中實作為方法 (例如：將 OrderItem 物件新增至彙總的 AddOrderItem)。 您不應獨立或直接建立或更新 OrderItems 物件。AggregateRoot 類別必須控制並使任何對其子實體所做出的更新作業保持一致。

## <a name="encapsulate-data-in-the-domain-entities"></a>封裝領域實體內的資料

實體模型中的常見問題之一便是他們會將集合導覽屬性作為可公開存取的清單類型公開。 這可讓任何共同作業的開發人員操縱這些集合類型的內容，使其略過與集合相關的重要商務規則，並可能讓物件處於無效狀態。 其中一個解決方案便是公開相關集合的唯讀存取，並明確提供定義用戶端可操縱他們之方式的方法。

在先前的程式碼中，請注意許多屬性都是唯讀或私用，且只能透過類別方法進行更新，以使得任何更新都必須考量到類別方法中指定的商務領域變異及邏輯。

例如，根據 DDD 模式，**您「不」  應從任何命令處理常式方法或應用程式層類別進行下列動作** (實際上，您應該無法這麼做)：

```csharp
// WRONG ACCORDING TO DDD PATTERNS – CODE AT THE APPLICATION LAYER OR
// COMMAND HANDLERS
// Code in command handler methods or Web API controllers
//... (WRONG) Some code with business logic out of the domain classes ...
OrderItem myNewOrderItem = new OrderItem(orderId, productId, productName,
    pictureUrl, unitPrice, discount, units);

//... (WRONG) Accessing the OrderItems collection directly from the application layer // or command handlers
myOrder.OrderItems.Add(myNewOrderItem);
//...
```

在此案例下，Add 方法純粹只是新增資料的作業，可直接存取 OrderItems 集合。 因此，與該帶有子實體之作業相關的大部分領域邏輯、規則或驗證都會擴張至應用程式層 (命令處理常式及 Web API 控制器)。

若您繞過了彙總根，彙總根便無法保證其不區分、有效性，或是一致性。 最後您便可能會擁有雜亂的程式碼或交易指令碼。

若要遵循 DDD 模式，實體便不可在任何實體屬性中具有公用的 setter。 實體的變更必須使用關於其在實體中執行之變更的明確通用語言，透過明確的方法來驅動。

此外，實體中的集合 (例如訂購項目) 應為唯讀屬性 (即稍後解釋的 AsReadOnly 方法)。 您只能在彙總根類別方法或子實體方法中對其進行更新。

如同您可在 Order 彙總根程式碼中所看到的，所有的 setter 都必須是私用的，或至少必須是外部唯讀的，以使得所有對實體資料或其子實體進行的作業都必須透過實體類別中的方法執行。 這可透過受控及物件導向的方式維持一致性，而非實作交易指令碼。

下列程式碼片段顯示了撰寫將 OrderItem 物件新增至 Order 彙總工作之程式碼的適當方式。

```csharp
// RIGHT ACCORDING TO DDD--CODE AT THE APPLICATION LAYER OR COMMAND HANDLERS
// The code in command handlers or WebAPI controllers, related only to application stuff
// There is NO code here related to OrderItem object’s business logic
myOrder.AddOrderItem(productId, productName, pictureUrl, unitPrice, discount, units);

// The code related to OrderItem params validations or domain rules should
// be WITHIN the AddOrderItem method.

//...
```

在此片段中，與建立 OrderItem 物件相關的大部分驗證和邏輯都會受控於 Order 彙總根—於 AddOrderItem 方法中—尤其是與彙總內其他元素相關的驗證及邏輯。 例如，多次呼叫 AddOrderItem 的結果可能是您會取得相同的產品項目。 在該方法中，您可以檢查產品項目並將相同的產品項目合併為單一、帶有幾個單位的 OrderItem 物件。 此外，若有不同的折扣金額，但產品識別碼都是相同的，您也可以套用更高的折扣金額。 此準則適用於任何其他 OrderItem 物件的領域邏輯。

此外，新的 OrderItem(params) 作業也會由 Order 彙總根的 AddOrderItem 方法控制及執行。 因此，與該作業相關的大多數邏輯或驗證 (尤其是任何會影響到與其他子實體間一致性的內容) 都會位於彙總根中的單一空間內。 這便是彙總根模式的最終目的。

當您使用 Entity Framework Core 1.1 或更新版本時，DDD 實體可以更好的方式進行表達，因為除了屬性之外，它還允許了[對應至欄位 (支援欄位)](https://docs.microsoft.com/ef/core/modeling/backing-field)。 這在保護子實體或值物件集合時將會很有用。 透過這項增強功能，您可以使用簡單的私用欄位 (而非屬性)，並且也能在公用方法中實作任何對欄位集合進行的更新，並透過 AsReadOnly 方法提供唯讀存取。

在 DDD 中，您會希望只透過實體 (或建構函式) 中的方法來更新實體，以控制任何不區分及資料的一致性，使屬性可以只定義 get 存取子。 屬性會受私用欄位支援。 私用成員只能在類別中進行存取。 不過，有一個例外：EF Core 也需要先設定這些欄位 (讓它可以傳回具有適當值的物件)。

### <a name="map-properties-with-only-get-accessors-to-the-fields-in-the-database-table"></a>僅使用 Get 存取子來將屬性對應至資料庫資料表中的欄位

將屬性對應至資料庫資料表資料行並非領域的責任，而是基礎結構及永續性層的一部份。 我們在此提到這個，以讓您了解到 EF Core 1.1 及更新版本中您可以為實體建立模型之方式的新功能。 本主題的其他詳細資料會在基礎結構及永續性一節解釋。

當您使用 EF Core 1.0 或更新版本時，在 DbContext 中，您需要將只使用 getter 定義的屬性對應至資料庫資料表中實際欄位。 這可透過 PropertyBuilder 類別的 HasField 方法來完成。

### <a name="map-fields-without-properties"></a>不使用屬性來對應欄位

藉由使用 EF Core 1.1 或更新版本中的功能來將資料行對應至欄位，您也可以不使用屬性。 相反的，您可以直接將資料表中的資料行對應至欄位。 常見的使用案例便是不需要從實體外部存取之內部狀態的私用欄位。

例如，在上述的 OrderAggregate 程式碼範例中，有幾個私用欄位 (例如 `_paymentMethodId` 欄位) 針對 setter 或 getter 都不具有任何相關屬性。 該欄位也可以透過在訂單的商務邏輯內計算取得，並由訂單的方法使用，但它也必須永續保存在資料庫中。 因此，在 EF Core (v1.1 之後) 中，有一種方式可不使用相關屬性來將欄位對應至資料庫中的資料行。 這也會在本指南中的[基礎結構層](ddd-oriented-microservice.md#the-infrastructure-layer)一節解釋。

### <a name="additional-resources"></a>其他資源

- **Vaughn Vernon：使用 DDD 及 Entity Framework 為彙總建立模型** 請注意，這*並非* Entity Framework Core。 \
  <https://kalele.io/blog-posts/modeling-aggregates-with-ddd-and-entity-framework/>

- **Julie Lerman。資料點 - 針對領域驅動設計撰寫程式碼：進行資料型開發的祕訣** \
  <https://msdn.microsoft.com/magazine/dn342868.aspx>

- **Udi Dahan.如何建立完整封裝式領域模型** \
  <http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/>

> [!div class="step-by-step"]
> [上一頁](microservice-domain-model.md)
> [下一頁](seedwork-domain-model-base-classes-interfaces.md)
