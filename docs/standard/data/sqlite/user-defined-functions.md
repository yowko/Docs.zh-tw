---
title: 使用者定義函式
ms.date: 12/13/2019
description: 瞭解如何建立使用者定義的純量和彙總函式。
ms.openlocfilehash: 9ee3fbac73215353c8dc82199203b0d25e580cdb
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447171"
---
# <a name="user-defined-functions"></a><span data-ttu-id="0725a-103">使用者定義函式</span><span class="sxs-lookup"><span data-stu-id="0725a-103">User-defined functions</span></span>

<span data-ttu-id="0725a-104">大部分的資料庫都具有 SQL 的程式性方言，您可以用它來定義自己的函式。</span><span class="sxs-lookup"><span data-stu-id="0725a-104">Most databases have a procedural dialect of SQL that you can use to define your own functions.</span></span> <span data-ttu-id="0725a-105">不過，SQLite 會使用您的應用程式在同進程中執行。</span><span class="sxs-lookup"><span data-stu-id="0725a-105">SQLite however, runs in-process with your app.</span></span> <span data-ttu-id="0725a-106">您不需要學習新的 SQL 方言，只要使用應用程式的程式設計語言就可以了。</span><span class="sxs-lookup"><span data-stu-id="0725a-106">Instead of having to learn a new dialect of SQL, you can just use the programming language of your app.</span></span>

## <a name="scalar-functions"></a><span data-ttu-id="0725a-107">純量函式</span><span class="sxs-lookup"><span data-stu-id="0725a-107">Scalar functions</span></span>

<span data-ttu-id="0725a-108">純量函數會針對查詢中的每個資料列傳回單一純量值。</span><span class="sxs-lookup"><span data-stu-id="0725a-108">Scalar functions return a single, scalar value for each row in a query.</span></span> <span data-ttu-id="0725a-109">定義新的純量函數，並使用 <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateFunction%2A>覆寫內建的函式。</span><span class="sxs-lookup"><span data-stu-id="0725a-109">Define new scalar functions and override the built-in ones using <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateFunction%2A>.</span></span>

<span data-ttu-id="0725a-110">如需 `func` 引數的支援參數和傳回類型清單，請參閱[資料類型](types.md)。</span><span class="sxs-lookup"><span data-stu-id="0725a-110">See [Data types](types.md) for a list of supported parameter and return types for the `func` argument.</span></span>

<span data-ttu-id="0725a-111">指定 `state` 引數會將該值傳遞至函式的每個調用。</span><span class="sxs-lookup"><span data-stu-id="0725a-111">Specifying the `state` argument will pass that value into every invocation of the function.</span></span> <span data-ttu-id="0725a-112">使用此來避免結束。</span><span class="sxs-lookup"><span data-stu-id="0725a-112">Use this to avoid closures.</span></span>

<span data-ttu-id="0725a-113">如果您的函式具有決定性，可讓 SQLite 在編譯查詢時使用額外的優化，請指定 `isDeterministic`。</span><span class="sxs-lookup"><span data-stu-id="0725a-113">Specify `isDeterministic` if your function is deterministic to allow SQLite to use additional optimizations when compiling queries.</span></span>

<span data-ttu-id="0725a-114">下列範例顯示如何新增純量函數來計算圓柱的半徑。</span><span class="sxs-lookup"><span data-stu-id="0725a-114">The following example shows how to add a scalar function to calculate the radius of a cylinder.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ScalarFunctionSample/Program.cs?name=snippet_CreateFunction)]

## <a name="operators"></a><span data-ttu-id="0725a-115">運算子</span><span class="sxs-lookup"><span data-stu-id="0725a-115">Operators</span></span>

<span data-ttu-id="0725a-116">下列 SQLite 運算子會由對應的純量函式來執行。</span><span class="sxs-lookup"><span data-stu-id="0725a-116">The following SQLite operators are implemented by corresponding scalar functions.</span></span> <span data-ttu-id="0725a-117">在您的應用程式中定義這些純量函數將會覆寫這些運算子的行為。</span><span class="sxs-lookup"><span data-stu-id="0725a-117">Defining these scalar functions in your app will override the behavior of these operators.</span></span>

