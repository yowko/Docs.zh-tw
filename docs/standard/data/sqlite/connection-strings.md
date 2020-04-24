---
title: 連接字串
ms.date: 12/13/2019
description: 連接字串支援的關鍵字和值。
ms.openlocfilehash: bb54d152bac62a86c2a49192cf678a745159164e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400446"
---
# <a name="connection-strings"></a>連接字串

連接字串是用來指定如何連接到資料庫。 在 Microsoft 中的連接字串會遵循標準[ADO.NET 語法](../../../framework/data/adonet/connection-strings.md)，做為關鍵字和值的分號分隔清單。

## <a name="keywords"></a>關鍵字

下列連接字串關鍵字可與 Microsoft 一起使用。 Sqlite：

### <a name="data-source"></a>資料來源

資料庫檔案的路徑。 *DataSource* （不含空格）和*Filename*是此關鍵字的別名。

SQLite 會對待相對於目前工作目錄的路徑。 也可以指定絕對路徑。

如果是**空**的，SQLite 會在關閉連線時，建立已刪除的暫存磁片資料庫。

如果`:memory:`為，則會使用記憶體內部資料庫。 如需詳細資訊，請參閱[記憶體內部資料庫](in-memory-databases.md)。

以`|DataDirectory|`替代字串開頭的路徑會被視為相對路徑。 如果設定，則會建立相對於 DataDirectory 應用程式域屬性值的路徑。

此關鍵字也支援[URI 檔案名](https://www.sqlite.org/uri.html)。

### <a name="mode"></a>[模式]

連接模式。

| 值           | 說明                                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------- |
| ReadWriteCreate | 開啟資料庫進行讀取和寫入，如果不存在，則建立它。 這是預設值。 |
| 讀寫       | 開啟資料庫進行讀取和寫入。                                                        |
| 唯讀        | 以唯讀模式開啟資料庫。                                                              |
| 記憶體          | 開啟記憶體內部資料庫。                                                                       |

### <a name="cache"></a>快取

連接所使用的快取模式。

| 值   | 描述                                                                                    |
| ------- | ---------------------------------------------------------------------------------------------- |
| 預設 | 使用基礎 SQLite 程式庫的預設模式。 這是預設值。                   |
| Private | 每個連接都會使用私用快取。                                                          |
| 共用  | 連接會共用快取。 此模式可以變更交易和表鎖定的行為。 |

### <a name="password"></a>密碼

加密金鑰。 當指定時`PRAGMA key` ，會在開啟連接之後立即傳送。

> [!WARNING]
> 當原生 SQLite 程式庫不支援加密時，Password 不會有任何作用。

### <a name="foreign-keys"></a>外部索引鍵

值，指出是否啟用外鍵條件約束。

| 值   | 說明
| ------- | --- |
| True    | 在`PRAGMA foreign_keys = 1`開啟連接之後立即傳送。
| False   | 在`PRAGMA foreign_keys = 0`開啟連接之後立即傳送。
| (空白) | 不會`PRAGMA foreign_keys`傳送。 這是預設值。 |

不需要啟用外鍵，如 e_sqlite3 中，SQLITE_DEFAULT_FOREIGN_KEYS 用來編譯原生 SQLite 程式庫。

### <a name="recursive-triggers"></a>遞迴觸發程式

值，指出是否要啟用遞迴觸發程式。

| 值 | 說明                                                                 |
| ----- | --------------------------------------------------------------------------- |
| True  | 在`PRAGMA recursive_triggers`開啟連接之後立即傳送。 |
| False | 不會`PRAGMA recursive_triggers`傳送。 這是預設值。              |

## <a name="connection-string-builder"></a>連接字串產生器

您可以使用<xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder>做為建立連接字串的強型別方式。 它也可以用來防止連接字串插入式攻擊。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="examples"></a>範例

### <a name="basic"></a>基本

具有共用快取以改善並行的基本連接字串。

```ConnectionString
Data Source=Application.db;Cache=Shared
```

### <a name="encrypted"></a>已加密

加密的資料庫。

```ConnectionString
Data Source=Encrypted.db;Password=MyEncryptionKey
```

### <a name="read-only"></a>唯讀

應用程式無法修改的唯讀資料庫。

```ConnectionString
Data Source=Reference.db;Mode=ReadOnly
```

### <a name="in-memory"></a>記憶體內

私用記憶體內部資料庫。

```ConnectionString
Data Source=:memory:
```

### <a name="sharable-in-memory"></a>可在記憶體中共用

由可*共用*的名稱所識別的可共用記憶體內部資料庫。

```ConnectionString
Data Source=Sharable;Mode=Memory;Cache=Shared
```

## <a name="see-also"></a>另請參閱

* [ADO.NET 中的連接字串](../../../framework/data/adonet/connection-strings.md)
* [記憶體內部資料庫](in-memory-databases.md)
* [異動](transactions.md)
