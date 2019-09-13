---
title: 產生及使用非同步資料流
description: 這個進階教學課程說明產生及取用非同步資料流提供更自然的方式來處理能以非同步方式產生之資料序列的案例。
ms.date: 02/10/2019
ms.custom: mvc
ms.openlocfilehash: 3fdf5299deca365c62a00a8320ea335e96d9078c
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926695"
---
# <a name="tutorial-generate-and-consume-async-streams-using-c-80-and-net-core-30"></a>教學課程：使用 C# 8.0 與 .NET Core 3.0 產生及取用非同步資料流

C# 8.0 引進了**非同步資料流**，當能以非同步方式擷取或產生資料流中的元素時，它會建構資料來源資料流處理模型。 非同步資料流仰賴 .NET Standard 2.1 中引進並在 .NET Core 3.0 中實作的新介面來針對非同步資料流處理資料來源提供自然程式設計模型。

在本教學課程中，您將了解如何：

> [!div class="checklist"]
>
> - 建立會以非同步方式產生資料元素序列的資料來源。
> - 以非同步方式取用資料來源。
> - 識別何時應該使用新的介面與資料來源，而非先前的同步資料來源。

## <a name="prerequisites"></a>必要條件

您將必須設定電腦來執行 .NET Core，包括 C# 8.0 搶鮮版 (Beta) 編譯器。 從 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) 或最新的 [.NET Core 3.0 Preview SDK](https://dotnet.microsoft.com/download/dotnet-core/3.0) 開始，可以使用 C# 8 搶鮮版 (Beta) 編譯器。 非同步資料流最早是在 .NET Core 3.0 Preview 1 中提供。

