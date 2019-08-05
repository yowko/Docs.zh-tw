---
title: 設計領域模型層中的驗證
description: .NET 微服務：容器化 .NET 應用程式的架構 | 了解領域模型驗證的關鍵概念。
ms.date: 10/08/2018
ms.openlocfilehash: 1d3196d2130df33969ed231bccfe0fc6f0af2ad8
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68674245"
---
# <a name="design-validations-in-the-domain-model-layer"></a><span data-ttu-id="d8026-103">設計領域模型層中的驗證</span><span class="sxs-lookup"><span data-stu-id="d8026-103">Design validations in the domain model layer</span></span>

<span data-ttu-id="d8026-104">在 DDD 中，驗證規則可以視為非變異值。</span><span class="sxs-lookup"><span data-stu-id="d8026-104">In DDD, validation rules can be thought as invariants.</span></span> <span data-ttu-id="d8026-105">彙總的主要責任是跨該彙總內所有實體的狀態變更來強制執行非變異值。</span><span class="sxs-lookup"><span data-stu-id="d8026-105">The main responsibility of an aggregate is to enforce invariants across state changes for all the entities within that aggregate.</span></span>

<span data-ttu-id="d8026-106">領域實體應該一律是有效的實體。</span><span class="sxs-lookup"><span data-stu-id="d8026-106">Domain entities should always be valid entities.</span></span> <span data-ttu-id="d8026-107">一律應該為 true 的物件會有特定數目的非變異值。</span><span class="sxs-lookup"><span data-stu-id="d8026-107">There are a certain number of invariants for an object that should always be true.</span></span> <span data-ttu-id="d8026-108">例如，訂單項目物件一律必須要有必須是正整數的數量，以及發行項名稱和價格。</span><span class="sxs-lookup"><span data-stu-id="d8026-108">For example, an order item object always has to have a quantity that must be a positive integer, plus an article name and price.</span></span> <span data-ttu-id="d8026-109">因此，非變異值強制執行負責領域實體 (特別是彙總根)，而且存在的實體物件應該有效。</span><span class="sxs-lookup"><span data-stu-id="d8026-109">Therefore, invariants enforcement is the responsibility of the domain entities (especially of the aggregate root) and an entity object should not be able to exist without being valid.</span></span> <span data-ttu-id="d8026-110">非變異值規則只會表示為合約，而且會在違反時引發例外狀況或通知。</span><span class="sxs-lookup"><span data-stu-id="d8026-110">Invariant rules are simply expressed as contracts, and exceptions or notifications are raised when they are violated.</span></span>

