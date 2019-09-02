---
title: 產生及使用非同步資料流
description: 這個進階教學課程說明產生及取用非同步資料流提供更自然的方式來處理能以非同步方式產生之資料序列的案例。
ms.date: 02/10/2019
ms.custom: mvc
ms.openlocfilehash: cd1159c139f2c885eacf55b8577bea9e79bf0d7a
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105858"
---
# <a name="tutorial-generate-and-consume-async-streams-using-c-80-and-net-core-30"></a><span data-ttu-id="7ee70-103">教學課程：使用 C# 8.0 與 .NET Core 3.0 產生及取用非同步資料流</span><span class="sxs-lookup"><span data-stu-id="7ee70-103">Tutorial: Generate and consume async streams using C# 8.0 and .NET Core 3.0</span></span>

<span data-ttu-id="7ee70-104">C# 8.0 引進了**非同步資料流**，當能以非同步方式擷取或產生資料流中的元素時，它會建構資料來源資料流處理模型。</span><span class="sxs-lookup"><span data-stu-id="7ee70-104">C# 8.0 introduces **async streams**, which model a streaming source of data when the elements in the data stream may be retrieved or generated asynchronously.</span></span> <span data-ttu-id="7ee70-105">非同步資料流仰賴 .NET Standard 2.1 中引進並在 .NET Core 3.0 中實作的新介面來針對非同步資料流處理資料來源提供自然程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="7ee70-105">Async streams rely on new interfaces introduced in .NET Standard 2.1 and implemented in .NET Core 3.0 to provide a natural programming model for asynchronous streaming data sources.</span></span>

<span data-ttu-id="7ee70-106">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="7ee70-106">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
> - <span data-ttu-id="7ee70-107">建立會以非同步方式產生資料元素序列的資料來源。</span><span class="sxs-lookup"><span data-stu-id="7ee70-107">Create a data source that generates a sequence of data elements asynchronously.</span></span>
> - <span data-ttu-id="7ee70-108">以非同步方式取用資料來源。</span><span class="sxs-lookup"><span data-stu-id="7ee70-108">Consume that data source asynchronously.</span></span>
> - <span data-ttu-id="7ee70-109">識別何時應該使用新的介面與資料來源，而非先前的同步資料來源。</span><span class="sxs-lookup"><span data-stu-id="7ee70-109">Recognize when the new interface and data source are preferred to earlier synchronous data sequences.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7ee70-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="7ee70-110">Prerequisites</span></span>

<span data-ttu-id="7ee70-111">您將必須設定電腦來執行 .NET Core，包括 C# 8.0 搶鮮版 (Beta) 編譯器。</span><span class="sxs-lookup"><span data-stu-id="7ee70-111">You’ll need to set up your machine to run .NET Core, including the C# 8.0 beta compiler.</span></span> <span data-ttu-id="7ee70-112">從 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) 或最新的 [.NET Core 3.0 Preview SDK](https://dotnet.microsoft.com/download/dotnet-core/3.0) 開始，可以使用 C# 8 搶鮮版 (Beta) 編譯器。</span><span class="sxs-lookup"><span data-stu-id="7ee70-112">The C# 8 beta compiler is available starting with [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), or the latest [.NET Core 3.0 preview SDK](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span> <span data-ttu-id="7ee70-113">非同步資料流最早是在 .NET Core 3.0 Preview 1 中提供。</span><span class="sxs-lookup"><span data-stu-id="7ee70-113">Async streams are first available in .NET Core 3.0 preview 1.</span></span>

