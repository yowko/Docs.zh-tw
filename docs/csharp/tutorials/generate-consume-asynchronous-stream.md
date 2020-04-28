---
title: 產生及使用非同步資料流
description: 這個 advanced 教學課程會示範如何產生和使用非同步資料流程。 非同步資料流程提供更自然的方法來處理可能以非同步方式產生的資料序列。
ms.date: 02/10/2019
ms.technology: csharp-async
ms.custom: mvc
ms.openlocfilehash: 03254e5208a048469f4753d632de7b0d451cde40
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2020
ms.locfileid: "82200102"
---
# <a name="tutorial-generate-and-consume-async-streams-using-c-80-and-net-core-30"></a>教學課程：使用 c # 8.0 和 .NET Core 3.0 產生和使用非同步資料流程

C # 8.0 引進**非同步資料流程**，它會建立資料流程的資料流程來源模型。 資料流程通常會以非同步方式抓取或產生元素。 非同步資料流程依賴 .NET Standard 2.1 中引進的新介面。 這些介面在 .NET Core 3.0 和更新版本中受到支援。 它們會為非同步串流資料來源提供自然的程式設計模型。

您將在本教學課程中了解如何：

> [!div class="checklist"]
>
> - 建立會以非同步方式產生資料元素序列的資料來源。
> - 以非同步方式取用資料來源。
> - 支援非同步資料流程的取消和捕捉內容。
> - 識別何時應該使用新的介面與資料來源，而非先前的同步資料來源。

## <a name="prerequisites"></a>先決條件

您必須設定電腦以執行 .NET Core，包括 c # 8.0 編譯器。 從[Visual Studio 2019 16.3 版](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)或[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download)開始，可以使用 c # 8 編譯器。