| <span data-ttu-id="0725a-118">運算子</span><span class="sxs-lookup"><span data-stu-id="0725a-118">Operator</span></span>          | <span data-ttu-id="0725a-119">函數</span><span class="sxs-lookup"><span data-stu-id="0725a-119">Function</span></span>      |
| ----------------- | ------------- |
| <span data-ttu-id="0725a-120">X GLOB Y</span><span class="sxs-lookup"><span data-stu-id="0725a-120">X GLOB Y</span></span>          | <span data-ttu-id="0725a-121">glob （Y，X）</span><span class="sxs-lookup"><span data-stu-id="0725a-121">glob(Y, X)</span></span>    |
| <span data-ttu-id="0725a-122">X，例如 Y</span><span class="sxs-lookup"><span data-stu-id="0725a-122">X LIKE Y</span></span>          | <span data-ttu-id="0725a-123">like （Y，X）</span><span class="sxs-lookup"><span data-stu-id="0725a-123">like(Y, X)</span></span>    |
| <span data-ttu-id="0725a-124">X，如同 Y ESCAPE Z</span><span class="sxs-lookup"><span data-stu-id="0725a-124">X LIKE Y ESCAPE Z</span></span> | <span data-ttu-id="0725a-125">like （Y，X，Z）</span><span class="sxs-lookup"><span data-stu-id="0725a-125">like(Y, X, Z)</span></span> |
| <span data-ttu-id="0725a-126">X 符合 Y</span><span class="sxs-lookup"><span data-stu-id="0725a-126">X MATCH Y</span></span>         | <span data-ttu-id="0725a-127">match （Y，X）</span><span class="sxs-lookup"><span data-stu-id="0725a-127">match(Y, X)</span></span>   |
| <span data-ttu-id="0725a-128">X REGEXP Y</span><span class="sxs-lookup"><span data-stu-id="0725a-128">X REGEXP Y</span></span>        | <span data-ttu-id="0725a-129">RegExp （Y，X）</span><span class="sxs-lookup"><span data-stu-id="0725a-129">regexp(Y, X)</span></span>  |

<span data-ttu-id="0725a-130">下列範例顯示如何定義 RegExp 函式，以啟用其對應的運算子。</span><span class="sxs-lookup"><span data-stu-id="0725a-130">The following example shows how to define the regexp function to enable its corresponding operator.</span></span> <span data-ttu-id="0725a-131">SQLite 不包含 RegExp 函數的預設執行。</span><span class="sxs-lookup"><span data-stu-id="0725a-131">SQLite doesn't include a default implementation of the regexp function.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/RegularExpressionSample/Program.cs?name=snippet_Regex)]

## <a name="aggregate-functions"></a><span data-ttu-id="0725a-132">彙總函式</span><span class="sxs-lookup"><span data-stu-id="0725a-132">Aggregate functions</span></span>

<span data-ttu-id="0725a-133">彙總函式會針對查詢中的所有資料列傳回單一匯總的值。</span><span class="sxs-lookup"><span data-stu-id="0725a-133">Aggregate functions return a single, aggregated value for all the rows in a query.</span></span> <span data-ttu-id="0725a-134">使用 <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateAggregate%2A>定義和覆寫彙總函式。</span><span class="sxs-lookup"><span data-stu-id="0725a-134">Define and override aggregate functions using <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateAggregate%2A>.</span></span>

<span data-ttu-id="0725a-135">`seed` 引數會指定內容的初始狀態。</span><span class="sxs-lookup"><span data-stu-id="0725a-135">The `seed` argument specifies the initial state of the context.</span></span> <span data-ttu-id="0725a-136">請使用此來避免同時結束。</span><span class="sxs-lookup"><span data-stu-id="0725a-136">Use this to avoid closures also.</span></span>

<span data-ttu-id="0725a-137">每個資料列會叫用一次 `func` 引數。</span><span class="sxs-lookup"><span data-stu-id="0725a-137">The `func` argument is invoked once per row.</span></span> <span data-ttu-id="0725a-138">使用內容來累積最終的結果。</span><span class="sxs-lookup"><span data-stu-id="0725a-138">Use the context to accumulate a final result.</span></span> <span data-ttu-id="0725a-139">傳回內容。</span><span class="sxs-lookup"><span data-stu-id="0725a-139">Return the context.</span></span> <span data-ttu-id="0725a-140">此模式可讓內容是實值型別或不可變的。</span><span class="sxs-lookup"><span data-stu-id="0725a-140">This pattern allows the context to be a value type or immutable.</span></span>

<span data-ttu-id="0725a-141">如果未指定 `resultSelector`，則會使用內容的最終狀態做為結果。</span><span class="sxs-lookup"><span data-stu-id="0725a-141">If no `resultSelector` is specified, the final state of the context is used as the result.</span></span> <span data-ttu-id="0725a-142">這可簡化函式的定義，例如 sum 和 count，這只需要每個資料列遞增一個數位，然後傳回它。</span><span class="sxs-lookup"><span data-stu-id="0725a-142">This can simplify the definition of functions like sum and count that only need to increment a number each row and return it.</span></span>

<span data-ttu-id="0725a-143">指定 `resultSelector`，以便在逐一查看所有資料列之後，計算內容的最終結果。</span><span class="sxs-lookup"><span data-stu-id="0725a-143">Specify `resultSelector` to calculate the final result from the context after iterating through all the rows.</span></span>

