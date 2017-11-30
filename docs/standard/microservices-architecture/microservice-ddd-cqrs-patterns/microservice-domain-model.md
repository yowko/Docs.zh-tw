---
title: "設計的微服務網域模型"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |設計的微服務網域模型"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 455a2c5a39fb9b765b557610ab108f8c75882dbd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="designing-a-microservice-domain-model"></a><span data-ttu-id="406e4-104">設計的微服務網域模型</span><span class="sxs-lookup"><span data-stu-id="406e4-104">Designing a microservice domain model</span></span>

<span data-ttu-id="406e4-105">*定義一個豐富的網域模型，針對每個商務微服務 」 或 「 繫結的內容*</span><span class="sxs-lookup"><span data-stu-id="406e4-105">*Define one rich domain model for each business microservice or Bounded Context*</span></span>

<span data-ttu-id="406e4-106">您的目標是建立單一的一致網域模型，針對每個商務微服務 」 或 「 繫結的內容 (BC)。</span><span class="sxs-lookup"><span data-stu-id="406e4-106">Your goal is to create a single cohesive domain model for each business microservice or Bounded Context (BC).</span></span> <span data-ttu-id="406e4-107">記住，不過，BC 或商務微服務有時無法組成數個共用單一網域模型的實體服務。</span><span class="sxs-lookup"><span data-stu-id="406e4-107">Keep in mind, however, that a BC or business microservice could sometimes be composed of several physical services that share a single domain model.</span></span> <span data-ttu-id="406e4-108">網域模型必須擷取規則、 行為、 商務語言和單一繫結的內容或它所代表的商務微服務的條件約束。</span><span class="sxs-lookup"><span data-stu-id="406e4-108">The domain model must capture the rules, behavior, business language, and constraints of the single Bounded Context or business microservice that it represents.</span></span>

## <a name="the-domain-entity-pattern"></a><span data-ttu-id="406e4-109">網域實體模式</span><span class="sxs-lookup"><span data-stu-id="406e4-109">The Domain Entity pattern</span></span>

<span data-ttu-id="406e4-110">實體代表網域物件，並由其身分識別、 提供續航力和經過一段時間，持續性並不只是由包含這些屬性主要是定義。</span><span class="sxs-lookup"><span data-stu-id="406e4-110">Entities represent domain objects and are primarily defined by their identity, continuity, and persistence over time, and not only by the attributes that comprise them.</span></span> <span data-ttu-id="406e4-111">因為 Eric Evans 說，「 主要定義其識別的物件被呼叫實體 」。</span><span class="sxs-lookup"><span data-stu-id="406e4-111">As Eric Evans says, “an object primarily defined by its identity is called an Entity.”</span></span> <span data-ttu-id="406e4-112">實體是在網域模型中，非常重要，因為它是以模型的基底。</span><span class="sxs-lookup"><span data-stu-id="406e4-112">Entities are very important in the domain model, since they are the base for a model.</span></span> <span data-ttu-id="406e4-113">因此，您應該識別和它們仔細的設計。</span><span class="sxs-lookup"><span data-stu-id="406e4-113">Therefore, you should identify and design them carefully.</span></span>

<span data-ttu-id="406e4-114">*實體的識別身分都不得跨越多個 microservices 或繫結的內容。*</span><span class="sxs-lookup"><span data-stu-id="406e4-114">*An entity’s identity can cross multiple microservices or Bounded Contexts.*</span></span>

<span data-ttu-id="406e4-115">在相同識別 （但不相同的實體） 可以跨多個繫結的內容或 microservices 建立模型。</span><span class="sxs-lookup"><span data-stu-id="406e4-115">The same identity (though not the same entity) can be modeled across multiple Bounded Contexts or microservices.</span></span> <span data-ttu-id="406e4-116">不過，並不意味著，在多個繫結的內容中實作相同的實體，具有相同的屬性和邏輯。</span><span class="sxs-lookup"><span data-stu-id="406e4-116">However, that does not imply that the same entity, with the same attributes and logic would be implemented in multiple Bounded Contexts.</span></span> <span data-ttu-id="406e4-117">相反地，每個繫結的內容中的實體限制其屬性和行為，以必要的繫結內容的網域中。</span><span class="sxs-lookup"><span data-stu-id="406e4-117">Instead, entities in each Bounded Context limit their attributes and behaviors to those required in that Bounded Context’s domain.</span></span>

