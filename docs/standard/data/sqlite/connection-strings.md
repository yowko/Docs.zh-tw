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
# <a name="connection-strings"></a>連接字串

連接字串是用來指定如何連接到資料庫。 ADO.NET 中的連接字串會遵循標準的 [語法](../../../framework/data/adonet/connection-strings.md) ，以分號分隔的關鍵字和值清單。

## <a name="keywords"></a>關鍵字

下列連接字串關鍵字可以搭配使用 Sqlite：

### <a name="data-source"></a>資料來源

資料庫檔案的路徑。 沒有空格的 *DataSource* () 和 *Filename* 是這個關鍵字的別名。

SQLite 會將路徑視為相對於目前工作目錄的路徑。 也可以指定絕對路徑。

如果是 **空** 的，SQLite 會建立暫時的磁片上資料庫，當連接關閉時，就會刪除此資料庫。

如果 `:memory:` 為，則會使用記憶體內部資料庫。 如需詳細資訊，請參閱 [記憶體內部資料庫](in-memory-databases.md)。

以替代字串開頭的路徑 `|DataDirectory|` 會被視為與相對路徑相同。 如果設定，則會建立相對於 DataDirectory 應用程式域屬性值的路徑。

此關鍵字也支援 [URI 檔案名](https://www.sqlite.org/uri.html)。

### <a name="mode"></a>[模式]

連接模式。

| 值           | 說明                                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------- |
| ReadWriteCreate | 開啟資料庫進行讀取和寫入，如果不存在，則建立資料庫。 此為預設值。 |
| 讀寫       | 開啟資料庫進行讀取和寫入。                                                        |
| ReadOnly        | 以唯讀模式開啟資料庫。                                                              |
| 記憶體          | 開啟記憶體中的資料庫。                                                                       |

### <a name="cache"></a>快取

連接所使用的快取模式。

| 值   | 描述                                                                                    |
| ------- | ---------------------------------------------------------------------------------------------- |
| 預設 | 使用基礎 SQLite 程式庫的預設模式。 此為預設值。                   |
| 私人 | 每個連接都使用私用快取。                                                          |
| 共用  | 連接會共用快取。 這個模式可以改變交易和表鎖的行為。 |

### <a name="password"></a>密碼

加密金鑰。 若有指定， `PRAGMA key` 會在開啟連接之後立即傳送。

> [!WARNING]
> 當原生 SQLite 程式庫不支援加密時，密碼沒有任何作用。

> [!NOTE]
> 在3.0 版中已新增 Password 關鍵字。

### <a name="foreign-keys"></a>外部索引鍵

值，指出是否啟用外鍵條件約束。

> [!NOTE]
> 在3.0 版中已加入外鍵關鍵字。

| 值   | 描述
| ------- | --- |
| True    | `PRAGMA foreign_keys = 1`在開啟連接之後立即傳送。
| 否   | `PRAGMA foreign_keys = 0`在開啟連接之後立即傳送。
| (空白) | 不會傳送 `PRAGMA foreign_keys` 。 此為預設值。 |

如果 SQLITE_DEFAULT_FOREIGN_KEYS 用來編譯原生 SQLite 程式庫，則不需要啟用外鍵（例如 e_sqlite3）。

### <a name="recursive-triggers"></a>遞迴觸發程式

值，指出是否啟用遞迴觸發程式。

> [!NOTE]
> 在3.0 版中已加入遞迴觸發程式關鍵字。

| 值 | 描述                                                                 |
| ----- | --------------------------------------------------------------------------- |
| True  | `PRAGMA recursive_triggers`在開啟連接之後立即傳送。 |
| 否 | 不會傳送 `PRAGMA recursive_triggers` 。 此為預設值。              |

## <a name="connection-string-builder"></a>連接字串產生器

您可以使用 <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> 做為建立連接字串的強型別方法。 它也可以用來防止連接字串插入式攻擊。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="examples"></a>範例

### <a name="basic"></a>基本

具有共用快取以改善平行存取的基本連接字串。

```connectionstring
Data Source=Application.db;Cache=Shared
```

### <a name="encrypted"></a>已加密

加密的資料庫。

```connectionstring
Data Source=Encrypted.db;Password=MyEncryptionKey
```

### <a name="read-only"></a>唯讀

應用程式無法修改的唯讀資料庫。

```connectionstring
Data Source=Reference.db;Mode=ReadOnly
```

### <a name="in-memory"></a>記憶體內

私用記憶體中的資料庫。

```connectionstring
Data Source=:memory:
```

### <a name="sharable-in-memory"></a>可在記憶體中共用

可共用的記憶體內部資料庫，以可 *共用* 的名稱識別。

```connectionstring
Data Source=Sharable;Mode=Memory;Cache=Shared
```

## <a name="see-also"></a>另請參閱

* [ADO.NET 中的連接字串](../../../framework/data/adonet/connection-strings.md)
* [記憶體內部資料庫](in-memory-databases.md)
* [交易](transactions.md)