您將必須建立 [GitHub 存取權杖](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/#creating-a-token)，以便存取 GitHub GraphQL 端點。 為您的 GitHub 存取權杖選取下列權限：

- repo:status
- public_repo

將存取權杖儲存在安全的地方，以便您可以使用它來取得對 GitHub API 端點的存取權。

> [!WARNING]
> 保護您個人存取權杖的安全。 使用您個人存取權杖的任何軟體都可以使用您的存取權限進行 GitHub API 呼叫。

本教學課程假設您已熟悉 C# 和 .NET，包括 Visual Studio 或 .NET Core CLI。

## <a name="run-the-starter-application"></a>執行入門應用程式

您可以從[csharp/教學課程/AsyncStreams](https://github.com/dotnet/docs/tree/master/csharp/tutorials/snippets/generate-consume-asynchronous-streams/start)資料夾中的[dotnet/](https://github.com/dotnet/docs)檔存放庫，取得本教學課程中使用之入門應用程式的程式碼。

入門應用程式是主控台應用程式，它使用 [GitHub GraphQL](https://developer.github.com/v4/) 介面來擷取 [dotnet/docs](https://github.com/dotnet/docs) 存放庫中最近撰寫的議題。 從查看入門應用程式 `Main` 方法的下列程式碼開始：

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/start/Program.cs" id="SnippetStarterAppMain" :::

您可以將 `GitHubKey` 環境變數設定到您的個人存取權杖，或可以您可以將 `GenEnvVariable` 呼叫中的最後一個引數取代為您自己的個人存取權杖。 如果您要與其他人共用原始碼，請勿將您的存取程式碼放在原始程式碼中。 絕對不要將存取代碼上傳至共用來源存放庫。

建立 GitHub 用戶端之後，`Main` 中的程式碼會建立進度報告物件與取消權杖。 一旦建立那些物件，`Main` 就會呼叫 `runPagedQueryAsync` 以擷取最近的 250 個已建立議題。 該工作完成之後，會顯示結果。

當您執行入門應用程式時，您可以重點觀察此應用程式如何執行。  您將會看到針對從 GitHub 傳回的每個頁面回報的進度。 您會發現 GitHub 傳回議題的每個新頁面時暫停了一些時間。 最後，只有在從 GitHub 擷取全部 10 頁之後，才會顯示議題。

## <a name="examine-the-implementation"></a>檢查實作

實作會揭示為何您觀察到上一節中討論的行為。 檢查 `runPagedQueryAsync` 的程式碼：

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/start/Program.cs" id="SnippetRunPagedQuery" :::

讓我們專注在分頁上述程式碼的演算法與非同步結構。 （如需 GitHub GraphQL API 的詳細資訊，您可以參閱[Github GraphQL 檔](https://developer.github.com/v4/guides/)）。`runPagedQueryAsync`方法會列舉最新到最舊的問題。 它會要求每頁 25 個議題，並檢查回應的 `pageInfo` 結構以使用上一頁繼續。 這遵循 GraphQL 對多頁回應的標準分頁支援。 回應包括 `pageInfo` 物件，此物件包括 `hasPreviousPages` 值與用來要求上一頁的 `startCursor` 值。 議題位於 `nodes` 陣列中。 `runPagedQueryAsync` 方法會將這些節點附加到包含來自所有頁面之結果的陣列。

擷取並還原一頁的結果之後，`runPagedQueryAsync` 會回報進度並檢查取消。 若已要求取消，`runPagedQueryAsync` 會擲回 <xref:System.OperationCanceledException>。

此程式碼中有許多元素可以改進。 最重要的是，`runPagedQueryAsync` 必須為傳回的所有議題配置儲存體。 此案例會在第 250 個議題停止，因為擷取所有未決議題將需要多得多的記憶體來儲存所以已擷取的議題。 支援進度報告和取消的通訊協定會使演算法更難理解其第一次閱讀。 涉及更多類型和 Api。 您必須透過<xref:System.Threading.CancellationTokenSource>和其相關聯<xref:System.Threading.CancellationToken>的來追蹤通訊，以瞭解要求取消的位置及授與的位置。

## <a name="async-streams-provide-a-better-way"></a>非同步資料流提供更好的方式

非同步資料流與關聯的語言支援可處理所有哪些顧慮。 產生序列的程式碼現在可以使用 `yield return` 在使用 `async` 修飾詞宣告的方法中傳回元素。 您可以使用 `await foreach` 迴圈取用非同步資料流，就像您使用 `foreach` 迴圈取用任何序列一樣。

這些新語言功能仰賴 .NET Standard 2.1 中新增並在 .NET Core 3.0 中實作的三個新介面：

- <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>
- <xref:System.IAsyncDisposable?displayProperty=nameWithType>

這三個介面對大部分的 C# 開發人員來說應該都很熟悉。 它們的運作方式與行為類似其同步對等項：

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IEnumerator%601?displayProperty=nameWithType>
- <xref:System.IDisposable?displayProperty=nameWithType>

一個不熟悉的型別可能是 <xref:System.Threading.Tasks.ValueTask?displayProperty=nameWithType>。 `ValueTask` 結構提供類似的 API 給 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 類別。 `ValueTask` 因為效能原因而用於這些介面。

## <a name="convert-to-async-streams"></a>轉換為非同步資料流

接著，轉換 `runPagedQueryAsync` 方法以產生非同步資料流。 首先，變更f `runPagedQueryAsync` 的簽章以傳回 `IAsyncEnumerable<JToken>`，並從參數清單移除取消權杖與進度物件，如下列程式碼所示：

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetUpdateSignature" :::

入門程式碼會在擷取頁面時處理每一頁，如下列程式碼所示：

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/start/Program.cs" id="SnippetProcessPage" :::

使用下列程式碼取代那三行：

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetYieldReturnPage" :::

您也可以移除此方法中稍早的 `finalResults` 宣告以及遵循您先前修改之迴圈的 `return` 陳述式。

您已完成變更以產生非同步資料流。 完成的方法應該類似下列程式碼：

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetGenerateAsyncStream" :::

接著，您必須變更取用集合以取用非同步資料流的程式碼。 在 `Main` 中尋找會處理議題集合的下列程式碼：

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/start/Program.cs" id="SnippetEnumerateOldStyle" :::

使用下列 `await foreach` 迴圈取代該程式碼：

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetEnumerateAsyncStream" :::

新介面<xref:System.Collections.Generic.IAsyncEnumerator%601>衍生自<xref:System.IAsyncDisposable>。 這表示當迴圈完成時，先前的迴圈會以非同步方式處置資料流程。 您可以想像一下迴圈看起來像下列程式碼：

```csharp
int num = 0;
var enumerator = runPagedQueryAsync(client, PagedIssueQuery, "docs").GetEnumeratorAsync();
try
{
    while (await enumerator.MoveNextAsync())
    {
        var issue = enumerator.Current;
        Console.WriteLine(issue);
        Console.WriteLine($"Received {++num} issues in total");
    }
} finally
{
    if (enumerator != null)
        await enumerator.DisposeAsync();
}
```

根據預設，資料流程元素會在已捕捉的內容中處理。 如果您想要停用內容的捕捉，請使用<xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType>擴充方法。 如需同步處理內容及取得目前內容的詳細資訊，請參閱有關[使用以工作為基礎的非同步模式](../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)的文章。

非同步資料流程支援使用與其他`async`方法相同的通訊協定取消。 您會修改非同步反覆運算器方法的簽章，如下所示，以支援取消：

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetGenerateWithCancellation" :::

<xref:System.Runtime.CompilerServices.EnumeratorCancellationAttribute?dipslayProperty=nameWithType>屬性會使編譯器產生的<xref:System.Collections.Generic.IAsyncEnumerator%601>程式碼，讓非同步反覆運算器的主體能夠`GetAsyncEnumerator`看見該 token 做為該引數。 在`runQueryAsync`中，您可以檢查權杖的狀態，並在要求時取消進一步的工作。

您可以使用另一個擴充<xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.WithCancellation%2A>方法，將解除標記傳遞給非同步資料流程。 您將修改列舉問題的迴圈，如下所示：

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetEnumerateWithCancellation" :::

您可以從[csharp/教學課程/AsyncStreams](https://github.com/dotnet/docs/tree/master/csharp/tutorials/snippets/generate-consume-asynchronous-streams/finished)資料夾中的[dotnet/](https://github.com/dotnet/docs)檔存放庫取得已完成之教學課程的程式碼。

## <a name="run-the-finished-application"></a>執行已完成的應用程式

再次執行應用程式。 將其行為與入門應用程式的行為進行比較。 當第一個結果頁面可用時會儘快列舉。 您會發現要求並擷取每個新頁面時會暫停一些時間，燃後快速列舉下一個頁面的結果。 不需要 `try` / `catch` 區塊就能處理取消：呼叫者可以停止列舉集合。 系統會明確回報進度，因為非同步資料流會在下載每個頁面時產生結果。 傳回之每個問題的狀態會順暢地包含`await foreach`在迴圈中。 您不需要回呼物件來追蹤進度。

您可以透過檢查程式碼看到記憶體使用狀況的改進。 您再也不需要在列舉結果之前配置集合以儲存所有結果。 呼叫者可以決定如何取用結果，以及是否需要儲存體集合。

執行入門與已完成的應用程式，您將能親自觀察實作之間的差異。 完成之後，您可以刪除開始此教學課程時建立的 GitHub 存取權杖。 若攻擊者取得權杖的存取權，他們將能使用您的認證存取 GitHub API。
