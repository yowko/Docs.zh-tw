---
title: 設計領域模型層中的驗證
description: .NET 微服務：容器化 .NET 應用程式的架構 | 了解領域模型驗證的關鍵概念。
ms.date: 10/08/2018
ms.openlocfilehash: 18c8350d0bf514a8a01a210a2a2a6d8f73317580
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94820627"
---
# <a name="design-validations-in-the-domain-model-layer"></a><span data-ttu-id="e294c-103">設計領域模型層中的驗證</span><span class="sxs-lookup"><span data-stu-id="e294c-103">Design validations in the domain model layer</span></span>

<span data-ttu-id="e294c-104">在 DDD 中，驗證規則可以視為非變異值。</span><span class="sxs-lookup"><span data-stu-id="e294c-104">In DDD, validation rules can be thought as invariants.</span></span> <span data-ttu-id="e294c-105">彙總的主要責任是跨該彙總內所有實體的狀態變更來強制執行非變異值。</span><span class="sxs-lookup"><span data-stu-id="e294c-105">The main responsibility of an aggregate is to enforce invariants across state changes for all the entities within that aggregate.</span></span>

<span data-ttu-id="e294c-106">領域實體應該一律是有效的實體。</span><span class="sxs-lookup"><span data-stu-id="e294c-106">Domain entities should always be valid entities.</span></span> <span data-ttu-id="e294c-107">一律應該為 true 的物件會有特定數目的非變異值。</span><span class="sxs-lookup"><span data-stu-id="e294c-107">There are a certain number of invariants for an object that should always be true.</span></span> <span data-ttu-id="e294c-108">例如，訂單項目物件一律必須要有必須是正整數的數量，以及發行項名稱和價格。</span><span class="sxs-lookup"><span data-stu-id="e294c-108">For example, an order item object always has to have a quantity that must be a positive integer, plus an article name and price.</span></span> <span data-ttu-id="e294c-109">因此，非變異值強制執行負責領域實體 (特別是彙總根)，而且存在的實體物件應該有效。</span><span class="sxs-lookup"><span data-stu-id="e294c-109">Therefore, invariants enforcement is the responsibility of the domain entities (especially of the aggregate root) and an entity object should not be able to exist without being valid.</span></span> <span data-ttu-id="e294c-110">非變異值規則只會表示為合約，而且會在違反時引發例外狀況或通知。</span><span class="sxs-lookup"><span data-stu-id="e294c-110">Invariant rules are simply expressed as contracts, and exceptions or notifications are raised when they are violated.</span></span>

<span data-ttu-id="e294c-111">背後原因是物件處於絕對不應該處於的狀態而發生許多 Bug。</span><span class="sxs-lookup"><span data-stu-id="e294c-111">The reasoning behind this is that many bugs occur because objects are in a state they should never have been in.</span></span>

<span data-ttu-id="e294c-112">建議我們現在具有採用 UserProfile 的 SendUserCreationEmailService ... 如何合理化 Name 不是 Null 的該服務？</span><span class="sxs-lookup"><span data-stu-id="e294c-112">Let's propose we now have a SendUserCreationEmailService that takes a UserProfile ... how can we rationalize in that service that Name is not null?</span></span> <span data-ttu-id="e294c-113">要再次確認嗎？</span><span class="sxs-lookup"><span data-stu-id="e294c-113">Do we check it again?</span></span> <span data-ttu-id="e294c-114">或者，更可能 ... 您不需要檢查並且「獲得最佳結果」- 您希望有人先進行驗證，再將它傳送給您。</span><span class="sxs-lookup"><span data-stu-id="e294c-114">Or more likely ... you just don't bother to check and "hope for the best"—you hope that someone bothered to validate it before sending it to you.</span></span> <span data-ttu-id="e294c-115">當然，使用 TDD，我們應該撰寫的其中一個第一個測試就是將應該會引發錯誤的 Null 名稱傳送給客戶。</span><span class="sxs-lookup"><span data-stu-id="e294c-115">Of course, using TDD one of the first tests we should be writing is that if I send a customer with a null name that it should raise an error.</span></span> <span data-ttu-id="e294c-116">但是一旦我們開始撰寫這類測試之後，我們就能實現 .。。「如果我們永遠不允許名稱為 null，就不會有這些測試」。</span><span class="sxs-lookup"><span data-stu-id="e294c-116">But once we start writing these kinds of tests over and over again we realize ... "wait if we never allowed name to become null we wouldn't have all of these tests".</span></span>

