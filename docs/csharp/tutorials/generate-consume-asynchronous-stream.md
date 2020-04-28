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
# <a name="tutorial-generate-and-consume-async-streams-using-c-80-and-net-core-30"></a><span data-ttu-id="5a81b-104">教學課程：使用 c # 8.0 和 .NET Core 3.0 產生和使用非同步資料流程</span><span class="sxs-lookup"><span data-stu-id="5a81b-104">Tutorial: Generate and consume async streams using C# 8.0 and .NET Core 3.0</span></span>

<span data-ttu-id="5a81b-105">C # 8.0 引進**非同步資料流程**，它會建立資料流程的資料流程來源模型。</span><span class="sxs-lookup"><span data-stu-id="5a81b-105">C# 8.0 introduces **async streams**, which model a streaming source of data.</span></span> <span data-ttu-id="5a81b-106">資料流程通常會以非同步方式抓取或產生元素。</span><span class="sxs-lookup"><span data-stu-id="5a81b-106">Data streams often retrieve or generate elements asynchronously.</span></span> <span data-ttu-id="5a81b-107">非同步資料流程依賴 .NET Standard 2.1 中引進的新介面。</span><span class="sxs-lookup"><span data-stu-id="5a81b-107">Async streams rely on new interfaces introduced in .NET Standard 2.1.</span></span> <span data-ttu-id="5a81b-108">這些介面在 .NET Core 3.0 和更新版本中受到支援。</span><span class="sxs-lookup"><span data-stu-id="5a81b-108">These interfaces are supported in .NET Core 3.0 and later.</span></span> <span data-ttu-id="5a81b-109">它們會為非同步串流資料來源提供自然的程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="5a81b-109">They provide a natural programming model for asynchronous streaming data sources.</span></span>

<span data-ttu-id="5a81b-110">您將在本教學課程中了解如何：</span><span class="sxs-lookup"><span data-stu-id="5a81b-110">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="5a81b-111">建立會以非同步方式產生資料元素序列的資料來源。</span><span class="sxs-lookup"><span data-stu-id="5a81b-111">Create a data source that generates a sequence of data elements asynchronously.</span></span>
> - <span data-ttu-id="5a81b-112">以非同步方式取用資料來源。</span><span class="sxs-lookup"><span data-stu-id="5a81b-112">Consume that data source asynchronously.</span></span>
> - <span data-ttu-id="5a81b-113">支援非同步資料流程的取消和捕捉內容。</span><span class="sxs-lookup"><span data-stu-id="5a81b-113">Support cancellation and captured contexts for asynchronous streams.</span></span>
> - <span data-ttu-id="5a81b-114">識別何時應該使用新的介面與資料來源，而非先前的同步資料來源。</span><span class="sxs-lookup"><span data-stu-id="5a81b-114">Recognize when the new interface and data source are preferred to earlier synchronous data sequences.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5a81b-115">先決條件</span><span class="sxs-lookup"><span data-stu-id="5a81b-115">Prerequisites</span></span>

<span data-ttu-id="5a81b-116">您必須設定電腦以執行 .NET Core，包括 c # 8.0 編譯器。</span><span class="sxs-lookup"><span data-stu-id="5a81b-116">You'll need to set up your machine to run .NET Core, including the C# 8.0 compiler.</span></span> <span data-ttu-id="5a81b-117">從[Visual Studio 2019 16.3 版](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)或[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download)開始，可以使用 c # 8 編譯器。</span><span class="sxs-lookup"><span data-stu-id="5a81b-117">The C# 8 compiler is available starting with [Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download).</span></span>

