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
# <a name="database-errors"></a>資料庫錯誤

遇到 SQLite 錯誤時，會擲回 <xref:Microsoft.Data.Sqlite.SqliteException>。 訊息是由 SQLite 所提供。 `SqliteErrorCode` 和 `SqliteExtendedErrorCode` 屬性包含錯誤的 SQLite[結果碼](https://www.sqlite.org/rescode.html)。

任何時間都可能發生錯誤。 Sqlite 會與原生的 SQLite 程式庫互動。 下列清單顯示錯誤可能發生的常見案例：

* 開啟連接。
* 開始交易。
* 執行命令。
* 呼叫 <xref:Microsoft.Data.Sqlite.SqliteDataReader.NextResult%2A>。

請仔細考慮您的應用程式將如何處理這些錯誤。

## <a name="locking-retries-and-timeouts"></a>鎖定、重試和超時

SQLite 在鎖定資料表和資料庫檔案時非常積極。 如果您的應用程式啟用任何並行資料庫存取，您可能會遇到忙碌和鎖定的錯誤。 您可以使用[共用](connection-strings.md#cache)快取和預先[寫入記錄](async.md)來減輕許多錯誤。

每當 Microsoft Data Sqlite 遇到忙碌或鎖定的錯誤時，它會自動重試，直到成功或到達命令逾時為止。

您可以藉由設定 <xref:Microsoft.Data.Sqlite.SqliteCommand.CommandTimeout%2A>來增加命令的超時時間。 預設的超時時間為30秒。 `0` 的值表示沒有超時。

```csharp
// Retry for 60 seconds while locked
command.CommandTimeout = 60;
```

然後，Sqlite 有時需要建立隱含的命令物件。 例如，在 BeginTransaction 期間。 若要設定這些命令的超時時間，請使用 <xref:Microsoft.Data.Sqlite.SqliteConnection.DefaultTimeout%2A>。

```csharp
// Set the default timeout of all commands on this connection
connection.DefaultTimeout = 60;
```

## <a name="see-also"></a>請參閱

* [SQLite 錯誤碼](https://www.sqlite.org/rescode.html)
* [SQLite 中的檔案鎖定](https://www.sqlite.org/lockingv3.html)
* [共用-快取模式](https://www.sqlite.org/sharedcache.html)
* [預先寫入記錄](https://www.sqlite.org/wal.html)
