---
title: 使用定義對空值的預期的屬性升級可空引用類型的 API
description: 瞭解如何使用描述性屬性「允許無效」、可能無效、無虛無等來完全描述 API 的空狀態。
ms.technology: csharp-null-safety
ms.date: 07/31/2019
ms.openlocfilehash: 5d7a864ba1b66ad6b4ae7b0391d170a29147c537
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805840"
---
# <a name="update-libraries-to-use-nullable-reference-types-and-communicate-nullable-rules-to-callers"></a>更新函式庫以使用空引言類型,並將無效規則傳達給呼叫者

新增[可取消的引用類型](nullable-references.md)意味著您`null`可以聲明 是否允許或預期每個變數的值。 此外`AllowNull`,還可以應用許多屬性: `DisallowNull` `MaybeNull`、 `NotNull` `NotNullWhen`、 `MaybeNullWhen` `NotNullIfNotNull` 、 、 、 、 、 、 、 、 、 、 、 和, 並完全描述參數和返回值的 null 狀態。 在編寫代碼時,這提供了很好的體驗。 如果非空變數可能設置為`null`,則會收到警告。 如果在取消引用之前未選中空變數,則會收到警告。 更新庫可能需要一些時間,但回報是值得的。 您向編譯器提供的關於*何時*允許`null`或禁止 值的資訊越多,API 使用者得到的更好警告。 讓我們從一個熟悉的例子開始。 假設您的函式庫有以下 API 來檢索資源字串:

```csharp
bool TryGetMessage(string key, out string message)
```

前面的範例遵循 .NET`Try*`中熟悉的模式。 此 API 有兩個引用`key`參數:`message`與 參數 。 此 API 有以下與這些參數的不合法的規則:

- 調用方不應作為`null``key`的參數傳遞。
- 調用方可以傳遞其值為`null``message`的變數作為 的 參數。
- 如果`TryGetMessage`方法`true`返回`message`,則 的值不為空。 如果傳回值`false,``message`為 (及其 null 狀態) 的值為 null。

的規則`key`可以通過變數類型完全表示`key`: 應該是一個不可空的引用類型。 參數`message`更為複雜。 它允許`null`作為參數,但保證,在成功時,`out`該 參數不為空。 對於這些方案,您需要更豐富的詞彙來描述期望值。

更新庫以進行空引用需要的不僅僅是灑`?`灑某些變數和類型名稱。 前面的範例表明,您需要檢查 API 並考慮您對每個輸入參數的期望。 考慮返回值的保證,以及方法返回時`out`的`ref`任何 或參數。 然後,將這些規則傳達給編譯器,當調用方不遵守這些規則時,編譯器將提供警告。

這項工作需要時間。 讓我們從使庫或應用程式具有空感知性的策略開始,同時平衡其他要求和可交付成果。 您將看到如何平衡支援空引用類型的持續開發。 您將瞭解泛型類型定義的挑戰。 您將學習應用屬性來描述單個 API 的預置和後置條件。

## <a name="choose-a-strategy-for-nullable-reference-types"></a>選擇空白的引言型態

第一種選擇是預設是可空引用類型應打開還是關閉。 您有兩種策略:

- 為整個項目啟用空引用類型,並在未準備好的代碼中禁用它。
- 僅為已為空引用類型提供已註明的代碼的可啟用引用類型。

當您為庫更新其他要素以進行空引用類型更新時,第一個策略效果最佳。 所有新開發都是空意識的。 更新現有代碼時,在這些類中啟用空引用類型。

遵循第一個策略,執行以下操作:

1. 通過將元素添加到`<Nullable>enable</Nullable>`*csproj*檔,為整個項目啟用可無效的引用類型。
1. 將`#nullable disable`實用方案添加到專案中的每個源檔。
1. 處理每個檔時,請刪除雜注並解決任何警告。

第一個策略具有更多的前期工作,以將實用處理添加到每個檔。 優點是,添加到專案的每個新代碼檔都將為空。 任何新工作都將是可撤銷的;只能更新現有代碼。

如果庫總體穩定,第二種策略效果更好,開發的重點是採用可無引用類型。 在對 API 進行編號時,打開可取消的引用類型。 完成後,將對整個項目啟用空引用類型。

遵循第二個策略,您可以執行以下操作:

1. 將`#nullable enable`雜注添加到要使空感知的檔中。
1. 解決任何警告。
1. 繼續前兩個步驟,直到使整個庫都為空所知。
1. 通過將元素添加到`<Nullable>enable</Nullable>`*csproj*檔,為整個項目啟用可無效的類型。
1. 刪除`#nullable enable`雜注,因為它們不再需要。

第二種戰略前期工作較少。 權衡是,創建新檔時的第一個任務是添加雜注並使之無效。 如果團隊中的任何開發人員忘記了該新代碼,則新代碼現在處於工作積壓中,以使所有代碼都為空所知。

您選擇哪些策略取決於專案中正在進行多少主動開發。 專案越成熟、越穩定,第二個策略越好。 正在開發的功能越多,第一個策略越好。

## <a name="should-nullable-warnings-introduce-breaking-changes"></a>不合法警告是否應引入重大更改?

開啟可取消參考型態之前,變數被被被被被*被被被被被被被被被被被被被被被被被被被被被被被被被被被被被被* 開啟空引引型態後,所有這些變數都是*非空的*。 如果這些變數未初始化為非空值,編譯器將發出警告。

另一個可能的警告來源是在尚未初始化該值時返回值。

