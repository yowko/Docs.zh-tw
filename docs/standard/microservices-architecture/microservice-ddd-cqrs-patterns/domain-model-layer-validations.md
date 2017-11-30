---
title: "設計網域模型層中的驗證"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |設計網域模型層中的驗證"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: f4870d0568c3539f296bcb3f577291cb0250cfca
ms.sourcegitcommit: 62d3e3e74c1b7ffa927590012c0b9f87de1b0848
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="designing-validations-in-the-domain-model-layer"></a><span data-ttu-id="ef10d-104">設計網域模型層中的驗證</span><span class="sxs-lookup"><span data-stu-id="ef10d-104">Designing validations in the domain model layer</span></span>

<span data-ttu-id="ef10d-105">在 DDD，驗證規則可以視為非變異值。</span><span class="sxs-lookup"><span data-stu-id="ef10d-105">In DDD, validation rules can be thought as invariants.</span></span> <span data-ttu-id="ef10d-106">彙總的主要的責任是跨彙總內的所有實體的狀態變更強制執行非變異值。</span><span class="sxs-lookup"><span data-stu-id="ef10d-106">The main responsibility of an aggregate is to enforce invariants across state changes for all the entities within that aggregate.</span></span>

<span data-ttu-id="ef10d-107">網域實體應該一律是有效的實體。</span><span class="sxs-lookup"><span data-stu-id="ef10d-107">Domain entities should always be valid entities.</span></span> <span data-ttu-id="ef10d-108">有非變異值應永遠為 true 的物件數目。</span><span class="sxs-lookup"><span data-stu-id="ef10d-108">There are a certain number of invariants for an object that should always be true.</span></span> <span data-ttu-id="ef10d-109">例如，訂單項目物件一律必須要有必須是正整數，加上一個發行項名稱和價格的數量。</span><span class="sxs-lookup"><span data-stu-id="ef10d-109">For example, an order item object always has to have a quantity that must be a positive integer, plus an article name and price.</span></span> <span data-ttu-id="ef10d-110">因此，非變異項目強制負責 （特別是彙總的根目錄） 之網域實體和實體物件不應該能夠存在而無效。</span><span class="sxs-lookup"><span data-stu-id="ef10d-110">Therefore, invariants enforcement is the responsibility of the domain entities (especially of the aggregate root) and an entity object should not be able to exist without being valid.</span></span> <span data-ttu-id="ef10d-111">而異的規則只是表示為合約，以及它們違反時引發的例外狀況或通知。</span><span class="sxs-lookup"><span data-stu-id="ef10d-111">Invariant rules are simply expressed as contracts, and exceptions or notifications are raised when they are violated.</span></span>