## <a name="implement-validations-in-the-domain-model-layer"></a><span data-ttu-id="e294c-117">實作領域模型層中的驗證</span><span class="sxs-lookup"><span data-stu-id="e294c-117">Implement validations in the domain model layer</span></span>

<span data-ttu-id="e294c-118">通常是在領域實體建構函式或可更新實體的方法中實作驗證。</span><span class="sxs-lookup"><span data-stu-id="e294c-118">Validations are usually implemented in domain entity constructors or in methods that can update the entity.</span></span> <span data-ttu-id="e294c-119">有多種方式可以實作驗證，例如驗證資料，以及在驗證失敗時引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e294c-119">There are multiple ways to implement validations, such as verifying data and raising exceptions if the validation fails.</span></span> <span data-ttu-id="e294c-120">另外還有更進階模式，例如使用規格模式進行驗證，以及使用通知模式傳回錯誤集合，而不是傳回每個驗證所發生的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e294c-120">There are also more advanced patterns such as using the Specification pattern for validations, and the Notification pattern to return a collection of errors instead of returning an exception for each validation as it occurs.</span></span>

### <a name="validate-conditions-and-throw-exceptions"></a><span data-ttu-id="e294c-121">驗證條件並擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="e294c-121">Validate conditions and throw exceptions</span></span>

<span data-ttu-id="e294c-122">下列程式碼範例透過引發例外狀況來示範領域實體中的最簡單驗證方法。</span><span class="sxs-lookup"><span data-stu-id="e294c-122">The following code example shows the simplest approach to validation in a domain entity by raising an exception.</span></span> <span data-ttu-id="e294c-123">在本節結尾的參考資料表中，您可以看到根據我們先前討論過之模式的更進階實作連結。</span><span class="sxs-lookup"><span data-stu-id="e294c-123">In the references table at the end of this section you can see links to more advanced implementations based on the patterns we have discussed previously.</span></span>

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

<span data-ttu-id="e294c-124">更好的範例會示範需要確定內部狀態未變更，或方法的所有變化。</span><span class="sxs-lookup"><span data-stu-id="e294c-124">A better example would demonstrate the need to ensure that either the internal state did not change, or that all the mutations for a method occurred.</span></span> <span data-ttu-id="e294c-125">例如，下列實作會讓物件處於無效狀態：</span><span class="sxs-lookup"><span data-stu-id="e294c-125">For example, the following implementation would leave the object in an invalid state:</span></span>

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

<span data-ttu-id="e294c-126">如果狀態的值無效，則已經變更第一個地址行和縣 (市)。</span><span class="sxs-lookup"><span data-stu-id="e294c-126">If the value of the state is invalid, the first address line and the city have already been changed.</span></span> <span data-ttu-id="e294c-127">這可能會讓地址無效。</span><span class="sxs-lookup"><span data-stu-id="e294c-127">That might make the address invalid.</span></span>

<span data-ttu-id="e294c-128">您可以在實體的函式中使用類似的方法，並引發例外狀況，以確定實體在建立之後是有效的。</span><span class="sxs-lookup"><span data-stu-id="e294c-128">A similar approach can be used in the entity's constructor, raising an exception to make sure that the entity is valid once it is created.</span></span>