<span data-ttu-id="5a81b-118">您將必須建立 [GitHub 存取權杖](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/#creating-a-token)，以便存取 GitHub GraphQL 端點。</span><span class="sxs-lookup"><span data-stu-id="5a81b-118">You'll need to create a [GitHub access token](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/#creating-a-token) so that you can access the GitHub GraphQL endpoint.</span></span> <span data-ttu-id="5a81b-119">為您的 GitHub 存取權杖選取下列權限：</span><span class="sxs-lookup"><span data-stu-id="5a81b-119">Select the following permissions for your GitHub Access Token:</span></span>

- <span data-ttu-id="5a81b-120">repo:status</span><span class="sxs-lookup"><span data-stu-id="5a81b-120">repo:status</span></span>
- <span data-ttu-id="5a81b-121">public_repo</span><span class="sxs-lookup"><span data-stu-id="5a81b-121">public_repo</span></span>

<span data-ttu-id="5a81b-122">將存取權杖儲存在安全的地方，以便您可以使用它來取得對 GitHub API 端點的存取權。</span><span class="sxs-lookup"><span data-stu-id="5a81b-122">Save the access token in a safe place so you can use it to gain access to the GitHub API endpoint.</span></span>

> [!WARNING]
> <span data-ttu-id="5a81b-123">保護您個人存取權杖的安全。</span><span class="sxs-lookup"><span data-stu-id="5a81b-123">Keep your personal access token secure.</span></span> <span data-ttu-id="5a81b-124">使用您個人存取權杖的任何軟體都可以使用您的存取權限進行 GitHub API 呼叫。</span><span class="sxs-lookup"><span data-stu-id="5a81b-124">Any software with your personal access token could make GitHub API calls using your access rights.</span></span>

<span data-ttu-id="5a81b-125">本教學課程假設您已熟悉 C# 和 .NET，包括 Visual Studio 或 .NET Core CLI。</span><span class="sxs-lookup"><span data-stu-id="5a81b-125">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="run-the-starter-application"></a><span data-ttu-id="5a81b-126">執行入門應用程式</span><span class="sxs-lookup"><span data-stu-id="5a81b-126">Run the starter application</span></span>

<span data-ttu-id="5a81b-127">您可以從[csharp/教學課程/AsyncStreams](https://github.com/dotnet/docs/tree/master/csharp/tutorials/snippets/generate-consume-asynchronous-streams/start)資料夾中的[dotnet/](https://github.com/dotnet/docs)檔存放庫，取得本教學課程中使用之入門應用程式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5a81b-127">You can get the code for the starter application used in this tutorial from the [dotnet/docs](https://github.com/dotnet/docs) repository in the [csharp/tutorials/AsyncStreams](https://github.com/dotnet/docs/tree/master/csharp/tutorials/snippets/generate-consume-asynchronous-streams/start) folder.</span></span>

<span data-ttu-id="5a81b-128">入門應用程式是主控台應用程式，它使用 [GitHub GraphQL](https://developer.github.com/v4/) 介面來擷取 [dotnet/docs](https://github.com/dotnet/docs) 存放庫中最近撰寫的議題。</span><span class="sxs-lookup"><span data-stu-id="5a81b-128">The starter application is a console application that uses the [GitHub GraphQL](https://developer.github.com/v4/) interface to retrieve recent issues written in the [dotnet/docs](https://github.com/dotnet/docs) repository.</span></span> <span data-ttu-id="5a81b-129">從查看入門應用程式 `Main` 方法的下列程式碼開始：</span><span class="sxs-lookup"><span data-stu-id="5a81b-129">Start by looking at the following code for the starter app `Main` method:</span></span>

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/start/Program.cs" id="SnippetStarterAppMain" :::

<span data-ttu-id="5a81b-130">您可以將 `GitHubKey` 環境變數設定到您的個人存取權杖，或可以您可以將 `GenEnvVariable` 呼叫中的最後一個引數取代為您自己的個人存取權杖。</span><span class="sxs-lookup"><span data-stu-id="5a81b-130">You can either set a `GitHubKey` environment variable to your personal access token, or you can replace the last argument in the call to `GenEnvVariable` with your personal access token.</span></span> <span data-ttu-id="5a81b-131">如果您要與其他人共用原始碼，請勿將您的存取程式碼放在原始程式碼中。</span><span class="sxs-lookup"><span data-stu-id="5a81b-131">Don't put your access code in source code if you'll be sharing the source with others.</span></span> <span data-ttu-id="5a81b-132">絕對不要將存取代碼上傳至共用來源存放庫。</span><span class="sxs-lookup"><span data-stu-id="5a81b-132">Never upload access codes to a shared source repository.</span></span>

<span data-ttu-id="5a81b-133">建立 GitHub 用戶端之後，`Main` 中的程式碼會建立進度報告物件與取消權杖。</span><span class="sxs-lookup"><span data-stu-id="5a81b-133">After creating the GitHub client, the code in `Main` creates a progress reporting object and a cancellation token.</span></span> <span data-ttu-id="5a81b-134">一旦建立那些物件，`Main` 就會呼叫 `runPagedQueryAsync` 以擷取最近的 250 個已建立議題。</span><span class="sxs-lookup"><span data-stu-id="5a81b-134">Once those objects are created, `Main` calls `runPagedQueryAsync` to retrieve the most recent 250 created issues.</span></span> <span data-ttu-id="5a81b-135">該工作完成之後，會顯示結果。</span><span class="sxs-lookup"><span data-stu-id="5a81b-135">After that task has finished, the results are displayed.</span></span>

<span data-ttu-id="5a81b-136">當您執行入門應用程式時，您可以重點觀察此應用程式如何執行。</span><span class="sxs-lookup"><span data-stu-id="5a81b-136">When you run the starter application, you can make some important observations about how this application runs.</span></span>  <span data-ttu-id="5a81b-137">您將會看到針對從 GitHub 傳回的每個頁面回報的進度。</span><span class="sxs-lookup"><span data-stu-id="5a81b-137">You'll see progress reported for each page returned from GitHub.</span></span> <span data-ttu-id="5a81b-138">您會發現 GitHub 傳回議題的每個新頁面時暫停了一些時間。</span><span class="sxs-lookup"><span data-stu-id="5a81b-138">You can observe a noticeable pause before GitHub returns each new page of issues.</span></span> <span data-ttu-id="5a81b-139">最後，只有在從 GitHub 擷取全部 10 頁之後，才會顯示議題。</span><span class="sxs-lookup"><span data-stu-id="5a81b-139">Finally, the issues are displayed only after all 10 pages have been retrieved from GitHub.</span></span>

## <a name="examine-the-implementation"></a><span data-ttu-id="5a81b-140">檢查實作</span><span class="sxs-lookup"><span data-stu-id="5a81b-140">Examine the implementation</span></span>

<span data-ttu-id="5a81b-141">實作會揭示為何您觀察到上一節中討論的行為。</span><span class="sxs-lookup"><span data-stu-id="5a81b-141">The implementation reveals why you observed the behavior discussed in the previous section.</span></span> <span data-ttu-id="5a81b-142">檢查 `runPagedQueryAsync` 的程式碼：</span><span class="sxs-lookup"><span data-stu-id="5a81b-142">Examine the code for `runPagedQueryAsync`:</span></span>

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/start/Program.cs" id="SnippetRunPagedQuery" :::

<span data-ttu-id="5a81b-143">讓我們專注在分頁上述程式碼的演算法與非同步結構。</span><span class="sxs-lookup"><span data-stu-id="5a81b-143">Let's concentrate on the paging algorithm and async structure of the preceding code.</span></span> <span data-ttu-id="5a81b-144">（如需 GitHub GraphQL API 的詳細資訊，您可以參閱[Github GraphQL 檔](https://developer.github.com/v4/guides/)）。`runPagedQueryAsync`方法會列舉最新到最舊的問題。</span><span class="sxs-lookup"><span data-stu-id="5a81b-144">(You can consult the [GitHub GraphQL documentation](https://developer.github.com/v4/guides/) for details on the GitHub GraphQL API.) The `runPagedQueryAsync` method enumerates the issues from most recent to oldest.</span></span> <span data-ttu-id="5a81b-145">它會要求每頁 25 個議題，並檢查回應的 `pageInfo` 結構以使用上一頁繼續。</span><span class="sxs-lookup"><span data-stu-id="5a81b-145">It requests 25 issues per page and examines the `pageInfo` structure of the response to continue with the previous page.</span></span> <span data-ttu-id="5a81b-146">這遵循 GraphQL 對多頁回應的標準分頁支援。</span><span class="sxs-lookup"><span data-stu-id="5a81b-146">That follows GraphQL's standard paging support for multi-page responses.</span></span> <span data-ttu-id="5a81b-147">回應包括 `pageInfo` 物件，此物件包括 `hasPreviousPages` 值與用來要求上一頁的 `startCursor` 值。</span><span class="sxs-lookup"><span data-stu-id="5a81b-147">The response includes a `pageInfo` object that includes a `hasPreviousPages` value and a `startCursor` value used to request the previous page.</span></span> <span data-ttu-id="5a81b-148">議題位於 `nodes` 陣列中。</span><span class="sxs-lookup"><span data-stu-id="5a81b-148">The issues are in the `nodes` array.</span></span> <span data-ttu-id="5a81b-149">`runPagedQueryAsync` 方法會將這些節點附加到包含來自所有頁面之結果的陣列。</span><span class="sxs-lookup"><span data-stu-id="5a81b-149">The `runPagedQueryAsync` method appends these nodes to an array that contains all the results from all pages.</span></span>

<span data-ttu-id="5a81b-150">擷取並還原一頁的結果之後，`runPagedQueryAsync` 會回報進度並檢查取消。</span><span class="sxs-lookup"><span data-stu-id="5a81b-150">After retrieving and restoring a page of results, `runPagedQueryAsync` reports progress and checks for cancellation.</span></span> <span data-ttu-id="5a81b-151">若已要求取消，`runPagedQueryAsync` 會擲回 <xref:System.OperationCanceledException>。</span><span class="sxs-lookup"><span data-stu-id="5a81b-151">If cancellation has been requested, `runPagedQueryAsync` throws an <xref:System.OperationCanceledException>.</span></span>

<span data-ttu-id="5a81b-152">此程式碼中有許多元素可以改進。</span><span class="sxs-lookup"><span data-stu-id="5a81b-152">There are several elements in this code that can be improved.</span></span> <span data-ttu-id="5a81b-153">最重要的是，`runPagedQueryAsync` 必須為傳回的所有議題配置儲存體。</span><span class="sxs-lookup"><span data-stu-id="5a81b-153">Most importantly, `runPagedQueryAsync` must allocate storage for all the issues returned.</span></span> <span data-ttu-id="5a81b-154">此案例會在第 250 個議題停止，因為擷取所有未決議題將需要多得多的記憶體來儲存所以已擷取的議題。</span><span class="sxs-lookup"><span data-stu-id="5a81b-154">This sample stops at 250 issues because retrieving all open issues would require much more memory to store all the retrieved issues.</span></span> <span data-ttu-id="5a81b-155">支援進度報告和取消的通訊協定會使演算法更難理解其第一次閱讀。</span><span class="sxs-lookup"><span data-stu-id="5a81b-155">The protocols for supporting progress reports and cancellation make the algorithm harder to understand on its first reading.</span></span> <span data-ttu-id="5a81b-156">涉及更多類型和 Api。</span><span class="sxs-lookup"><span data-stu-id="5a81b-156">More types and APIs are involved.</span></span> <span data-ttu-id="5a81b-157">您必須透過<xref:System.Threading.CancellationTokenSource>和其相關聯<xref:System.Threading.CancellationToken>的來追蹤通訊，以瞭解要求取消的位置及授與的位置。</span><span class="sxs-lookup"><span data-stu-id="5a81b-157">You must trace the communications through the <xref:System.Threading.CancellationTokenSource> and its associated <xref:System.Threading.CancellationToken> to understand where cancellation is requested and where it's granted.</span></span>

## <a name="async-streams-provide-a-better-way"></a><span data-ttu-id="5a81b-158">非同步資料流提供更好的方式</span><span class="sxs-lookup"><span data-stu-id="5a81b-158">Async streams provide a better way</span></span>

<span data-ttu-id="5a81b-159">非同步資料流與關聯的語言支援可處理所有哪些顧慮。</span><span class="sxs-lookup"><span data-stu-id="5a81b-159">Async streams and the associated language support address all those concerns.</span></span> <span data-ttu-id="5a81b-160">產生序列的程式碼現在可以使用 `yield return` 在使用 `async` 修飾詞宣告的方法中傳回元素。</span><span class="sxs-lookup"><span data-stu-id="5a81b-160">The code that generates the sequence can now use `yield return` to return elements in a method that was declared with the `async` modifier.</span></span> <span data-ttu-id="5a81b-161">您可以使用 `await foreach` 迴圈取用非同步資料流，就像您使用 `foreach` 迴圈取用任何序列一樣。</span><span class="sxs-lookup"><span data-stu-id="5a81b-161">You can consume an async stream using an `await foreach` loop just as you consume any sequence using a `foreach` loop.</span></span>

<span data-ttu-id="5a81b-162">這些新語言功能仰賴 .NET Standard 2.1 中新增並在 .NET Core 3.0 中實作的三個新介面：</span><span class="sxs-lookup"><span data-stu-id="5a81b-162">These new language features depend on three new interfaces added to .NET Standard 2.1 and implemented in .NET Core 3.0:</span></span>

- <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>
- <xref:System.IAsyncDisposable?displayProperty=nameWithType>

<span data-ttu-id="5a81b-163">這三個介面對大部分的 C# 開發人員來說應該都很熟悉。</span><span class="sxs-lookup"><span data-stu-id="5a81b-163">These three interfaces should be familiar to most C# developers.</span></span> <span data-ttu-id="5a81b-164">它們的運作方式與行為類似其同步對等項：</span><span class="sxs-lookup"><span data-stu-id="5a81b-164">They behave in a manner similar to their synchronous counterparts:</span></span>

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IEnumerator%601?displayProperty=nameWithType>
- <xref:System.IDisposable?displayProperty=nameWithType>

<span data-ttu-id="5a81b-165">一個不熟悉的型別可能是 <xref:System.Threading.Tasks.ValueTask?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="5a81b-165">One type that may be unfamiliar is <xref:System.Threading.Tasks.ValueTask?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5a81b-166">`ValueTask` 結構提供類似的 API 給 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 類別。</span><span class="sxs-lookup"><span data-stu-id="5a81b-166">The `ValueTask` struct provides a similar API to the <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="5a81b-167">`ValueTask` 因為效能原因而用於這些介面。</span><span class="sxs-lookup"><span data-stu-id="5a81b-167">`ValueTask` is used in these interfaces for performance reasons.</span></span>

## <a name="convert-to-async-streams"></a><span data-ttu-id="5a81b-168">轉換為非同步資料流</span><span class="sxs-lookup"><span data-stu-id="5a81b-168">Convert to async streams</span></span>

<span data-ttu-id="5a81b-169">接著，轉換 `runPagedQueryAsync` 方法以產生非同步資料流。</span><span class="sxs-lookup"><span data-stu-id="5a81b-169">Next, convert the `runPagedQueryAsync` method to generate an async stream.</span></span> <span data-ttu-id="5a81b-170">首先，變更f `runPagedQueryAsync` 的簽章以傳回 `IAsyncEnumerable<JToken>`，並從參數清單移除取消權杖與進度物件，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="5a81b-170">First, change the signature of `runPagedQueryAsync` to return an `IAsyncEnumerable<JToken>`, and remove the cancellation token and progress objects from the parameter list as shown in the following code:</span></span>

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetUpdateSignature" :::

<span data-ttu-id="5a81b-171">入門程式碼會在擷取頁面時處理每一頁，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="5a81b-171">The starter code processes each page as the page is retrieved, as shown in the following code:</span></span>

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/start/Program.cs" id="SnippetProcessPage" :::

<span data-ttu-id="5a81b-172">使用下列程式碼取代那三行：</span><span class="sxs-lookup"><span data-stu-id="5a81b-172">Replace those three lines with the following code:</span></span>

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetYieldReturnPage" :::

<span data-ttu-id="5a81b-173">您也可以移除此方法中稍早的 `finalResults` 宣告以及遵循您先前修改之迴圈的 `return` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="5a81b-173">You can also remove the declaration of `finalResults` earlier in this method and the `return` statement that follows the loop you modified.</span></span>

<span data-ttu-id="5a81b-174">您已完成變更以產生非同步資料流。</span><span class="sxs-lookup"><span data-stu-id="5a81b-174">You've finished the changes to generate an async stream.</span></span> <span data-ttu-id="5a81b-175">完成的方法應該類似下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="5a81b-175">The finished method should resemble the following code:</span></span>

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetGenerateAsyncStream" :::

<span data-ttu-id="5a81b-176">接著，您必須變更取用集合以取用非同步資料流的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5a81b-176">Next, you change the code that consumes the collection to consume the async stream.</span></span> <span data-ttu-id="5a81b-177">在 `Main` 中尋找會處理議題集合的下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="5a81b-177">Find the following code in `Main` that processes the collection of issues:</span></span>

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/start/Program.cs" id="SnippetEnumerateOldStyle" :::

<span data-ttu-id="5a81b-178">使用下列 `await foreach` 迴圈取代該程式碼：</span><span class="sxs-lookup"><span data-stu-id="5a81b-178">Replace that code with the following `await foreach` loop:</span></span>

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetEnumerateAsyncStream" :::

<span data-ttu-id="5a81b-179">新介面<xref:System.Collections.Generic.IAsyncEnumerator%601>衍生自<xref:System.IAsyncDisposable>。</span><span class="sxs-lookup"><span data-stu-id="5a81b-179">The new interface <xref:System.Collections.Generic.IAsyncEnumerator%601> derives from <xref:System.IAsyncDisposable>.</span></span> <span data-ttu-id="5a81b-180">這表示當迴圈完成時，先前的迴圈會以非同步方式處置資料流程。</span><span class="sxs-lookup"><span data-stu-id="5a81b-180">That means the preceding loop will asynchronously dispose the stream when the loop finishes.</span></span> <span data-ttu-id="5a81b-181">您可以想像一下迴圈看起來像下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="5a81b-181">You can imagine the loop looks like the following code:</span></span>

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

<span data-ttu-id="5a81b-182">根據預設，資料流程元素會在已捕捉的內容中處理。</span><span class="sxs-lookup"><span data-stu-id="5a81b-182">By default, stream elements are processed in the captured context.</span></span> <span data-ttu-id="5a81b-183">如果您想要停用內容的捕捉，請使用<xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType>擴充方法。</span><span class="sxs-lookup"><span data-stu-id="5a81b-183">If you want to disable capturing of the context, use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> extension method.</span></span> <span data-ttu-id="5a81b-184">如需同步處理內容及取得目前內容的詳細資訊，請參閱有關[使用以工作為基礎的非同步模式](../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)的文章。</span><span class="sxs-lookup"><span data-stu-id="5a81b-184">For more information about synchronization contexts and capturing the current context, see the article on [consuming the Task-based asynchronous pattern](../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span></span>

<span data-ttu-id="5a81b-185">非同步資料流程支援使用與其他`async`方法相同的通訊協定取消。</span><span class="sxs-lookup"><span data-stu-id="5a81b-185">Async streams support cancellation using the same protocol as other `async` methods.</span></span> <span data-ttu-id="5a81b-186">您會修改非同步反覆運算器方法的簽章，如下所示，以支援取消：</span><span class="sxs-lookup"><span data-stu-id="5a81b-186">You would modify the signature for the async iterator method as follows to support cancellation:</span></span>

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetGenerateWithCancellation" :::

<span data-ttu-id="5a81b-187"><xref:System.Runtime.CompilerServices.EnumeratorCancellationAttribute?dipslayProperty=nameWithType>屬性會使編譯器產生的<xref:System.Collections.Generic.IAsyncEnumerator%601>程式碼，讓非同步反覆運算器的主體能夠`GetAsyncEnumerator`看見該 token 做為該引數。</span><span class="sxs-lookup"><span data-stu-id="5a81b-187">The <xref:System.Runtime.CompilerServices.EnumeratorCancellationAttribute?dipslayProperty=nameWithType> attribute causes the compiler to generate code for the <xref:System.Collections.Generic.IAsyncEnumerator%601> that makes the token passed to `GetAsyncEnumerator` visible to the body of the async iterator as that argument.</span></span> <span data-ttu-id="5a81b-188">在`runQueryAsync`中，您可以檢查權杖的狀態，並在要求時取消進一步的工作。</span><span class="sxs-lookup"><span data-stu-id="5a81b-188">Inside `runQueryAsync`, you could examine the state of the token and cancel further work if requested.</span></span>

<span data-ttu-id="5a81b-189">您可以使用另一個擴充<xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.WithCancellation%2A>方法，將解除標記傳遞給非同步資料流程。</span><span class="sxs-lookup"><span data-stu-id="5a81b-189">You use another extension method, <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.WithCancellation%2A>, to pass the cancellation token to the async stream.</span></span> <span data-ttu-id="5a81b-190">您將修改列舉問題的迴圈，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5a81b-190">You would modify the loop enumerating the issues as follows:</span></span>

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetEnumerateWithCancellation" :::

<span data-ttu-id="5a81b-191">您可以從[csharp/教學課程/AsyncStreams](https://github.com/dotnet/docs/tree/master/csharp/tutorials/snippets/generate-consume-asynchronous-streams/finished)資料夾中的[dotnet/](https://github.com/dotnet/docs)檔存放庫取得已完成之教學課程的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5a81b-191">You can get the code for the finished tutorial from the [dotnet/docs](https://github.com/dotnet/docs) repository in the [csharp/tutorials/AsyncStreams](https://github.com/dotnet/docs/tree/master/csharp/tutorials/snippets/generate-consume-asynchronous-streams/finished) folder.</span></span>

## <a name="run-the-finished-application"></a><span data-ttu-id="5a81b-192">執行已完成的應用程式</span><span class="sxs-lookup"><span data-stu-id="5a81b-192">Run the finished application</span></span>

<span data-ttu-id="5a81b-193">再次執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="5a81b-193">Run the application again.</span></span> <span data-ttu-id="5a81b-194">將其行為與入門應用程式的行為進行比較。</span><span class="sxs-lookup"><span data-stu-id="5a81b-194">Contrast its behavior with the behavior of the starter application.</span></span> <span data-ttu-id="5a81b-195">當第一個結果頁面可用時會儘快列舉。</span><span class="sxs-lookup"><span data-stu-id="5a81b-195">The first page of results is enumerated as soon as it's available.</span></span> <span data-ttu-id="5a81b-196">您會發現要求並擷取每個新頁面時會暫停一些時間，燃後快速列舉下一個頁面的結果。</span><span class="sxs-lookup"><span data-stu-id="5a81b-196">There's an observable pause as each new page is requested and retrieved, then the next page's results are quickly enumerated.</span></span> <span data-ttu-id="5a81b-197">不需要 `try` / `catch` 區塊就能處理取消：呼叫者可以停止列舉集合。</span><span class="sxs-lookup"><span data-stu-id="5a81b-197">The `try` / `catch` block isn't needed to handle cancellation: the caller can stop enumerating the collection.</span></span> <span data-ttu-id="5a81b-198">系統會明確回報進度，因為非同步資料流會在下載每個頁面時產生結果。</span><span class="sxs-lookup"><span data-stu-id="5a81b-198">Progress is clearly reported because the async stream generates results as each page is downloaded.</span></span> <span data-ttu-id="5a81b-199">傳回之每個問題的狀態會順暢地包含`await foreach`在迴圈中。</span><span class="sxs-lookup"><span data-stu-id="5a81b-199">The status for each issue returned is seamlessly included in the `await foreach` loop.</span></span> <span data-ttu-id="5a81b-200">您不需要回呼物件來追蹤進度。</span><span class="sxs-lookup"><span data-stu-id="5a81b-200">You don't need a callback object to track progress.</span></span>

<span data-ttu-id="5a81b-201">您可以透過檢查程式碼看到記憶體使用狀況的改進。</span><span class="sxs-lookup"><span data-stu-id="5a81b-201">You can see improvements in memory use by examining the code.</span></span> <span data-ttu-id="5a81b-202">您再也不需要在列舉結果之前配置集合以儲存所有結果。</span><span class="sxs-lookup"><span data-stu-id="5a81b-202">You no longer need to allocate a collection to store all the results before they're enumerated.</span></span> <span data-ttu-id="5a81b-203">呼叫者可以決定如何取用結果，以及是否需要儲存體集合。</span><span class="sxs-lookup"><span data-stu-id="5a81b-203">The caller can determine how to consume the results and if a storage collection is needed.</span></span>

<span data-ttu-id="5a81b-204">執行入門與已完成的應用程式，您將能親自觀察實作之間的差異。</span><span class="sxs-lookup"><span data-stu-id="5a81b-204">Run both the starter and finished applications and you can observe the differences between the implementations for yourself.</span></span> <span data-ttu-id="5a81b-205">完成之後，您可以刪除開始此教學課程時建立的 GitHub 存取權杖。</span><span class="sxs-lookup"><span data-stu-id="5a81b-205">You can delete the GitHub access token you created when you started this tutorial after you've finished.</span></span> <span data-ttu-id="5a81b-206">若攻擊者取得權杖的存取權，他們將能使用您的認證存取 GitHub API。</span><span class="sxs-lookup"><span data-stu-id="5a81b-206">If an attacker gained access to that token, they could access GitHub APIs using your credentials.</span></span>
