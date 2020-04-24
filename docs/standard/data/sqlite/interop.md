---
title: 互通性
ms.date: 12/13/2019
description: 瞭解如何與其他 SQLite 程式庫相交互操作。
ms.openlocfilehash: 486e2a8e00999b8ebe9c85a5fcc1539c514676d3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447234"
---
# <a name="interoperability"></a>互通性

Sqlite 會使用 SQLitePCLRaw 與原生 SQLite 程式庫互動。 SQLitePCLRaw 透過原生 SQLite API 提供精簡型 .NET API。 SqliteConnection 和 SqliteDataReader 提供基礎 SQLitePCLRaw 物件的存取權，讓您可以直接呼叫這些 Api。

下列範例示範如何呼叫`sqlite3_trace` ，以將已執行的 SQL 語句寫入主控台：

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/InteropSample/Program.cs?name=snippet_Trace)]

下列範例顯示呼叫`sqlite3_stmt_status` ，以查看有多少 SQLite 虛擬機器會將 SQL 語句編譯成：

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/InteropSample/Program.cs?name=snippet_StatementStatus)]

SQLitePCLRaw 物件甚至會公開原生物件的指標，讓您可以 P/Invoke 其他原生 SQLite Api。
