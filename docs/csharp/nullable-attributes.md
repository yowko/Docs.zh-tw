---
title: 使用定義對空值的預期的屬性升級可空參考型別的 API
description: 瞭解如何使用描述性屬性"允許無效"、可能無效、無虛無等來完全描述 API 的空狀態。
ms.technology: csharp-null-safety
ms.date: 07/31/2019
ms.openlocfilehash: ca04db800271b9b01b5b9f1482dd5a0db2cc1c35
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249241"
---
# <a name="update-libraries-to-use-nullable-reference-types-and-communicate-nullable-rules-to-callers"></a>更新庫以使用空參考型別，並將無效規則傳達給調用方

添加[可取消的參考型別](nullable-references.md)意味著您可以聲明`null`是否允許或預期每個變數的值。 此外`AllowNull`，還可以應用許多屬性： `DisallowNull`、 `MaybeNull`、 `NotNull`、 `NotNullWhen`、 `MaybeNullWhen`、 `NotNullWhenNotNull` 、 、 、 、 、 、 和 ， 並完全描述參數和傳回值的 null 狀態。 在編寫代碼時，這提供了很好的體驗。 如果非空變數可能設置為`null`，則會收到警告。 如果在取消引用之前未選中空變數，則會收到警告。 更新庫可能需要一些時間，但回報是值得的。 您向編譯器提供的關於*何時*允許或禁止`null`值的資訊越多，API 使用者得到的更好警告。 讓我們從一個熟悉的例子開始。 假設您的庫具有以下 API 來檢索資源字串：

```csharp
bool TryGetMessage(string key, out string message)
```

前面的示例遵循 .NET`Try*`中熟悉的模式。 此 API 有兩個傳址參數：`key`和 參數`message`。 此 API 具有以下與這些參數的無效性相關的規則：

- 調用方不應作為`null``key`的參數傳遞。
- 調用方可以傳遞其值為`null``message`的變數作為 的 參數。
- 如果`TryGetMessage`方法返回`true`，則`message`的值不為空。 如果傳回值為`false,` `message` （及其 null 狀態） 的值為 null。

的規則`key`可以通過變數類型完全表示：`key`應該是一個不可空的參考型別。 參數`message`更為複雜。 它允許`null`作為參數，但保證，在成功時，該`out`參數不為空。 對於這些方案，您需要更豐富的詞彙來描述期望值。

更新庫以進行空引用需要的不僅僅是灑`?`灑某些變數和類型名稱。 前面的示例表明，您需要檢查 API 並考慮您對每個輸入參數的期望。 考慮傳回值的保證，以及方法返回時`out`的任何`ref`或參數。 然後，將這些規則傳達給編譯器，當調用方不遵守這些規則時，編譯器將提供警告。

這項工作需要時間。 讓我們從使庫或應用程式具有空感知性的策略開始，同時平衡其他要求和可交付成果。 您將看到如何平衡支援空參考型別的持續開發。 您將瞭解泛型型別定義的挑戰。 您將學習應用屬性來描述單個 API 的預置和後置條件。

## <a name="choose-a-strategy-for-nullable-reference-types"></a>為空參考型別選擇策略

第一種選擇是預設是可空參考型別應打開還是關閉。 您有兩種策略：

- 為整個專案啟用空參考型別，並在未準備好的代碼中禁用它。
- 僅為已為空參考型別提供已注明的代碼的可啟用參考型別。

當您為庫更新其他要素以進行空參考型別更新時，第一個策略效果最佳。 所有新開發都是空意識的。 更新現有代碼時，在這些類中啟用空參考型別。

遵循第一個策略，執行以下操作：

1. 通過將元素添加到`<Nullable>enable</Nullable>`*csproj*檔，為整個專案啟用可不正確參考型別。
1. 將`#nullable disable`實用方案添加到專案中的每個原始檔案。
1. 處理每個檔時，請刪除雜注並解決任何警告。

第一個策略具有更多的前期工作，以將實用處理添加到每個檔。 優點是，添加到專案的每個新代碼檔都將為空。 任何新工作都將是可撤銷的;只能更新現有代碼。

