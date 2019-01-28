---
title: 使用 .NET Core 實作微服務領域模型
description: .NET 微服務：容器化 .NET 應用程式的架構 | 進入 DDD 導向領域模型的實作詳細資料。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: 884a558827e0e016e27315cee1ea9ed3e0d03dc4
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55065904"
---
# <a name="implement-a-microservice-domain-model-with-net-core"></a><span data-ttu-id="ed05f-103">使用 .NET Core 實作微服務領域模型</span><span class="sxs-lookup"><span data-stu-id="ed05f-103">Implement a microservice domain model with .NET Core</span></span> 

<span data-ttu-id="ed05f-104">上一節解釋了設計領域模型的基本設計準則及模式。</span><span class="sxs-lookup"><span data-stu-id="ed05f-104">In the previous section, the fundamental design principles and patterns for designing a domain model were explained.</span></span> <span data-ttu-id="ed05f-105">現在是探索使用 .NET Core (純 C\# 程式碼) 及 EF Core 實作領域模型之可能方式的時候了。</span><span class="sxs-lookup"><span data-stu-id="ed05f-105">Now it is time to explore possible ways to implement the domain model by using .NET Core (plain C\# code) and EF Core.</span></span> <span data-ttu-id="ed05f-106">請注意，您的領域模型會僅由您的程式碼組成。</span><span class="sxs-lookup"><span data-stu-id="ed05f-106">Note that your domain model will be composed simply of your code.</span></span> <span data-ttu-id="ed05f-107">它只會有 EF Core 模型需求，而非真正對 EF 的相依性。</span><span class="sxs-lookup"><span data-stu-id="ed05f-107">It will have just the EF Core model requirements, but not real dependencies on EF.</span></span> <span data-ttu-id="ed05f-108">您不應該在您的領域模型中對 EF Core 或任何其他的 ORM 具有硬式相依性或參考。</span><span class="sxs-lookup"><span data-stu-id="ed05f-108">You should not have hard dependencies or references to EF Core or any other ORM in your domain model.</span></span>

## <a name="domain-model-structure-in-a-custom-net-standard-library"></a><span data-ttu-id="ed05f-109">自訂 .NET Standard 程式庫中的領域模型結構</span><span class="sxs-lookup"><span data-stu-id="ed05f-109">Domain model structure in a custom .NET Standard Library</span></span>

<span data-ttu-id="ed05f-110">用於 eShopOnContainers 參考應用程式的資料夾組織展示了應用程式的 DDD 模型。</span><span class="sxs-lookup"><span data-stu-id="ed05f-110">The folder organization used for the eShopOnContainers reference application demonstrates the DDD model for the application.</span></span> <span data-ttu-id="ed05f-111">您可能會發現不同的資料夾組織可以更清楚的與您為應用程式選擇的設計進行通訊。</span><span class="sxs-lookup"><span data-stu-id="ed05f-111">You might find that a different folder organization more clearly communicates the design choices made for your application.</span></span> <span data-ttu-id="ed05f-112">如同您在圖 7-10 中所看到的，在訂購領域模型中有兩個彙總，即訂單彙總和購買者彙總。</span><span class="sxs-lookup"><span data-stu-id="ed05f-112">As you can see in Figure 7-10, in the ordering domain model there are two aggregates, the order aggregate and the buyer aggregate.</span></span> <span data-ttu-id="ed05f-113">每一個彙總都是一組領域實體和值物件，雖然您也可以使用單一領域實體 (彙總根或根實體) 來組成彙總。</span><span class="sxs-lookup"><span data-stu-id="ed05f-113">Each aggregate is a group of domain entities and value objects, although you could have an aggregate composed of a single domain entity (the aggregate root or root entity) as well.</span></span>

![<span data-ttu-id="ed05f-114">Ordering.Domain 專案的 [方案總管] 檢視，顯示包含 BuyerAggregate 及 OrderAggregate 資料夾的 AggregatesModel 資料夾，每一個包含它的實體類別、值物件檔案等等。</span><span class="sxs-lookup"><span data-stu-id="ed05f-114">The Solution Explorer view for the Ordering.Domain project, showing the AggregatesModel folder containing the BuyerAggregate and OrderAggregate folders, each one containing it's entity classes, value object files and so on.</span></span> ](./media/image11.png)

<span data-ttu-id="ed05f-115">**圖 7-10**。</span><span class="sxs-lookup"><span data-stu-id="ed05f-115">**Figure 7-10**.</span></span> <span data-ttu-id="ed05f-116">eShopOnContainers 訂購微服務的領域模型結構</span><span class="sxs-lookup"><span data-stu-id="ed05f-116">Domain model structure for the ordering microservice in eShopOnContainers</span></span>

<span data-ttu-id="ed05f-117">此外，領域模型層還包含了您領域模型之基礎結構需求的存放庫合約 (介面)。</span><span class="sxs-lookup"><span data-stu-id="ed05f-117">Additionally, the domain model layer includes the repository contracts (interfaces) that are the infrastructure requirements of your domain model.</span></span> <span data-ttu-id="ed05f-118">換句話說，這些介面表達了基礎結構層必須實作的存放庫和方法。</span><span class="sxs-lookup"><span data-stu-id="ed05f-118">In other words, these interfaces express what repositories and the methods the infrastructure layer must implement.</span></span> <span data-ttu-id="ed05f-119">將存放庫的實作放置於基礎結構層程式庫及領域模型層之外是非常重要的，這可讓領域模型層不會受到基礎結構技術 (例如 Entity Framework) API 或類別的「污染」。</span><span class="sxs-lookup"><span data-stu-id="ed05f-119">It is critical that the implementation of the repositories be placed outside of the domain model layer, in the infrastructure layer library, so the domain model layer is not “contaminated” by API or classes from infrastructure technologies, like Entity Framework.</span></span>

<span data-ttu-id="ed05f-120">您也可以查看包含了可讓您用來作為領域實體及值物件基底之自訂基底類別的 [SeedWork](https://martinfowler.com/bliki/Seedwork.html) 資料夾，以便您在每一個領域物件類別中不會有冗餘的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ed05f-120">You can also see a [SeedWork](https://martinfowler.com/bliki/Seedwork.html) folder that contains custom base classes that you can use as a base for your domain entities and value objects, so you do not have redundant code in each domain’s object class.</span></span>

## <a name="structure-aggregates-in-a-custom-net-standard-library"></a><span data-ttu-id="ed05f-121">自訂 .NET Standard 程式庫中的結構彙總</span><span class="sxs-lookup"><span data-stu-id="ed05f-121">Structure aggregates in a custom .NET Standard library</span></span>

<span data-ttu-id="ed05f-122">「彙總」指的是為了符合交易一致性而群組在一起的領域物件所構成的叢集。</span><span class="sxs-lookup"><span data-stu-id="ed05f-122">An aggregate refers to a cluster of domain objects grouped together to match transactional consistency.</span></span> <span data-ttu-id="ed05f-123">這些物件可以是實體的執行個體 (其中一個為彙總根或根實體) 加上任何額外的值物件。</span><span class="sxs-lookup"><span data-stu-id="ed05f-123">Those objects could be instances of entities (one of which is the aggregate root or root entity) plus any additional value objects.</span></span>

<span data-ttu-id="ed05f-124">「交易一致性」表示彙總保證會在商務動作結束時維持一致及最新狀態。</span><span class="sxs-lookup"><span data-stu-id="ed05f-124">Transactional consistency means that an aggregate is guaranteed to be consistent and up to date at the end of a business action.</span></span> <span data-ttu-id="ed05f-125">例如，來自 eShopOnContainers 訂購微服務領域模型的訂單彙總是由圖 7-11 中的內容所組成。</span><span class="sxs-lookup"><span data-stu-id="ed05f-125">For example, the order aggregate from the eShopOnContainers ordering microservice domain model is composed as shown in Figure 7-11.</span></span>

![OrderAggregate 資料夾的詳細檢視：Address.cs 是值物件、IOrderRepository 是存放庫介面、Order.cs 是彙總根、OrderItem.cs 是子系實體，且 OrderStatus.cs 是列舉類別。](./media/image12.png)

<span data-ttu-id="ed05f-127">**圖 7-11**。</span><span class="sxs-lookup"><span data-stu-id="ed05f-127">**Figure 7-11**.</span></span> <span data-ttu-id="ed05f-128">Visual Studio 方案中的訂單彙總</span><span class="sxs-lookup"><span data-stu-id="ed05f-128">The order aggregate in Visual Studio solution</span></span>

<span data-ttu-id="ed05f-129">若您在彙總資料夾中開啟了任何檔案，您可以看到其標示為自訂基底類別或介面 (例如實體或值物件) 的方式，如同在 [SeedWork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) 資料夾中所實作的。</span><span class="sxs-lookup"><span data-stu-id="ed05f-129">If you open any of the files in an aggregate folder, you can see how it is marked as either a custom base class or interface, like entity or value object, as implemented in the [SeedWork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) folder.</span></span>

## <a name="implement-domain-entities-as-poco-classes"></a><span data-ttu-id="ed05f-130">將領域實體實作為 POCO 類別</span><span class="sxs-lookup"><span data-stu-id="ed05f-130">Implement domain entities as POCO classes</span></span>

<span data-ttu-id="ed05f-131">您可以藉由建立實作您領域實體的 POCO 類別，來在 .NET 中實作領域模型。</span><span class="sxs-lookup"><span data-stu-id="ed05f-131">You implement a domain model in .NET by creating POCO classes that implement your domain entities.</span></span> <span data-ttu-id="ed05f-132">在下列範例中，Order 類別已定義為一個實體，同時也是彙總根。</span><span class="sxs-lookup"><span data-stu-id="ed05f-132">In the following example, the Order class is defined as an entity and also as an aggregate root.</span></span> <span data-ttu-id="ed05f-133">因為 Order 類別衍生自 Entity 基底類別，它可重複使用與實體相關的常見程式碼。</span><span class="sxs-lookup"><span data-stu-id="ed05f-133">Because the Order class derives from the Entity base class, it can reuse common code related to entities.</span></span> <span data-ttu-id="ed05f-134">請記住，這些基底類別和介面是您在領域模型物件中定義的，因此它是您的程式碼，而非來自像是 EF 之類的 ORM 的基礎結構程式碼。</span><span class="sxs-lookup"><span data-stu-id="ed05f-134">Bear in mind that these base classes and interfaces are defined by you in the domain model project, so it is your code, not infrastructure code from an ORM like EF.</span></span>

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

<span data-ttu-id="ed05f-135">請務必注意，這是實作為 POCO 類別的領域實體。</span><span class="sxs-lookup"><span data-stu-id="ed05f-135">It is important to note that this is a domain entity implemented as a POCO class.</span></span> <span data-ttu-id="ed05f-136">它對 Entity Framework Core 或任何其他基礎結構架構都沒有任何直接相依性。</span><span class="sxs-lookup"><span data-stu-id="ed05f-136">It does not have any direct dependency on Entity Framework Core or any other infrastructure framework.</span></span> <span data-ttu-id="ed05f-137">這項實作是以 DDD 方式進行的 (也應如此)，單純只是實作領域模型的 C\# 程式碼。</span><span class="sxs-lookup"><span data-stu-id="ed05f-137">This implementation is as it should be in DDD, just C\# code implementing a domain model.</span></span>

<span data-ttu-id="ed05f-138">此外，類別會使用名為 IAggregateRoot 的介面裝飾。</span><span class="sxs-lookup"><span data-stu-id="ed05f-138">In addition, the class is decorated with an interface named IAggregateRoot.</span></span> <span data-ttu-id="ed05f-139">該介面是一個空介面，有時候稱之為*標記介面 (marker interface)*，單純用於指出此實體類別同時也是一個彙總根。</span><span class="sxs-lookup"><span data-stu-id="ed05f-139">That interface is an empty interface, sometimes called a *marker interface*, that is used just to indicate that this entity class is also an aggregate root.</span></span>

<span data-ttu-id="ed05f-140">標記介面有時候會被視為「反模式 (anti-pattern)」。然而，它同時也是一種標記類別的明瞭方式，尤其是在該介面可能會進一步發展的情況下。</span><span class="sxs-lookup"><span data-stu-id="ed05f-140">A marker interface is sometimes considered as an anti-pattern; however, it is also a clean way to mark a class, especially when that interface might be evolving.</span></span> <span data-ttu-id="ed05f-141">屬性也可以是用於標記的另外一個選擇，但通常看見 IAggregate 介面旁邊的基底類別 (Entity)，會比將 Aggregate 屬性標記放在類別上方要來得更快。</span><span class="sxs-lookup"><span data-stu-id="ed05f-141">An attribute could be the other choice for the marker, but it is quicker to see the base class (Entity) next to the IAggregate interface instead of putting an Aggregate attribute marker above the class.</span></span> <span data-ttu-id="ed05f-142">這在任何案例中都只是一種喜好設定。</span><span class="sxs-lookup"><span data-stu-id="ed05f-142">It is a matter of preferences, in any case.</span></span>

<span data-ttu-id="ed05f-143">擁有彙總根表示與一致性和彙總實體商務規則有關的大部分程式碼都應在 Order 彙總根類別中實作為方法 (例如：將 OrderItem 物件新增至彙總的 AddOrderItem)。</span><span class="sxs-lookup"><span data-stu-id="ed05f-143">Having an aggregate root means that most of the code related to consistency and business rules of the aggregate’s entities should be implemented as methods in the Order aggregate root class (for example, AddOrderItem when adding an OrderItem object to the aggregate).</span></span> <span data-ttu-id="ed05f-144">您不應獨立或直接建立或更新 OrderItems 物件。AggregateRoot 類別必須控制並使任何對其子實體所做出的更新作業保持一致。</span><span class="sxs-lookup"><span data-stu-id="ed05f-144">You should not create or update OrderItems objects independently or directly; the AggregateRoot class must keep control and consistency of any update operation against its child entities.</span></span>

## <a name="encapsulate-data-in-the-domain-entities"></a><span data-ttu-id="ed05f-145">封裝領域實體內的資料</span><span class="sxs-lookup"><span data-stu-id="ed05f-145">Encapsulate data in the Domain Entities</span></span>

<span data-ttu-id="ed05f-146">實體模型中的常見問題之一便是他們會將集合導覽屬性作為可公開存取的清單類型公開。</span><span class="sxs-lookup"><span data-stu-id="ed05f-146">A common problem in entity models is that they expose collection navigation properties as publicly accessible list types.</span></span> <span data-ttu-id="ed05f-147">這可讓任何共同作業的開發人員操縱這些集合類型的內容，使其略過與集合相關的重要商務規則，並可能讓物件處於無效狀態。</span><span class="sxs-lookup"><span data-stu-id="ed05f-147">This allows any collaborator developer to manipulate the contents of these collection types, which may bypass important business rules related to the collection, possibly leaving the object in an invalid state.</span></span> <span data-ttu-id="ed05f-148">其中一個解決方案便是公開相關集合的唯讀存取，並明確提供定義用戶端可操縱他們之方式的方法。</span><span class="sxs-lookup"><span data-stu-id="ed05f-148">The solution to this is to expose read-only access to related collections and explicitly provide methods that define ways in which clients can manipulate them.</span></span>

<span data-ttu-id="ed05f-149">在先前的程式碼中，請注意許多屬性都是唯讀或私用，且只能透過類別方法進行更新，以使得任何更新都必須考量到類別方法中指定的商務領域變異及邏輯。</span><span class="sxs-lookup"><span data-stu-id="ed05f-149">In the previous code, note that many attributes are read-only or private and are only updatable by the class methods, so any update considers business domain invariants and logic specified within the class methods.</span></span>

<span data-ttu-id="ed05f-150">例如，根據 DDD 模式，**您「不」應從任何命令處理常式方法或應用程式層類別進行下列動作** (實際上，您應該無法這麼做)：</span><span class="sxs-lookup"><span data-stu-id="ed05f-150">For example, following DDD patterns, **you should *not* do the following** from any command handler method or application layer class (actually, it should be impossible for you to do so):</span></span>

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

<span data-ttu-id="ed05f-151">在此案例下，Add 方法純粹只是新增資料的作業，可直接存取 OrderItems 集合。</span><span class="sxs-lookup"><span data-stu-id="ed05f-151">In this case, the Add method is purely an operation to add data, with direct access to the OrderItems collection.</span></span> <span data-ttu-id="ed05f-152">因此，與該帶有子實體之作業相關的大部分領域邏輯、規則或驗證都會擴張至應用程式層 (命令處理常式及 Web API 控制器)。</span><span class="sxs-lookup"><span data-stu-id="ed05f-152">Therefore, most of the domain logic, rules, or validations related to that operation with the child entities will be spread across the application layer (command handlers and Web API controllers).</span></span>

<span data-ttu-id="ed05f-153">若您繞過了彙總根，彙總根便無法保證其不區分、有效性，或是一致性。</span><span class="sxs-lookup"><span data-stu-id="ed05f-153">If you go around the aggregate root, the aggregate root cannot guarantee its invariants, its validity, or its consistency.</span></span> <span data-ttu-id="ed05f-154">最後您便可能會擁有雜亂的程式碼或交易指令碼。</span><span class="sxs-lookup"><span data-stu-id="ed05f-154">Eventually you will have spaghetti code or transactional script code.</span></span>

<span data-ttu-id="ed05f-155">若要遵循 DDD 模式，實體便不可在任何實體屬性中具有公用的 setter。</span><span class="sxs-lookup"><span data-stu-id="ed05f-155">To follow DDD patterns, entities must not have public setters in any entity property.</span></span> <span data-ttu-id="ed05f-156">實體的變更必須使用關於其在實體中執行之變更的明確通用語言，透過明確的方法來驅動。</span><span class="sxs-lookup"><span data-stu-id="ed05f-156">Changes in an entity should be driven by explicit methods with explicit ubiquitous language about the change they are performing in the entity.</span></span>

<span data-ttu-id="ed05f-157">此外，實體中的集合 (例如訂購項目) 應為唯讀屬性 (即稍後解釋的 AsReadOnly 方法)。</span><span class="sxs-lookup"><span data-stu-id="ed05f-157">Furthermore, collections within the entity (like the order items) should be read-only properties (the AsReadOnly method explained later).</span></span> <span data-ttu-id="ed05f-158">您只能在彙總根類別方法或子實體方法中對其進行更新。</span><span class="sxs-lookup"><span data-stu-id="ed05f-158">You should be able to update it only from within the aggregate root class methods or the child entity methods.</span></span>

<span data-ttu-id="ed05f-159">如同您可在 Order 彙總根程式碼中所看到的，所有的 setter 都必須是私用的，或至少必須是外部唯讀的，以使得所有對實體資料或其子實體進行的作業都必須透過實體類別中的方法執行。</span><span class="sxs-lookup"><span data-stu-id="ed05f-159">As you can see in the code for the Order aggregate root, all setters should be private or at least read-only externally, so that any operation against the entity’s data or its child entities has to be performed through methods in the entity class.</span></span> <span data-ttu-id="ed05f-160">這可透過受控及物件導向的方式維持一致性，而非實作交易指令碼。</span><span class="sxs-lookup"><span data-stu-id="ed05f-160">This maintains consistency in a controlled and object-oriented way instead of implementing transactional script code.</span></span>

<span data-ttu-id="ed05f-161">下列程式碼片段顯示了撰寫將 OrderItem 物件新增至 Order 彙總工作之程式碼的適當方式。</span><span class="sxs-lookup"><span data-stu-id="ed05f-161">The following code snippet shows the proper way to code the task of adding an OrderItem object to the Order aggregate.</span></span>

```csharp
// RIGHT ACCORDING TO DDD--CODE AT THE APPLICATION LAYER OR COMMAND HANDLERS
// The code in command handlers or WebAPI controllers, related only to application stuff
// There is NO code here related to OrderItem object’s business logic
myOrder.AddOrderItem(productId, productName, pictureUrl, unitPrice, discount, units);

// The code related to OrderItem params validations or domain rules should
// be WITHIN the AddOrderItem method.

//...
```

<span data-ttu-id="ed05f-162">在此片段中，與建立 OrderItem 物件相關的大部分驗證和邏輯都會受控於 Order 彙總根—於 AddOrderItem 方法中—尤其是與彙總內其他元素相關的驗證及邏輯。</span><span class="sxs-lookup"><span data-stu-id="ed05f-162">In this snippet, most of the validations or logic related to the creation of an OrderItem object will be under the control of the Order aggregate root—in the AddOrderItem method—especially validations and logic related to other elements in the aggregate.</span></span> <span data-ttu-id="ed05f-163">例如，多次呼叫 AddOrderItem 的結果可能是您會取得相同的產品項目。</span><span class="sxs-lookup"><span data-stu-id="ed05f-163">For instance, you might get the same product item as the result of multiple calls to AddOrderItem.</span></span> <span data-ttu-id="ed05f-164">在該方法中，您可以檢查產品項目並將相同的產品項目合併為單一、帶有幾個單位的 OrderItem 物件。</span><span class="sxs-lookup"><span data-stu-id="ed05f-164">In that method, you could examine the product items and consolidate the same product items into a single OrderItem object with several units.</span></span> <span data-ttu-id="ed05f-165">此外，若有不同的折扣金額，但產品識別碼都是相同的，您也可以套用更高的折扣金額。</span><span class="sxs-lookup"><span data-stu-id="ed05f-165">Additionally, if there are different discount amounts but the product ID is the same, you would likely apply the higher discount.</span></span> <span data-ttu-id="ed05f-166">此準則適用於任何其他 OrderItem 物件的領域邏輯。</span><span class="sxs-lookup"><span data-stu-id="ed05f-166">This principle applies to any other domain logic for the OrderItem object.</span></span>

<span data-ttu-id="ed05f-167">此外，新的 OrderItem(params) 作業也會由 Order 彙總根的 AddOrderItem 方法控制及執行。</span><span class="sxs-lookup"><span data-stu-id="ed05f-167">In addition, the new OrderItem(params) operation will also be controlled and performed by the AddOrderItem method from the Order aggregate root.</span></span> <span data-ttu-id="ed05f-168">因此，與該作業相關的大多數邏輯或驗證 (尤其是任何會影響到與其他子實體間一致性的內容) 都會位於彙總根中的單一空間內。</span><span class="sxs-lookup"><span data-stu-id="ed05f-168">Therefore, most of the logic or validations related to that operation (especially anything that impacts the consistency between other child entities) will be in a single place within the aggregate root.</span></span> <span data-ttu-id="ed05f-169">這便是彙總根模式的最終目的。</span><span class="sxs-lookup"><span data-stu-id="ed05f-169">That is the ultimate purpose of the aggregate root pattern.</span></span>

<span data-ttu-id="ed05f-170">當您使用 Entity Framework Core 1.1 或更新版本時，DDD 實體可以更好的方式進行表達，因為除了屬性之外，它還允許了[對應至欄位 (支援欄位)](https://docs.microsoft.com/ef/core/modeling/backing-field)。</span><span class="sxs-lookup"><span data-stu-id="ed05f-170">When you use Entity Framework Core 1.1 or later, a DDD entity can be better expressed because it allows [mapping to fields](https://docs.microsoft.com/ef/core/modeling/backing-field) in addition to properties.</span></span> <span data-ttu-id="ed05f-171">這在保護子實體或值物件集合時將會很有用。</span><span class="sxs-lookup"><span data-stu-id="ed05f-171">This is useful when protecting collections of child entities or value objects.</span></span> <span data-ttu-id="ed05f-172">透過這項增強功能，您可以使用簡單的私用欄位 (而非屬性)，並且也能在公用方法中實作任何對欄位集合進行的更新，並透過 AsReadOnly 方法提供唯讀存取。</span><span class="sxs-lookup"><span data-stu-id="ed05f-172">With this enhancement, you can use simple private fields instead of properties and you can implement any update to the field collection in public methods and provide read-only access through the AsReadOnly method.</span></span>

<span data-ttu-id="ed05f-173">在 DDD 中，您會希望只透過實體 (或建構函式) 中的方法來更新實體，以控制任何不區分及資料的一致性，使屬性可以只定義 get 存取子。</span><span class="sxs-lookup"><span data-stu-id="ed05f-173">In DDD you want to update the entity only through methods in the entity (or the constructor) in order to control any invariant and the consistency of the data, so properties are defined only with a get accessor.</span></span> <span data-ttu-id="ed05f-174">屬性會受私用欄位支援。</span><span class="sxs-lookup"><span data-stu-id="ed05f-174">The properties are backed by private fields.</span></span> <span data-ttu-id="ed05f-175">私用成員只能在類別中進行存取。</span><span class="sxs-lookup"><span data-stu-id="ed05f-175">Private members can only be accessed from within the class.</span></span> <span data-ttu-id="ed05f-176">不過，有一個例外：EF Core 也需要先設定這些欄位 (讓它可以傳回具有適當值的物件)。</span><span class="sxs-lookup"><span data-stu-id="ed05f-176">However, there one exception: EF Core needs to set these fields as well (so it can return the object with the proper values).</span></span>

### <a name="map-properties-with-only-get-accessors-to-the-fields-in-the-database-table"></a><span data-ttu-id="ed05f-177">僅使用 Get 存取子來將屬性對應至資料庫資料表中的欄位</span><span class="sxs-lookup"><span data-stu-id="ed05f-177">Map properties with only get accessors to the fields in the database table</span></span>

<span data-ttu-id="ed05f-178">將屬性對應至資料庫資料表資料行並非領域的責任，而是基礎結構及永續性層的一部份。</span><span class="sxs-lookup"><span data-stu-id="ed05f-178">Mapping properties to database table columns is not a domain responsibility but part of the infrastructure and persistence layer.</span></span> <span data-ttu-id="ed05f-179">我們在此提到這個，以讓您了解到 EF Core 1.1 及更新版本中您可以為實體建立模型之方式的新功能。</span><span class="sxs-lookup"><span data-stu-id="ed05f-179">We mention this here just so you are aware of the new capabilities in EF Core 1.1 or later related to how you can model entities.</span></span> <span data-ttu-id="ed05f-180">本主題的其他詳細資料會在基礎結構及永續性一節解釋。</span><span class="sxs-lookup"><span data-stu-id="ed05f-180">Additional details on this topic are explained in the infrastructure and persistence section.</span></span>

<span data-ttu-id="ed05f-181">當您使用 EF Core 1.0 或更新版本時，在 DbContext 中，您需要將只使用 getter 定義的屬性對應至資料庫資料表中實際欄位。</span><span class="sxs-lookup"><span data-stu-id="ed05f-181">When you use EF Core 1.0 or later, within the DbContext you need to map the properties that are defined only with getters to the actual fields in the database table.</span></span> <span data-ttu-id="ed05f-182">這可透過 PropertyBuilder 類別的 HasField 方法來完成。</span><span class="sxs-lookup"><span data-stu-id="ed05f-182">This is done with the HasField method of the PropertyBuilder class.</span></span>

### <a name="map-fields-without-properties"></a><span data-ttu-id="ed05f-183">不使用屬性來對應欄位</span><span class="sxs-lookup"><span data-stu-id="ed05f-183">Map fields without properties</span></span>

<span data-ttu-id="ed05f-184">藉由使用 EF Core 1.1 或更新版本中的功能來將資料行對應至欄位，您也可以不使用屬性。</span><span class="sxs-lookup"><span data-stu-id="ed05f-184">With the feature in EF Core 1.1 or later to map columns to fields, it is also possible to not use properties.</span></span> <span data-ttu-id="ed05f-185">相反的，您可以直接將資料表中的資料行對應至欄位。</span><span class="sxs-lookup"><span data-stu-id="ed05f-185">Instead, you can just map columns from a table to fields.</span></span> <span data-ttu-id="ed05f-186">常見的使用案例便是不需要從實體外部存取之內部狀態的私用欄位。</span><span class="sxs-lookup"><span data-stu-id="ed05f-186">A common use case for this is private fields for an internal state that does not need to be accessed from outside the entity.</span></span>

<span data-ttu-id="ed05f-187">例如，在上述的 OrderAggregate 程式碼範例中，有幾個私用欄位 (例如 `_paymentMethodId` 欄位) 針對 setter 或 getter 都不具有任何相關屬性。</span><span class="sxs-lookup"><span data-stu-id="ed05f-187">For example, in the preceding OrderAggregate code example, there are several private fields, like the  `_paymentMethodId` field, that have no related property for either a setter or getter.</span></span> <span data-ttu-id="ed05f-188">該欄位也可以透過在訂單的商務邏輯內計算取得，並由訂單的方法使用，但它也必須永續保存在資料庫中。</span><span class="sxs-lookup"><span data-stu-id="ed05f-188">That field could also be calculated within the order’s business logic and used from the order’s methods, but it needs to be persisted in the database as well.</span></span> <span data-ttu-id="ed05f-189">因此，在 EF Core (v1.1 之後) 中，有一種方式可不使用相關屬性來將欄位對應至資料庫中的資料行。</span><span class="sxs-lookup"><span data-stu-id="ed05f-189">So in EF Core (since v1.1) there is a way to map a field without a related property to a column in the database.</span></span> <span data-ttu-id="ed05f-190">這也會在本指南中的[基礎結構層](ddd-oriented-microservice.md#the-infrastructure-layer)一節解釋。</span><span class="sxs-lookup"><span data-stu-id="ed05f-190">This is also explained in the [Infrastructure layer](ddd-oriented-microservice.md#the-infrastructure-layer) section of this guide.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="ed05f-191">其他資源</span><span class="sxs-lookup"><span data-stu-id="ed05f-191">Additional resources</span></span>

- <span data-ttu-id="ed05f-192">**Vaughn Vernon：使用 DDD 及 Entity Framework 為彙總建立模型**</span><span class="sxs-lookup"><span data-stu-id="ed05f-192">**Vaughn Vernon. Modeling Aggregates with DDD and Entity Framework.**</span></span> <span data-ttu-id="ed05f-193">請注意，這*並非* Entity Framework Core。</span><span class="sxs-lookup"><span data-stu-id="ed05f-193">Note that this is *not* Entity Framework Core.</span></span> \
  <https://kalele.io/blog-posts/modeling-aggregates-with-ddd-and-entity-framework/>

- <span data-ttu-id="ed05f-194">**Julie Lerman。針對領域驅動設計撰寫程式碼：進行資料型開發的祕訣** \\</span><span class="sxs-lookup"><span data-stu-id="ed05f-194">**Julie Lerman. Coding for Domain-Driven Design: Tips for Data-Focused Devs** \\</span></span>
  [*https://msdn.microsoft.com/magazine/dn342868.aspx*](https://msdn.microsoft.com/magazine/dn342868.aspx)

- <span data-ttu-id="ed05f-195">**Udi Dahan.如何建立完整封裝式領域模型** \\</span><span class="sxs-lookup"><span data-stu-id="ed05f-195">**Udi Dahan. How to create fully encapsulated Domain Models** \\</span></span>
  [*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)

>[!div class="step-by-step"]
><span data-ttu-id="ed05f-196">[上一頁](microservice-domain-model.md)
>[下一頁](seedwork-domain-model-base-classes-interfaces.md)</span><span class="sxs-lookup"><span data-stu-id="ed05f-196">[Previous](microservice-domain-model.md)
[Next](seedwork-domain-model-base-classes-interfaces.md)</span></span>
