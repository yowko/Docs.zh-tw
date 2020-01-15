---
title: 與 System.object 的比較
ms.date: 12/13/2019
description: 描述 Microsoft. Data Sqlite 和 system.string 程式庫之間的一些差異。
ms.openlocfilehash: 076bbc6f746cf9296c96ec73047397a21a3b2558
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900704"
---
# <a name="comparison-to-systemdatasqlite"></a><span data-ttu-id="27f52-103">與 System.object 的比較</span><span class="sxs-lookup"><span data-stu-id="27f52-103">Comparison to System.Data.SQLite</span></span>

<span data-ttu-id="27f52-104">在2005中，Robert Simpson 已建立 ADO.NET 2.0 的 SQLite 提供者。</span><span class="sxs-lookup"><span data-stu-id="27f52-104">In 2005, Robert Simpson created System.Data.SQLite, a SQLite provider for ADO.NET 2.0.</span></span> <span data-ttu-id="27f52-105">在2010中，SQLite 團隊接管了專案的維護和開發。</span><span class="sxs-lookup"><span data-stu-id="27f52-105">In 2010, the SQLite team took over maintenance and development of the project.</span></span> <span data-ttu-id="27f52-106">另外值得一提的是，Mono 小組會將2007中的程式碼分叉為 Mono。</span><span class="sxs-lookup"><span data-stu-id="27f52-106">It's also worth noting that the Mono team forked the code in 2007 as Mono.Data.Sqlite.</span></span> <span data-ttu-id="27f52-107">SQLite 有很長的歷程記錄，並已演變為穩定且功能完整的 ADO.NET 提供者，並使用 Visual Studio 工具完成。</span><span class="sxs-lookup"><span data-stu-id="27f52-107">System.Data.SQLite has a long history and has evolved into a stable and full-featured ADO.NET provider complete with Visual Studio tooling.</span></span> <span data-ttu-id="27f52-108">新版本會繼續將與每個版本 .NET Framework 相容的元件送回2.0 版，甚至 .NET Compact Framework 3.5。</span><span class="sxs-lookup"><span data-stu-id="27f52-108">New releases continue to ship assemblies compatible with every version of .NET Framework back to version 2.0 and even .NET Compact Framework 3.5.</span></span>

<span data-ttu-id="27f52-109">第一版的 .NET Core （于2016發行）是 .NET 的單一、輕量、現代化且跨平臺的執行。</span><span class="sxs-lookup"><span data-stu-id="27f52-109">The first version of .NET Core (released in 2016) was a single, lightweight, modern, and cross-platform implementation of .NET.</span></span> <span data-ttu-id="27f52-110">已刻意移除具有更多新式替代專案的過時 Api 和 Api。</span><span class="sxs-lookup"><span data-stu-id="27f52-110">Obsolete APIs and APIs with more modern alternatives were intentionally removed.</span></span> <span data-ttu-id="27f52-111">ADO.NET 未包含任何資料集 Api （包括 DataTable 和 DataAdapter）。</span><span class="sxs-lookup"><span data-stu-id="27f52-111">ADO.NET didn't include any of the DataSet APIs (including DataTable and DataAdapter).</span></span>

<span data-ttu-id="27f52-112">Entity Framework 小組有點熟悉 System.object 程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="27f52-112">The Entity Framework team was somewhat familiar with the System.Data.SQLite codebase.</span></span> <span data-ttu-id="27f52-113">Brice Lambson 是 EF 小組的成員，先前已協助 SQLite 團隊新增 Entity Framework 版本5和6的支援。</span><span class="sxs-lookup"><span data-stu-id="27f52-113">Brice Lambson, a member of the EF team, had previously helped the SQLite team add support for Entity Framework versions 5 and 6.</span></span> <span data-ttu-id="27f52-114">Brice 也會在規劃 .NET Core 的同時，透過自己的 SQLite ADO.NET 提供者執行進行實驗。</span><span class="sxs-lookup"><span data-stu-id="27f52-114">Brice was also experimenting with his own implementation of a SQLite ADO.NET provider around the same time that .NET Core was being planned.</span></span> <span data-ttu-id="27f52-115">經過一段時間的討論之後，Entity Framework 小組決定根據 Brice 的原型建立 Microsoft 資料 Sqlite。</span><span class="sxs-lookup"><span data-stu-id="27f52-115">After a long discussion, the Entity Framework team decided to create Microsoft.Data.Sqlite based on Brice's prototype.</span></span> <span data-ttu-id="27f52-116">這可讓他們建立新的輕量和現代化的執行，以配合 .NET Core 的目標。</span><span class="sxs-lookup"><span data-stu-id="27f52-116">This would allow them to create a new lightweight and modern implementation that would align with the goals of .NET Core.</span></span>

