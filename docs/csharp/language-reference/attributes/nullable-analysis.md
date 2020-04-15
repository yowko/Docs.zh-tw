---
title: C# 保留屬性:可無靜態分析
ms.date: 04/14/2020
description: 這些屬性由編譯器解釋,以便為可無和不可取消的引用類型提供更好的靜態分析。
ms.openlocfilehash: 0315d78db7517541efe578d8675c0f2fe45f5aea
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389860"
---
# <a name="reserved-attributes-contribute-to-the-compilers-null-state-static-analysis"></a>保留屬性有助於編譯器的空狀態靜態分析

在可無的上下文中,編譯器執行代碼的靜態分析,以確定所有引用類型變數的 null 狀態:

- *非空*:靜態分析確定變數已分配給非空值。
- *可能為空*:靜態分析無法確定變數已分配非空值。

可以應用許多屬性,這些屬性向編譯器提供有關 API 語義的資訊。 此資訊可幫助編譯器執行靜態分析並確定變數何時不是空。 本文簡要描述了每個屬性以及如何使用它們。 所有示例都假定 C# 8.0 或更新,並且代碼位於可空上下文中。

讓我們從一個熟悉的例子開始。 假設您的函式庫有以下 API 來檢索資源字串:

```csharp
bool TryGetMessage(string key, out string message)
```

前面的範例遵循 .NET`Try*`中熟悉的模式。 此 API 有兩個引用`key`參數:`message`與 參數 。 此 API 有以下與這些參數的不合法的規則:

- 調用方不應作為`null``key`的參數傳遞。
- 調用方可以傳遞其值為`null``message`的變數作為 的 參數。
- 如果`TryGetMessage`方法`true`返回`message`,則 的值不為空。 如果傳回值`false,``message`為 (及其 null 狀態) 的值為 null。

的規則`key`可以通過變數類型表示`key`: 應為不可消除的引用類型。 參數`message`更為複雜。 它允許`null`作為參數,但保證,在成功時,`out`該 參數不為空。 對於這些方案,您需要更豐富的詞彙來描述期望值。

添加了多個屬性以表示有關變數的 null 狀態的其他資訊。 在 C# 8 引入可無引用類型之前編寫的所有代碼都是*無效的。* 這意味著任何引用類型變數可能為空,但不需要 null 檢查。 一旦代碼*是空的,* 這些規則就會改變。 引用類型絕不應為`null`值,並且在取消引用之前必須`null`針對 選中可消除的引用類型。

API 的規則可能更為複雜,正如您在 API 方案中所`TryGetValue`看到的那樣 。 許多 API 對於變數可以或不能`null`是 時,都有更複雜的規則。 在這些情況下,您將使用以下屬性之一來表示這些規則:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): 不可無效的輸入參數可能為空。
- [禁止無效](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute):可空輸入參數絕不應為空。
- [可能 Null](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): 無法取消的傳回值可能為 null。
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): 空返回值永遠不會為空。
- [當](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute)方法返回指定`bool`的 值時,可能 Null 時:非空輸入參數可能為空。
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute):當方法返回指定`bool`的 值時,可 null 的輸入參數不會為空。
- [NotNullIf NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute):如果指定參數的參數不是 null,則返回值不為空。
- [不返回](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute):方法永遠不會返回。 換句話說,它總是引發異常。
- [不返回If](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute):如果關聯`bool`的 參數具有指定的值,則此方法永遠不會返回。

前面的說明是每個屬性執行功能的快速引用。 以下各節更全面地描述行為和含義。

添加這些屬性為編譯器提供有關 API 規則的詳細資訊。 在啟用空的上下文中編譯調用代碼時,編譯器將在調用方違反這些規則時發出警告。 這些屬性無法對實現啟用其他檢查。

## <a name="specify-preconditions-allownull-and-disallownull"></a>指定先決條件:`AllowNull`與`DisallowNull`

請考慮從不返回`null`的讀/寫屬性,因為它具有合理的默認值。 將調用方`null`設置為該預設值時,將傳遞給集訪問器。 例如,考慮在聊天室中要求顯示螢幕名稱的郵件系統。 如果未提供,系統將產生隨機名稱:

