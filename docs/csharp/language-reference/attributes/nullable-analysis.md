---
title: 'C # 保留屬性：可為 Null 的靜態分析'
ms.date: 04/14/2020
description: 編譯器會解讀這些屬性，以提供可為 null 且不可為 null 的參考型別的更佳靜態分析。
ms.openlocfilehash: d2405162ece3df209111de65fdef54f70cc86d45
ms.sourcegitcommit: 1e8382d0ce8b5515864f8fbb178b9fd692a7503f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2020
ms.locfileid: "89656300"
---
# <a name="reserved-attributes-contribute-to-the-compilers-null-state-static-analysis"></a>保留的屬性有助於編譯器的 null 狀態靜態分析

在可為 null 的內容中，編譯器會執行程式碼的靜態分析，以判斷所有參考型別變數的 null 狀態：

- *not null*：靜態分析判斷變數已指派給非 null 值。
- *可能是 null*：靜態分析無法判斷變數是否已指派非 null 值。

您可以套用多個屬性，以提供有關 Api 之語義的資訊給編譯器。 這項資訊可協助編譯器執行靜態分析，並判斷變數是否為 null。 本文提供每個屬性的簡短描述，以及如何使用這些屬性。 所有範例都採用 c # 8.0 或更新版本，且程式碼位於可為 null 的內容中。

讓我們從熟悉的範例開始。 假設您的程式庫有下列 API 可取得資源字串：

```csharp
bool TryGetMessage(string key, out string message)
```

上述範例會遵循 `Try*` .net 中熟悉的模式。 此 API 有兩個參考引數： `key` 和 `message` 參數。 此 API 具有下列與這些引數 null f.23 相關的規則：

- 呼叫端不應該傳遞 `null` 做為的引數 `key` 。
- 呼叫端可以傳遞變數，其值為 `null` 的引數 `message` 。
- 如果 `TryGetMessage` 方法傳回 `true` ，的值 `message` 不是 null。 如果傳回值是 `false,` (的值 `message` ，且其 null 狀態) 為 null。

的規則 `key` 可以用變數型別表示： `key` 應為不可為 null 的參考型別。 `message`參數較為複雜。 它可 `null` 做為引數，但保證在成功時，該 `out` 引數不是 null。 在這些情況下，您需要更豐富的詞彙來描述期望。

已加入數個屬性，以表達變數 null 狀態的其他相關資訊。 您在 c # 8 之前撰寫的所有程式碼都是 null 的參考型別 *無警示*。 這表示任何參考型別變數可能是 null，但不需要 null 檢查。 當您的程式碼 *可為 null 感知*時，這些規則就會變更。 參考型別絕對不應該是 `null` 值，而且必須先檢查可為 null 的參考型別， `null` 再進行取值。

您的 Api 規則可能更複雜，如您在 API 案例中所見 `TryGetValue` 。 許多 Api 都有更複雜的規則，可供變數或無法使用 `null` 。 在這些情況下，您將使用下列其中一個屬性來表示這些規則：

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute)：不可為 null 的輸入引數可能是 null。
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute)：可為 null 的輸入引數永遠不應為 null。
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute)：不可為 null 的傳回值可能是 null。
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute)：可為 null 的傳回值絕對不會是 null。
- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute)：當方法傳回指定的值時，不可為 null 的輸入引數可能是 null `bool` 。
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute)：當方法傳回指定的值時，可為 null 的輸入引數不會是 null `bool` 。
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute)：如果指定參數的引數不是 null，則傳回值不是 null。
- [DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute)：方法永遠不會傳回。 換句話說，它一律會擲回例外狀況。
- [DoesNotReturnIf](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute)：如果相關聯的 `bool` 參數具有指定的值，則不會傳回這個方法。

上述描述可快速參考每個屬性的用途。 下一節會更詳盡地說明行為和意義。

新增這些屬性可讓編譯器更詳細地瞭解您的 API 規則。 在可為 null 的已啟用內容中編譯呼叫程式碼時，編譯器會在違反這些規則時警告呼叫端。 這些屬性不會在您的執行上啟用其他檢查。

## <a name="specify-preconditions-allownull-and-disallownull"></a>指定前置條件： `AllowNull` 和 `DisallowNull`

請考慮永遠不會傳回的讀取/寫入屬性， `null` 因為它具有合理的預設值。 將呼叫端 `null` 設定為預設值時，呼叫端會傳遞至 set 存取子。 例如，假設有一個訊息系統要求您在聊天室中提供螢幕名稱。 如果沒有提供，系統會產生隨機名稱：

