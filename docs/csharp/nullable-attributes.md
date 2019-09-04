---
title: 升級具有屬性的 Api 以定義 null 預期
description: 本文說明加入描述性屬性的動機和技術, 以描述引數的 null 狀態和 Api 的傳回值
ms.date: 07/31/2019
ms.openlocfilehash: eebd3d190b8c93833de6e1c1f1594c1c1f56e14e
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "70234672"
---
# <a name="update-libraries-to-use-nullable-reference-types-and-communicate-nullable-rules-to-callers"></a>更新程式庫以使用可為 null 的參考型別, 並將可為 null 的規則與呼叫端

加入[可為 null 的參考型別](nullable-references.md)表示您可以宣告每個變數`null`是否允許或預期值。 這會在您撰寫程式碼時提供絕佳的體驗。 如果不可為 null 的變數可能設定為`null`, 則會收到警告。 如果可為 null 的變數不是 null, 則您會收到警告, 然後再對其進行取值。 更新您的程式庫可能需要一些時間, 但回報值得一提。 *當*允許或禁止某個`null`值時, 您提供給編譯器的資訊越多, API 的使用者就會得到更好的警告。 讓我們從熟悉的範例開始。 假設您的程式庫具有下列 API 來抓取資源字串:

```csharp
bool TryGetMessage(string key, out string message)
```

上述範例會遵循 .net 中`Try*`熟悉的模式。 此 API 有兩個參考引數: `key` `message`和參數。 此 API 具有下列與這些引數的 null 相關的規則:

- 呼叫端不`null`應傳遞做為`key`的引數。
- 呼叫端可以傳遞一個變數, 其`null`值會當做的`message`引數。
- `TryGetMessage`如果`message`方法傳回`true`, 則的值不是 null。 如果傳回值是`false,` `message` (和其 null 狀態) 的值, 則為 null。

的規則`key`可以完全以變數類型表示: `key`應該是不可為 null 的參考型別。 `message`參數較複雜。 它允許`null`做為引數, 但可保證在成功時, `out`該引數不是 null。 在這些情況下, 您需要更豐富的詞彙來描述預期。

針對可為 null 的參考更新您的連結`?`庫, 在某些變數和類型名稱上不需要隨處揮灑 threadpool.queueuserworkitem。 上述範例顯示您需要檢查您的 Api, 並考慮每個輸入引數的預期。 請考慮傳回值的保證, 以及方法傳回`out`時`ref`的任何或引數。 然後將這些規則傳達給編譯器, 而編譯器會在呼叫者不遵守這些規則時提供警告。

此工作需要一些時間。 讓我們從策略開始, 將您的程式庫或應用程式設為可為 null 感知, 同時平衡其他需求和交付專案。 您將瞭解如何平衡進行中的開發, 並啟用可為 null 的參考型別。 您將會學到泛型型別定義的挑戰。 您將瞭解如何套用屬性, 以描述個別 Api 的前置和後置條件。

## <a name="choose-a-nullable-strategy"></a>選擇可為 null 的策略

第一個選擇是可為 null 的參考型別是否預設為開啟或關閉。 您有兩種策略:

- 為整個專案啟用可為 null 的參考型別, 並在未就緒的程式碼中停用它。
- 僅針對已針對可為 null 的參考型別標注的程式碼, 啟用可為 null 的參考型別。

當您將其他功能新增至程式庫時, 第一個策略的效果最佳, 是針對可為 null 的參考型別進行更新。 所有新的開發都是可為 null 的感知。 當您更新現有程式碼時, 您可以在這些類別中啟用可為 null 的參考型別。

遵循第一個策略, 您可以執行下列動作:

1. 將`<Nullable>enable</Nullable>`元素新增至您的 *.csproj*檔案, 為整個專案啟用可為 null 的類型。 
1. `#nullable disable`將 pragma 新增至專案中的每個原始程式檔。 
1. 當您處理每個檔案時, 請移除 pragma 並解決任何警告。

第一個策略有更多的最新工作, 可以將 pragma 新增至每個檔案。 優點是每個新增至專案的新程式碼檔案都可為 null 啟用。 任何新工作都可為 null 感知;僅必須更新現有的程式碼。

如果程式庫通常穩定, 第二個策略的效果更好, 而開發的主要重點是採用可為 null 的參考型別。 當您標注 Api 時, 您會開啟可為 null 的參考型別。 當您完成時, 您可以為整個專案啟用可為 null 的參考型別。