您將必須建立 [GitHub 存取權杖](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/#creating-a-token)，以便存取 GitHub GraphQL 端點。 為您的 GitHub 存取權杖選取下列權限：

- repo:status
- public_repo

將存取權杖儲存在安全的地方，以便您可以使用它來取得對 GitHub API 端點的存取權。

> [!WARNING]
> 保護您個人存取權杖的安全。 使用您個人存取權杖的任何軟體都可以使用您的存取權限進行 GitHub API 呼叫。

本教學課程假設您已熟悉 C# 和 .NET，包括 Visual Studio 或 .NET Core CLI。

## <a name="run-the-starter-application"></a>執行入門應用程式

您可以從我們的 [dotnet/samples](https://github.com/dotnet/samples) 存放庫 (位於 [csharp/tutorials/AsyncStreams](https://github.com/dotnet/samples/tree/master/csharp/tutorials/AsyncStreams/start) 資料夾中) 取得此教學課程中使用的入門應用程式程式碼。

入門應用程式是主控台應用程式，它使用 [GitHub GraphQL](https://developer.github.com/v4/) 介面來擷取 [dotnet/docs](https://github.com/dotnet/docs) 存放庫中最近撰寫的議題。 從查看入門應用程式 `Main` 方法的下列程式碼開始：

[!code-csharp[StarterAppMain](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#StarterAppMain)]

您可以將 `GitHubKey` 環境變數設定到您的個人存取權杖，或可以您可以將 `GenEnvVariable` 呼叫中的最後一個引數取代為您自己的個人存取權杖。 若您會隨著其他項目儲存原始程式碼，或請不要將您的存取碼放在原始程式碼中，也不要將它放在共用原始程式碼存放庫中。

建立 GitHub 用戶端之後，`Main` 中的程式碼會建立進度報告物件與取消權杖。 一旦建立那些物件，`Main` 就會呼叫 `runPagedQueryAsync` 以擷取最近的 250 個已建立議題。 該工作完成之後，會顯示結果。

當您執行入門應用程式時，您可以重點觀察此應用程式如何執行。  您將會看到針對從 GitHub 傳回的每個頁面回報的進度。 您會發現 GitHub 傳回議題的每個新頁面時暫停了一些時間。 最後，只有在從 GitHub 擷取全部 10 頁之後，才會顯示議題。

## <a name="examine-the-implementation"></a>檢查實作

實作會揭示為何您觀察到上一節中討論的行為。 檢查 `runPagedQueryAsync` 的程式碼：

[!code-csharp[RunPagedQueryStarter](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#RunPagedQuery)]

讓我們專注在分頁上述程式碼的演算法與非同步結構。 (您可以查閱 [GitHub GraphQL 文件](https://developer.github.com/v4/guides/)以取得有關 GitHub GraphQL API 的詳細資料。)`runPagedQueryAsync` 方法會依從最新到最舊的順序列舉議題。 它會要求每頁 25 個議題，並檢查回應的 `pageInfo` 結構以使用上一頁繼續。 這遵循 GraphQL 對多頁回應的標準分頁支援。 回應包括 `pageInfo` 物件，此物件包括 `hasPreviousPages` 值與用來要求上一頁的 `startCursor` 值。 議題位於 `nodes` 陣列中。 `runPagedQueryAsync` 方法會將這些節點附加到包含來自所有頁面之結果的陣列。

擷取並還原一頁的結果之後，`runPagedQueryAsync` 會回報進度並檢查取消。 若已要求取消，`runPagedQueryAsync` 會擲回 <xref:System.OperationCanceledException>。

此程式碼中有許多元素可以改進。 最重要的是，`runPagedQueryAsync` 必須為傳回的所有議題配置儲存體。 此案例會在第 250 個議題停止，因為擷取所有未決議題將需要多得多的記憶體來儲存所以已擷取的議題。 此外，支援進度與支援取消的通訊協定讓第一次讀取演算法時更難以理解。 您必須查看進度類別以尋找回報進度之處。 您也必須透過 <xref:System.Threading.CancellationTokenSource> 與其關聯的 <xref:System.Threading.CancellationToken> 來追蹤通訊，以了解要求取消之處與授與權限之處。

## <a name="async-streams-provide-a-better-way"></a>非同步資料流提供更好的方式

非同步資料流與關聯的語言支援可處理所有哪些顧慮。 產生序列的程式碼現在可以使用 `yield return` 在使用 `async` 修飾詞宣告的方法中傳回元素。 您可以使用 `await foreach` 迴圈取用非同步資料流，就像您使用 `foreach` 迴圈取用任何序列一樣。

這些新語言功能仰賴 .NET Standard 2.1 中新增並在 .NET Core 3.0 中實作的三個新介面：

```csharp
namespace System.Collections.Generic
{
    public interface IAsyncEnumerable<out T>
    {
        IAsyncEnumerator<T> GetAsyncEnumerator(CancellationToken cancellationToken = default);
    }

    public interface IAsyncEnumerator<out T> : IAsyncDisposable
    {
        T Current { get; }

        ValueTask<bool> MoveNextAsync();
    }
}

namespace System
{
    public interface IAsyncDisposable
    {
        ValueTask DisposeAsync();
    }
}
```

這三個介面對大部分的 C# 開發人員來說應該都很熟悉。 它們的運作方式與行為類似其同步對等項：

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IEnumerator%601?displayProperty=nameWithType>
- <xref:System.IDisposable?displayProperty=nameWithType>

一個不熟悉的型別可能是 <xref:System.Threading.Tasks.ValueTask?displayProperty=nameWithType>。 `ValueTask` 結構提供類似的 API 給 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 類別。 `ValueTask` 因為效能原因而用於這些介面。

## <a name="convert-to-async-streams"></a>轉換為非同步資料流

接著，轉換 `runPagedQueryAsync` 方法以產生非同步資料流。 首先，變更f `runPagedQueryAsync` 的簽章以傳回 `IAsyncEnumerable<JToken>`，並從參數清單移除取消權杖與進度物件，如下列程式碼所示：

[!code-csharp[FinishedSignature](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#UpdateSignature)]

入門程式碼會在擷取頁面時處理每一頁，如下列程式碼所示：

[!code-csharp[StarterPaging](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#ProcessPage)]

使用下列程式碼取代那三行：

[!code-csharp[FinishedPaging](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#YieldReturnPage)]

您也可以移除此方法中稍早的 `finalResults` 宣告以及遵循您先前修改之迴圈的 `return` 陳述式。

您已完成變更以產生非同步資料流。 已完成的方法看起來應該類似下面的程式碼：

[!code-csharp[FinishedGenerate](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#GenerateAsyncStream)]

接著，您必須變更取用集合以取用非同步資料流的程式碼。 在 `Main` 中尋找會處理議題集合的下列程式碼：

[!code-csharp[EnumerateOldStyle](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#EnumerateOldStyle)]

使用下列 `await foreach` 迴圈取代該程式碼：

[!code-csharp[FinishedEnumerateAsyncStream](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#EnumerateAsyncStream)]

您可以從 [dotnet/samples](https://github.com/dotnet/samples) 存放庫 (位於 [csharp/tutorials/AsyncStreams](https://github.com/dotnet/samples/tree/master/csharp/tutorials/AsyncStreams/finished) 資料夾中) 取得已完成之教學課程的程式碼。

## <a name="run-the-finished-application"></a>執行已完成的應用程式

再次執行應用程式。 將其行為與入門應用程式的行為進行比較。 當第一個結果頁面可用時會儘快列舉。 您會發現要求並擷取每個新頁面時會暫停一些時間，燃後快速列舉下一個頁面的結果。 不需要 `try` / `catch` 區塊就能處理取消：呼叫者可以停止列舉集合。 系統會明確回報進度，因為非同步資料流會在下載每個頁面時產生結果。

您可以透過檢查程式碼看到記憶體使用狀況的改進。 您再也不需要在列舉結果之前配置集合以儲存所有結果。 呼叫者可以決定如何取用結果，以及是否需要儲存體集合。

執行入門與已完成的應用程式，您將能親自觀察實作之間的差異。 完成之後，您可以刪除開始此教學課程時建立的 GitHub 存取權杖。 若攻擊者取得權杖的存取權，他們將能使用您的認證存取 GitHub API。
