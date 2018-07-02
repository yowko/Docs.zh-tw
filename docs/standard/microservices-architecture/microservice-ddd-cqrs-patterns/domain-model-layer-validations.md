---
title: 設計領域模型層中的驗證
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 設計領域模型層中的驗證
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: c071d269977ccecea9a7d4d79da78d7967bb1618
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105731"
---
# <a name="designing-validations-in-the-domain-model-layer"></a><span data-ttu-id="76cc9-103">設計領域模型層中的驗證</span><span class="sxs-lookup"><span data-stu-id="76cc9-103">Designing validations in the domain model layer</span></span>

<span data-ttu-id="76cc9-104">在 DDD 中，驗證規則可以視為非變異值。</span><span class="sxs-lookup"><span data-stu-id="76cc9-104">In DDD, validation rules can be thought as invariants.</span></span> <span data-ttu-id="76cc9-105">彙總的主要責任是跨該彙總內所有實體的狀態變更來強制執行非變異值。</span><span class="sxs-lookup"><span data-stu-id="76cc9-105">The main responsibility of an aggregate is to enforce invariants across state changes for all the entities within that aggregate.</span></span>

<span data-ttu-id="76cc9-106">領域實體應該一律是有效的實體。</span><span class="sxs-lookup"><span data-stu-id="76cc9-106">Domain entities should always be valid entities.</span></span> <span data-ttu-id="76cc9-107">一律應該為 true 的物件會有特定數目的非變異值。</span><span class="sxs-lookup"><span data-stu-id="76cc9-107">There are a certain number of invariants for an object that should always be true.</span></span> <span data-ttu-id="76cc9-108">例如，訂單項目物件一律必須要有必須是正整數的數量，以及發行項名稱和價格。</span><span class="sxs-lookup"><span data-stu-id="76cc9-108">For example, an order item object always has to have a quantity that must be a positive integer, plus an article name and price.</span></span> <span data-ttu-id="76cc9-109">因此，非變異值強制執行負責領域實體 (特別是彙總根)，而且存在的實體物件應該有效。</span><span class="sxs-lookup"><span data-stu-id="76cc9-109">Therefore, invariants enforcement is the responsibility of the domain entities (especially of the aggregate root) and an entity object should not be able to exist without being valid.</span></span> <span data-ttu-id="76cc9-110">非變異值規則只會表示為合約，而且會在違反時引發例外狀況或通知。</span><span class="sxs-lookup"><span data-stu-id="76cc9-110">Invariant rules are simply expressed as contracts, and exceptions or notifications are raised when they are violated.</span></span>