```csharp
public string ScreenName
{
   get => _screenName;
   set => _screenName = value ?? GenerateRandomScreenName();
}
private string _screenName;
```

當您在可為 null 的無警示內容中編譯上述程式碼時，一切都沒問題。 啟用可為 null 的參考型別之後， `ScreenName` 屬性會變成不可為 null 的參考。 這對存取子而言是正確的 `get` ：它永遠不會傳回 `null` 。 呼叫端不需要檢查傳回的屬性 `null` 。 但現在設定屬性以 `null` 產生警告。 為了繼續支援這種類型的程式碼，您可以將 <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType> 屬性加入至屬性中，如下列程式碼所示：

```csharp
[AllowNull]
public string ScreenName
{
   get => _screenName;
   set => _screenName = value ?? GenerateRandomScreenName();
}
private string _screenName = GenerateRandomScreenName();
```

您可能需要加入的指示詞， `using` <xref:System.Diagnostics.CodeAnalysis> 才能使用此程式和本文中討論的其他屬性。 屬性（attribute）會套用至屬性（property），而不是 `set` 存取子。 `AllowNull`屬性會指定*前置條件*，而且只會套用至輸入。 `get`存取子有傳回值，但沒有輸入引數。 因此， `AllowNull` 屬性只會套用至 `set` 存取子。

上述範例示範在引數上加入屬性時要尋找的內容 `AllowNull` ：

1. 該變數的一般合約是它不應該是 `null` ，因此您想要使用不可為 null 的參考型別。
1. 雖然輸入變數不是 `null` 最常見的使用方式，但仍有一些案例。

大部分情況下，您都需要屬性、、 `in` `out` 和引數的這個屬性 `ref` 。 `AllowNull`當變數通常為非 null 時，屬性是最佳選擇，但您必須允許 `null` 前置條件。

相較之下，使用的案例 `DisallowNull` ：您可以使用這個屬性來指定可為 null 的參考型別的輸入變數不應該是 `null` 。 請考慮屬性 `null` ，其中是預設值，但用戶端只能將它設定為非 null 值。 請考慮下列程式碼：

```csharp
public string ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string _comment;
```

上述程式碼是表達您設計的最佳方式 `ReviewComment` `null` ，但無法設定為 `null` 。 一旦這段程式碼可成為可為 null 的可感知，您就可以更清楚地向呼叫者表達這個概念 <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType> ：

```csharp
[DisallowNull]
public string? ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string? _comment;
```

在可為 null 的內容中， `ReviewComment` `get` 存取子可能會傳回的預設值 `null` 。 編譯器會警告您必須在存取之前檢查它。 此外，它也會警告呼叫端（即使可能的話 `null` ），呼叫端不應該將它明確設定為 `null` 。 `DisallowNull`屬性也會指定*前置條件*，而不會影響 `get` 存取子。 `DisallowNull`當您觀察這些特性時，請使用屬性：

1. 變數可能 `null` 在核心案例中，通常是在第一次具現化時。
1. 變數不應明確設定為 `null` 。

這些情況在原本是 *null 無警示*的程式碼中很常見。 可能是物件屬性是在兩個不同的初始化作業中所設定。 可能是某些屬性只有在某些非同步工作完成後才會設定。

`AllowNull`和 `DisallowNull` 屬性可讓您指定變數上的前置條件可能不符合這些變數上的可為 null 注釋。 這些會提供 API 特性的更多詳細資料。 此額外資訊可協助呼叫端正確地使用您的 API。 請記住，您可以使用下列屬性來指定前置條件：

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute)：不可為 null 的輸入引數可能是 null。
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute)：可為 null 的輸入引數永遠不應為 null。

## <a name="specify-post-conditions-maybenull-and-notnull"></a>指定後置條件： `MaybeNull` 和 `NotNull`

假設您有一個具有下列簽章的方法：

```csharp
public Customer FindCustomer(string lastName, string firstName)
```

您可能會撰寫如下所示的方法，以在找不到找不到 `null` 的名稱時傳回。 `null`顯然會指出找不到記錄。 在此範例中，您可能會將傳回類型從變更 `Customer` 為 `Customer?` 。 將傳回值宣告為可為 null 的參考型別，可明確指定此 API 的意圖。

