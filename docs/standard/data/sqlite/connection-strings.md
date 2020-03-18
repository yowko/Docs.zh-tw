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
# <a name="connection-strings"></a>連接字串

連接字串用於指定如何連接到資料庫。 Microsoft.Data.Sqlite 中的連接字串遵循標準[ADO.NET語法](../../../framework/data/adonet/connection-strings.md)作為關鍵字和值的分號分隔清單。

## <a name="keywords"></a>關鍵字

以下連接字串關鍵字可用於 Microsoft.Data.Sqlite：

### <a name="data-source"></a>資料來源

資料庫檔案的路徑。 *資料來源*（沒有空格）和*檔案名*是此關鍵字的別名。

SQLite 處理相對於當前工作目錄的路徑。 也可以指定絕對路徑。

如果**為空**，SQLite 將創建一個臨時磁片資料庫，該資料庫在連接關閉時被刪除。

如果`:memory:`使用 記憶體中資料庫。 有關詳細資訊，請參閱[記憶體中資料庫](in-memory-databases.md)。

以替換字串開頭的`|DataDirectory|`路徑與相對路徑相同。 如果設置，則根據 DataDirectory 應用程式域屬性值製作路徑。

此關鍵字還支援[URI 檔案名](https://www.sqlite.org/uri.html)。

### <a name="mode"></a>[模式]

連接模式。

| 值           | 描述                                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------- |
| 讀取寫入創建 | 打開資料庫進行讀取和寫入，如果資料庫不存在，請創建它。 這是預設值。 |
| 讀寫       | 打開用於讀取和寫入的資料庫。                                                        |
| 唯讀        | 以唯讀模式打開資料庫。                                                              |
| 記憶體          | 打開記憶體中資料庫。                                                                       |

### <a name="cache"></a>快取

連接使用的緩存模式。

| 值   | 描述                                                                                    |
| ------- | ---------------------------------------------------------------------------------------------- |
| 預設 | 使用基礎 SQLite 庫的預設模式。 這是預設值。                   |
| Private | 每個連接都使用專用緩存。                                                          |
| 共用  | 連接共用緩存。 此模式可以更改事務和表鎖定的行為。 |

### <a name="password"></a>密碼

加密金鑰。 指定後，`PRAGMA key`將立即在打開連接後發送。

> [!WARNING]
> 當本機 SQLite 庫不支援加密時，密碼不起作用。

### <a name="foreign-keys"></a>外部索引鍵

指示是否啟用外鍵約束的值。

| 值   | 描述
| ------- | --- |
| True    | 打開`PRAGMA foreign_keys = 1`連接後立即發送。
| False   | 打開`PRAGMA foreign_keys = 0`連接後立即發送。
| (空白) | 不發送`PRAGMA foreign_keys`。 這是預設值。 |

e_sqlite3 如果SQLITE_DEFAULT_FOREIGN_KEYS用於編譯本機 SQLite 庫，則無需啟用外鍵。

### <a name="recursive-triggers"></a>遞迴觸發器

指示是否啟用遞迴觸發器的值。

| 值 | 描述                                                                 |
| ----- | --------------------------------------------------------------------------- |
| True  | 打開`PRAGMA recursive_triggers`連接後立即發送。 |
| False | 不發送`PRAGMA recursive_triggers`。 這是預設值。              |

## <a name="connection-string-builder"></a>連接字串產生器

可以使用<xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder>作為創建連接字串的強型別方法。 它還可用於防止連接字串注入攻擊。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="examples"></a>範例

### <a name="basic"></a>基本

具有共用緩存的基本連接字串，用於改進併發性。

```ConnectionString
Data Source=Application.db;Cache=Shared
```

### <a name="encrypted"></a>已加密

加密的資料庫。

```ConnectionString
Data Source=Encrypted.db;Password=MyEncryptionKey
```

### <a name="read-only"></a>唯讀

應用無法修改的唯讀資料庫。

```ConnectionString
Data Source=Reference.db;Mode=ReadOnly
```

### <a name="in-memory"></a>記憶體內

專用記憶體資料庫。

```ConnectionString
Data Source=:memory:
```

### <a name="sharable-in-memory"></a>可共用記憶體

由名稱 *"可共用*"標識的可共用記憶體資料庫。

```ConnectionString
Data Source=Sharable;Mode=Memory;Cache=Shared
```

## <a name="see-also"></a>另請參閱

* [ADO.NET 中的連接字串](../../../framework/data/adonet/connection-strings.md)
* [記憶體中資料庫](in-memory-databases.md)
* [交易](transactions.md)
