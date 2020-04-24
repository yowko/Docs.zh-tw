---
title: 異動
ms.date: 12/13/2019
description: 瞭解如何使用交易。
ms.openlocfilehash: 4b72a1573a560ffd1bfd0f54d46ab3b135280976
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447136"
---
# <a name="transactions"></a><span data-ttu-id="0bbf2-103">交易</span><span class="sxs-lookup"><span data-stu-id="0bbf2-103">Transactions</span></span>

<span data-ttu-id="0bbf2-104">交易可讓您將多個 SQL 語句組成單一工作單位，並以一個不可部分完成的單位認可到資料庫。</span><span class="sxs-lookup"><span data-stu-id="0bbf2-104">Transactions let you group multiple SQL statements into a single unit of work that is committed to the database as one atomic unit.</span></span> <span data-ttu-id="0bbf2-105">如果交易中的任何語句失敗，則可以復原先前語句所做的變更。</span><span class="sxs-lookup"><span data-stu-id="0bbf2-105">If any statement in the transaction fails, changes made by the previous statements can be rolled back.</span></span> <span data-ttu-id="0bbf2-106">當交易啟動時，資料庫的初始狀態會保留下來。</span><span class="sxs-lookup"><span data-stu-id="0bbf2-106">The initial state of the database when the transaction was started is preserved.</span></span> <span data-ttu-id="0bbf2-107">當一次對資料庫進行許多變更時，使用交易也可以改善 SQLite 上的效能。</span><span class="sxs-lookup"><span data-stu-id="0bbf2-107">Using a transaction can also improve performance on SQLite when making numerous changes to the database at once.</span></span>

## <a name="concurrency"></a><span data-ttu-id="0bbf2-108">並行</span><span class="sxs-lookup"><span data-stu-id="0bbf2-108">Concurrency</span></span>

<span data-ttu-id="0bbf2-109">在 SQLite 中，一次只能有一個交易在資料庫中有暫止的變更。</span><span class="sxs-lookup"><span data-stu-id="0bbf2-109">In SQLite, only one transaction is allowed to have changes pending in the database at a time.</span></span> <span data-ttu-id="0bbf2-110">因此，對的呼叫<xref:Microsoft.Data.Sqlite.SqliteConnection.BeginTransaction%2A>和`Execute`方法可能會在<xref:Microsoft.Data.Sqlite.SqliteCommand>其他交易花費太長的時間才能完成。</span><span class="sxs-lookup"><span data-stu-id="0bbf2-110">Because of this, calls to <xref:Microsoft.Data.Sqlite.SqliteConnection.BeginTransaction%2A> and the `Execute` methods on <xref:Microsoft.Data.Sqlite.SqliteCommand> may time out if another transaction takes too long to complete.</span></span>

<span data-ttu-id="0bbf2-111">如需有關鎖定、重試和超時的詳細資訊，請參閱[資料庫錯誤](database-errors.md)。</span><span class="sxs-lookup"><span data-stu-id="0bbf2-111">For more information about locking, retries, and timeouts, see [Database errors](database-errors.md).</span></span>

## <a name="isolation-levels"></a><span data-ttu-id="0bbf2-112">隔離層級</span><span class="sxs-lookup"><span data-stu-id="0bbf2-112">Isolation levels</span></span>

<span data-ttu-id="0bbf2-113">根據預設，SQLite 中的交易是**可**序列化的。</span><span class="sxs-lookup"><span data-stu-id="0bbf2-113">Transactions are **serializable** by default in SQLite.</span></span> <span data-ttu-id="0bbf2-114">此隔離等級可確保在交易內進行的任何變更都完全隔離。</span><span class="sxs-lookup"><span data-stu-id="0bbf2-114">This isolation level guarantees that any changes made within a transaction are completely isolated.</span></span> <span data-ttu-id="0bbf2-115">在交易外部執行的其他語句不會受到交易變更的影響。</span><span class="sxs-lookup"><span data-stu-id="0bbf2-115">Other statements executed outside of the transaction aren't affected by the transaction's changes.</span></span>

<span data-ttu-id="0bbf2-116">SQLite 也支援使用共用快取時的**讀取未**認可。</span><span class="sxs-lookup"><span data-stu-id="0bbf2-116">SQLite also supports **read uncommitted** when using a shared cache.</span></span> <span data-ttu-id="0bbf2-117">此層級允許中途讀取、不可重複讀取和幻像：</span><span class="sxs-lookup"><span data-stu-id="0bbf2-117">This level allows dirty reads, nonrepeatable reads, and phantoms:</span></span>

- <span data-ttu-id="0bbf2-118">當某筆交易中的暫止變更由交易以外的查詢傳回時，就會發生中途*讀取*，但會回復交易中的變更。</span><span class="sxs-lookup"><span data-stu-id="0bbf2-118">A *dirty read* occurs when changes pending in one transaction are returned by a query outside of the transaction, but the changes in the transaction are rolled back.</span></span> <span data-ttu-id="0bbf2-119">結果會包含從未實際認可到資料庫的資料。</span><span class="sxs-lookup"><span data-stu-id="0bbf2-119">The results contain data that was never actually committed to the database.</span></span>

- <span data-ttu-id="0bbf2-120">當交易查詢相同的資料列兩次時，就會發生*不可重複讀取*，但結果會不同，因為另一個交易的兩個查詢之間有變更。</span><span class="sxs-lookup"><span data-stu-id="0bbf2-120">A *nonrepeatable read* occurs when a transaction queries same row twice, but the results are different because it was changed between the two queries by another transaction.</span></span>

- <span data-ttu-id="0bbf2-121">*幻像*是在交易期間變更或加入以符合查詢 where 子句的資料列。</span><span class="sxs-lookup"><span data-stu-id="0bbf2-121">*Phantoms* are rows that get changed or added to meet the where clause of a query during a transaction.</span></span> <span data-ttu-id="0bbf2-122">如果允許的話，相同的查詢在相同交易中執行兩次時，可能會傳回不同的資料列。</span><span class="sxs-lookup"><span data-stu-id="0bbf2-122">If allowed, the same query could return different rows when executed twice in the same transaction.</span></span>

<span data-ttu-id="0bbf2-123">Sqlite 會將傳遞至<xref:Microsoft.Data.Sqlite.SqliteConnection.BeginTransaction%2A>的 IsolationLevel 視為最小層級。</span><span class="sxs-lookup"><span data-stu-id="0bbf2-123">Microsoft.Data.Sqlite treats the IsolationLevel passed to <xref:Microsoft.Data.Sqlite.SqliteConnection.BeginTransaction%2A> as a minimum level.</span></span> <span data-ttu-id="0bbf2-124">實際的隔離等級會升級為讀取未認可或可序列化。</span><span class="sxs-lookup"><span data-stu-id="0bbf2-124">The actual isolation level will be promoted to either read uncommitted or serializable.</span></span>

<span data-ttu-id="0bbf2-125">下列程式碼會模擬中途讀取。</span><span class="sxs-lookup"><span data-stu-id="0bbf2-125">The following code simulates a dirty read.</span></span> <span data-ttu-id="0bbf2-126">請注意，連接字串必須包含`Cache=Shared`。</span><span class="sxs-lookup"><span data-stu-id="0bbf2-126">Note, the connection string must include `Cache=Shared`.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DirtyReadSample/Program.cs?name=snippet_DirtyRead)]
