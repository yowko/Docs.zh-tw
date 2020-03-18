---
title: 連接字串
ms.date: 12/13/2019
description: 支援的關鍵字和連接字串的值。
ms.openlocfilehash: bb54d152bac62a86c2a49192cf678a745159164e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400446"
---
# <a name="connection-strings"></a><span data-ttu-id="4871b-103">連接字串</span><span class="sxs-lookup"><span data-stu-id="4871b-103">Connection strings</span></span>

<span data-ttu-id="4871b-104">連接字串用於指定如何連接到資料庫。</span><span class="sxs-lookup"><span data-stu-id="4871b-104">A connection string is used to specify how to connect to the database.</span></span> <span data-ttu-id="4871b-105">Microsoft.Data.Sqlite 中的連接字串遵循標準[ADO.NET語法](../../../framework/data/adonet/connection-strings.md)作為關鍵字和值的分號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="4871b-105">Connection strings in Microsoft.Data.Sqlite follow the standard [ADO.NET syntax](../../../framework/data/adonet/connection-strings.md) as a semicolon-separated list of keywords and values.</span></span>

## <a name="keywords"></a><span data-ttu-id="4871b-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="4871b-106">Keywords</span></span>

<span data-ttu-id="4871b-107">以下連接字串關鍵字可用於 Microsoft.Data.Sqlite：</span><span class="sxs-lookup"><span data-stu-id="4871b-107">The following connection string keywords can be used with Microsoft.Data.Sqlite:</span></span>

### <a name="data-source"></a><span data-ttu-id="4871b-108">資料來源</span><span class="sxs-lookup"><span data-stu-id="4871b-108">Data source</span></span>

<span data-ttu-id="4871b-109">資料庫檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="4871b-109">The path to the database file.</span></span> <span data-ttu-id="4871b-110">*資料來源*（沒有空格）和*檔案名*是此關鍵字的別名。</span><span class="sxs-lookup"><span data-stu-id="4871b-110">*DataSource* (without a space) and *Filename* are aliases of this keyword.</span></span>

<span data-ttu-id="4871b-111">SQLite 處理相對於當前工作目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="4871b-111">SQLite treats paths relative to the current working directory.</span></span> <span data-ttu-id="4871b-112">也可以指定絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="4871b-112">Absolute paths can also be specified.</span></span>

<span data-ttu-id="4871b-113">如果**為空**，SQLite 將創建一個臨時磁片資料庫，該資料庫在連接關閉時被刪除。</span><span class="sxs-lookup"><span data-stu-id="4871b-113">If **empty**, SQLite creates a temporary on-disk database that's deleted when the connection is closed.</span></span>

