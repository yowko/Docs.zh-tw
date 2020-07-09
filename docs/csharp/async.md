---
title: 非同步程式設計 - C#
description: 深入了解 .NET Core 提供之 C# 語言層級的非同步程式設計模型。
author: cartermp
ms.date: 05/20/2020
ms.technology: csharp-async
ms.assetid: b878c34c-a78f-419e-a594-a2b44fa521a4
ms.openlocfilehash: b5643dd7eddefebc9cbf922ff5cce75d72dee4dd
ms.sourcegitcommit: 4ad2f8920251f3744240c3b42a443ffbe0a46577
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/08/2020
ms.locfileid: "86100895"
---
# <a name="asynchronous-programming"></a>非同步程式設計

如果您有任何 i/o 系結的需求（例如，從網路要求資料、存取資料庫，或讀取和寫入檔案系統），您會想要利用非同步程式設計。 您也可能會有 CPU 繫結程式碼，例如執行耗費資源的計算，這也是不錯的非同步程式碼撰寫案例。

C # 具有語言層級的非同步程式設計模型，可讓您輕鬆地撰寫非同步程式碼，而不需要操控回呼或符合支援非同步程式庫。 它會遵循稱為[工作式非同步模式 (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) 的模式。

## <a name="overview-of-the-asynchronous-model"></a>非同步模型的總覽

非同步程式設計的核心是建立非同步作業模型的 `Task` 和 `Task<T>` 物件。 它們是受 `async` 和 `await` 關鍵字所支援。 在大部分情況下，模型都相當簡單︰

- 針對 i/o 系結程式碼，您會等候會傳回 `Task` 或 `Task<T>` 在方法內部的作業 `async` 。
- 針對 CPU 系結程式碼，您會使用方法，來等候在背景執行緒上啟動的作業 <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> 。

`await` 關鍵字就是顯現魔力的地方。 它會將控制交給執行 `await` 的方法呼叫端，最後讓 UI 有回應或服務有彈性。 雖然[有方法](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)可以處理和以外的非同步程式碼，但本文 `async` `await` 的重點在於語言層級的結構。

### <a name="io-bound-example-download-data-from-a-web-service"></a>I/o 系結範例：從 web 服務下載資料

當按下按鈕時，您可能需要從 web 服務下載一些資料，但不想要封鎖 UI 執行緒。 它可以如下完成：

```csharp
private readonly HttpClient _httpClient = new HttpClient();

downloadButton.Clicked += async (o, e) =>
{
    // This line will yield control to the UI as the request
    // from the web service is happening.
    //
    // The UI thread is now free to perform other work.
    var stringData = await _httpClient.GetStringAsync(URL);
    DoSomethingWithData(stringData);
};
```

此程式碼會表示意圖（以非同步方式下載資料），而不會向下很快與 `Task` 物件互動。

### <a name="cpu-bound-example-perform-a-calculation-for-a-game"></a>CPU 系結範例：執行遊戲的計算

假設您正在撰寫行動遊戲，而按下按鈕可能會損壞畫面上的許多敵人。 執行損壞計算可能十分耗費資源，而且在 UI 執行緒上這麼做會讓遊戲似乎在執行計算時暫停！

處理這種情況的最佳方式是啟動背景執行緒，它會使用來執行工作 `Task.Run` ，並使用來等待其結果 `await` 。 這可讓 UI 在工作完成時感覺順暢。

```csharp
private DamageResult CalculateDamageDone()
{
    // Code omitted:
    //
    // Does an expensive calculation and returns
    // the result of that calculation.
}

calculateButton.Clicked += async (o, e) =>
{
    // This line will yield control to the UI while CalculateDamageDone()
    // performs its work. The UI thread is free to perform other work.
    var damageResult = await Task.Run(() => CalculateDamageDone());
    DisplayDamage(damageResult);
};
```

此程式碼完全表示按鈕 click 事件的目的、不需要手動管理背景執行緒，並且以非封鎖方式這麼做。