基於泛型定義下所涵蓋的原因 [，以及](../../nullable-migration-strategies.md#generic-definitions-and-nullability) 此技術無法使用泛型方法的 null 屬性。 您可能會有遵循類似模式的泛型方法：

```csharp
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> predicate)
```

您無法指定傳回值為 `T?` 。 `null`找不到搜尋的專案時，方法會傳回。 由於您無法宣告傳回 `T?` 型別，因此您會將 `MaybeNull` 批註加入至方法傳回：

```csharp
[return: MaybeNull]
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> predicate)
```

上述程式碼會通知呼叫者，合約意指不可為 null 的型別，但是傳回值實際上 *可能* 是 null。  `MaybeNull`當您的 API 應為不可為 null 的類型（通常是泛型型別參數）時，請使用屬性，但可能會有可能會傳回的實例 `null` 。

`out`即使型別是可為 null 的參考型別，您也可以指定傳回值或或 `ref` 引數不是 null。 假設有一個方法可確保陣列夠大，足以容納一些元素。 如果輸入引數沒有容量，則常式會配置新的陣列，並將所有現有的元素複製到其中。 如果輸入引數是 `null` ，則常式會配置新的儲存區。 如果有足夠的容量，常式不會執行任何動作：

```csharp
public void EnsureCapacity<T>(ref T[] storage, int size)
```

您可以呼叫此常式，如下所示：

```csharp
// messages has the default value (null) when EnsureCapacity is called:
EnsureCapacity<string>(ref messages, 10);
// messages is not null.
EnsureCapacity<string>(messages, 50);
```

啟用 null 參考型別之後，您想要確保先前的程式碼會進行編譯而不發出警告。 當方法傳回時， `storage` 引數保證不是 null。 不過，您可以 `EnsureCapacity` 使用 null 參考來呼叫。 您可以建立 `storage` 可為 null 的參考型別，並將 `NotNull` 後置條件新增至參數宣告：

```csharp
public void EnsureCapacity<T>([NotNull] ref T[]? storage, int size)
```

上述程式碼清楚地表示現有的合約：呼叫端可以傳遞具有值的變數 `null` ，但傳回值保證永遠不會是 null。 `NotNull`屬性最適用于 `ref` 和 `out` 引數 `null` ，可傳遞做為引數，但在方法傳回時，該引數保證不是 null。

您可以使用下列屬性來指定無條件後置條件：

- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute)：不可為 null 的傳回值可能是 null。
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute)：可為 null 的傳回值絕對不會是 null。

## <a name="specify-conditional-post-conditions-notnullwhen-maybenullwhen-and-notnullifnotnull"></a>指定條件式後置條件： `NotNullWhen` 、 `MaybeNullWhen` 和 `NotNullIfNotNull`

您可能很熟悉該 `string` 方法 <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> 。 `true`當引數為 null 或空字串時，這個方法會傳回。 這是一種 null 檢查形式：呼叫端不需要 null-如果方法傳回，則檢查引數 `false` 。 若要讓此方法成為可為 null 的感知，您要將引數設定為可為 null 的參考型別，並新增 `NotNullWhen` 屬性：

```csharp
bool IsNullOrEmpty([NotNullWhen(false)] string? value);
```

這會通知編譯器，傳回值不 `false` 需要是 null 檢查的任何程式碼。 加入屬性會通知編譯器 `IsNullOrEmpty` 執行必要 null 檢查的靜態分析：傳回時 `false` ，輸入引數不是 `null` 。

```csharp
string? userInput = GetUserInput();
if (!string.IsNullOrEmpty(userInput))
{
   int messageLength = userInput.Length; // no null check needed.
}
// null check needed on userInput here.
```

此 <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> 方法會針對 .Net Core 3.0 標注為如上所示。 您的程式碼基底中可能會有類似的方法，可檢查物件的狀態是否有 null 值。 編譯器無法辨識自訂 null 檢查方法，您必須自行新增批註。 當您加入屬性時，編譯器的靜態分析會知道測試的變數是否已核取為 null。

這些屬性的另一個用法是 `Try*` 模式。 `ref`和變數的後置條件 `out` 會透過傳回值進行通訊。 請考慮稍早所示的這個方法：

```csharp
bool TryGetMessage(string key, out string message)
```

上述方法會遵循一般的 .NET 用法：傳回值會指出是否 `message` 已將設定為找到的值，如果找不到任何訊息，則為預設值。 如果方法傳回 `true` ，的值 `message` 不是 null; 否則，方法會將設定 `message` 為 null。

您可以使用屬性來傳達該用法 `NotNullWhen` 。 當您針對可為 null 的參考型別更新簽章時，請建立 `message` `string?` 並新增屬性：

```csharp
bool TryGetMessage(string key, [NotNullWhen(true)] out string? message)
```

在上述範例中，當傳回時，的值 `message` 已知為非 null `TryGetMessage` `true` 。 您應以相同方式在程式碼基底中標注類似的方法：引數可能是 `null` ，而且當方法傳回時，已知為非 null `true` 。

