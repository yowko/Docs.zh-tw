---
title: '工作非同步程式設計 (利用 async 和 await (c # ) 」來利用) 模型」'
description: '瞭解何時及如何使用以工作為基礎的非同步程式設計，這是以 c # 進行非同步程式設計的簡化方法。'
ms.date: 08/19/2020
ms.assetid: 9bcf896a-5826-4189-8c1a-3e35fa08243a
ms.openlocfilehash: 5e85b99025b31e205c66468d4bd886701cbaea17
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812080"
---
# <a name="task-asynchronous-programming-model"></a>非同步工作程式設計模型

您可以使用非同步程式設計，避免發生效能瓶頸並增強應用程式的整體回應性。 不過，撰寫非同步應用程式的傳統技術可能很複雜，因而難以撰寫、偵錯和維護。

[C# 5](../../../whats-new/csharp-version-history.md#c-version-50) 引進了一種簡化的方法 (非同步程式設計)，來運用 .NET Framework 4.5 和更新版本、.NET Core 以及 Windows 執行階段中的非同步支援。 編譯器會代替開發人員處理過去經常要處理的困難工作，而您的應用程式仍保有類似同步程式碼的邏輯結構。 因此，您可以輕鬆擁有非同步程式設計的所有優點。

本主題提供使用非同步程式設計的時機和使用方式的概觀，並加入包含詳細資料及範例的支援主題連結。

## <a name="async-improves-responsiveness"></a><a name="BKMK_WhentoUseAsynchrony"></a> 非同步可改善回應性

非同步對於可能在像是 Web 存取時會進行封鎖的活動而言相當重要。 存取 Web 資源的速度有時會變慢或延遲。 如果這類活動在同步處理序中遭到封鎖，整個應用程式就必須等候。 在非同步處理序中，應用程式可以繼續處理其他與 Web 資源不相關的工作，直到可能的封鎖工作完成。

下表顯示非同步程式設計一般會改善回應速度的部分。 從 .NET 和 Windows 執行階段列出的 API 包含支援非同步程式設計的方法。

| 應用程式區域 | 使用非同步方法的 .NET 類型 | 使用非同步方法的 Windows 執行階段類型 |
|--|--|--|
| Web 存取 | <xref:System.Net.Http.HttpClient> | <xref:Windows.Web.Http.HttpClient?displayProperty=nameWithType> <br> <xref:Windows.Web.Syndication.SyndicationClient> |
| 處理檔案 | <xref:System.Text.Json.JsonSerializer> <br> <xref:System.IO.StreamReader> <br> <xref:System.IO.StreamWriter> <br> <xref:System.Xml.XmlReader> <br> <xref:System.Xml.XmlWriter> | <xref:Windows.Storage.StorageFile> |
| 使用映像 |  | <xref:Windows.Media.Capture.MediaCapture> <br> <xref:Windows.Graphics.Imaging.BitmapEncoder> <br> <xref:Windows.Graphics.Imaging.BitmapDecoder> |
| WCF 程式設計 | [同步和非同步作業](../../../../framework/wcf/synchronous-and-asynchronous-operations.md) |  |

非同步對於存取 UI 執行緒的應用程式而言確實特別有用，因為所有 UI 相關活動通常都會共用一個執行緒。 如果同步應用程式中有任何處理序遭到封鎖，所有處理序都會遭到封鎖。 您的應用程式會停止回應，而且您可能會認為應用程式失敗，但實際上只是在等候。

當您使用非同步方法時，應用程式會繼續回應 UI。 例如，您可以調整視窗大小或將視窗縮到最小，如果不想要等待應用程式完成，也可以將它關閉。

非同步方法會在設計非同步作業時，於選項清單中加入自動傳輸的對等項目讓您選擇。 也就是說，除了擁有傳統非同步程式設計的所有優點之外，開發人員所需投入的時間也大為減少。

## <a name="async-methods-are-easy-to-write"></a><a name="BKMK_HowtoWriteanAsyncMethod"></a> 非同步方法很容易撰寫

C# 中的 [async](../../../language-reference/keywords/async.md) 和 [await](../../../language-reference/operators/await.md) 關鍵字都是非同步程式設計的核心。 藉由使用這兩個關鍵字，您可以使用 .NET Framework、.NET Core 或 Windows 執行階段中的資源來建立異步方法，幾乎就像建立同步方法一樣容易。 使用 `async` 關鍵字的非同步方法就稱為*非同步方法*。

下列範例將示範非同步方法。 程式碼中幾乎所有的東西都應該看起來很熟悉。

您可以 [使用 c # 中的 async 和 await](https://docs.microsoft.com/samples/dotnet/samples/async-and-await-cs)，找到可從非同步程式設計下載的完整 WINDOWS PRESENTATION FOUNDATION (WPF) 範例。

:::code language="csharp" source="snippets/access-web/Program.cs" id="ControlFlow":::

您可以從上述範例中了解數個做法。 從方法簽章開始。 它包括 `async` 修飾詞。 傳回型別是 `Task<int>` (請參閱＜傳回型別＞一節以取得更多選項)。 方法名稱結尾為 `Async`。 在方法的主體中，`GetStringAsync` 會傳回 `Task<string>`。 也就是說，當您 `await` 工作時，您會收到 `string` (`contents`)。 等候工作之前，您可以從 `GetStringAsync` 執行不依賴 `string` 的工作。

密切注意 `await` 運算子。 它會暫停 `GetUrlContentLengthAsync` ：

- `GetUrlContentLengthAsync` 無法繼續，直到 `getStringTask` 完成為止。
- 同時，控制項會傳回 `GetUrlContentLengthAsync` 的呼叫端。
- 當 `getStringTask` 完成時，控制項會繼續這裡執行。
- 接著，`await` 運算子會從 `getStringTask` 擷取 `string` 結果。

return 陳述式會指定整數結果。 正在等待 `GetUrlContentLengthAsync` 的任何方法都會擷取長度值。

如果 `GetUrlContentLengthAsync` 在呼叫 `GetStringAsync` 與等候其完成之間沒有任何可以執行的工作，您可以在下列單一陳述式中呼叫和等候，以簡化程式碼。

```csharp
string contents = await client.GetStringAsync("https://docs.microsoft.com/dotnet");
```

下列特性會摘要說明上述範例的非同步方法：

- 方法簽章包含 `async` 修飾詞。
- 按照慣例，非同步方法的名稱是以 "Async" 後置字元為結尾。
- 傳回型別是下列其中一種類型：

  - 如果方法的 return 陳述式中運算元的類型為 `TResult`，則為 <xref:System.Threading.Tasks.Task%601>。
  - 如果方法沒有 return 陳述式或是 return 陳述式沒有運算元，則為 <xref:System.Threading.Tasks.Task>。
  - 如果您撰寫的是非同步事件處理常式，則為 `void`。
  - 任何具有 `GetAwaiter` 方法的其他類型 (從 C# 7.0 開始)。

  如需詳細資訊，請參閱傳回 [類型和參數](#BKMK_ReturnTypesandParameters) 一節。

- 方法通常至少包含一個 `await` 運算式，表示方法在等候的非同步作業完成後才能繼續的點。 此時，方法已暫停，而且控制權返回到方法的呼叫端。 本主題的下一節將說明暫停點會發生什麼情況。

在非同步方法中，您會使用提供的關鍵字和類型表示您想要執行的工作，而編譯器會完成其餘的部分，包括追蹤控制權返回已暫停方法中的等候點時必須進行的作業。 某些常式處理序像是迴圈和例外狀況處理，在傳統非同步程式碼中可能不容易處理。 在非同步方法中，您可以像在同步方案中一樣撰寫這些項目，如此就可以解決這個問題了。

如需舊版 .NET Framework 非同步詳細資訊，請參閱 [TPL 和傳統 .NET Framework 非同步程式設計](../../../../standard/parallel-programming/tpl-and-traditional-async-programming.md)。

## <a name="what-happens-in-an-async-method"></a><a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a> 非同步方法中執行了哪些工作

在非同步程式設計中要了解的最重要事情，就是控制流程如何在方法之間移動。 下圖將引導您了解整個程序：

:::image type="content" source="media/task-asynchronous-programming-model/navigation-trace-async-program.png" alt-text="非同步控制流程的追蹤導覽" lightbox="media/task-asynchronous-programming-model/navigation-trace-async-program.png":::

圖表中的數位會對應至下列步驟，這些步驟會在呼叫方法呼叫 async 方法時起始。

1. 呼叫方法會呼叫並等候 `GetUrlContentLengthAsync` async 方法。

1. `GetUrlContentLengthAsync` 會建立 <xref:System.Net.Http.HttpClient> 執行個體並呼叫 <xref:System.Net.Http.HttpClient.GetStringAsync%2A> 非同步方法，將網站的內容當做字串下載。

1. `GetStringAsync` 中發生了導致進度暫停的一些狀況。 可能必須等待網站下載或其他封鎖活動。 為了避免封鎖資源，`GetStringAsync` 會將控制權遞交 (Yield) 給它的呼叫端 `GetUrlContentLengthAsync`。

     `GetStringAsync` 會傳回 <xref:System.Threading.Tasks.Task%601> (其中 `TResult` 是字串)，而 `GetUrlContentLengthAsync` 則會將工作指派給 `getStringTask` 變數。 工作代表對 `GetStringAsync` 之呼叫的進行中程序，並承諾會在工作完成時產生實際字串值。

1. 因為尚未等候 `getStringTask`，所以 `GetUrlContentLengthAsync` 可以繼續進行其他不相依於 `GetStringAsync` 之最終結果的其他工作。 這項工作是由對同步方法 `DoIndependentWork` 的呼叫來表示。

1. `DoIndependentWork` 是完成其工作並傳回其呼叫端的同步方法。

1. `GetUrlContentLengthAsync` 已完成所有可處理的工作，但未取得來自 `getStringTask` 的結果。 `GetUrlContentLengthAsync` 接著要計算和傳回下載字串的長度，但是方法必須等到有字串時才能計算該值。

    因此，`GetUrlContentLengthAsync` 會使用 await 運算子暫停其進度，並將控制權遞交 (Yield) 給呼叫 `GetUrlContentLengthAsync` 的方法。 `GetUrlContentLengthAsync` 會將 `Task<int>` 傳回呼叫端。 這項工作代表承諾會產生相當於下載字串長度的整數結果。

    > [!NOTE]
    > 如果 `GetStringAsync` (和 `getStringTask`) 在 `GetUrlContentLengthAsync` 等候它之前先完成，控制權仍會留在 `GetUrlContentLengthAsync`。 `GetUrlContentLengthAsync`如果被呼叫的非同步處理已 `getStringTask` 完成，而 `GetUrlContentLengthAsync` 不需要等候最後的結果，則暫停和返回的費用將會浪費。

    在呼叫方法內，處理模式會繼續。 呼叫端可能會在等候結果之前執行其他不取決於 `GetUrlContentLengthAsync` 之結果的工作，或者呼叫端可能立即等候。 呼叫方法正在等候，正在 `GetUrlContentLengthAsync` `GetUrlContentLengthAsync` 等候 `GetStringAsync` 。

1. `GetStringAsync` 完成並產生字串結果。 字串結果不會依照您預期的方式透過呼叫 `GetStringAsync` 來傳回  (請記住，方法已在步驟 3 傳回工作)。字串結果會改為儲存在表示方法 `getStringTask` 完成的工作中。 await 運算子會從 `getStringTask` 擷取結果。 指派陳述式會將擷取的結果指派給 `contents`。

1. 當 `GetUrlContentLengthAsync` 擁有字串結果時，方法就可以計算字串的長度。 然後 `GetUrlContentLengthAsync` 的工作也已完成，而且等候事件處理常式可以繼續執行。 在本主題最後的完整範例中，您可以確認事件處理常式會擷取並列印長度結果的值。
如果您不熟悉非同步程式設計，請花一分鐘思考同步和非同步行為之間的差異。 同步方法會在其工作完成時傳回 (步驟 5)，而非同步方法則會在其工作暫停時傳回工作值 (步驟 3 和步驟 6)。 當非同步方法最後完成其工作時，工作會標示為已完成，而結果 (如果有的話) 會儲存在工作中。

## <a name="api-async-methods"></a><a name="BKMK_APIAsyncMethods"></a> API 非同步方法

您可能會想知道哪裡可以找到支援非同步程式設計的方法，例如 `GetStringAsync`。 .NET Framework 4.5 或更高版本，且 .NET Core 包含許多可搭配和使用的成員 `async` `await` 。 您可以透過附加至成員名稱的 "Async" 尾碼，以及其對或的傳回型別來辨識它們 <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> 。 例如，相對於同步方法 <xref:System.IO.Stream.CopyTo%2A>、<xref:System.IO.Stream.Read%2A> 和 <xref:System.IO.Stream.Write%2A>，`System.IO.Stream` 類別也包含一些方法，例如 <xref:System.IO.Stream.CopyToAsync%2A>、<xref:System.IO.Stream.ReadAsync%2A> 和 <xref:System.IO.Stream.WriteAsync%2A>。

Windows 執行階段也包含許多您可以在 Windows 應用程式中與 `async` 和 `await` 搭配使用的方法。 如需詳細資訊，請參閱適用於 UWP 開發的[執行緒和非同步程式設計](/windows/uwp/threading-async/)，如果您使用舊版的 Windows 執行階段，則請參閱[非同步程式設計 (Microsoft Store 應用程式)](https://docs.microsoft.com/previous-versions/windows/apps/hh464924(v=win.10)) 和[快速入門：在 C# 或 Visual Basic 中呼叫非同步 API](https://docs.microsoft.com/previous-versions/windows/apps/hh452713(v=win.10))。

## <a name="threads"></a><a name="BKMK_Threads"></a> 執行緒

非同步方法主要做為非封鎖作業使用。 `await`當等候的工作正在執行時，非同步方法中的運算式不會封鎖目前的執行緒。 運算式會改為註冊方法的其餘部分做為接續，並將控制權交還給非同步方法的呼叫端。

`async` 和 `await` 關鍵字不會導致建立其他執行緒。 由於非同步方法不會在本身的執行緒上執行，因此非同步方法不需要多執行緒。 方法會在目前的同步處理內容執行，而且只有在方法為作用中時才會在執行緒上花費時間。 您可以使用 <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> 將受限於 CPU 的工作移到背景執行緒，但是背景執行緒無法協助處理正在等待結果產生的處理序。

非同步程式設計的非同步方法幾乎是所有案例的現有方法當中較好的方法。 特別是，這個方法比受限於 I/O 作業的 <xref:System.ComponentModel.BackgroundWorker> 類別還要好，因為程式碼較簡單，而且不需要防範競爭條件。 相較于 <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> 方法，非同步程式設計比針對 CPU 系結作業更好， <xref:System.ComponentModel.BackgroundWorker> 因為非同步程式設計會將執行程式碼的協調細節，從 `Task.Run` 傳輸到執行緒集區的工作分離出來。

## <a name="async-and-await"></a><a name="BKMK_AsyncandAwait"></a> async 和 await

如果您使用 [async](../../../language-reference/keywords/async.md) 修飾詞來將方法指定為非同步方法，就會啟用下列兩項功能。

- 標記的非同步方法可以使用 [await](../../../language-reference/operators/await.md) 來指定暫停點。 `await` 運算子會告知編譯器，非同步方法只有在等候的非同步處理序完成後，才能繼續通過該點。 同時，控制權會返回非同步方法的呼叫端。

     非同步方法在運算式中的暫止 `await` 不會構成方法的結束，而且區塊也 `finally` 不會執行。

- 標記的非同步方法本身可以做為其呼叫方法的等候目標。

非同步方法通常會包含一或多個出現的 `await` 運算子，但不存在的 `await` 運算式不會造成編譯器錯誤。 如果非同步方法未使用 `await` 運算子來標記暫停點，則不論修飾詞為何，方法都會以同步方法執行 `async` 。 編譯器將對這類方法發出警告。

`async` 和 `await` 都是內容關鍵字。 如需詳細資訊和範例，請參閱下列主題：

- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)

## <a name="return-types-and-parameters"></a><a name="BKMK_ReturnTypesandParameters"></a> 傳回類型和參數

async 方法通常會傳回 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601>。 在非同步方法內，會將 `await` 運算子套用到呼叫另一個非同步方法所傳回的工作。

<xref:System.Threading.Tasks.Task%601>如果方法包含 [`return`](../../../language-reference/keywords/return.md) 指定類型運算元的語句，您可以指定做為傳回型別 `TResult` 。

如果方法沒有 return 陳述式，或者方法的 return 陳述式不會傳回運算元，請使用 <xref:System.Threading.Tasks.Task> 作為傳回型別。

從 C# 7.0 開始，您也可以指定任何其他傳回型別，前提是該類型包括 `GetAwaiter` 方法。 這類類型的範例是 <xref:System.Threading.Tasks.ValueTask%601>。 它提供於 [System.Threading.Tasks.Extension](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) NuGet 套件中。

下列範例顯示如何宣告和呼叫傳回 <xref:System.Threading.Tasks.Task%601> 或的方法 <xref:System.Threading.Tasks.Task> ：

```csharp
async Task<int> GetTaskOfTResultAsync()
{
    int hours = 0;
    await Task.Delay(0);

    return hours;
}


Task<int> returnedTaskTResult = GetTaskOfTResultAsync();
int intResult = await returnedTaskTResult;
// Single line
// int intResult = await GetTaskOfTResultAsync();

async Task GetTaskAsync()
{
    await Task.Delay(0);
    // No return statement needed
}

Task returnedTask = GetTaskAsync();
await returnedTask;
// Single line
await GetTaskAsync();
```

每項傳回的工作都代表進行中的工作。 工作會封裝這個非同步處理序狀態的相關資訊，以及處理序的最終結果，或是處理序不成功時，則會封裝處理序引發的例外狀況。

非同步方法的傳回型別也可以是 `void`。 這個傳回類型主要用於定義需要 `void` 傳回類型的事件處理常式。 非同步事件處理常式通常做為非同步程式的起點。

具有傳回類型的非同步方法 `void` 無法等候，而且 void 傳回方法的呼叫端無法攔截方法擲回的任何例外狀況。

非同步方法無法宣告 [in](../../../language-reference/keywords/in-parameter-modifier.md)、[ref](../../../language-reference/keywords/ref.md) 或 [out](../../../language-reference/keywords/out-parameter-modifier.md) 參數，但是此方法可以呼叫具有這類參數的方法。 同樣地，async 方法無法以傳址方式傳回值，但可以使用 ref 傳回值呼叫方法。

如需詳細資訊和範例，請參閱 [非同步傳回類型 (c # ) ](async-return-types.md)。 如需如何在非同步方法中攔截例外狀況的詳細資訊，請參閱 [try-catch](../../../language-reference/keywords/try-catch.md)。

Windows 執行階段程式設計中的非同步 API 具有下列其中一種傳回型別 (類似於工作)：

- <xref:Windows.Foundation.IAsyncOperation%601>，對應至 <xref:System.Threading.Tasks.Task%601>
- <xref:Windows.Foundation.IAsyncAction>，對應至 <xref:System.Threading.Tasks.Task>
- <xref:Windows.Foundation.IAsyncActionWithProgress%601>
- <xref:Windows.Foundation.IAsyncOperationWithProgress%602>

## <a name="naming-convention"></a><a name="BKMK_NamingConvention"></a> 命名慣例

依照慣例，傳回常用可等候型別的方法 (例如，、、、 `Task` `Task<T>`) 的 `ValueTask` `ValueTask<T>` 名稱應該以 "Async" 結尾。 會開始執行非同步作業但不會傳回可等候類型的方法不應該具有結尾為 "Async" 的名稱，但其名稱開頭可以是 "Begin"、"Start" 或一些其他動詞，以建議此方法不會傳回或擲回作業結果。

當事件、基底類別或介面合約採用不同的名稱時，您可以忽略慣例。 例如，您不應該重新命名常見的事件處理常式，例如 `OnButtonClick` 。

## <a name="related-topics-and-samples-visual-studio"></a><a name="BKMK_RelatedTopics"></a> 相關主題和範例 (Visual Studio)

| 標題 | 描述 | 範例 |
|--|--|--|
| [如何使用 async 和 await，同時發出多個 web 要求 (c # ) ](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) | 示範如何同時啟動數個工作。 | [非同步範例：平行進行多個 Web 要求 (英文)](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e) |
| [非同步傳回類型 (c # ) ](async-return-types.md) | 說明非同步方法可以傳回的類型，並說明每個類型的適用時機。 |  |
| 使用解除標記做為信號機制來取消工作。 | 顯示如何將下列功能加入至您的非同步方案：<br><br> - [取消 (c # ) 的工作清單 ](cancel-an-async-task-or-a-list-of-tasks.md)<br>- [在一段時間後取消工作 (c # ) ](cancel-async-tasks-after-a-period-of-time.md)<br>- [在非同步工作完成時加以處理 (c # ) ](start-multiple-async-tasks-and-process-them-as-they-complete.md) |  |
| [使用 async 進行檔案存取 (c # ) ](using-async-for-file-access.md) | 列出並示範使用 async 和 await 存取檔案的優點。 |  |
| [以工作為基礎的非同步模式 (點擊) ](../../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) | 描述非同步模式，此模式是以 <xref:System.Threading.Tasks.Task> 和類型為基礎 <xref:System.Threading.Tasks.Task%601> 。 |  |
| [Channel 9 上的非同步影片](https://channel9.msdn.com/search?term=async%20&type=All#pubDate=year&ch9Search&lang-en=en) | 提供有關非同步程式設計的各種不同視訊連結。 |  |

## <a name="see-also"></a>另請參閱

- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)
- [非同步程式設計](../../../async.md)
- [非同步總覽](../../../../standard/async.md)
