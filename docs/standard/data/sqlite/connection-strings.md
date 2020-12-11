---
title: 連接字串
ms.date: 12/08/2020
description: 支援的連接字串關鍵字和值。
ms.openlocfilehash: 35283664c4ac3985d4f517fde77644ab2a891120
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110737"
---
# <a name="connection-strings"></a><span data-ttu-id="c399e-103">連接字串</span><span class="sxs-lookup"><span data-stu-id="c399e-103">Connection strings</span></span>

<span data-ttu-id="c399e-104">連接字串是用來指定如何連接到資料庫。</span><span class="sxs-lookup"><span data-stu-id="c399e-104">A connection string is used to specify how to connect to the database.</span></span> <span data-ttu-id="c399e-105">ADO.NET 中的連接字串會遵循標準的 [語法](../../../framework/data/adonet/connection-strings.md) ，以分號分隔的關鍵字和值清單。</span><span class="sxs-lookup"><span data-stu-id="c399e-105">Connection strings in Microsoft.Data.Sqlite follow the standard [ADO.NET syntax](../../../framework/data/adonet/connection-strings.md) as a semicolon-separated list of keywords and values.</span></span>

## <a name="keywords"></a><span data-ttu-id="c399e-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="c399e-106">Keywords</span></span>

<span data-ttu-id="c399e-107">下列連接字串關鍵字可以搭配使用 Sqlite：</span><span class="sxs-lookup"><span data-stu-id="c399e-107">The following connection string keywords can be used with Microsoft.Data.Sqlite:</span></span>

### <a name="data-source"></a><span data-ttu-id="c399e-108">資料來源</span><span class="sxs-lookup"><span data-stu-id="c399e-108">Data source</span></span>

<span data-ttu-id="c399e-109">資料庫檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="c399e-109">The path to the database file.</span></span> <span data-ttu-id="c399e-110">沒有空格的 *DataSource* () 和 *Filename* 是這個關鍵字的別名。</span><span class="sxs-lookup"><span data-stu-id="c399e-110">*DataSource* (without a space) and *Filename* are aliases of this keyword.</span></span>

<span data-ttu-id="c399e-111">SQLite 會將路徑視為相對於目前工作目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="c399e-111">SQLite treats paths relative to the current working directory.</span></span> <span data-ttu-id="c399e-112">也可以指定絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="c399e-112">Absolute paths can also be specified.</span></span>

<span data-ttu-id="c399e-113">如果是 **空** 的，SQLite 會建立暫時的磁片上資料庫，當連接關閉時，就會刪除此資料庫。</span><span class="sxs-lookup"><span data-stu-id="c399e-113">If **empty**, SQLite creates a temporary on-disk database that's deleted when the connection is closed.</span></span>

