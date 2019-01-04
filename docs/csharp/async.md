---
title: 非同步程式設計 - C#
description: 深入了解 .NET Core 提供之 C# 語言層級的非同步程式設計模型。
author: cartermp
ms.date: 06/20/2016
ms.assetid: b878c34c-a78f-419e-a594-a2b44fa521a4
ms.custom: seodec18
ms.openlocfilehash: 231cbbde7c908c3d63d3ff0f59cf3d797e8b9543
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612123"
---
# <a name="asynchronous-programming"></a>非同步程式設計

如果您有任何 I/O 繫結需求 (例如，從網路要求資料，或存取資料庫)，則會想要利用非同步程式設計。  您也可能會有 CPU 繫結程式碼，例如執行耗費資源的計算，這也是不錯的非同步程式碼撰寫案例。

C# 具有語言層級非同步程式設計模型，可輕鬆撰寫非同步程式碼，而不需要竄改回呼或符合支援非同步的程式庫。 它會遵循稱為[工作式非同步模式 (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) 的模式。

## <a name="basic-overview-of-the-asynchronous-model"></a>非同步模型的基本概觀

非同步程式設計的核心是建立非同步作業模型的 `Task` 和 `Task<T>` 物件。  它們是受 `async` 和 `await` 關鍵字所支援。  在大部分情況下，模型都相當簡單︰ 

針對 I/O 繫結程式碼，您可以 `await` 作業，這項作業會在 `async` 方法內傳回 `Task` 或 `Task<T>`。

針對 CPU 繫結程式碼，您可以 `await` 作業，這項作業是使用 `Task.Run` 方法在背景執行緒上啟動。

`await` 關鍵字就是顯現魔力的地方。 它會將控制交給執行 `await` 的方法呼叫端，最後讓 UI 有回應或服務有彈性。

有其他方法可以達成上面所連結 TAP 文章中所述的 `async` 和 `await` 以外的非同步程式碼，但本文件著重在從這點開始的語言層級建構。

### <a name="io-bound-example-downloading-data-from-a-web-service"></a>I/O 繫結範例：從 Web 服務下載資料

您可能需要在按下按鈕時從 Web 服務下載一些資料，但不想要封鎖 UI 執行緒。 只要使用下列項目，即可達成這項作業：

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

就是這麼容易！ 這個程式碼表示目的 (非同步下載一些資料)，而不陷入與工作物件的互動。

### <a name="cpu-bound-example-performing-a-calculation-for-a-game"></a>CPU 繫結範例：執行遊戲的計算

假設您正在撰寫行動遊戲，而按下按鈕可能會損壞畫面上的許多敵人。  執行損壞計算可能十分耗費資源，而且在 UI 執行緒上這麼做會讓遊戲似乎在執行計算時暫停！

