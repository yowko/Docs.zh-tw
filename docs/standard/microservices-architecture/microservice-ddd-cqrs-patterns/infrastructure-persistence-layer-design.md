---
title: "設計基礎結構的持續性層級"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |設計基礎結構的持續性層級"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: ce0f1d608eed909a7707f3c580afc5253f3eef06
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="designing-the-infrastructure-persistence-layer"></a><span data-ttu-id="86706-104">設計基礎結構的持續性層級</span><span class="sxs-lookup"><span data-stu-id="86706-104">Designing the infrastructure persistence layer</span></span>

<span data-ttu-id="86706-105">資料持續性元件提供裝載界限內的微服務 （也就是微服務 」 資料庫） 資料的存取權。</span><span class="sxs-lookup"><span data-stu-id="86706-105">Data persistence components provide access to the data hosted within the boundaries of a microservice (that is, a microservice’s database).</span></span> <span data-ttu-id="86706-106">它們包含的元件，例如儲存機制的實際實作和[工作單位](http://martinfowler.com/eaaCatalog/unitOfWork.html)類別，如自訂 EF DBContexts。</span><span class="sxs-lookup"><span data-stu-id="86706-106">They contain the actual implementation of components such as repositories and [Unit of Work](http://martinfowler.com/eaaCatalog/unitOfWork.html) classes, like custom EF DBContexts.</span></span>

## <a name="the-repository-pattern"></a><span data-ttu-id="86706-107">儲存機制模式</span><span class="sxs-lookup"><span data-stu-id="86706-107">The Repository pattern</span></span>

<span data-ttu-id="86706-108">儲存機制是類別或元件的封裝來存取資料來源所需的邏輯。</span><span class="sxs-lookup"><span data-stu-id="86706-108">Repositories are classes or components that encapsulate the logic required to access data sources.</span></span> <span data-ttu-id="86706-109">它們集中化通用資料存取功能，提供更佳的可維護性，並減少基礎結構或技術，用來存取資料庫，從網域模型層。</span><span class="sxs-lookup"><span data-stu-id="86706-109">They centralize common data access functionality, providing better maintainability and decoupling the infrastructure or technology used to access databases from the domain model layer.</span></span> <span data-ttu-id="86706-110">如果您使用 Entity Framework 像 ORM 時，必須實作的程式碼已經過簡化，這點受惠 LINQ 和強型別。</span><span class="sxs-lookup"><span data-stu-id="86706-110">If you use an ORM like Entity Framework, the code that must be implemented is simplified, thanks to LINQ and strong typing.</span></span> <span data-ttu-id="86706-111">這可讓您將焦點放在資料持續性邏輯上，而不是資料存取配管。</span><span class="sxs-lookup"><span data-stu-id="86706-111">This lets you focus on the data persistence logic rather than on data access plumbing.</span></span>

<span data-ttu-id="86706-112">儲存機制模式會完善記載使用這種使用資料來源。</span><span class="sxs-lookup"><span data-stu-id="86706-112">The Repository pattern is a well-documented way of working with a data source.</span></span> <span data-ttu-id="86706-113">活頁簿中[企業應用程式架構模式](https://www.amazon.com/Patterns-Enterprise-Application-Architecture-Martin/dp/0321127420/)，Martin Fowler 描述儲存機制，如下所示：</span><span class="sxs-lookup"><span data-stu-id="86706-113">In the book [Patterns of Enterprise Application Architecture](https://www.amazon.com/Patterns-Enterprise-Application-Architecture-Martin/dp/0321127420/), Martin Fowler describes a repository as follows:</span></span>

<span data-ttu-id="86706-114">儲存機制會執行之間的媒介，網域模型圖層與資料對應到記憶體中的網域物件的一組類似的方式做的工作。</span><span class="sxs-lookup"><span data-stu-id="86706-114">A repository performs the tasks of an intermediary between the domain model layers and data mapping, acting in a similar way to a set of domain objects in memory.</span></span> <span data-ttu-id="86706-115">用戶端物件以宣告方式建立查詢，並將它們傳送至儲存機制的答案。</span><span class="sxs-lookup"><span data-stu-id="86706-115">Client objects declaratively build queries and send them to the repositories for answers.</span></span> <span data-ttu-id="86706-116">就概念而言，儲存機制封裝一組儲存在資料庫和作業可執行的頁面，提供一種方式較接近保存層中的物件。</span><span class="sxs-lookup"><span data-stu-id="86706-116">Conceptually, a repository encapsulates a set of objects stored in the database and operations that can be performed on them, providing a way that is closer to the persistence layer.</span></span> <span data-ttu-id="86706-117">儲存機制中，此外，支援分隔，清楚地與一個方向工作網域 」 和 「 資料配置之間的相依性或對應的目的。</span><span class="sxs-lookup"><span data-stu-id="86706-117">Repositories, also, support the purpose of separating, clearly and in one direction, the dependency between the work domain and the data allocation or mapping.</span></span>

### <a name="define-one-repository-per-aggregate"></a><span data-ttu-id="86706-118">定義彙總每一個儲存機制</span><span class="sxs-lookup"><span data-stu-id="86706-118">Define one repository per aggregate</span></span>

<span data-ttu-id="86706-119">您應針對每個彙總或彙總根，建立一個儲存機制類別。</span><span class="sxs-lookup"><span data-stu-id="86706-119">For each aggregate or aggregate root, you should create one repository class.</span></span> <span data-ttu-id="86706-120">在微服務，根據網域導向設計模式，您應該使用以更新資料庫的通道唯一應該儲存機制。</span><span class="sxs-lookup"><span data-stu-id="86706-120">In a microservice based on domain-driven design patterns, the only channel you should use to update the database should be the repositories.</span></span> <span data-ttu-id="86706-121">這是因為它們具有一對一的關聯性的彙總根，控制彙總的非變異值與交易一致性。</span><span class="sxs-lookup"><span data-stu-id="86706-121">This is because they have a one-to-one relationship with the aggregate root, which controls the aggregate’s invariants and transactional consistency.</span></span> <span data-ttu-id="86706-122">還是可以查詢資料庫，透過其他通道 （因為您可以執行下列 CQRS 方法），因為查詢不會變更資料庫的狀態。</span><span class="sxs-lookup"><span data-stu-id="86706-122">It is okay to query the database through other channels (as you can do following a CQRS approach), because queries do not change the state of the database.</span></span> <span data-ttu-id="86706-123">不過，交易式區域 — 更新 — 永遠必須控制儲存機制和彙總的根目錄。</span><span class="sxs-lookup"><span data-stu-id="86706-123">However, the transactional area—the updates—must always be controlled by the repositories and the aggregate roots.</span></span>

<span data-ttu-id="86706-124">基本上，儲存機制可讓您填入來自網域實體的表單中的資料庫的記憶體中的資料。</span><span class="sxs-lookup"><span data-stu-id="86706-124">Basically, a repository allows you to populate data in memory that comes from the database in the form of the domain entities.</span></span> <span data-ttu-id="86706-125">實體都在記憶體中之後，它們可以變更，然後回到交易透過資料庫保存。</span><span class="sxs-lookup"><span data-stu-id="86706-125">Once the entities are in memory, they can be changed and then persisted back to the database through transactions.</span></span>

<span data-ttu-id="86706-126">如前文所述，如果您使用 CQS/CQRS 架構模式，從網域模型，使用 Dapper 簡單的 SQL 陳述式所執行的側邊查詢來執行初始查詢。</span><span class="sxs-lookup"><span data-stu-id="86706-126">As noted earlier, if you are using the CQS/CQRS architectural pattern, the initial queries will be performed by side queries out of the domain model, performed by simple SQL statements using Dapper.</span></span> <span data-ttu-id="86706-127">這個方法是較具彈性的儲存機制，因此您可以查詢聯結任何資料表需要而且這些查詢不受限於的規則從彙總更多。</span><span class="sxs-lookup"><span data-stu-id="86706-127">This approach is much more flexible than repositories because you can query and join any tables you need, and these queries are not restricted by rules from the aggregates.</span></span> <span data-ttu-id="86706-128">該資料將會移至展示層或用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="86706-128">That data will go to the presentation layer or client app.</span></span>

<span data-ttu-id="86706-129">如果使用者對進行變更，更新的資料將來自用戶端應用程式或展示層到應用程式層 （例如 Web API 服務）。</span><span class="sxs-lookup"><span data-stu-id="86706-129">If the user makes changes, the data to be updated will come from the client app or presentation layer to the application layer (such as a Web API service).</span></span> <span data-ttu-id="86706-130">當您收到的命令 （資料） 是命令處理常式中時，您可以使用儲存機制取得您想要從資料庫更新的資料。</span><span class="sxs-lookup"><span data-stu-id="86706-130">When you receive a command (with data) in a command handler, you use repositories to get the data you want to update from the database.</span></span> <span data-ttu-id="86706-131">您在記憶體中已使用更新的命令，傳遞的資訊，然後加入或更新交易透過資料庫中的資料 （網域實體）。</span><span class="sxs-lookup"><span data-stu-id="86706-131">You update it in memory with the information passed with the commands, and you then add or update the data (domain entities) in the database through a transaction.</span></span>

<span data-ttu-id="86706-132">我們必須強調一次，應該對於每個彙總根，定義只能有一個儲存機制，為顯示圖 9-17。</span><span class="sxs-lookup"><span data-stu-id="86706-132">We must emphasize again that only one repository should be defined for each aggregate root, as shown in Figure 9-17.</span></span> <span data-ttu-id="86706-133">若要達到以維護交易一致性彙總中的所有物件之間的彙總根目標，您應該永遠不會在資料庫中建立每個資料表的儲存機制。</span><span class="sxs-lookup"><span data-stu-id="86706-133">To achieve the goal of the aggregate root to maintain transactional consistency between all the objects within the aggregate, you should never create a repository for each table in the database.</span></span>

![](./media/image18.png)

<span data-ttu-id="86706-134">**圖 9-17**。</span><span class="sxs-lookup"><span data-stu-id="86706-134">**Figure 9-17**.</span></span> <span data-ttu-id="86706-135">儲存機制、 彙總，以及資料庫資料表之間的關聯性</span><span class="sxs-lookup"><span data-stu-id="86706-135">The relationship between repositories, aggregates, and database tables</span></span>

### <a name="enforcing-one-aggregate-root-per-repository"></a><span data-ttu-id="86706-136">強制執行一個彙總根，每個儲存機制</span><span class="sxs-lookup"><span data-stu-id="86706-136">Enforcing one aggregate root per repository</span></span>

<span data-ttu-id="86706-137">它可以是實作您儲存機制的設計方式，它會強制執行彙總根只應該有儲存機制的規則有價值。</span><span class="sxs-lookup"><span data-stu-id="86706-137">It can be valuable to implement your repository design in such a way that it enforces the rule that only aggregate roots should have repositories.</span></span> <span data-ttu-id="86706-138">您可以建立會限制它以確定它們有 IAggregateRoot 標記介面使用的實體類型的泛型或基底的儲存機制類型。</span><span class="sxs-lookup"><span data-stu-id="86706-138">You can create a generic or base repository type that constrains the type of entities it works with to ensure they have the IAggregateRoot marker interface.</span></span>

<span data-ttu-id="86706-139">因此，在基礎結構層級實作每個儲存機制類別會實作自己的合約或介面，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="86706-139">Thus, each repository class implemented at the infrastructure layer implements its own contract or interface, as shown in the following code:</span></span>

```csharp
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class OrderRepository : IOrderRepository
    {
```

<span data-ttu-id="86706-140">每個特定的儲存機制介面會實作泛型 IRepository 介面：</span><span class="sxs-lookup"><span data-stu-id="86706-140">Each specific repository interface implements the generic IRepository interface:</span></span>

```csharp
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);
    // ...
}
```

<span data-ttu-id="86706-141">不過，強制執行慣例使程式碼更好的方法，每個儲存機制應該與相關的單一彙總就是實作泛型的儲存機制類型，所以明確使用儲存機制為目標的特定彙總。</span><span class="sxs-lookup"><span data-stu-id="86706-141">However, a better way to have the code enforce the convention that each repository should be related to a single aggregate would be to implement a generic repository type so it is explicit that you are using a repository to target a specific aggregate.</span></span> <span data-ttu-id="86706-142">可以輕鬆地完成藉由實作該泛型 IRepository 基底介面中，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="86706-142">That can be easily done by implementing that generic in the IRepository base interface, as in the following code:</span></span>

```csharp
  public interface IRepository<T> where T : IAggregateRoot
```

### <a name="the-repository-pattern-makes-it-easier-to-test-your-application-logic"></a><span data-ttu-id="86706-143">儲存機制模式可讓您更輕鬆地測試您的應用程式邏輯</span><span class="sxs-lookup"><span data-stu-id="86706-143">The Repository pattern makes it easier to test your application logic</span></span>

<span data-ttu-id="86706-144">儲存機制模式可讓您輕鬆地測試您的應用程式與單元測試。</span><span class="sxs-lookup"><span data-stu-id="86706-144">The Repository pattern allows you to easily test your application with unit tests.</span></span> <span data-ttu-id="86706-145">請記住，單元測試只測試您的程式碼，不是基礎結構，因此儲存機制的抽象概念更輕鬆地達成這個目標。</span><span class="sxs-lookup"><span data-stu-id="86706-145">Remember that unit tests only test your code, not infrastructure, so the repository abstractions make it easier to achieve that goal.</span></span>

<span data-ttu-id="86706-146">如前一節中所述，建議您定義，並放置儲存機制介面網域模型層中讓應用程式層 （比方說，您 Web 應用程式開發介面微服務） 不會依賴直接基礎結構層級具有實作實際的儲存機制類別。</span><span class="sxs-lookup"><span data-stu-id="86706-146">As noted in an earlier section, it is recommended that you define and place the repository interfaces in the domain model layer so the application layer (for instance, your Web API microservice) does not depend directly on the infrastructure layer where you have implemented the actual repository classes.</span></span> <span data-ttu-id="86706-147">如此一來，並使用您的 Web API 控制器中的相依性插入，您可以實作模擬儲存機制從資料庫傳回假的資料，而非資料。</span><span class="sxs-lookup"><span data-stu-id="86706-147">By doing this and using Dependency Injection in the controllers of your Web API, you can implement mock repositories that return fake data instead of data from the database.</span></span> <span data-ttu-id="86706-148">解除解合的方式可讓您建立，並執行的單元測試，可以測試應用程式的邏輯，而不需要連線到資料庫。</span><span class="sxs-lookup"><span data-stu-id="86706-148">That decoupled approach allows you to create and run unit tests that can test just the logic of your application without requiring connectivity to the database.</span></span>

<span data-ttu-id="86706-149">資料庫的連線可能會失敗，並更重要的是，對資料庫執行數百項測試錯誤原因有兩個。</span><span class="sxs-lookup"><span data-stu-id="86706-149">Connections to databases can fail and, more importantly, running hundreds of tests against a database is bad for two reasons.</span></span> <span data-ttu-id="86706-150">首先，因為大量的測試可能需要大量時間。</span><span class="sxs-lookup"><span data-stu-id="86706-150">First, it can take a lot of time because of the large number of tests.</span></span> <span data-ttu-id="86706-151">第二，可能會變更資料庫記錄，並影響您的測試結果，因此，它們可能不一致。</span><span class="sxs-lookup"><span data-stu-id="86706-151">Second, the database records might change and impact the results of your tests, so that they might not be consistent.</span></span> <span data-ttu-id="86706-152">對資料庫的測試並不是單元測試整合測試。</span><span class="sxs-lookup"><span data-stu-id="86706-152">Testing against the database is not a unit tests but an integration test.</span></span> <span data-ttu-id="86706-153">您應該有許多的單元測試執行快速，但較少的整合測試針對資料庫。</span><span class="sxs-lookup"><span data-stu-id="86706-153">You should have many unit tests running fast, but fewer integration tests against the databases.</span></span>

<span data-ttu-id="86706-154">單元測試的重要性分離，根據您的邏輯作業網域中的實體記憶體。</span><span class="sxs-lookup"><span data-stu-id="86706-154">In terms of separation of concerns for unit tests, your logic operates on domain entities in memory.</span></span> <span data-ttu-id="86706-155">它會假設此儲存機制類別提供的。</span><span class="sxs-lookup"><span data-stu-id="86706-155">It assumes the repository class has delivered those.</span></span> <span data-ttu-id="86706-156">一旦您的邏輯修改網域實體時，它會假設此儲存機制類別將能正確地儲存。</span><span class="sxs-lookup"><span data-stu-id="86706-156">Once your logic modifies the domain entities, it assumes the repository class will store them correctly.</span></span> <span data-ttu-id="86706-157">此處的重點是要建立單元測試對您的網域模型和其網域邏輯。</span><span class="sxs-lookup"><span data-stu-id="86706-157">The important point here is to create unit tests against your domain model and its domain logic.</span></span> <span data-ttu-id="86706-158">彙總的根目錄是 DDD 中的主要的一致性。</span><span class="sxs-lookup"><span data-stu-id="86706-158">Aggregate roots are the main consistency boundaries in DDD.</span></span>

### <a name="the-difference-between-the-repository-pattern-and-the-legacy-data-access-class-dal-class-pattern"></a><span data-ttu-id="86706-159">儲存機制模式與舊版的資料存取類別 （DAL 類別） 模式之間的差異</span><span class="sxs-lookup"><span data-stu-id="86706-159">The difference between the Repository pattern and the legacy Data Access class (DAL class) pattern</span></span>

<span data-ttu-id="86706-160">資料存取物件直接執行資料存取與持續性作業，對儲存體。</span><span class="sxs-lookup"><span data-stu-id="86706-160">A data access object directly performs data access and persistence operations against storage.</span></span> <span data-ttu-id="86706-161">儲存機制標記，與您想要執行的工作物件 （如同在 EF 使用 DbContext 時)，但這些更新的一個單位的記憶體中作業的資料不會立即執行。</span><span class="sxs-lookup"><span data-stu-id="86706-161">A repository marks the data with the operations you want to perform in the memory of a unit of work object (as in EF when using the DbContext), but these updates will not be performed immediately.</span></span>

<span data-ttu-id="86706-162">工作的單位被指視為單一交易，包括多項插入、 更新或刪除作業。</span><span class="sxs-lookup"><span data-stu-id="86706-162">A unit of work is referred to as a single transaction that involves multiple insert, update, or delete operations.</span></span> <span data-ttu-id="86706-163">簡單來說，這表示，特定的使用者動作 （例如，在網站上註冊），所有插入、 更新和刪除交易都處理在單一交易中。</span><span class="sxs-lookup"><span data-stu-id="86706-163">In simple terms, it means that for a specific user action (for example, registration on a website), all the insert, update, and delete transactions are handled in a single transaction.</span></span> <span data-ttu-id="86706-164">這是更有效率的 chattier 方式處理多個資料庫交易。</span><span class="sxs-lookup"><span data-stu-id="86706-164">This is more efficient than handling multiple database transactions in a chattier way.</span></span>

<span data-ttu-id="86706-165">您的程式碼應用程式層命令它時，將會在單一動作中稍後執行這些多個持續性作業。</span><span class="sxs-lookup"><span data-stu-id="86706-165">These multiple persistence operations will be performed later in a single action when your code from the application layer commands it.</span></span> <span data-ttu-id="86706-166">將記憶體中的變更套用至實際的資料庫儲存體的決策通常根據[工作單位模式](http://martinfowler.com/eaaCatalog/unitOfWork.html)。</span><span class="sxs-lookup"><span data-stu-id="86706-166">The decision about applying the in-memory changes to the actual database storage is typically based on the [Unit of Work pattern](http://martinfowler.com/eaaCatalog/unitOfWork.html).</span></span> <span data-ttu-id="86706-167">在 EF，工作單元模式會實作為 DBContext。</span><span class="sxs-lookup"><span data-stu-id="86706-167">In EF, the Unit of Work pattern is implemented as the DBContext.</span></span>

<span data-ttu-id="86706-168">在許多情況下，此模式或套用對儲存體作業的方式可以提高應用程式效能，並降低不一致的可能性。</span><span class="sxs-lookup"><span data-stu-id="86706-168">In many cases, this pattern or way of applying operations against the storage can increase application performance and reduce the possibility of inconsistencies.</span></span> <span data-ttu-id="86706-169">此外，它會降低交易封鎖資料庫的資料表，因為所有預期的作業都會認可為單一交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="86706-169">Also, it reduces transaction blocking in the database tables, because all the intended operations are committed as part of one transaction.</span></span> <span data-ttu-id="86706-170">這是相較於執行許多對資料庫的隔離的作業更有效率。</span><span class="sxs-lookup"><span data-stu-id="86706-170">This is more efficient in comparison to executing many isolated operations against the database.</span></span> <span data-ttu-id="86706-171">因此，所選的 ORM 可以最佳化對資料庫執行分組為相同的交易，而不是許多小型和個別的交易執行中的數個更新動作。</span><span class="sxs-lookup"><span data-stu-id="86706-171">Therefore, the selected ORM will be able to optimize the execution against the database by grouping several update actions within the same transaction, as opposed to many small and separate transaction executions.</span></span>

### <a name="repositories-should-not-be-mandatory"></a><span data-ttu-id="86706-172">儲存機制不是強制性</span><span class="sxs-lookup"><span data-stu-id="86706-172">Repositories should not be mandatory</span></span>

<span data-ttu-id="86706-173">由於稍早所提的原因很有用的自訂儲存機制，而這是在 eShopOnContainers 順序的微服務的方法。</span><span class="sxs-lookup"><span data-stu-id="86706-173">Custom repositories are useful for the reasons cited earlier, and that is the approach for the ordering microservice in eShopOnContainers.</span></span> <span data-ttu-id="86706-174">不過，它不是實作 DDD 設計中，或甚至一般的.NET 中的程式開發基本模式。</span><span class="sxs-lookup"><span data-stu-id="86706-174">However, it is not an essential pattern to implement in a DDD design or even in general development in .NET.</span></span>

<span data-ttu-id="86706-175">比方說，Jimmy Bogard，本指南中，為提供直接的意見反應時說下列：</span><span class="sxs-lookup"><span data-stu-id="86706-175">For instance, Jimmy Bogard, when providing direct feedback for this guide, said the following:</span></span>

<span data-ttu-id="86706-176">這可能會是大我的意見反應。</span><span class="sxs-lookup"><span data-stu-id="86706-176">This’ll probably be my biggest feedback.</span></span> <span data-ttu-id="86706-177">我實際上風扇的儲存機制中，主要是因為它們隱藏基礎持續性機制的重要詳細資料。</span><span class="sxs-lookup"><span data-stu-id="86706-177">I’m really not a fan of repositories, mainly because they hide the important details of the underlying persistence mechanism.</span></span> <span data-ttu-id="86706-178">它的原因在哪裡尋求 MediatR 的命令，太。</span><span class="sxs-lookup"><span data-stu-id="86706-178">It’s why I go for MediatR for commands, too.</span></span> <span data-ttu-id="86706-179">我可以使用完整的持續性的圖層，並將所有網域行為都推送至我的彙總根。</span><span class="sxs-lookup"><span data-stu-id="86706-179">I can use the full power of the persistence layer, and push all that domain behavior into my aggregate roots.</span></span> <span data-ttu-id="86706-180">通常不希望我的儲存機制的模擬 – 仍然需要的整合測試與實際的動作。</span><span class="sxs-lookup"><span data-stu-id="86706-180">I don’t usually want to mock my repositories – I still need to have that integration test with the real thing.</span></span> <span data-ttu-id="86706-181">將 CQRS，目的在於我們真的沒有任何多具有儲存機制的需求。</span><span class="sxs-lookup"><span data-stu-id="86706-181">Going CQRS meant that we didn’t really have a need for repositories any more.</span></span>

<span data-ttu-id="86706-182">我們有幫助，儲存機制，但我們了解它們並不重要的您 DDD，彙總模式和豐富的網域模型的方式。</span><span class="sxs-lookup"><span data-stu-id="86706-182">We find repositories useful, but we acknowledge that they are not critical for your DDD, in the way that the Aggregate pattern and rich domain model are.</span></span> <span data-ttu-id="86706-183">因此，要使用儲存機制模式，如 調整。</span><span class="sxs-lookup"><span data-stu-id="86706-183">Therefore, use the Repository pattern or not, as you see fit.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="86706-184">其他資源</span><span class="sxs-lookup"><span data-stu-id="86706-184">Additional resources</span></span>

##### <a name="the-repository-pattern"></a><span data-ttu-id="86706-185">儲存機制模式</span><span class="sxs-lookup"><span data-stu-id="86706-185">The Repository pattern</span></span>

-   <span data-ttu-id="86706-186">**愛德華 Hieatt 和 Rob 我。儲存機制模式。** 
     [ *http://martinfowler.com/eaaCatalog/repository.html*](http://martinfowler.com/eaaCatalog/repository.html)</span><span class="sxs-lookup"><span data-stu-id="86706-186">**Edward Hieatt and Rob Mee. Repository pattern.**
[*http://martinfowler.com/eaaCatalog/repository.html*](http://martinfowler.com/eaaCatalog/repository.html)</span></span>

-   <span data-ttu-id="86706-187">**儲存機制模式**
    [*https://msdn.microsoft.com/en-us/library/ff649690.aspx*](https://msdn.microsoft.com/en-us/library/ff649690.aspx)</span><span class="sxs-lookup"><span data-stu-id="86706-187">**The Repository pattern**
[*https://msdn.microsoft.com/en-us/library/ff649690.aspx*](https://msdn.microsoft.com/en-us/library/ff649690.aspx)</span></span>

-   <span data-ttu-id="86706-188">**儲存機制模式： 資料持續性抽象**
    [*http://deviq.com/repository-pattern/*](http://deviq.com/repository-pattern/)</span><span class="sxs-lookup"><span data-stu-id="86706-188">**Repository Pattern: A data persistence abstraction**
[*http://deviq.com/repository-pattern/*](http://deviq.com/repository-pattern/)</span></span>

-   <span data-ttu-id="86706-189">**Eric Evans：網域導向設計： 解決核心軟體的複雜度。**</span><span class="sxs-lookup"><span data-stu-id="86706-189">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software.**</span></span> <span data-ttu-id="86706-190">（書籍; 儲存機制模式的討論包括）[ *https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span><span class="sxs-lookup"><span data-stu-id="86706-190">(Book; includes a discussion of the Repository pattern) [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span></span>

##### <a name="unit-of-work-pattern"></a><span data-ttu-id="86706-191">工作模式的單位</span><span class="sxs-lookup"><span data-stu-id="86706-191">Unit of Work pattern</span></span>

-   <span data-ttu-id="86706-192">**Martin Fowler：工作模式的單位。** 
     [ *http://martinfowler.com/eaaCatalog/unitOfWork.html*](http://martinfowler.com/eaaCatalog/unitOfWork.html)</span><span class="sxs-lookup"><span data-stu-id="86706-192">**Martin Fowler. Unit of Work pattern.**
[*http://martinfowler.com/eaaCatalog/unitOfWork.html*](http://martinfowler.com/eaaCatalog/unitOfWork.html)</span></span>

<!-- -->

-   <span data-ttu-id="86706-193">**ASP.NET MVC 應用程式中實作的儲存機制和工作模式單位**
    [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)</span><span class="sxs-lookup"><span data-stu-id="86706-193">**Implementing the Repository and Unit of Work Patterns in an ASP.NET MVC Application**
[*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="86706-194">[上一個](網域-事件-設計-implementation.md) [下一步] (infrastructure-persistence-layer-implemenation-entity-framework-core.md)</span><span class="sxs-lookup"><span data-stu-id="86706-194">[Previous] (domain-events-design-implementation.md) [Next] (infrastructure-persistence-layer-implemenation-entity-framework-core.md)</span></span>