<span data-ttu-id="7ee70-114">您將必須建立 [GitHub 存取權杖](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/#creating-a-token)，以便存取 GitHub GraphQL 端點。</span><span class="sxs-lookup"><span data-stu-id="7ee70-114">You'll need to create a [GitHub access token](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/#creating-a-token) so that you can access the GitHub GraphQL endpoint.</span></span> <span data-ttu-id="7ee70-115">為您的 GitHub 存取權杖選取下列權限：</span><span class="sxs-lookup"><span data-stu-id="7ee70-115">Select the following permissions for your GitHub Access Token:</span></span>

- <span data-ttu-id="7ee70-116">repo:status</span><span class="sxs-lookup"><span data-stu-id="7ee70-116">repo:status</span></span>
- <span data-ttu-id="7ee70-117">public_repo</span><span class="sxs-lookup"><span data-stu-id="7ee70-117">public_repo</span></span>

<span data-ttu-id="7ee70-118">將存取權杖儲存在安全的地方，以便您可以使用它來取得對 GitHub API 端點的存取權。</span><span class="sxs-lookup"><span data-stu-id="7ee70-118">Save the access token in a safe place so you can use it to gain access to the GitHub API endpoint.</span></span>

> [!WARNING]
> <span data-ttu-id="7ee70-119">保護您個人存取權杖的安全。</span><span class="sxs-lookup"><span data-stu-id="7ee70-119">Keep your personal access token secure.</span></span> <span data-ttu-id="7ee70-120">使用您個人存取權杖的任何軟體都可以使用您的存取權限進行 GitHub API 呼叫。</span><span class="sxs-lookup"><span data-stu-id="7ee70-120">Any software with your personal access token could make GitHub API calls using your access rights.</span></span>

<span data-ttu-id="7ee70-121">本教學課程假設您已熟悉 C# 和 .NET，包括 Visual Studio 或 .NET Core CLI。</span><span class="sxs-lookup"><span data-stu-id="7ee70-121">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="run-the-starter-application"></a><span data-ttu-id="7ee70-122">執行入門應用程式</span><span class="sxs-lookup"><span data-stu-id="7ee70-122">Run the starter application</span></span>

<span data-ttu-id="7ee70-123">您可以從我們的 [dotnet/samples](https://github.com/dotnet/samples) 存放庫 (位於 [csharp/tutorials/AsyncStreams](https://github.com/dotnet/samples/tree/master/csharp/tutorials/AsyncStreams/start) 資料夾中) 取得此教學課程中使用的入門應用程式程式碼。</span><span class="sxs-lookup"><span data-stu-id="7ee70-123">You can get the code for the starter application used in this tutorial from our [dotnet/samples](https://github.com/dotnet/samples) repository in the [csharp/tutorials/AsyncStreams](https://github.com/dotnet/samples/tree/master/csharp/tutorials/AsyncStreams/start) folder.</span></span>

<span data-ttu-id="7ee70-124">入門應用程式是主控台應用程式，它使用 [GitHub GraphQL](https://developer.github.com/v4/) 介面來擷取 [dotnet/docs](https://github.com/dotnet/docs) 存放庫中最近撰寫的議題。</span><span class="sxs-lookup"><span data-stu-id="7ee70-124">The starter application is a console application that uses the [GitHub GraphQL](https://developer.github.com/v4/) interface to retrieve recent issues written in the [dotnet/docs](https://github.com/dotnet/docs) repository.</span></span> <span data-ttu-id="7ee70-125">從查看入門應用程式 `Main` 方法的下列程式碼開始：</span><span class="sxs-lookup"><span data-stu-id="7ee70-125">Start by looking at the following code for the starter app `Main` method:</span></span>

[!code-csharp[StarterAppMain](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#StarterAppMain)]

<span data-ttu-id="7ee70-126">您可以將 `GitHubKey` 環境變數設定到您的個人存取權杖，或可以您可以將 `GenEnvVariable` 呼叫中的最後一個引數取代為您自己的個人存取權杖。</span><span class="sxs-lookup"><span data-stu-id="7ee70-126">You can either set a `GitHubKey` environment variable to your personal access token, or you can replace the last argument in the call to `GenEnvVariable` with your personal access token.</span></span> <span data-ttu-id="7ee70-127">若您會隨著其他項目儲存原始程式碼，或請不要將您的存取碼放在原始程式碼中，也不要將它放在共用原始程式碼存放庫中。</span><span class="sxs-lookup"><span data-stu-id="7ee70-127">Don't put your access code in source code if you'll be saving the source with others, or putting it in a shared source repository.</span></span>

<span data-ttu-id="7ee70-128">建立 GitHub 用戶端之後，`Main` 中的程式碼會建立進度報告物件與取消權杖。</span><span class="sxs-lookup"><span data-stu-id="7ee70-128">After creating the GitHub client, the code in `Main` creates a progress reporting object and a cancellation token.</span></span> <span data-ttu-id="7ee70-129">一旦建立那些物件，`Main` 就會呼叫 `runPagedQueryAsync` 以擷取最近的 250 個已建立議題。</span><span class="sxs-lookup"><span data-stu-id="7ee70-129">Once those objects are created, `Main` calls `runPagedQueryAsync` to retrieve the most recent 250 created issues.</span></span> <span data-ttu-id="7ee70-130">該工作完成之後，會顯示結果。</span><span class="sxs-lookup"><span data-stu-id="7ee70-130">After that task has finished, the results are displayed.</span></span>

<span data-ttu-id="7ee70-131">當您執行入門應用程式時，您可以重點觀察此應用程式如何執行。</span><span class="sxs-lookup"><span data-stu-id="7ee70-131">When you run the starter application, you can make some important observations about how this application runs.</span></span>  <span data-ttu-id="7ee70-132">您將會看到針對從 GitHub 傳回的每個頁面回報的進度。</span><span class="sxs-lookup"><span data-stu-id="7ee70-132">You'll see progress reported for each page returned from GitHub.</span></span> <span data-ttu-id="7ee70-133">您會發現 GitHub 傳回議題的每個新頁面時暫停了一些時間。</span><span class="sxs-lookup"><span data-stu-id="7ee70-133">You can observe a noticeable pause before GitHub returns each new page of issues.</span></span> <span data-ttu-id="7ee70-134">最後，只有在從 GitHub 擷取全部 10 頁之後，才會顯示議題。</span><span class="sxs-lookup"><span data-stu-id="7ee70-134">Finally, the issues are displayed only after all 10 pages have been retrieved from GitHub.</span></span>

## <a name="examine-the-implementation"></a><span data-ttu-id="7ee70-135">檢查實作</span><span class="sxs-lookup"><span data-stu-id="7ee70-135">Examine the implementation</span></span>

<span data-ttu-id="7ee70-136">實作會揭示為何您觀察到上一節中討論的行為。</span><span class="sxs-lookup"><span data-stu-id="7ee70-136">The implementation reveals why you observed the behavior discussed in the previous section.</span></span> <span data-ttu-id="7ee70-137">檢查 `runPagedQueryAsync` 的程式碼：</span><span class="sxs-lookup"><span data-stu-id="7ee70-137">Examine the code for `runPagedQueryAsync`:</span></span>

[!code-csharp[RunPagedQueryStarter](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#RunPagedQuery)]

<span data-ttu-id="7ee70-138">讓我們專注在分頁上述程式碼的演算法與非同步結構。</span><span class="sxs-lookup"><span data-stu-id="7ee70-138">Let's concentrate on the paging algorithm and async structure of the preceding code.</span></span> <span data-ttu-id="7ee70-139">(您可以查閱 [GitHub GraphQL 文件](https://developer.github.com/v4/guides/)以取得有關 GitHub GraphQL API 的詳細資料。)`runPagedQueryAsync` 方法會依從最新到最舊的順序列舉議題。</span><span class="sxs-lookup"><span data-stu-id="7ee70-139">(You can consult the [GitHub GraphQL documentation](https://developer.github.com/v4/guides/) for details on the GitHub GraphQL API.) The `runPagedQueryAsync` method enumerates the issues from most recent to oldest.</span></span> <span data-ttu-id="7ee70-140">它會要求每頁 25 個議題，並檢查回應的 `pageInfo` 結構以使用上一頁繼續。</span><span class="sxs-lookup"><span data-stu-id="7ee70-140">It requests 25 issues per page and examines the `pageInfo` structure of the response to continue with the previous page.</span></span> <span data-ttu-id="7ee70-141">這遵循 GraphQL 對多頁回應的標準分頁支援。</span><span class="sxs-lookup"><span data-stu-id="7ee70-141">That follows GraphQL's standard paging support for multi-page responses.</span></span> <span data-ttu-id="7ee70-142">回應包括 `pageInfo` 物件，此物件包括 `hasPreviousPages` 值與用來要求上一頁的 `startCursor` 值。</span><span class="sxs-lookup"><span data-stu-id="7ee70-142">The response includes a `pageInfo` object that includes a `hasPreviousPages` value and a `startCursor` value used to request the previous page.</span></span> <span data-ttu-id="7ee70-143">議題位於 `nodes` 陣列中。</span><span class="sxs-lookup"><span data-stu-id="7ee70-143">The issues are in the `nodes` array.</span></span> <span data-ttu-id="7ee70-144">`runPagedQueryAsync` 方法會將這些節點附加到包含來自所有頁面之結果的陣列。</span><span class="sxs-lookup"><span data-stu-id="7ee70-144">The `runPagedQueryAsync` method appends these nodes to an array that contains all the results from all pages.</span></span>

<span data-ttu-id="7ee70-145">擷取並還原一頁的結果之後，`runPagedQueryAsync` 會回報進度並檢查取消。</span><span class="sxs-lookup"><span data-stu-id="7ee70-145">After retrieving and restoring a page of results, `runPagedQueryAsync` reports progress and checks for cancellation.</span></span> <span data-ttu-id="7ee70-146">若已要求取消，`runPagedQueryAsync` 會擲回 <xref:System.OperationCanceledException>。</span><span class="sxs-lookup"><span data-stu-id="7ee70-146">If cancellation has been requested, `runPagedQueryAsync` throws an <xref:System.OperationCanceledException>.</span></span>

<span data-ttu-id="7ee70-147">此程式碼中有許多元素可以改進。</span><span class="sxs-lookup"><span data-stu-id="7ee70-147">There are several elements in this code that can be improved.</span></span> <span data-ttu-id="7ee70-148">最重要的是，`runPagedQueryAsync` 必須為傳回的所有議題配置儲存體。</span><span class="sxs-lookup"><span data-stu-id="7ee70-148">Most importantly, `runPagedQueryAsync` must allocate storage for all the issues returned.</span></span> <span data-ttu-id="7ee70-149">此案例會在第 250 個議題停止，因為擷取所有未決議題將需要多得多的記憶體來儲存所以已擷取的議題。</span><span class="sxs-lookup"><span data-stu-id="7ee70-149">This sample stops at 250 issues because retrieving all open issues would require much more memory to store all the retrieved issues.</span></span> <span data-ttu-id="7ee70-150">此外，支援進度與支援取消的通訊協定讓第一次讀取演算法時更難以理解。</span><span class="sxs-lookup"><span data-stu-id="7ee70-150">In addition, the protocols for supporting progress and supporting cancellation make the algorithm harder to understand on its first reading.</span></span> <span data-ttu-id="7ee70-151">您必須查看進度類別以尋找回報進度之處。</span><span class="sxs-lookup"><span data-stu-id="7ee70-151">You must look for the progress class to find where progress is reported.</span></span> <span data-ttu-id="7ee70-152">您也必須透過 <xref:System.Threading.CancellationTokenSource> 與其關聯的 <xref:System.Threading.CancellationToken> 來追蹤通訊，以了解要求取消之處與授與權限之處。</span><span class="sxs-lookup"><span data-stu-id="7ee70-152">You also have to trace the communications through the <xref:System.Threading.CancellationTokenSource> and its associated <xref:System.Threading.CancellationToken> to understand where cancellation is requested and where it's granted.</span></span>

## <a name="async-streams-provide-a-better-way"></a><span data-ttu-id="7ee70-153">非同步資料流提供更好的方式</span><span class="sxs-lookup"><span data-stu-id="7ee70-153">Async streams provide a better way</span></span>

<span data-ttu-id="7ee70-154">非同步資料流與關聯的語言支援可處理所有哪些顧慮。</span><span class="sxs-lookup"><span data-stu-id="7ee70-154">Async streams and the associated language support address all those concerns.</span></span> <span data-ttu-id="7ee70-155">產生序列的程式碼現在可以使用 `yield return` 在使用 `async` 修飾詞宣告的方法中傳回元素。</span><span class="sxs-lookup"><span data-stu-id="7ee70-155">The code that generates the sequence can now use `yield return` to return elements in a method that was declared with the `async` modifier.</span></span> <span data-ttu-id="7ee70-156">您可以使用 `await foreach` 迴圈取用非同步資料流，就像您使用 `foreach` 迴圈取用任何序列一樣。</span><span class="sxs-lookup"><span data-stu-id="7ee70-156">You can consume an async stream using an `await foreach` loop just as you consume any sequence using a `foreach` loop.</span></span>

<span data-ttu-id="7ee70-157">這些新語言功能仰賴 .NET Standard 2.1 中新增並在 .NET Core 3.0 中實作的三個新介面：</span><span class="sxs-lookup"><span data-stu-id="7ee70-157">These new language features depend on three new interfaces added to .NET Standard 2.1 and implemented in .NET Core 3.0:</span></span>

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

<span data-ttu-id="7ee70-158">這三個介面對大部分的 C# 開發人員來說應該都很熟悉。</span><span class="sxs-lookup"><span data-stu-id="7ee70-158">These three interfaces should be familiar to most C# developers.</span></span> <span data-ttu-id="7ee70-159">它們的運作方式與行為類似其同步對等項：</span><span class="sxs-lookup"><span data-stu-id="7ee70-159">They behave in a manner similar to their synchronous counterparts:</span></span>

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IEnumerator%601?displayProperty=nameWithType>
- <xref:System.IDisposable?displayProperty=nameWithType>

<span data-ttu-id="7ee70-160">一個不熟悉的型別可能是 <xref:System.Threading.Tasks.ValueTask?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="7ee70-160">One type that may be unfamiliar is <xref:System.Threading.Tasks.ValueTask?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7ee70-161">`ValueTask` 結構提供類似的 API 給 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 類別。</span><span class="sxs-lookup"><span data-stu-id="7ee70-161">The `ValueTask` struct provides a similar API to the <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="7ee70-162">`ValueTask` 因為效能原因而用於這些介面。</span><span class="sxs-lookup"><span data-stu-id="7ee70-162">`ValueTask` is used in these interfaces for performance reasons.</span></span>

## <a name="convert-to-async-streams"></a><span data-ttu-id="7ee70-163">轉換為非同步資料流</span><span class="sxs-lookup"><span data-stu-id="7ee70-163">Convert to async streams</span></span>

<span data-ttu-id="7ee70-164">接著，轉換 `runPagedQueryAsync` 方法以產生非同步資料流。</span><span class="sxs-lookup"><span data-stu-id="7ee70-164">Next, convert the `runPagedQueryAsync` method to generate an async stream.</span></span> <span data-ttu-id="7ee70-165">首先，變更f `runPagedQueryAsync` 的簽章以傳回 `IAsyncEnumerable<JToken>`，並從參數清單移除取消權杖與進度物件，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="7ee70-165">First, change the signature of `runPagedQueryAsync` to return an `IAsyncEnumerable<JToken>`, and remove the cancellation token and progress objects from the parameter list as shown in the following code:</span></span>

[!code-csharp[FinishedSignature](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#UpdateSignature)]

<span data-ttu-id="7ee70-166">入門程式碼會在擷取頁面時處理每一頁，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="7ee70-166">The starter code processes each page as the page is retrieved, as shown in the following code:</span></span>

[!code-csharp[StarterPaging](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#ProcessPage)]

<span data-ttu-id="7ee70-167">使用下列程式碼取代那三行：</span><span class="sxs-lookup"><span data-stu-id="7ee70-167">Replace those three lines with the following code:</span></span>

[!code-csharp[FinishedPaging](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#YieldReturnPage)]

<span data-ttu-id="7ee70-168">您也可以移除此方法中稍早的 `finalResults` 宣告以及遵循您先前修改之迴圈的 `return` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="7ee70-168">You can also remove the declaration of `finalResults` earlier in this method and the `return` statement that follows the loop you modified.</span></span>

<span data-ttu-id="7ee70-169">您已完成變更以產生非同步資料流。</span><span class="sxs-lookup"><span data-stu-id="7ee70-169">You've finished the changes to generate an async stream.</span></span> <span data-ttu-id="7ee70-170">已完成的方法看起來應該類似下面的程式碼：</span><span class="sxs-lookup"><span data-stu-id="7ee70-170">The finished method should resemble the code below:</span></span>

[!code-csharp[FinishedGenerate](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#GenerateAsyncStream)]

<span data-ttu-id="7ee70-171">接著，您必須變更取用集合以取用非同步資料流的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7ee70-171">Next, you change the code that consumes the collection to consume the async stream.</span></span> <span data-ttu-id="7ee70-172">在 `Main` 中尋找會處理議題集合的下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="7ee70-172">Find the following code in `Main` that processes the collection of issues:</span></span>

[!code-csharp[EnumerateOldStyle](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#EnumerateOldStyle)]

<span data-ttu-id="7ee70-173">使用下列 `await foreach` 迴圈取代該程式碼：</span><span class="sxs-lookup"><span data-stu-id="7ee70-173">Replace that code with the following `await foreach` loop:</span></span>

[!code-csharp[FinishedEnumerateAsyncStream](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#EnumerateAsyncStream)]

<span data-ttu-id="7ee70-174">您可以從 [dotnet/samples](https://github.com/dotnet/samples) 存放庫 (位於 [csharp/tutorials/AsyncStreams](https://github.com/dotnet/samples/tree/master/csharp/tutorials/AsyncStreams/finished) 資料夾中) 取得已完成之教學課程的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7ee70-174">You can get the code for the finished tutorial from the [dotnet/samples](https://github.com/dotnet/samples) repository in the [csharp/tutorials/AsyncStreams](https://github.com/dotnet/samples/tree/master/csharp/tutorials/AsyncStreams/finished) folder.</span></span>

## <a name="run-the-finished-application"></a><span data-ttu-id="7ee70-175">執行已完成的應用程式</span><span class="sxs-lookup"><span data-stu-id="7ee70-175">Run the finished application</span></span>

<span data-ttu-id="7ee70-176">再次執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="7ee70-176">Run the application again.</span></span> <span data-ttu-id="7ee70-177">將其行為與入門應用程式的行為進行比較。</span><span class="sxs-lookup"><span data-stu-id="7ee70-177">Contrast its behavior with the behavior of the starter application.</span></span> <span data-ttu-id="7ee70-178">當第一個結果頁面可用時會儘快列舉。</span><span class="sxs-lookup"><span data-stu-id="7ee70-178">The first page of results is enumerated as soon as it's available.</span></span> <span data-ttu-id="7ee70-179">您會發現要求並擷取每個新頁面時會暫停一些時間，燃後快速列舉下一個頁面的結果。</span><span class="sxs-lookup"><span data-stu-id="7ee70-179">There's an observable pause as each new page is requested and retrieved, then the next page's results are quickly enumerated.</span></span> <span data-ttu-id="7ee70-180">不需要 `try` / `catch` 區塊就能處理取消：呼叫者可以停止列舉集合。</span><span class="sxs-lookup"><span data-stu-id="7ee70-180">The `try` / `catch` block isn't needed to handle cancellation: the caller can stop enumerating the collection.</span></span> <span data-ttu-id="7ee70-181">系統會明確回報進度，因為非同步資料流會在下載每個頁面時產生結果。</span><span class="sxs-lookup"><span data-stu-id="7ee70-181">Progress is clearly reported because the async stream generates results as each page is downloaded.</span></span>

<span data-ttu-id="7ee70-182">您可以透過檢查程式碼看到記憶體使用狀況的改進。</span><span class="sxs-lookup"><span data-stu-id="7ee70-182">You can see improvements in memory use by examining the code.</span></span> <span data-ttu-id="7ee70-183">您再也不需要在列舉結果之前配置集合以儲存所有結果。</span><span class="sxs-lookup"><span data-stu-id="7ee70-183">You no longer need to allocate a collection to store all the results before they're enumerated.</span></span> <span data-ttu-id="7ee70-184">呼叫者可以決定如何取用結果，以及是否需要儲存體集合。</span><span class="sxs-lookup"><span data-stu-id="7ee70-184">The caller can determine how to consume the results and if a storage collection is needed.</span></span>

<span data-ttu-id="7ee70-185">執行入門與已完成的應用程式，您將能親自觀察實作之間的差異。</span><span class="sxs-lookup"><span data-stu-id="7ee70-185">Run both the starter and finished applications and you can observe the differences between the implementations for yourself.</span></span> <span data-ttu-id="7ee70-186">完成之後，您可以刪除開始此教學課程時建立的 GitHub 存取權杖。</span><span class="sxs-lookup"><span data-stu-id="7ee70-186">You can delete the GitHub access token you created when you started this tutorial after you've finished.</span></span> <span data-ttu-id="7ee70-187">若攻擊者取得權杖的存取權，他們將能使用您的認證存取 GitHub API。</span><span class="sxs-lookup"><span data-stu-id="7ee70-187">If an attacker gained access to that token, they could access GitHub APIs using your credentials.</span></span>