<span data-ttu-id="d8026-111">背後原因是物件處於絕對不應該處於的狀態而發生許多 Bug。</span><span class="sxs-lookup"><span data-stu-id="d8026-111">The reasoning behind this is that many bugs occur because objects are in a state they should never have been in.</span></span> <span data-ttu-id="d8026-112">下列是 Greg Young 在[線上討論](https://jeffreypalermo.com/2009/05/the-fallacy-of-the-always-valid-entity/)中的合理解釋：</span><span class="sxs-lookup"><span data-stu-id="d8026-112">The following is a good explanation from Greg Young in an [online discussion](https://jeffreypalermo.com/2009/05/the-fallacy-of-the-always-valid-entity/):</span></span>

<span data-ttu-id="d8026-113">建議我們現在具有採用 UserProfile 的 SendUserCreationEmailService ... 如何合理化 Name 不是 Null 的該服務？</span><span class="sxs-lookup"><span data-stu-id="d8026-113">Let's propose we now have a SendUserCreationEmailService that takes a UserProfile ... how can we rationalize in that service that Name is not null?</span></span> <span data-ttu-id="d8026-114">要再次確認嗎？</span><span class="sxs-lookup"><span data-stu-id="d8026-114">Do we check it again?</span></span> <span data-ttu-id="d8026-115">或者，更可能 ... 您不需要檢查並且「獲得最佳結果」- 您希望有人先進行驗證，再將它傳送給您。</span><span class="sxs-lookup"><span data-stu-id="d8026-115">Or more likely ... you just don't bother to check and "hope for the best"—you hope that someone bothered to validate it before sending it to you.</span></span> <span data-ttu-id="d8026-116">當然，使用 TDD，我們應該撰寫的其中一個第一個測試就是將應該會引發錯誤的 Null 名稱傳送給客戶。</span><span class="sxs-lookup"><span data-stu-id="d8026-116">Of course, using TDD one of the first tests we should be writing is that if I send a customer with a null name that it should raise an error.</span></span> <span data-ttu-id="d8026-117">但是，當我們開始不斷地撰寫這些類型的測試時了解：「等一下，如果我們永遠不允許名稱變成 Null，就不會有所有這些測試」。</span><span class="sxs-lookup"><span data-stu-id="d8026-117">But once we start writing these kinds of tests over and over again we realize ... "wait if we never allowed name to become null we wouldn't have all of these tests"</span></span>

## <a name="implement-validations-in-the-domain-model-layer"></a><span data-ttu-id="d8026-118">實作領域模型層中的驗證</span><span class="sxs-lookup"><span data-stu-id="d8026-118">Implement validations in the domain model layer</span></span>

<span data-ttu-id="d8026-119">通常是在領域實體建構函式或可更新實體的方法中實作驗證。</span><span class="sxs-lookup"><span data-stu-id="d8026-119">Validations are usually implemented in domain entity constructors or in methods that can update the entity.</span></span> <span data-ttu-id="d8026-120">有多種方式可以實作驗證，例如驗證資料，以及在驗證失敗時引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d8026-120">There are multiple ways to implement validations, such as verifying data and raising exceptions if the validation fails.</span></span> <span data-ttu-id="d8026-121">另外還有更進階模式，例如使用規格模式進行驗證，以及使用通知模式傳回錯誤集合，而不是傳回每個驗證所發生的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d8026-121">There are also more advanced patterns such as using the Specification pattern for validations, and the Notification pattern to return a collection of errors instead of returning an exception for each validation as it occurs.</span></span>

### <a name="validate-conditions-and-throw-exceptions"></a><span data-ttu-id="d8026-122">驗證條件並擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="d8026-122">Validate conditions and throw exceptions</span></span>

<span data-ttu-id="d8026-123">下列程式碼範例透過引發例外狀況來示範領域實體中的最簡單驗證方法。</span><span class="sxs-lookup"><span data-stu-id="d8026-123">The following code example shows the simplest approach to validation in a domain entity by raising an exception.</span></span> <span data-ttu-id="d8026-124">在本節結尾的參考資料表中，您可以看到根據我們先前討論過之模式的更進階實作連結。</span><span class="sxs-lookup"><span data-stu-id="d8026-124">In the references table at the end of this section you can see links to more advanced implementations based on the patterns we have discussed previously.</span></span>

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

<span data-ttu-id="d8026-125">更好的範例會示範需要確定內部狀態未變更，或方法的所有變化。</span><span class="sxs-lookup"><span data-stu-id="d8026-125">A better example would demonstrate the need to ensure that either the internal state did not change, or that all the mutations for a method occurred.</span></span> <span data-ttu-id="d8026-126">例如，下列實作會讓物件處於無效狀態：</span><span class="sxs-lookup"><span data-stu-id="d8026-126">For example, the following implementation would leave the object in an invalid state:</span></span>

```csharp
public void SetAddress(string line1, string line2,
    string city, string state, int zip)
{
    _shippingAddress.line1 = line1 ?? throw new ...
    _shippingAddress.line2 = line2;
    _shippingAddress.city = city ?? throw new ...
    _shippingAddress.state = (IsValid(state) ? state : throw new …);
}
```

<span data-ttu-id="d8026-127">如果狀態的值無效，則已經變更第一個地址行和縣 (市)。</span><span class="sxs-lookup"><span data-stu-id="d8026-127">If the value of the state is invalid, the first address line and the city have already been changed.</span></span> <span data-ttu-id="d8026-128">這可能會讓地址無效。</span><span class="sxs-lookup"><span data-stu-id="d8026-128">That might make the address invalid.</span></span>

<span data-ttu-id="d8026-129">類似的方法可以用於實體的建構函式，即引發例外狀況來確定實體在建立之後有效。</span><span class="sxs-lookup"><span data-stu-id="d8026-129">A similar approach can be used in the entity’s constructor, raising an exception to make sure that the entity is valid once it is created.</span></span>

### <a name="use-validation-attributes-in-the-model-based-on-data-annotations"></a><span data-ttu-id="d8026-130">在以資料註解為基礎的模型中使用驗證屬性</span><span class="sxs-lookup"><span data-stu-id="d8026-130">Use validation attributes in the model based on data annotations</span></span>

<span data-ttu-id="d8026-131">資料註解與 Required 或 MaxLength 屬性相似，可用來設定 EF Core 資料庫欄位屬性 (如[資料表對應](infrastructure-persistence-layer-implemenation-entity-framework-core.md#table-mapping)一節中詳細資料所述)，但與 .NET Framework 中 EF 4.x 以來的版本不同，它們[已不再能用於 EF Core 中的實體驗證](https://github.com/aspnet/EntityFrameworkCore/issues/3680) (<xref:System.ComponentModel.DataAnnotations.IValidatableObject.Validate%2A?displayProperty=nameWithType> 方法也一樣)。</span><span class="sxs-lookup"><span data-stu-id="d8026-131">Data annotations, like the Required or MaxLength attributes, can be used to configure EF Core database field properties, as explained in detail in the [Table mapping](infrastructure-persistence-layer-implemenation-entity-framework-core.md#table-mapping) section, but [they no longer work for entity validation in EF Core](https://github.com/aspnet/EntityFrameworkCore/issues/3680) (neither does the <xref:System.ComponentModel.DataAnnotations.IValidatableObject.Validate%2A?displayProperty=nameWithType> method), as they have done since EF 4.x in .NET Framework.</span></span>

<span data-ttu-id="d8026-132">資料註解和 <xref:System.ComponentModel.DataAnnotations.IValidatableObject> 介面與過去相同，仍然可以在控制器的動作叫用前，於模型繫結期間用於模型驗證，但該模型應用來作為 ViewModel 或 DTO。這是 MVC 或 API 的考量事項，而非領域模型的考量事項。</span><span class="sxs-lookup"><span data-stu-id="d8026-132">Data annotations and the <xref:System.ComponentModel.DataAnnotations.IValidatableObject> interface can still be used for model validation during model binding, prior to the controller’s actions invocation as usual, but that model is meant to be a ViewModel or DTO and that’s an MVC or API concern not a domain model concern.</span></span>

<span data-ttu-id="d8026-133">在釐清概念差異之後，若您的動作會接受實體類別物件參數 (不建議)，則您仍然可以在實體類別中使用資料註解和 `IValidatableObject` 進行驗證。</span><span class="sxs-lookup"><span data-stu-id="d8026-133">Having made the conceptual difference clear, you can still use data annotations and `IValidatableObject` in the entity class for validation, if your actions receive an entity class object parameter, which is not recommended.</span></span> <span data-ttu-id="d8026-134">在該情況下，驗證會在叫用動作前，於模型繫結時進行，且您可以檢查控制器的 ModelState.IsValid 屬性來檢查結果，但同樣的，與 EF 4.x 以來的版本不同，它會在控制器中發生，而非在將實體物件保存到 DbContext 前發生。</span><span class="sxs-lookup"><span data-stu-id="d8026-134">In that case, validation will occur upon model binding, just before invoking the action and you can check the controller’s ModelState.IsValid property to check the result, but then again, it happens in the controller, not before persisting the entity object in the DbContext, as it had done since EF 4.x.</span></span>

<span data-ttu-id="d8026-135">您仍然可以在實體類別中使用資料註解和 `IValidatableObject.Validate` 方法，透過覆寫 DbContext 的 SaveChanges 方法來實作自訂驗證。</span><span class="sxs-lookup"><span data-stu-id="d8026-135">You can still implement custom validation in the entity class using data annotations and the `IValidatableObject.Validate` method, by overriding the DbContext’s SaveChanges method.</span></span>

<span data-ttu-id="d8026-136">您可以在 [GitHub 上的這個留言](https://github.com/aspnet/EntityFrameworkCore/issues/3680#issuecomment-155502539)裡看到驗證 `IValidatableObject` 實體的範例實作。</span><span class="sxs-lookup"><span data-stu-id="d8026-136">You can see a sample implementation for validating `IValidatableObject` entities in [this comment on GitHub](https://github.com/aspnet/EntityFrameworkCore/issues/3680#issuecomment-155502539).</span></span> <span data-ttu-id="d8026-137">該範例不會進行以屬性為基礎的驗證，但它們可以在相同覆寫中，使用反映來輕鬆實作。</span><span class="sxs-lookup"><span data-stu-id="d8026-137">That sample doesn’t do attribute-based validations, but they should be easy to implement using reflection in the same override.</span></span>

<span data-ttu-id="d8026-138">不過，從 DDD 觀點，領域模型會妥善使用您實體行為方法中的例外狀況，或藉由實作規格和通知模式來強制執行驗證規則。</span><span class="sxs-lookup"><span data-stu-id="d8026-138">However, from a DDD point of view, the domain model is best kept lean with the use of exceptions in your entity’s behavior methods, or by implementing the Specification and Notification patterns to enforce validation rules.</span></span>

<span data-ttu-id="d8026-139">它可以合理地使用接受輸入之 ViewModel 類別 (而非領域實體) 中應用程式層的資料註解，以允許 UI 層內的模型驗證。</span><span class="sxs-lookup"><span data-stu-id="d8026-139">It can make sense to use data annotations at the application layer in ViewModel classes (instead of domain entities) that will accept input, to allow for model validation within the UI layer.</span></span> <span data-ttu-id="d8026-140">不過，在領域模型內，這不應該排除驗證。</span><span class="sxs-lookup"><span data-stu-id="d8026-140">However, this should not be done at the exclusion of validation within the domain model.</span></span>

### <a name="validate-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a><span data-ttu-id="d8026-141">實作規格模式和通知模式來驗證實體</span><span class="sxs-lookup"><span data-stu-id="d8026-141">Validate entities by implementing the Specification pattern and the Notification pattern</span></span>

<span data-ttu-id="d8026-142">最後，在領域模型中實作驗證的更複雜方法，是一起實作規格模式與通知模式，如稍後列出的一些其他資源所述。</span><span class="sxs-lookup"><span data-stu-id="d8026-142">Finally, a more elaborate approach to implementing validations in the domain model is by implementing the Specification pattern in conjunction with the Notification pattern, as explained in some of the additional resources listed later.</span></span>

<span data-ttu-id="d8026-143">值得一提的是，您也可以只使用其中一種模式；例如，使用 control 陳述式手動驗證，但使用通知模式來堆疊和傳回驗證錯誤清單。</span><span class="sxs-lookup"><span data-stu-id="d8026-143">It is worth mentioning that you can also use just one of those patterns—for example, validating manually with control statements, but using the Notification pattern to stack and return a list of validation errors.</span></span>

### <a name="use-deferred-validation-in-the-domain"></a><span data-ttu-id="d8026-144">在領域中使用延後驗證</span><span class="sxs-lookup"><span data-stu-id="d8026-144">Use deferred validation in the domain</span></span>

<span data-ttu-id="d8026-145">有各種方法來處理領域中的延後驗證。</span><span class="sxs-lookup"><span data-stu-id="d8026-145">There are various approaches to deal with deferred validations in the domain.</span></span> <span data-ttu-id="d8026-146">Vaughn Vernon 會在其 [Implementing Domain-Driven Design](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577) (實作領域驅動設計) 書籍的驗證小節中討論這些方法。</span><span class="sxs-lookup"><span data-stu-id="d8026-146">In his book [Implementing Domain-Driven Design](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon discusses these in the section on validation.</span></span>

### <a name="two-step-validation"></a><span data-ttu-id="d8026-147">兩步驟驗證</span><span class="sxs-lookup"><span data-stu-id="d8026-147">Two-step validation</span></span>

<span data-ttu-id="d8026-148">也請考慮兩步驟驗證。</span><span class="sxs-lookup"><span data-stu-id="d8026-148">Also consider two-step validation.</span></span> <span data-ttu-id="d8026-149">在命令資料傳輸物件 (DTO) 上使用欄位層級驗證，以及在實體內部使用領域層級驗證。</span><span class="sxs-lookup"><span data-stu-id="d8026-149">Use field-level validation on your command Data Transfer Objects (DTOs) and domain-level validation inside your entities.</span></span> <span data-ttu-id="d8026-150">做法是傳回結果物件而不是例外狀況，以更輕鬆地處理驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="d8026-150">You can do this by returning a result object instead of exceptions in order to make it easier to deal with the validation errors.</span></span>

<span data-ttu-id="d8026-151">例如，使用具有資料註解的欄位驗證，就不會有重複的驗證定義。</span><span class="sxs-lookup"><span data-stu-id="d8026-151">Using field validation with data annotations, for example, you do not duplicate the validation definition.</span></span> <span data-ttu-id="d8026-152">不過，如果是 DTO，則執行可以是伺服器端和用戶端 (例如，命令和 ViewModel)。</span><span class="sxs-lookup"><span data-stu-id="d8026-152">The execution, though, can be both server-side and client-side in the case of DTOs (commands and ViewModels, for instance).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="d8026-153">其他資源</span><span class="sxs-lookup"><span data-stu-id="d8026-153">Additional resources</span></span>

- <span data-ttu-id="d8026-154">**Rachel Appel：ASP.NET Core MVC 中的模型驗證簡介** </span><span class="sxs-lookup"><span data-stu-id="d8026-154">**Rachel Appel. Introduction to model validation in ASP.NET Core MVC** </span></span>\
  <https://docs.microsoft.com/aspnet/core/mvc/models/validation>

- <span data-ttu-id="d8026-155">**Rick Anderson，新增驗證** </span><span class="sxs-lookup"><span data-stu-id="d8026-155">**Rick Anderson. Adding validation** </span></span>\
  <https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation>

- <span data-ttu-id="d8026-156">**Martin Fowler：在驗證中將擲回例外狀況取代為通知** </span><span class="sxs-lookup"><span data-stu-id="d8026-156">**Martin Fowler. Replacing Throwing Exceptions with Notification in Validations** </span></span>\
  <https://martinfowler.com/articles/replaceThrowWithNotification.html>

- <span data-ttu-id="d8026-157">**規格和通知模式** </span><span class="sxs-lookup"><span data-stu-id="d8026-157">**Specification and Notification Patterns** </span></span>\
  <https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns>

- <span data-ttu-id="d8026-158">**Lev Gorodinski：網域驅動設計 (DDD) 中的驗證** </span><span class="sxs-lookup"><span data-stu-id="d8026-158">**Lev Gorodinski. Validation in Domain-Driven Design (DDD)** </span></span>\
  <http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/>

- <span data-ttu-id="d8026-159">**Colin Jack：領域模型驗證** </span><span class="sxs-lookup"><span data-stu-id="d8026-159">**Colin Jack. Domain Model Validation** </span></span>\
  <https://colinjack.blogspot.com/2008/03/domain-model-validation.html>

- <span data-ttu-id="d8026-160">**Jimmy Bogard：DDD 世界中的驗證** </span><span class="sxs-lookup"><span data-stu-id="d8026-160">**Jimmy Bogard. Validation in a DDD world** </span></span>\
  <https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/>

> [!div class="step-by-step"]
> <span data-ttu-id="d8026-161">[上一頁](enumeration-classes-over-enum-types.md)
> [下一頁](client-side-validation.md)</span><span class="sxs-lookup"><span data-stu-id="d8026-161">[Previous](enumeration-classes-over-enum-types.md)
[Next](client-side-validation.md)</span></span>
