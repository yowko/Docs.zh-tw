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
# <a name="designing-validations-in-the-domain-model-layer"></a>設計網域模型層中的驗證

在 DDD，驗證規則可以視為非變異值。 彙總的主要的責任是跨彙總內的所有實體的狀態變更強制執行非變異值。

網域實體應該一律是有效的實體。 有非變異值應永遠為 true 的物件數目。 例如，訂單項目物件一律必須要有必須是正整數，加上一個發行項名稱和價格的數量。 因此，非變異項目強制負責 （特別是彙總的根目錄） 之網域實體和實體物件不應該能夠存在而無效。 而異的規則只是表示為合約，以及它們違反時引發的例外狀況或通知。

這背後的原因是因為物件處於它們應永遠不會過的會發生很多 bug。 以下是合理的解釋，從在 Greg Young[線上討論](http://jeffreypalermo.com/blog/the-fallacy-of-the-always-valid-entity/):

我們建議我們現在有 SendUserCreationEmailService 採用 UserProfile...方式可以我們合理化中該名稱不是 null 的服務嗎？ 請勿我們檢查它一次？ 或更...您就不必擔心會檢查並"希望獲得最佳"— 您希望有人既然驗證再將它傳送給您。 當然，使用第一個測試，我們應該，如果傳送擁有名稱為空值的客戶應該引發錯誤會寫入一個的 TDD。 但是，當我們開始不斷地撰寫這些類型的測試我們了解...「 等待我們永遠不會允許名稱成為 null 就不會有所有這些測試 」

## <a name="implementing-validations-in-the-domain-model-layer"></a>在網域模型層中實作驗證

網域實體的建構函式中或在可以更新實體的方法，通常會實作驗證。 有多個方式來實作驗證，例如驗證資料和驗證失敗時引發的例外狀況。 另外還有更進階的模式，例如規格模式用於驗證和通知模式，傳回錯誤，而不是傳回的每個驗證例外狀況發生時的集合。

### <a name="validating-conditions-and-throwing-exceptions"></a>驗證條件並擲回例外狀況

下列程式碼範例會顯示最簡單的方法來驗證網域實體中引發例外狀況。 在本節結尾處的參考資料表中，您可以看到連結更進階的實作，根據我們先前已經討論過的模式。

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

更好的範例會示範須確定的內部狀態並未變更，或為方法的所有變化都發生。 例如，下列實作會讓物件處於無效狀態：

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

如果狀態的值無效，已經已變更第一個地址和縣 （市）。 可能會使位址無效。

類似的方法可以用於實體的建構函式，引發例外狀況以確定此實體是有效的一旦建立之後。

### <a name="using-validation-attributes-in-the-model-based-on-data-annotations"></a>使用資料註解為基礎的模型中的驗證屬性

另一種方法是使用資料註解為基礎的驗證屬性。 驗證屬性提供設定模型驗證，也就是在概念上類似資料庫資料表中的欄位上的驗證方法。 這包括條件約束，例如指派必要的欄位或資料型別。 其他類型的驗證模式來套用到資料，以強制執行商務規則，例如信用卡號碼，電話號碼或電子郵件地址。 驗證屬性，讓您輕鬆地強制執行需求。

不過，下列程式碼所示，這種方法可能太具侵入性在 DDD 模型中，因為所需的相依性上 ModelState.IsValid Microsoft.AspNetCore.Mvc.ModelState，您必須從 MVC 控制器方法呼叫。 模型驗證，就會發生在之前所叫用每個控制器動作，並負責控制器方法來檢查呼叫 ModelState.IsValid 結果和作出適當回應。 若要使用它的決定取決於如何緊密結合您想要該基礎結構的模型。

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

不過，DDD 觀點來看，從網域模型妥善保存 「 精實 」 例外狀況的使用中實體的行為的方法，或藉由實作來強制執行驗證規則的規格和通知模式。 驗證架構，像 ASP.NET Core 中的資料註解或 FluentValidation 像任何其他驗證架構執行叫用的應用程式架構的需求。 例如，呼叫 ModelState.IsValid 方法時資料註解中，您需要叫用 ASP.NET 控制器。

它可以合理層的應用程式會接受輸入，以提供 UI 層中的模型驗證的 ViewModel 類別 （而不是網域實體） 中使用資料註解。 不過，這不應該在驗證網域模型中排除。

### <a name="validating-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a>藉由實作規格模式和通知模式驗證實體

最後，更複雜的方法，在網域模型中實作驗證是實作規格模式搭配通知模式中，稍後將列出的其他資源的部分中所述。

值得一提，您也可以使用這些模式的其中一 — 比方說，手動驗證與控制陳述式，但使用的通知模式堆疊，並傳回驗證錯誤的清單。

### <a name="using-deferred-validation-in-the-domain"></a>在網域中使用延後的驗證

有各種方法來處理網域中延後的驗證。 他活頁簿中[Implementing Domain-Driven 設計](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577)，Vaughn Vernon 討論這些區段中驗證。

### <a name="two-step-validation"></a>兩步驟驗證

也請考慮雙步驟驗證。 在命令資料傳輸物件 (Dto) 和網域層級驗證，在您的實體上使用欄位層級驗證。 您可以傳回結果物件改為例外狀況以使其更容易處理的驗證錯誤。

使用資料註解欄位驗證，例如，您不會重複驗證定義。 執行時，不過，可以是伺服器端和用戶端在 DTOs 的情況下 (命令和 ViewModels，執行個體)。

## <a name="additional-resources"></a>其他資源

-   **Rachel Appel。ASP.NET Core MVC 中的模型驗證的簡介**
    [*https://docs.microsoft.com/aspnet/core/mvc/models/validation*](https://docs.microsoft.com/aspnet/core/mvc/models/validation)

-   **Rick Anderson，加入驗證**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)

-   **Martin Fowler：取代在驗證中擲回例外狀況，其通知**
    [*https://martinfowler.com/articles/replaceThrowWithNotification.html*](https://martinfowler.com/articles/replaceThrowWithNotification.html)

-   **規格和通知模式**
    [*https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns*](https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns)

-   **列弗 Gorodinski。驗證在網域導向設計 (DDD)**
    [*http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/*](http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/)

-   **Colin 端子。網域模型驗證**
    [*http://colinjack.blogspot.com/2008/03/domain-model-validation.html*](http://colinjack.blogspot.com/2008/03/domain-model-validation.html)

-   **Jimmy Bogard：DDD 世界中的驗證**
    [*https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/*](https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/)


>[!div class="step-by-step"]
[上一個](列舉-類別-over-列舉-types.md) [下一步] (用戶端-側邊-validation.md)