遵循第二個策略, 您可以執行下列動作:

1. `#nullable enable`將 pragma 新增到您想要使其成為可為 null 的檔案。
1. 解決任何警告。
1. 繼續執行前兩個步驟, 直到您將整個程式庫設為可為 null 為止。
1. 將`<Nullable>enable</Nullable>`元素新增至您的 *.csproj*檔案, 為整個專案啟用可為 null 的類型。 
1. `#nullable enable`移除 pragma, 因為已不再需要它。

第二個策略的處理時間較少。 缺點是, 當您建立新檔案時, 第一項工作是新增 pragma 並讓它成為可為 null 的感知。 如果您小組中的任何開發人員忘記, 新的程式碼現在已在工作待處理專案中, 使所有程式碼可為 null 感知。

您挑選的其中一個策略, 取決於您的專案中有多少使用中的開發。 您的專案越成熟且穩定, 第二個策略就越好。 開發的功能越多, 第一個策略就越好。

## <a name="should-nullable-warnings-introduce-breaking-changes"></a>可為 null 的警告是否會引進重大變更？

啟用可為 null 的參考型別之前, 變數會被視為*可為 null 的遺忘式*。 啟用可為 null 的參考型別後, 所有這些變數都*不可為 null*。 如果未將這些變數初始化為非 null 值, 編譯器會發出警告。

另一個可能的警告來源是值未初始化時的傳回值。

解決編譯器警告的第一個步驟是在參數和`?`傳回型別上使用注釋, 以指示引數或傳回值是否可以是 null。 當參考變數不得為 null 時, 原始宣告是正確的。 當您這麼做時, 您的目標不是要修正警告。 較重要的目標是讓編譯器瞭解潛在 null 值的意圖。 當您檢查這些警告時, 您會到達程式庫的下一個主要決策。 您是否想要考慮修改 API 簽章, 以更清楚地傳達您的設計意圖？ 更好的 API 簽章`TryGetMessage`適用于先前檢查的方法, 可能是:

```csharp
string? TryGetMessage(string key);
```

傳回值表示成功或失敗, 如果找到值, 則會攜帶值。 在許多情況下, 變更 API 簽章可以改善它們傳達 null 值的方式。

不過, 對於公用程式庫或具有大型使用者群的程式庫, 您可能不會想要引入任何 API 簽章變更。 針對這些案例和其他常見的模式, 您可以套用屬性, 以更清楚地定義引數或傳回值可能`null`的時機。 無論您是否考慮變更 API 的介面, 您可能會發現單獨的類型注釋並不足以描述`null`引數或傳回值的值。 在這些情況下, 您可以套用屬性, 以更清楚地描述 API。 

## <a name="attributes-extend-type-annotations"></a>屬性擴充類型注釋

已經加入數個屬性, 以表達變數的 null 狀態的其他相關資訊。 您在8之前C#撰寫的所有程式碼, 都是 null 的參考型別*遺忘式*。 這表示任何參考型別變數都可以是 null, 但不需要 null 檢查。 一旦您的程式碼*可為 null 感知*, 這些規則就會變更。 參考型別應該永遠不`null`會是值, 而且必須`null`先檢查可為 null 的參考型別, 然後再進行引用。

您的 api 規則可能會更複雜, 如您在`TryGetValue` API 案例中所見。 許多 Api 在變數可以或不是`null`時, 會有更複雜的規則。 在這些情況下, 您將使用下列其中一個屬性來表示這些規則:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute):不可為 null 的輸入引數可能是 null。
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute):可為 null 的輸入引數絕對不應為 null。
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute):不可為 null 的傳回值可以是 null。
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute):可為 null 的傳回值永遠不會是 null。
- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute):當傳回值符合`out`條件`ref`時, 不可為 null 或引數可能會是 null。
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute):當傳回`out`值`ref`符合條件時, 可為 null 或引數不可以是 null。
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute):如果指定參數的輸入引數不是 null, 則傳回值不是 null。

上述描述是每個屬性的快速參考。 下一節將詳細說明行為和意義。

新增這些屬性可讓編譯器詳細說明您 API 的規則。 在可為 null 的已啟用內容中編譯呼叫程式碼時, 編譯器會在呼叫端違反這些規則時發出警告。 這些屬性不會在您的執行上啟用額外的檢查。

