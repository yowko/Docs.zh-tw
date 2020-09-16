---
title: 交易
ms.date: 09/08/2020
description: 瞭解如何使用交易。
ms.openlocfilehash: 50c4cd1023eac892cafc3ae4395e9168bd8e9f36
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90678858"
---
# <a name="transactions"></a><span data-ttu-id="78795-103">交易</span><span class="sxs-lookup"><span data-stu-id="78795-103">Transactions</span></span>

<span data-ttu-id="78795-104">交易可讓您將多個 SQL 語句群組成單一工作單位，並認可至資料庫做為一個不可部分完成的單位。</span><span class="sxs-lookup"><span data-stu-id="78795-104">Transactions let you group multiple SQL statements into a single unit of work that is committed to the database as one atomic unit.</span></span> <span data-ttu-id="78795-105">如果交易中有任何語句失敗，則可以回復前一個語句所做的變更。</span><span class="sxs-lookup"><span data-stu-id="78795-105">If any statement in the transaction fails, changes made by the previous statements can be rolled back.</span></span> <span data-ttu-id="78795-106">當交易開始時，資料庫的初始狀態會保留下來。</span><span class="sxs-lookup"><span data-stu-id="78795-106">The initial state of the database when the transaction was started is preserved.</span></span> <span data-ttu-id="78795-107">在對資料庫進行許多變更時，使用交易也可以改善 SQLite 的效能。</span><span class="sxs-lookup"><span data-stu-id="78795-107">Using a transaction can also improve performance on SQLite when making numerous changes to the database at once.</span></span>

## <a name="concurrency"></a><span data-ttu-id="78795-108">並行</span><span class="sxs-lookup"><span data-stu-id="78795-108">Concurrency</span></span>

<span data-ttu-id="78795-109">在 SQLite 中，一次只允許一個交易在資料庫中暫止變更。</span><span class="sxs-lookup"><span data-stu-id="78795-109">In SQLite, only one transaction is allowed to have changes pending in the database at a time.</span></span> <span data-ttu-id="78795-110">基於這個原因， <xref:Microsoft.Data.Sqlite.SqliteConnection.BeginTransaction%2A> `Execute` <xref:Microsoft.Data.Sqlite.SqliteCommand> 如果另一個交易花太多時間來完成，的呼叫和方法可能會過期。</span><span class="sxs-lookup"><span data-stu-id="78795-110">Because of this, calls to <xref:Microsoft.Data.Sqlite.SqliteConnection.BeginTransaction%2A> and the `Execute` methods on <xref:Microsoft.Data.Sqlite.SqliteCommand> may time out if another transaction takes too long to complete.</span></span>

<span data-ttu-id="78795-111">如需鎖定、重試和超時的詳細資訊，請參閱 [資料庫錯誤](database-errors.md)。</span><span class="sxs-lookup"><span data-stu-id="78795-111">For more information about locking, retries, and timeouts, see [Database errors](database-errors.md).</span></span>

## <a name="isolation-levels"></a><span data-ttu-id="78795-112">隔離層級</span><span class="sxs-lookup"><span data-stu-id="78795-112">Isolation levels</span></span>

<span data-ttu-id="78795-113">在 SQLite 中，交易預設為 **可** 序列化。</span><span class="sxs-lookup"><span data-stu-id="78795-113">Transactions are **serializable** by default in SQLite.</span></span> <span data-ttu-id="78795-114">這種隔離等級保證在交易內進行的任何變更都是完全隔離的。</span><span class="sxs-lookup"><span data-stu-id="78795-114">This isolation level guarantees that any changes made within a transaction are completely isolated.</span></span> <span data-ttu-id="78795-115">在交易以外執行的其他語句不會受交易的變更影響。</span><span class="sxs-lookup"><span data-stu-id="78795-115">Other statements executed outside of the transaction aren't affected by the transaction's changes.</span></span>

<span data-ttu-id="78795-116">使用共用快取時，SQLite 也支援 **讀取未** 認可。</span><span class="sxs-lookup"><span data-stu-id="78795-116">SQLite also supports **read uncommitted** when using a shared cache.</span></span> <span data-ttu-id="78795-117">此層級允許中途讀取、不可重複讀取和幻像：</span><span class="sxs-lookup"><span data-stu-id="78795-117">This level allows dirty reads, nonrepeatable reads, and phantoms:</span></span>

