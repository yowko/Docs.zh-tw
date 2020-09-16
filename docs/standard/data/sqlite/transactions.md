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
# <a name="transactions"></a>交易

交易可讓您將多個 SQL 語句群組成單一工作單位，並認可至資料庫做為一個不可部分完成的單位。 如果交易中有任何語句失敗，則可以回復前一個語句所做的變更。 當交易開始時，資料庫的初始狀態會保留下來。 在對資料庫進行許多變更時，使用交易也可以改善 SQLite 的效能。

## <a name="concurrency"></a>並行

在 SQLite 中，一次只允許一個交易在資料庫中暫止變更。 基於這個原因， <xref:Microsoft.Data.Sqlite.SqliteConnection.BeginTransaction%2A> `Execute` <xref:Microsoft.Data.Sqlite.SqliteCommand> 如果另一個交易花太多時間來完成，的呼叫和方法可能會過期。

如需鎖定、重試和超時的詳細資訊，請參閱 [資料庫錯誤](database-errors.md)。

## <a name="isolation-levels"></a>隔離層級

在 SQLite 中，交易預設為 **可** 序列化。 這種隔離等級保證在交易內進行的任何變更都是完全隔離的。 在交易以外執行的其他語句不會受交易的變更影響。

使用共用快取時，SQLite 也支援 **讀取未** 認可。 此層級允許中途讀取、不可重複讀取和幻像：

- 在交易以外的查詢傳回某一交易的暫止變更時，就會發生中途 *讀取* ，但交易中的變更會回復。 結果包含從未實際認可至資料庫的資料。

- 當交易查詢相同的資料列兩次時，會發生 *不可重複讀取* ，但結果會不同，因為另一個交易的兩個查詢之間有變更。

- *幻像* 是在交易期間變更或加入以符合查詢 where 子句的資料列。 如果允許，相同的查詢在相同交易中執行兩次時，可能會傳回不同的資料列。

IsolationLevel 會將傳遞至的視為 <xref:Microsoft.Data.Sqlite.SqliteConnection.BeginTransaction%2A> 最小層級。 實際的隔離等級將會升級為讀取未認可或可序列化。

下列程式碼會模擬中途讀取。 請注意，連接字串必須包含 `Cache=Shared` 。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DirtyReadSample/Program.cs?name=snippet_DirtyRead)]

## <a name="deferred-transactions"></a>延遲交易

從5.0 版開始，可以延後交易。 這會延遲在資料庫中建立實際的交易，直到第一個命令執行為止。 它也會讓交易從讀取交易逐漸升級到其命令所需的寫入交易。 這有助於在交易期間啟用資料庫的平行存取。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DeferredTransactionSample/Program.cs?name=snippet_DeferredTransaction)]

> [!WARNING]
> 延遲交易內的命令可能會在資料庫被鎖定時，將交易從讀取交易升級到寫入交易時失敗。 當發生這種情況時，應用程式就必須重試整個交易。