### <a name="use-validation-attributes-in-the-model-based-on-data-annotations"></a><span data-ttu-id="e294c-129">在以資料註解為基礎的模型中使用驗證屬性</span><span class="sxs-lookup"><span data-stu-id="e294c-129">Use validation attributes in the model based on data annotations</span></span>

<span data-ttu-id="e294c-130">資料註解與 Required 或 MaxLength 屬性相似，可用來設定 EF Core 資料庫欄位屬性 (如[資料表對應](infrastructure-persistence-layer-implementation-entity-framework-core.md#table-mapping)一節中詳細資料所述)，但與 .NET Framework 中 EF 4.x 以來的版本不同，它們[已不再能用於 EF Core 中的實體驗證](https://github.com/dotnet/efcore/issues/3680) (<xref:System.ComponentModel.DataAnnotations.IValidatableObject.Validate%2A?displayProperty=nameWithType> 方法也一樣)。</span><span class="sxs-lookup"><span data-stu-id="e294c-130">Data annotations, like the Required or MaxLength attributes, can be used to configure EF Core database field properties, as explained in detail in the [Table mapping](infrastructure-persistence-layer-implementation-entity-framework-core.md#table-mapping) section, but [they no longer work for entity validation in EF Core](https://github.com/dotnet/efcore/issues/3680) (neither does the <xref:System.ComponentModel.DataAnnotations.IValidatableObject.Validate%2A?displayProperty=nameWithType> method), as they have done since EF 4.x in .NET Framework.</span></span>

<span data-ttu-id="e294c-131">在模型系結 <xref:System.ComponentModel.DataAnnotations.IValidatableObject> 期間，資料批註和介面仍可用於模型系結（如往常一樣），但該模型的目的是 ViewModel 或 DTO，而這是 MVC 或 API 考慮不是領域模型的考慮。</span><span class="sxs-lookup"><span data-stu-id="e294c-131">Data annotations and the <xref:System.ComponentModel.DataAnnotations.IValidatableObject> interface can still be used for model validation during model binding, prior to the controller's actions invocation as usual, but that model is meant to be a ViewModel or DTO and that's an MVC or API concern not a domain model concern.</span></span>

<span data-ttu-id="e294c-132">在釐清概念差異之後，若您的動作會接受實體類別物件參數 (不建議)，則您仍然可以在實體類別中使用資料註解和 `IValidatableObject` 進行驗證。</span><span class="sxs-lookup"><span data-stu-id="e294c-132">Having made the conceptual difference clear, you can still use data annotations and `IValidatableObject` in the entity class for validation, if your actions receive an entity class object parameter, which is not recommended.</span></span> <span data-ttu-id="e294c-133">在這種情況下，驗證將會在模型系結時發生，只要叫用動作，您就可以檢查控制器的 ModelState IsValid 屬性來檢查結果，但同樣地，它會發生在控制器中，而不是在保存 DbCoNtext 中的實體物件之前（因為 EF 4.x 之後所做的）。</span><span class="sxs-lookup"><span data-stu-id="e294c-133">In that case, validation will occur upon model binding, just before invoking the action and you can check the controller's ModelState.IsValid property to check the result, but then again, it happens in the controller, not before persisting the entity object in the DbContext, as it had done since EF 4.x.</span></span>

<span data-ttu-id="e294c-134">您仍然可以藉 `IValidatableObject.Validate` 由覆寫 DbCoNtext 的 SaveChanges 方法，在實體類別中使用資料批註和方法來執行自訂驗證。</span><span class="sxs-lookup"><span data-stu-id="e294c-134">You can still implement custom validation in the entity class using data annotations and the `IValidatableObject.Validate` method, by overriding the DbContext's SaveChanges method.</span></span>

<span data-ttu-id="e294c-135">您可以在 [GitHub 上的這個留言](https://github.com/dotnet/efcore/issues/3680#issuecomment-155502539)裡看到驗證 `IValidatableObject` 實體的範例實作。</span><span class="sxs-lookup"><span data-stu-id="e294c-135">You can see a sample implementation for validating `IValidatableObject` entities in [this comment on GitHub](https://github.com/dotnet/efcore/issues/3680#issuecomment-155502539).</span></span> <span data-ttu-id="e294c-136">該範例不會執行以屬性為基礎的驗證，但在相同的覆寫中使用反映應該很容易執行。</span><span class="sxs-lookup"><span data-stu-id="e294c-136">That sample doesn't do attribute-based validations, but they should be easy to implement using reflection in the same override.</span></span>

<span data-ttu-id="e294c-137">不過，從 DDD 觀點來看，網域模型最適合用來在實體的行為方法中使用例外狀況，或藉由執行規格和通知模式來強制執行驗證規則。</span><span class="sxs-lookup"><span data-stu-id="e294c-137">However, from a DDD point of view, the domain model is best kept lean with the use of exceptions in your entity's behavior methods, or by implementing the Specification and Notification patterns to enforce validation rules.</span></span>

<span data-ttu-id="e294c-138">它可以合理地使用接受輸入之 ViewModel 類別 (而非領域實體) 中應用程式層的資料註解，以允許 UI 層內的模型驗證。</span><span class="sxs-lookup"><span data-stu-id="e294c-138">It can make sense to use data annotations at the application layer in ViewModel classes (instead of domain entities) that will accept input, to allow for model validation within the UI layer.</span></span> <span data-ttu-id="e294c-139">不過，在領域模型內，這不應該排除驗證。</span><span class="sxs-lookup"><span data-stu-id="e294c-139">However, this should not be done at the exclusion of validation within the domain model.</span></span>

### <a name="validate-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a><span data-ttu-id="e294c-140">實作規格模式和通知模式來驗證實體</span><span class="sxs-lookup"><span data-stu-id="e294c-140">Validate entities by implementing the Specification pattern and the Notification pattern</span></span>

<span data-ttu-id="e294c-141">最後，在領域模型中實作驗證的更複雜方法，是一起實作規格模式與通知模式，如稍後列出的一些其他資源所述。</span><span class="sxs-lookup"><span data-stu-id="e294c-141">Finally, a more elaborate approach to implementing validations in the domain model is by implementing the Specification pattern in conjunction with the Notification pattern, as explained in some of the additional resources listed later.</span></span>

<span data-ttu-id="e294c-142">值得一提的是，您也可以只使用其中一種模式；例如，使用 control 陳述式手動驗證，但使用通知模式來堆疊和傳回驗證錯誤清單。</span><span class="sxs-lookup"><span data-stu-id="e294c-142">It is worth mentioning that you can also use just one of those patterns—for example, validating manually with control statements, but using the Notification pattern to stack and return a list of validation errors.</span></span>

### <a name="use-deferred-validation-in-the-domain"></a><span data-ttu-id="e294c-143">在領域中使用延後驗證</span><span class="sxs-lookup"><span data-stu-id="e294c-143">Use deferred validation in the domain</span></span>

<span data-ttu-id="e294c-144">有各種方法來處理領域中的延後驗證。</span><span class="sxs-lookup"><span data-stu-id="e294c-144">There are various approaches to deal with deferred validations in the domain.</span></span> <span data-ttu-id="e294c-145">Vaughn Vernon 會在其 [Implementing Domain-Driven Design](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577) (實作領域驅動設計) 書籍的驗證小節中討論這些方法。</span><span class="sxs-lookup"><span data-stu-id="e294c-145">In his book [Implementing Domain-Driven Design](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon discusses these in the section on validation.</span></span>

### <a name="two-step-validation"></a><span data-ttu-id="e294c-146">兩步驟驗證</span><span class="sxs-lookup"><span data-stu-id="e294c-146">Two-step validation</span></span>

<span data-ttu-id="e294c-147">也請考慮兩步驟驗證。</span><span class="sxs-lookup"><span data-stu-id="e294c-147">Also consider two-step validation.</span></span> <span data-ttu-id="e294c-148">在命令資料傳輸物件 (DTO) 上使用欄位層級驗證，以及在實體內部使用領域層級驗證。</span><span class="sxs-lookup"><span data-stu-id="e294c-148">Use field-level validation on your command Data Transfer Objects (DTOs) and domain-level validation inside your entities.</span></span> <span data-ttu-id="e294c-149">做法是傳回結果物件而不是例外狀況，以更輕鬆地處理驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="e294c-149">You can do this by returning a result object instead of exceptions in order to make it easier to deal with the validation errors.</span></span>

<span data-ttu-id="e294c-150">例如，使用具有資料註解的欄位驗證，就不會有重複的驗證定義。</span><span class="sxs-lookup"><span data-stu-id="e294c-150">Using field validation with data annotations, for example, you do not duplicate the validation definition.</span></span> <span data-ttu-id="e294c-151">不過，如果是 DTO，則執行可以是伺服器端和用戶端 (例如，命令和 ViewModel)。</span><span class="sxs-lookup"><span data-stu-id="e294c-151">The execution, though, can be both server-side and client-side in the case of DTOs (commands and ViewModels, for instance).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="e294c-152">其他資源</span><span class="sxs-lookup"><span data-stu-id="e294c-152">Additional resources</span></span>

- <span data-ttu-id="e294c-153">**Rachel Appel。ASP.NET Core MVC 中的模型驗證簡介** </span><span class="sxs-lookup"><span data-stu-id="e294c-153">**Rachel Appel. Introduction to model validation in ASP.NET Core MVC** </span></span>\
  <https://docs.microsoft.com/aspnet/core/mvc/models/validation>

- <span data-ttu-id="e294c-154">**Rick Anderson。新增驗證** </span><span class="sxs-lookup"><span data-stu-id="e294c-154">**Rick Anderson. Adding validation** </span></span>\
  <https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation>

- <span data-ttu-id="e294c-155">**聖馬丁 Fowler。在驗證中將擲回例外狀況取代為通知** </span><span class="sxs-lookup"><span data-stu-id="e294c-155">**Martin Fowler. Replacing Throwing Exceptions with Notification in Validations** </span></span>\
  <https://martinfowler.com/articles/replaceThrowWithNotification.html>

- <span data-ttu-id="e294c-156">**規格和通知模式** </span><span class="sxs-lookup"><span data-stu-id="e294c-156">**Specification and Notification Patterns** </span></span>\
  <https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns>

- <span data-ttu-id="e294c-157">**Lev Gorodinski.Domain-Driven 設計 (DDD) 中的驗證** </span><span class="sxs-lookup"><span data-stu-id="e294c-157">**Lev Gorodinski. Validation in Domain-Driven Design (DDD)** </span></span>\
  <http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/>

- <span data-ttu-id="e294c-158">**Colin 插座。領域模型驗證** </span><span class="sxs-lookup"><span data-stu-id="e294c-158">**Colin Jack. Domain Model Validation** </span></span>\
  <https://colinjack.blogspot.com/2008/03/domain-model-validation.html>

- <span data-ttu-id="e294c-159">**Jimmy Bogard。DDD 世界中的驗證** </span><span class="sxs-lookup"><span data-stu-id="e294c-159">**Jimmy Bogard. Validation in a DDD world** </span></span>\
  <https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/>

> [!div class="step-by-step"]
> <span data-ttu-id="e294c-160">[上一個](enumeration-classes-over-enum-types.md) 
> [下一步](client-side-validation.md)</span><span class="sxs-lookup"><span data-stu-id="e294c-160">[Previous](enumeration-classes-over-enum-types.md)
[Next](client-side-validation.md)</span></span>