- <span data-ttu-id="78795-118">在交易以外的查詢傳回某一交易的暫止變更時，就會發生中途 *讀取* ，但交易中的變更會回復。</span><span class="sxs-lookup"><span data-stu-id="78795-118">A *dirty read* occurs when changes pending in one transaction are returned by a query outside of the transaction, but the changes in the transaction are rolled back.</span></span> <span data-ttu-id="78795-119">結果包含從未實際認可至資料庫的資料。</span><span class="sxs-lookup"><span data-stu-id="78795-119">The results contain data that was never actually committed to the database.</span></span>

- <span data-ttu-id="78795-120">當交易查詢相同的資料列兩次時，會發生 *不可重複讀取* ，但結果會不同，因為另一個交易的兩個查詢之間有變更。</span><span class="sxs-lookup"><span data-stu-id="78795-120">A *nonrepeatable read* occurs when a transaction queries same row twice, but the results are different because it was changed between the two queries by another transaction.</span></span>

- <span data-ttu-id="78795-121">*幻像* 是在交易期間變更或加入以符合查詢 where 子句的資料列。</span><span class="sxs-lookup"><span data-stu-id="78795-121">*Phantoms* are rows that get changed or added to meet the where clause of a query during a transaction.</span></span> <span data-ttu-id="78795-122">如果允許，相同的查詢在相同交易中執行兩次時，可能會傳回不同的資料列。</span><span class="sxs-lookup"><span data-stu-id="78795-122">If allowed, the same query could return different rows when executed twice in the same transaction.</span></span>

<span data-ttu-id="78795-123">IsolationLevel 會將傳遞至的視為 <xref:Microsoft.Data.Sqlite.SqliteConnection.BeginTransaction%2A> 最小層級。</span><span class="sxs-lookup"><span data-stu-id="78795-123">Microsoft.Data.Sqlite treats the IsolationLevel passed to <xref:Microsoft.Data.Sqlite.SqliteConnection.BeginTransaction%2A> as a minimum level.</span></span> <span data-ttu-id="78795-124">實際的隔離等級將會升級為讀取未認可或可序列化。</span><span class="sxs-lookup"><span data-stu-id="78795-124">The actual isolation level will be promoted to either read uncommitted or serializable.</span></span>

<span data-ttu-id="78795-125">下列程式碼會模擬中途讀取。</span><span class="sxs-lookup"><span data-stu-id="78795-125">The following code simulates a dirty read.</span></span> <span data-ttu-id="78795-126">請注意，連接字串必須包含 `Cache=Shared` 。</span><span class="sxs-lookup"><span data-stu-id="78795-126">Note, the connection string must include `Cache=Shared`.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DirtyReadSample/Program.cs?name=snippet_DirtyRead)]

## <a name="deferred-transactions"></a><span data-ttu-id="78795-127">延遲交易</span><span class="sxs-lookup"><span data-stu-id="78795-127">Deferred transactions</span></span>

<span data-ttu-id="78795-128">從5.0 版開始，可以延後交易。</span><span class="sxs-lookup"><span data-stu-id="78795-128">Starting with Microsoft.Data.Sqlite version 5.0, transactions can be deferred.</span></span> <span data-ttu-id="78795-129">這會延遲在資料庫中建立實際的交易，直到第一個命令執行為止。</span><span class="sxs-lookup"><span data-stu-id="78795-129">This defers the creation of the actual transaction in the database until the first command is executed.</span></span> <span data-ttu-id="78795-130">它也會讓交易從讀取交易逐漸升級到其命令所需的寫入交易。</span><span class="sxs-lookup"><span data-stu-id="78795-130">It also causes the transaction to gradually upgrade from a read transaction to a write transaction as needed by its commands.</span></span> <span data-ttu-id="78795-131">這有助於在交易期間啟用資料庫的平行存取。</span><span class="sxs-lookup"><span data-stu-id="78795-131">This can be useful for enabling concurrent access to the database during the transaction.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DeferredTransactionSample/Program.cs?name=snippet_DeferredTransaction)]

> [!WARNING]
> <span data-ttu-id="78795-132">延遲交易內的命令可能會在資料庫被鎖定時，將交易從讀取交易升級到寫入交易時失敗。</span><span class="sxs-lookup"><span data-stu-id="78795-132">Commands inside a deferred transaction can fail if they cause the transaction to be upgraded from a read transaction to a write transaction while the database is locked.</span></span> <span data-ttu-id="78795-133">當發生這種情況時，應用程式就必須重試整個交易。</span><span class="sxs-lookup"><span data-stu-id="78795-133">When this happens, the application will need to retry the entire transaction.</span></span>
