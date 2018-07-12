---
title: 設計微服務領域模型
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 設計微服務領域模型
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/09/2017
ms.openlocfilehash: e672685666c846ea63bcd9cdb713af58f5e6fb1b
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106248"
---
# <a name="designing-a-microservice-domain-model"></a><span data-ttu-id="44709-103">設計微服務領域模型</span><span class="sxs-lookup"><span data-stu-id="44709-103">Designing a microservice domain model</span></span>

<span data-ttu-id="44709-104">*為每個商務微服務或限定內容定義一個豐富領域模型*</span><span class="sxs-lookup"><span data-stu-id="44709-104">*Define one rich domain model for each business microservice or Bounded Context*</span></span>

<span data-ttu-id="44709-105">您的目標是為每個商務微服務或限定內容 (BC) 建立單一內聚領域模型。</span><span class="sxs-lookup"><span data-stu-id="44709-105">Your goal is to create a single cohesive domain model for each business microservice or Bounded Context (BC).</span></span> <span data-ttu-id="44709-106">不過請記住，BC 或商務微服務有時候可能是由共用單一領域模型的多個實體服務所組成。</span><span class="sxs-lookup"><span data-stu-id="44709-106">Keep in mind, however, that a BC or business microservice could sometimes be composed of several physical services that share a single domain model.</span></span> <span data-ttu-id="44709-107">領域模型必須擷取單一限定內容或其代表之商務微服務的規則、行為、商務語言和限定式。</span><span class="sxs-lookup"><span data-stu-id="44709-107">The domain model must capture the rules, behavior, business language, and constraints of the single Bounded Context or business microservice that it represents.</span></span>

## <a name="the-domain-entity-pattern"></a><span data-ttu-id="44709-108">領域實體模式</span><span class="sxs-lookup"><span data-stu-id="44709-108">The Domain Entity pattern</span></span>

<span data-ttu-id="44709-109">實體代表領域物件，而且主要是由其身分識別、連續性及一段時間的持續性所定義，而不只是由包含這些項目的屬性所定義。</span><span class="sxs-lookup"><span data-stu-id="44709-109">Entities represent domain objects and are primarily defined by their identity, continuity, and persistence over time, and not only by the attributes that comprise them.</span></span> <span data-ttu-id="44709-110">如同 Eric Evans 指出，「主要是由其身分識別定義的物件稱為實體」。</span><span class="sxs-lookup"><span data-stu-id="44709-110">As Eric Evans says, “an object primarily defined by its identity is called an Entity.”</span></span> <span data-ttu-id="44709-111">實體在領域模型中很重要，因為它們是模型的基礎。</span><span class="sxs-lookup"><span data-stu-id="44709-111">Entities are very important in the domain model, since they are the base for a model.</span></span> <span data-ttu-id="44709-112">因此，您應該仔細識別及設計。</span><span class="sxs-lookup"><span data-stu-id="44709-112">Therefore, you should identify and design them carefully.</span></span>

<span data-ttu-id="44709-113">*實體的識別身分可跨多個微服務或限定內容。*</span><span class="sxs-lookup"><span data-stu-id="44709-113">*An entity’s identity can cross multiple microservices or Bounded Contexts.*</span></span>

<span data-ttu-id="44709-114">您可以在多個限定內容或微服務之間建立相同身分識別 (但不同實體) 的模型。</span><span class="sxs-lookup"><span data-stu-id="44709-114">The same identity (though not the same entity) can be modeled across multiple Bounded Contexts or microservices.</span></span> <span data-ttu-id="44709-115">不過，這並不表示會在多個限定內容中實作具有相同屬性和邏輯的相同實體。</span><span class="sxs-lookup"><span data-stu-id="44709-115">However, that does not imply that the same entity, with the same attributes and logic would be implemented in multiple Bounded Contexts.</span></span> <span data-ttu-id="44709-116">相反地，每個限定內容中的實體會將其屬性和行為，限制為該限定內容的領域中所需的屬性和行為。</span><span class="sxs-lookup"><span data-stu-id="44709-116">Instead, entities in each Bounded Context limit their attributes and behaviors to those required in that Bounded Context’s domain.</span></span>

