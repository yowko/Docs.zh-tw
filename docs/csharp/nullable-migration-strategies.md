---
title: 更新您的程式碼基底以使用可為 null 的參考型別
description: 選擇最佳的策略來升級程式碼基底，以使用可為 null 的參考型別。
ms.technology: csharp-null-safety
ms.date: 07/31/2019
ms.openlocfilehash: 5909eb9ffe1f5398fc2eb74848b82f8fe9516548
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975330"
---
# <a name="update-libraries-to-use-nullable-reference-types-and-communicate-nullable-rules-to-callers"></a>更新程式庫以使用可為 null 的參考型別，並將可為 null 的規則與呼叫

加入[可為 null 的參考型別](nullable-references.md)表示您可以宣告每個變數`null`是否允許或預期值。 此外，您可以套用`AllowNull`一些屬性：、 `DisallowNull`、 `MaybeNull`、 `NotNull`、 `NotNullWhen` `MaybeNullWhen`、和`NotNullIfNotNull` ，以完整描述引數和傳回值的 null 狀態。 這會在您撰寫程式碼時提供絕佳的體驗。 如果不可為 null 的變數可能設定為`null`，則會收到警告。 如果可為 null 的變數不是 null，則您會收到警告，然後再對其進行取值。 更新您的程式庫可能需要一些時間，但回報值得一提。 *當*允許或禁止某個`null`值時，您提供給編譯器的資訊越多，API 的使用者就會得到更好的警告。 讓我們從熟悉的範例開始。 假設您的程式庫具有下列 API 來抓取資源字串：

```csharp
bool TryGetMessage(string key, out string message)
```

上述範例會遵循 .NET 中`Try*`熟悉的模式。 此 API 有兩個參考引數： `key`和`message`參數。 此 API 具有下列與這些引數的 null 相關的規則：

- 呼叫端不`null`應傳遞做為`key`的引數。
- 呼叫端可以傳遞一個變數，其`null`值會當做的`message`引數。
- 如果`TryGetMessage`方法傳回`true`，則的值`message`不是 null。 如果傳回值是`false,` `message` （和其 null 狀態）的值，則為 null。

的規則`key`可以完全以變數類型表示： `key`應該是不可為 null 的參考型別。 `message`參數較複雜。 它允許`null`做為引數，但可保證在成功時， `out`該引數不是 null。 在這些情況下，您需要更豐富的詞彙來描述預期。

針對可為 null 的參考更新您的連結`?`庫，在某些變數和類型名稱上不需要隨處揮灑 threadpool.queueuserworkitem。 上述範例顯示您需要檢查您的 Api，並考慮每個輸入引數的預期。 請考慮傳回值的保證，以及方法傳回`out`時`ref`的任何或引數。 然後將這些規則傳達給編譯器，而編譯器會在呼叫者不遵守這些規則時提供警告。

此工作需要一些時間。 讓我們從策略開始，將您的程式庫或應用程式設為可為 null 感知，同時平衡其他需求和交付專案。 您將瞭解如何平衡進行中的開發，並啟用可為 null 的參考型別。 您將會學到泛型型別定義的挑戰。 您將瞭解如何套用屬性，以描述個別 Api 的前置和後置條件。

## <a name="choose-a-strategy-for-nullable-reference-types"></a>選擇可為 null 之參考型別的策略

第一個選擇是可為 null 的參考型別是否預設為開啟或關閉。 您有兩種策略：

- 為整個專案啟用可為 null 的參考型別，並在未就緒的程式碼中停用它。
- 僅針對已針對可為 null 的參考型別標注的程式碼，啟用可為 null 的參考型別。

當您將其他功能新增至程式庫時，第一個策略的效果最佳，是針對可為 null 的參考型別進行更新。 所有新的開發都是可為 null 的感知。 當您更新現有程式碼時，您可以在這些類別中啟用可為 null 的參考型別。

遵循第一個策略，您可以執行下列動作：

1. 藉由將`<Nullable>enable</Nullable>`元素新增至您的 *.csproj*檔案，為整個專案啟用可為 null 的參考型別。
1. 將`#nullable disable` pragma 新增至專案中的每個原始程式檔。
1. 當您處理每個檔案時，請移除 pragma 並解決任何警告。

第一個策略有更多的最新工作，可以將 pragma 新增至每個檔案。 優點是每個新增至專案的新程式碼檔案都可為 null 啟用。 任何新工作都可為 null 感知;僅必須更新現有的程式碼。