```csharp
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName;
```

當您在一個無效的遺忘上下文中編譯前面的代碼時,一切都很好。 啟用空引用類型後,該`ScreenName`屬性將成為不可取消的引用。 這對`get`存取者是正確的:它永遠不會`null`返回 。 調用方不需要檢查 返回的屬性`null`。 但現在將屬性設置為`null`生成警告。 為了繼續支援這種類型的代碼,將<xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType>屬性添加到屬性,如以下代碼所示:

```csharp
[AllowNull]
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName = GenerateRandomScreenName();
```

您可能需要添加一個`using`指令,<xref:System.Diagnostics.CodeAnalysis>以便使用此屬性和本文中討論的其他屬性。 該屬性應用於屬性,而不是`set`訪問器。 屬性`AllowNull`指定*先決條件*,並且僅適用於輸入。 `get`訪問器具有返回值,但沒有輸入參數。 因此,該`AllowNull`屬性僅適用於`set`訪問器。

前面的範例展示在參數上新增`AllowNull`屬性時要尋找的內容:

1. 該變數的一般協定是,它不應該是`null`,因此您需要一個不可取消的引用類型。
1. 輸入變數有一些方案,`null`儘管它們不是最常見的用法。

通常,屬性或`in`或或`out`.`ref`和參數需要此屬性。 當`AllowNull`變數通常是非空的,但您需要作為先決條件允許`null`時,該屬性是最佳選擇。

與使用`DisallowNull`: 的機制相比,使用此屬性指定 null 引用類型的輸入變數`null`不應為 。 請考慮一個屬性`null`,其中是預設值,但用戶端只能將其設置為非 null 值。 請考慮下列程式碼：

```csharp
public string ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string _comment;
```

前面的代碼是表示設計的最佳方式,`ReviewComment`可以`null`是 ,但不能`null`設定為 。 一旦此代碼是空的,您可以使用 更清楚地向呼叫方表達這<xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType>一 概念:

```csharp
[DisallowNull]
public string? ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string? _comment;
```

在空中,`ReviewComment``get`存取器可以傳回`null`預設值 。 編譯器警告必須在訪問之前檢查它。 此外,它警告呼叫方,即使它可能是`null`,呼叫方也不應顯式將其設定為`null`。 該`DisallowNull`屬性還指定*一個先決條件*,它`get`不會影響 訪問器。 當您觀察以下`DisallowNull`特徵時,可以使用該屬性:

1. 變數可能`null`位於核心方案中,通常是在第一次實例化時。
1. 變數不應顯示式設定為`null`。

這些情況在最初*為空遺忘*的代碼中很常見。 可能是對象屬性設置在兩個不同的初始化操作中。 可能某些屬性僅在某些非同步工作完成後進行設置。

`AllowNull`和`DisallowNull`屬性使您能夠指定變數的先決條件可能與這些變數上的空註釋不匹配。 這些提供了有關 API 特徵的更多詳細資訊。 此附加資訊可幫助呼叫方正確使用API。 請記住,您使用以下屬性指定先決條件:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): 不可無效的輸入參數可能為空。
- [禁止無效](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute):可空輸入參數絕不應為空。

## <a name="specify-post-conditions-maybenull-and-notnull"></a>指定後條件:`MaybeNull`與`NotNull`

假設您有一個具有以下簽名的方法:

```csharp
public Customer FindCustomer(string lastName, string firstName)
```

您可能已經編寫了這樣的方法,在未找到要`null`找的名稱時返回。 清楚地`null`指示找不到記錄。 這個選項, 可能會傳回類型從`Customer`變更為`Customer?`。 將返回值聲明為空引用類型明確指定此 API 的意圖。