<span data-ttu-id="44709-117">例如，購買者實體可能會在設定檔或身分識別微服務的使用者實體中定義某個人的大部分屬性，包括身分識別。</span><span class="sxs-lookup"><span data-stu-id="44709-117">For instance, the buyer entity might have most of a person’s attributes that are defined in the user entity in the profile or identity microservice, including the identity.</span></span> <span data-ttu-id="44709-118">但訂購微服務中的購買者實體可能有較少的屬性，因為只有特定購買者資料會與訂購流程相關。</span><span class="sxs-lookup"><span data-stu-id="44709-118">But the buyer entity in the ordering microservice might have fewer attributes, because only certain buyer data is related to the order process.</span></span> <span data-ttu-id="44709-119">每個微服務或限定內容的內容會影響其領域模型。</span><span class="sxs-lookup"><span data-stu-id="44709-119">The context of each microservice or Bounded Context impacts its domain model.</span></span>

<span data-ttu-id="44709-120">*除了實作資料屬性，領域實體必須實作行為*</span><span class="sxs-lookup"><span data-stu-id="44709-120">*Domain entities must implement behavior in addition to implementing data attributes*</span></span>

<span data-ttu-id="44709-121">DDD 中的領域實體必須實作與實體資料 (從記憶體存取的物件) 相關的領域邏輯或行為。</span><span class="sxs-lookup"><span data-stu-id="44709-121">A domain entity in DDD must implement the domain logic or behavior related to the entity data (the object accessed in memory).</span></span> <span data-ttu-id="44709-122">例如，作為訂單實體類別的一部分，您必須將商務邏輯和作業實作為工作的方法，例如新增訂單項目、資料驗證和總計算。</span><span class="sxs-lookup"><span data-stu-id="44709-122">For example, as part of an order entity class you must have business logic and operations implemented as methods for tasks such as adding an order item, data validation, and total calculation.</span></span> <span data-ttu-id="44709-123">實體的方法會處理實體的不變式和規則，而不是跨應用程式層散佈這些規則。</span><span class="sxs-lookup"><span data-stu-id="44709-123">The entity’s methods take care of the invariants and rules of the entity instead of having those rules spread across the application layer.</span></span>

<span data-ttu-id="44709-124">圖 9-8 所顯示的領域實體不只會實作資料屬性，還會實作含有相關領域邏輯的作業或方法。</span><span class="sxs-lookup"><span data-stu-id="44709-124">Figure 9-8 shows a domain entity that implements not only data attributes but operations or methods with related domain logic.</span></span>

![](./media/image9.png)

<span data-ttu-id="44709-125">**圖 9-8**：</span><span class="sxs-lookup"><span data-stu-id="44709-125">**Figure 9-8**.</span></span> <span data-ttu-id="44709-126">實作資料加上行為的領域實體設計範例</span><span class="sxs-lookup"><span data-stu-id="44709-126">Example of a domain entity design implementing data plus behavior</span></span>

<span data-ttu-id="44709-127">當然，有時候您可以有未實作任何邏輯作為實體類別一部分的實體。</span><span class="sxs-lookup"><span data-stu-id="44709-127">Of course, sometimes you can have entities that do not implement any logic as part of the entity class.</span></span> <span data-ttu-id="44709-128">如果子實體沒有任何特殊邏輯，彙總內的子實體就可能會發生這種情況，因為彙總根中已定義大部分邏輯。</span><span class="sxs-lookup"><span data-stu-id="44709-128">This can happen in child entities within an aggregate if the child entity does not have any special logic because most of the logic is defined in the aggregate root.</span></span> <span data-ttu-id="44709-129">如果您有一個複雜的微服務在服務類別 (而不是領域實體) 中實作許多邏輯，則可能會落入 Anemic 領域模型中，如下一節中所述。</span><span class="sxs-lookup"><span data-stu-id="44709-129">If you have a complex microservice that has a lot of logic implemented in the service classes instead of in the domain entities, you could be falling into the anemic domain model, explained in the following section.</span></span>

### <a name="rich-domain-model-versus-anemic-domain-model"></a><span data-ttu-id="44709-130">豐富領域模型與 Anemic 領域模型</span><span class="sxs-lookup"><span data-stu-id="44709-130">Rich domain model versus anemic domain model</span></span>