<span data-ttu-id="27f52-117">做為我們的重要性，我們的程式碼如下所示：在 system.string 和. sqlite 中建立[使用者定義函數](user-defined-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="27f52-117">As an example of what we mean by more modern, here is code to create a [user-defined function](user-defined-functions.md) in both System.Data.SQLite and Microsoft.Data.Sqlite.</span></span>

```csharp
// System.Data.SQLite
connection.BindFunction(
    new SQLiteFunctionAttribute("ceiling", 1, FunctionType.Scalar),
    (Func<object[], object>)((object[] args) => Math.Ceiling((double)((object[])args[1])[0])),
    null);

// Microsoft.Data.Sqlite
connection.CreateFunction(
    "ceiling",
    (double arg) => Math.Ceiling(arg));
```

<span data-ttu-id="27f52-118">在2017中，.NET Core 2.0 在策略方面有變更。</span><span class="sxs-lookup"><span data-stu-id="27f52-118">In 2017, .NET Core 2.0 experienced a change in strategy.</span></span> <span data-ttu-id="27f52-119">它決定與 .NET Framework 的相容性對於 .NET Core 的成功非常重要。</span><span class="sxs-lookup"><span data-stu-id="27f52-119">It was decided that compatibility with .NET Framework was vital to the success of .NET Core.</span></span> <span data-ttu-id="27f52-120">許多已移除的 Api，包括資料集 Api，都已新增回來。</span><span class="sxs-lookup"><span data-stu-id="27f52-120">Many of the removed APIs, including the DataSet APIs, were added back.</span></span> <span data-ttu-id="27f52-121">與其他許多人一樣，這會解除封鎖的 System.object，讓它也可以移植到 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="27f52-121">Like it did for many others, this unblocked System.Data.SQLite allowing it to also be ported to .NET Core.</span></span> <span data-ttu-id="27f52-122">但是，Microsoft 的原始目標是輕量且現代化的資料，不過仍會保持不變。</span><span class="sxs-lookup"><span data-stu-id="27f52-122">The original goal of Microsoft.Data.Sqlite to be lightweight and modern, however, still remains.</span></span> <span data-ttu-id="27f52-123">如需 ADO.NET 不是由 Microsoft 所實行之 Api 的詳細資料，請參閱[ADO.NET 限制](adonet-limitations.md)。</span><span class="sxs-lookup"><span data-stu-id="27f52-123">See [ADO.NET limitations](adonet-limitations.md) for details about ADO.NET APIs not implemented by Microsoft.Data.Sqlite.</span></span>

<span data-ttu-id="27f52-124">將新功能新增至 [Sqlite] 時，會將 System.object 的設計納入考慮。</span><span class="sxs-lookup"><span data-stu-id="27f52-124">When new features are added to Microsoft.Data.Sqlite, the design of System.Data.SQLite is taken into account.</span></span> <span data-ttu-id="27f52-125">我們盡可能嘗試將兩者之間的變更降至最低，以減輕兩者之間的轉換。</span><span class="sxs-lookup"><span data-stu-id="27f52-125">We try, when possible, to minimize changes between the two to ease transitioning between them.</span></span>

## <a name="data-types"></a><span data-ttu-id="27f52-126">資料類型</span><span class="sxs-lookup"><span data-stu-id="27f52-126">Data types</span></span>

<span data-ttu-id="27f52-127">Microsoft. Sqlite 和 System.object 的最大差異在於資料類型的處理方式。</span><span class="sxs-lookup"><span data-stu-id="27f52-127">The biggest difference between Microsoft.Data.Sqlite and System.Data.SQLite is how data types are handled.</span></span> <span data-ttu-id="27f52-128">如[資料類型](types.md)中所述，Microsoft. Sqlite 不會嘗試隱藏 Sqlite 的基礎 quirkiness，這可讓任何任一字元串指定為數據行類型，而且只有四種基本類型：整數、實數、文字和 BLOB。</span><span class="sxs-lookup"><span data-stu-id="27f52-128">As described in [Data types](types.md), Microsoft.Data.Sqlite doesn't try to hide the underlying quirkiness of SQLite, which allows any arbitrary string to be specified as the column type, and only has four primitive types: INTEGER, REAL, TEXT, and BLOB.</span></span>

<span data-ttu-id="27f52-129">SQLite 會將其他的語義套用至資料行類型，將它們直接對應至 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="27f52-129">System.Data.SQLite applies additional semantics to column types mapping them directly to .NET types.</span></span> <span data-ttu-id="27f52-130">這讓提供者具有更強型別風格，但有一些粗略的邊緣。</span><span class="sxs-lookup"><span data-stu-id="27f52-130">This gives the provider a more strongly typed feel, but it has some rough edges.</span></span> <span data-ttu-id="27f52-131">例如，他們必須引進新的 SQL 語句（類型），以在 SELECT 語句中指定運算式的資料行類型。</span><span class="sxs-lookup"><span data-stu-id="27f52-131">For example, they had to introduce a new SQL statement (TYPES) to specify the column types of expressions in SELECT statements.</span></span>

## <a name="connection-strings"></a><span data-ttu-id="27f52-132">連接字串</span><span class="sxs-lookup"><span data-stu-id="27f52-132">Connection strings</span></span>

<span data-ttu-id="27f52-133">Sqlite 的[連接字串](connection-strings.md)關鍵字較少。</span><span class="sxs-lookup"><span data-stu-id="27f52-133">Microsoft.Data.Sqlite has a lot fewer [connection string](connection-strings.md) keywords.</span></span> <span data-ttu-id="27f52-134">下表顯示可以改為使用的替代方案。</span><span class="sxs-lookup"><span data-stu-id="27f52-134">The following table shows alternatives that can be used instead.</span></span>

| <span data-ttu-id="27f52-135">關鍵字</span><span class="sxs-lookup"><span data-stu-id="27f52-135">Keyword</span></span>          | <span data-ttu-id="27f52-136">選項</span><span class="sxs-lookup"><span data-stu-id="27f52-136">Alternative</span></span>                                         |
| ---------------- | --------------------------------------------------- |
| <span data-ttu-id="27f52-137">快取大小</span><span class="sxs-lookup"><span data-stu-id="27f52-137">Cache Size</span></span>       | <span data-ttu-id="27f52-138">傳送 `PRAGMA cache_size = <pages>`</span><span class="sxs-lookup"><span data-stu-id="27f52-138">Send `PRAGMA cache_size = <pages>`</span></span>                  |
| <span data-ttu-id="27f52-139">預設逾時</span><span class="sxs-lookup"><span data-stu-id="27f52-139">Default Timeout</span></span>  | <span data-ttu-id="27f52-140">在 SqliteConnection 上使用 DefaultTimeout 屬性</span><span class="sxs-lookup"><span data-stu-id="27f52-140">Use the DefaultTimeout property on SqliteConnection</span></span> |
| <span data-ttu-id="27f52-141">FailIfMissing</span><span class="sxs-lookup"><span data-stu-id="27f52-141">FailIfMissing</span></span>    | <span data-ttu-id="27f52-142">使用`Mode=ReadWrite`</span><span class="sxs-lookup"><span data-stu-id="27f52-142">Use `Mode=ReadWrite`</span></span>                                |
| <span data-ttu-id="27f52-143">FullUri</span><span class="sxs-lookup"><span data-stu-id="27f52-143">FullUri</span></span>          | <span data-ttu-id="27f52-144">使用資料來源關鍵字</span><span class="sxs-lookup"><span data-stu-id="27f52-144">Use the Data Source keyword</span></span>                         |
| <span data-ttu-id="27f52-145">記錄模式</span><span class="sxs-lookup"><span data-stu-id="27f52-145">Journal Mode</span></span>     | <span data-ttu-id="27f52-146">傳送 `PRAGMA journal_mode = <mode>`</span><span class="sxs-lookup"><span data-stu-id="27f52-146">Send `PRAGMA journal_mode = <mode>`</span></span>                 |
| <span data-ttu-id="27f52-147">舊版格式</span><span class="sxs-lookup"><span data-stu-id="27f52-147">Legacy Format</span></span>    | <span data-ttu-id="27f52-148">傳送 `PRAGMA legacy_file_format = 1`</span><span class="sxs-lookup"><span data-stu-id="27f52-148">Send `PRAGMA legacy_file_format = 1`</span></span>                |
| <span data-ttu-id="27f52-149">最大頁面計數</span><span class="sxs-lookup"><span data-stu-id="27f52-149">Max Page Count</span></span>   | <span data-ttu-id="27f52-150">傳送 `PRAGMA max_page_count = <pages>`</span><span class="sxs-lookup"><span data-stu-id="27f52-150">Send `PRAGMA max_page_count = <pages>`</span></span>              |
| <span data-ttu-id="27f52-151">頁面大小</span><span class="sxs-lookup"><span data-stu-id="27f52-151">Page Size</span></span>        | <span data-ttu-id="27f52-152">傳送 `PRAGMA page_size = <bytes>`</span><span class="sxs-lookup"><span data-stu-id="27f52-152">Send `PRAGMA page_size = <bytes>`</span></span>                   |
| <span data-ttu-id="27f52-153">唯讀</span><span class="sxs-lookup"><span data-stu-id="27f52-153">Read Only</span></span>        | <span data-ttu-id="27f52-154">使用`Mode=ReadOnly`</span><span class="sxs-lookup"><span data-stu-id="27f52-154">Use `Mode=ReadOnly`</span></span>                                 |
| <span data-ttu-id="27f52-155">同步</span><span class="sxs-lookup"><span data-stu-id="27f52-155">Synchronous</span></span>      | <span data-ttu-id="27f52-156">傳送 `PRAGMA synchronous = <mode>`</span><span class="sxs-lookup"><span data-stu-id="27f52-156">Send `PRAGMA synchronous = <mode>`</span></span>                  |
| <span data-ttu-id="27f52-157">URI</span><span class="sxs-lookup"><span data-stu-id="27f52-157">Uri</span></span>              | <span data-ttu-id="27f52-158">使用資料來源關鍵字</span><span class="sxs-lookup"><span data-stu-id="27f52-158">Use the Data Source keyword</span></span>                         |
| <span data-ttu-id="27f52-159">UseUTF16Encoding</span><span class="sxs-lookup"><span data-stu-id="27f52-159">UseUTF16Encoding</span></span> | <span data-ttu-id="27f52-160">傳送 `PRAGMA encoding = 'UTF-16'`</span><span class="sxs-lookup"><span data-stu-id="27f52-160">Send `PRAGMA encoding = 'UTF-16'`</span></span>                   |

## <a name="authorization"></a><span data-ttu-id="27f52-161">授權</span><span class="sxs-lookup"><span data-stu-id="27f52-161">Authorization</span></span>

<span data-ttu-id="27f52-162">Microsoft. Sqlite 沒有任何 API 公開 SQLite 的授權回呼。</span><span class="sxs-lookup"><span data-stu-id="27f52-162">Microsoft.Data.Sqlite doesn't have any API exposing SQLite's authorization callback.</span></span> <span data-ttu-id="27f52-163">使用 [問題[#13835](https://github.com/dotnet/efcore/issues/13835) ] 來提供有關此功能的意見反應。</span><span class="sxs-lookup"><span data-stu-id="27f52-163">Use issue [#13835](https://github.com/dotnet/efcore/issues/13835) to provide feedback about this feature.</span></span>

## <a name="data-change-notifications"></a><span data-ttu-id="27f52-164">資料變更通知</span><span class="sxs-lookup"><span data-stu-id="27f52-164">Data change notifications</span></span>

<span data-ttu-id="27f52-165">Microsoft. Sqlite 沒有任何 API 公開 SQLite 的資料變更通知。</span><span class="sxs-lookup"><span data-stu-id="27f52-165">Microsoft.Data.Sqlite doesn't have any API exposing SQLite's data change notifications.</span></span> <span data-ttu-id="27f52-166">使用 [問題[#13827](https://github.com/dotnet/efcore/issues/13827) ] 來提供有關此功能的意見反應。</span><span class="sxs-lookup"><span data-stu-id="27f52-166">Use issue [#13827](https://github.com/dotnet/efcore/issues/13827) to provide feedback about this feature.</span></span>

## <a name="virtual-table-modules"></a><span data-ttu-id="27f52-167">虛擬資料表模組</span><span class="sxs-lookup"><span data-stu-id="27f52-167">Virtual table modules</span></span>

<span data-ttu-id="27f52-168">在建立虛擬資料表模組時，Sqlite 沒有任何 API。</span><span class="sxs-lookup"><span data-stu-id="27f52-168">Microsoft.Data.Sqlite doesn't have any API for creating virtual table modules.</span></span> <span data-ttu-id="27f52-169">使用 [問題[#13823](https://github.com/dotnet/efcore/issues/13823) ] 來提供有關此功能的意見反應。</span><span class="sxs-lookup"><span data-stu-id="27f52-169">Use issue [#13823](https://github.com/dotnet/efcore/issues/13823) to provide feedback about this feature.</span></span>

## <a name="see-also"></a><span data-ttu-id="27f52-170">請參閱</span><span class="sxs-lookup"><span data-stu-id="27f52-170">See also</span></span>

* [<span data-ttu-id="27f52-171">資料類型</span><span class="sxs-lookup"><span data-stu-id="27f52-171">Data types</span></span>](types.md)
* [<span data-ttu-id="27f52-172">連接字串</span><span class="sxs-lookup"><span data-stu-id="27f52-172">Connection strings</span></span>](connection-strings.md)
* [<span data-ttu-id="27f52-173">加密</span><span class="sxs-lookup"><span data-stu-id="27f52-173">Encryption</span></span>](encryption.md)
* [<span data-ttu-id="27f52-174">ADO.NET 限制</span><span class="sxs-lookup"><span data-stu-id="27f52-174">ADO.NET limitations</span></span>](adonet-limitations.md)
* [<span data-ttu-id="27f52-175">Dapper 限制</span><span class="sxs-lookup"><span data-stu-id="27f52-175">Dapper limitations</span></span>](dapper-limitations.md)
