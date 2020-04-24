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
# <a name="transactions"></a>交易

交易可讓您將多個 SQL 語句組成單一工作單位，並以一個不可部分完成的單位認可到資料庫。 如果交易中的任何語句失敗，則可以復原先前語句所做的變更。 當交易啟動時，資料庫的初始狀態會保留下來。 當一次對資料庫進行許多變更時，使用交易也可以改善 SQLite 上的效能。

## <a name="concurrency"></a>並行

在 SQLite 中，一次只能有一個交易在資料庫中有暫止的變更。 因此，對的呼叫<xref:Microsoft.Data.Sqlite.SqliteConnection.BeginTransaction%2A>和`Execute`方法可能會在<xref:Microsoft.Data.Sqlite.SqliteCommand>其他交易花費太長的時間才能完成。

如需有關鎖定、重試和超時的詳細資訊，請參閱[資料庫錯誤](database-errors.md)。

## <a name="isolation-levels"></a>隔離層級

根據預設，SQLite 中的交易是**可**序列化的。 此隔離等級可確保在交易內進行的任何變更都完全隔離。 在交易外部執行的其他語句不會受到交易變更的影響。

SQLite 也支援使用共用快取時的**讀取未**認可。 此層級允許中途讀取、不可重複讀取和幻像：

- 當某筆交易中的暫止變更由交易以外的查詢傳回時，就會發生中途*讀取*，但會回復交易中的變更。 結果會包含從未實際認可到資料庫的資料。

- 當交易查詢相同的資料列兩次時，就會發生*不可重複讀取*，但結果會不同，因為另一個交易的兩個查詢之間有變更。

- *幻像*是在交易期間變更或加入以符合查詢 where 子句的資料列。 如果允許的話，相同的查詢在相同交易中執行兩次時，可能會傳回不同的資料列。

Sqlite 會將傳遞至<xref:Microsoft.Data.Sqlite.SqliteConnection.BeginTransaction%2A>的 IsolationLevel 視為最小層級。 實際的隔離等級會升級為讀取未認可或可序列化。

下列程式碼會模擬中途讀取。 請注意，連接字串必須包含`Cache=Shared`。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DirtyReadSample/Program.cs?name=snippet_DirtyRead)]
