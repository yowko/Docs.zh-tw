---
title: ADO.NET 限制
ms.date: 12/13/2019
description: 說明您可能會遇到的一些 ADO.NET 限制。
ms.openlocfilehash: 8664b73071fc859ed30080f549b05e7d6ed020f4
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901257"
---
# <a name="adonet-limitations"></a><span data-ttu-id="28e3a-103">ADO.NET 限制</span><span class="sxs-lookup"><span data-stu-id="28e3a-103">ADO.NET limitations</span></span>

<span data-ttu-id="28e3a-104">ADO.NET 提供許多抽象概念的執行，但有一些限制。</span><span class="sxs-lookup"><span data-stu-id="28e3a-104">Microsoft.Data.Sqlite provides implementations of many of the ADO.NET abstractions, but there are some limitations.</span></span>

## <a name="database-schema-information"></a><span data-ttu-id="28e3a-105">資料庫架構資訊</span><span class="sxs-lookup"><span data-stu-id="28e3a-105">Database schema information</span></span>

<span data-ttu-id="28e3a-106">您可以使用<xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A>方法來取得有關查詢結果的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="28e3a-106">Metadata about query results is available using the <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> method.</span></span>

<span data-ttu-id="28e3a-107">`DbConnection.GetSchema()`未執行。</span><span class="sxs-lookup"><span data-stu-id="28e3a-107">`DbConnection.GetSchema()` isn't implemented.</span></span> <span data-ttu-id="28e3a-108">此 API 未妥善定義，因此建議您直接使用標準 SQLite Api （例如[sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema)資料表和[table_info](https://www.sqlite.org/pragma.html#pragma_table_info) PRAGMA）來抓取資料庫中繼資料。</span><span class="sxs-lookup"><span data-stu-id="28e3a-108">This API isn't well-defined, so we recommend retrieving database metadata directly using standard SQLite APIs like the [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) table and the [table_info](https://www.sqlite.org/pragma.html#pragma_table_info) PRAGMA.</span></span>

<span data-ttu-id="28e3a-109">如需詳細資訊，請參閱[中繼資料](metadata.md)。</span><span class="sxs-lookup"><span data-stu-id="28e3a-109">For more information, see [Metadata](metadata.md).</span></span>

## <a name="systemtransactions"></a><span data-ttu-id="28e3a-110">System.Transactions</span><span class="sxs-lookup"><span data-stu-id="28e3a-110">System.Transactions</span></span>

<span data-ttu-id="28e3a-111">Microsoft. Sqlite 尚未支援 System.object。</span><span class="sxs-lookup"><span data-stu-id="28e3a-111">Microsoft.Data.Sqlite doesn't yet support System.Transactions.</span></span> <span data-ttu-id="28e3a-112">請改用 ADO.NET 的交易。</span><span class="sxs-lookup"><span data-stu-id="28e3a-112">Use ADO.NET transactions instead.</span></span> <span data-ttu-id="28e3a-113">如需詳細資訊，請參閱[交易](transactions.md)。</span><span class="sxs-lookup"><span data-stu-id="28e3a-113">For more information, see [Transactions](transactions.md).</span></span>

<span data-ttu-id="28e3a-114">提供有關缺少系統支援的意見反應[#13825](https://github.com/dotnet/efcore/issues/13825)的問題。</span><span class="sxs-lookup"><span data-stu-id="28e3a-114">Provide feedback about the lack of support for System.Transactions on issue [#13825](https://github.com/dotnet/efcore/issues/13825).</span></span>

## <a name="data-adapters"></a><span data-ttu-id="28e3a-115">資料介面卡</span><span class="sxs-lookup"><span data-stu-id="28e3a-115">Data adapters</span></span>

<span data-ttu-id="28e3a-116">`DbDataAdapter`尚未由 Microsoft. Sqlite 執行。</span><span class="sxs-lookup"><span data-stu-id="28e3a-116">`DbDataAdapter` isn't yet implemented by Microsoft.Data.Sqlite.</span></span> <span data-ttu-id="28e3a-117">這表示您只能使用 ADO.NET `DataSet`和`DataTable`來載入資料，而不會進行更新。</span><span class="sxs-lookup"><span data-stu-id="28e3a-117">This means you can only use ADO.NET `DataSet` and `DataTable` to load data and not update it.</span></span>

<span data-ttu-id="28e3a-118">使用問題[#13838](https://github.com/dotnet/efcore/issues/13838) ，提供有關執行`DbDataAdapter`的意見反應。</span><span class="sxs-lookup"><span data-stu-id="28e3a-118">Use issue [#13838](https://github.com/dotnet/efcore/issues/13838) to provide feedback about implementing `DbDataAdapter`.</span></span>

## <a name="output-parameters"></a><span data-ttu-id="28e3a-119">輸出參數</span><span class="sxs-lookup"><span data-stu-id="28e3a-119">Output parameters</span></span>

<span data-ttu-id="28e3a-120">SQLite 不支援輸出參數。</span><span class="sxs-lookup"><span data-stu-id="28e3a-120">SQLite doesn't support output parameters.</span></span>

## <a name="positional-parameters"></a><span data-ttu-id="28e3a-121">位置參數</span><span class="sxs-lookup"><span data-stu-id="28e3a-121">Positional parameters</span></span>

<span data-ttu-id="28e3a-122">Sqlite 僅支援命名[參數](parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="28e3a-122">Microsoft.Data.Sqlite only supports named [parameters](parameters.md).</span></span> <span data-ttu-id="28e3a-123">不支援位置參數。</span><span class="sxs-lookup"><span data-stu-id="28e3a-123">Positional parameters aren't supported.</span></span>

## <a name="stored-procedures"></a><span data-ttu-id="28e3a-124">預存程序</span><span class="sxs-lookup"><span data-stu-id="28e3a-124">Stored procedures</span></span>

<span data-ttu-id="28e3a-125">SQLite 不支援預存程式。</span><span class="sxs-lookup"><span data-stu-id="28e3a-125">SQLite doesn't support stored procedures.</span></span>

## <a name="isolation-levels"></a><span data-ttu-id="28e3a-126">隔離層級</span><span class="sxs-lookup"><span data-stu-id="28e3a-126">Isolation levels</span></span>

<span data-ttu-id="28e3a-127">SQLite `Chaos`交易`Snapshot`中不支援和隔離等級。</span><span class="sxs-lookup"><span data-stu-id="28e3a-127">The `Chaos` and `Snapshot` isolation levels aren't supported in SQLite transactions.</span></span>

## <a name="see-also"></a><span data-ttu-id="28e3a-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28e3a-128">See also</span></span>

* [<span data-ttu-id="28e3a-129">非同步限制</span><span class="sxs-lookup"><span data-stu-id="28e3a-129">Async limitations</span></span>](async.md)
* [<span data-ttu-id="28e3a-130">資料類型</span><span class="sxs-lookup"><span data-stu-id="28e3a-130">Data types</span></span>](types.md)
* [<span data-ttu-id="28e3a-131">異動</span><span class="sxs-lookup"><span data-stu-id="28e3a-131">Transactions</span></span>](transactions.md)