如果庫總體穩定，第二種策略效果更好，開發的重點是採用可無參考型別。 在對 API 進行編號時，打開可取消的參考型別。 完成後，將對整個專案啟用空參考型別。

遵循第二個策略，您可以執行以下操作：

1. 將`#nullable enable`雜注添加到要使空感知的檔中。
1. 解決任何警告。
1. 繼續前兩個步驟，直到使整個庫都為空所知。
1. 通過將元素添加到`<Nullable>enable</Nullable>`*csproj*檔，為整個專案啟用可不正確類型。
1. 刪除`#nullable enable`雜注，因為它們不再需要。

第二種戰略前期工作較少。 權衡是，創建新檔時的第一個任務是添加雜注並使之無效。 如果團隊中的任何開發人員忘記了該新代碼，則新代碼現在處於工作積壓中，以使所有代碼都為空所知。

您選擇哪些策略取決於專案中正在進行多少主動開發。 專案越成熟、越穩定，第二個策略越好。 正在開發的功能越多，第一個策略越好。

## <a name="should-nullable-warnings-introduce-breaking-changes"></a>無效警告是否應引入重大更改？

在啟用可取消參考型別之前，變數被視為*空忘*。 啟用空參考型別後，所有這些變數都是*非空的*。 如果這些變數未初始化為非空值，編譯器將發出警告。

另一個可能的警告來源是在尚未初始化該值時傳回值。

解決編譯器警告的第一步是對參數和返回類型`?`使用注釋來指示參數或傳回值何時可能為空。 當引用變數不能為空時，原始聲明是正確的。 執行此操作時，您的目標不僅僅是修復警告。 更重要的目標是使編譯器瞭解您對於潛在空值的意圖。 在檢查警告時，您將得出庫的下一個重大決策。 是否要考慮修改 API 簽名以更清楚地傳達您的設計意圖？ 前面檢查`TryGetMessage`的方法更好的 API 簽名可以是：

```csharp
string? TryGetMessage(string key);
```

傳回值指示成功或失敗，如果找到該值，則攜帶該值。 在許多情況下，更改 API 簽名可以改進它們傳達空值的方式。

但是，對於公共圖書館或具有大型使用者群的庫，您可能不希望引入任何 API 簽名更改。 對於這些情況和其他常見模式，可以將屬性應用於更明確地定義參數或傳回值何時可能是`null`。 無論您是否考慮更改 API 的表面，您都可能會發現，僅類型注釋不足以描述`null`參數或傳回值的值。 在這些情況下，可以將屬性應用於更清晰地描述 API。

## <a name="attributes-extend-type-annotations"></a>屬性擴展類型注釋

添加了多個屬性以表示有關變數的 null 狀態的其他資訊。 在 C# 8 引入可無參考型別之前編寫的所有代碼都是*不正確。* 這意味著任何參考型別變數可能為空，但不需要 null 檢查。 一旦代碼*是空的，* 這些規則就會改變。 參考型別絕不應為`null`值，並且在取消引用之前必須針對`null`選中可消除的參考型別。

API 的規則可能更為複雜，正如您在 API 方案中所看到的那樣`TryGetValue`。 許多 API 對於變數可以或不能是`null`時，都有更複雜的規則。 在這些情況下，您將使用以下屬性之一來表示這些規則：

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute)： 不可不正確輸入參數可能為空。
- [禁止無效](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute)：可空輸入參數絕不應為空。
- [可能 Null](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute)： 不可取消的傳回值可能為 null。
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute)： 空傳回值永遠不會為空。
- [當](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute)方法返回指定的`bool`值時，可能 Null 時：非空輸入參數可能為空。
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute)：當方法返回指定的`bool`值時，可 null 的輸入參數不會為空。
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute)：如果指定參數的參數不是 null，則傳回值不為空。

前面的說明是每個屬性執行功能的快速引用。 以下各節更全面地描述行為和含義。

添加這些屬性為編譯器提供有關 API 規則的詳細資訊。 在啟用空的上下文中編譯調用代碼時，編譯器將在調用方違反這些規則時發出警告。 這些屬性無法對實現啟用其他檢查。