處理這種情形的最佳方式是啟動背景執行緒，以使用 `Task.Run` 和 `await` 結果所執行的工作。  這可讓 UI 順暢地完成工作。

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
    // performs its work.  The UI thread is free to perform other work.
    var damageResult = await Task.Run(() => CalculateDamageDone());
    DisplayDamage(damageResult);
};
```

就是這麼容易！  此程式碼完全表示按鈕 click 事件的目的、不需要手動管理背景執行緒，並且以非封鎖方式這麼做。

### <a name="what-happens-under-the-covers"></a>背後作業

有許多與非同步作業有關的移動部分。  如果您想知道 `Task` 和 `Task<T>` 的背後作業，請查看[深入了解非同步](../standard/async-in-depth.md)一文以取得詳細資訊。

在 C# 端，編譯器會將程式碼轉換為狀態電腦，而狀態電腦會追蹤下列這類事項：在達到 `await` 時產生執行，以及在完成背景工作時繼續執行。

甚於理論上的需要，這是 [Promise Model of asynchrony](https://en.wikipedia.org/wiki/Futures_and_promises) (非同步的承諾模型) 的實作。

## <a name="key-pieces-to-understand"></a>要了解的重要部分

*   非同步程式碼可以用於 I/O 繫結和 CPU 繫結程式碼，但每個案例都不同。
*   非同步程式碼會使用 `Task<T>` 和 `Task`，這是用來在背景中完成建立工作模型的建構。
* `async` 關鍵字會將方法轉換為非同步方法，讓您可以在其主體中使用 `await` 關鍵字。
*   套用 `await` 關鍵字時，除非等候的工作完成，否則會暫止呼叫的方法，並將控制權返回其呼叫端。
*   `await` 只能在非同步方法內使用。

## <a name="recognize-cpu-bound-and-io-bound-work"></a>辨識 CPU 繫結和 I/O 繫結工作

本手冊的前兩個範例示範如何使用 `async` 和 `await` 進行 I/O 繫結和 CPU 繫結工作。  這是您識別所需執行的工作是 I/O 繫結還是 CPU 繫結的關鍵，因為它會大幅影響程式碼的效能，而且可能會導致誤用特定建構。

以下是您應該在撰寫任何程式碼之前提問的兩個問題︰

1. 程式碼是否要「等候」什麼項目，例如資料庫中的資料？

    如果您的答案為「是」，則工作是 **I/O 繫結**。

2. 程式碼要執行極耗費資源的計算嗎？

    如果您的答案為「是」，則工作是 **CPU 繫結**。
    
如果您的工作是「I/O 繫結」，請使用「沒有」`Task.Run` 的 `async` 和 `await`。  您「不應該」使用 Task Parallel Library。  [深入了解非同步](../standard/async-in-depth.md)一文中描述這個問題的原因。

如果您的工作是「CPU 繫結」，而且您關心回應性，請使用 `async` 和 `await`，但在「含」`Task.Run` 的其他執行緒上繁衍工作。  如果工作適用於並行和平行處理原則，您應該也考慮使用 [工作平行程式庫](../standard/parallel-programming/task-parallel-library-tpl.md)。

此外，您應該一律測量程式碼的執行。  例如，您可能會發現，在進行多執行緒處理時，與內容切換的負擔相較之下，CPU 繫結工作較不耗費資源。  每個選項都有其取捨，您應該挑選適用於您情況的正確取捨。

## <a name="more-examples"></a>更多範例

下列範例示範可使用 C# 撰寫非同步程式碼的各種方式。  它們會涵蓋數個您可能會遇到的不同案例。

### <a name="extracting-data-from-a-network"></a>從網路擷取資料

此程式碼片段會從首頁 ([www.dotnetfoundation.org](https://www.dotnetfoundation.org)) 下載 HTML，並計算字串 ".NET" 在 HTML 中的出現次數。  它會使用 ASP.NET MVC 來定義執行此工作的 Web 控制器方法，並傳回數字。

> [!NOTE]
> 如果您打算在生產程式碼中執行 HTML 剖析，請不要使用規則運算式。 請改用剖析程式庫。

```csharp
private readonly HttpClient _httpClient = new HttpClient();

[HttpGet]
[Route("DotNetCount")]
public async Task<int> GetDotNetCountAsync()
{
    // Suspends GetDotNetCountAsync() to allow the caller (the web server)
    // to accept another request, rather than blocking on this one.
    var html = await _httpClient.GetStringAsync("https://dotnetfoundation.org");

    return Regex.Matches(html, @"\.NET").Count;
}
```

以下是針對通用 Windows 應用程式撰寫的相同案例，而通用 Windows 應用程式會在按下按鈕時執行相同工作︰

```csharp
private readonly HttpClient _httpClient = new HttpClient();