由於[泛型定義和無效性](../../nullable-attributes.md#generic-definitions-and-nullability)所涵蓋的原因,該技術不適用於泛型方法。 您可能有一個遵循類似模式的泛型方法:

```csharp
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

無法指定傳回值`T?`為 。 當未找到`null`已請求的項時,該方法將返回。 由於無法聲明`T?`傳回類型,`MaybeNull`因此將註釋添加到方法傳回:

```csharp
[return: MaybeNull]
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

前面的代碼通知調用方協定意味著一種不可空的類型,但返回值*實際上可能*為空。  當`MaybeNull`API 應為非空類型(通常是泛型類型參數),但可能存在`null`返回的 實例時,請使用該屬性。

還可以指定返回值或`out`或`ref`或參數 不為空,即使類型為空引用類型。 考慮一種確保數組足夠大以容納多個元素的方法。 如果輸入參數沒有容量,例程將分配一個新陣組並將所有現有元素複製到其中。 如果輸入參數為`null`,例程將分配新的存儲。 如果容量充足,例程將不執行任何操作:

```csharp
public void EnsureCapacity<T>(ref T[] storage, int size)
```

您可以按照以下方式呼叫此例程式:

```csharp
// messages has the default value (null) when EnsureCapacity is called:
EnsureCapacity<string>(ref messages, 10);
// messages is not null.
EnsureCapacity<string>(messages, 50);
```

開啟空引用類型後,您希望確保前面的代碼在無警告的情況下編譯。 當方法返回時,`storage`參數保證不為空。 但是,使用空引用進行調用`EnsureCapacity`是可以接受的。 您可以建立`storage`空白參考類型,並將`NotNull`後條件加入參數的聲明:

```csharp
public void EnsureCapacity<T>([NotNull]ref T[]? storage, int size)
```

前面的代碼清楚地表達了現有協定:調用方可以傳遞具有該值的`null`變數,但返回值保證永遠不會為空。 該`NotNull`屬性`ref`對於`out`和 參數`null`最有用, 其中可以作為參數傳遞,但當方法返回時,該參數保證不為空。

使用以下屬性指定無條件的後情況:

- [可能 Null](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): 無法取消的傳回值可能為 null。
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): 空返回值永遠不會為空。

## <a name="specify-conditional-post-conditions-notnullwhen-maybenullwhen-and-notnullifnotnull"></a>指定條件後條件: `NotNullWhen``MaybeNullWhen`、 與`NotNullIfNotNull`

您可能熟悉這種方法`string`<xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>。 當參數為`true`空字串或空字串時,此方法將返回。 它是一種 null 檢查形式:如果`false`方法返回 ,調用方不需要對參數進行空檢查。 要使此類方法具有 null 感知,您需要將參數設定為可 null 引用類型`NotNullWhen`,並新增屬性 :

```csharp
bool IsNullOrEmpty([NotNullWhen(false)]string? value);
```

這通知編譯器不需要對返回值`false`的任何代碼進行空檢查。 屬性的新增通知編譯器的靜態分析,該`IsNullOrEmpty`分析執行必要的 null 檢查:`false`當它傳回`null`時,輸入參數不是 。

```csharp
string? userInput = GetUserInput();
if (!string.IsNullOrEmpty(userInput))
{
   int messageLength = userInput.Length; // no null check needed.
}
// null check needed on userInput here.
```

該方法<xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>將如上所述.NET Core 3.0的用點子。 代碼庫中可能也有類似的方法,用於檢查物件的狀態為 null 值。 編譯器不會識別自定義 null 檢查方法,您需要自己添加註釋。 添加屬性時,編譯器的靜態分析知道測試變數何時被空檢查。

這些屬性的另一個用途是`Try*`模式。 和`out`變數的`ref`后情況通過返回值進行通信。 請考慮前面顯示的方法:

```csharp
bool TryGetMessage(string key, out string message)
```

前面的方法遵循典型的 .NET 習慣用法:返回`message`值指示 是否設置為找到的值,或者如果沒有找到消息,則指示默認值。 如果方法返回`true`,則`message`的值 不為 null;如果 方法傳回 ,則值為 null。否則,該方法將設置`message`為null。

您可以使用`NotNullWhen`屬性來傳達該習慣用法。 更新可空引言型態的簽名時,`message``string?`請建立並新增屬性:

```csharp
bool TryGetMessage(string key, [NotNullWhen(true)] out string? message)
```

在前面的範例中,`message`當`TryGetMessage``true`傳回時,值已知不為 null。 應在代碼庫中以相同的方式對類似的方法進行編帶:當方法返回`null``true`時,參數可以是 ,並且已知為不為空。

