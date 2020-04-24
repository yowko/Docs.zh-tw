---
title: 資料庫錯誤
ms.date: 12/13/2019
description: 描述資料庫錯誤和淘汰如何由程式庫處理。
ms.openlocfilehash: 9a613b6f94a89dc40e627c14f46836be77080035
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447269"
---
# <a name="database-errors"></a><span data-ttu-id="65a11-103">資料庫錯誤</span><span class="sxs-lookup"><span data-stu-id="65a11-103">Database errors</span></span>

<span data-ttu-id="65a11-104"><xref:Microsoft.Data.Sqlite.SqliteException>當遇到 SQLite 錯誤時，就會擲回。</span><span class="sxs-lookup"><span data-stu-id="65a11-104"><xref:Microsoft.Data.Sqlite.SqliteException> is thrown when a SQLite error is encountered.</span></span> <span data-ttu-id="65a11-105">訊息是由 SQLite 所提供。</span><span class="sxs-lookup"><span data-stu-id="65a11-105">The message is provided by SQLite.</span></span> <span data-ttu-id="65a11-106">和屬性包含錯誤的 SQLite[結果程式碼。](https://www.sqlite.org/rescode.html) `SqliteErrorCode` `SqliteExtendedErrorCode`</span><span class="sxs-lookup"><span data-stu-id="65a11-106">The `SqliteErrorCode` and `SqliteExtendedErrorCode` properties contain the SQLite [result code](https://www.sqlite.org/rescode.html) of the error.</span></span>

<span data-ttu-id="65a11-107">任何時間都可能發生錯誤。 Sqlite 會與原生的 SQLite 程式庫互動。</span><span class="sxs-lookup"><span data-stu-id="65a11-107">Errors may be encountered any time the Microsoft.Data.Sqlite interacts with the native SQLite library.</span></span> <span data-ttu-id="65a11-108">下列清單顯示錯誤可能發生的常見案例：</span><span class="sxs-lookup"><span data-stu-id="65a11-108">The following list shows the common scenarios where errors can occur:</span></span>

* <span data-ttu-id="65a11-109">開啟連接。</span><span class="sxs-lookup"><span data-stu-id="65a11-109">Opening a connection.</span></span>
* <span data-ttu-id="65a11-110">開始交易。</span><span class="sxs-lookup"><span data-stu-id="65a11-110">Beginning a transaction.</span></span>
* <span data-ttu-id="65a11-111">執行命令。</span><span class="sxs-lookup"><span data-stu-id="65a11-111">Executing a command.</span></span>
* <span data-ttu-id="65a11-112">呼叫 <xref:Microsoft.Data.Sqlite.SqliteDataReader.NextResult%2A>。</span><span class="sxs-lookup"><span data-stu-id="65a11-112">Calling <xref:Microsoft.Data.Sqlite.SqliteDataReader.NextResult%2A>.</span></span>

<span data-ttu-id="65a11-113">請仔細考慮您的應用程式將如何處理這些錯誤。</span><span class="sxs-lookup"><span data-stu-id="65a11-113">Consider carefully how your app will handle these errors.</span></span>

## <a name="locking-retries-and-timeouts"></a><span data-ttu-id="65a11-114">鎖定、重試和超時</span><span class="sxs-lookup"><span data-stu-id="65a11-114">Locking, retries, and timeouts</span></span>

<span data-ttu-id="65a11-115">SQLite 在鎖定資料表和資料庫檔案時非常積極。</span><span class="sxs-lookup"><span data-stu-id="65a11-115">SQLite is aggressive when it comes to locking tables and database files.</span></span> <span data-ttu-id="65a11-116">如果您的應用程式啟用任何並行資料庫存取，您可能會遇到忙碌和鎖定的錯誤。</span><span class="sxs-lookup"><span data-stu-id="65a11-116">If your app enables any concurrent database access, you'll likely encounter busy and locked errors.</span></span> <span data-ttu-id="65a11-117">您可以使用[共用](connection-strings.md#cache)快取和預先[寫入記錄](async.md)來減輕許多錯誤。</span><span class="sxs-lookup"><span data-stu-id="65a11-117">You can mitigate many errors by using a [shared cache](connection-strings.md#cache) and [write-ahead logging](async.md).</span></span>

<span data-ttu-id="65a11-118">每當 Microsoft Data Sqlite 遇到忙碌或鎖定的錯誤時，它會自動重試，直到成功或到達命令逾時為止。</span><span class="sxs-lookup"><span data-stu-id="65a11-118">Whenever Microsoft.Data.Sqlite encounters a busy or locked error, it will automatically retry until it succeeds or the command timeout is reached.</span></span>

<span data-ttu-id="65a11-119">您可以藉由設定<xref:Microsoft.Data.Sqlite.SqliteCommand.CommandTimeout%2A>來增加命令的超時時間。</span><span class="sxs-lookup"><span data-stu-id="65a11-119">You can increase the timeout of command by setting <xref:Microsoft.Data.Sqlite.SqliteCommand.CommandTimeout%2A>.</span></span> <span data-ttu-id="65a11-120">預設的超時時間為30秒。</span><span class="sxs-lookup"><span data-stu-id="65a11-120">The default timeout is 30 seconds.</span></span> <span data-ttu-id="65a11-121">的`0`值表示沒有 timeout。</span><span class="sxs-lookup"><span data-stu-id="65a11-121">A value of `0` means no timeout.</span></span>

```csharp
// Retry for 60 seconds while locked
command.CommandTimeout = 60;
```

<span data-ttu-id="65a11-122">然後，Sqlite 有時需要建立隱含的命令物件。</span><span class="sxs-lookup"><span data-stu-id="65a11-122">Microsoft.Data.Sqlite sometimes needs to create an implicit command object.</span></span> <span data-ttu-id="65a11-123">例如，在 BeginTransaction 期間。</span><span class="sxs-lookup"><span data-stu-id="65a11-123">For example, during BeginTransaction.</span></span> <span data-ttu-id="65a11-124">若要設定這些命令的超時時間， <xref:Microsoft.Data.Sqlite.SqliteConnection.DefaultTimeout%2A>請使用。</span><span class="sxs-lookup"><span data-stu-id="65a11-124">To set the timeout for these commands, use <xref:Microsoft.Data.Sqlite.SqliteConnection.DefaultTimeout%2A>.</span></span>

```csharp
// Set the default timeout of all commands on this connection
connection.DefaultTimeout = 60;
```

## <a name="see-also"></a><span data-ttu-id="65a11-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65a11-125">See also</span></span>

* [<span data-ttu-id="65a11-126">SQLite 錯誤碼</span><span class="sxs-lookup"><span data-stu-id="65a11-126">SQLite Error Codes</span></span>](https://www.sqlite.org/rescode.html)
* [<span data-ttu-id="65a11-127">SQLite 中的檔案鎖定</span><span class="sxs-lookup"><span data-stu-id="65a11-127">File Locking In SQLite</span></span>](https://www.sqlite.org/lockingv3.html)
* [<span data-ttu-id="65a11-128">共用-快取模式</span><span class="sxs-lookup"><span data-stu-id="65a11-128">Shared-Cache Mode</span></span>](https://www.sqlite.org/sharedcache.html)
* [<span data-ttu-id="65a11-129">預先寫入記錄</span><span class="sxs-lookup"><span data-stu-id="65a11-129">Write-Ahead Logging</span></span>](https://www.sqlite.org/wal.html)