private async void SeeTheDotNets_Click(object sender, RoutedEventArgs e)
{
    // Capture the task handle here so we can await the background task later.
    var getDotNetFoundationHtmlTask = _httpClient.GetStringAsync("https://www.dotnetfoundation.org");

    // Any other work on the UI thread can be done here, such as enabling a Progress Bar.
    // This is important to do here, before the "await" call, so that the user
    // sees the progress bar before execution of this method is yielded.
    NetworkProgressBar.IsEnabled = true;
    NetworkProgressBar.Visibility = Visibility.Visible;

    // The await operator suspends SeeTheDotNets_Click, returning control to its caller.
    // This is what allows the app to be responsive and not hang on the UI thread.
    var html = await getDotNetFoundationHtmlTask;
    int count = Regex.Matches(html, @"\.NET").Count;

    DotNetCountLabel.Text = $"Number of .NETs on dotnetfoundation.org: {count}";

    NetworkProgressBar.IsEnabled = false;
    NetworkProgressBar.Visibility = Visibility.Collapsed;
}
```

### <a name="waiting-for-multiple-tasks-to-complete"></a>正在等候多個工作完成

您可能會發現必須同時擷取多個資料片段。  `Task` API 包含兩種方法︰`Task.WhenAll` 和 `Task.WhenAny`，可讓您撰寫非同步程式碼，以對多個背景作業執行非封鎖等候。

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

以下是使用 LINQ 利用更簡潔的方式撰寫這個項目的另一種方式：

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
雖然程式碼較少，但是混合使用 LINQ 與非同步程式碼時請小心。  因為 LINQ 使用延後 (延遲) 執行，所以除非使用 `.ToList()` 或 `.ToArray()` 呼叫強制逐一查看產生的序列，否則不會像在 `foreach()` 迴圈中一樣立即進行非同步呼叫。

## <a name="important-info-and-advice"></a>重要資訊和建議

雖然非同步程式設計相當簡單，但是需要牢記一些詳細資料，以避免非預期的行為。

*  `async` **方法需要其主體中有** `await` **關鍵字，或永遠不會產生它們！**

這是需要記住的重要事項。  如果 `await` 未用於 `async` 方法的主體中，C# 編譯器將會產生警告，但程式碼的編譯和執行就像一般方法一樣。  請注意，因為 C# 編譯器針對非同步方法所產生的狀態機器不會完成任何作業，所以這也非常沒有效率。

*   **您應該新增 “Async” 作為所撰寫之每個非同步方法名稱的尾碼。**

這是 .NET 中所使用的慣例，可更容易區分同步與非同步方法。 請注意，不一定會套用程式碼未明確呼叫的特定方法 (例如事件處理常式或 Web 控制器方法)。 因為您的程式碼未明確呼叫這些方法，則明確命名並不重要。

*   `async void` **應該只用於事件處理常式。**

因為事件沒有傳回型別 (因此無法利用 `Task` 和 `Task<T>`)，所以 `async void` 是允許非同步事件處理常式運作的唯一方式。 `async void` 的任何其他使用都未遵循 TAP 模型，而且不容易使用，例如：

  *   `async void` 方法中所擲回的例外狀況無法在該方法外部進行攔截。
  *   `async void` 方法很難進行測試。
  *   如果呼叫端未預期 `async void` 方法非同步執行，則這些方法可能會造成不好的副作用。

*   **在 LINQ 運算式中使用非同步 Lambda 時，請小心處理**

LINQ 中的 Lambda 運算式會使用延後執行，這表示程式碼可以在未預期它執行時結束執行。 如果未正確撰寫，則將封鎖工作導入這個作業很容易會造成死結。 此外，這類非同步程式碼的巢狀結構也更難分析程式碼的執行。 非同步和 LINQ 功能強大，但應該盡可能小心且清楚地一起使用。

*   **以非封鎖方式撰寫等候工作的程式碼**

將封鎖目前執行緒作為等候工作完成的方式可能會造成死結和封鎖的內容執行緒，而且可能需要更為複雜的錯誤處理。 下表提供如何處理以非封鎖方式等候工作的指引︰

| 使用這個項目... | 而不是這個項目... | 執行時機 |
| --- | --- | --- |
| `await` | `Task.Wait` 或 `Task.Result` | 擷取背景工作的結果 |
| `await Task.WhenAny` | `Task.WaitAny` | 等候任何工作完成 |
| `await Task.WhenAll` | `Task.WaitAll` | 等候所有工作完成 |
| `await Task.Delay` | `Thread.Sleep` | 等候一段時間 |

*   **撰寫較不具狀態的程式碼**

請不要取決於全域物件的狀態或特定方法的執行。 相反地，請只取決於方法的傳回值。 為什麼？

  *   程式碼會比較容易理解。
  *   程式碼會比較容易測試。
  *   混合使用非同步與同步程式碼則相當簡單。
  *   一般可以避免追蹤條件。
  *   根據傳回值，讓非同步程式碼的協調更為簡單。
  *   (紅利) 它可實際與相依性插入良好搭配。

建議的目標是在程式碼中達到完全或幾乎完全的 [Referential Transparency](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) (參考透明度)。 這樣做會導致極容易預測、測試和維護的程式碼基底。

## <a name="other-resources"></a>其他資源

* [深入了解非同步](../standard/async-in-depth.md)提供工作運作方式的詳細資訊。
* [使用 async 和 await 進行非同步程式設計 (C#)](./programming-guide/concepts/async/index.md)
* Lucian Wischik 的 [Six Essential Tips for Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) (非同步的六個必要祕訣) 是進行非同步程式設計的不錯資源。