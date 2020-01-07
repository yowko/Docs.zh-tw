---
title: Dapper 限制
ms.date: 12/13/2019
description: 說明您在使用 Dapper 時會遇到的一些限制。
ms.openlocfilehash: 90c7fb24f068d663081390bdba9b1b222b4be56e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447276"
---
# <a name="dapper-limitations"></a><span data-ttu-id="f45f0-103">Dapper 限制</span><span class="sxs-lookup"><span data-stu-id="f45f0-103">Dapper limitations</span></span>

<span data-ttu-id="f45f0-104">當您使用[Dapper](https://stackexchange.github.io/Dapper/)時，您應該注意一些限制。</span><span class="sxs-lookup"><span data-stu-id="f45f0-104">There are a few limitations you should be aware of when using Microsoft.Data.Sqlite with [Dapper](https://stackexchange.github.io/Dapper/).</span></span>

## <a name="parameters"></a><span data-ttu-id="f45f0-105">參數</span><span class="sxs-lookup"><span data-stu-id="f45f0-105">Parameters</span></span>

<span data-ttu-id="f45f0-106">SQLite 參數名稱會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="f45f0-106">SQLite parameter names are case-sensitive.</span></span> <span data-ttu-id="f45f0-107">請確定 SQL 中所使用的參數名稱符合匿名物件屬性的大小寫。</span><span class="sxs-lookup"><span data-stu-id="f45f0-107">Ensure that the parameter names used in SQL match the case of the anonymous object's properties.</span></span> <span data-ttu-id="f45f0-108">問題[#18861](https://github.com/aspnet/EntityFrameworkCore/issues/18861)會改善這項體驗。</span><span class="sxs-lookup"><span data-stu-id="f45f0-108">Issue [#18861](https://github.com/aspnet/EntityFrameworkCore/issues/18861) would improve this experience.</span></span>

<span data-ttu-id="f45f0-109">Dapper 也預期參數會使用 `@` 前置詞。</span><span class="sxs-lookup"><span data-stu-id="f45f0-109">Dapper also expects parameters to use the `@` prefix.</span></span> <span data-ttu-id="f45f0-110">其他首碼將無法使用。</span><span class="sxs-lookup"><span data-stu-id="f45f0-110">Other prefixes won't work.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_Parameter)]

## <a name="data-types"></a><span data-ttu-id="f45f0-111">資料類型</span><span class="sxs-lookup"><span data-stu-id="f45f0-111">Data types</span></span>

<span data-ttu-id="f45f0-112">Dapper 會使用 SqliteDataReader 索引子來讀取值。</span><span class="sxs-lookup"><span data-stu-id="f45f0-112">Dapper reads values using the SqliteDataReader indexer.</span></span> <span data-ttu-id="f45f0-113">此索引子的傳回型別為 object，這表示它只會傳回 long、double、string 或 byte [] 值。</span><span class="sxs-lookup"><span data-stu-id="f45f0-113">The return type of this indexer is object, which means it will only ever return long, double, string, or byte[] values.</span></span> <span data-ttu-id="f45f0-114">如需詳細資訊，請參閱[資料類型](types.md)。</span><span class="sxs-lookup"><span data-stu-id="f45f0-114">For more information, see [Data types](types.md).</span></span> <span data-ttu-id="f45f0-115">Dapper 會處理這些和其他基本類型之間的大部分轉換。</span><span class="sxs-lookup"><span data-stu-id="f45f0-115">Dapper handles most conversions between these and other primitive types.</span></span> <span data-ttu-id="f45f0-116">可惜的是，它不會處理 `DateTimeOffset`、`Guid`或 `TimeSpan`。</span><span class="sxs-lookup"><span data-stu-id="f45f0-116">Unfortunately, it doesn't handle `DateTimeOffset`, `Guid`, or `TimeSpan`.</span></span> <span data-ttu-id="f45f0-117">如果您想要在結果中使用這些類型，請建立類型處理常式。</span><span class="sxs-lookup"><span data-stu-id="f45f0-117">Create type handlers if you want to use these types in your results.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_TypeHandlers)]

<span data-ttu-id="f45f0-118">在查詢之前，請不要忘記加入型別處理程式。</span><span class="sxs-lookup"><span data-stu-id="f45f0-118">Don't forget to add the type handlers before querying.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_AddTypeHandlers)]

## <a name="see-also"></a><span data-ttu-id="f45f0-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="f45f0-119">See also</span></span>

* [<span data-ttu-id="f45f0-120">資料類型</span><span class="sxs-lookup"><span data-stu-id="f45f0-120">Data types</span></span>](types.md)
* [<span data-ttu-id="f45f0-121">非同步限制</span><span class="sxs-lookup"><span data-stu-id="f45f0-121">Async limitations</span></span>](async.md)
