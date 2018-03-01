---
title: "設計基礎結構持續性層"
description: "容器化 .NET 應用程式的 .NET 微服務架構 | 設計基礎結構持續性層"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/08/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 76db5388c75d4eb3b5cc23c1e57cc391a15f2934
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="designing-the-infrastructure-persistence-layer"></a><span data-ttu-id="b2e31-104">設計基礎結構持續性層</span><span class="sxs-lookup"><span data-stu-id="b2e31-104">Designing the infrastructure persistence layer</span></span>

<span data-ttu-id="b2e31-105">資料持續性元件可讓您存取裝載於微服務界限 (也就是微服務的資料庫) 內的資料。</span><span class="sxs-lookup"><span data-stu-id="b2e31-105">Data persistence components provide access to the data hosted within the boundaries of a microservice (that is, a microservice’s database).</span></span> <span data-ttu-id="b2e31-106">它們包含儲存機制和[工作單位](http://martinfowler.com/eaaCatalog/unitOfWork.html)類別 (例如自訂 EF DBContext) 等元件的實際實作。</span><span class="sxs-lookup"><span data-stu-id="b2e31-106">They contain the actual implementation of components such as repositories and [Unit of Work](http://martinfowler.com/eaaCatalog/unitOfWork.html) classes, like custom EF DBContexts.</span></span>

## <a name="the-repository-pattern"></a><span data-ttu-id="b2e31-107">儲存機制模式</span><span class="sxs-lookup"><span data-stu-id="b2e31-107">The Repository pattern</span></span>

<span data-ttu-id="b2e31-108">儲存機制是封裝存取資料來源所需邏輯的類別或元件。</span><span class="sxs-lookup"><span data-stu-id="b2e31-108">Repositories are classes or components that encapsulate the logic required to access data sources.</span></span> <span data-ttu-id="b2e31-109">它們會集中管理常見的資料存取功能，以提供更佳的可維護性，並將用來存取資料庫與用來存取領域模型層的基礎結構或技術分離。</span><span class="sxs-lookup"><span data-stu-id="b2e31-109">They centralize common data access functionality, providing better maintainability and decoupling the infrastructure or technology used to access databases from the domain model layer.</span></span> <span data-ttu-id="b2e31-110">如果您使用類似 ORM 的 Entity Framework，多虧有 LINQ 和強型別，必須實作的程式碼會經過簡化。</span><span class="sxs-lookup"><span data-stu-id="b2e31-110">If you use an ORM like Entity Framework, the code that must be implemented is simplified, thanks to LINQ and strong typing.</span></span> <span data-ttu-id="b2e31-111">這可讓您專注於資料持續性邏輯，而不是資料存取連接。</span><span class="sxs-lookup"><span data-stu-id="b2e31-111">This lets you focus on the data persistence logic rather than on data access plumbing.</span></span>

<span data-ttu-id="b2e31-112">儲存機制模式是使用資料來源之妥善記載的方法。</span><span class="sxs-lookup"><span data-stu-id="b2e31-112">The Repository pattern is a well-documented way of working with a data source.</span></span> <span data-ttu-id="b2e31-113">在 [Patterns of Enterprise Application Architecture](https://www.amazon.com/Patterns-Enterprise-Application-Architecture-Martin/dp/0321127420/) 一書中，Martin Fowler 對儲存機制有以下描述：</span><span class="sxs-lookup"><span data-stu-id="b2e31-113">In the book [Patterns of Enterprise Application Architecture](https://www.amazon.com/Patterns-Enterprise-Application-Architecture-Martin/dp/0321127420/), Martin Fowler describes a repository as follows:</span></span>

<span data-ttu-id="b2e31-114">儲存機制會在領域模型層與資料對應之間執行中繼工作，其作用類似於記憶體內部的一組領域物件。</span><span class="sxs-lookup"><span data-stu-id="b2e31-114">A repository performs the tasks of an intermediary between the domain model layers and data mapping, acting in a similar way to a set of domain objects in memory.</span></span> <span data-ttu-id="b2e31-115">用戶端物件以宣告方式建立查詢，並將它們傳送至儲存機制以尋求解答。</span><span class="sxs-lookup"><span data-stu-id="b2e31-115">Client objects declaratively build queries and send them to the repositories for answers.</span></span> <span data-ttu-id="b2e31-116">就概念而言，儲存機制會封裝一組儲存在資料庫中的物件，以及可在其上執行的作業，來提供接近持續性層的方式。</span><span class="sxs-lookup"><span data-stu-id="b2e31-116">Conceptually, a repository encapsulates a set of objects stored in the database and operations that can be performed on them, providing a way that is closer to the persistence layer.</span></span> <span data-ttu-id="b2e31-117">儲存機制也支援清楚且一個方向的分離用途，以及工作領域與資料配置或對應之間的一致性。</span><span class="sxs-lookup"><span data-stu-id="b2e31-117">Repositories, also, support the purpose of separating, clearly and in one direction, the dependency between the work domain and the data allocation or mapping.</span></span>

### <a name="define-one-repository-per-aggregate"></a><span data-ttu-id="b2e31-118">每個彙總定義一個儲存機制</span><span class="sxs-lookup"><span data-stu-id="b2e31-118">Define one repository per aggregate</span></span>

<span data-ttu-id="b2e31-119">您應針對每個彙總或彙總根，建立一個儲存機制類別。</span><span class="sxs-lookup"><span data-stu-id="b2e31-119">For each aggregate or aggregate root, you should create one repository class.</span></span> <span data-ttu-id="b2e31-120">在以領域導向設計模式為基礎的微服務中，您唯一可用來更新資料庫的通道應該是儲存機制。</span><span class="sxs-lookup"><span data-stu-id="b2e31-120">In a microservice based on domain-driven design patterns, the only channel you should use to update the database should be the repositories.</span></span> <span data-ttu-id="b2e31-121">這是因為它們具有一對一關聯性和彙總根，可控制彙總的不變式和交易一致性。</span><span class="sxs-lookup"><span data-stu-id="b2e31-121">This is because they have a one-to-one relationship with the aggregate root, which controls the aggregate’s invariants and transactional consistency.</span></span> <span data-ttu-id="b2e31-122">您還是可以透過其他通道來查詢資料庫 (例如您可以遵循 CQRS 方法來這樣做)，因為查詢不會變更資料庫的狀態。</span><span class="sxs-lookup"><span data-stu-id="b2e31-122">It is okay to query the database through other channels (as you can do following a CQRS approach), because queries do not change the state of the database.</span></span> <span data-ttu-id="b2e31-123">不過，交易區域 (更新) 必須一律受到儲存機制和彙總根的控制。</span><span class="sxs-lookup"><span data-stu-id="b2e31-123">However, the transactional area—the updates—must always be controlled by the repositories and the aggregate roots.</span></span>

<span data-ttu-id="b2e31-124">基本上，儲存機制可讓您將來自資料庫的資料，以領域實體形式填入記憶體。</span><span class="sxs-lookup"><span data-stu-id="b2e31-124">Basically, a repository allows you to populate data in memory that comes from the database in the form of the domain entities.</span></span> <span data-ttu-id="b2e31-125">一旦實體在記憶體中，就可以變更，然後透過交易保存回到資料庫。</span><span class="sxs-lookup"><span data-stu-id="b2e31-125">Once the entities are in memory, they can be changed and then persisted back to the database through transactions.</span></span>

<span data-ttu-id="b2e31-126">如稍早所述，如果您使用 CQS/CQRS 架構模式，來自領域模型端的查詢 (由使用 Dapper 的簡單 SQL 陳述式來執行) 會執行初始查詢。</span><span class="sxs-lookup"><span data-stu-id="b2e31-126">As noted earlier, if you are using the CQS/CQRS architectural pattern, the initial queries will be performed by side queries out of the domain model, performed by simple SQL statements using Dapper.</span></span> <span data-ttu-id="b2e31-127">此方法比儲存機制更有彈性，因為您可以查詢並聯結任何需要的資料表，而且這些查詢不會受到彙總規則的限制。</span><span class="sxs-lookup"><span data-stu-id="b2e31-127">This approach is much more flexible than repositories because you can query and join any tables you need, and these queries are not restricted by rules from the aggregates.</span></span> <span data-ttu-id="b2e31-128">該資料將會移至展示層或用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="b2e31-128">That data will go to the presentation layer or client app.</span></span>

<span data-ttu-id="b2e31-129">如果使用者進行變更，資料會從用戶端應用程式或展示層更新至應用程式層 (例如 Web API 服務)。</span><span class="sxs-lookup"><span data-stu-id="b2e31-129">If the user makes changes, the data to be updated will come from the client app or presentation layer to the application layer (such as a Web API service).</span></span> <span data-ttu-id="b2e31-130">當您在命令處理常式中收到命令 (含資料) 時，您可以使用儲存機制從資料庫取得您要更新的資料。</span><span class="sxs-lookup"><span data-stu-id="b2e31-130">When you receive a command (with data) in a command handler, you use repositories to get the data you want to update from the database.</span></span> <span data-ttu-id="b2e31-131">您在記憶體中將它更新為使用命令所傳遞的資訊，然後透過交易在資料庫中新增或更新資料 (領域實體)。</span><span class="sxs-lookup"><span data-stu-id="b2e31-131">You update it in memory with the information passed with the commands, and you then add or update the data (domain entities) in the database through a transaction.</span></span>

<span data-ttu-id="b2e31-132">請記住，每個彙總根只應該定義一個儲存機制，如圖 9-17 所示。</span><span class="sxs-lookup"><span data-stu-id="b2e31-132">Remember that only one repository should be defined for each aggregate root, as shown in Figure 9-17.</span></span> <span data-ttu-id="b2e31-133">若要達到在彙總內所有物件之間維持交易一致性的彙總根目標，請絕對不要針對資料庫中的每個資料表建立儲存機制。</span><span class="sxs-lookup"><span data-stu-id="b2e31-133">To achieve the goal of the aggregate root to maintain transactional consistency between all the objects within the aggregate, you should never create a repository for each table in the database.</span></span>

![](./media/image18.png)

<span data-ttu-id="b2e31-134">**圖 9-17**：</span><span class="sxs-lookup"><span data-stu-id="b2e31-134">**Figure 9-17**.</span></span> <span data-ttu-id="b2e31-135">儲存機制、彙總和資料庫資料表之間的關聯性</span><span class="sxs-lookup"><span data-stu-id="b2e31-135">The relationship between repositories, aggregates, and database tables</span></span>

### <a name="enforcing-one-aggregate-root-per-repository"></a><span data-ttu-id="b2e31-136">每個儲存機制會強制執行一個彙總根</span><span class="sxs-lookup"><span data-stu-id="b2e31-136">Enforcing one aggregate root per repository</span></span>

<span data-ttu-id="b2e31-137">以此方式來實作您的儲存機制設計可能很重要，因為它會強制執行規則，只允許彙總根有儲存機制。</span><span class="sxs-lookup"><span data-stu-id="b2e31-137">It can be valuable to implement your repository design in such a way that it enforces the rule that only aggregate roots should have repositories.</span></span> <span data-ttu-id="b2e31-138">您可以建立泛型或基底儲存機制類型來限制可搭配使用的實體類型，確保這些實體具有 IAggregateRoot 標記介面。</span><span class="sxs-lookup"><span data-stu-id="b2e31-138">You can create a generic or base repository type that constrains the type of entities it works with to ensure they have the IAggregateRoot marker interface.</span></span>

<span data-ttu-id="b2e31-139">因此，在基礎結構層實作的每個儲存機制類別會實作自己的合約或介面，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="b2e31-139">Thus, each repository class implemented at the infrastructure layer implements its own contract or interface, as shown in the following code:</span></span>

```csharp
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class OrderRepository : IOrderRepository
    {
```

<span data-ttu-id="b2e31-140">每個特定儲存機制介面會實作泛型 IRepository 介面：</span><span class="sxs-lookup"><span data-stu-id="b2e31-140">Each specific repository interface implements the generic IRepository interface:</span></span>

```csharp
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);
    // ...
}
```

<span data-ttu-id="b2e31-141">不過，若要讓程式碼強制執行每個儲存機制應該與單一彙總關聯的慣例，建議實作泛型儲存機制類型，以明確指出您使用的儲存機制是以特定彙總為目標。</span><span class="sxs-lookup"><span data-stu-id="b2e31-141">However, a better way to have the code enforce the convention that each repository should be related to a single aggregate would be to implement a generic repository type so it is explicit that you are using a repository to target a specific aggregate.</span></span> <span data-ttu-id="b2e31-142">這可透過在 IRepository 基底介面中實作該泛型來輕鬆完成，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="b2e31-142">That can be easily done by implementing that generic in the IRepository base interface, as in the following code:</span></span>

```csharp
  public interface IRepository<T> where T : IAggregateRoot
```

### <a name="the-repository-pattern-makes-it-easier-to-test-your-application-logic"></a><span data-ttu-id="b2e31-143">儲存機制模式可讓您更輕鬆地測試應用程式邏輯</span><span class="sxs-lookup"><span data-stu-id="b2e31-143">The Repository pattern makes it easier to test your application logic</span></span>

<span data-ttu-id="b2e31-144">儲存機制模式可讓您使用單元測試輕鬆地測試應用程式。</span><span class="sxs-lookup"><span data-stu-id="b2e31-144">The Repository pattern allows you to easily test your application with unit tests.</span></span> <span data-ttu-id="b2e31-145">請記住，單元測試只會測試您的程式碼，不會測試基礎結構，因此儲存機制抽象概念可讓您更輕鬆地達成該目標。</span><span class="sxs-lookup"><span data-stu-id="b2e31-145">Remember that unit tests only test your code, not infrastructure, so the repository abstractions make it easier to achieve that goal.</span></span>

<span data-ttu-id="b2e31-146">如稍早一節所述，建議您定義儲存機制介面並將它放在領域模型層中，讓應用程式層 (例如您的 Web API 微服務) 不會直接相依於您實作實際儲存機制類別的基礎結構層。</span><span class="sxs-lookup"><span data-stu-id="b2e31-146">As noted in an earlier section, it is recommended that you define and place the repository interfaces in the domain model layer so the application layer (for instance, your Web API microservice) does not depend directly on the infrastructure layer where you have implemented the actual repository classes.</span></span> <span data-ttu-id="b2e31-147">藉由這樣做，以及在您的 Web API 的控制器中使用相依性插入，您就可以實作模擬儲存機制來傳回假的資料，而不是資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="b2e31-147">By doing this and using Dependency Injection in the controllers of your Web API, you can implement mock repositories that return fake data instead of data from the database.</span></span> <span data-ttu-id="b2e31-148">該低耦合方法可讓您建立並執行單元測試，只測試您應用程式的邏輯，而不需要連接到資料庫。</span><span class="sxs-lookup"><span data-stu-id="b2e31-148">That decoupled approach allows you to create and run unit tests that can test just the logic of your application without requiring connectivity to the database.</span></span>

<span data-ttu-id="b2e31-149">資料庫連接可能會失敗，而且更重要的是，對資料庫執行數百個測試不適當的原因有兩個。</span><span class="sxs-lookup"><span data-stu-id="b2e31-149">Connections to databases can fail and, more importantly, running hundreds of tests against a database is bad for two reasons.</span></span> <span data-ttu-id="b2e31-150">首先，因為測試數目很大，所以可能需要很多時間。</span><span class="sxs-lookup"><span data-stu-id="b2e31-150">First, it can take a lot of time because of the large number of tests.</span></span> <span data-ttu-id="b2e31-151">其次，資料庫記錄可能會變更並影響您的測試結果，因此結果可能會不一致。</span><span class="sxs-lookup"><span data-stu-id="b2e31-151">Second, the database records might change and impact the results of your tests, so that they might not be consistent.</span></span> <span data-ttu-id="b2e31-152">對資料庫進行的測試不是單元測試，而是整合測試。</span><span class="sxs-lookup"><span data-stu-id="b2e31-152">Testing against the database is not a unit tests but an integration test.</span></span> <span data-ttu-id="b2e31-153">您應該會有許多執行速度很快的單元測試，但對資料庫的整合測試則較少。</span><span class="sxs-lookup"><span data-stu-id="b2e31-153">You should have many unit tests running fast, but fewer integration tests against the databases.</span></span>

<span data-ttu-id="b2e31-154">從單元測試的關注點分離觀點來看，您的邏輯會在記憶體內部的領域實體上運作。</span><span class="sxs-lookup"><span data-stu-id="b2e31-154">In terms of separation of concerns for unit tests, your logic operates on domain entities in memory.</span></span> <span data-ttu-id="b2e31-155">它假設儲存機制類別已達到這些目的。</span><span class="sxs-lookup"><span data-stu-id="b2e31-155">It assumes the repository class has delivered those.</span></span> <span data-ttu-id="b2e31-156">一旦您的邏輯修改領域實體，它會假設儲存機制類別將會正確地儲存這些實體。</span><span class="sxs-lookup"><span data-stu-id="b2e31-156">Once your logic modifies the domain entities, it assumes the repository class will store them correctly.</span></span> <span data-ttu-id="b2e31-157">此處的重點是對領域模型及其領域邏輯建立單元測試。</span><span class="sxs-lookup"><span data-stu-id="b2e31-157">The important point here is to create unit tests against your domain model and its domain logic.</span></span> <span data-ttu-id="b2e31-158">彙總根是 DDD 中的主要一致性界限。</span><span class="sxs-lookup"><span data-stu-id="b2e31-158">Aggregate roots are the main consistency boundaries in DDD.</span></span>

### <a name="the-difference-between-the-repository-pattern-and-the-legacy-data-access-class-dal-class-pattern"></a><span data-ttu-id="b2e31-159">儲存機制模式與舊版資料存取類別 (DAL 類別) 模式之間的差異</span><span class="sxs-lookup"><span data-stu-id="b2e31-159">The difference between the Repository pattern and the legacy Data Access class (DAL class) pattern</span></span>

<span data-ttu-id="b2e31-160">資料存取物件會直接對儲存體執行資料存取和持續性作業。</span><span class="sxs-lookup"><span data-stu-id="b2e31-160">A data access object directly performs data access and persistence operations against storage.</span></span> <span data-ttu-id="b2e31-161">儲存機制會以您要在工作單位物件的記憶體中執行的作業來標示資料 (如同使用 DbContext 時的 EF)，但不會立即執行這些更新。</span><span class="sxs-lookup"><span data-stu-id="b2e31-161">A repository marks the data with the operations you want to perform in the memory of a unit of work object (as in EF when using the DbContext), but these updates aren't performed immediately.</span></span>

<span data-ttu-id="b2e31-162">工作單位是指涉及多項插入、更新或刪除作業的單一交易。</span><span class="sxs-lookup"><span data-stu-id="b2e31-162">A unit of work is referred to as a single transaction that involves multiple insert, update, or delete operations.</span></span> <span data-ttu-id="b2e31-163">簡單來說，這表示針對特定使用者動作 (例如網站註冊)，所有插入、更新和刪除交易都會在單一交易中處理。</span><span class="sxs-lookup"><span data-stu-id="b2e31-163">In simple terms, it means that for a specific user action (for example, registration on a website), all the insert, update, and delete transactions are handled in a single transaction.</span></span> <span data-ttu-id="b2e31-164">比起更耗時地處理多個資料庫交易，這樣做會更有效率。</span><span class="sxs-lookup"><span data-stu-id="b2e31-164">This is more efficient than handling multiple database transactions in a chattier way.</span></span>

<span data-ttu-id="b2e31-165">稍後在單一動作中，當來自應用程式層的程式碼命令時，就會執行多個持續性作業。</span><span class="sxs-lookup"><span data-stu-id="b2e31-165">These multiple persistence operations are performed later in a single action when your code from the application layer commands it.</span></span> <span data-ttu-id="b2e31-166">將記憶體內部變更套用至實際資料庫儲存體的決策通常會採用[工作單位模式](http://martinfowler.com/eaaCatalog/unitOfWork.html)。</span><span class="sxs-lookup"><span data-stu-id="b2e31-166">The decision about applying the in-memory changes to the actual database storage is typically based on the [Unit of Work pattern](http://martinfowler.com/eaaCatalog/unitOfWork.html).</span></span> <span data-ttu-id="b2e31-167">在 EF 中，工作單位模式會實作為 DBContext。</span><span class="sxs-lookup"><span data-stu-id="b2e31-167">In EF, the Unit of Work pattern is implemented as the DBContext.</span></span>

<span data-ttu-id="b2e31-168">在許多情況下，此模式或對儲存體套用作業的方式可提高應用程式效能，並降低不一致的可能性。</span><span class="sxs-lookup"><span data-stu-id="b2e31-168">In many cases, this pattern or way of applying operations against the storage can increase application performance and reduce the possibility of inconsistencies.</span></span> <span data-ttu-id="b2e31-169">此外，它會降低資料庫資料表中的交易封鎖，因為所有預期的作業都會認可為單一交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="b2e31-169">Also, it reduces transaction blocking in the database tables, because all the intended operations are committed as part of one transaction.</span></span> <span data-ttu-id="b2e31-170">相較於對資料庫執行許多隔離作業，這樣做會更有效率。</span><span class="sxs-lookup"><span data-stu-id="b2e31-170">This is more efficient in comparison to executing many isolated operations against the database.</span></span> <span data-ttu-id="b2e31-171">因此，選取的 ORM 能夠藉由群組相同交易內的數個更新動作來最佳化對資料庫的執行，這與許多小型且個別的交易執行正好相反。</span><span class="sxs-lookup"><span data-stu-id="b2e31-171">Therefore, the selected ORM is able to optimize the execution against the database by grouping several update actions within the same transaction, as opposed to many small and separate transaction executions.</span></span>

### <a name="repositories-should-not-be-mandatory"></a><span data-ttu-id="b2e31-172">儲存機制不應該是強制的</span><span class="sxs-lookup"><span data-stu-id="b2e31-172">Repositories should not be mandatory</span></span>

<span data-ttu-id="b2e31-173">自訂儲存機制很有用 (原因如稍早所述)，而且是 eShopOnContainers 中訂購微服務的方法。</span><span class="sxs-lookup"><span data-stu-id="b2e31-173">Custom repositories are useful for the reasons cited earlier, and that is the approach for the ordering microservice in eShopOnContainers.</span></span> <span data-ttu-id="b2e31-174">不過，它不是在 DDD 設計或甚至是一般 .NET 程式開發中實作的基本模式。</span><span class="sxs-lookup"><span data-stu-id="b2e31-174">However, it is not an essential pattern to implement in a DDD design or even in general development in .NET.</span></span>

<span data-ttu-id="b2e31-175">例如，當 Jimmy Bogard 對本指南提供直接意見反應時表示：</span><span class="sxs-lookup"><span data-stu-id="b2e31-175">For instance, Jimmy Bogard, when providing direct feedback for this guide, said the following:</span></span>

<span data-ttu-id="b2e31-176">這可能是我最強烈的意見反應。</span><span class="sxs-lookup"><span data-stu-id="b2e31-176">This’ll probably be my biggest feedback.</span></span> <span data-ttu-id="b2e31-177">我其實不是儲存機制的愛好者，主要是因為儲存機制會隱藏基礎持續性機制的重要詳細資料。</span><span class="sxs-lookup"><span data-stu-id="b2e31-177">I’m really not a fan of repositories, mainly because they hide the important details of the underlying persistence mechanism.</span></span> <span data-ttu-id="b2e31-178">這也是為什麼我使用 MediatR 命令的原因。</span><span class="sxs-lookup"><span data-stu-id="b2e31-178">It’s why I go for MediatR for commands, too.</span></span> <span data-ttu-id="b2e31-179">我可以利用持續性層的完整強大功能，並將所有領域行為推送至我的彙總根。</span><span class="sxs-lookup"><span data-stu-id="b2e31-179">I can use the full power of the persistence layer, and push all that domain behavior into my aggregate roots.</span></span> <span data-ttu-id="b2e31-180">我通常不需要模擬儲存機制 (我仍需要使用真實內容進行整合測試)。</span><span class="sxs-lookup"><span data-stu-id="b2e31-180">I don’t usually want to mock my repositories – I still need to have that integration test with the real thing.</span></span> <span data-ttu-id="b2e31-181">移至 CQRS 表示我們實際上不再需要儲存機制。</span><span class="sxs-lookup"><span data-stu-id="b2e31-181">Going CQRS meant that we didn’t really have a need for repositories any more.</span></span>

<span data-ttu-id="b2e31-182">我們發現儲存機制雖然有用，但認為它對您的 DDD 並不如彙總模式和豐富領域模型同樣重要。</span><span class="sxs-lookup"><span data-stu-id="b2e31-182">We find repositories useful, but we acknowledge that they are not critical for your DDD, in the way that the Aggregate pattern and rich domain model are.</span></span> <span data-ttu-id="b2e31-183">因此，是否使用儲存機制模式完全取決於您。</span><span class="sxs-lookup"><span data-stu-id="b2e31-183">Therefore, use the Repository pattern or not, as you see fit.</span></span>

## <a name="the-specification-pattern"></a><span data-ttu-id="b2e31-184">規格模式</span><span class="sxs-lookup"><span data-stu-id="b2e31-184">The Specification pattern</span></span>

<span data-ttu-id="b2e31-185">規格模式 (其全名會是查詢規格模式) 是領域導向設計模式，設計成您可以放置查詢定義以及選擇性排序和分頁邏輯的位置。</span><span class="sxs-lookup"><span data-stu-id="b2e31-185">The Specification pattern (its full name would be Query-specification pattern) is a Domain-Driven Design pattern designed as the place where you can put the definition of a query with optional sorting and paging logic.</span></span>

<span data-ttu-id="b2e31-186">規格模式會定義物件中的查詢。</span><span class="sxs-lookup"><span data-stu-id="b2e31-186">The Specification pattern defines a query in an object.</span></span> <span data-ttu-id="b2e31-187">例如，若要封裝搜尋一些產品的分頁查詢，您可以建立 PagedProduct 規格來接受必要的輸入參數 (pageNumber、pageSize、filter 等)。</span><span class="sxs-lookup"><span data-stu-id="b2e31-187">For example, in order to encapsulate a paged query that searches for some products, you can create a PagedProduct specification that takes the necessary input parameters (pageNumber, pageSize, filter, etc.).</span></span> <span data-ttu-id="b2e31-188">然後，在任何儲存機制方法中 (通常是 List() 多載)，它會接受 ISpecification 並根據規格執行預期的查詢。</span><span class="sxs-lookup"><span data-stu-id="b2e31-188">Then, within any Repository method (usually a List() overload) it would accept an ISpecification and run the expected query based on that specification.</span></span>

<span data-ttu-id="b2e31-189">此方法有幾個好處：</span><span class="sxs-lookup"><span data-stu-id="b2e31-189">There are several benefits to this approach:</span></span>

* <span data-ttu-id="b2e31-190">規格具有您可以討論的名稱 (而不是只有一些 LINQ 運算式)。</span><span class="sxs-lookup"><span data-stu-id="b2e31-190">The specification has a name (as opposed to just a bunch of LINQ expressions) that you can discuss about.</span></span>

* <span data-ttu-id="b2e31-191">規格可隔離進行單元測試，以確保其正確無誤。</span><span class="sxs-lookup"><span data-stu-id="b2e31-191">The specification can be unit tested in isolation to ensure it is right.</span></span> <span data-ttu-id="b2e31-192">如果您需要類似的行為，也很容易重複使用。</span><span class="sxs-lookup"><span data-stu-id="b2e31-192">It can also easily be reused if you need similar behavior.</span></span> <span data-ttu-id="b2e31-193">例如，在 MVC 檢視動作和 Web API 動作上，以及在各種服務中。</span><span class="sxs-lookup"><span data-stu-id="b2e31-193">For example, on an MVC View action and a Web API action, as well as in various services.</span></span>

* <span data-ttu-id="b2e31-194">規格也可用來描述要傳回之資料的圖形，讓查詢只傳回所需的資料。</span><span class="sxs-lookup"><span data-stu-id="b2e31-194">A specification can also be used to describe the shape of the data to be returned, so that queries can return just the data they required.</span></span> <span data-ttu-id="b2e31-195">這樣做可避免必須在 Web 應用程式中進行消極式載入 (通常並不建議)，也可協助防止儲存機制實作因為這些詳細資料而變得雜亂無章。</span><span class="sxs-lookup"><span data-stu-id="b2e31-195">This eliminates the need for lazy loading in web applications (which is usually not a good idea) and helps keep repository implementations from becoming cluttered with these details.</span></span>

<span data-ttu-id="b2e31-196">泛型規格介面的一個範例是來自 [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb ) 的下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="b2e31-196">An example of a generic Specification interface is the following code from [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb ).</span></span>

```csharp
// https://github.com/dotnet-architecture/eShopOnWeb 
public interface ISpecification<T>
{
    Expression<Func<T, bool>> Criteria { get; }
    List<Expression<Func<T, object>>> Includes { get; }
    List<string> IncludeStrings { get; }
}
```

<span data-ttu-id="b2e31-197">在接下來的章節中，將會說明如何使用 Entity Framework Core 2.0 來實作規格模式，以及如何從任何儲存機制類別來使用它。</span><span class="sxs-lookup"><span data-stu-id="b2e31-197">In the upcoming sections, it is explained how to implement the Specification pattern with Entity Framework Core 2.0 and how to use it from any Repository class.</span></span>

<span data-ttu-id="b2e31-198">**重要事項：**規格模式是可透過許多不同方式實作的舊模式，如下列其他資源所示。</span><span class="sxs-lookup"><span data-stu-id="b2e31-198">**Important note:** The specification pattern is an old pattern that can be implemented in many different ways, as in the following additional resources.</span></span> <span data-ttu-id="b2e31-199">作為模式/概念，較舊的方法比較容易了解，但請注意，較舊的實作不會利用 Linq 和運算式等現代語言功能。</span><span class="sxs-lookup"><span data-stu-id="b2e31-199">As a pattern/idea, older approaches are good to know, but beware of older implementations that are not taking advantage of modern language capabilities like Linq and expressions.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="b2e31-200">其他資源</span><span class="sxs-lookup"><span data-stu-id="b2e31-200">Additional resources</span></span>

### <a name="the-repository-pattern"></a><span data-ttu-id="b2e31-201">儲存機制模式</span><span class="sxs-lookup"><span data-stu-id="b2e31-201">The Repository pattern</span></span>

-   <span data-ttu-id="b2e31-202">**Edward Hieatt 和 Rob Mee：Repository (儲存機制) 模式**
    [*http://martinfowler.com/eaaCatalog/repository.html*](http://martinfowler.com/eaaCatalog/repository.html)</span><span class="sxs-lookup"><span data-stu-id="b2e31-202">**Edward Hieatt and Rob Mee. Repository pattern.**
[*http://martinfowler.com/eaaCatalog/repository.html*](http://martinfowler.com/eaaCatalog/repository.html)</span></span>

-   <span data-ttu-id="b2e31-203">**The Repository Pattern (儲存機制模式)**
    [*https://msdn.microsoft.com/library/ff649690.aspx*](https://msdn.microsoft.com/library/ff649690.aspx)</span><span class="sxs-lookup"><span data-stu-id="b2e31-203">**The Repository pattern**
[*https://msdn.microsoft.com/library/ff649690.aspx*](https://msdn.microsoft.com/library/ff649690.aspx)</span></span>

-   <span data-ttu-id="b2e31-204">**Repository Pattern: A data persistence abstraction (儲存機制模式：資料持續性抽象概念)**
    [*http://deviq.com/repository-pattern/*](http://deviq.com/repository-pattern/)</span><span class="sxs-lookup"><span data-stu-id="b2e31-204">**Repository Pattern: A data persistence abstraction**
[*http://deviq.com/repository-pattern/*](http://deviq.com/repository-pattern/)</span></span>

-   <span data-ttu-id="b2e31-205">**Eric Evans：Domain-Driven Design: Tackling Complexity in the Heart of Software**</span><span class="sxs-lookup"><span data-stu-id="b2e31-205">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software.**</span></span> <span data-ttu-id="b2e31-206">(叢書，內含儲存機制模式的討論) [ *https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span><span class="sxs-lookup"><span data-stu-id="b2e31-206">(Book; includes a discussion of the Repository pattern) [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span></span>

### <a name="unit-of-work-pattern"></a><span data-ttu-id="b2e31-207">工作單位模式</span><span class="sxs-lookup"><span data-stu-id="b2e31-207">Unit of Work pattern</span></span>

-   <span data-ttu-id="b2e31-208">**Martin Fowler：Unit of Work (工作單位) 模式**
    [*http://martinfowler.com/eaaCatalog/unitOfWork.html*](http://martinfowler.com/eaaCatalog/unitOfWork.html)</span><span class="sxs-lookup"><span data-stu-id="b2e31-208">**Martin Fowler. Unit of Work pattern.**
[*http://martinfowler.com/eaaCatalog/unitOfWork.html*](http://martinfowler.com/eaaCatalog/unitOfWork.html)</span></span>

<!-- -->

-   <span data-ttu-id="b2e31-209">**Implementing the Repository and Unit of Work Patterns in an ASP.NET MVC Application (在 ASP.NET MVC 應用程式中實作儲存機制和工作單位模式)**
    [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)</span><span class="sxs-lookup"><span data-stu-id="b2e31-209">**Implementing the Repository and Unit of Work Patterns in an ASP.NET MVC Application**
[*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)</span></span>

### <a name="the-specification-pattern"></a><span data-ttu-id="b2e31-210">規格模式</span><span class="sxs-lookup"><span data-stu-id="b2e31-210">The Specification pattern</span></span>

-   <span data-ttu-id="b2e31-211">**Specification Pattern (規格模式)**
    [*http://deviq.com/specification-pattern/*](http://deviq.com/specification-pattern/)</span><span class="sxs-lookup"><span data-stu-id="b2e31-211">**The Specification pattern.**
[*http://deviq.com/specification-pattern/*](http://deviq.com/specification-pattern/)</span></span>

-   <span data-ttu-id="b2e31-212">**Eric Evans (2004)：Domain Driven Design，Addison-Wesley，第 224 頁。**</span><span class="sxs-lookup"><span data-stu-id="b2e31-212">**Evans, Eric (2004). Domain Driven Design. Addison-Wesley. p. 224.**</span></span>

-   <span data-ttu-id="b2e31-213">**Specifications (規格)，Martin Fowler**
    [*https://www.martinfowler.com/apsupp/spec.pdf/*](https://www.martinfowler.com/apsupp/spec.pdf)</span><span class="sxs-lookup"><span data-stu-id="b2e31-213">**Specifications. Martin Fowler**
[*https://www.martinfowler.com/apsupp/spec.pdf/*](https://www.martinfowler.com/apsupp/spec.pdf)</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="b2e31-214">[上一個] (domain-events-design-implementation.md) [下一個] (infrastructure-persistence-layer-implemenation-entity-framework-core.md)</span><span class="sxs-lookup"><span data-stu-id="b2e31-214">[Previous] (domain-events-design-implementation.md) [Next] (infrastructure-persistence-layer-implemenation-entity-framework-core.md)</span></span>