您可能還需要的最後一個屬性。 有時，傳回值的 null 狀態取決於一或多個輸入引數的 null 狀態。 當特定輸入引數不是時，這些方法會傳回非 null 的值 `null` 。 若要正確地批註這些方法，請使用 `NotNullIfNotNull` 屬性。 請考慮下列方法：

```csharp
string GetTopLevelDomainFromFullUrl(string url);
```

如果 `url` 引數不是 null，則輸出不是 `null` 。 啟用可為 null 的參考之後，如果您的 API 永遠不接受 null 輸入，則該簽章會正確運作。 但是，如果輸入可以是 null，則傳回值也可以是 null。 因此，您可以將簽章變更為下列程式碼：

```csharp
string? GetTopLevelDomainFromFullUrl(string? url);
```

這也可以運作，但通常會強制呼叫者執行額外的 `null` 檢查。 合約是 `null` 只有當輸入引數為時，傳回值才會 `url` 是 `null` 。 若要表達該合約，您可以標注此方法，如下列程式碼所示：

```csharp
[return: NotNullIfNotNull("url")]
string? GetTopLevelDomainFromFullUrl(string? url);
```

傳回值和引數都已加上批註， `?` 指出可能是 `null` 。 屬性會進一步說明當引數不是時，傳回值不會是 null `url` `null` 。

您可以使用下列屬性來指定條件式後置條件：

- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute)：當方法傳回指定的值時，不可為 null 的輸入引數可能是 null `bool` 。
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute)：當方法傳回指定的值時，可為 null 的輸入引數不會是 null `bool` 。
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute)：如果指定參數的輸入引數不是 null，則傳回值不是 null。

## <a name="verify-unreachable-code"></a>驗證無法連線的程式碼

某些方法（通常是例外狀況協助程式或其他公用程式方法）一律會擲回例外狀況來結束。 或者，helper 可能會根據布林值引數的值來擲回例外狀況。

在第一種情況下，您可以將 `DoesNotReturn` 屬性加入至方法宣告。 編譯器以三種方式協助您。 首先，如果沒有擲回例外狀況的方法可以結束，則編譯器會發出警告。 其次，編譯器會在呼叫該方法之後，將任何程式碼標示為 *無法*存取，直到遇到適當的 `catch` 子句為止。 第三，無法連線的程式碼將不會影響任何 null 狀態。 請參考下列方法：

```csharp
[DoesNotReturn]
private void FailFast()
{
    throw new InvalidOperationException();
}

public void SetState(object containedField)
{
    if (!isInitialized)
    {
        FailFast();
    }

    // unreachable code:
    _field = containedField;
}
```

在第二個案例中，您會將 `DoesNotReturnIf` 屬性加入至方法的布林值參數。 您可以修改先前的範例，如下所示：

```csharp
private void FailFast([DoesNotReturnIf(false)] bool isValid)
{
    if (!isValid)
    {
        throw new InvalidOperationException();
    }
}

public void SetState(object containedField)
{
    FailFast(isInitialized);

    // unreachable code when "isInitialized" is false:
    _field = containedField;
}
```

## <a name="summary"></a>摘要

[!INCLUDE [C# version alert](../../includes/csharp-version-alert.md)]

加入可為 null 的參考型別會提供初始詞彙，以描述您的 Api 對可能的變數的期望 `null` 。 額外的屬性會提供更豐富的詞彙，以將變數的 null 狀態原因為前置條件與後置條件。 這些屬性更清楚地描述您的期望，並為使用您 Api 的開發人員提供更好的體驗。

當您更新可為 null 內容的程式庫時，請新增這些屬性，以引導您的 Api 使用者使用正確的使用方式。 這些屬性可協助您完整描述輸入引數和傳回值的 null 狀態：

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute)：不可為 null 的輸入引數可能是 null。
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute)：可為 null 的輸入引數永遠不應為 null。
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute)：不可為 null 的傳回值可能是 null。
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute)：可為 null 的傳回值絕對不會是 null。
- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute)：當方法傳回指定的值時，不可為 null 的輸入引數可能是 null `bool` 。
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute)：當方法傳回指定的值時，可為 null 的輸入引數不會是 null `bool` 。
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute)：如果指定參數的輸入引數不是 null，則傳回值不是 null。
- [DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute)：方法永遠不會傳回。 換句話說，它一律會擲回例外狀況。
- [DoesNotReturnIf](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute)：如果相關聯的 `bool` 參數具有指定的值，則不會傳回這個方法。