<span data-ttu-id="406e4-118">比方說，買方實體可能會有大部分的設定檔或識別微服務，包括身分識別的使用者實體中定義的個人的屬性。</span><span class="sxs-lookup"><span data-stu-id="406e4-118">For instance, the buyer entity might have most of a person’s attributes that are defined in the user entity in the profile or identity microservice, including the identity.</span></span> <span data-ttu-id="406e4-119">但是，買方中的實體順序的微服務可能具有較少的屬性，只有特定買方資料與訂單程序。</span><span class="sxs-lookup"><span data-stu-id="406e4-119">But the buyer entity in the ordering microservice might have fewer attributes, because only certain buyer data is related to the order process.</span></span> <span data-ttu-id="406e4-120">每個微服務的內容或繫結的內容會影響其網域模型。</span><span class="sxs-lookup"><span data-stu-id="406e4-120">The context of each microservice or Bounded Context impacts its domain model.</span></span>

<span data-ttu-id="406e4-121">*網域實體必須實作除了實作資料屬性的行為*</span><span class="sxs-lookup"><span data-stu-id="406e4-121">*Domain entities must implement behavior in addition to implementing data attributes*</span></span>

<span data-ttu-id="406e4-122">網域中的實體 DDD 必須實作網域邏輯或實體資料 （在記憶體中存取的物件） 的相關行為。</span><span class="sxs-lookup"><span data-stu-id="406e4-122">A domain entity in DDD must implement the domain logic or behavior related to the entity data (the object accessed in memory).</span></span> <span data-ttu-id="406e4-123">例如，order 實體類別的一部分必須商務邏輯和實作為工作，例如新增訂單項目、 資料驗證及總計算的方法的作業。</span><span class="sxs-lookup"><span data-stu-id="406e4-123">For example, as part of an order entity class you must have business logic and operations implemented as methods for tasks such as adding an order item, data validation, and total calculation.</span></span> <span data-ttu-id="406e4-124">實體的方法負責的非變異值和規則的實體，而不需要這些分散應用程式層的規則。</span><span class="sxs-lookup"><span data-stu-id="406e4-124">The entity’s methods take care of the invariants and rules of the entity instead of having those rules spread across the application layer.</span></span>

<span data-ttu-id="406e4-125">圖 9-8 顯示實作不僅資料屬性，但作業或方法相關的網域邏輯使用網域實體。</span><span class="sxs-lookup"><span data-stu-id="406e4-125">Figure 9-8 shows a domain entity that implements not only data attributes but operations or methods with related domain logic.</span></span>

![](./media/image9.png)

<span data-ttu-id="406e4-126">**圖 9-8**。</span><span class="sxs-lookup"><span data-stu-id="406e4-126">**Figure 9-8**.</span></span> <span data-ttu-id="406e4-127">實作資料加上行為網域實體設計的範例</span><span class="sxs-lookup"><span data-stu-id="406e4-127">Example of a domain entity design implementing data plus behavior</span></span>

<span data-ttu-id="406e4-128">當然，有時您可以有不會為實體類別的一部分實作的任何邏輯實體。</span><span class="sxs-lookup"><span data-stu-id="406e4-128">Of course, sometimes you can have entities that do not implement any logic as part of the entity class.</span></span> <span data-ttu-id="406e4-129">這種情況中彙總內的子實體子實體沒有任何特殊邏輯，因為大部分的邏輯定義彙總的根目錄中。</span><span class="sxs-lookup"><span data-stu-id="406e4-129">This can happen in child entities within an aggregate if the child entity does not have any special logic because most of the logic is defined in the aggregate root.</span></span> <span data-ttu-id="406e4-130">如果您有複雜的微服務具有大量網域實體中而不是服務類別中實作的邏輯，您無法落入 anemic 網域模型下, 一節所述。</span><span class="sxs-lookup"><span data-stu-id="406e4-130">If you have a complex microservice that has a lot of logic implemented in the service classes instead of in the domain entities, you could be falling into the anemic domain model, explained in the following section.</span></span>

### <a name="rich-domain-model-versus-anemic-domain-model"></a><span data-ttu-id="406e4-131">與 anemic 網域模型的豐富網域模型</span><span class="sxs-lookup"><span data-stu-id="406e4-131">Rich domain model versus anemic domain model</span></span>