## <a name="specify-preconditions-allownull-and-disallownull"></a>指定前置條件`AllowNull` : 和`DisallowNull`

請考慮永遠不會`null`傳回的讀取/寫入屬性, 因為它有合理的預設值。 當呼叫`null`端將它設定為預設值時, 會傳遞至 set 存取子。 例如, 假設有一個訊息系統會要求聊天室中的螢幕名稱。 如果未提供, 系統會產生隨機名稱:

```csharp
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName;
```

當您在可為 null 的遺忘式內容中編譯上述程式碼時, 一切都沒問題。 啟用可為 null 的`ScreenName`參考型別後, 屬性會變成不可為 null 的參考。 這對`get`存取子而言是正確的: `null`永遠不會傳回。 呼叫端不需要檢查傳回的屬性`null`。 但現在將屬性設定為`null`會產生警告。 為了繼續支援這種類型的程式碼, 您可以將<xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType>屬性新增至屬性, 如下列程式碼所示: 

```csharp
[AllowNull]
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName = GenerateRandomScreenName();
```

您可能需要新增的`using` <xref:System.Diagnostics.CodeAnalysis>指示詞, 才能使用此和本文中討論的其他屬性。 屬性會套用至屬性, 而不`set`是存取子。 屬性會指定*前置條件*, 而且只會套用至輸入。 `AllowNull` `get`存取子具有傳回值, 但沒有輸入引數。 因此, `AllowNull`屬性只適用`set`于存取子。

上述範例示範在引數上加入`AllowNull`屬性時要尋找的內容:

1. 該變數的一般合約是它不應該是`null`, 因此您需要不可為 null 的參考型別。
1. 雖然輸入變數`null`不是最常見的使用方式, 但還是有一些案例。

通常您需要屬性、 `in` `out`、和`ref`引數的這個屬性。 當變數通常不是 null 時, `null` 屬性是最佳選擇,但您必須允許做為前置條件。`AllowNull`

相較之下, 使用`DisallowNull`的案例如下:您可以使用這個屬性來指定可為 null 類型的輸入變數不應`null`為。 假設有一個屬性`null` , 其中是預設值, 但是用戶端只能將它設定為非 null 值。 請考慮下列程式碼：

```csharp
public string ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string _comment;
```

上述程式碼是表達設計`ReviewComment`的最佳方式, 可以是`null`, 但不能設定為`null`。 一旦這段程式碼可為 null, 您就可以更清楚地將此概念<xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType>表達給呼叫者, 使用:

```csharp
[DisallowNull] 
public string? ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string? _comment;
```

在可為 null 的內容`ReviewComment`中, `get`存取子可能會傳回`null`的預設值。 編譯器會警告您必須在存取之前先檢查它。 此外, 它也會警告呼叫端, 雖然呼叫端`null`不應該明確地將它設定`null`為。 屬性也會指定*前置條件*, 而不會影響`get`存取子。 `DisallowNull` 當您觀察下列有關的`DisallowNull`特性時, 應該選擇使用屬性:

1. 變數可能在核心`null`案例中, 通常是在第一次具現化時。
1. 變數不應明確設定為`null`。

這些情況在原本是*null 遺忘式*的程式碼中很常見。 這可能是在兩個不同的初始化作業中設定物件屬性。 這可能是某些屬性只有在一些非同步工作完成後才會設定。

`AllowNull` 和`DisallowNull`屬性可讓您指定變數上的前置條件可能不符合那些變數上的可為 null 注釋。 這些會提供 API 特性的更多詳細資料。 此額外資訊可協助呼叫者正確地使用您的 API。 請記住, 您可以使用下列屬性來指定前置條件:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute):不可為 null 的輸入引數可能是 null。
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute):可為 null 的輸入引數絕對不應為 null。

## <a name="specify-post-conditions-maybenull-and-notnull"></a>指定後置條件: `MaybeNull`和`NotNull`

假設您有一個具有下列簽章的方法:

```csharp
public Customer FindCustomer(string lastName, string firstName)
```

在找不到所尋找的名稱`null`時, 您可能會撰寫如下所示的方法來傳回。 `null`顯然會指出找不到記錄。 在此範例中, 您可能會將傳回型別`Customer`從`Customer?`變更為。 將傳回值宣告為可為 null 的參考型別, 可以清楚地指定這個 API 的意圖。 