<span data-ttu-id="0725a-144">如需 `resultSelector`的 `func` 引數和傳回類型的支援參數類型清單，請參閱[資料類型](types.md)。</span><span class="sxs-lookup"><span data-stu-id="0725a-144">See [Data types](types.md) for a list of supported parameter types for the `func` argument and return types for `resultSelector`.</span></span>

<span data-ttu-id="0725a-145">如果您的函式具決定性，請指定 `isDeterministic`，以允許 SQLite 在編譯查詢時使用額外的優化。</span><span class="sxs-lookup"><span data-stu-id="0725a-145">If your function is deterministic, specify `isDeterministic` to allow SQLite to use additional optimizations when compiling queries.</span></span>

<span data-ttu-id="0725a-146">下列範例會定義彙總函式來計算資料行的標準差。</span><span class="sxs-lookup"><span data-stu-id="0725a-146">The following example defines an aggregate function to calculate the standard deviation of a column.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/AggregateFunctionSample/Program.cs?name=snippet_CreateAggregate)]

## <a name="errors"></a><span data-ttu-id="0725a-147">錯誤</span><span class="sxs-lookup"><span data-stu-id="0725a-147">Errors</span></span>

<span data-ttu-id="0725a-148">如果使用者定義的函式擲回例外狀況，則訊息會傳回 SQLite。</span><span class="sxs-lookup"><span data-stu-id="0725a-148">If a user-defined function throws an exception, the message is returned to SQLite.</span></span> <span data-ttu-id="0725a-149">接著，SQLite 會引發錯誤和 SqliteException。 Sqlite 會擲回一個。</span><span class="sxs-lookup"><span data-stu-id="0725a-149">SQLite will then raise an error and Microsoft.Data.Sqlite will throw a SqliteException.</span></span> <span data-ttu-id="0725a-150">如需詳細資訊，請參閱[資料庫錯誤](database-errors.md)。</span><span class="sxs-lookup"><span data-stu-id="0725a-150">For more information, see [Database errors](database-errors.md).</span></span>

<span data-ttu-id="0725a-151">根據預設，錯誤 SQLite 錯誤碼將會 SQLITE_ERROR （或1）。</span><span class="sxs-lookup"><span data-stu-id="0725a-151">By default, the error SQLite error code will be SQLITE_ERROR (or 1).</span></span> <span data-ttu-id="0725a-152">不過，您可以在函式中擲回 <xref:Microsoft.Data.Sqlite.SqliteException>，並指定所需的 <xref:Microsoft.Data.Sqlite.SqliteException.SqliteErrorCode> 來變更它。</span><span class="sxs-lookup"><span data-stu-id="0725a-152">You can, however, change it by throwing a <xref:Microsoft.Data.Sqlite.SqliteException> in your function with the desired <xref:Microsoft.Data.Sqlite.SqliteException.SqliteErrorCode> specified.</span></span>

## <a name="debugging"></a><span data-ttu-id="0725a-153">偵錯</span><span class="sxs-lookup"><span data-stu-id="0725a-153">Debugging</span></span>

<span data-ttu-id="0725a-154">SQLite 會直接呼叫您的實作為。</span><span class="sxs-lookup"><span data-stu-id="0725a-154">SQLite calls your implementation directly.</span></span> <span data-ttu-id="0725a-155">這可讓您新增在 SQLite 正在評估查詢時觸發的中斷點。</span><span class="sxs-lookup"><span data-stu-id="0725a-155">This lets you add breakpoints that trigger while SQLite is evaluating queries.</span></span> <span data-ttu-id="0725a-156">完整的 .NET 偵錯工具體驗可協助您建立使用者定義函數。</span><span class="sxs-lookup"><span data-stu-id="0725a-156">The full .NET debugging experience is available to help you create your user-defined functions.</span></span>

## <a name="see-also"></a><span data-ttu-id="0725a-157">請參閱</span><span class="sxs-lookup"><span data-stu-id="0725a-157">See also</span></span>

* [<span data-ttu-id="0725a-158">資料類型</span><span class="sxs-lookup"><span data-stu-id="0725a-158">Data types</span></span>](types.md)
* [<span data-ttu-id="0725a-159">SQLite 核心函式</span><span class="sxs-lookup"><span data-stu-id="0725a-159">SQLite Core functions</span></span>](https://www.sqlite.org/lang_corefunc.html)
* [<span data-ttu-id="0725a-160">SQLite 彙總函式</span><span class="sxs-lookup"><span data-stu-id="0725a-160">SQLite Aggregate Functions</span></span>](https://www.sqlite.org/lang_aggfunc.html)