還有一個最終屬性,您可能還需要。 有時,返回值的 null 狀態取決於一個或多個輸入參數的 null 狀態。 當某些輸入參數不是`null`時,這些方法將返回一個非空值。 要正確對這些方法進行給上用,請使用`NotNullIfNotNull`屬性 。 請考慮以下方法:

```csharp
string GetTopLevelDomainFromFullUrl(string url);
```

如果`url`參數不為空,則輸出`null`不是 。 啟用了可無效引用後,該簽名將正常工作,前提是 API 永遠不會接受空輸入。 但是,如果輸入可以為空,則返回值也可以為空。 因此,您可以將簽名更改為以下代碼:

```csharp
string? GetTopLevelDomainFromFullUrl(string? url);
```

這也行得通,但通常會強制調用方實施額外的`null`檢查。 協定是返回值僅在輸入參數`null``url``null`為 時才。 要表示該協定,您需要對此方法進行編號,如以下代碼所示:

```csharp
[return: NotNullIfNotNull("url")]
string? GetTopLevelDomainFromFullUrl(string? url);
```

傳回值和參數都帶`?`有 指示,指示任一`null`可以是 。 該屬性進一步闡明,當參數不是`url``null`時,返回值不會為空。

使用這些屬性指定條件後條件:

- [當](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute)方法返回指定`bool`的 值時,可能 Null 時:非空輸入參數可能為空。
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute):當方法返回指定`bool`的 值時,可 null 的輸入參數不會為空。
- [NotNullIf NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute):如果指定參數的輸入參數不是 null,則返回值不為空。

## <a name="verify-unreachable-code"></a>驗證無法存取的代碼

某些方法(通常是異常説明器或其他實用程式方法)總是通過引發異常退出。 或者,説明程式可能會根據布爾參數的值引發異常。

在第一種情況下,可以將`DoesNotReturn`屬性添加到方法聲明。 編譯器在三個方面為您提供説明。 首先,如果有一個路徑可以退出而不引發異常,編譯器會發出警告。 其次,編譯器在調用該方法后將任何代碼標記為*不可訪問*,直到遇到`catch`適當的 子句。 第三,無法訪問的代碼不會影響任何空狀態。 請參考下列方法：

```csharp
[DoesNotReturn]
private void FailFast()
{
   throw new InvalidOperationException();
}

public void SetState(object containedField)
{
   if (!isInitialized)
      FailFast();

   // unreachable code:
   this.field = containedField;
}
```

在第二種情況下,您將`DoesNotReturnIf`屬性添加到方法的布爾參數。 您可以修改前面的範例,如下所示:

```csharp
private void FailFast([DoesNotReturnIf(false)]bool isValid)
{
   if (!isValid)
       throw new InvalidOperationException();
}

public void SetState(object containedField)
{
   FailFast(isInitialized);

   // unreachable code when "isInitialized" is false:
   this.field = containedField;
}
```

## <a name="summary"></a>摘要

添加可取消的引用類型提供了一個初始詞彙表來描述 API 對`null`可能為的變數的期望。 附加屬性提供了更豐富的詞彙,將變數的 null 狀態描述為先決條件和後條件。 這些屬性更清楚地描述了您的期望,並為使用 API 的開發人員提供更好的體驗。

更新可無效上下文的庫時,請添加這些屬性以引導 API 的使用者使用正確的方法。 這些屬性可説明您完全描述輸入參數和傳回值的 null 狀態:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): 不可無效的輸入參數可能為空。
- [禁止無效](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute):可空輸入參數絕不應為空。
- [可能 Null](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): 無法取消的傳回值可能為 null。
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): 空返回值永遠不會為空。
- [當](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute)方法返回指定`bool`的 值時,可能 Null 時:非空輸入參數可能為空。
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute):當方法返回指定`bool`的 值時,可 null 的輸入參數不會為空。
- [NotNullIf NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute):如果指定參數的輸入參數不是 null,則返回值不為空。
- [不返回](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute):方法永遠不會返回。 換句話說,它總是引發異常。
- [不返回If](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute):如果關聯`bool`的 參數具有指定的值,則此方法永遠不會返回。