<span data-ttu-id="4871b-114">如果`:memory:`使用 記憶體中資料庫。</span><span class="sxs-lookup"><span data-stu-id="4871b-114">If `:memory:`, an in-memory database is used.</span></span> <span data-ttu-id="4871b-115">有關詳細資訊，請參閱[記憶體中資料庫](in-memory-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="4871b-115">For more information, see [In-Memory databases](in-memory-databases.md).</span></span>

<span data-ttu-id="4871b-116">以替換字串開頭的`|DataDirectory|`路徑與相對路徑相同。</span><span class="sxs-lookup"><span data-stu-id="4871b-116">Paths that start with the `|DataDirectory|` substitution string are treated the same as relative paths.</span></span> <span data-ttu-id="4871b-117">如果設置，則根據 DataDirectory 應用程式域屬性值製作路徑。</span><span class="sxs-lookup"><span data-stu-id="4871b-117">If set, paths are made relative to the DataDirectory application domain property value.</span></span>

<span data-ttu-id="4871b-118">此關鍵字還支援[URI 檔案名](https://www.sqlite.org/uri.html)。</span><span class="sxs-lookup"><span data-stu-id="4871b-118">This keyword also supports [URI Filenames](https://www.sqlite.org/uri.html).</span></span>

### <a name="mode"></a><span data-ttu-id="4871b-119">[模式]</span><span class="sxs-lookup"><span data-stu-id="4871b-119">Mode</span></span>

<span data-ttu-id="4871b-120">連接模式。</span><span class="sxs-lookup"><span data-stu-id="4871b-120">The connection mode.</span></span>

| <span data-ttu-id="4871b-121">值</span><span class="sxs-lookup"><span data-stu-id="4871b-121">Value</span></span>           | <span data-ttu-id="4871b-122">描述</span><span class="sxs-lookup"><span data-stu-id="4871b-122">Description</span></span>                                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="4871b-123">讀取寫入創建</span><span class="sxs-lookup"><span data-stu-id="4871b-123">ReadWriteCreate</span></span> | <span data-ttu-id="4871b-124">打開資料庫進行讀取和寫入，如果資料庫不存在，請創建它。</span><span class="sxs-lookup"><span data-stu-id="4871b-124">Opens the database for reading and writing, and creates it if it doesn't exist.</span></span> <span data-ttu-id="4871b-125">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="4871b-125">This is the default.</span></span> |
| <span data-ttu-id="4871b-126">讀寫</span><span class="sxs-lookup"><span data-stu-id="4871b-126">ReadWrite</span></span>       | <span data-ttu-id="4871b-127">打開用於讀取和寫入的資料庫。</span><span class="sxs-lookup"><span data-stu-id="4871b-127">Opens the database for reading and writing.</span></span>                                                        |
| <span data-ttu-id="4871b-128">唯讀</span><span class="sxs-lookup"><span data-stu-id="4871b-128">ReadOnly</span></span>        | <span data-ttu-id="4871b-129">以唯讀模式打開資料庫。</span><span class="sxs-lookup"><span data-stu-id="4871b-129">Opens the database in read-only mode.</span></span>                                                              |
| <span data-ttu-id="4871b-130">記憶體</span><span class="sxs-lookup"><span data-stu-id="4871b-130">Memory</span></span>          | <span data-ttu-id="4871b-131">打開記憶體中資料庫。</span><span class="sxs-lookup"><span data-stu-id="4871b-131">Opens an in-memory database.</span></span>                                                                       |

### <a name="cache"></a><span data-ttu-id="4871b-132">快取</span><span class="sxs-lookup"><span data-stu-id="4871b-132">Cache</span></span>

<span data-ttu-id="4871b-133">連接使用的緩存模式。</span><span class="sxs-lookup"><span data-stu-id="4871b-133">The caching mode used by the connection.</span></span>

| <span data-ttu-id="4871b-134">值</span><span class="sxs-lookup"><span data-stu-id="4871b-134">Value</span></span>   | <span data-ttu-id="4871b-135">描述</span><span class="sxs-lookup"><span data-stu-id="4871b-135">Description</span></span>                                                                                    |
| ------- | ---------------------------------------------------------------------------------------------- |
| <span data-ttu-id="4871b-136">預設</span><span class="sxs-lookup"><span data-stu-id="4871b-136">Default</span></span> | <span data-ttu-id="4871b-137">使用基礎 SQLite 庫的預設模式。</span><span class="sxs-lookup"><span data-stu-id="4871b-137">Uses the default mode of the underlying SQLite library.</span></span> <span data-ttu-id="4871b-138">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="4871b-138">This is the default.</span></span>                   |
| <span data-ttu-id="4871b-139">Private</span><span class="sxs-lookup"><span data-stu-id="4871b-139">Private</span></span> | <span data-ttu-id="4871b-140">每個連接都使用專用緩存。</span><span class="sxs-lookup"><span data-stu-id="4871b-140">Each connection uses a private cache.</span></span>                                                          |
| <span data-ttu-id="4871b-141">共用</span><span class="sxs-lookup"><span data-stu-id="4871b-141">Shared</span></span>  | <span data-ttu-id="4871b-142">連接共用緩存。</span><span class="sxs-lookup"><span data-stu-id="4871b-142">Connections share a cache.</span></span> <span data-ttu-id="4871b-143">此模式可以更改事務和表鎖定的行為。</span><span class="sxs-lookup"><span data-stu-id="4871b-143">This mode can change the behavior of transaction and table locking.</span></span> |

### <a name="password"></a><span data-ttu-id="4871b-144">密碼</span><span class="sxs-lookup"><span data-stu-id="4871b-144">Password</span></span>

<span data-ttu-id="4871b-145">加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="4871b-145">The encryption key.</span></span> <span data-ttu-id="4871b-146">指定後，`PRAGMA key`將立即在打開連接後發送。</span><span class="sxs-lookup"><span data-stu-id="4871b-146">When specified, `PRAGMA key` is sent immediately after opening the connection.</span></span>

> [!WARNING]
> <span data-ttu-id="4871b-147">當本機 SQLite 庫不支援加密時，密碼不起作用。</span><span class="sxs-lookup"><span data-stu-id="4871b-147">Password has no effect when encryption isn't supported by the native SQLite library.</span></span>

### <a name="foreign-keys"></a><span data-ttu-id="4871b-148">外部索引鍵</span><span class="sxs-lookup"><span data-stu-id="4871b-148">Foreign Keys</span></span>

<span data-ttu-id="4871b-149">指示是否啟用外鍵約束的值。</span><span class="sxs-lookup"><span data-stu-id="4871b-149">A value indicating whether to enable foreign key constraints.</span></span>

| <span data-ttu-id="4871b-150">值</span><span class="sxs-lookup"><span data-stu-id="4871b-150">Value</span></span>   | <span data-ttu-id="4871b-151">描述</span><span class="sxs-lookup"><span data-stu-id="4871b-151">Description</span></span>
| ------- | --- |
| <span data-ttu-id="4871b-152">True</span><span class="sxs-lookup"><span data-stu-id="4871b-152">True</span></span>    | <span data-ttu-id="4871b-153">打開`PRAGMA foreign_keys = 1`連接後立即發送。</span><span class="sxs-lookup"><span data-stu-id="4871b-153">Sends `PRAGMA foreign_keys = 1` immediately after opening the connection.</span></span>
| <span data-ttu-id="4871b-154">False</span><span class="sxs-lookup"><span data-stu-id="4871b-154">False</span></span>   | <span data-ttu-id="4871b-155">打開`PRAGMA foreign_keys = 0`連接後立即發送。</span><span class="sxs-lookup"><span data-stu-id="4871b-155">Sends `PRAGMA foreign_keys = 0` immediately after opening the connection.</span></span>
| <span data-ttu-id="4871b-156">(空白)</span><span class="sxs-lookup"><span data-stu-id="4871b-156">(empty)</span></span> | <span data-ttu-id="4871b-157">不發送`PRAGMA foreign_keys`。</span><span class="sxs-lookup"><span data-stu-id="4871b-157">Doesn't send `PRAGMA foreign_keys`.</span></span> <span data-ttu-id="4871b-158">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="4871b-158">This is the default.</span></span> |

<span data-ttu-id="4871b-159">e_sqlite3 如果SQLITE_DEFAULT_FOREIGN_KEYS用於編譯本機 SQLite 庫，則無需啟用外鍵。</span><span class="sxs-lookup"><span data-stu-id="4871b-159">There's no need enable foreign keys if, like in e_sqlite3, SQLITE_DEFAULT_FOREIGN_KEYS was used to compile the native SQLite library.</span></span>

### <a name="recursive-triggers"></a><span data-ttu-id="4871b-160">遞迴觸發器</span><span class="sxs-lookup"><span data-stu-id="4871b-160">Recursive triggers</span></span>

<span data-ttu-id="4871b-161">指示是否啟用遞迴觸發器的值。</span><span class="sxs-lookup"><span data-stu-id="4871b-161">A value that indicates whether to enable recursive triggers.</span></span>

| <span data-ttu-id="4871b-162">值</span><span class="sxs-lookup"><span data-stu-id="4871b-162">Value</span></span> | <span data-ttu-id="4871b-163">描述</span><span class="sxs-lookup"><span data-stu-id="4871b-163">Description</span></span>                                                                 |
| ----- | --------------------------------------------------------------------------- |
| <span data-ttu-id="4871b-164">True</span><span class="sxs-lookup"><span data-stu-id="4871b-164">True</span></span>  | <span data-ttu-id="4871b-165">打開`PRAGMA recursive_triggers`連接後立即發送。</span><span class="sxs-lookup"><span data-stu-id="4871b-165">Sends `PRAGMA recursive_triggers` immediately after opening the connection.</span></span> |
| <span data-ttu-id="4871b-166">False</span><span class="sxs-lookup"><span data-stu-id="4871b-166">False</span></span> | <span data-ttu-id="4871b-167">不發送`PRAGMA recursive_triggers`。</span><span class="sxs-lookup"><span data-stu-id="4871b-167">Doesn't send `PRAGMA recursive_triggers`.</span></span> <span data-ttu-id="4871b-168">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="4871b-168">This is the default.</span></span>              |

## <a name="connection-string-builder"></a><span data-ttu-id="4871b-169">連接字串產生器</span><span class="sxs-lookup"><span data-stu-id="4871b-169">Connection string builder</span></span>

<span data-ttu-id="4871b-170">可以使用<xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder>作為創建連接字串的強型別方法。</span><span class="sxs-lookup"><span data-stu-id="4871b-170">You can use <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> as a strongly typed way of creating connection strings.</span></span> <span data-ttu-id="4871b-171">它還可用於防止連接字串注入攻擊。</span><span class="sxs-lookup"><span data-stu-id="4871b-171">It can also be used to prevent connection string injection attacks.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="examples"></a><span data-ttu-id="4871b-172">範例</span><span class="sxs-lookup"><span data-stu-id="4871b-172">Examples</span></span>

### <a name="basic"></a><span data-ttu-id="4871b-173">基本</span><span class="sxs-lookup"><span data-stu-id="4871b-173">Basic</span></span>

<span data-ttu-id="4871b-174">具有共用緩存的基本連接字串，用於改進併發性。</span><span class="sxs-lookup"><span data-stu-id="4871b-174">A basic connection string with a shared cache for improved concurrency.</span></span>

```ConnectionString
Data Source=Application.db;Cache=Shared
```

### <a name="encrypted"></a><span data-ttu-id="4871b-175">已加密</span><span class="sxs-lookup"><span data-stu-id="4871b-175">Encrypted</span></span>

<span data-ttu-id="4871b-176">加密的資料庫。</span><span class="sxs-lookup"><span data-stu-id="4871b-176">An encrypted database.</span></span>

```ConnectionString
Data Source=Encrypted.db;Password=MyEncryptionKey
```

### <a name="read-only"></a><span data-ttu-id="4871b-177">唯讀</span><span class="sxs-lookup"><span data-stu-id="4871b-177">Read-only</span></span>

<span data-ttu-id="4871b-178">應用無法修改的唯讀資料庫。</span><span class="sxs-lookup"><span data-stu-id="4871b-178">A read-only database that cannot be modified by the app.</span></span>

```ConnectionString
Data Source=Reference.db;Mode=ReadOnly
```

### <a name="in-memory"></a><span data-ttu-id="4871b-179">記憶體內</span><span class="sxs-lookup"><span data-stu-id="4871b-179">In-memory</span></span>

<span data-ttu-id="4871b-180">專用記憶體資料庫。</span><span class="sxs-lookup"><span data-stu-id="4871b-180">A private, in-memory database.</span></span>

```ConnectionString
Data Source=:memory:
```

### <a name="sharable-in-memory"></a><span data-ttu-id="4871b-181">可共用記憶體</span><span class="sxs-lookup"><span data-stu-id="4871b-181">Sharable in-memory</span></span>

<span data-ttu-id="4871b-182">由名稱 *"可共用*"標識的可共用記憶體資料庫。</span><span class="sxs-lookup"><span data-stu-id="4871b-182">A sharable, in-memory database identified by the name *Sharable*.</span></span>

```ConnectionString
Data Source=Sharable;Mode=Memory;Cache=Shared
```

## <a name="see-also"></a><span data-ttu-id="4871b-183">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4871b-183">See also</span></span>

* [<span data-ttu-id="4871b-184">ADO.NET 中的連接字串</span><span class="sxs-lookup"><span data-stu-id="4871b-184">Connection Strings in ADO.NET</span></span>](../../../framework/data/adonet/connection-strings.md)
* [<span data-ttu-id="4871b-185">記憶體中資料庫</span><span class="sxs-lookup"><span data-stu-id="4871b-185">In-Memory databases</span></span>](in-memory-databases.md)
* [<span data-ttu-id="4871b-186">交易</span><span class="sxs-lookup"><span data-stu-id="4871b-186">Transactions</span></span>](transactions.md)