<span data-ttu-id="ef10d-112">這背後的原因是因為物件處於它們應永遠不會過的會發生很多 bug。</span><span class="sxs-lookup"><span data-stu-id="ef10d-112">The reasoning behind this is that many bugs occur because objects are in a state they should never have been in.</span></span> <span data-ttu-id="ef10d-113">以下是合理的解釋，從在 Greg Young[線上討論](http://jeffreypalermo.com/blog/the-fallacy-of-the-always-valid-entity/):</span><span class="sxs-lookup"><span data-stu-id="ef10d-113">The following is a good explanation from Greg Young in an [online discussion](http://jeffreypalermo.com/blog/the-fallacy-of-the-always-valid-entity/):</span></span>

<span data-ttu-id="ef10d-114">我們建議我們現在有 SendUserCreationEmailService 採用 UserProfile...方式可以我們合理化中該名稱不是 null 的服務嗎？</span><span class="sxs-lookup"><span data-stu-id="ef10d-114">Let's propose we now have a SendUserCreationEmailService that takes a UserProfile ... how can we rationalize in that service that Name is not null?</span></span> <span data-ttu-id="ef10d-115">請勿我們檢查它一次？</span><span class="sxs-lookup"><span data-stu-id="ef10d-115">Do we check it again?</span></span> <span data-ttu-id="ef10d-116">或更...您就不必擔心會檢查並"希望獲得最佳"— 您希望有人既然驗證再將它傳送給您。</span><span class="sxs-lookup"><span data-stu-id="ef10d-116">Or more likely ... you just don't bother to check and "hope for the best"—you hope that someone bothered to validate it before sending it to you.</span></span> <span data-ttu-id="ef10d-117">當然，使用第一個測試，我們應該，如果傳送擁有名稱為空值的客戶應該引發錯誤會寫入一個的 TDD。</span><span class="sxs-lookup"><span data-stu-id="ef10d-117">Of course, using TDD one of the first tests we should be writing is that if I send a customer with a null name that it should raise an error.</span></span> <span data-ttu-id="ef10d-118">但是，當我們開始不斷地撰寫這些類型的測試我們了解...「 等待我們永遠不會允許名稱成為 null 就不會有所有這些測試 」</span><span class="sxs-lookup"><span data-stu-id="ef10d-118">But once we start writing these kinds of tests over and over again we realize ... "wait if we never allowed name to become null we wouldn't have all of these tests"</span></span>

## <a name="implementing-validations-in-the-domain-model-layer"></a><span data-ttu-id="ef10d-119">在網域模型層中實作驗證</span><span class="sxs-lookup"><span data-stu-id="ef10d-119">Implementing validations in the domain model layer</span></span>

<span data-ttu-id="ef10d-120">網域實體的建構函式中或在可以更新實體的方法，通常會實作驗證。</span><span class="sxs-lookup"><span data-stu-id="ef10d-120">Validations are usually implemented in domain entity constructors or in methods that can update the entity.</span></span> <span data-ttu-id="ef10d-121">有多個方式來實作驗證，例如驗證資料和驗證失敗時引發的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ef10d-121">There are multiple ways to implement validations, such as verifying data and raising exceptions if the validation fails.</span></span> <span data-ttu-id="ef10d-122">另外還有更進階的模式，例如規格模式用於驗證和通知模式，傳回錯誤，而不是傳回的每個驗證例外狀況發生時的集合。</span><span class="sxs-lookup"><span data-stu-id="ef10d-122">There are also more advanced patterns such as using the Specification pattern for validations, and the Notification pattern to return a collection of errors instead of returning an exception for each validation as it occurs.</span></span>

### <a name="validating-conditions-and-throwing-exceptions"></a><span data-ttu-id="ef10d-123">驗證條件並擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="ef10d-123">Validating conditions and throwing exceptions</span></span>

<span data-ttu-id="ef10d-124">下列程式碼範例會顯示最簡單的方法來驗證網域實體中引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ef10d-124">The following code example shows the simplest approach to validation in a domain entity by raising an exception.</span></span> <span data-ttu-id="ef10d-125">在本節結尾處的參考資料表中，您可以看到連結更進階的實作，根據我們先前已經討論過的模式。</span><span class="sxs-lookup"><span data-stu-id="ef10d-125">In the references table at the end of this section you can see links to more advanced implementations based on the patterns we have discussed previously.</span></span>

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

<span data-ttu-id="ef10d-126">更好的範例會示範須確定的內部狀態並未變更，或為方法的所有變化都發生。</span><span class="sxs-lookup"><span data-stu-id="ef10d-126">A better example would demonstrate the need to ensure that either the internal state did not change, or that all the mutations for a method occurred.</span></span> <span data-ttu-id="ef10d-127">例如，下列實作會讓物件處於無效狀態：</span><span class="sxs-lookup"><span data-stu-id="ef10d-127">For example, the following implementation would leave the object in an invalid state:</span></span>

```csharp
public void SetAddress(string line1, string line2,
    string city, string state, int zip)
{
    _shipingAddress.line1 = line1 ?? throw new ...
    _shippingAddress.line2 = line2;
    _shippingAddress.city = city ?? throw new ...
    _shippingAddress.state = (IsValid(state) ? state : throw new …);
}
```

<span data-ttu-id="ef10d-128">如果狀態的值無效，已經已變更第一個地址和縣 （市）。</span><span class="sxs-lookup"><span data-stu-id="ef10d-128">If the value of the state is invalid, the first address line and the city have already been changed.</span></span> <span data-ttu-id="ef10d-129">可能會使位址無效。</span><span class="sxs-lookup"><span data-stu-id="ef10d-129">That might make the address invalid.</span></span>

<span data-ttu-id="ef10d-130">類似的方法可以用於實體的建構函式，引發例外狀況以確定此實體是有效的一旦建立之後。</span><span class="sxs-lookup"><span data-stu-id="ef10d-130">A similar approach can be used in the entity’s constructor, raising an exception to make sure that the entity is valid once it is created.</span></span>

### <a name="using-validation-attributes-in-the-model-based-on-data-annotations"></a><span data-ttu-id="ef10d-131">使用資料註解為基礎的模型中的驗證屬性</span><span class="sxs-lookup"><span data-stu-id="ef10d-131">Using validation attributes in the model based on data annotations</span></span>

<span data-ttu-id="ef10d-132">另一種方法是使用資料註解為基礎的驗證屬性。</span><span class="sxs-lookup"><span data-stu-id="ef10d-132">Another approach is to use validation attributes based on data annotations.</span></span> <span data-ttu-id="ef10d-133">驗證屬性提供設定模型驗證，也就是在概念上類似資料庫資料表中的欄位上的驗證方法。</span><span class="sxs-lookup"><span data-stu-id="ef10d-133">Validation attributes provide a way to configure model validation, which is similar conceptually to validation on fields in database tables.</span></span> <span data-ttu-id="ef10d-134">這包括條件約束，例如指派必要的欄位或資料型別。</span><span class="sxs-lookup"><span data-stu-id="ef10d-134">This includes constraints such as assigning data types or required fields.</span></span> <span data-ttu-id="ef10d-135">其他類型的驗證模式來套用到資料，以強制執行商務規則，例如信用卡號碼，電話號碼或電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="ef10d-135">Other types of validation include applying patterns to data to enforce business rules, such as a credit card number, phone number, or email address.</span></span> <span data-ttu-id="ef10d-136">驗證屬性，讓您輕鬆地強制執行需求。</span><span class="sxs-lookup"><span data-stu-id="ef10d-136">Validation attributes make it easy to enforce requirements.</span></span>

<span data-ttu-id="ef10d-137">不過，下列程式碼所示，這種方法可能太具侵入性在 DDD 模型中，因為所需的相依性上 ModelState.IsValid Microsoft.AspNetCore.Mvc.ModelState，您必須從 MVC 控制器方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="ef10d-137">However, as shown in the following code, this approach might be too intrusive in a DDD model, because it takes a dependency on ModelState.IsValid from Microsoft.AspNetCore.Mvc.ModelState, which you must call from your MVC controllers.</span></span> <span data-ttu-id="ef10d-138">模型驗證，就會發生在之前所叫用每個控制器動作，並負責控制器方法來檢查呼叫 ModelState.IsValid 結果和作出適當回應。</span><span class="sxs-lookup"><span data-stu-id="ef10d-138">The model validation occurs prior to each controller action being invoked, and it is the controller method’s responsibility to inspect the result of calling ModelState.IsValid and react appropriately.</span></span> <span data-ttu-id="ef10d-139">若要使用它的決定取決於如何緊密結合您想要該基礎結構的模型。</span><span class="sxs-lookup"><span data-stu-id="ef10d-139">The decision to use it depends on how tightly coupled you want the model to be with that infrastructure.</span></span>

```csharp
using System.ComponentModel.DataAnnotations;
// Other using statements ...
// Entity is a custom base class which has the ID
public class Product : Entity
{
    [Required]
    [StringLength(100)]
    public string Title { get; private set; }

    [Required]
    [Range(0, 999.99)]
    public decimal Price { get; private set; }

    [Required]
    [VintageProduct(1970)]
    [DataType(DataType.Date)]
    public DateTime ReleaseDate { get; private set; }

    [Required]
    [StringLength(1000)]
    public string Description { get; private set; }

    // Constructor...
    // Additional methods for entity logic and constructor...
}
```

<span data-ttu-id="ef10d-140">不過，DDD 觀點來看，從網域模型妥善保存 「 精實 」 例外狀況的使用中實體的行為的方法，或藉由實作來強制執行驗證規則的規格和通知模式。</span><span class="sxs-lookup"><span data-stu-id="ef10d-140">However, from a DDD point of view, the domain model is best kept lean with the use of exceptions in your entity’s behavior methods, or by implementing the Specification and Notification patterns to enforce validation rules.</span></span> <span data-ttu-id="ef10d-141">驗證架構，像 ASP.NET Core 中的資料註解或 FluentValidation 像任何其他驗證架構執行叫用的應用程式架構的需求。</span><span class="sxs-lookup"><span data-stu-id="ef10d-141">Validation frameworks like data annotations in ASP.NET Core or any other validation frameworks like FluentValidation carry a requirement to invoke the application framework.</span></span> <span data-ttu-id="ef10d-142">例如，呼叫 ModelState.IsValid 方法時資料註解中，您需要叫用 ASP.NET 控制器。</span><span class="sxs-lookup"><span data-stu-id="ef10d-142">For example, when calling the ModelState.IsValid method in data annotations, you need to invoke ASP.NET controllers.</span></span>

<span data-ttu-id="ef10d-143">它可以合理層的應用程式會接受輸入，以提供 UI 層中的模型驗證的 ViewModel 類別 （而不是網域實體） 中使用資料註解。</span><span class="sxs-lookup"><span data-stu-id="ef10d-143">It can make sense to use data annotations at the application layer in ViewModel classes (instead of domain entities) that will accept input, to allow for model validation within the UI layer.</span></span> <span data-ttu-id="ef10d-144">不過，這不應該在驗證網域模型中排除。</span><span class="sxs-lookup"><span data-stu-id="ef10d-144">However, this should not be done at the exclusion of validation within the domain model.</span></span>

### <a name="validating-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a><span data-ttu-id="ef10d-145">藉由實作規格模式和通知模式驗證實體</span><span class="sxs-lookup"><span data-stu-id="ef10d-145">Validating entities by implementing the Specification pattern and the Notification pattern</span></span>

<span data-ttu-id="ef10d-146">最後，更複雜的方法，在網域模型中實作驗證是實作規格模式搭配通知模式中，稍後將列出的其他資源的部分中所述。</span><span class="sxs-lookup"><span data-stu-id="ef10d-146">Finally, a more elaborate approach to implementing validations in the domain model is by implementing the Specification pattern in conjunction with the Notification pattern, as explained in some of the additional resources listed later.</span></span>

<span data-ttu-id="ef10d-147">值得一提，您也可以使用這些模式的其中一 — 比方說，手動驗證與控制陳述式，但使用的通知模式堆疊，並傳回驗證錯誤的清單。</span><span class="sxs-lookup"><span data-stu-id="ef10d-147">It is worth mentioning that you can also use just one of those patterns—for example, validating manually with control statements, but using the Notification pattern to stack and return a list of validation errors.</span></span>

### <a name="using-deferred-validation-in-the-domain"></a><span data-ttu-id="ef10d-148">在網域中使用延後的驗證</span><span class="sxs-lookup"><span data-stu-id="ef10d-148">Using deferred validation in the domain</span></span>

<span data-ttu-id="ef10d-149">有各種方法來處理網域中延後的驗證。</span><span class="sxs-lookup"><span data-stu-id="ef10d-149">There are various approaches to deal with deferred validations in the domain.</span></span> <span data-ttu-id="ef10d-150">他活頁簿中[Implementing Domain-Driven 設計](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577)，Vaughn Vernon 討論這些區段中驗證。</span><span class="sxs-lookup"><span data-stu-id="ef10d-150">In his book [Implementing Domain-Driven Design](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon discusses these in the section on validation.</span></span>

### <a name="two-step-validation"></a><span data-ttu-id="ef10d-151">兩步驟驗證</span><span class="sxs-lookup"><span data-stu-id="ef10d-151">Two-step validation</span></span>

<span data-ttu-id="ef10d-152">也請考慮雙步驟驗證。</span><span class="sxs-lookup"><span data-stu-id="ef10d-152">Also consider two-step validation.</span></span> <span data-ttu-id="ef10d-153">在命令資料傳輸物件 (Dto) 和網域層級驗證，在您的實體上使用欄位層級驗證。</span><span class="sxs-lookup"><span data-stu-id="ef10d-153">Use field-level validation on your command Data Transfer Objects (DTOs) and domain-level validation inside your entities.</span></span> <span data-ttu-id="ef10d-154">您可以傳回結果物件改為例外狀況以使其更容易處理的驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="ef10d-154">You can do this by returning a result object instead exceptions in order to make it easier to deal with the validation errors.</span></span>

<span data-ttu-id="ef10d-155">使用資料註解欄位驗證，例如，您不會重複驗證定義。</span><span class="sxs-lookup"><span data-stu-id="ef10d-155">Using field validation with data annotations, for example, you do not duplicate the validation definition.</span></span> <span data-ttu-id="ef10d-156">執行時，不過，可以是伺服器端和用戶端在 DTOs 的情況下 (命令和 ViewModels，執行個體)。</span><span class="sxs-lookup"><span data-stu-id="ef10d-156">The execution, though, can be both server-side and client-side in the case of DTOs (commands and ViewModels, for instance).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="ef10d-157">其他資源</span><span class="sxs-lookup"><span data-stu-id="ef10d-157">Additional resources</span></span>

-   <span data-ttu-id="ef10d-158">**Rachel Appel。ASP.NET Core MVC 中的模型驗證的簡介**
    [*https://docs.microsoft.com/aspnet/core/mvc/models/validation*](https://docs.microsoft.com/aspnet/core/mvc/models/validation)</span><span class="sxs-lookup"><span data-stu-id="ef10d-158">**Rachel Appel. Introduction to model validation in ASP.NET Core MVC**
[*https://docs.microsoft.com/aspnet/core/mvc/models/validation*](https://docs.microsoft.com/aspnet/core/mvc/models/validation)</span></span>

-   <span data-ttu-id="ef10d-159">**Rick Anderson，加入驗證**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span><span class="sxs-lookup"><span data-stu-id="ef10d-159">**Rick Anderson. Adding validation**
[*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span></span>

-   <span data-ttu-id="ef10d-160">**Martin Fowler：取代在驗證中擲回例外狀況，其通知**
    [*https://martinfowler.com/articles/replaceThrowWithNotification.html*](https://martinfowler.com/articles/replaceThrowWithNotification.html)</span><span class="sxs-lookup"><span data-stu-id="ef10d-160">**Martin Fowler. Replacing Throwing Exceptions with Notification in Validations**
[*https://martinfowler.com/articles/replaceThrowWithNotification.html*](https://martinfowler.com/articles/replaceThrowWithNotification.html)</span></span>

-   <span data-ttu-id="ef10d-161">**規格和通知模式**
    [*https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns*](https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns)</span><span class="sxs-lookup"><span data-stu-id="ef10d-161">**Specification and Notification Patterns**
[*https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns*](https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns)</span></span>

-   <span data-ttu-id="ef10d-162">**列弗 Gorodinski。驗證在網域導向設計 (DDD)**
    [*http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/*](http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/)</span><span class="sxs-lookup"><span data-stu-id="ef10d-162">**Lev Gorodinski. Validation in Domain-Driven Design (DDD)**
[*http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/*](http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/)</span></span>

-   <span data-ttu-id="ef10d-163">**Colin 端子。網域模型驗證**
    [*http://colinjack.blogspot.com/2008/03/domain-model-validation.html*](http://colinjack.blogspot.com/2008/03/domain-model-validation.html)</span><span class="sxs-lookup"><span data-stu-id="ef10d-163">**Colin Jack. Domain Model Validation**
[*http://colinjack.blogspot.com/2008/03/domain-model-validation.html*](http://colinjack.blogspot.com/2008/03/domain-model-validation.html)</span></span>

-   <span data-ttu-id="ef10d-164">**Jimmy Bogard：DDD 世界中的驗證**
    [*https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/*](https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/)</span><span class="sxs-lookup"><span data-stu-id="ef10d-164">**Jimmy Bogard. Validation in a DDD world**
[*https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/*](https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="ef10d-165">[上一個](列舉-類別-over-列舉-types.md) [下一步] (用戶端-側邊-validation.md)</span><span class="sxs-lookup"><span data-stu-id="ef10d-165">[Previous] (enumeration-classes-over-enum-types.md) [Next] (client-side-validation.md)</span></span>
