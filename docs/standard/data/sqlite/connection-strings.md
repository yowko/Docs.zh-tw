---
title: 連接字串
ms.date: 12/13/2019
description: 連接字串支援的關鍵字和值。
ms.openlocfilehash: bb54d152bac62a86c2a49192cf678a745159164e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447010"
---
# <a name="connection-strings"></a><span data-ttu-id="f5a89-103">連接字串</span><span class="sxs-lookup"><span data-stu-id="f5a89-103">Connection strings</span></span>

<span data-ttu-id="f5a89-104">連接字串是用來指定如何連接到資料庫。</span><span class="sxs-lookup"><span data-stu-id="f5a89-104">A connection string is used to specify how to connect to the database.</span></span> <span data-ttu-id="f5a89-105">在 Microsoft 中的連接字串會遵循標準[ADO.NET 語法](../../../framework/data/adonet/connection-strings.md)，做為關鍵字和值的分號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="f5a89-105">Connection strings in Microsoft.Data.Sqlite follow the standard [ADO.NET syntax](../../../framework/data/adonet/connection-strings.md) as a semicolon-separated list of keywords and values.</span></span>

## <a name="keywords"></a><span data-ttu-id="f5a89-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="f5a89-106">Keywords</span></span>

<span data-ttu-id="f5a89-107">下列連接字串關鍵字可與 Microsoft 一起使用。 Sqlite：</span><span class="sxs-lookup"><span data-stu-id="f5a89-107">The following connection string keywords can be used with Microsoft.Data.Sqlite:</span></span>

### <a name="data-source"></a><span data-ttu-id="f5a89-108">資料來源</span><span class="sxs-lookup"><span data-stu-id="f5a89-108">Data source</span></span>

<span data-ttu-id="f5a89-109">資料庫檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="f5a89-109">The path to the database file.</span></span> <span data-ttu-id="f5a89-110">*DataSource* （不含空格）和*Filename*是此關鍵字的別名。</span><span class="sxs-lookup"><span data-stu-id="f5a89-110">*DataSource* (without a space) and *Filename* are aliases of this keyword.</span></span>

<span data-ttu-id="f5a89-111">SQLite 會對待相對於目前工作目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="f5a89-111">SQLite treats paths relative to the current working directory.</span></span> <span data-ttu-id="f5a89-112">也可以指定絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="f5a89-112">Absolute paths can also be specified.</span></span>

<span data-ttu-id="f5a89-113">如果是**空**的，SQLite 會在關閉連線時，建立已刪除的暫存磁片資料庫。</span><span class="sxs-lookup"><span data-stu-id="f5a89-113">If **empty**, SQLite creates a temporary on-disk database that's deleted when the connection is closed.</span></span>