基於[泛型定義和 null](#generic-definitions-and-nullability)屬性所涵蓋的原因, 這項技術無法與泛型方法搭配使用。 您的泛型方法可能會遵循類似的模式:

```csharp
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

您無法指定傳回值為`T?`。 找不到`null`尋找的專案時, 方法會傳回。 因為您無法`T?`宣告傳回型別, 所以您會`MaybeNull`將注釋加入至方法傳回:

```csharp
[return: MaybeNull]
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

上述程式碼會通知呼叫者, 合約隱含了不可為 null 的型別, 但傳回值實際上*可能*是 null。  當您的 API 應該是不可為 null 的型別 (通常是泛型型別參數) 時, 請使用`null` 屬性,但可能會傳回實例。`MaybeNull`

您也可以指定傳回值或`out`或`ref`引數不是 null, 即使該類型是可為 null 的類型也一樣。 假設有一個方法可確保陣列夠大, 足以容納多個元素。 如果輸入引數沒有容量, 常式會配置新的陣列, 並將所有現有的元素複製到其中。 如果輸入引數為`null`, 則常式會配置新的儲存區。 如果有足夠的容量, 常式不會執行任何動作:

```csharp
public void EnsureCapacity<T>(ref T[] storage, int size)
```

您可以呼叫此常式, 如下所示:

```csharp
// messages has the default value (null) when EnsureCapacity is called:
EnsureCapacity<string>(ref messages, 10);
// messages is not null.
EnsureCapacity<string>(messages, 50);
```

啟用 null 參考型別之後, 您想要確保先前的程式碼會編譯而不會出現警告。 當此方法傳回時, `storage`會保證引數不是 null。 不過, 您可以使用 null 參考`EnsureCapacity`來呼叫。 您可以建立`storage`可為 null 的參考型別, `NotNull`並將後續條件新增至參數宣告:

```csharp
public void EnsureCapacity<T>([NotNull]ref T[]? storage, int size)
```

上述程式碼非常清楚地表示現有的合約:呼叫端可以傳遞`null`值為的變數, 但傳回值保證永遠不會是 null。 屬性最適用于`ref`和`out`引數, 其中`null`可當做引數傳遞, 但當方法傳回時, 該引數保證不會是 null。 `NotNull`

您可以使用下列屬性來指定無條件的後置條件:

- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute):不可為 null 的傳回值可以是 null。
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute):可為 null 的傳回值永遠不會是 null。

## <a name="specify-conditional-post-conditions-notnullwhen-and-maybenullwhen"></a>指定條件式後置條件`NotNullWhen` : 和`MaybeNullWhen`

您很可能已經熟悉`string`方法。 <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> `true`當引數不是 null, 而不是空字串時, 這個方法會傳回。 這是一種 null 檢查的形式:如果方法`false`傳回, 則呼叫端不需要 null 檢查引數。 若要讓方法類似于可為 null 的感知, 您可以將引數設定為可為 null `NotNullWhen`的型別, 並新增屬性:

```csharp
bool IsNullOrEmpty([NotNullWhen(false)]string? value);
```

這會通知編譯器, 傳回值所`false`需的任何程式碼都不能以 null 檢查。 新增屬性會通知編譯器`IsNullOrEmpty`執行必要 null 檢查的靜態分析: 傳回時`false`, 輸入引數不`null`是。

```csharp
string? userInput = GetUserInput();
if (!(string.IsNullOrEmpty(userInput))
{
   int messageLength = userInput.Length; // no null check needed.
}
// null check needed on userInput here.
```

<xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>方法將會針對 .net Core 3.0 標注為如上所示。 您的程式碼基底中可能會有類似的方法, 可檢查物件的狀態是否為 null 值。 編譯器不會辨識自訂的 null 檢查方法, 您必須自行新增批註。 當您新增屬性時, 編譯器的靜態分析會知道已檢查過測試的變數何時已進行 null。

這些屬性的另一個用法是`Try*`模式。 `ref` 和`out`變數的後置條件會透過傳回值進行通訊。 請考慮稍早所示的這個方法:

```csharp
bool TryGetMessage(string key, out string message)
```

上述方法會遵循一般的 .net 用法: 傳回值會指出`message`是否設定為找到的值, 或如果找不到任何訊息, 則為預設值。 如果方法`true`傳回, 的`message`值不是 null, 否則, 方法會將設定`message`為 null。

您可以使用`NotNullWhen`屬性來傳達該用法。 當您更新可為 null 之參考型別的簽`message`章`string?`時, 請建立並加入屬性:

```csharp
bool TryGetMessage(string key, [NotNullWhen(true)] out string? message)
```

在上述範例中, `message` `true`當傳回時`TryGetMessage` , 的值已知為 not null。 您應該以相同的方式, 在程式碼基底中標注類似的方法`null`: 引數可能是, 而`true`方法傳回時已知為 not null。

還有一個您可能也需要的最終屬性。 有時傳回值的 null 狀態會視一或多個輸入引數的 null 狀態而定。 每當特定輸入引數不是`null`時, 這些方法會傳回非 null 值。 若要正確地為這些方法加上`NotNullIfNotNull`批註, 您可以使用屬性。 請考慮下列方法:

```csharp
string GetTopLevelDomainFromFullUrl(string url);
```

如果引數不是 null, 輸出就`null`不會。 `url` 啟用可為 null 的參考後, 如果您的 API 永遠不接受 null 輸入, 則該簽章會正常運作。 不過, 如果輸入可以是 null, 則傳回值也可以是 null。 因此, 您可以將簽章變更為下列程式碼:

```csharp
string? GetTopLevelDomainFromFullUrl(string? url);
```

這也可行, 但是通常會強制呼叫者執行額外`null`的檢查。 合約是`null`只有當輸入引數`url`為`null`時, 傳回值才會是。 若要表達該合約, 您可以標注此方法, 如下列程式碼所示:

```csharp
[return: NotNullIfNotNull("url")]
string? GetTopLevelDomainFromFullUrl(string? url);
```

傳回值和引數都已使用`?`標注, 表示可能是。 `null` 屬性會進一步說明當`url`引數不`null`是時, 傳回值不會是 null。

您可以使用下列屬性來指定條件性後置條件:

- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute):當傳回值符合`out`條件`ref`時, 不可為 null 或引數可能會是 null。
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute):當傳回`out`值`ref`符合條件時, 可為 null 或引數不可以是 null。
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute):如果指定參數的輸入引數不是 null, 則傳回值不是 null。

## <a name="generic-definitions-and-nullability"></a>泛型定義和 null 屬性

正確地傳達泛型型別和泛型方法的 null 狀態需要特別小心。 這源自于可為 null 的實值型別和可為 null 的參考型別, 基本上是不同的事實。 是的`string?`同義字, 而則是`string`由編譯器新增的屬性。 `Nullable<int>` `int?` 結果是, 編譯器無法產生的正確`T?`程式碼, 而不`T`知道是`class`或`struct`。 

這並不表示您無法使用可為 null 的類型 (實數值型別或參考型別) 做為封閉式泛型型別的類型引數。 和都是的`List<T>`有效具現化。 `List<int?>` `List<string?>` 

它的意思是, 您無法在沒有`T?`條件約束的泛型類別或方法宣告中使用。 例如, <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType>不會變更`T?`為傳回。 您可以藉由新增`struct`或`class`條件約束來克服這項限制。 使用上述任一條件約束時, 編譯器會知道如何為`T`和`T?`產生程式碼。

您可能想要將泛型型別引數所使用的類型限制為不可為 null 的類型。 您可以在該型別自`notnull`變數上加入條件約束來達到這個目的。 套用該條件約束時, 類型引數不能是可為 null 的類型。

## <a name="conclusions"></a>結論

加入可為 null 的參考型別會`null`提供初始詞彙, 以描述您的 api 對可能的變數的期望。 其他屬性會提供更豐富的詞彙, 將變數的 null 狀態原因為前置條件和後置條件。 這些屬性會更清楚地描述您的期望, 並為使用您 Api 的開發人員提供更好的體驗。

當您更新可為 null 內容的程式庫時, 請新增這些屬性以引導 Api 的使用者使用正確的用法。 這些屬性可協助您完整描述輸入引數和傳回值的 null 狀態:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute):不可為 null 的輸入引數可能是 null。
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute):可為 null 的輸入引數絕對不應為 null。
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute):不可為 null 的傳回值可以是 null。
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute):可為 null 的傳回值永遠不會是 null。
- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute):當傳回值符合`out`條件`ref`時, 不可為 null 或引數可能會是 null。
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute):當傳回`out`值`ref`符合條件時, 可為 null 或引數不可以是 null。
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute):如果指定參數的輸入引數不是 null, 則傳回值不是 null。