<span data-ttu-id="c399e-114">如果 `:memory:` 為，則會使用記憶體內部資料庫。</span><span class="sxs-lookup"><span data-stu-id="c399e-114">If `:memory:`, an in-memory database is used.</span></span> <span data-ttu-id="c399e-115">如需詳細資訊，請參閱 [記憶體內部資料庫](in-memory-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="c399e-115">For more information, see [In-Memory databases](in-memory-databases.md).</span></span>

<span data-ttu-id="c399e-116">以替代字串開頭的路徑 `|DataDirectory|` 會被視為與相對路徑相同。</span><span class="sxs-lookup"><span data-stu-id="c399e-116">Paths that start with the `|DataDirectory|` substitution string are treated the same as relative paths.</span></span> <span data-ttu-id="c399e-117">如果設定，則會建立相對於 DataDirectory 應用程式域屬性值的路徑。</span><span class="sxs-lookup"><span data-stu-id="c399e-117">If set, paths are made relative to the DataDirectory application domain property value.</span></span>

<span data-ttu-id="c399e-118">此關鍵字也支援 [URI 檔案名](https://www.sqlite.org/uri.html)。</span><span class="sxs-lookup"><span data-stu-id="c399e-118">This keyword also supports [URI Filenames](https://www.sqlite.org/uri.html).</span></span>

### <a name="mode"></a><span data-ttu-id="c399e-119">[模式]</span><span class="sxs-lookup"><span data-stu-id="c399e-119">Mode</span></span>

<span data-ttu-id="c399e-120">連接模式。</span><span class="sxs-lookup"><span data-stu-id="c399e-120">The connection mode.</span></span>

| <span data-ttu-id="c399e-121">值</span><span class="sxs-lookup"><span data-stu-id="c399e-121">Value</span></span>           | <span data-ttu-id="c399e-122">說明</span><span class="sxs-lookup"><span data-stu-id="c399e-122">Description</span></span>                                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="c399e-123">ReadWriteCreate</span><span class="sxs-lookup"><span data-stu-id="c399e-123">ReadWriteCreate</span></span> | <span data-ttu-id="c399e-124">開啟資料庫進行讀取和寫入，如果不存在，則建立資料庫。</span><span class="sxs-lookup"><span data-stu-id="c399e-124">Opens the database for reading and writing, and creates it if it doesn't exist.</span></span> <span data-ttu-id="c399e-125">此為預設值。</span><span class="sxs-lookup"><span data-stu-id="c399e-125">This is the default.</span></span> |
| <span data-ttu-id="c399e-126">讀寫</span><span class="sxs-lookup"><span data-stu-id="c399e-126">ReadWrite</span></span>       | <span data-ttu-id="c399e-127">開啟資料庫進行讀取和寫入。</span><span class="sxs-lookup"><span data-stu-id="c399e-127">Opens the database for reading and writing.</span></span>                                                        |
| <span data-ttu-id="c399e-128">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="c399e-128">ReadOnly</span></span>        | <span data-ttu-id="c399e-129">以唯讀模式開啟資料庫。</span><span class="sxs-lookup"><span data-stu-id="c399e-129">Opens the database in read-only mode.</span></span>                                                              |
| <span data-ttu-id="c399e-130">記憶體</span><span class="sxs-lookup"><span data-stu-id="c399e-130">Memory</span></span>          | <span data-ttu-id="c399e-131">開啟記憶體中的資料庫。</span><span class="sxs-lookup"><span data-stu-id="c399e-131">Opens an in-memory database.</span></span>                                                                       |

### <a name="cache"></a><span data-ttu-id="c399e-132">快取</span><span class="sxs-lookup"><span data-stu-id="c399e-132">Cache</span></span>

<span data-ttu-id="c399e-133">連接所使用的快取模式。</span><span class="sxs-lookup"><span data-stu-id="c399e-133">The caching mode used by the connection.</span></span>

| <span data-ttu-id="c399e-134">值</span><span class="sxs-lookup"><span data-stu-id="c399e-134">Value</span></span>   | <span data-ttu-id="c399e-135">描述</span><span class="sxs-lookup"><span data-stu-id="c399e-135">Description</span></span>                                                                                    |
| ------- | ---------------------------------------------------------------------------------------------- |
| <span data-ttu-id="c399e-136">預設</span><span class="sxs-lookup"><span data-stu-id="c399e-136">Default</span></span> | <span data-ttu-id="c399e-137">使用基礎 SQLite 程式庫的預設模式。</span><span class="sxs-lookup"><span data-stu-id="c399e-137">Uses the default mode of the underlying SQLite library.</span></span> <span data-ttu-id="c399e-138">此為預設值。</span><span class="sxs-lookup"><span data-stu-id="c399e-138">This is the default.</span></span>                   |
| <span data-ttu-id="c399e-139">私人</span><span class="sxs-lookup"><span data-stu-id="c399e-139">Private</span></span> | <span data-ttu-id="c399e-140">每個連接都使用私用快取。</span><span class="sxs-lookup"><span data-stu-id="c399e-140">Each connection uses a private cache.</span></span>                                                          |
| <span data-ttu-id="c399e-141">共用</span><span class="sxs-lookup"><span data-stu-id="c399e-141">Shared</span></span>  | <span data-ttu-id="c399e-142">連接會共用快取。</span><span class="sxs-lookup"><span data-stu-id="c399e-142">Connections share a cache.</span></span> <span data-ttu-id="c399e-143">這個模式可以改變交易和表鎖的行為。</span><span class="sxs-lookup"><span data-stu-id="c399e-143">This mode can change the behavior of transaction and table locking.</span></span> |

### <a name="password"></a><span data-ttu-id="c399e-144">密碼</span><span class="sxs-lookup"><span data-stu-id="c399e-144">Password</span></span>

<span data-ttu-id="c399e-145">加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="c399e-145">The encryption key.</span></span> <span data-ttu-id="c399e-146">若有指定， `PRAGMA key` 會在開啟連接之後立即傳送。</span><span class="sxs-lookup"><span data-stu-id="c399e-146">When specified, `PRAGMA key` is sent immediately after opening the connection.</span></span>

> [!WARNING]
> <span data-ttu-id="c399e-147">當原生 SQLite 程式庫不支援加密時，密碼沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="c399e-147">Password has no effect when encryption isn't supported by the native SQLite library.</span></span>

> [!NOTE]
> <span data-ttu-id="c399e-148">在3.0 版中已新增 Password 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c399e-148">The Password keyword was added in version 3.0.</span></span>

### <a name="foreign-keys"></a><span data-ttu-id="c399e-149">外部索引鍵</span><span class="sxs-lookup"><span data-stu-id="c399e-149">Foreign Keys</span></span>

<span data-ttu-id="c399e-150">值，指出是否啟用外鍵條件約束。</span><span class="sxs-lookup"><span data-stu-id="c399e-150">A value indicating whether to enable foreign key constraints.</span></span>

> [!NOTE]
> <span data-ttu-id="c399e-151">在3.0 版中已加入外鍵關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c399e-151">The Foreign Keys keyword was added in version 3.0.</span></span>

| <span data-ttu-id="c399e-152">值</span><span class="sxs-lookup"><span data-stu-id="c399e-152">Value</span></span>   | <span data-ttu-id="c399e-153">描述</span><span class="sxs-lookup"><span data-stu-id="c399e-153">Description</span></span>
| ------- | --- |
| <span data-ttu-id="c399e-154">True</span><span class="sxs-lookup"><span data-stu-id="c399e-154">True</span></span>    | <span data-ttu-id="c399e-155">`PRAGMA foreign_keys = 1`在開啟連接之後立即傳送。</span><span class="sxs-lookup"><span data-stu-id="c399e-155">Sends `PRAGMA foreign_keys = 1` immediately after opening the connection.</span></span>
| <span data-ttu-id="c399e-156">否</span><span class="sxs-lookup"><span data-stu-id="c399e-156">False</span></span>   | <span data-ttu-id="c399e-157">`PRAGMA foreign_keys = 0`在開啟連接之後立即傳送。</span><span class="sxs-lookup"><span data-stu-id="c399e-157">Sends `PRAGMA foreign_keys = 0` immediately after opening the connection.</span></span>
| <span data-ttu-id="c399e-158">(空白)</span><span class="sxs-lookup"><span data-stu-id="c399e-158">(empty)</span></span> | <span data-ttu-id="c399e-159">不會傳送 `PRAGMA foreign_keys` 。</span><span class="sxs-lookup"><span data-stu-id="c399e-159">Doesn't send `PRAGMA foreign_keys`.</span></span> <span data-ttu-id="c399e-160">此為預設值。</span><span class="sxs-lookup"><span data-stu-id="c399e-160">This is the default.</span></span> |

<span data-ttu-id="c399e-161">如果 SQLITE_DEFAULT_FOREIGN_KEYS 用來編譯原生 SQLite 程式庫，則不需要啟用外鍵（例如 e_sqlite3）。</span><span class="sxs-lookup"><span data-stu-id="c399e-161">There's no need enable foreign keys if, like in e_sqlite3, SQLITE_DEFAULT_FOREIGN_KEYS was used to compile the native SQLite library.</span></span>

### <a name="recursive-triggers"></a><span data-ttu-id="c399e-162">遞迴觸發程式</span><span class="sxs-lookup"><span data-stu-id="c399e-162">Recursive triggers</span></span>

<span data-ttu-id="c399e-163">值，指出是否啟用遞迴觸發程式。</span><span class="sxs-lookup"><span data-stu-id="c399e-163">A value that indicates whether to enable recursive triggers.</span></span>

> [!NOTE]
> <span data-ttu-id="c399e-164">在3.0 版中已加入遞迴觸發程式關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c399e-164">The Recursive Triggers keyword was added in version 3.0.</span></span>

| <span data-ttu-id="c399e-165">值</span><span class="sxs-lookup"><span data-stu-id="c399e-165">Value</span></span> | <span data-ttu-id="c399e-166">描述</span><span class="sxs-lookup"><span data-stu-id="c399e-166">Description</span></span>                                                                 |
| ----- | --------------------------------------------------------------------------- |
| <span data-ttu-id="c399e-167">True</span><span class="sxs-lookup"><span data-stu-id="c399e-167">True</span></span>  | <span data-ttu-id="c399e-168">`PRAGMA recursive_triggers`在開啟連接之後立即傳送。</span><span class="sxs-lookup"><span data-stu-id="c399e-168">Sends `PRAGMA recursive_triggers` immediately after opening the connection.</span></span> |
| <span data-ttu-id="c399e-169">否</span><span class="sxs-lookup"><span data-stu-id="c399e-169">False</span></span> | <span data-ttu-id="c399e-170">不會傳送 `PRAGMA recursive_triggers` 。</span><span class="sxs-lookup"><span data-stu-id="c399e-170">Doesn't send `PRAGMA recursive_triggers`.</span></span> <span data-ttu-id="c399e-171">此為預設值。</span><span class="sxs-lookup"><span data-stu-id="c399e-171">This is the default.</span></span>              |

## <a name="connection-string-builder"></a><span data-ttu-id="c399e-172">連接字串產生器</span><span class="sxs-lookup"><span data-stu-id="c399e-172">Connection string builder</span></span>

<span data-ttu-id="c399e-173">您可以使用 <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> 做為建立連接字串的強型別方法。</span><span class="sxs-lookup"><span data-stu-id="c399e-173">You can use <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> as a strongly typed way of creating connection strings.</span></span> <span data-ttu-id="c399e-174">它也可以用來防止連接字串插入式攻擊。</span><span class="sxs-lookup"><span data-stu-id="c399e-174">It can also be used to prevent connection string injection attacks.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="examples"></a><span data-ttu-id="c399e-175">範例</span><span class="sxs-lookup"><span data-stu-id="c399e-175">Examples</span></span>

### <a name="basic"></a><span data-ttu-id="c399e-176">基本</span><span class="sxs-lookup"><span data-stu-id="c399e-176">Basic</span></span>

<span data-ttu-id="c399e-177">具有共用快取以改善平行存取的基本連接字串。</span><span class="sxs-lookup"><span data-stu-id="c399e-177">A basic connection string with a shared cache for improved concurrency.</span></span>

```connectionstring
Data Source=Application.db;Cache=Shared
```

### <a name="encrypted"></a><span data-ttu-id="c399e-178">已加密</span><span class="sxs-lookup"><span data-stu-id="c399e-178">Encrypted</span></span>

<span data-ttu-id="c399e-179">加密的資料庫。</span><span class="sxs-lookup"><span data-stu-id="c399e-179">An encrypted database.</span></span>

```connectionstring
Data Source=Encrypted.db;Password=MyEncryptionKey
```

### <a name="read-only"></a><span data-ttu-id="c399e-180">唯讀</span><span class="sxs-lookup"><span data-stu-id="c399e-180">Read-only</span></span>

<span data-ttu-id="c399e-181">應用程式無法修改的唯讀資料庫。</span><span class="sxs-lookup"><span data-stu-id="c399e-181">A read-only database that cannot be modified by the app.</span></span>

```connectionstring
Data Source=Reference.db;Mode=ReadOnly
```

### <a name="in-memory"></a><span data-ttu-id="c399e-182">記憶體內</span><span class="sxs-lookup"><span data-stu-id="c399e-182">In-memory</span></span>

<span data-ttu-id="c399e-183">私用記憶體中的資料庫。</span><span class="sxs-lookup"><span data-stu-id="c399e-183">A private, in-memory database.</span></span>

```connectionstring
Data Source=:memory:
```

### <a name="sharable-in-memory"></a><span data-ttu-id="c399e-184">可在記憶體中共用</span><span class="sxs-lookup"><span data-stu-id="c399e-184">Sharable in-memory</span></span>

<span data-ttu-id="c399e-185">可共用的記憶體內部資料庫，以可 *共用* 的名稱識別。</span><span class="sxs-lookup"><span data-stu-id="c399e-185">A sharable, in-memory database identified by the name *Sharable*.</span></span>

```connectionstring
Data Source=Sharable;Mode=Memory;Cache=Shared
```

## <a name="see-also"></a><span data-ttu-id="c399e-186">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c399e-186">See also</span></span>

* [<span data-ttu-id="c399e-187">ADO.NET 中的連接字串</span><span class="sxs-lookup"><span data-stu-id="c399e-187">Connection Strings in ADO.NET</span></span>](../../../framework/data/adonet/connection-strings.md)
* [<span data-ttu-id="c399e-188">記憶體內部資料庫</span><span class="sxs-lookup"><span data-stu-id="c399e-188">In-Memory databases</span></span>](in-memory-databases.md)
* [<span data-ttu-id="c399e-189">交易</span><span class="sxs-lookup"><span data-stu-id="c399e-189">Transactions</span></span>](transactions.md)