<span data-ttu-id="f5a89-114">如果 `:memory:`，則會使用記憶體內部資料庫。</span><span class="sxs-lookup"><span data-stu-id="f5a89-114">If `:memory:`, an in-memory database is used.</span></span> <span data-ttu-id="f5a89-115">如需詳細資訊，請參閱[記憶體內部資料庫](in-memory-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="f5a89-115">For more information, see [In-Memory databases](in-memory-databases.md).</span></span>

<span data-ttu-id="f5a89-116">以 `|DataDirectory|` 替代字串開頭的路徑會被視為相對路徑。</span><span class="sxs-lookup"><span data-stu-id="f5a89-116">Paths that start with the `|DataDirectory|` substitution string are treated the same as relative paths.</span></span> <span data-ttu-id="f5a89-117">如果設定，則會建立相對於 DataDirectory 應用程式域屬性值的路徑。</span><span class="sxs-lookup"><span data-stu-id="f5a89-117">If set, paths are made relative to the DataDirectory application domain property value.</span></span>

<span data-ttu-id="f5a89-118">此關鍵字也支援[URI 檔案名](https://www.sqlite.org/uri.html)。</span><span class="sxs-lookup"><span data-stu-id="f5a89-118">This keyword also supports [URI Filenames](https://www.sqlite.org/uri.html).</span></span>

### <a name="mode"></a><span data-ttu-id="f5a89-119">Mode</span><span class="sxs-lookup"><span data-stu-id="f5a89-119">Mode</span></span>

<span data-ttu-id="f5a89-120">連接模式。</span><span class="sxs-lookup"><span data-stu-id="f5a89-120">The connection mode.</span></span>

| <span data-ttu-id="f5a89-121">{2&gt;值&lt;2}</span><span class="sxs-lookup"><span data-stu-id="f5a89-121">Value</span></span>           | <span data-ttu-id="f5a89-122">描述</span><span class="sxs-lookup"><span data-stu-id="f5a89-122">Description</span></span>                                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="f5a89-123">ReadWriteCreate</span><span class="sxs-lookup"><span data-stu-id="f5a89-123">ReadWriteCreate</span></span> | <span data-ttu-id="f5a89-124">開啟資料庫進行讀取和寫入，如果不存在，則建立它。</span><span class="sxs-lookup"><span data-stu-id="f5a89-124">Opens the database for reading and writing, and creates it if it doesn't exist.</span></span> <span data-ttu-id="f5a89-125">這是預設設定。</span><span class="sxs-lookup"><span data-stu-id="f5a89-125">This is the default.</span></span> |
| <span data-ttu-id="f5a89-126">ReadWrite</span><span class="sxs-lookup"><span data-stu-id="f5a89-126">ReadWrite</span></span>       | <span data-ttu-id="f5a89-127">開啟資料庫進行讀取和寫入。</span><span class="sxs-lookup"><span data-stu-id="f5a89-127">Opens the database for reading and writing.</span></span>                                                        |
| <span data-ttu-id="f5a89-128">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="f5a89-128">ReadOnly</span></span>        | <span data-ttu-id="f5a89-129">以唯讀模式開啟資料庫。</span><span class="sxs-lookup"><span data-stu-id="f5a89-129">Opens the database in read-only mode.</span></span>                                                              |
| <span data-ttu-id="f5a89-130">記憶體</span><span class="sxs-lookup"><span data-stu-id="f5a89-130">Memory</span></span>          | <span data-ttu-id="f5a89-131">開啟記憶體內部資料庫。</span><span class="sxs-lookup"><span data-stu-id="f5a89-131">Opens an in-memory database.</span></span>                                                                       |

### <a name="cache"></a><span data-ttu-id="f5a89-132">快取</span><span class="sxs-lookup"><span data-stu-id="f5a89-132">Cache</span></span>

<span data-ttu-id="f5a89-133">連接所使用的快取模式。</span><span class="sxs-lookup"><span data-stu-id="f5a89-133">The caching mode used by the connection.</span></span>

| <span data-ttu-id="f5a89-134">{2&gt;值&lt;2}</span><span class="sxs-lookup"><span data-stu-id="f5a89-134">Value</span></span>   | <span data-ttu-id="f5a89-135">描述</span><span class="sxs-lookup"><span data-stu-id="f5a89-135">Description</span></span>                                                                                    |
| ------- | ---------------------------------------------------------------------------------------------- |
| <span data-ttu-id="f5a89-136">預設值</span><span class="sxs-lookup"><span data-stu-id="f5a89-136">Default</span></span> | <span data-ttu-id="f5a89-137">使用基礎 SQLite 程式庫的預設模式。</span><span class="sxs-lookup"><span data-stu-id="f5a89-137">Uses the default mode of the underlying SQLite library.</span></span> <span data-ttu-id="f5a89-138">這是預設設定。</span><span class="sxs-lookup"><span data-stu-id="f5a89-138">This is the default.</span></span>                   |
| <span data-ttu-id="f5a89-139">私人</span><span class="sxs-lookup"><span data-stu-id="f5a89-139">Private</span></span> | <span data-ttu-id="f5a89-140">每個連接都會使用私用快取。</span><span class="sxs-lookup"><span data-stu-id="f5a89-140">Each connection uses a private cache.</span></span>                                                          |
| <span data-ttu-id="f5a89-141">[共用]</span><span class="sxs-lookup"><span data-stu-id="f5a89-141">Shared</span></span>  | <span data-ttu-id="f5a89-142">連接會共用快取。</span><span class="sxs-lookup"><span data-stu-id="f5a89-142">Connections share a cache.</span></span> <span data-ttu-id="f5a89-143">此模式可以變更交易和表鎖定的行為。</span><span class="sxs-lookup"><span data-stu-id="f5a89-143">This mode can change the behavior of transaction and table locking.</span></span> |

### <a name="password"></a><span data-ttu-id="f5a89-144">密碼</span><span class="sxs-lookup"><span data-stu-id="f5a89-144">Password</span></span>

<span data-ttu-id="f5a89-145">加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="f5a89-145">The encryption key.</span></span> <span data-ttu-id="f5a89-146">當指定時，會在開啟連接之後立即傳送 `PRAGMA key`。</span><span class="sxs-lookup"><span data-stu-id="f5a89-146">When specified, `PRAGMA key` is sent immediately after opening the connection.</span></span>

> [!WARNING]
> <span data-ttu-id="f5a89-147">當原生 SQLite 程式庫不支援加密時，Password 不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="f5a89-147">Password has no effect when encryption isn't supported by the native SQLite library.</span></span>

### <a name="foreign-keys"></a><span data-ttu-id="f5a89-148">外部索引鍵</span><span class="sxs-lookup"><span data-stu-id="f5a89-148">Foreign Keys</span></span>

<span data-ttu-id="f5a89-149">值，指出是否啟用外鍵條件約束。</span><span class="sxs-lookup"><span data-stu-id="f5a89-149">A value indicating whether to enable foreign key constraints.</span></span>

| <span data-ttu-id="f5a89-150">{2&gt;值&lt;2}</span><span class="sxs-lookup"><span data-stu-id="f5a89-150">Value</span></span>   | <span data-ttu-id="f5a89-151">描述</span><span class="sxs-lookup"><span data-stu-id="f5a89-151">Description</span></span>
| ------- | --- |
| <span data-ttu-id="f5a89-152">True</span><span class="sxs-lookup"><span data-stu-id="f5a89-152">True</span></span>    | <span data-ttu-id="f5a89-153">在開啟連接之後立即傳送 `PRAGMA foreign_keys = 1`。</span><span class="sxs-lookup"><span data-stu-id="f5a89-153">Sends `PRAGMA foreign_keys = 1` immediately after opening the connection.</span></span>
| <span data-ttu-id="f5a89-154">False</span><span class="sxs-lookup"><span data-stu-id="f5a89-154">False</span></span>   | <span data-ttu-id="f5a89-155">在開啟連接之後立即傳送 `PRAGMA foreign_keys = 0`。</span><span class="sxs-lookup"><span data-stu-id="f5a89-155">Sends `PRAGMA foreign_keys = 0` immediately after opening the connection.</span></span>
| <span data-ttu-id="f5a89-156">(空白)</span><span class="sxs-lookup"><span data-stu-id="f5a89-156">(empty)</span></span> | <span data-ttu-id="f5a89-157">不會傳送 `PRAGMA foreign_keys`。</span><span class="sxs-lookup"><span data-stu-id="f5a89-157">Doesn't send `PRAGMA foreign_keys`.</span></span> <span data-ttu-id="f5a89-158">這是預設設定。</span><span class="sxs-lookup"><span data-stu-id="f5a89-158">This is the default.</span></span> |

<span data-ttu-id="f5a89-159">不需要啟用外鍵，如 e_sqlite3 中，SQLITE_DEFAULT_FOREIGN_KEYS 用來編譯原生 SQLite 程式庫。</span><span class="sxs-lookup"><span data-stu-id="f5a89-159">There's no need enable foreign keys if, like in e_sqlite3, SQLITE_DEFAULT_FOREIGN_KEYS was used to compile the native SQLite library.</span></span>

### <a name="recursive-triggers"></a><span data-ttu-id="f5a89-160">遞迴觸發程式</span><span class="sxs-lookup"><span data-stu-id="f5a89-160">Recursive triggers</span></span>

<span data-ttu-id="f5a89-161">值，指出是否要啟用遞迴觸發程式。</span><span class="sxs-lookup"><span data-stu-id="f5a89-161">A value that indicates whether to enable recursive triggers.</span></span>

| <span data-ttu-id="f5a89-162">{2&gt;值&lt;2}</span><span class="sxs-lookup"><span data-stu-id="f5a89-162">Value</span></span> | <span data-ttu-id="f5a89-163">描述</span><span class="sxs-lookup"><span data-stu-id="f5a89-163">Description</span></span>                                                                 |
| ----- | --------------------------------------------------------------------------- |
| <span data-ttu-id="f5a89-164">True</span><span class="sxs-lookup"><span data-stu-id="f5a89-164">True</span></span>  | <span data-ttu-id="f5a89-165">在開啟連接之後立即傳送 `PRAGMA recursive_triggers`。</span><span class="sxs-lookup"><span data-stu-id="f5a89-165">Sends `PRAGMA recursive_triggers` immediately after opening the connection.</span></span> |
| <span data-ttu-id="f5a89-166">False</span><span class="sxs-lookup"><span data-stu-id="f5a89-166">False</span></span> | <span data-ttu-id="f5a89-167">不會傳送 `PRAGMA recursive_triggers`。</span><span class="sxs-lookup"><span data-stu-id="f5a89-167">Doesn't send `PRAGMA recursive_triggers`.</span></span> <span data-ttu-id="f5a89-168">這是預設設定。</span><span class="sxs-lookup"><span data-stu-id="f5a89-168">This is the default.</span></span>              |

## <a name="connection-string-builder"></a><span data-ttu-id="f5a89-169">連接字串產生器</span><span class="sxs-lookup"><span data-stu-id="f5a89-169">Connection string builder</span></span>

<span data-ttu-id="f5a89-170">您可以使用 <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> 做為建立連接字串的強型別方式。</span><span class="sxs-lookup"><span data-stu-id="f5a89-170">You can use <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> as a strongly typed way of creating connection strings.</span></span> <span data-ttu-id="f5a89-171">它也可以用來防止連接字串插入式攻擊。</span><span class="sxs-lookup"><span data-stu-id="f5a89-171">It can also be used to prevent connection string injection attacks.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="examples"></a><span data-ttu-id="f5a89-172">範例</span><span class="sxs-lookup"><span data-stu-id="f5a89-172">Examples</span></span>

### <a name="basic"></a><span data-ttu-id="f5a89-173">Basic</span><span class="sxs-lookup"><span data-stu-id="f5a89-173">Basic</span></span>

<span data-ttu-id="f5a89-174">具有共用快取以改善並行的基本連接字串。</span><span class="sxs-lookup"><span data-stu-id="f5a89-174">A basic connection string with a shared cache for improved concurrency.</span></span>

```ConnectionString
Data Source=Application.db;Cache=Shared
```

### <a name="encrypted"></a><span data-ttu-id="f5a89-175">已加密</span><span class="sxs-lookup"><span data-stu-id="f5a89-175">Encrypted</span></span>

<span data-ttu-id="f5a89-176">加密的資料庫。</span><span class="sxs-lookup"><span data-stu-id="f5a89-176">An encrypted database.</span></span>

```ConnectionString
Data Source=Encrypted.db;Password=MyEncryptionKey
```

### <a name="read-only"></a><span data-ttu-id="f5a89-177">唯讀</span><span class="sxs-lookup"><span data-stu-id="f5a89-177">Read-only</span></span>

<span data-ttu-id="f5a89-178">應用程式無法修改的唯讀資料庫。</span><span class="sxs-lookup"><span data-stu-id="f5a89-178">A read-only database that cannot be modified by the app.</span></span>

```ConnectionString
Data Source=Reference.db;Mode=ReadOnly
```

### <a name="in-memory"></a><span data-ttu-id="f5a89-179">記憶體中</span><span class="sxs-lookup"><span data-stu-id="f5a89-179">In-memory</span></span>

<span data-ttu-id="f5a89-180">私用記憶體內部資料庫。</span><span class="sxs-lookup"><span data-stu-id="f5a89-180">A private, in-memory database.</span></span>

```ConnectionString
Data Source=:memory:
```

### <a name="sharable-in-memory"></a><span data-ttu-id="f5a89-181">可在記憶體中共用</span><span class="sxs-lookup"><span data-stu-id="f5a89-181">Sharable in-memory</span></span>

<span data-ttu-id="f5a89-182">由可*共用*的名稱所識別的可共用記憶體內部資料庫。</span><span class="sxs-lookup"><span data-stu-id="f5a89-182">A sharable, in-memory database identified by the name *Sharable*.</span></span>

```ConnectionString
Data Source=Sharable;Mode=Memory;Cache=Shared
```

## <a name="see-also"></a><span data-ttu-id="f5a89-183">請參閱</span><span class="sxs-lookup"><span data-stu-id="f5a89-183">See also</span></span>

* [<span data-ttu-id="f5a89-184">ADO.NET 中的連接字串</span><span class="sxs-lookup"><span data-stu-id="f5a89-184">Connection Strings in ADO.NET</span></span>](../../../framework/data/adonet/connection-strings.md)
* [<span data-ttu-id="f5a89-185">記憶體內部資料庫</span><span class="sxs-lookup"><span data-stu-id="f5a89-185">In-Memory databases</span></span>](in-memory-databases.md)
* [<span data-ttu-id="f5a89-186">異動</span><span class="sxs-lookup"><span data-stu-id="f5a89-186">Transactions</span></span>](transactions.md)