## <a name="specify-preconditions-allownull-and-disallownull"></a>指定先決條件：`AllowNull`和`DisallowNull`

請考慮從不返回`null`的讀/寫屬性，因為它具有合理的預設值。 將調用方`null`設置為該預設值時，將傳遞給集訪問器。 例如，考慮在聊天室中要求顯示幕幕名稱的郵件系統。 如果未提供，系統將生成隨機名稱：

```csharp
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName;
```

當您在一個不正確遺忘上下文中編譯前面的代碼時，一切都很好。 啟用空參考型別後，該`ScreenName`屬性將成為不可取消的引用。 這對`get`訪問者是正確的：它永遠不會返回`null`。 調用方不需要檢查 返回的屬性。 `null` 但現在將屬性設置為`null`生成警告。 為了繼續支援這種類型的代碼，將<xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType>屬性添加到屬性，如以下代碼所示：

```csharp
[AllowNull]
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName = GenerateRandomScreenName();
```

您可能需要添加一個`using`指令，以便<xref:System.Diagnostics.CodeAnalysis>使用此屬性和本文中討論的其他屬性。 該屬性應用於屬性，而不是`set`訪問器。 屬性`AllowNull`指定*先決條件*，並且僅適用于輸入。 `get`訪問器具有傳回值，但沒有輸入參數。 因此，該`AllowNull`屬性僅適用于`set`訪問器。

前面的示例演示了在參數上添加`AllowNull`屬性時要查找的內容：

1. 該變數的一般協定是，它不應該是`null`，因此您需要一個不可取消的參考型別。
1. 輸入變數有一些方案，`null`儘管它們不是最常見的用法。

通常，屬性或`in`或 或`out`. 和`ref`參數需要此屬性。 當`AllowNull`變數通常是非空的，但您需要作為先決條件允許`null`時，該屬性是最佳選擇。

與使用`DisallowNull`： 的方案相比，使用此屬性指定 null 參考型別的輸入變數不應為`null`。 請考慮一個屬性`null`，其中是預設值，但用戶端只能將其設置為非 null 值。 請考慮下列程式碼：

```csharp
public string ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string _comment;
```

前面的代碼是表達設計的最佳方式，`ReviewComment`可以是`null`，但不能設置為`null`。 一旦此代碼是空的，您可以使用 更清楚地向調用方表達這一<xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType>概念：

```csharp
[DisallowNull]
public string? ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string? _comment;
```

在空上下文中，`ReviewComment``get`訪問器可以返回 的`null`預設值 。 編譯器警告必須在訪問之前檢查它。 此外，它警告調用方，即使它可能是`null`，調用方也不應顯式將其設置為`null`。 該`DisallowNull`屬性還指定*一個先決條件*，它不會影響`get`訪問器。 當您觀察以下特徵時，`DisallowNull`應選擇使用該屬性：

1. 變數可能`null`位於核心方案中，通常是在第一次具現化時。
1. 變數不應顯式設置為`null`。

這些情況在最初*為空遺忘*的代碼中很常見。 可能是物件屬性設置在兩個不同的初始化操作中。 可能某些屬性僅在某些非同步工作完成後進行設置。

`AllowNull`和`DisallowNull`屬性使您能夠指定變數的先決條件可能與這些變數上的空注釋不匹配。 這些提供了有關 API 特徵的更多詳細資訊。 此附加資訊可説明調用方正確使用 API。 請記住，您使用以下屬性指定先決條件：

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute)： 不可不正確輸入參數可能為空。
- [禁止無效](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute)：可空輸入參數絕不應為空。

## <a name="specify-post-conditions-maybenull-and-notnull"></a>指定後條件：`MaybeNull`和`NotNull`

假設您有一個具有以下簽名的方法：

```csharp
public Customer FindCustomer(string lastName, string firstName)
```

您可能已經編寫了這樣的方法，在未找到要`null`找的名稱時返回。 清楚地`null`指示找不到記錄。 在此示例中，可能會將返回類型從`Customer`更改為`Customer?`。 將傳回值聲明為空參考型別明確指定此 API 的意圖。

