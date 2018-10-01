---
title: 撰寫單元測試的最佳做法
description: 了解撰寫單元測試的最佳做法，提高程式碼品質和復原功能
author: jpreese
ms.author: wiwagn
ms.date: 07/28/2018
ms.openlocfilehash: 69fe0cae141d1ed1e1281eecd78bf03e6e8be961
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43527757"
---
# <a name="unit-testing-best-practices"></a>單元測試最佳做法

作者：[John Reese](http://reesespieces.io) (特別感謝 [Roy Osherove](http://osherove.com/))

撰寫單元測試有許多優點；運用迴歸加以協助、提供文件，並增進良好的設計。 不過，難以閱讀且容易損毀的單元測試可能會破壞程式碼基底。

本指南中，您將了解一些撰寫單元測試時的最佳做法，讓您的測試保有復原能力且易於了解。

## <a name="why-unit-test"></a>為何選擇單元測試？

### <a name="less-time-performing-functional-tests"></a>執行功能測試的時間較少
功能測試很耗費資源。 功能測試通常涉及開啟應用程式，以及執行您 (或其他人) 必須遵循的一系列步驟，藉此驗證預期行為。 測試人員不一定會熟悉這些步驟，表示他們必須連絡該領域中更加專業的人員，才得以執行測試。 對於較細瑣的變更，測試本身可能需要費時幾秒鐘，而對於較大的變更，可能會花上幾分鐘的時間。 最後，將必須對您在系統中所做的所有變更重複執行此程序。

另一方面，單元測試只需費時幾毫秒，按下按鈕便可執行，並不需要有整個系統的相關知識。 測試通過或失敗取決於測試執行者，而不是個人。

### <a name="protection-against-regression"></a>對於迴歸的保護
迴歸缺失是對應用程式進行變更時帶來的缺失。 通常測試人員不僅要測試其新功能，也要測試早已存在的功能，確認先前實作的功能仍可如預期般運作。

利用單元測試，您就可以在每次建置之後，甚至是您變更程式碼行之後，重新執行一整套測試。 讓您確信新的程式碼不會中斷現有的功能。

### <a name="executable-documentation"></a>可執行檔文件
在提供特定輸入的情況下，特定方法的用途或其運作方式不一定很明顯。 您可能會自問：如果我將空白字串傳遞給此方法，其運作方式為何？ Null 呢？

如果您有一套妥善命名的單元測試，每個測試都應該能清楚說明給定輸入的預期輸出。 此外，應該還能確認它實際上可正常運作。

### <a name="less-coupled-code"></a>結合的程式碼較少
當程式碼緊密結合時，可能難以進行單元測試。 如果不針對您所撰寫的程式碼建立單元測試，結合程度就可能較不明顯。

為您的程式碼撰寫測試時會自然分離程式碼，否則它會更難以測試。

## <a name="characteristics-of-a-good-unit-test"></a>良好單元測試的特性
- **快速**。 具有數千個單元測試的成熟專案並不罕見。 單元測試應只需要極少的時間執行。 毫秒。
- **隔離**。 單元測試是獨立的，可以單獨執行，並且對所有外部因素 (例如檔案系統或資料庫) 沒有任何相依性。
- **可重複**。 執行單元測試應該與其結果一致，亦即，如果您未變更回合之間的任何項目，會一律傳回相同的結果。
- **自我檢查**。 測試應該能夠自行偵測到通過或失敗，不需要任何人為互動。
- **及時**。 相較於所測試的程式碼，單元測試不應耗費不成比例的冗長時間來撰寫。 相較於撰寫程式碼，如果您發現測試程式碼花費大量時間，請考慮使用更易於測試的設計。

## <a name="lets-speak-the-same-language"></a>讓我們使用相同的語言
說到測試，遺憾的是「模擬」(*mock*) 一詞遭到誤用。 以下將定義撰寫單元測試時最常見的 *fakes* 類型：

假功能 (*Fake*) - 假功能是一般詞彙，用來描述虛設常式或模擬物件。 至於是虛設常式還是模擬，取決於使用的內容而定。 因此，換句話說，假功能可以是虛設常式或是模擬。

模擬 (*Mock*) - 模擬物件是系統中的假物件，可決定單元測試通過或失敗。 模擬一開始是假功能，直到另行判定為止。

虛設常式 (*Stub*) - 虛設常式是系統中現有相依性 (或共同作業者) 的可控制取代項目。 藉由使用虛設常式，您可以測試程式碼，而不必直接處理相依性。 根據預設，假功能一開始是虛設常式。

請考慮下列程式碼片段：

```csharp
var mockOrder = new MockOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

這是稱為模擬 (mock) 的虛設常式範例。 在此情況下為虛設常式。 您只是傳入訂單，作為能夠具現化 `Purchase` (待測系統) 的方法。 名稱 `MockOrder` 也很容易產生誤導，因為訂單並不是模擬。

更好的方式會是

```csharp
var stubOrder = new FakeOrder();
var purchase = new Purchase(stubOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

透過將類別重新命名為 `FakeOrder`，您已使該類別更加通用，因此可將該類別作為模擬或虛設常式使用。 請取其更適合測試案例者。 在上述範例中，`FakeOrder` 作為虛設常式使用。 在判定期間，您沒有以任何形式使用 `FakeOrder`。 `FakeOrder` 只是傳入 `Purchase` 類別以滿足建構函式的需求。

若要用作模擬，您可以執行類似下述內容

```csharp
var mockOrder = new FakeOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(mockOrder.Validated);
```

在此情況下，您正在檢查假功能上的屬性 (另行判定)，因此在上述程式碼片段中，屬性 `mockOrder` 是模擬。

> [!IMPORTANT]
> 請務必正確使用這個術語。 如果您將虛設常式稱為「模擬」，其他開發人員會對您的意圖帶有錯誤的假設。

關於模擬與虛設常式要記住的重點在於，模擬就像虛設常式一樣，只是您會對模擬物件另行判定，而不會對虛設常式另行判定。

## <a name="best-practices"></a>最佳作法

### <a name="naming-your-tests"></a>為測試命名
測試的名稱應該包含三個部分：
- 所測試的方法名稱。
- 用以測試的案例。
- 叫用案例時的預期行為。

#### <a name="why"></a>為什麼？
- 命名標準很重要，因為名稱會明確表示測試目的。

測試不只要確定您的程式碼能夠運作，還會提供文件。 只要查看這套單元測試，您應能推斷程式碼的行為，甚至無需查看程式碼本身。 此外，當測試失敗時，您可以確切看到哪些案例不符合預期。

#### <a name="bad"></a>不良：
[!code-csharp[BeforeNaming](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeNaming)]

#### <a name="better"></a>較佳：
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="arranging-your-tests"></a>排列測試
**排列、採取動作、判定**是進行單元測試時的常見模式。 顧名思義，其中包含三個主要動作：
- 「排列」物件，並視需要建立和設定這些物件。
- 對物件「採取動作」。
- 「判定」某個項目如預期般運作。

#### <a name="why"></a>為什麼？
- 清楚分隔正在測試的項目與「排列」和「判定」步驟。
- 這麼做可使判定與「採取動作」程式碼相互摻雜的機率更低。

可讀性是撰寫測試時最重要的層面之一。 分隔測試內的每個動作可清楚突顯呼叫程式碼、如何呼叫程式碼，以及您嘗試進行判定所需的相依性。 雖然可以合併某些步驟並減少測試的大小，但主要目標是盡可能讓測試可讀。

#### <a name="bad"></a>不良：
[!code-csharp[BeforeArranging](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeArranging)]

#### <a name="better"></a>較佳：
[!code-csharp[AfterArranging](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterArranging)]

### <a name="write-minimally-passing-tests"></a>撰寫最低限度通過測試
要在單元測試中使用的輸入應該是最簡單的，才能驗證您目前正在測試的行為。

#### <a name="why"></a>為什麼？
- 測試對程式碼基底的未來變更變得更具復原性。
- 更接近測試行為而不是實作。

如果測試包含的資訊比通過測試所需還要多，更有可能會將錯誤帶進測試中，且會讓測試的意圖較不清楚。 撰寫測試時，您想要著重於行為。 在模型上設定額外的屬性，或在不需要時使用非零值，只會減損您嘗試證明的項目。

#### <a name="bad"></a>不良：
[!code-csharp[BeforeMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMinimallyPassing)]

#### <a name="better"></a>較佳：
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="avoid-magic-strings"></a>避免魔術字串
相較於在生產環境程式碼中為變數命名，在單元測試中為變數命名的重要性有過之而無不及。 單元測試不應該包含魔術字串。

#### <a name="why"></a>為什麼？
- 避免測試的讀者為了找出使該值變得特殊的原因而需要檢查生產環境程式碼。
- 明確地顯示您想要「證明」的項目，而不是嘗試「完成」的項目。

魔術字串可能會對測試的讀者造成混淆。 如果字串看起來不正常，讀者可能會納悶為什麼針對參數或傳回值選擇特定值。 這可能會導致他們過於仔細查看實作詳細資料，而不是專注於測試。

> [!TIP] 
> 在撰寫測試時，您的目標應該是盡可能表達意圖。 如果是魔術字串，將這些值指派給常數會是不錯的方法。

#### <a name="bad"></a>不良：
[!code-csharp[BeforeMagicString](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMagicString)]

#### <a name="better"></a>較佳：
[!code-csharp[AfterMagicString](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterMagicString)]

### <a name="avoid-logic-in-tests"></a>避免在測試中使用邏輯
撰寫您的單元測試時，請避免使用手動字串串連和邏輯條件，例如 `if`、`while`、`for`、`switch` 等等。

#### <a name="why"></a>為什麼？
- 在測試內帶進 Bug 的機率更低。
- 著重最終結果，而不是實作詳細資料。

將邏輯引入您的測試套件時，在其中帶進 Bug 的機率會大幅增加。 您不會想要在您的測試套件尋找 Bug。 您應該對測試正確運作的結果具有高度信心，否則您不會信任測試。 您不信任的測試將無法提供任何價值。 當測試失敗時，您要意識到確實是程式碼發生問題，且無法予以忽略。

> [!TIP]
> 如果測試中的邏輯看似無法避免，請考慮將測試分割成兩個或多個不同的測試。

#### <a name="bad"></a>不良：
[!code-csharp[LogicInTests](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#LogicInTests)]

#### <a name="better"></a>較佳：
[!code-csharp[AfterTestLogic](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterTestLogic)]

### <a name="prefer-helper-methods-to-setup-and-teardown"></a>慣用 Helper 方法來設定及終止
如果您的測試需要類似的物件或狀態，比起利用 Setup 和 Teardown 屬性 (若有)，更慣用 Helper 方法。

#### <a name="why"></a>為什麼？
- 讀取測試時混淆較少，因為在每個測試內都可以看見所有的程式碼。
- 對於給定的測試，設定太多或太少的機率更低。
- 在測試之間共用狀態，進而在測試之間建立非必要相依性的機率更低。

在單元測試架構中，會在測試套件內的每個單元測試之前或其中呼叫 `Setup`。 雖然有人可能會認為這是很有用的工具，但它最後通常會導致測試過大且難以閱讀。 每個測試通常會有不同的需求，以便啟動及執測試。 不幸的是，`Setup` 會強迫您針對每個測試使用完全相同的需求。

> [!NOTE] 
> 自 2.x 版開始，xUnit 已移除 Setup 及 TearDown 這兩者

#### <a name="bad"></a>不良：
[!code-csharp[BeforeSetup](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeSetup)]

```csharp
// more tests...
```

[!code-csharp[BeforeHelperMethod](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeHelperMethod)]

#### <a name="better"></a>較佳：
[!code-csharp[AfterHelperMethod](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterHelperMethod)]

```csharp
// more tests...
```

[!code-csharp[AfterSetup](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterSetup)]

### <a name="avoid-multiple-asserts"></a>避免多個判定
在撰寫測試時，請嘗試於每個測試只包含一個判定。 只使用一個判定的常見方法包括：
- 為每個判定建立個別測試。
- 使用參數化測試。

#### <a name="why"></a>為什麼？
- 如果某個判定失敗，將不會評估後續的判定。
- 確保您不會在測試中判定多個案例。
- 為您提供測試失敗原因的全貌。 

將多個判定帶進測試案例時，並不保證所有的判定皆會執行。 在大部分的單元測試架構中，一旦判定在單元測試中失敗，進行中的測試將自動視為失敗。 這可能會令人困惑，因為實際運作的功能會顯示為失敗。

> [!NOTE]
> 這項規則的常見例外狀況是針對物件進行判定時。 在此情況下，通常可以接受對每個屬性擁有多個判定，確保物件處於您預期的狀態。

#### <a name="bad"></a>不良：
[!code-csharp[BeforeMultipleAsserts](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMultipleAsserts)]

#### <a name="better"></a>較佳：
[!code-csharp[AfterMultipleAsserts](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterMultipleAsserts)]

### <a name="validate-private-methods-by-unit-testing-public-methods"></a>透過單元測試的公用方法驗證私用方法
在大部分情況下，應該不需要測試私用方法。 私用方法是實作詳細資料。 您可以這樣來看：私用方法永遠不會單獨存在。 在某個時間點，將有一個公眾對應方法呼叫私用方法作為其實作的一部分。 您應該關注的是呼叫私用方法的公用方法最終結果。 

請考慮下列情況

```csharp
public string ParseLogLine(string input)
{
    var sanitizedInput = trimInput(input);
    return sanitizedInput;
}

private string trimInput(string input)
{
    return input.Trim();
}
```

您的第一個反應可能是開始撰寫 `trimInput` 的測試，因為您想要確定該方法是否如預期般運作。 不過，`ParseLogLine` 很有可能會以非預期的方式操作 `sanitizedInput`，使得對 `trimInput` 的測試變得毫無用處。 

實際的測試應該針對公眾對應方法 `ParseLogLine` 執行，因為這才是您最應關注的項目。 

```csharp
public void ParseLogLine_ByDefault_ReturnsTrimmedResult()
{
    var parser = new Parser();

    var result = parser.ParseLogLine(" a ");

    Assert.Equals("a", result);
}
```

從這個觀點來看，如果您看到私用方法，請找出公開方法，並針對該方法撰寫您的測試。 私用方法傳回預期結果，並不表示最終呼叫私用方法的系統會正確地使用結果。

### <a name="stub-static-references"></a>虛設 (Stub) 靜態參考
單元測試的其中一個準則是，其必須具有待測系統的完整控制權。 這可能會在生產環境程式碼包含靜態參考呼叫時 (例如 `DateTime.Now`) 造成問題。 請考慮下列程式碼

```csharp
public int GetDiscountedPrice(int price)
{
    if(DateTime.Now == DayOfWeek.Tuesday) 
    {
        return price / 2;
    }
    else 
    {
        return price;
    }
}
```

如何對此程式碼進行單元測試？ 您可以嘗試一種方法，例如

```csharp
public void GetDiscountedPrice_ByDefault_ReturnsFullPrice()
{
    var priceCalculator = new PriceCalculator();

    var actual = priceCalculator.GetDiscountedPrice(2);

    Assert.Equals(2, actual)
}

public void GetDiscountedPrice_OnTuesday_ReturnsHalfPrice()
{
    var priceCalculator = new PriceCalculator();

    var actual = priceCalculator.GetDiscountedPrice(2);

    Assert.Equals(1, actual);
}
```

不幸的是，您很快就會發現測試有幾個問題。 

- 如果測試套件是在星期二執行，第二項測試會通過，但第一項測試會失敗。
- 如果測試套件是在其他天執行，第一項測試會通過，但第二項測試會失敗。

若要解決這些問題，您需要將「接合線」帶進生產環境程式碼。 其中一個方法是在介面中包裝您需要控制的程式碼，並使生產環境程式碼相依於該介面。

```csharp
public interface IDateTimeProvider
{
    DayOfWeek DayOfWeek();
}

public bool GetDiscountedPrice(int price, IDateTimeProvider dateTimeProvider)
{
    if(dateTimeProvider.DayOfWeek() == DayOfWeek.Tuesday) 
    {
        return price / 2;
    }
    else 
    {
        return price;
    }
}
```

您的測試套件現在已變成

```csharp
public void GetDiscountedPrice_ByDefault_ReturnsFullPrice()
{
    var priceCalculator = new PriceCalculator();
    var dateTimeProviderStub = new Mock<IDateTimeProvider>();
    dateTimeProviderStub.Setup(dtp => dtp.DayOfWeek()).Returns(DayOfWeek.Monday);

    var actual = priceCalculator.GetDiscountedPrice(2, dateTimeProviderStub);

    Assert.Equals(2, actual);
}

public void GetDiscountedPrice_OnTuesday_ReturnsHalfPrice()
{
    var priceCalculator = new PriceCalculator();
    var dateTimeProviderStub = new Mock<IDateTimeProvider>();
    dateTimeProviderStub.Setup(dtp => dtp.DayOfWeek()).Returns(DayOfWeek.Tuesday);

    var actual = priceCalculator.GetDiscountedPrice(2, dateTimeProviderStub);

    Assert.Equals(1, actual);
}
```

現在，測試套件具有 `DateTime.Now` 的完整控制權，而且可以在呼叫方法時虛設任何值。