如果程式庫通常穩定，第二個策略的效果更好，而開發的主要重點是採用可為 null 的參考型別。 當您標注 Api 時，您會開啟可為 null 的參考型別。 當您完成時，您可以為整個專案啟用可為 null 的參考型別。

遵循第二個策略，您可以執行下列動作：

1. 將`#nullable enable` pragma 新增到您想要使其成為可為 null 的檔案。
1. 解決任何警告。
1. 繼續執行前兩個步驟，直到您將整個程式庫設為可為 null 為止。
1. 將`<Nullable>enable</Nullable>`元素新增至您的 *.csproj*檔案，為整個專案啟用可為 null 的類型。
1. 移除`#nullable enable` pragma，因為已不再需要它。

第二個策略的處理時間較少。 缺點是，當您建立新檔案時，第一項工作是新增 pragma 並讓它成為可為 null 的感知。 如果您小組中的任何開發人員忘記，新的程式碼現在已在工作待處理專案中，使所有程式碼可為 null 感知。

您挑選的其中一個策略，取決於您的專案中有多少使用中的開發。 您的專案越成熟且穩定，第二個策略就越好。 開發的功能越多，第一個策略就越好。

## <a name="should-nullable-warnings-introduce-breaking-changes"></a>可為 null 的警告是否會引進重大變更？

啟用可為 null 的參考型別之前，變數會被視為*可為 null 的遺忘式*。 啟用可為 null 的參考型別後，所有這些變數都*不可為 null*。 如果未將這些變數初始化為非 null 值，編譯器會發出警告。

另一個可能的警告來源是值未初始化時的傳回值。

解決編譯器警告的第一個步驟是在參數和`?`傳回型別上使用注釋，以指示引數或傳回值是否可以是 null。 當參考變數不得為 null 時，原始宣告是正確的。 當您這麼做時，您的目標不是要修正警告。 較重要的目標是讓編譯器瞭解潛在 null 值的意圖。 當您檢查這些警告時，您會到達程式庫的下一個主要決策。 您是否想要考慮修改 API 簽章，以更清楚地傳達您的設計意圖？ 更好的 API 簽章`TryGetMessage`適用于先前檢查的方法，可能是：

```csharp
string? TryGetMessage(string key);
```

傳回值表示成功或失敗，如果找到值，則會攜帶值。 在許多情況下，變更 API 簽章可以改善它們傳達 null 值的方式。

不過，對於公用程式庫或具有大型使用者群的程式庫，您可能不會想要引入任何 API 簽章變更。 針對這些案例和其他常見的模式，您可以套用屬性，以更清楚地定義引數或傳回值可能`null`的時機。 無論您是否考慮變更 API 的介面，您可能會發現單獨的類型注釋並不足以描述`null`引數或傳回值的值。 在這些情況下，您可以套用屬性，以更清楚地描述 API。

## <a name="attributes-extend-type-annotations"></a>屬性擴充類型注釋

已經加入數個屬性，以表達變數的 null 狀態的其他相關資訊。 您在 c # 8 之前撰寫的所有程式碼引進了可為 null 的參考型別，*遺忘式*。 這表示任何參考型別變數都可以是 null，但不需要 null 檢查。 一旦您的程式碼*可為 null 感知*，這些規則就會變更。 參考型別應該永遠不`null`會是值，而且必須`null`先檢查可為 null 的參考型別，然後再進行引用。

您的 Api 規則可能會更複雜，如您在`TryGetValue` API 案例中所見。 許多 Api 在變數可以或不是`null`時，會有更複雜的規則。 在這些情況下，您將使用屬性來表示這些規則。 描述 API 的語義的屬性可在[影響可為 null 分析的屬性](./language-reference/attributes/nullable-analysis.md)一文中找到。

## <a name="generic-definitions-and-nullability"></a>泛型定義和 null 屬性

正確地傳達泛型型別和泛型方法的 null 狀態需要特別小心。 這源自于可為 null 的實值型別和可為 null 的參考型別，基本上是不同的事實。 `int?`是的同義字`Nullable<int>`，而`string?`則是`string`由編譯器新增的屬性。 結果是`T?` ，編譯器無法產生的正確程式碼，而不知道`T`是`class`或。 `struct`

這並不表示您無法使用可為 null 的類型（實數值型別或參考型別）做為封閉式泛型型別的類型引數。 `List<string?>`和`List<int?>`都是的`List<T>`有效具現化。

它的意思是，您無法在沒有`T?`條件約束的泛型類別或方法宣告中使用。 例如， <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType>不會變更為傳回`T?`。 您可以藉由新增`struct`或`class`條件約束來克服這項限制。 使用上述任一條件約束時，編譯器會知道如何為`T`和`T?`產生程式碼。