由於[泛型定義和無效性](#generic-definitions-and-nullability)所涵蓋的原因，該技術不適用於泛型方法。 您可能有一個遵循類似模式的泛型方法：

```csharp
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

不能指定傳回值為`T?`。 當未找到`null`要求的的項時，該方法將返回。 由於無法聲明`T?`返回類型，因此將`MaybeNull`注釋添加到方法返回：

```csharp
[return: MaybeNull]
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

前面的代碼通知調用方協定意味著一種不可空的類型，但傳回值*實際上可能*為空。  當`MaybeNull`API 應為非空類型（通常是泛型型別參數），但可能存在返回的`null`實例時，請使用該屬性。

還可以指定傳回值或 或`out`或 參數`ref`不為空，即使類型為空參考型別。 考慮一種確保陣列足夠大以容納多個元素的方法。 如果輸入參數沒有容量，常式將分配一個新陣列並將所有現有元素複製到其中。 如果輸入參數為`null`，常式將分配新的存儲。 如果容量充足，常式將不執行任何操作：

```csharp
public void EnsureCapacity<T>(ref T[] storage, int size)
```

您可以按照如下方式調用此常式：

```csharp
// messages has the default value (null) when EnsureCapacity is called:
EnsureCapacity<string>(ref messages, 10);
// messages is not null.
EnsureCapacity<string>(messages, 50);
```

啟用空參考型別後，您希望確保前面的代碼在無警告的情況下編譯。 當方法返回時，`storage`參數保證不為空。 但是，使用空引用進行調用`EnsureCapacity`是可以接受的。 您可以創建`storage`一個空參考型別，並將`NotNull`後條件添加到參數聲明：

```csharp
public void EnsureCapacity<T>([NotNull]ref T[]? storage, int size)
```

前面的代碼非常清楚地表示現有協定：調用方可以傳遞具有該值的`null`變數，但傳回值保證永遠不會為空。 該`NotNull`屬性對於`ref`和`out`參數最有用，`null`其中可以作為參數傳遞，但當方法返回時，該參數保證不為空。

使用以下屬性指定無條件的後情況：

- [可能 Null](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute)： 不可取消的傳回值可能為 null。
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute)： 空傳回值永遠不會為空。

## <a name="specify-conditional-post-conditions-notnullwhen-maybenullwhen-and-notnullifnotnull"></a>指定條件後條件： `NotNullWhen`、`MaybeNullWhen`和`NotNullIfNotNull`

你可能熟悉這種方法`string`<xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>。 當參數為`true`空字串或空字串時，此方法將返回。 它是一種 null 檢查形式：如果方法返回`false`，調用方不需要對參數進行空檢查。 要使此類方法具有 null 感知，您需要將參數設置為可 null 參考型別，並添加屬性`NotNullWhen`：

```csharp
bool IsNullOrEmpty([NotNullWhen(false)]string? value);
```

這通知編譯器不需要對傳回值`false`的任何代碼進行空檢查。 屬性的添加通知編譯器的靜態分析，該`IsNullOrEmpty`分析執行必要的 null 檢查：當它返回`false`時，輸入參數不是`null`。

```csharp
string? userInput = GetUserInput();
if (!string.IsNullOrEmpty(userInput))
{
   int messageLength = userInput.Length; // no null check needed.
}
// null check needed on userInput here.
```

該方法<xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>將如上所述.NET Core 3.0的用點子。 代碼庫中可能也有類似的方法，用於檢查物件的狀態為 null 值。 編譯器不會識別自訂 null 檢查方法，您需要自己添加注釋。 添加屬性時，編譯器的靜態分析知道測試變數何時被空檢查。

這些屬性的另一個用途是`Try*`模式。 和`out`變數的`ref`後情況通過傳回值進行通信。 請考慮前面顯示的方法：

```csharp
bool TryGetMessage(string key, out string message)
```

前面的方法遵循典型的 .NET 習慣用法：傳回值指示`message`是否設置為找到的值，或者如果沒有找到消息，則指示預設值。 如果方法返回`true`，則 的值`message`不為 null;如果 方法返回 ，則 值為 null。否則，該方法將設置`message`為 null。