<span data-ttu-id="76cc9-111">背後原因是物件處於絕對不應該處於的狀態而發生許多 Bug。</span><span class="sxs-lookup"><span data-stu-id="76cc9-111">The reasoning behind this is that many bugs occur because objects are in a state they should never have been in.</span></span> <span data-ttu-id="76cc9-112">下列是 Greg Young 在[線上討論](http://jeffreypalermo.com/blog/the-fallacy-of-the-always-valid-entity/)中的合理解釋：</span><span class="sxs-lookup"><span data-stu-id="76cc9-112">The following is a good explanation from Greg Young in an [online discussion](http://jeffreypalermo.com/blog/the-fallacy-of-the-always-valid-entity/):</span></span>

<span data-ttu-id="76cc9-113">建議我們現在具有採用 UserProfile 的 SendUserCreationEmailService ... 如何合理化 Name 不是 Null 的該服務？</span><span class="sxs-lookup"><span data-stu-id="76cc9-113">Let's propose we now have a SendUserCreationEmailService that takes a UserProfile ... how can we rationalize in that service that Name is not null?</span></span> <span data-ttu-id="76cc9-114">要再次確認嗎？</span><span class="sxs-lookup"><span data-stu-id="76cc9-114">Do we check it again?</span></span> <span data-ttu-id="76cc9-115">或者，更可能 ... 您不需要檢查並且「獲得最佳結果」- 您希望有人先進行驗證，再將它傳送給您。</span><span class="sxs-lookup"><span data-stu-id="76cc9-115">Or more likely ... you just don't bother to check and "hope for the best"—you hope that someone bothered to validate it before sending it to you.</span></span> <span data-ttu-id="76cc9-116">當然，使用 TDD，我們應該撰寫的其中一個第一個測試就是將應該會引發錯誤的 Null 名稱傳送給客戶。</span><span class="sxs-lookup"><span data-stu-id="76cc9-116">Of course, using TDD one of the first tests we should be writing is that if I send a customer with a null name that it should raise an error.</span></span> <span data-ttu-id="76cc9-117">但是，當我們開始不斷地撰寫這些類型的測試時了解：「等一下，如果我們永遠不允許名稱變成 Null，就不會有所有這些測試」。</span><span class="sxs-lookup"><span data-stu-id="76cc9-117">But once we start writing these kinds of tests over and over again we realize ... "wait if we never allowed name to become null we wouldn't have all of these tests"</span></span>

## <a name="implementing-validations-in-the-domain-model-layer"></a><span data-ttu-id="76cc9-118">實作領域模型層中的驗證</span><span class="sxs-lookup"><span data-stu-id="76cc9-118">Implementing validations in the domain model layer</span></span>

<span data-ttu-id="76cc9-119">通常是在領域實體建構函式或可更新實體的方法中實作驗證。</span><span class="sxs-lookup"><span data-stu-id="76cc9-119">Validations are usually implemented in domain entity constructors or in methods that can update the entity.</span></span> <span data-ttu-id="76cc9-120">有多種方式可以實作驗證，例如驗證資料，以及在驗證失敗時引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="76cc9-120">There are multiple ways to implement validations, such as verifying data and raising exceptions if the validation fails.</span></span> <span data-ttu-id="76cc9-121">另外還有更進階模式，例如使用規格模式進行驗證，以及使用通知模式傳回錯誤集合，而不是傳回每個驗證所發生的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="76cc9-121">There are also more advanced patterns such as using the Specification pattern for validations, and the Notification pattern to return a collection of errors instead of returning an exception for each validation as it occurs.</span></span>

### <a name="validating-conditions-and-throwing-exceptions"></a><span data-ttu-id="76cc9-122">驗證條件並擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="76cc9-122">Validating conditions and throwing exceptions</span></span>

<span data-ttu-id="76cc9-123">下列程式碼範例透過引發例外狀況來示範領域實體中的最簡單驗證方法。</span><span class="sxs-lookup"><span data-stu-id="76cc9-123">The following code example shows the simplest approach to validation in a domain entity by raising an exception.</span></span> <span data-ttu-id="76cc9-124">在本節結尾的參考資料表中，您可以看到根據我們先前討論過之模式的更進階實作連結。</span><span class="sxs-lookup"><span data-stu-id="76cc9-124">In the references table at the end of this section you can see links to more advanced implementations based on the patterns we have discussed previously.</span></span>

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

<span data-ttu-id="76cc9-125">更好的範例會示範需要確定內部狀態未變更，或方法的所有變化。</span><span class="sxs-lookup"><span data-stu-id="76cc9-125">A better example would demonstrate the need to ensure that either the internal state did not change, or that all the mutations for a method occurred.</span></span> <span data-ttu-id="76cc9-126">例如，下列實作會讓物件處於無效狀態：</span><span class="sxs-lookup"><span data-stu-id="76cc9-126">For example, the following implementation would leave the object in an invalid state:</span></span>

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

<span data-ttu-id="76cc9-127">如果狀態的值無效，則已經變更第一個地址行和縣 (市)。</span><span class="sxs-lookup"><span data-stu-id="76cc9-127">If the value of the state is invalid, the first address line and the city have already been changed.</span></span> <span data-ttu-id="76cc9-128">這可能會讓地址無效。</span><span class="sxs-lookup"><span data-stu-id="76cc9-128">That might make the address invalid.</span></span>

<span data-ttu-id="76cc9-129">類似的方法可以用於實體的建構函式，即引發例外狀況來確定實體在建立之後有效。</span><span class="sxs-lookup"><span data-stu-id="76cc9-129">A similar approach can be used in the entity’s constructor, raising an exception to make sure that the entity is valid once it is created.</span></span>

### <a name="using-validation-attributes-in-the-model-based-on-data-annotations"></a><span data-ttu-id="76cc9-130">在根據資料註解的模型中使用驗證屬性</span><span class="sxs-lookup"><span data-stu-id="76cc9-130">Using validation attributes in the model based on data annotations</span></span>

<span data-ttu-id="76cc9-131">另一種方法是使用根據資料註解的驗證屬性。</span><span class="sxs-lookup"><span data-stu-id="76cc9-131">Another approach is to use validation attributes based on data annotations.</span></span> <span data-ttu-id="76cc9-132">驗證屬性提供設定模型驗證的方式，而在概念上，類似資料庫資料表中的欄位驗證。</span><span class="sxs-lookup"><span data-stu-id="76cc9-132">Validation attributes provide a way to configure model validation, which is similar conceptually to validation on fields in database tables.</span></span> <span data-ttu-id="76cc9-133">這包括條件約束，例如指派資料類型或必要欄位。</span><span class="sxs-lookup"><span data-stu-id="76cc9-133">This includes constraints such as assigning data types or required fields.</span></span> <span data-ttu-id="76cc9-134">其他驗證類型還包括將模式套用至資料以強制執行商務規則，例如信用卡號碼、電話號碼或電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="76cc9-134">Other types of validation include applying patterns to data to enforce business rules, such as a credit card number, phone number, or email address.</span></span> <span data-ttu-id="76cc9-135">驗證屬性可簡化需求強制執行。</span><span class="sxs-lookup"><span data-stu-id="76cc9-135">Validation attributes make it easy to enforce requirements.</span></span>

<span data-ttu-id="76cc9-136">不過，如下列程式碼所示，這種方法在 DDD 模型中可能太具侵入性，因為它相依於您必須從 MVC 控制器呼叫之 Microsoft.AspNetCore.Mvc.ModelState 中的 ModelState.IsValid。</span><span class="sxs-lookup"><span data-stu-id="76cc9-136">However, as shown in the following code, this approach might be too intrusive in a DDD model, because it takes a dependency on ModelState.IsValid from Microsoft.AspNetCore.Mvc.ModelState, which you must call from your MVC controllers.</span></span> <span data-ttu-id="76cc9-137">模型驗證會在叫用每個控制器動作之前發生，而且控制器方法負責檢查呼叫中 ModelState.IsValid 的結果並做出適當回應。</span><span class="sxs-lookup"><span data-stu-id="76cc9-137">The model validation occurs prior to each controller action being invoked, and it is the controller method’s responsibility to inspect the result of calling ModelState.IsValid and react appropriately.</span></span> <span data-ttu-id="76cc9-138">使用它的決定取決於如何緊密結合模型與該基礎結構。</span><span class="sxs-lookup"><span data-stu-id="76cc9-138">The decision to use it depends on how tightly coupled you want the model to be with that infrastructure.</span></span>

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

<span data-ttu-id="76cc9-139">不過，從 DDD 觀點，領域模型會妥善使用您實體行為方法中的例外狀況，或藉由實作規格和通知模式來強制執行驗證規則。</span><span class="sxs-lookup"><span data-stu-id="76cc9-139">However, from a DDD point of view, the domain model is best kept lean with the use of exceptions in your entity’s behavior methods, or by implementing the Specification and Notification patterns to enforce validation rules.</span></span> <span data-ttu-id="76cc9-140">ASP.NET Core 中資料註解這類驗證架構或 FluentValidation 這類任何其他驗證架構需要叫用應用程式架構。</span><span class="sxs-lookup"><span data-stu-id="76cc9-140">Validation frameworks like data annotations in ASP.NET Core or any other validation frameworks like FluentValidation carry a requirement to invoke the application framework.</span></span> <span data-ttu-id="76cc9-141">例如，在資料註解中呼叫 ModelState.IsValid 方法時，您需要叫用 ASP.NET 控制器。</span><span class="sxs-lookup"><span data-stu-id="76cc9-141">For example, when calling the ModelState.IsValid method in data annotations, you need to invoke ASP.NET controllers.</span></span>

<span data-ttu-id="76cc9-142">它可以合理地使用接受輸入之 ViewModel 類別 (而非領域實體) 中應用程式層的資料註解，以允許 UI 層內的模型驗證。</span><span class="sxs-lookup"><span data-stu-id="76cc9-142">It can make sense to use data annotations at the application layer in ViewModel classes (instead of domain entities) that will accept input, to allow for model validation within the UI layer.</span></span> <span data-ttu-id="76cc9-143">不過，在領域模型內，這不應該排除驗證。</span><span class="sxs-lookup"><span data-stu-id="76cc9-143">However, this should not be done at the exclusion of validation within the domain model.</span></span>

### <a name="validating-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a><span data-ttu-id="76cc9-144">實作規格模式和通知模式來驗證實體</span><span class="sxs-lookup"><span data-stu-id="76cc9-144">Validating entities by implementing the Specification pattern and the Notification pattern</span></span>

<span data-ttu-id="76cc9-145">最後，在領域模型中實作驗證的更複雜方法，是一起實作規格模式與通知模式，如稍後列出的一些其他資源所述。</span><span class="sxs-lookup"><span data-stu-id="76cc9-145">Finally, a more elaborate approach to implementing validations in the domain model is by implementing the Specification pattern in conjunction with the Notification pattern, as explained in some of the additional resources listed later.</span></span>

<span data-ttu-id="76cc9-146">值得一提的是，您也可以只使用其中一種模式；例如，使用 control 陳述式手動驗證，但使用通知模式來堆疊和傳回驗證錯誤清單。</span><span class="sxs-lookup"><span data-stu-id="76cc9-146">It is worth mentioning that you can also use just one of those patterns—for example, validating manually with control statements, but using the Notification pattern to stack and return a list of validation errors.</span></span>

### <a name="using-deferred-validation-in-the-domain"></a><span data-ttu-id="76cc9-147">在領域中使用延後驗證</span><span class="sxs-lookup"><span data-stu-id="76cc9-147">Using deferred validation in the domain</span></span>

<span data-ttu-id="76cc9-148">有各種方法來處理領域中的延後驗證。</span><span class="sxs-lookup"><span data-stu-id="76cc9-148">There are various approaches to deal with deferred validations in the domain.</span></span> <span data-ttu-id="76cc9-149">Vaughn Vernon 會在其 [Implementing Domain-Driven Design](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577) (實作領域驅動設計) 書籍的驗證小節中討論這些方法。</span><span class="sxs-lookup"><span data-stu-id="76cc9-149">In his book [Implementing Domain-Driven Design](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon discusses these in the section on validation.</span></span>

### <a name="two-step-validation"></a><span data-ttu-id="76cc9-150">兩步驟驗證</span><span class="sxs-lookup"><span data-stu-id="76cc9-150">Two-step validation</span></span>

<span data-ttu-id="76cc9-151">也請考慮兩步驟驗證。</span><span class="sxs-lookup"><span data-stu-id="76cc9-151">Also consider two-step validation.</span></span> <span data-ttu-id="76cc9-152">在命令資料傳輸物件 (DTO) 上使用欄位層級驗證，以及在實體內部使用領域層級驗證。</span><span class="sxs-lookup"><span data-stu-id="76cc9-152">Use field-level validation on your command Data Transfer Objects (DTOs) and domain-level validation inside your entities.</span></span> <span data-ttu-id="76cc9-153">作法是傳回結果物件，而不是例外狀況，以更輕鬆地處理驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="76cc9-153">You can do this by returning a result object instead exceptions in order to make it easier to deal with the validation errors.</span></span>

<span data-ttu-id="76cc9-154">例如，使用具有資料註解的欄位驗證，就不會有重複的驗證定義。</span><span class="sxs-lookup"><span data-stu-id="76cc9-154">Using field validation with data annotations, for example, you do not duplicate the validation definition.</span></span> <span data-ttu-id="76cc9-155">不過，如果是 DTO，則執行可以是伺服器端和用戶端 (例如，命令和 ViewModel)。</span><span class="sxs-lookup"><span data-stu-id="76cc9-155">The execution, though, can be both server-side and client-side in the case of DTOs (commands and ViewModels, for instance).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="76cc9-156">其他資源</span><span class="sxs-lookup"><span data-stu-id="76cc9-156">Additional resources</span></span>

-   <span data-ttu-id="76cc9-157">**Rachel Appel：ASP.NET Core MVC 中的模型驗證簡介**
    [*https://docs.microsoft.com/aspnet/core/mvc/models/validation*](https://docs.microsoft.com/aspnet/core/mvc/models/validation)</span><span class="sxs-lookup"><span data-stu-id="76cc9-157">**Rachel Appel. Introduction to model validation in ASP.NET Core MVC**
[*https://docs.microsoft.com/aspnet/core/mvc/models/validation*](https://docs.microsoft.com/aspnet/core/mvc/models/validation)</span></span>

-   <span data-ttu-id="76cc9-158">**Rick Anderson，新增驗證**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span><span class="sxs-lookup"><span data-stu-id="76cc9-158">**Rick Anderson. Adding validation**
[*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span></span>

-   <span data-ttu-id="76cc9-159">**Martin Fowler：在驗證中將擲回例外狀況取代為通知**
    [*https://martinfowler.com/articles/replaceThrowWithNotification.html*](https://martinfowler.com/articles/replaceThrowWithNotification.html)</span><span class="sxs-lookup"><span data-stu-id="76cc9-159">**Martin Fowler. Replacing Throwing Exceptions with Notification in Validations**
[*https://martinfowler.com/articles/replaceThrowWithNotification.html*](https://martinfowler.com/articles/replaceThrowWithNotification.html)</span></span>

-   <span data-ttu-id="76cc9-160">**規格和通知模式**
    [*https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns*](https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns)</span><span class="sxs-lookup"><span data-stu-id="76cc9-160">**Specification and Notification Patterns**
[*https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns*](https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns)</span></span>

-   <span data-ttu-id="76cc9-161">**Lev Gorodinski：網域導向設計 (DDD) 中的驗證**
    [*http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/*](http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/)</span><span class="sxs-lookup"><span data-stu-id="76cc9-161">**Lev Gorodinski. Validation in Domain-Driven Design (DDD)**
[*http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/*](http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/)</span></span>

-   <span data-ttu-id="76cc9-162">**Colin Jack：領域模型驗證**
    [*http://colinjack.blogspot.com/2008/03/domain-model-validation.html*](http://colinjack.blogspot.com/2008/03/domain-model-validation.html)</span><span class="sxs-lookup"><span data-stu-id="76cc9-162">**Colin Jack. Domain Model Validation**
[*http://colinjack.blogspot.com/2008/03/domain-model-validation.html*](http://colinjack.blogspot.com/2008/03/domain-model-validation.html)</span></span>

-   <span data-ttu-id="76cc9-163">**Jimmy Bogard：DDD 世界中的驗證**
    [*https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/*](https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/)</span><span class="sxs-lookup"><span data-stu-id="76cc9-163">**Jimmy Bogard. Validation in a DDD world**
[*https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/*](https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="76cc9-164">[上一頁](enumeration-classes-over-enum-types.md)
[下一頁](client-side-validation.md)</span><span class="sxs-lookup"><span data-stu-id="76cc9-164">[Previous](enumeration-classes-over-enum-types.md)
[Next](client-side-validation.md)</span></span>