解決編譯器警告的第一步是對參數和返回類型`?`使用註釋來指示參數或返回值何時可能為空。 當引用變數不能為空時,原始聲明是正確的。 執行此操作時,您的目標不僅僅是修復警告。 更重要的目標是使編譯器瞭解您對於潛在空值的意圖。 在檢查警告時,您將得出庫的下一個重大決策。 是否要考慮修改 API 簽名以更清楚地傳達您的設計意圖? 前面檢查`TryGetMessage`的方法更好的 API 簽章可以是:

```csharp
string? TryGetMessage(string key);
```

返回值指示成功或失敗,如果找到該值,則攜帶該值。 在許多情況下,更改 API 簽名可以改進它們傳達空值的方式。

但是,對於公共圖書館或具有大型使用者群的庫,您可能不希望引入任何 API 簽名更改。 對於這些情況和其他常見模式,可以將屬性應用於更明確地定義參數或返回值何時可能是`null`。 無論您是否考慮更改 API 的表面,您都可能會發現,僅類型註釋`null`不足以描述 參數或返回值的值。 在這些情況下,可以將屬性應用於更清晰地描述 API。

## <a name="attributes-extend-type-annotations"></a>屬性延伸型態

添加了多個屬性以表示有關變數的 null 狀態的其他資訊。 在 C# 8 引入可無引用類型之前編寫的所有代碼都是*無效的。* 這意味著任何引用類型變數可能為空,但不需要 null 檢查。 一旦代碼*是空的,* 這些規則就會改變。 引用類型絕不應為`null`值,並且在取消引用之前必須`null`針對 選中可消除的引用類型。

API 的規則可能更為複雜,正如您在 API 方案中所`TryGetValue`看到的那樣 。 許多 API 對於變數可以或不能`null`是 時,都有更複雜的規則。 在這些情況下,您將使用以下屬性之一來表示這些規則:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): 不可無效的輸入參數可能為空。
- [禁止無效](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute):可空輸入參數絕不應為空。
- [可能 Null](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): 無法取消的傳回值可能為 null。
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): 空返回值永遠不會為空。
- [當](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute)方法返回指定`bool`的 值時,可能 Null 時:非空輸入參數可能為空。
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute):當方法返回指定`bool`的 值時,可 null 的輸入參數不會為空。
- [NotNullIf NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute):如果指定參數的參數不是 null,則返回值不為空。

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

在空中,`ReviewComment``get`存取器可以傳回`null`預設值 。 編譯器警告必須在訪問之前檢查它。 此外,它警告呼叫方,即使它可能是`null`,呼叫方也不應顯式將其設定為`null`。 該`DisallowNull`屬性還指定*一個先決條件*,它`get`不會影響 訪問器。 當您觀察以下特徵時,`DisallowNull`應選擇使用該屬性:

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

由於[泛型定義和無效性](#generic-definitions-and-nullability)所涵蓋的原因,該技術不適用於泛型方法。 您可能有一個遵循類似模式的泛型方法:

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

前面的代碼非常清楚地表示現有協定:調用方可以傳遞具有該值的`null`變數,但返回值保證永遠不會為空。 該`NotNull`屬性`ref`對於`out`和 參數`null`最有用, 其中可以作為參數傳遞,但當方法返回時,該參數保證不為空。

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

## <a name="generic-definitions-and-nullability"></a>一般定義與空值

正確傳達泛型類型和泛型方法的 null 狀態需要特別注意。 這是因為可 null 值類型和空引用類型根本不同。 是 的`Nullable<int>`同 義詞`string?`,而與編譯`string`器添加 的屬性`int?`一起。 `T?`結果是,如果不知道是`T``class`. 或 , 編譯器無法`struct`生成正確的代碼。

這並不意味著不能使用空類型(值類型或引用類型)作為閉合泛型的類型參數。 和`List<string?>``List<int?>`都是`List<T>`的有效實例化。

它的意思是,在泛型類或方法聲明中,`T?`沒有約束,不能使用。 例如,<xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType>不會變更為`T?`傳回 。 您可以通過添加`struct``class`或約束來克服此限制。 對於其中任一約束,編譯器知道如何為和`T``T?`生成代碼。

您可能希望將泛型類型參數使用的類型限制為非空類型。 可以通過添加該類型參數的`notnull`約束 來執行此操作。 應用該約束時,類型參數不能為空類型。

## <a name="conclusions"></a>結論

添加可取消的引用類型提供了一個初始詞彙表來描述 API 對`null`可能為的變數的期望。 附加屬性提供了更豐富的詞彙,將變數的 null 狀態描述為先決條件和後條件。 這些屬性更清楚地描述了您的期望,並為使用 API 的開發人員提供更好的體驗。

更新可無效上下文的庫時,請添加這些屬性以引導 API 的使用者使用正確的方法。 這些屬性可説明您完全描述輸入參數和傳回值的 null 狀態:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): 不可無效的輸入參數可能為空。
- [禁止無效](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute):可空輸入參數絕不應為空。
- [可能 Null](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): 無法取消的傳回值可能為 null。
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): 空返回值永遠不會為空。
- [當](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute)方法返回指定`bool`的 值時,可能 Null 時:非空輸入參數可能為空。
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute):當方法返回指定`bool`的 值時,可 null 的輸入參數不會為空。
- [NotNullIf NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute):如果指定參數的輸入參數不是 null,則返回值不為空。