您可以使用`NotNullWhen`屬性來傳達該習慣用法。 更新可空參考型別的簽名時，請創建`message``string?`並添加屬性：

```csharp
bool TryGetMessage(string key, [NotNullWhen(true)] out string? message)
```

在前面的示例中，`message`當返回`TryGetMessage``true`時，值已知不為 null。 應在代碼庫中以相同的方式對類似的方法進行編帶：當方法返回`null``true`時，參數可以是 ，並且已知為不為空。

還有一個最終屬性，您可能還需要。 有時，傳回值的 null 狀態取決於一個或多個輸入參數的 null 狀態。 當某些輸入參數不是`null`時，這些方法將返回一個非空值。 要正確對這些方法進行給上用，請使用 屬性`NotNullIfNotNull`。 請考慮以下方法：

```csharp
string GetTopLevelDomainFromFullUrl(string url);
```

如果`url`參數不為空，則輸出不是`null`。 啟用了可無效引用後，該簽名將正常工作，前提是 API 永遠不會接受空輸入。 但是，如果輸入可以為空，則傳回值也可以為空。 因此，您可以將簽名更改為以下代碼：

```csharp
string? GetTopLevelDomainFromFullUrl(string? url);
```

這也行得通，但通常會強制調用方實施額外的`null`檢查。 協定是傳回值僅在輸入參數`null``url`為`null`時才。 要表示該協定，您需要對此方法進行編號，如以下代碼所示：

```csharp
[return: NotNullIfNotNull("url")]
string? GetTopLevelDomainFromFullUrl(string? url);
```

傳回值和參數都帶有`?`指示，指示任一可以是`null`。 該屬性進一步闡明，當參數不是`url``null`時，傳回值不會為空。

使用這些屬性指定條件後條件：

- [當](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute)方法返回指定的`bool`值時，可能 Null 時：非空輸入參數可能為空。
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute)：當方法返回指定的`bool`值時，可 null 的輸入參數不會為空。
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute)：如果指定參數的輸入參數不是 null，則傳回值不為空。

## <a name="generic-definitions-and-nullability"></a>通用定義和空值

正確傳達泛型型別和泛型方法的 null 狀態需要特別注意。 這是因為可 null 數值型別和空參考型別根本不同。 是 的同`Nullable<int>`義詞，而`string?`與編譯器添加`string`的屬性一起。 `int?` `T?`結果是，如果不知道是`T`.`class`或 ， 編譯器無法生成正確的代碼。 `struct`

這並不意味著不能使用空類型（數值型別或參考型別）作為閉合泛型的類型參數。 和`List<string?>``List<int?>`都是`List<T>`的有效具現化。

它的意思是，在泛型類或方法聲明中，`T?`沒有約束，不能使用。 例如，<xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType>不會更改為返回`T?`。 您可以通過添加 或`struct``class`約束來克服此限制。 對於其中任一約束，編譯器知道如何為 和`T``T?`生成代碼。

您可能希望將泛型型別參數使用的類型限制為非空類型。 可以通過添加該類型參數的約束`notnull`來執行此操作。 應用該約束時，類型參數不能為空類型。

## <a name="conclusions"></a>結論

添加可取消的參考型別提供了一個初始詞彙表來描述 API 對可能為`null`的變數的期望。 附加屬性提供了更豐富的詞彙，將變數的 null 狀態原因為先決條件和後條件。 這些屬性更清楚地描述了您的期望，並為使用 API 的開發人員提供更好的體驗。

更新可無效上下文的庫時，請添加這些屬性以引導 API 的使用者使用正確的方法。 這些屬性可説明您完全描述輸入參數和傳回值的 null 狀態：

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute)： 不可不正確輸入參數可能為空。
- [禁止無效](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute)：可空輸入參數絕不應為空。
- [可能 Null](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute)： 不可取消的傳回值可能為 null。
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute)： 空傳回值永遠不會為空。
- [當](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute)方法返回指定的`bool`值時，可能 Null 時：非空輸入參數可能為空。
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute)：當方法返回指定的`bool`值時，可 null 的輸入參數不會為空。
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute)：如果指定參數的輸入參數不是 null，則傳回值不為空。