### <a name="what-happens-under-the-covers"></a>背後作業

其中有許多非同步作業的相關移動部分。 如果您想知道和背後的情況 `Task` `Task<T>` ，請參閱[非同步](../standard/async-in-depth.md)深入文章以取得詳細資訊。

在 c # 方面，編譯器會將您的程式碼轉換成狀態機器，以追蹤在達到時執行的動作 `await` ，並在背景作業完成時繼續執行。

甚於理論上的需要，這是 [Promise Model of asynchrony](https://en.wikipedia.org/wiki/Futures_and_promises) (非同步的承諾模型) 的實作。

## <a name="key-pieces-to-understand"></a>要瞭解的重要部分

* 非同步程式碼可以用於 I/O 繫結和 CPU 繫結程式碼，但每個案例都不同。
* 非同步程式碼會使用 `Task<T>` 和 `Task`，這是用來在背景中完成建立工作模型的建構。
* `async` 關鍵字會將方法轉換為非同步方法，讓您可以在其主體中使用 `await` 關鍵字。
* 套用 `await` 關鍵字時，除非等候的工作完成，否則會暫止呼叫的方法，並將控制權返回其呼叫端。
* `await` 只能在非同步方法內使用。

## <a name="recognize-cpu-bound-and-io-bound-work"></a>辨識 CPU 系結和 i/o 系結工作

本手冊的前兩個範例示範如何使用 `async` 和 `await` 進行 I/O 繫結和 CPU 繫結工作。 這是您識別所需執行的工作是 I/O 繫結還是 CPU 繫結的關鍵，因為它會大幅影響程式碼的效能，而且可能會導致誤用特定建構。

以下是您應該在撰寫任何程式碼之前提問的兩個問題︰

1. 程式碼是否要「等候」什麼項目，例如資料庫中的資料？

   如果您的答案為「是」，則工作是 **I/O 繫結**。

1. 您的程式碼會執行昂貴的計算嗎？

   如果您的答案為「是」，則工作是 **CPU 繫結**。

如果您的工作是「I/O 繫結」****，請使用「沒有」`await` ** `Task.Run` 的 `async` 和 。 您「不應該」** 使用 Task Parallel Library。 這項功能的原因會以[非同步方式](../standard/async-in-depth.md)概述。

如果您擁有的工作是**CPU**系結，而且您在意回應能力，請使用 `async` 和 `await` ，但使用在另一個執行緒*with*上衍生工作 `Task.Run` 。 如果工作適用于並行和平行處理原則，也請考慮使用[Task Parallel Library](../standard/parallel-programming/task-parallel-library-tpl.md)。

此外，您應該一律測量程式碼的執行。 例如，您可能會發現，在進行多執行緒處理時，與內容切換的負擔相較之下，CPU 繫結工作較不耗費資源。 每個選項都有其取捨，您應該挑選適用於您情況的正確取捨。

## <a name="more-examples"></a>更多範例

下列範例示範可使用 C# 撰寫非同步程式碼的各種方式。 它們會涵蓋數個您可能會遇到的不同案例。

### <a name="extract-data-from-a-network"></a>從網路解壓縮資料

此程式碼片段會從首頁下載 HTML <https://dotnetfoundation.org> ，並計算字串 ".net" 在 html 中出現的次數。 它會使用 ASP.NET 來定義 Web API 控制器方法，這會執行這項工作並傳回數位。

> [!NOTE]
> 如果您打算在生產程式碼中執行 HTML 剖析，請不要使用規則運算式。 請改用剖析程式庫。

```csharp
private readonly HttpClient _httpClient = new HttpClient();

[HttpGet, Route("DotNetCount")]
public async Task<int> GetDotNetCount()
{
    // Suspends GetDotNetCount() to allow the caller (the web server)
    // to accept another request, rather than blocking on this one.
    var html = await _httpClient.GetStringAsync("https://dotnetfoundation.org");

    return Regex.Matches(html, @"\.NET").Count;
}
```

以下是針對通用 Windows 應用程式撰寫的相同案例，而通用 Windows 應用程式會在按下按鈕時執行相同工作︰

```csharp
private readonly HttpClient _httpClient = new HttpClient();

private async void OnSeeTheDotNetsButtonClick(object sender, RoutedEventArgs e)
{
    // Capture the task handle here so we can await the background task later.
    var getDotNetFoundationHtmlTask = _httpClient.GetStringAsync("https://dotnetfoundation.org");

    // Any other work on the UI thread can be done here, such as enabling a Progress Bar.
    // This is important to do here, before the "await" call, so that the user
    // sees the progress bar before execution of this method is yielded.
    NetworkProgressBar.IsEnabled = true;
    NetworkProgressBar.Visibility = Visibility.Visible;

    // The await operator suspends OnSeeTheDotNetsButtonClick(), returning control to its caller.
    // This is what allows the app to be responsive and not block the UI thread.
    var html = await getDotNetFoundationHtmlTask;
    int count = Regex.Matches(html, @"\.NET").Count;

    DotNetCountLabel.Text = $"Number of .NETs on dotnetfoundation.org: {count}";

    NetworkProgressBar.IsEnabled = false;
    NetworkProgressBar.Visibility = Visibility.Collapsed;
}
```

### <a name="wait-for-multiple-tasks-to-complete"></a>等待多個工作完成

您可能會發現必須同時擷取多個資料片段。 此 `Task` API 包含兩種方法： <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> ，可讓您撰寫非同步程式碼，在多個背景工作上執行非封鎖等候。

這個範例示範如何捕捉一組 `userId` 的 `User` 資料。

```csharp
public async Task<User> GetUserAsync(int userId)
{
    // Code omitted:
    //
    // Given a user Id {userId}, retrieves a User object corresponding
    // to the entry in the database with {userId} as its Id.
}

public static async Task<IEnumerable<User>> GetUsersAsync(IEnumerable<int> userIds)
{
    var getUserTasks = new List<Task<User>>();
    foreach (int userId in userIds)
    {
        getUserTasks.Add(GetUserAsync(userId));
    }

    return await Task.WhenAll(getUserTasks);
}
```

以下是使用 LINQ 撰寫更簡潔的另一種方式：

```csharp
public async Task<User> GetUserAsync(int userId)
{
    // Code omitted:
    //
    // Given a user Id {userId}, retrieves a User object corresponding
    // to the entry in the database with {userId} as its Id.
}

public static async Task<User[]> GetUsersAsync(IEnumerable<int> userIds)
{
    var getUserTasks = userIds.Select(id => GetUserAsync(id));
    return await Task.WhenAll(getUserTasks);
}
```

雖然程式碼較少，但是混合使用 LINQ 與非同步程式碼時請小心。 因為 LINQ 使用延後 (延遲) 執行，所以除非使用 `.ToList()` 或 `.ToArray()` 呼叫強制逐一查看產生的序列，否則不會像在 `foreach` 迴圈中一樣立即進行非同步呼叫。

## <a name="important-info-and-advice"></a>重要資訊與建議

在非同步程式設計中，有一些要牢記在心的詳細資料，這可能會導致非預期的行為。

* `async` **方法需要其主體中有** `await` **關鍵字，否則它們將永遠不會產生！**

  這是需要記住的重要事項。 如果 `await` 不是在方法的主體中使用 `async` ，則 c # 編譯器會產生警告，但程式碼會編譯並執行，就像是一般方法一樣。 這項作業非常沒有效率，因為非同步方法的 c # 編譯器所產生的狀態機器不會完成任何作業。

* **您應該新增 "Async" 作為您所撰寫之每個非同步方法名稱的尾碼。**

這是 .NET 中用來更輕鬆區分同步和非同步方法的慣例。 不一定會套用您的程式碼未明確呼叫的某些方法（例如事件處理常式或 web 控制器方法）。 因為您的程式碼並未明確呼叫它們，所以明確指出其命名並不重要。

* `async void`**應該只用于事件處理常式。**

因為事件沒有傳回型別 (因此無法利用 `Task` 和 `Task<T>`)，所以 `async void` 是允許非同步事件處理常式運作的唯一方式。 `async void` 的任何其他使用都未遵循 TAP 模型，而且不容易使用，例如：

* 在方法中擲回的例外狀況 `async void` 無法在該方法之外捕捉。
* `async void`方法很容易測試。
* `async void`如果呼叫端不希望它們是非同步，方法可能會造成不良的副作用。

* **在 LINQ 運算式中使用非同步 Lambda 時，請小心處理**

LINQ 中的 Lambda 運算式會使用延後執行，這表示程式碼可能會在您不想要的時候結束執行。 如果未正確撰寫，則將封鎖工作導入這個作業很容易會造成死結。 此外，這類非同步程式碼的巢狀結構也更難分析程式碼的執行。 非同步和 LINQ 功能強大，但應該盡可能小心且清楚地一起使用。

* **以非封鎖方式撰寫等候工作的程式碼**

封鎖目前的執行緒做為等候完成的方法 `Task` ，可能會導致鎖死和已封鎖的內容執行緒，而且可能需要更複雜的錯誤處理。 下表提供如何處理以非封鎖方式等候工作的指引：

| 目的...          | 而不是這個項目...           | 當您想要這麼做時 .。。                 |
|----------------------|------------------------------|--------------------------------------------|
| `await`              | `Task.Wait` 或 `Task.Result` | 擷取背景工作的結果 |
| `await Task.WhenAny` | `Task.WaitAny`               | 等候任何工作完成           |
| `await Task.WhenAll` | `Task.WaitAll`               | 等候所有工作完成          |
| `await Task.Delay`   | `Thread.Sleep`               | 等候一段時間               |

* **請考慮使用** `ValueTask`**可能的話**

從非同步方法傳回 `Task` 物件可能會造成在特定路徑的效能瓶頸。 `Task` 是參考型別，因此使用它表示要配置物件。 如果使用修飾詞宣告的方法傳回快取 `async` 的結果，或同步完成，則額外的配置可能會在程式碼的效能關鍵區段中變成相當長的時間成本。 如果這些配置發生在緊密迴圈中，它可能會變得成本很高。 如需詳細資訊，請參閱[一般化非同步](whats-new/csharp-7.md#generalized-async-return-types)傳回型別。

* **請考慮使用** `ConfigureAwait(false)`

常見的問題是：「我應該使用 <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> 方法嗎？」。 方法可讓 `Task` 實例設定其 awaiter。 這是很重要的考慮，並不正確地設定它可能會影響效能，甚至會造成鎖死。 如需的詳細資訊 `ConfigureAwait` ，請參閱[ConfigureAwait 常見問題](https://devblogs.microsoft.com/dotnet/configureawait-faq)。

* **撰寫較不具狀態的程式碼**

請不要依賴全域物件的狀態或特定方法的執行。 相反地，請只取決於方法的傳回值。 為什麼？

* 程式碼會比較容易理解。
* 程式碼會比較容易測試。
* 混合使用非同步與同步程式碼則相當簡單。
* 一般可以避免追蹤條件。
* 根據傳回值，讓非同步程式碼的協調更為簡單。
* (紅利) 它可實際與相依性插入良好搭配。

建議的目標是在程式碼中達到完全或幾乎完全的 [Referential Transparency](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) (參考透明度)。 這樣做會導致極容易預測、測試和維護的程式碼基底。

## <a name="other-resources"></a>其他資源

* [深入了解非同步](../standard/async-in-depth.md)提供工作運作方式的詳細資訊。
* [使用 async 和 await 進行非同步程式設計（c #）](./programming-guide/concepts/async/index.md)
* Lucian Wischik 的 [Six Essential Tips for Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) (非同步的六個必要祕訣) 是進行非同步程式設計的不錯資源。
