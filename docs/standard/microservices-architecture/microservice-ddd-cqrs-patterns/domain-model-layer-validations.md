---
title: 設計領域模型層中的驗證
description: .NET 微服務：容器化 .NET 應用程式的架構 | 了解領域模型驗證的關鍵概念。
ms.date: 10/08/2018
ms.openlocfilehash: 1d3196d2130df33969ed231bccfe0fc6f0af2ad8
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639579"
---
# <a name="design-validations-in-the-domain-model-layer"></a>設計領域模型層中的驗證

在 DDD 中，驗證規則可以視為非變異值。 彙總的主要責任是跨該彙總內所有實體的狀態變更來強制執行非變異值。

領域實體應該一律是有效的實體。 一律應該為 true 的物件會有特定數目的非變異值。 例如，訂單項目物件一律必須要有必須是正整數的數量，以及發行項名稱和價格。 因此，非變異值強制執行負責領域實體 (特別是彙總根)，而且存在的實體物件應該有效。 非變異值規則只會表示為合約，而且會在違反時引發例外狀況或通知。

背後原因是物件處於絕對不應該處於的狀態而發生許多 Bug。 下列是 Greg Young 在[線上討論](https://jeffreypalermo.com/2009/05/the-fallacy-of-the-always-valid-entity/)中的合理解釋：

建議我們現在具有採用 UserProfile 的 SendUserCreationEmailService ... 如何合理化 Name 不是 Null 的該服務？ 要再次確認嗎？ 或者，更可能 ... 您不需要檢查並且「獲得最佳結果」- 您希望有人先進行驗證，再將它傳送給您。 當然，使用 TDD，我們應該撰寫的其中一個第一個測試就是將應該會引發錯誤的 Null 名稱傳送給客戶。 但是，當我們開始不斷地撰寫這些類型的測試時了解：「等一下，如果我們永遠不允許名稱變成 Null，就不會有所有這些測試」。

## <a name="implement-validations-in-the-domain-model-layer"></a>實作領域模型層中的驗證

通常是在領域實體建構函式或可更新實體的方法中實作驗證。 有多種方式可以實作驗證，例如驗證資料，以及在驗證失敗時引發例外狀況。 另外還有更進階模式，例如使用規格模式進行驗證，以及使用通知模式傳回錯誤集合，而不是傳回每個驗證所發生的例外狀況。

### <a name="validate-conditions-and-throw-exceptions"></a>驗證條件並擲回例外狀況

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
    _shippingAddress.line1 = line1 ?? throw new ...
    _shippingAddress.line2 = line2;
    _shippingAddress.city = city ?? throw new ...
    _shippingAddress.state = (IsValid(state) ? state : throw new …);
}
```

如果狀態的值無效，則已經變更第一個地址行和縣 (市)。 這可能會讓地址無效。

類似的方法可以用於實體的建構函式，即引發例外狀況來確定實體在建立之後有效。

### <a name="use-validation-attributes-in-the-model-based-on-data-annotations"></a>在以資料註解為基礎的模型中使用驗證屬性

資料註解與 Required 或 MaxLength 屬性相似，可用來設定 EF Core 資料庫欄位屬性 (如[資料表對應](infrastructure-persistence-layer-implemenation-entity-framework-core.md#table-mapping)一節中詳細資料所述)，但與 .NET Framework 中 EF 4.x 以來的版本不同，它們[已不再能用於 EF Core 中的實體驗證](https://github.com/aspnet/EntityFrameworkCore/issues/3680) (<xref:System.ComponentModel.DataAnnotations.IValidatableObject.Validate%2A?displayProperty=nameWithType> 方法也一樣)。

資料註解和 <xref:System.ComponentModel.DataAnnotations.IValidatableObject> 介面與過去相同，仍然可以在控制器的動作叫用前，於模型繫結期間用於模型驗證，但該模型應用來作為 ViewModel 或 DTO。這是 MVC 或 API 的考量事項，而非領域模型的考量事項。

在釐清概念差異之後，若您的動作會接受實體類別物件參數 (不建議)，則您仍然可以在實體類別中使用資料註解和 `IValidatableObject` 進行驗證。 在該情況下，驗證會在叫用動作前，於模型繫結時進行，且您可以檢查控制器的 ModelState.IsValid 屬性來檢查結果，但同樣的，與 EF 4.x 以來的版本不同，它會在控制器中發生，而非在將實體物件保存到 DbContext 前發生。

您仍然可以在實體類別中使用資料註解和 `IValidatableObject.Validate` 方法，透過覆寫 DbContext 的 SaveChanges 方法來實作自訂驗證。

您可以在 [GitHub 上的這個留言](https://github.com/aspnet/EntityFrameworkCore/issues/3680#issuecomment-155502539)裡看到驗證 `IValidatableObject` 實體的範例實作。 該範例不會進行以屬性為基礎的驗證，但它們可以在相同覆寫中，使用反映來輕鬆實作。

不過，從 DDD 觀點，領域模型會妥善使用您實體行為方法中的例外狀況，或藉由實作規格和通知模式來強制執行驗證規則。

它可以合理地使用接受輸入之 ViewModel 類別 (而非領域實體) 中應用程式層的資料註解，以允許 UI 層內的模型驗證。 不過，在領域模型內，這不應該排除驗證。

### <a name="validate-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a>實作規格模式和通知模式來驗證實體

最後，在領域模型中實作驗證的更複雜方法，是一起實作規格模式與通知模式，如稍後列出的一些其他資源所述。

值得一提的是，您也可以只使用其中一種模式；例如，使用 control 陳述式手動驗證，但使用通知模式來堆疊和傳回驗證錯誤清單。

### <a name="use-deferred-validation-in-the-domain"></a>在領域中使用延後驗證

有各種方法來處理領域中的延後驗證。 Vaughn Vernon 會在其 [Implementing Domain-Driven Design](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577) (實作領域驅動設計) 書籍的驗證小節中討論這些方法。

### <a name="two-step-validation"></a>兩步驟驗證

也請考慮兩步驟驗證。 在命令資料傳輸物件 (DTO) 上使用欄位層級驗證，以及在實體內部使用領域層級驗證。 做法是傳回結果物件而不是例外狀況，以更輕鬆地處理驗證錯誤。

例如，使用具有資料註解的欄位驗證，就不會有重複的驗證定義。 不過，如果是 DTO，則執行可以是伺服器端和用戶端 (例如，命令和 ViewModel)。

## <a name="additional-resources"></a>其他資源

- **Rachel Appel：ASP.NET Core MVC 中的模型驗證簡介** \
  <https://docs.microsoft.com/aspnet/core/mvc/models/validation>

- **Rick Anderson，新增驗證** \
  <https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation>

- **Martin Fowler：在驗證中將擲回例外狀況取代為通知** \
  <https://martinfowler.com/articles/replaceThrowWithNotification.html>

- **規格和通知模式** \
  <https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns>

- **Lev Gorodinski：網域驅動設計 (DDD) 中的驗證** \
  <http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/>

- **Colin Jack：領域模型驗證** \
  <https://colinjack.blogspot.com/2008/03/domain-model-validation.html>

- **Jimmy Bogard：DDD 世界中的驗證** \
  <https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/>

> [!div class="step-by-step"]
> [上一頁](enumeration-classes-over-enum-types.md)
> [下一頁](client-side-validation.md)