您可能想要將泛型型別引數所使用的類型限制為不可為 null 的類型。 您可以在該型別自`notnull`變數上加入條件約束來達到這個目的。 套用該條件約束時，類型引數不能是可為 null 的類型。

## <a name="late-initialized-properties-data-transfer-objects-and-nullability"></a>晚期初始化的屬性、資料傳輸物件和可為 null

指出已延遲初始化之屬性的 null 屬性（亦即在結構之後設定）可能需要特別考慮，以確保您的類別會繼續正確地表達原始的設計意圖。

包含晚期初始化屬性的型別（如資料傳輸物件（Dto））通常是由外部程式庫（例如資料庫 ORM （物件關聯式對應程式）、還原序列化程式，或是自動從另一個來源填入屬性的其他元件）所具現化。

在啟用可為 null 的參考型別（代表學生）之前，請先考慮下列 DTO 類別：

```csharp
class Student
{
    [Required]
    public string FirstName { get; set; }

    [Required]
    public string LastName { get; set; }

    public string VehicleRegistration { get; set; }
}
```

設計意圖（在此案例中是`Required`由屬性所表示）表示在此系統中， `FirstName`和`LastName`屬性是**強制性**的，因此不是 null。

屬性`VehicleRegistration`不是**強制性**的，因此可能是 null。

當您啟用可為 null 的參考型別時，您會想要在 DTO 上指出哪些屬性可為 null，與您的原始意圖一致：

```csharp
class Student
{
    [Required]
    public string FirstName { get; set; }

    [Required]
    public string LastName { get; set; }

    public string? VehicleRegistration { get; set; }
}
```

對於此 DTO，唯一可為 null 的屬性是``VehicleRegistration``。

不過，編譯器會同時`CS8618` `FirstName`引發和`LastName`的警告，表示不可為 null 的屬性未初始化。

有三個選項可供您使用，以維護原始意圖的方式解決編譯器警告。 任何這些選項都是有效的;您應該選擇最適合您程式碼樣式和設計需求的應用程式。

### <a name="initialize-in-the-constructor"></a>在函式中初始化

解決未初始化警告的理想方式，是初始化此函式中的屬性：

```csharp
class Student
{
    public Student(string firstName, string lastName)
    {
        FirstName = firstName;
        LastName = lastName;
    }

    [Required]
    public string FirstName { get; set; }

    [Required]
    public string LastName { get; set; }

    public string? VehicleRegistration { get; set; }
}
```

只有當您用來具現化類別的程式庫支援在此函式中傳遞參數時，這個方法才有效。

此外，程式庫可能支援在函式中傳遞*某些*屬性，但並非全部。
例如， [EF Core 支援一般](/ef/core/modeling/constructors)資料行屬性的「函式系結」，而非「導覽屬性」。

請查看具現化類別之程式庫上的檔，以瞭解它支援的函式系結程度。

### <a name="property-with-nullable-backing-field"></a>具有可為 null 支援欄位的屬性

如果函式系結無法供您使用，則解決此問題的其中一種方法是將不可為 null 的屬性與可為 null 的支援欄位搭配使用：

```csharp
private string? _firstName;

[Required]
public string FirstName
{
    set => _firstName = value;
    get => _firstName
           ?? throw new InvalidOperationException("Uninitialized " + nameof(FirstName))
}
```

在此案例中，如果`FirstName`在初始化之前存取屬性，則程式`InvalidOperationException`代碼會擲回，因為 API 合約的使用不正確。

使用支援欄位時，您應該考慮某些程式庫可能會有特殊的考慮。 例如，EF Core 可能需要設定為正確使用[支援欄位](/ef/core/modeling/backing-field)。

### <a name="initialize-the-property-to-null"></a>將屬性初始化為 null

做為使用可為 null 之支援欄位的 terser 替代方案，或如果具現化類別的程式庫與該方法不相容，您可以直接將`null`屬性初始化為，並搭配 null-容許運算子（`!`）的協助：

```csharp
[Required]
public string FirstName { get; set; } = null!;

[Required]
public string LastName { get; set; } = null!;

public string? VehicleRegistration { get; set; }
```

您永遠不會在執行時間看到實際的 null 值，但由於程式設計錯誤的結果，會先存取屬性，再進行正確的初始化。

## <a name="see-also"></a>另請參閱

- [將現有的程式碼基底遷移至可為 Null 參考](tutorials/upgrade-to-nullable-references.md)
- [在 EF Core 中使用可為 Null 的參考型別](/ef/core/miscellaneous/nullable-reference-types)