<span data-ttu-id="406e4-132">他的文章中[AnemicDomainModel](https://martinfowler.com/bliki/AnemicDomainModel.html)，Martin Fowler 描述 anemic 網域模型這種方式：</span><span class="sxs-lookup"><span data-stu-id="406e4-132">In his post [AnemicDomainModel](https://martinfowler.com/bliki/AnemicDomainModel.html), Martin Fowler describes an anemic domain model this way:</span></span>

<span data-ttu-id="406e4-133">Anemic 網域模型的基本徵兆是乍看之下它看起來像真正的動作。</span><span class="sxs-lookup"><span data-stu-id="406e4-133">The basic symptom of an Anemic Domain Model is that at first blush it looks like the real thing.</span></span> <span data-ttu-id="406e4-134">沒有物件、 許多為名網域空間中的名詞和這些物件來連接具有豐富的關聯性，則為 true 的網域模型具有的結構。</span><span class="sxs-lookup"><span data-stu-id="406e4-134">There are objects, many named after the nouns in the domain space, and these objects are connected with the rich relationships and structure that true domain models have.</span></span> <span data-ttu-id="406e4-135">捕捉來自您查看行為，和您了解這些物件上沒有任何難以行為使其稍微超過的 getter 和 setter 包時。</span><span class="sxs-lookup"><span data-stu-id="406e4-135">The catch comes when you look at the behavior, and you realize that there is hardly any behavior on these objects, making them little more than bags of getters and setters.</span></span>

<span data-ttu-id="406e4-136">當然，當您使用 anemic 網域模型，這些資料模型中要使用的一組服務物件 (傳統上具名*： 商務圖層*) 這會擷取所有的網域或商務邏輯。</span><span class="sxs-lookup"><span data-stu-id="406e4-136">Of course, when you use an anemic domain model, those data models will be used from a set of service objects (traditionally named the *business layer*) which capture all the domain or business logic.</span></span> <span data-ttu-id="406e4-137">商業層位於資料模型之上，並使用只做為資料的資料模型。</span><span class="sxs-lookup"><span data-stu-id="406e4-137">The business layer sits on top of the data model and uses the data model just as data.</span></span>

<span data-ttu-id="406e4-138">Anemic 網域模型是只程序樣式設計。</span><span class="sxs-lookup"><span data-stu-id="406e4-138">The anemic domain model is just a procedural style design.</span></span> <span data-ttu-id="406e4-139">Anemic 實體物件不是真正的物件，因為它們缺少行為 （方法）。</span><span class="sxs-lookup"><span data-stu-id="406e4-139">Anemic entity objects are not real objects because they lack behavior (methods).</span></span> <span data-ttu-id="406e4-140">它們只會保存資料的屬性，因此它不是物件導向設計。</span><span class="sxs-lookup"><span data-stu-id="406e4-140">They only hold data properties and thus it is not object-oriented design.</span></span> <span data-ttu-id="406e4-141">透過將所有的行為出服務物件 （商務層） 放入您基本上得到[之程式碼](https://en.wikipedia.org/wiki/Spaghetti_code)或[交易指令碼](https://martinfowler.com/eaaCatalog/transactionScript.html)，因此您遺失優點，並網域模型提供。</span><span class="sxs-lookup"><span data-stu-id="406e4-141">By putting all the behavior out into service objects (the business layer) you essentially end up with [spaghetti code](https://en.wikipedia.org/wiki/Spaghetti_code) or [transaction scripts](https://martinfowler.com/eaaCatalog/transactionScript.html), and therefore you lose the advantages that a domain model provides.</span></span>

<span data-ttu-id="406e4-142">不論，如果您的微服務或繫結的內容是非常簡單 （服務 CRUD） anemic 網域中的模型只是資料屬性與實體物件的形式可能夠好，而且可能無法值得實作更複雜的 DDD 模式。</span><span class="sxs-lookup"><span data-stu-id="406e4-142">Regardless, if your microservice or Bounded Context is very simple (a CRUD service), the anemic domain model in the form of entity objects with just data properties might be good enough, and it might not be worth implementing more complex DDD patterns.</span></span> <span data-ttu-id="406e4-143">在此情況下，這是簡單的持續性模式，因為您只使用資料基於 CRUD 刻意建立實體。</span><span class="sxs-lookup"><span data-stu-id="406e4-143">In that case, it will be simply a persistence model, because you have intentionally created an entity with only data for CRUD purposes.</span></span>

<span data-ttu-id="406e4-144">這是為什麼 microservices 架構是完美的多重架構的方法，根據每個繫結的內容。</span><span class="sxs-lookup"><span data-stu-id="406e4-144">That is why microservices architectures are perfect for a multi-architectural approach depending on each Bounded Context.</span></span> <span data-ttu-id="406e4-145">比方說，在 eShopOnContainers，排序的微服務實作 DDD 模式，但目錄微服務，這是一個簡單的 CRUD 服務，並不會。</span><span class="sxs-lookup"><span data-stu-id="406e4-145">For instance, in eShopOnContainers, the ordering microservice implements DDD patterns, but the catalog microservice, which is a simple CRUD service, does not.</span></span>

<span data-ttu-id="406e4-146">有些人說出 anemic 網域模型是反向的模式。</span><span class="sxs-lookup"><span data-stu-id="406e4-146">Some people say that the anemic domain model is an anti-pattern.</span></span> <span data-ttu-id="406e4-147">它其實取決於您要實作。</span><span class="sxs-lookup"><span data-stu-id="406e4-147">It really depends on what you are implementing.</span></span> <span data-ttu-id="406e4-148">如果您要建立微服務是簡單足夠 （例如，CRUD 服務），下列 anemic 網域模型不是反向的模式。</span><span class="sxs-lookup"><span data-stu-id="406e4-148">If the microservice you are creating is simple enough (for example, a CRUD service), following the anemic domain model it is not an anti-pattern.</span></span> <span data-ttu-id="406e4-149">不過，如果您需要處理具有大量不斷改變的商務規則的微服務網域的複雜性，anemic 網域模型可能反面模式或繫結內容的微服務。</span><span class="sxs-lookup"><span data-stu-id="406e4-149">However, if you need to tackle the complexity of a microservice’s domain that has a lot of ever-changing business rules, the anemic domain model might be an anti-pattern for that microservice or Bounded Context.</span></span> <span data-ttu-id="406e4-150">在此情況下，將它設計為 rich 與實體，其中包含資料，以及行為，以及實作其他 DDD 模式 （彙總、 值的物件等） 的模型可能會有很大的優點，長期成功的微服務。</span><span class="sxs-lookup"><span data-stu-id="406e4-150">In that case, designing it as a rich model with entities containing data plus behavior as well as implementing additional DDD patterns (aggregates, value objects, etc.) might have huge benefits for the long-term success of such a microservice.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="406e4-151">其他資源</span><span class="sxs-lookup"><span data-stu-id="406e4-151">Additional resources</span></span>

-   <span data-ttu-id="406e4-152">**DevIQ。網域實體**
    [*http://deviq.com/entity/*](http://deviq.com/entity/)</span><span class="sxs-lookup"><span data-stu-id="406e4-152">**DevIQ. Domain Entity**
[*http://deviq.com/entity/*](http://deviq.com/entity/)</span></span>

-   <span data-ttu-id="406e4-153">**Martin Fowler：網域模型**
    [*https://martinfowler.com/eaaCatalog/domainModel.html*](https://martinfowler.com/eaaCatalog/domainModel.html)</span><span class="sxs-lookup"><span data-stu-id="406e4-153">**Martin Fowler. The Domain Model**
[*https://martinfowler.com/eaaCatalog/domainModel.html*](https://martinfowler.com/eaaCatalog/domainModel.html)</span></span>

-   <span data-ttu-id="406e4-154">**Martin Fowler：Anemic 網域模型**</span><span class="sxs-lookup"><span data-stu-id="406e4-154">**Martin Fowler. The Anemic Domain Model**</span></span>

    <span data-ttu-id="406e4-155"><https://martinfowler.com/bliki/AnemicDomainModel.html></span><span class="sxs-lookup"><span data-stu-id="406e4-155"><https://martinfowler.com/bliki/AnemicDomainModel.html></span></span>

### <a name="the-value-object-pattern"></a><span data-ttu-id="406e4-156">值物件模式</span><span class="sxs-lookup"><span data-stu-id="406e4-156">The Value Object pattern</span></span>

<span data-ttu-id="406e4-157">Eric Evans 已經提過，「 許多物件沒有概念的身分識別。</span><span class="sxs-lookup"><span data-stu-id="406e4-157">As Eric Evans has noted, “Many objects do not have conceptual identity.</span></span> <span data-ttu-id="406e4-158">這些物件描述特定特性的事。 」</span><span class="sxs-lookup"><span data-stu-id="406e4-158">These objects describe certain characteristics of a thing.”</span></span>

<span data-ttu-id="406e4-159">實體需要身分識別，但系統不會有許多物件類似的值物件的模式。</span><span class="sxs-lookup"><span data-stu-id="406e4-159">An entity requires an identity, but there are many objects in a system that do not, like the Value Object pattern.</span></span> <span data-ttu-id="406e4-160">值物件是具有任何描述網域外觀的概念身分識別的物件。</span><span class="sxs-lookup"><span data-stu-id="406e4-160">A value object is an object with no conceptual identity that describes a domain aspect.</span></span> <span data-ttu-id="406e4-161">這些是您具現化來表示只有您有關暫時的設計元素的物件。</span><span class="sxs-lookup"><span data-stu-id="406e4-161">These are objects that you instantiate to represent design elements that only concern you temporarily.</span></span> <span data-ttu-id="406e4-162">您很重視*什麼*它們，不是*人員*它們。</span><span class="sxs-lookup"><span data-stu-id="406e4-162">You care about *what* they are, not *who* they are.</span></span> <span data-ttu-id="406e4-163">範例包含數字和字串，但也可能是較高層級的概念，像是群組的屬性。</span><span class="sxs-lookup"><span data-stu-id="406e4-163">Examples include numbers and strings, but can also be higher-level concepts like groups of attributes.</span></span>

<span data-ttu-id="406e4-164">項目中的微服務的實體不可能是另一個的微服務中的實體，因為在第二個案例中，繫結的內容可能會有不同的意義。</span><span class="sxs-lookup"><span data-stu-id="406e4-164">Something that is an entity in a microservice might not be an entity in another microservice, because in the second case, the Bounded Context might have a different meaning.</span></span> <span data-ttu-id="406e4-165">例如，電子商務應用程式中的位址可能沒有身分識別，因為它可能只代表客戶的個人或公司的設定檔的屬性群組。</span><span class="sxs-lookup"><span data-stu-id="406e4-165">For example, an address in an e-commerce application might not have an identity at all, since it might only represent a group of attributes of the customer’s profile for a person or company.</span></span> <span data-ttu-id="406e4-166">在此情況下，地址應該會歸類為值物件。</span><span class="sxs-lookup"><span data-stu-id="406e4-166">In this case, the address should be classified as a value object.</span></span> <span data-ttu-id="406e4-167">不過，接上電源公用程式的公司應用程式中，可能是很重要的商務網域的客戶地址。</span><span class="sxs-lookup"><span data-stu-id="406e4-167">However, in an application for an electric power utility company, the customer address could be important for the business domain.</span></span> <span data-ttu-id="406e4-168">因此，位址必須含有身分識別，因此帳務系統可以直接連接到位址。</span><span class="sxs-lookup"><span data-stu-id="406e4-168">Therefore, the address must have an identity so the billing system can be directly linked to the address.</span></span> <span data-ttu-id="406e4-169">在此情況下，地址應該會分類為網域實體。</span><span class="sxs-lookup"><span data-stu-id="406e4-169">In that case, an address should be classified as a domain entity.</span></span>

<span data-ttu-id="406e4-170">具有名稱和姓氏的人員通常是一個實體，因為個人身分識別，即使另一組值與一致的名稱和姓氏，例如，如果這些名稱也是指不同的人。</span><span class="sxs-lookup"><span data-stu-id="406e4-170">A person with a name and surname is usually an entity because a person has identity, even if the name and surname coincide with another set of values, such as if those names also refers to a different person.</span></span>

<span data-ttu-id="406e4-171">值物件難以管理關聯式資料庫和 Orm 像 EF，而在文件導向容易實作，並使用的資料庫。</span><span class="sxs-lookup"><span data-stu-id="406e4-171">Value objects are hard to manage in relational databases and ORMs like EF, whereas in document oriented databases they are easier to implement and use.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="406e4-172">其他資源</span><span class="sxs-lookup"><span data-stu-id="406e4-172">Additional resources</span></span>

-   <span data-ttu-id="406e4-173">**Martin Fowler：值物件模式**
    [*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)</span><span class="sxs-lookup"><span data-stu-id="406e4-173">**Martin Fowler. Value Object pattern**
[*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)</span></span>

-   <span data-ttu-id="406e4-174">**值物件**
    [*http://deviq.com/value-object/*](http://deviq.com/value-object/)</span><span class="sxs-lookup"><span data-stu-id="406e4-174">**Value Object**
[*http://deviq.com/value-object/*](http://deviq.com/value-object/)</span></span>

-   <span data-ttu-id="406e4-175">**值物件中有如開發**
    [*https://leanpub.com/tdd-ebook/read\#leanpub 自動值的物件*](https://leanpub.com/tdd-ebook/read#leanpub-auto-value-objects)</span><span class="sxs-lookup"><span data-stu-id="406e4-175">**Value Objects in Test-Driven Development**
[*https://leanpub.com/tdd-ebook/read\#leanpub-auto-value-objects*](https://leanpub.com/tdd-ebook/read#leanpub-auto-value-objects)</span></span>

-   <span data-ttu-id="406e4-176">**Eric Evans：網域導向設計： 解決核心軟體的複雜度。**</span><span class="sxs-lookup"><span data-stu-id="406e4-176">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software.**</span></span> <span data-ttu-id="406e4-177">（書籍; 包含的值物件的討論）[ *https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span><span class="sxs-lookup"><span data-stu-id="406e4-177">(Book; includes a discussion of value objects) [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span></span>

### <a name="the-aggregate-pattern"></a><span data-ttu-id="406e4-178">彙總模式</span><span class="sxs-lookup"><span data-stu-id="406e4-178">The Aggregate pattern</span></span>

<span data-ttu-id="406e4-179">網域模型包含不同的資料實體與可控制重要區域的功能，例如順序完成或清查處理程序的叢集。</span><span class="sxs-lookup"><span data-stu-id="406e4-179">A domain model contains clusters of different data entities and processes that can control a significant area of functionality, such as order fulfilment or inventory.</span></span> <span data-ttu-id="406e4-180">更精細的 DDD 單位是彙總，其中描述叢集或群組的實體和行為可視為凝聚的單元。</span><span class="sxs-lookup"><span data-stu-id="406e4-180">A more fine-grained DDD unit is the aggregate, which describes a cluster or group of entities and behaviors that can be treated as a cohesive unit.</span></span>

<span data-ttu-id="406e4-181">您通常會定義您所需要的交易為基礎的彙總。</span><span class="sxs-lookup"><span data-stu-id="406e4-181">You usually define an aggregate based on the transactions that you need.</span></span> <span data-ttu-id="406e4-182">典型的範例是也包含一份訂單項目順序。</span><span class="sxs-lookup"><span data-stu-id="406e4-182">A classic example is an order that also contains a list of order items.</span></span> <span data-ttu-id="406e4-183">訂單項目通常會為實體。</span><span class="sxs-lookup"><span data-stu-id="406e4-183">An order item will usually be an entity.</span></span> <span data-ttu-id="406e4-184">但是會有子實體內的順序彙總，也會包含 「 訂單 」 實體為其根目錄的實體，通常稱為彙總的根。</span><span class="sxs-lookup"><span data-stu-id="406e4-184">But it will be a child entity within the order aggregate, which will also contain the order entity as its root entity, typically called an aggregate root.</span></span>

<span data-ttu-id="406e4-185">識別彙總很困難。</span><span class="sxs-lookup"><span data-stu-id="406e4-185">Identifying aggregates can be hard.</span></span> <span data-ttu-id="406e4-186">彙總在一起，必須維持一致的物件群組但不能只需要挑選一整組物件，並加上標籤它們彙總。</span><span class="sxs-lookup"><span data-stu-id="406e4-186">An aggregate is a group of objects that must be consistent together, but you cannot just pick a group of objects and label them an aggregate.</span></span> <span data-ttu-id="406e4-187">您必須與網域概念開頭，並考慮與該概念相關的最常見交易中使用的實體。</span><span class="sxs-lookup"><span data-stu-id="406e4-187">You must start with a domain concept and think about the entities that are used in the most common transactions related to that concept.</span></span> <span data-ttu-id="406e4-188">處於交易一致狀態需要這些實體是什麼 form 彙總。</span><span class="sxs-lookup"><span data-stu-id="406e4-188">Those entities that need to be transactionally consistent are what forms an aggregate.</span></span> <span data-ttu-id="406e4-189">思考交易操作可能是最佳的方式來識別彙總。</span><span class="sxs-lookup"><span data-stu-id="406e4-189">Thinking about transaction operations is probably the best way to identify aggregates.</span></span>

### <a name="the-aggregate-root-or-root-entity-pattern"></a><span data-ttu-id="406e4-190">彙總根或根實體模式</span><span class="sxs-lookup"><span data-stu-id="406e4-190">The Aggregate Root or Root Entity pattern</span></span>

<span data-ttu-id="406e4-191">彙總由至少一個實體所組成： 彙總根，也稱為根實體或主要 ientity。</span><span class="sxs-lookup"><span data-stu-id="406e4-191">An aggregate is composed of at least one entity: the aggregate root, also called root entity or primary ientity.</span></span> <span data-ttu-id="406e4-192">此外，它可以有多個子實體和值的物件，包含的所有實體及物件一起工作來實作所需的行為與交易。</span><span class="sxs-lookup"><span data-stu-id="406e4-192">Additionally, it can have multiple child entities and value objects, with all entities and objects working together to implement required behavior and transactions.</span></span>

<span data-ttu-id="406e4-193">彙總根的目的是確保彙總; 一致性它應該是唯一的進入點的更新彙總透過方法或作業的彙總根類別。</span><span class="sxs-lookup"><span data-stu-id="406e4-193">The purpose of an aggregate root is to ensure the consistency of the aggregate; it should be the only entry point for updates to the aggregate through methods or operations in the aggregate root class.</span></span> <span data-ttu-id="406e4-194">您應該變更彙總根僅透過彙總內的實體。</span><span class="sxs-lookup"><span data-stu-id="406e4-194">You should make changes to entities within the aggregate only via the aggregate root.</span></span> <span data-ttu-id="406e4-195">它是在彙總一致性守護者，所有的非變異項目和您可能需要遵守您彙總中的一致性規則列入考量。</span><span class="sxs-lookup"><span data-stu-id="406e4-195">It is the aggregate’s consistency guardian, taking into account all the invariants and consistency rules you might need to comply with in your aggregate.</span></span> <span data-ttu-id="406e4-196">如果您是獨立變更子實體或值物件，無法確保彙總根，，彙總就是處於有效狀態。</span><span class="sxs-lookup"><span data-stu-id="406e4-196">If you change a child entity or value object independently, the aggregate root cannot ensure that the aggregate is in a valid state.</span></span> <span data-ttu-id="406e4-197">將與鬆散的階段與資料表類似。</span><span class="sxs-lookup"><span data-stu-id="406e4-197">It would be like a table with a loose leg.</span></span> <span data-ttu-id="406e4-198">維護的一致性是彙總根的主要用途。</span><span class="sxs-lookup"><span data-stu-id="406e4-198">Maintaining consistency is the main purpose of the aggregate root.</span></span>

<span data-ttu-id="406e4-199">在圖 9-9，您可以查看範例彙總，例如買方彙總，其中包含單一實體 （彙總根買方）。</span><span class="sxs-lookup"><span data-stu-id="406e4-199">In Figure 9-9, you can see sample aggregates like the buyer aggregate, which contains a single entity (the aggregate root Buyer).</span></span> <span data-ttu-id="406e4-200">順序彙總包含多個實體和值的物件。</span><span class="sxs-lookup"><span data-stu-id="406e4-200">The order aggregate contains multiple entities and a value object.</span></span>

![](./media/image10.png)

<span data-ttu-id="406e4-201">**圖 9 9**。</span><span class="sxs-lookup"><span data-stu-id="406e4-201">**Figure 9-9**.</span></span> <span data-ttu-id="406e4-202">使用多個彙總的範例或單一實體</span><span class="sxs-lookup"><span data-stu-id="406e4-202">Example of aggregates with multiple or single entities</span></span>

<span data-ttu-id="406e4-203">請注意買方彙總可能有其他子實體，根據您的網域中順序的微服務 eShopOnContainers 參考應用程式中一樣。</span><span class="sxs-lookup"><span data-stu-id="406e4-203">Note that the Buyer aggregate could have additional child entities, depending on your domain, as it does in the ordering microservice in the eShopOnContainers reference application.</span></span> <span data-ttu-id="406e4-204">圖 9 9 只將說明其中買方的單一實體，例如彙總，其中包含只有彙總根的情況。</span><span class="sxs-lookup"><span data-stu-id="406e4-204">Figure 9-9 just illustrates a case in which the buyer has a single entity, as an example of an aggregate that contains only an aggregate root.</span></span>

<span data-ttu-id="406e4-205">為了維持分離的彙總，並讓它們之間有清楚的界限，最佳作法是在 DDD 網域模型中不允許直接瀏覽不同的彙總，以及只取得外部索引鍵 (FK) 欄位中，以實作[排序微服務網域模型](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs)eShopOnContainers 中。</span><span class="sxs-lookup"><span data-stu-id="406e4-205">In order to maintain separation of aggregates and keep clear boundaries between them, it is a good practice in a DDD domain model to disallow direct navigation between aggregates and only having the foreign key (FK) field, as implemented in the [Ordering microservice domain model](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs) in eShopOnContainers.</span></span> <span data-ttu-id="406e4-206">「 訂單 」 實體只有 FK 欄位買方，但不 EF 核心導覽屬性，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="406e4-206">The Order entity only has a FK field for the buyer, but not an EF Core navigation property, as shown in the following code:</span></span>

```csharp
public class Order : Entity, IAggregateRoot
{
    private DateTime _orderDate;
    public Address Address { get; private set; }
    private int? _buyerId; //FK pointing to a different aggregate root
    public OrderStatus OrderStatus { get; private set; }
}
```

<span data-ttu-id="406e4-207">識別及使用彙總需要的研究和經驗。</span><span class="sxs-lookup"><span data-stu-id="406e4-207">Identifying and working with aggregates requires research and experience.</span></span> <span data-ttu-id="406e4-208">如需詳細資訊，請參閱下表的其他資源。</span><span class="sxs-lookup"><span data-stu-id="406e4-208">For more information, see the following Additional resources list.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="406e4-209">其他資源</span><span class="sxs-lookup"><span data-stu-id="406e4-209">Additional resources</span></span>

-   <span data-ttu-id="406e4-210">**Vaughn Vernon：有效的彙總設計的第一部份： 模型的單一彙總**
    [*https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD\_社群\_短文\_彙總\_一部分\_1.pdf*](https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_1.pdf)</span><span class="sxs-lookup"><span data-stu-id="406e4-210">**Vaughn Vernon. Effective Aggregate Design - Part I: Modeling a Single Aggregate**
[*https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD\_COMMUNITY\_ESSAY\_AGGREGATES\_PART\_1.pdf*](https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_1.pdf)</span></span>

-   <span data-ttu-id="406e4-211">**Vaughn Vernon：有效彙總設計-第 2 部分： 進行彙總可共同運作**
    *<https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_2.pdf>*</span><span class="sxs-lookup"><span data-stu-id="406e4-211">**Vaughn Vernon. Effective Aggregate Design - Part II: Making Aggregates Work Together**
*<https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_2.pdf> *</span></span>

-   <span data-ttu-id="406e4-212">**Vaughn Vernon：有效彙總設計-第 3 篇： 取得深入了解透過探索**
    *<https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_3.pdf>*</span><span class="sxs-lookup"><span data-stu-id="406e4-212">**Vaughn Vernon. Effective Aggregate Design - Part III: Gaining Insight Through Discovery**
*<https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_3.pdf> *</span></span>

-   <span data-ttu-id="406e4-213">**Sergey Grybniak。DDD 戰術設計模式**
    [*https://www.codeproject.com/Articles/1164363/Domain-Driven-Design-Tactical-Design-Patterns-Part*](https://www.codeproject.com/Articles/1164363/Domain-Driven-Design-Tactical-Design-Patterns-Part)</span><span class="sxs-lookup"><span data-stu-id="406e4-213">**Sergey Grybniak. DDD Tactical Design Patterns**
[*https://www.codeproject.com/Articles/1164363/Domain-Driven-Design-Tactical-Design-Patterns-Part*](https://www.codeproject.com/Articles/1164363/Domain-Driven-Design-Tactical-Design-Patterns-Part)</span></span>

-   <span data-ttu-id="406e4-214">**Chris Richardson。開發使用彙總的交易式 Microservices**
    [*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-1-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-1-richardson)</span><span class="sxs-lookup"><span data-stu-id="406e4-214">**Chris Richardson. Developing Transactional Microservices Using Aggregates**
[*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-1-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-1-richardson)</span></span>

-   <span data-ttu-id="406e4-215">**DevIQ。彙總模式**
    [*http://deviq.com/aggregate-pattern/*](http://deviq.com/aggregate-pattern/)</span><span class="sxs-lookup"><span data-stu-id="406e4-215">**DevIQ. The Aggregate pattern**
[*http://deviq.com/aggregate-pattern/*](http://deviq.com/aggregate-pattern/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="406e4-216">[上一個](ddd-導向-microservice.md) [下一步] (net-核心-微服務-網域-model.md)</span><span class="sxs-lookup"><span data-stu-id="406e4-216">[Previous] (ddd-oriented-microservice.md) [Next] (net-core-microservice-domain-model.md)</span></span>
