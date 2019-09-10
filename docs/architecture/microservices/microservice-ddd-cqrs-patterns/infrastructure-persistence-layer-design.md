---
title: 設計基礎結構持續性層
description: .NET 微服務：容器化 .NET 應用程式的架構 | 探索基礎結構持續性層設計中的存放庫模式。
ms.date: 10/08/2018
ms.openlocfilehash: 76f545403a1b595ce7a541a96d212b9406d89c10
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68674115"
---
# <a name="design-the-infrastructure-persistence-layer"></a><span data-ttu-id="6e835-103">設計基礎結構持續性層</span><span class="sxs-lookup"><span data-stu-id="6e835-103">Design the infrastructure persistence layer</span></span>

<span data-ttu-id="6e835-104">資料持續性元件可讓您存取裝載於微服務界限 (也就是微服務的資料庫) 內的資料。</span><span class="sxs-lookup"><span data-stu-id="6e835-104">Data persistence components provide access to the data hosted within the boundaries of a microservice (that is, a microservice’s database).</span></span> <span data-ttu-id="6e835-105">它們包含存放庫和[工作單位](https://martinfowler.com/eaaCatalog/unitOfWork.html)類別 (例如自訂 Entity Framework (EF) <xref:Microsoft.EntityFrameworkCore.DbContext> 物件) 等元件的實際實作。</span><span class="sxs-lookup"><span data-stu-id="6e835-105">They contain the actual implementation of components such as repositories and [Unit of Work](https://martinfowler.com/eaaCatalog/unitOfWork.html) classes, like custom Entity Framework (EF) <xref:Microsoft.EntityFrameworkCore.DbContext> objects.</span></span> <span data-ttu-id="6e835-106">EF DbContext 會同時實作存放庫和工作單位模式。</span><span class="sxs-lookup"><span data-stu-id="6e835-106">EF DbContext implements both, the Repository and the Unit of Work patterns.</span></span>

## <a name="the-repository-pattern"></a><span data-ttu-id="6e835-107">儲存機制模式</span><span class="sxs-lookup"><span data-stu-id="6e835-107">The Repository pattern</span></span>

<span data-ttu-id="6e835-108">儲存機制是封裝存取資料來源所需邏輯的類別或元件。</span><span class="sxs-lookup"><span data-stu-id="6e835-108">Repositories are classes or components that encapsulate the logic required to access data sources.</span></span> <span data-ttu-id="6e835-109">它們會集中管理常見的資料存取功能，以提供更佳的可維護性，並將用來存取資料庫與用來存取領域模型層的基礎結構或技術分離。</span><span class="sxs-lookup"><span data-stu-id="6e835-109">They centralize common data access functionality, providing better maintainability and decoupling the infrastructure or technology used to access databases from the domain model layer.</span></span> <span data-ttu-id="6e835-110">如果您使用類似 Entity Framework 的物件關聯式對應程式 (ORM)，多虧有 LINQ 和強型別，必須實作的程式碼會經過簡化。</span><span class="sxs-lookup"><span data-stu-id="6e835-110">If you use an Object-Relational Mapper (ORM) like Entity Framework, the code that must be implemented is simplified, thanks to LINQ and strong typing.</span></span> <span data-ttu-id="6e835-111">這可讓您專注於資料持續性邏輯，而不是資料存取連接。</span><span class="sxs-lookup"><span data-stu-id="6e835-111">This lets you focus on the data persistence logic rather than on data access plumbing.</span></span>

<span data-ttu-id="6e835-112">儲存機制模式是使用資料來源之妥善記載的方法。</span><span class="sxs-lookup"><span data-stu-id="6e835-112">The Repository pattern is a well-documented way of working with a data source.</span></span> <span data-ttu-id="6e835-113">在 [Patterns of Enterprise Application Architecture](https://www.amazon.com/Patterns-Enterprise-Application-Architecture-Martin/dp/0321127420/) 一書中，Martin Fowler 對儲存機制有以下描述：</span><span class="sxs-lookup"><span data-stu-id="6e835-113">In the book [Patterns of Enterprise Application Architecture](https://www.amazon.com/Patterns-Enterprise-Application-Architecture-Martin/dp/0321127420/), Martin Fowler describes a repository as follows:</span></span>

> <span data-ttu-id="6e835-114">儲存機制會在領域模型層與資料對應之間執行中繼工作，其作用類似於記憶體內部的一組領域物件。</span><span class="sxs-lookup"><span data-stu-id="6e835-114">A repository performs the tasks of an intermediary between the domain model layers and data mapping, acting in a similar way to a set of domain objects in memory.</span></span> <span data-ttu-id="6e835-115">用戶端物件以宣告方式建立查詢，並將它們傳送至儲存機制以尋求解答。</span><span class="sxs-lookup"><span data-stu-id="6e835-115">Client objects declaratively build queries and send them to the repositories for answers.</span></span> <span data-ttu-id="6e835-116">就概念而言，儲存機制會封裝一組儲存在資料庫中的物件，以及可在其上執行的作業，來提供接近持續性層的方式。</span><span class="sxs-lookup"><span data-stu-id="6e835-116">Conceptually, a repository encapsulates a set of objects stored in the database and operations that can be performed on them, providing a way that is closer to the persistence layer.</span></span> <span data-ttu-id="6e835-117">儲存機制也支援清楚且一個方向的分離用途，以及工作領域與資料配置或對應之間的一致性。</span><span class="sxs-lookup"><span data-stu-id="6e835-117">Repositories, also, support the purpose of separating, clearly and in one direction, the dependency between the work domain and the data allocation or mapping.</span></span>

### <a name="define-one-repository-per-aggregate"></a><span data-ttu-id="6e835-118">每個彙總定義一個儲存機制</span><span class="sxs-lookup"><span data-stu-id="6e835-118">Define one repository per aggregate</span></span>

<span data-ttu-id="6e835-119">您應針對每個彙總或彙總根，建立一個儲存機制類別。</span><span class="sxs-lookup"><span data-stu-id="6e835-119">For each aggregate or aggregate root, you should create one repository class.</span></span> <span data-ttu-id="6e835-120">在以領域驅動設計 (DDD) 模式為基礎的微服務中，您唯一可用來更新資料庫的通道應該是存放庫。</span><span class="sxs-lookup"><span data-stu-id="6e835-120">In a microservice based on Domain-Driven Design (DDD) patterns, the only channel you should use to update the database should be the repositories.</span></span> <span data-ttu-id="6e835-121">這是因為它們具有一對一關聯性和彙總根，可控制彙總的不變式和交易一致性。</span><span class="sxs-lookup"><span data-stu-id="6e835-121">This is because they have a one-to-one relationship with the aggregate root, which controls the aggregate’s invariants and transactional consistency.</span></span> <span data-ttu-id="6e835-122">您還是可以透過其他通道來查詢資料庫 (例如您可以遵循 CQRS 方法來這樣做)，因為查詢不會變更資料庫的狀態。</span><span class="sxs-lookup"><span data-stu-id="6e835-122">It's okay to query the database through other channels (as you can do following a CQRS approach), because queries don't change the state of the database.</span></span> <span data-ttu-id="6e835-123">不過，交易區域 (也就是更新) 必須一律受到存放庫和彙總根的控制。</span><span class="sxs-lookup"><span data-stu-id="6e835-123">However, the transactional area (that is, the updates) must always be controlled by the repositories and the aggregate roots.</span></span>

<span data-ttu-id="6e835-124">基本上，儲存機制可讓您將來自資料庫的資料，以領域實體形式填入記憶體。</span><span class="sxs-lookup"><span data-stu-id="6e835-124">Basically, a repository allows you to populate data in memory that comes from the database in the form of the domain entities.</span></span> <span data-ttu-id="6e835-125">一旦實體在記憶體中，就可以變更，然後透過交易保存回到資料庫。</span><span class="sxs-lookup"><span data-stu-id="6e835-125">Once the entities are in memory, they can be changed and then persisted back to the database through transactions.</span></span>

<span data-ttu-id="6e835-126">如稍早所述，如果您使用 CQS/CQRS 架構模式，來自領域模型端的查詢 (由使用 Dapper 的簡單 SQL 陳述式來執行) 會執行初始查詢。</span><span class="sxs-lookup"><span data-stu-id="6e835-126">As noted earlier, if you're using the CQS/CQRS architectural pattern, the initial queries are performed by side queries out of the domain model, performed by simple SQL statements using Dapper.</span></span> <span data-ttu-id="6e835-127">此方法比存放庫更有彈性，因為您可以查詢並聯結任何需要的資料表，而且這些查詢不會受到彙總規則的限制。</span><span class="sxs-lookup"><span data-stu-id="6e835-127">This approach is much more flexible than repositories because you can query and join any tables you need, and these queries aren't restricted by rules from the aggregates.</span></span> <span data-ttu-id="6e835-128">該資料會移至展示層或用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="6e835-128">That data goes to the presentation layer or client app.</span></span>

<span data-ttu-id="6e835-129">如果使用者進行變更，資料會從用戶端應用程式或展示層更新至應用程式層 (例如 Web API 服務)。</span><span class="sxs-lookup"><span data-stu-id="6e835-129">If the user makes changes, the data to be updated comes from the client app or presentation layer to the application layer (such as a Web API service).</span></span> <span data-ttu-id="6e835-130">當您在命令處理常式中收到命令時，您可以使用存放庫從資料庫取得您要更新的資料。</span><span class="sxs-lookup"><span data-stu-id="6e835-130">When you receive a command in a command handler, you use repositories to get the data you want to update from the database.</span></span> <span data-ttu-id="6e835-131">您在記憶體中將它更新為使用命令所傳遞的資料，然後透過交易在資料庫中新增或更新資料 (領域實體)。</span><span class="sxs-lookup"><span data-stu-id="6e835-131">You update it in memory with the data passed with the commands, and you then add or update the data (domain entities) in the database through a transaction.</span></span>

<span data-ttu-id="6e835-132">在這裡要特別再次強調的是，您應該只會針對每個彙總根定義一個存放庫，如圖 7-17 所示。</span><span class="sxs-lookup"><span data-stu-id="6e835-132">It's important to emphasize again that you should only define one repository for each aggregate root, as shown in Figure 7-17.</span></span> <span data-ttu-id="6e835-133">若要達到在彙總內所有物件之間維持交易一致性的彙總根目標，請絕對不要針對資料庫中的每個資料表建立儲存機制。</span><span class="sxs-lookup"><span data-stu-id="6e835-133">To achieve the goal of the aggregate root to maintain transactional consistency between all the objects within the aggregate, you should never create a repository for each table in the database.</span></span>

![網域層和基礎結構層之間的關聯性：購買者彙總相依於 IBuyerRepository，而訂單彙總相依於 IOrderRepository 介面，這些介面會在基礎結構層中由對應的存放庫實作，這些存放庫不僅相依於 UnitOfWork，也在該處實作，用來存取資料層中的資料表。](./media/image18.png)

<span data-ttu-id="6e835-135">**圖 7-17**。</span><span class="sxs-lookup"><span data-stu-id="6e835-135">**Figure 7-17**.</span></span> <span data-ttu-id="6e835-136">儲存機制、彙總和資料庫資料表之間的關聯性</span><span class="sxs-lookup"><span data-stu-id="6e835-136">The relationship between repositories, aggregates, and database tables</span></span>

### <a name="enforce-one-aggregate-root-per-repository"></a><span data-ttu-id="6e835-137">每個存放庫強制執行一個彙總根</span><span class="sxs-lookup"><span data-stu-id="6e835-137">Enforce one aggregate root per repository</span></span>

<span data-ttu-id="6e835-138">以此方式來實作您的儲存機制設計可能很重要，因為它會強制執行規則，只允許彙總根有儲存機制。</span><span class="sxs-lookup"><span data-stu-id="6e835-138">It can be valuable to implement your repository design in such a way that it enforces the rule that only aggregate roots should have repositories.</span></span> <span data-ttu-id="6e835-139">您可以建立泛型或基底存放庫類型來限制可搭配使用的實體類型，確保這些實體具有 `IAggregateRoot` 標記介面。</span><span class="sxs-lookup"><span data-stu-id="6e835-139">You can create a generic or base repository type that constrains the type of entities it works with to ensure they have the `IAggregateRoot` marker interface.</span></span>

<span data-ttu-id="6e835-140">因此，在基礎結構層實作的每個儲存機制類別會實作自己的合約或介面，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="6e835-140">Thus, each repository class implemented at the infrastructure layer implements its own contract or interface, as shown in the following code:</span></span>

```csharp
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class OrderRepository : IOrderRepository
    {
      // ...
    }
}
```

<span data-ttu-id="6e835-141">每個特定儲存機制介面會實作泛型 IRepository 介面：</span><span class="sxs-lookup"><span data-stu-id="6e835-141">Each specific repository interface implements the generic IRepository interface:</span></span>

```csharp
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);
    // ...
}
```

<span data-ttu-id="6e835-142">不過，若要讓程式碼強制執行每個存放庫與單一彙總關聯的慣例，建議實作泛型存放庫類型。</span><span class="sxs-lookup"><span data-stu-id="6e835-142">However, a better way to have the code enforce the convention that each repository is related to a single aggregate is to implement a generic repository type.</span></span> <span data-ttu-id="6e835-143">如此可明確指出您使用的存放庫是以特定彙總為目標。</span><span class="sxs-lookup"><span data-stu-id="6e835-143">That way, it's explicit that you're using a repository to target a specific aggregate.</span></span> <span data-ttu-id="6e835-144">這可透過實作泛型 `IRepository` 基底介面來輕鬆完成，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="6e835-144">That can be easily done by implementing a generic `IRepository` base interface, as in the following code:</span></span>

```csharp
public interface IRepository<T> where T : IAggregateRoot
{
    //....
}
```

### <a name="the-repository-pattern-makes-it-easier-to-test-your-application-logic"></a><span data-ttu-id="6e835-145">儲存機制模式可讓您更輕鬆地測試應用程式邏輯</span><span class="sxs-lookup"><span data-stu-id="6e835-145">The Repository pattern makes it easier to test your application logic</span></span>

<span data-ttu-id="6e835-146">儲存機制模式可讓您使用單元測試輕鬆地測試應用程式。</span><span class="sxs-lookup"><span data-stu-id="6e835-146">The Repository pattern allows you to easily test your application with unit tests.</span></span> <span data-ttu-id="6e835-147">請記住，單元測試只會測試您的程式碼，不會測試基礎結構，因此儲存機制抽象概念可讓您更輕鬆地達成該目標。</span><span class="sxs-lookup"><span data-stu-id="6e835-147">Remember that unit tests only test your code, not infrastructure, so the repository abstractions make it easier to achieve that goal.</span></span>

<span data-ttu-id="6e835-148">如稍早一節所述，建議您定義存放庫介面並將它放在領域模型層中，讓應用程式層 (例如您的 Web API 微服務) 不會直接相依於您實作實際存放庫類別的基礎結構層。</span><span class="sxs-lookup"><span data-stu-id="6e835-148">As noted in an earlier section, it's recommended that you define and place the repository interfaces in the domain model layer so the application layer, such as your Web API microservice, doesn't depend directly on the infrastructure layer where you've implemented the actual repository classes.</span></span> <span data-ttu-id="6e835-149">藉由這樣做，以及在您的 Web API 的控制器中使用相依性插入，您就可以實作模擬儲存機制來傳回假的資料，而不是資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="6e835-149">By doing this and using Dependency Injection in the controllers of your Web API, you can implement mock repositories that return fake data instead of data from the database.</span></span> <span data-ttu-id="6e835-150">此低結合方法可讓您建立並執行單元測試，只著重於您應用程式的邏輯，而不需要連接到資料庫。</span><span class="sxs-lookup"><span data-stu-id="6e835-150">This decoupled approach allows you to create and run unit tests that focus the logic of your application without requiring connectivity to the database.</span></span>

<span data-ttu-id="6e835-151">資料庫連接可能會失敗，而且更重要的是，對資料庫執行數百個測試不適當的原因有兩個。</span><span class="sxs-lookup"><span data-stu-id="6e835-151">Connections to databases can fail and, more importantly, running hundreds of tests against a database is bad for two reasons.</span></span> <span data-ttu-id="6e835-152">首先，因為測試數目很大，所以可能需要很長的時間。</span><span class="sxs-lookup"><span data-stu-id="6e835-152">First, it can take a long time because of the large number of tests.</span></span> <span data-ttu-id="6e835-153">其次，資料庫記錄可能會變更並影響您的測試結果，因此結果可能會不一致。</span><span class="sxs-lookup"><span data-stu-id="6e835-153">Second, the database records might change and impact the results of your tests, so that they might not be consistent.</span></span> <span data-ttu-id="6e835-154">對資料庫進行的測試不是單元測試，而是整合測試。</span><span class="sxs-lookup"><span data-stu-id="6e835-154">Testing against the database isn't a unit test but an integration test.</span></span> <span data-ttu-id="6e835-155">您應該會有許多執行速度很快的單元測試，但對資料庫的整合測試則較少。</span><span class="sxs-lookup"><span data-stu-id="6e835-155">You should have many unit tests running fast, but fewer integration tests against the databases.</span></span>

<span data-ttu-id="6e835-156">從單元測試的關注點分離觀點來看，您的邏輯會在記憶體內部的領域實體上運作。</span><span class="sxs-lookup"><span data-stu-id="6e835-156">In terms of separation of concerns for unit tests, your logic operates on domain entities in memory.</span></span> <span data-ttu-id="6e835-157">它假設儲存機制類別已達到這些目的。</span><span class="sxs-lookup"><span data-stu-id="6e835-157">It assumes the repository class has delivered those.</span></span> <span data-ttu-id="6e835-158">一旦您的邏輯修改領域實體，它會假設儲存機制類別將會正確地儲存這些實體。</span><span class="sxs-lookup"><span data-stu-id="6e835-158">Once your logic modifies the domain entities, it assumes the repository class will store them correctly.</span></span> <span data-ttu-id="6e835-159">此處的重點是對領域模型及其領域邏輯建立單元測試。</span><span class="sxs-lookup"><span data-stu-id="6e835-159">The important point here is to create unit tests against your domain model and its domain logic.</span></span> <span data-ttu-id="6e835-160">彙總根是 DDD 中的主要一致性界限。</span><span class="sxs-lookup"><span data-stu-id="6e835-160">Aggregate roots are the main consistency boundaries in DDD.</span></span>

<span data-ttu-id="6e835-161">在 eShopOnContainers 中實作的存放庫依賴 EF Core 的 DbContext 使用其變更追蹤程式實作存放庫和工作單位模式，因此它們不會複製這項功能。</span><span class="sxs-lookup"><span data-stu-id="6e835-161">The repositories implemented in eShopOnContainers rely on EF Core’s DbContext implementation of the Repository and Unit of Work patterns using its change tracker, so they don’t duplicate this functionality.</span></span>

### <a name="the-difference-between-the-repository-pattern-and-the-legacy-data-access-class-dal-class-pattern"></a><span data-ttu-id="6e835-162">儲存機制模式與舊版資料存取類別 (DAL 類別) 模式之間的差異</span><span class="sxs-lookup"><span data-stu-id="6e835-162">The difference between the Repository pattern and the legacy Data Access class (DAL class) pattern</span></span>

<span data-ttu-id="6e835-163">資料存取物件會直接對儲存體執行資料存取和持續性作業。</span><span class="sxs-lookup"><span data-stu-id="6e835-163">A data access object directly performs data access and persistence operations against storage.</span></span> <span data-ttu-id="6e835-164">存放庫會以您要在工作單位物件的記憶體中執行的作業來標示資料 (如同使用 <xref:Microsoft.EntityFrameworkCore.DbContext> 類別時的 EF)，但不會立即對資料庫執行這些更新。</span><span class="sxs-lookup"><span data-stu-id="6e835-164">A repository marks the data with the operations you want to perform in the memory of a unit of work object (as in EF when using the <xref:Microsoft.EntityFrameworkCore.DbContext> class), but these updates aren't performed immediately to the database.</span></span>

<span data-ttu-id="6e835-165">工作單位是指涉及多項插入、更新或刪除作業的單一交易。</span><span class="sxs-lookup"><span data-stu-id="6e835-165">A unit of work is referred to as a single transaction that involves multiple insert, update, or delete operations.</span></span> <span data-ttu-id="6e835-166">簡單來說，這表示針對特定使用者動作 (例如網站註冊)，所有插入、更新和刪除作業都會在單一交易中處理。</span><span class="sxs-lookup"><span data-stu-id="6e835-166">In simple terms, it means that for a specific user action, such as a registration on a website, all the insert, update, and delete operations are handled in a single transaction.</span></span> <span data-ttu-id="6e835-167">比起更耗時地處理多個資料庫交易，這樣做會更有效率。</span><span class="sxs-lookup"><span data-stu-id="6e835-167">This is more efficient than handling multiple database transactions in a chattier way.</span></span>

<span data-ttu-id="6e835-168">稍後在單一動作中，當來自應用程式層的程式碼命令時，就會執行多個持續性作業。</span><span class="sxs-lookup"><span data-stu-id="6e835-168">These multiple persistence operations are performed later in a single action when your code from the application layer commands it.</span></span> <span data-ttu-id="6e835-169">將記憶體內部變更套用至實際資料庫儲存體的決策通常會採用[工作單位模式](https://martinfowler.com/eaaCatalog/unitOfWork.html)。</span><span class="sxs-lookup"><span data-stu-id="6e835-169">The decision about applying the in-memory changes to the actual database storage is typically based on the [Unit of Work pattern](https://martinfowler.com/eaaCatalog/unitOfWork.html).</span></span> <span data-ttu-id="6e835-170">在 EF 中，工作單位模式會實作為 <xref:Microsoft.EntityFrameworkCore.DbContext>。</span><span class="sxs-lookup"><span data-stu-id="6e835-170">In EF, the Unit of Work pattern is implemented as the <xref:Microsoft.EntityFrameworkCore.DbContext>.</span></span>

<span data-ttu-id="6e835-171">在許多情況下，此模式或對儲存體套用作業的方式可提高應用程式效能，並降低不一致的可能性。</span><span class="sxs-lookup"><span data-stu-id="6e835-171">In many cases, this pattern or way of applying operations against the storage can increase application performance and reduce the possibility of inconsistencies.</span></span> <span data-ttu-id="6e835-172">它也會降低資料庫資料表中的交易封鎖，因為所有預期的作業都會認可為單一交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="6e835-172">It also reduces transaction blocking in the database tables, because all the intended operations are committed as part of one transaction.</span></span> <span data-ttu-id="6e835-173">相較於對資料庫執行許多隔離作業，這樣做會更有效率。</span><span class="sxs-lookup"><span data-stu-id="6e835-173">This is more efficient in comparison to executing many isolated operations against the database.</span></span> <span data-ttu-id="6e835-174">因此，選取的 ORM 能夠藉由群組相同交易內的數個更新動作來最佳化對資料庫的執行，這與許多小型且個別的交易執行正好相反。</span><span class="sxs-lookup"><span data-stu-id="6e835-174">Therefore, the selected ORM can optimize the execution against the database by grouping several update actions within the same transaction, as opposed to many small and separate transaction executions.</span></span>

### <a name="repositories-shouldnt-be-mandatory"></a><span data-ttu-id="6e835-175">存放庫不應該是強制的</span><span class="sxs-lookup"><span data-stu-id="6e835-175">Repositories shouldn't be mandatory</span></span>

<span data-ttu-id="6e835-176">自訂儲存機制很有用 (原因如稍早所述)，而且是 eShopOnContainers 中訂購微服務的方法。</span><span class="sxs-lookup"><span data-stu-id="6e835-176">Custom repositories are useful for the reasons cited earlier, and that is the approach for the ordering microservice in eShopOnContainers.</span></span> <span data-ttu-id="6e835-177">不過，它不是在 DDD 設計或甚至是一般 .NET 程式開發中實作的基本模式。</span><span class="sxs-lookup"><span data-stu-id="6e835-177">However, it isn't an essential pattern to implement in a DDD design or even in general .NET development.</span></span>

<span data-ttu-id="6e835-178">例如，當 Jimmy Bogard 對本指南提供直接意見反應時表示：</span><span class="sxs-lookup"><span data-stu-id="6e835-178">For instance, Jimmy Bogard, when providing direct feedback for this guide, said the following:</span></span>

> <span data-ttu-id="6e835-179">這可能是我最強烈的意見反應。</span><span class="sxs-lookup"><span data-stu-id="6e835-179">This’ll probably be my biggest feedback.</span></span> <span data-ttu-id="6e835-180">我其實不是儲存機制的愛好者，主要是因為儲存機制會隱藏基礎持續性機制的重要詳細資料。</span><span class="sxs-lookup"><span data-stu-id="6e835-180">I’m really not a fan of repositories, mainly because they hide the important details of the underlying persistence mechanism.</span></span> <span data-ttu-id="6e835-181">這也是為什麼我使用 MediatR 命令的原因。</span><span class="sxs-lookup"><span data-stu-id="6e835-181">It’s why I go for MediatR for commands, too.</span></span> <span data-ttu-id="6e835-182">我可以利用持續性層的完整強大功能，並將所有領域行為推送至我的彙總根。</span><span class="sxs-lookup"><span data-stu-id="6e835-182">I can use the full power of the persistence layer, and push all that domain behavior into my aggregate roots.</span></span> <span data-ttu-id="6e835-183">我通常不需要模擬儲存機制 (我仍需要使用真實內容進行整合測試)。</span><span class="sxs-lookup"><span data-stu-id="6e835-183">I don’t usually want to mock my repositories – I still need to have that integration test with the real thing.</span></span> <span data-ttu-id="6e835-184">移至 CQRS 表示我們實際上不再需要儲存機制。</span><span class="sxs-lookup"><span data-stu-id="6e835-184">Going CQRS meant that we didn’t really have a need for repositories any more.</span></span>

<span data-ttu-id="6e835-185">存放庫可能很有用，但它們對您的 DDD 設計並不如彙總模式和豐富領域模型同樣重要。</span><span class="sxs-lookup"><span data-stu-id="6e835-185">Repositories might be useful, but they are not critical for your DDD design, in the way that the Aggregate pattern and rich domain model are.</span></span> <span data-ttu-id="6e835-186">因此，是否使用儲存機制模式完全取決於您。</span><span class="sxs-lookup"><span data-stu-id="6e835-186">Therefore, use the Repository pattern or not, as you see fit.</span></span> <span data-ttu-id="6e835-187">無論如何，每當您使用 EF Core 時，都會使用存放庫模式，但在此情況下，存放庫會涵蓋整個微服務或限定內容。</span><span class="sxs-lookup"><span data-stu-id="6e835-187">Anyway, you’ll be using the repository pattern whenever you use EF Core although, in this case, the repository covers the whole microservice or bounded context.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="6e835-188">其他資源</span><span class="sxs-lookup"><span data-stu-id="6e835-188">Additional resources</span></span>

### <a name="repository-pattern"></a><span data-ttu-id="6e835-189">存放庫模式</span><span class="sxs-lookup"><span data-stu-id="6e835-189">Repository pattern</span></span>

- <span data-ttu-id="6e835-190">**The Repository pattern** \ (存放庫模式)</span><span class="sxs-lookup"><span data-stu-id="6e835-190">**The Repository pattern** </span></span>\
  <https://deviq.com/repository-pattern/>

- <span data-ttu-id="6e835-191">**Edward Hieatt 和 Rob Mee：Repository pattern.** (存放庫模式)。\</span><span class="sxs-lookup"><span data-stu-id="6e835-191">**Edward Hieatt and Rob Mee. Repository pattern.**</span></span> \
  <https://martinfowler.com/eaaCatalog/repository.html>

- <span data-ttu-id="6e835-192">**The Repository pattern** \ (存放庫模式)</span><span class="sxs-lookup"><span data-stu-id="6e835-192">**The Repository pattern** </span></span>\
  <https://docs.microsoft.com/previous-versions/msp-n-p/ff649690(v=pandp.10)>

- <span data-ttu-id="6e835-193">**Eric Evans：網域驅動設計：解決軟體核心的複雜度。**</span><span class="sxs-lookup"><span data-stu-id="6e835-193">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software.**</span></span> <span data-ttu-id="6e835-194">(書籍，包括存放庫模式的討論) </span><span class="sxs-lookup"><span data-stu-id="6e835-194">(Book; includes a discussion of the Repository pattern) </span></span>\
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

### <a name="unit-of-work-pattern"></a><span data-ttu-id="6e835-195">工作單位模式</span><span class="sxs-lookup"><span data-stu-id="6e835-195">Unit of Work pattern</span></span>

- <span data-ttu-id="6e835-196">**Martin Fowler：Unit of Work pattern (工作單位模式)。** \</span><span class="sxs-lookup"><span data-stu-id="6e835-196">**Martin Fowler. Unit of Work pattern.**</span></span> \
  <https://martinfowler.com/eaaCatalog/unitOfWork.html>

- <span data-ttu-id="6e835-197">**在 ASP.NET MVC 應用程式中實作存放庫與工作單位模式** </span><span class="sxs-lookup"><span data-stu-id="6e835-197">**Implementing the Repository and Unit of Work Patterns in an ASP.NET MVC Application** </span></span>\
  <https://docs.microsoft.com/aspnet/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application>

>[!div class="step-by-step"]
><span data-ttu-id="6e835-198">[上一頁](domain-events-design-implementation.md)
>[下一頁](infrastructure-persistence-layer-implemenation-entity-framework-core.md)</span><span class="sxs-lookup"><span data-stu-id="6e835-198">[Previous](domain-events-design-implementation.md)
[Next](infrastructure-persistence-layer-implemenation-entity-framework-core.md)</span></span>