<span data-ttu-id="44709-131">Martin Fowler 在 [AnemicDomainModel](https://martinfowler.com/bliki/AnemicDomainModel.html) (Anemic 領域模型) 一文中對 Anemic 領域模型有以下描述：</span><span class="sxs-lookup"><span data-stu-id="44709-131">In his post [AnemicDomainModel](https://martinfowler.com/bliki/AnemicDomainModel.html), Martin Fowler describes an anemic domain model this way:</span></span>

<span data-ttu-id="44709-132">Anemic 領域模型的基本特徵是，乍看之下很像實物。</span><span class="sxs-lookup"><span data-stu-id="44709-132">The basic symptom of an Anemic Domain Model is that at first blush it looks like the real thing.</span></span> <span data-ttu-id="44709-133">其中包含物件，許多物件會以領域空間中的名詞來命名，而且這些物件會透過真實領域模型所具有的豐富關聯性和結構來連接。</span><span class="sxs-lookup"><span data-stu-id="44709-133">There are objects, many named after the nouns in the domain space, and these objects are connected with the rich relationships and structure that true domain models have.</span></span> <span data-ttu-id="44709-134">從行為上會看出端倪，並了解這些物件上幾乎沒有任何行為，比較像是一組 getter 和 setter。</span><span class="sxs-lookup"><span data-stu-id="44709-134">The catch comes when you look at the behavior, and you realize that there is hardly any behavior on these objects, making them little more than bags of getters and setters.</span></span>

<span data-ttu-id="44709-135">當然，使用 Anemic 領域模型時，會從一組擷取所有領域或商務邏輯的服務物件 (傳統上稱為「商務層」) 來使用這些資料模型。</span><span class="sxs-lookup"><span data-stu-id="44709-135">Of course, when you use an anemic domain model, those data models will be used from a set of service objects (traditionally named the *business layer*) which capture all the domain or business logic.</span></span> <span data-ttu-id="44709-136">商務層位於資料模型最上層，其使用資料模型的方式就像是資料一樣。</span><span class="sxs-lookup"><span data-stu-id="44709-136">The business layer sits on top of the data model and uses the data model just as data.</span></span>

<span data-ttu-id="44709-137">Anemic 領域模型只是程序樣式設計。</span><span class="sxs-lookup"><span data-stu-id="44709-137">The anemic domain model is just a procedural style design.</span></span> <span data-ttu-id="44709-138">Anemic 實體物件不是真正的物件，因為它們缺少行為 (方法)。</span><span class="sxs-lookup"><span data-stu-id="44709-138">Anemic entity objects are not real objects because they lack behavior (methods).</span></span> <span data-ttu-id="44709-139">它們只會保存資料屬性，因此不是物件導向設計。</span><span class="sxs-lookup"><span data-stu-id="44709-139">They only hold data properties and thus it is not object-oriented design.</span></span> <span data-ttu-id="44709-140">藉由將所有行為放到服務物件 (商務層) 中，基本上會得到[麵條式程式碼](https://en.wikipedia.org/wiki/Spaghetti_code)或[交易指令碼](https://martinfowler.com/eaaCatalog/transactionScript.html)，因此會失去領域模型所提供的優點。</span><span class="sxs-lookup"><span data-stu-id="44709-140">By putting all the behavior out into service objects (the business layer) you essentially end up with [spaghetti code](https://en.wikipedia.org/wiki/Spaghetti_code) or [transaction scripts](https://martinfowler.com/eaaCatalog/transactionScript.html), and therefore you lose the advantages that a domain model provides.</span></span>

<span data-ttu-id="44709-141">即便如此，如果您的微服務或限定內容很簡單 (CRUD 服務)，只有資料屬性之實體物件形式的 Anemic 領域模型便已足夠，而且可能不值得實作更複雜的 DDD 模式。</span><span class="sxs-lookup"><span data-stu-id="44709-141">Regardless, if your microservice or Bounded Context is very simple (a CRUD service), the anemic domain model in the form of entity objects with just data properties might be good enough, and it might not be worth implementing more complex DDD patterns.</span></span> <span data-ttu-id="44709-142">在此情況下，它只是持續性模型，因為您刻意建立只有 CRUD 用途資料的實體。</span><span class="sxs-lookup"><span data-stu-id="44709-142">In that case, it will be simply a persistence model, because you have intentionally created an entity with only data for CRUD purposes.</span></span>

<span data-ttu-id="44709-143">這就是為什麼微服務架構對於根據每個限定內容之多架構方法很理想的原因。</span><span class="sxs-lookup"><span data-stu-id="44709-143">That is why microservices architectures are perfect for a multi-architectural approach depending on each Bounded Context.</span></span> <span data-ttu-id="44709-144">例如，在 eShopOnContainers 中，訂購微服務會實作 DDD 模式，但目錄微服務是簡易 CRUD 服務，因此不會實作此模式。</span><span class="sxs-lookup"><span data-stu-id="44709-144">For instance, in eShopOnContainers, the ordering microservice implements DDD patterns, but the catalog microservice, which is a simple CRUD service, does not.</span></span>

<span data-ttu-id="44709-145">有些人認為 Anemic 領域模型是反模式。</span><span class="sxs-lookup"><span data-stu-id="44709-145">Some people say that the anemic domain model is an anti-pattern.</span></span> <span data-ttu-id="44709-146">它其實取決於您實作的內容。</span><span class="sxs-lookup"><span data-stu-id="44709-146">It really depends on what you are implementing.</span></span> <span data-ttu-id="44709-147">如果您要建立的微服務夠簡單 (例如 CRUD 服務)，遵循 Anemic 領域模型就不是反模式。</span><span class="sxs-lookup"><span data-stu-id="44709-147">If the microservice you are creating is simple enough (for example, a CRUD service), following the anemic domain model it is not an anti-pattern.</span></span> <span data-ttu-id="44709-148">不過，如果您需要處理的微服務領域因具有大量不斷改變的商務規則而很複雜，Anemic 領域模型可能是該微服務或限定內容的反模式。</span><span class="sxs-lookup"><span data-stu-id="44709-148">However, if you need to tackle the complexity of a microservice’s domain that has a lot of ever-changing business rules, the anemic domain model might be an anti-pattern for that microservice or Bounded Context.</span></span> <span data-ttu-id="44709-149">在此情況下，將它設計為具有實體的豐富模型可能會相當有利於這類微服務的長期成功，因為這些實體包含資料加上行為，並實作額外的 DDD 模式 (彙總、值物件等)。</span><span class="sxs-lookup"><span data-stu-id="44709-149">In that case, designing it as a rich model with entities containing data plus behavior as well as implementing additional DDD patterns (aggregates, value objects, etc.) might have huge benefits for the long-term success of such a microservice.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="44709-150">其他資源</span><span class="sxs-lookup"><span data-stu-id="44709-150">Additional resources</span></span>

-   <span data-ttu-id="44709-151">**DevIQ。Domain Entity (網域實體)**
    [*http://deviq.com/entity/*](http://deviq.com/entity/)</span><span class="sxs-lookup"><span data-stu-id="44709-151">**DevIQ. Domain Entity**
[*http://deviq.com/entity/*](http://deviq.com/entity/)</span></span>

-   <span data-ttu-id="44709-152">**Martin Fowler：The Domain Model (網域模型)**
    [*https://martinfowler.com/eaaCatalog/domainModel.html*](https://martinfowler.com/eaaCatalog/domainModel.html)</span><span class="sxs-lookup"><span data-stu-id="44709-152">**Martin Fowler. The Domain Model**
[*https://martinfowler.com/eaaCatalog/domainModel.html*](https://martinfowler.com/eaaCatalog/domainModel.html)</span></span>

-   <span data-ttu-id="44709-153">**Martin Fowler：The Anemic Domain Model (Anemic 領域模型)**</span><span class="sxs-lookup"><span data-stu-id="44709-153">**Martin Fowler. The Anemic Domain Model**</span></span>

    <https://martinfowler.com/bliki/AnemicDomainModel.html>

### <a name="the-value-object-pattern"></a><span data-ttu-id="44709-154">值物件模式</span><span class="sxs-lookup"><span data-stu-id="44709-154">The Value Object pattern</span></span>

<span data-ttu-id="44709-155">Eric Evans 提到，「許多物件沒有概念性身分識別。</span><span class="sxs-lookup"><span data-stu-id="44709-155">As Eric Evans has noted, “Many objects do not have conceptual identity.</span></span> <span data-ttu-id="44709-156">這些物件會描述事件的某些特性。」</span><span class="sxs-lookup"><span data-stu-id="44709-156">These objects describe certain characteristics of a thing.”</span></span>

<span data-ttu-id="44709-157">實體需要身分識別，但系統中有許多物件則不需要，例如值物件模式。</span><span class="sxs-lookup"><span data-stu-id="44709-157">An entity requires an identity, but there are many objects in a system that do not, like the Value Object pattern.</span></span> <span data-ttu-id="44709-158">值物件是描述領域層面之不具概念性身分識別的物件。</span><span class="sxs-lookup"><span data-stu-id="44709-158">A value object is an object with no conceptual identity that describes a domain aspect.</span></span> <span data-ttu-id="44709-159">這些是您具現化來表示只與您暫時有關之設計元素的物件。</span><span class="sxs-lookup"><span data-stu-id="44709-159">These are objects that you instantiate to represent design elements that only concern you temporarily.</span></span> <span data-ttu-id="44709-160">您關心這些物件的「本質」，而不是它們的「身分」。</span><span class="sxs-lookup"><span data-stu-id="44709-160">You care about *what* they are, not *who* they are.</span></span> <span data-ttu-id="44709-161">範例包含數字和字串，但也可能是更高階的概念，例如屬性群組。</span><span class="sxs-lookup"><span data-stu-id="44709-161">Examples include numbers and strings, but can also be higher-level concepts like groups of attributes.</span></span>

<span data-ttu-id="44709-162">微服務中的實體不一定會是另一個微服務中的實體，因為在後者中，限定內容可能代表不同的意思。</span><span class="sxs-lookup"><span data-stu-id="44709-162">Something that is an entity in a microservice might not be an entity in another microservice, because in the second case, the Bounded Context might have a different meaning.</span></span> <span data-ttu-id="44709-163">例如，電子商務應用程式中的地址可能完全沒有身分識別，因為它可能只代表個人或公司客戶設定檔的屬性群組。</span><span class="sxs-lookup"><span data-stu-id="44709-163">For example, an address in an e-commerce application might not have an identity at all, since it might only represent a group of attributes of the customer’s profile for a person or company.</span></span> <span data-ttu-id="44709-164">在此情況下，該地址應該會分類為值物件。</span><span class="sxs-lookup"><span data-stu-id="44709-164">In this case, the address should be classified as a value object.</span></span> <span data-ttu-id="44709-165">不過，在電力公用事業公司的應用程式中，客戶地址對公司領域可能很重要。</span><span class="sxs-lookup"><span data-stu-id="44709-165">However, in an application for an electric power utility company, the customer address could be important for the business domain.</span></span> <span data-ttu-id="44709-166">因此，地址必須含有身分識別，帳務系統才能直接連結至該地址。</span><span class="sxs-lookup"><span data-stu-id="44709-166">Therefore, the address must have an identity so the billing system can be directly linked to the address.</span></span> <span data-ttu-id="44709-167">在此情況下，地址應該會分類為領域實體。</span><span class="sxs-lookup"><span data-stu-id="44709-167">In that case, an address should be classified as a domain entity.</span></span>

<span data-ttu-id="44709-168">具有名字和姓氏的一個人通常是一個實體，因為這個人具有身分識別，即使名字和姓氏與另一組值相同亦然，例如若這些姓名同時指向不同的人。</span><span class="sxs-lookup"><span data-stu-id="44709-168">A person with a name and surname is usually an entity because a person has identity, even if the name and surname coincide with another set of values, such as if those names also refers to a different person.</span></span>

<span data-ttu-id="44709-169">值物件在關聯式資料庫和 EF 等 ORM 中很難管理，但在文件導向資料庫中則更容易實作和使用。</span><span class="sxs-lookup"><span data-stu-id="44709-169">Value objects are hard to manage in relational databases and ORMs like EF, whereas in document oriented databases they are easier to implement and use.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="44709-170">其他資源</span><span class="sxs-lookup"><span data-stu-id="44709-170">Additional resources</span></span>

-   <span data-ttu-id="44709-171">**Martin Fowler：Value Object pattern (值物件模式)**
    [*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)</span><span class="sxs-lookup"><span data-stu-id="44709-171">**Martin Fowler. Value Object pattern**
[*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)</span></span>

-   <span data-ttu-id="44709-172">**Value Object (值物件)**
    [*http://deviq.com/value-object/*](http://deviq.com/value-object/)</span><span class="sxs-lookup"><span data-stu-id="44709-172">**Value Object**
[*http://deviq.com/value-object/*](http://deviq.com/value-object/)</span></span>

-   <span data-ttu-id="44709-173">**Value Objects in Test-Driven Development (測試導向開發中的值物件)**
    [*https://leanpub.com/tdd-ebook/read\#leanpub-auto-value-objects*](https://leanpub.com/tdd-ebook/read#leanpub-auto-value-objects)</span><span class="sxs-lookup"><span data-stu-id="44709-173">**Value Objects in Test-Driven Development**
[*https://leanpub.com/tdd-ebook/read\#leanpub-auto-value-objects*](https://leanpub.com/tdd-ebook/read#leanpub-auto-value-objects)</span></span>

-   <span data-ttu-id="44709-174">**Eric Evans：Domain-Driven Design: Tackling Complexity in the Heart of Software.**</span><span class="sxs-lookup"><span data-stu-id="44709-174">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software.**</span></span> <span data-ttu-id="44709-175">(書籍；包括值物件的探討) [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span><span class="sxs-lookup"><span data-stu-id="44709-175">(Book; includes a discussion of value objects) [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span></span>

### <a name="the-aggregate-pattern"></a><span data-ttu-id="44709-176">彙總模式</span><span class="sxs-lookup"><span data-stu-id="44709-176">The Aggregate pattern</span></span>

<span data-ttu-id="44709-177">領域模型包含不同資料實體和處理序的叢集，可控制重要功能區域，例如訂單完成或庫存。</span><span class="sxs-lookup"><span data-stu-id="44709-177">A domain model contains clusters of different data entities and processes that can control a significant area of functionality, such as order fulfilment or inventory.</span></span> <span data-ttu-id="44709-178">更精細的 DDD 單位是彙總，其描述可視為內聚單位之實體和行為的叢集或群組。</span><span class="sxs-lookup"><span data-stu-id="44709-178">A more fine-grained DDD unit is the aggregate, which describes a cluster or group of entities and behaviors that can be treated as a cohesive unit.</span></span>

<span data-ttu-id="44709-179">您通常會根據所需的交易來定義彙總。</span><span class="sxs-lookup"><span data-stu-id="44709-179">You usually define an aggregate based on the transactions that you need.</span></span> <span data-ttu-id="44709-180">典型的範例是同時包含訂單項目清單的訂單。</span><span class="sxs-lookup"><span data-stu-id="44709-180">A classic example is an order that also contains a list of order items.</span></span> <span data-ttu-id="44709-181">訂單項目通常會是實體。</span><span class="sxs-lookup"><span data-stu-id="44709-181">An order item will usually be an entity.</span></span> <span data-ttu-id="44709-182">但它會是訂單彙總內的子實體，這也會包含訂單實體作為其根實體，通常稱為彙總根。</span><span class="sxs-lookup"><span data-stu-id="44709-182">But it will be a child entity within the order aggregate, which will also contain the order entity as its root entity, typically called an aggregate root.</span></span>

<span data-ttu-id="44709-183">識別彙總可能很難。</span><span class="sxs-lookup"><span data-stu-id="44709-183">Identifying aggregates can be hard.</span></span> <span data-ttu-id="44709-184">彙總是一組必須同時一致的物件群組，但您不可以只挑選一組物件並將它們加上彙總標籤。</span><span class="sxs-lookup"><span data-stu-id="44709-184">An aggregate is a group of objects that must be consistent together, but you cannot just pick a group of objects and label them an aggregate.</span></span> <span data-ttu-id="44709-185">您必須從領域概念開始，並考慮在與該概念相關的最常見交易中使用的實體。</span><span class="sxs-lookup"><span data-stu-id="44709-185">You must start with a domain concept and think about the entities that are used in the most common transactions related to that concept.</span></span> <span data-ttu-id="44709-186">這些需要交易一致的實體會形成彙總。</span><span class="sxs-lookup"><span data-stu-id="44709-186">Those entities that need to be transactionally consistent are what forms an aggregate.</span></span> <span data-ttu-id="44709-187">考慮交易作業可能是識別彙總的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="44709-187">Thinking about transaction operations is probably the best way to identify aggregates.</span></span>

### <a name="the-aggregate-root-or-root-entity-pattern"></a><span data-ttu-id="44709-188">彙總根或根實體模式</span><span class="sxs-lookup"><span data-stu-id="44709-188">The Aggregate Root or Root Entity pattern</span></span>

<span data-ttu-id="44709-189">彙總至少是由一個實體所組成，那就是彙總根，也稱為根實體或主要實體。</span><span class="sxs-lookup"><span data-stu-id="44709-189">An aggregate is composed of at least one entity: the aggregate root, also called root entity or primary entity.</span></span> <span data-ttu-id="44709-190">此外，它可以有多個子實體和值物件，所有實體和物件會共同實作必要的行為和交易。</span><span class="sxs-lookup"><span data-stu-id="44709-190">Additionally, it can have multiple child entities and value objects, with all entities and objects working together to implement required behavior and transactions.</span></span>

<span data-ttu-id="44709-191">彙總根的目的是確保彙總的一致性，它應該是透過彙總根類別中的方法或作業對彙總進行更新的唯一進入點。</span><span class="sxs-lookup"><span data-stu-id="44709-191">The purpose of an aggregate root is to ensure the consistency of the aggregate; it should be the only entry point for updates to the aggregate through methods or operations in the aggregate root class.</span></span> <span data-ttu-id="44709-192">您只能透過彙總根變更彙總內的實體。</span><span class="sxs-lookup"><span data-stu-id="44709-192">You should make changes to entities within the aggregate only via the aggregate root.</span></span> <span data-ttu-id="44709-193">它可確保彙總的一致性，並考慮到您可能需要在彙總中遵守的所有不定式和一致性規則。</span><span class="sxs-lookup"><span data-stu-id="44709-193">It is the aggregate’s consistency guardian, taking into account all the invariants and consistency rules you might need to comply with in your aggregate.</span></span> <span data-ttu-id="44709-194">如果您獨立變更子實體或值物件，彙總根無法確保彙總處於有效狀態。</span><span class="sxs-lookup"><span data-stu-id="44709-194">If you change a child entity or value object independently, the aggregate root cannot ensure that the aggregate is in a valid state.</span></span> <span data-ttu-id="44709-195">就像是桌子鬆了桌腳一樣。</span><span class="sxs-lookup"><span data-stu-id="44709-195">It would be like a table with a loose leg.</span></span> <span data-ttu-id="44709-196">維護一致性是彙總根的主要目的。</span><span class="sxs-lookup"><span data-stu-id="44709-196">Maintaining consistency is the main purpose of the aggregate root.</span></span>

<span data-ttu-id="44709-197">在圖 9-9 中，您會看到購買者彙總之類的範例彙總，其中包含單一實體 (彙總根購買者)。</span><span class="sxs-lookup"><span data-stu-id="44709-197">In Figure 9-9, you can see sample aggregates like the buyer aggregate, which contains a single entity (the aggregate root Buyer).</span></span> <span data-ttu-id="44709-198">訂單彙總包含多個實體和值物件。</span><span class="sxs-lookup"><span data-stu-id="44709-198">The order aggregate contains multiple entities and a value object.</span></span>

![](./media/image10.png)

<span data-ttu-id="44709-199">**圖 9-9**：</span><span class="sxs-lookup"><span data-stu-id="44709-199">**Figure 9-9**.</span></span> <span data-ttu-id="44709-200">具有多個或單一實體的彙總範例</span><span class="sxs-lookup"><span data-stu-id="44709-200">Example of aggregates with multiple or single entities</span></span>

<span data-ttu-id="44709-201">請注意，視您的領域而定，購買者彙總可能會有其他子實體，就像是在 eShopOnContainers 參考應用程式中的訂購微服務一樣。</span><span class="sxs-lookup"><span data-stu-id="44709-201">Note that the Buyer aggregate could have additional child entities, depending on your domain, as it does in the ordering microservice in the eShopOnContainers reference application.</span></span> <span data-ttu-id="44709-202">圖 9 9 只會描述購買者具有單一實體的情況，例如只包含彙總根的彙總。</span><span class="sxs-lookup"><span data-stu-id="44709-202">Figure 9-9 just illustrates a case in which the buyer has a single entity, as an example of an aggregate that contains only an aggregate root.</span></span>

<span data-ttu-id="44709-203">若要維持彙總分離並保持彙總之間的清楚界限，建議在 DDD 領域模型中，不要允許在彙總之間直接瀏覽，而只具有外部索引鍵 (FK) 欄位，如 eShopOnContainers 的[訂購微服務領域模型](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs)中所實作。</span><span class="sxs-lookup"><span data-stu-id="44709-203">In order to maintain separation of aggregates and keep clear boundaries between them, it is a good practice in a DDD domain model to disallow direct navigation between aggregates and only having the foreign key (FK) field, as implemented in the [Ordering microservice domain model](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs) in eShopOnContainers.</span></span> <span data-ttu-id="44709-204">訂單實體只具有購買者的 FK 欄位，但不具有 EF Core 瀏覽屬性，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="44709-204">The Order entity only has a FK field for the buyer, but not an EF Core navigation property, as shown in the following code:</span></span>

```csharp
public class Order : Entity, IAggregateRoot
{
    private DateTime _orderDate;
    public Address Address { get; private set; }
    private int? _buyerId; //FK pointing to a different aggregate root
    public OrderStatus OrderStatus { get; private set; }
    private readonly List<OrderItem> _orderItems;
    public IReadOnlyCollection<OrderItem> OrderItems => _orderItems;
    // ... Additional code
}
```

<span data-ttu-id="44709-205">識別及使用彙總需要研究和經驗。</span><span class="sxs-lookup"><span data-stu-id="44709-205">Identifying and working with aggregates requires research and experience.</span></span> <span data-ttu-id="44709-206">如需詳細資訊，請參閱下列＜其他資源＞清單。</span><span class="sxs-lookup"><span data-stu-id="44709-206">For more information, see the following Additional resources list.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="44709-207">其他資源</span><span class="sxs-lookup"><span data-stu-id="44709-207">Additional resources</span></span>

-   <span data-ttu-id="44709-208">**Vaughn Vernon：Effective Aggregate Design - Part I: Modeling a Single Aggregate (有效彙總設計 - 第一部分：建立單一彙總模型)**
    [*https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD\_COMMUNITY\_ESSAY\_AGGREGATES\_PART\_1.pdf*](https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_1.pdf)</span><span class="sxs-lookup"><span data-stu-id="44709-208">**Vaughn Vernon. Effective Aggregate Design - Part I: Modeling a Single Aggregate**
[*https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD\_COMMUNITY\_ESSAY\_AGGREGATES\_PART\_1.pdf*](https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_1.pdf)</span></span>

-   <span data-ttu-id="44709-209">**Vaughn Vernon：Effective Aggregate Design - Part II: Making Aggregates Work Together (有效彙總設計 - 第二部分：使彙總共同作業)**
    *<https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_2.pdf> *</span><span class="sxs-lookup"><span data-stu-id="44709-209">**Vaughn Vernon. Effective Aggregate Design - Part II: Making Aggregates Work Together**
*<https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_2.pdf> *</span></span>

-   <span data-ttu-id="44709-210">**Vaughn Vernon：Effective Aggregate Design - Part III: Gaining Insight Through Discovery (有效彙總設計 - 第三部分：透過探索取得深入解析)**
    *<https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_3.pdf> *</span><span class="sxs-lookup"><span data-stu-id="44709-210">**Vaughn Vernon. Effective Aggregate Design - Part III: Gaining Insight Through Discovery**
*<https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_3.pdf> *</span></span>

-   <span data-ttu-id="44709-211">**Sergey Grybniak：DDD Tactical Design Patterns (DDD 戰術設計模式)**
    [*https://www.codeproject.com/Articles/1164363/Domain-Driven-Design-Tactical-Design-Patterns-Part*](https://www.codeproject.com/Articles/1164363/Domain-Driven-Design-Tactical-Design-Patterns-Part)</span><span class="sxs-lookup"><span data-stu-id="44709-211">**Sergey Grybniak. DDD Tactical Design Patterns**
[*https://www.codeproject.com/Articles/1164363/Domain-Driven-Design-Tactical-Design-Patterns-Part*](https://www.codeproject.com/Articles/1164363/Domain-Driven-Design-Tactical-Design-Patterns-Part)</span></span>

-   <span data-ttu-id="44709-212">**Chris Richardson：Developing Transactional Microservices Using Aggregates (使用彙總開發交易微服務)**
    [*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-1-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-1-richardson)</span><span class="sxs-lookup"><span data-stu-id="44709-212">**Chris Richardson. Developing Transactional Microservices Using Aggregates**
[*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-1-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-1-richardson)</span></span>

-   <span data-ttu-id="44709-213">**DevIQ。The Aggregate pattern (彙總模式)**
    [*http://deviq.com/aggregate-pattern/*](http://deviq.com/aggregate-pattern/)</span><span class="sxs-lookup"><span data-stu-id="44709-213">**DevIQ. The Aggregate pattern**
[*http://deviq.com/aggregate-pattern/*](http://deviq.com/aggregate-pattern/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="44709-214">[上一頁](ddd-oriented-microservice.md)
[下一頁](net-core-microservice-domain-model.md)</span><span class="sxs-lookup"><span data-stu-id="44709-214">[Previous](ddd-oriented-microservice.md)
[Next](net-core-microservice-domain-model.md)</span></span>
