---
title: 設計領域模型層中的驗證
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 設計領域模型層中的驗證
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: ce3cb0c79cbd492224ce1d4ecb25cd02062f11cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="designing-validations-in-the-domain-model-layer"></a>設計領域模型層中的驗證

在 DDD 中，驗證規則可以視為非變異值。 彙總的主要責任是跨該彙總內所有實體的狀態變更來強制執行非變異值。

領域實體應該一律是有效的實體。 一律應該為 true 的物件會有特定數目的非變異值。 例如，訂單項目物件一律必須要有必須是正整數的數量，以及發行項名稱和價格。 因此，非變異值強制執行負責領域實體 (特別是彙總根)，而且存在的實體物件應該有效。 非變異值規則只會表示為合約，而且會在違反時引發例外狀況或通知。

背後原因是物件處於絕對不應該處於的狀態而發生許多 Bug。 下列是 Greg Young 在[線上討論](http://jeffreypalermo.com/blog/the-fallacy-of-the-always-valid-entity/)中的合理解釋：

建議我們現在具有採用 UserProfile 的 SendUserCreationEmailService ... 如何合理化 Name 不是 Null 的該服務？ 要再次確認嗎？ 或者，更可能 ... 您不需要檢查並且「獲得最佳結果」- 您希望有人先進行驗證，再將它傳送給您。 當然，使用 TDD，我們應該撰寫的其中一個第一個測試就是將應該會引發錯誤的 Null 名稱傳送給客戶。 但是，當我們開始不斷地撰寫這些類型的測試時了解：「等一下，如果我們永遠不允許名稱變成 Null，就不會有所有這些測試」。

## <a name="implementing-validations-in-the-domain-model-layer"></a>實作領域模型層中的驗證

通常是在領域實體建構函式或可更新實體的方法中實作驗證。 有多種方式可以實作驗證，例如驗證資料，以及在驗證失敗時引發例外狀況。 另外還有更進階模式，例如使用規格模式進行驗證，以及使用通知模式傳回錯誤集合，而不是傳回每個驗證所發生的例外狀況。

### <a name="validating-conditions-and-throwing-exceptions"></a>驗證條件並擲回例外狀況

下列程式碼範例透過引發例外狀況來示範領域實體中的最簡單驗證方法。 在本節結尾的參考資料表中，您可以看到根據我們先前討論過之模式的更進階實作連結。

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

更好的範例會示範需要確定內部狀態未變更，或方法的所有變化。 例如，下列實作會讓物件處於無效狀態：

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

如果狀態的值無效，則已經變更第一個地址行和縣 (市)。 這可能會讓地址無效。

類似的方法可以用於實體的建構函式，即引發例外狀況來確定實體在建立之後有效。

### <a name="using-validation-attributes-in-the-model-based-on-data-annotations"></a>在根據資料註解的模型中使用驗證屬性

另一種方法是使用根據資料註解的驗證屬性。 驗證屬性提供設定模型驗證的方式，而在概念上，類似資料庫資料表中的欄位驗證。 這包括條件約束，例如指派資料類型或必要欄位。 其他驗證類型還包括將模式套用至資料以強制執行商務規則，例如信用卡號碼、電話號碼或電子郵件地址。 驗證屬性可簡化需求強制執行。

不過，如下列程式碼所示，這種方法在 DDD 模型中可能太具侵入性，因為它相依於您必須從 MVC 控制器呼叫之 Microsoft.AspNetCore.Mvc.ModelState 中的 ModelState.IsValid。 模型驗證會在叫用每個控制器動作之前發生，而且控制器方法負責檢查呼叫中 ModelState.IsValid 的結果並做出適當回應。 使用它的決定取決於如何緊密結合模型與該基礎結構。

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

不過，從 DDD 觀點，領域模型會妥善使用您實體行為方法中的例外狀況，或藉由實作規格和通知模式來強制執行驗證規則。 ASP.NET Core 中資料註解這類驗證架構或 FluentValidation 這類任何其他驗證架構需要叫用應用程式架構。 例如，在資料註解中呼叫 ModelState.IsValid 方法時，您需要叫用 ASP.NET 控制器。

它可以合理地使用接受輸入之 ViewModel 類別 (而非領域實體) 中應用程式層的資料註解，以允許 UI 層內的模型驗證。 不過，在領域模型內，這不應該排除驗證。

### <a name="validating-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a>實作規格模式和通知模式來驗證實體

最後，在領域模型中實作驗證的更複雜方法，是一起實作規格模式與通知模式，如稍後列出的一些其他資源所述。

值得一提的是，您也可以只使用其中一種模式；例如，使用 control 陳述式手動驗證，但使用通知模式來堆疊和傳回驗證錯誤清單。

### <a name="using-deferred-validation-in-the-domain"></a>在領域中使用延後驗證

有各種方法來處理領域中的延後驗證。 Vaughn Vernon 會在其 [Implementing Domain-Driven Design](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577) (實作領域驅動設計) 書籍的驗證小節中討論這些方法。

### <a name="two-step-validation"></a>兩步驟驗證

也請考慮兩步驟驗證。 在命令資料傳輸物件 (DTO) 上使用欄位層級驗證，以及在實體內部使用領域層級驗證。 作法是傳回結果物件，而不是例外狀況，以更輕鬆地處理驗證錯誤。

例如，使用具有資料註解的欄位驗證，就不會有重複的驗證定義。 不過，如果是 DTO，則執行可以是伺服器端和用戶端 (例如，命令和 ViewModel)。

## <a name="additional-resources"></a>其他資源

-   **Rachel Appel：ASP.NET Core MVC 中的模型驗證簡介**
    [*https://docs.microsoft.com/aspnet/core/mvc/models/validation*](https://docs.microsoft.com/aspnet/core/mvc/models/validation)

-   **Rick Anderson，新增驗證**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)

-   **Martin Fowler：在驗證中將擲回例外狀況取代為通知**
    [*https://martinfowler.com/articles/replaceThrowWithNotification.html*](https://martinfowler.com/articles/replaceThrowWithNotification.html)

-   **規格和通知模式**
    [*https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns*](https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns)

-   **Lev Gorodinski：網域導向設計 (DDD) 中的驗證**
    [*http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/*](http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/)

-   **Colin Jack：領域模型驗證**
    [*http://colinjack.blogspot.com/2008/03/domain-model-validation.html*](http://colinjack.blogspot.com/2008/03/domain-model-validation.html)

-   **Jimmy Bogard：DDD 世界中的驗證**
    [*https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/*](https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/)


>[!div class="step-by-step"]
[上一個] (enumeration-classes-over-enum-types.md) [下一個] (client-side-validation.md)
