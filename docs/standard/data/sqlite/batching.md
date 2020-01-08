---
title: 批次處理
ms.date: 12/13/2019
description: 瞭解如何在單一命令中執行 SQL 語句的批次。
ms.openlocfilehash: 0799784471520bb279db6a4b5879ad30945bdebb
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447052"
---
# <a name="batching"></a>批次處理

SQLite 原本就不支援將 SQL 語句一起批次處理成單一命令。 但是因為沒有涉及的網路，所以還是不會真正協助效能。 不過，Sqlite 會將語句批次處理實作為便利，使其行為更像其他 ADO.NET 提供者。

呼叫 <xref:System.Data.Common.DbCommand.ExecuteReader%2A?displayProperty=nameWithType>時，會執行語句，直到第一個傳回結果的語句為止。 呼叫 <xref:System.Data.Common.DbDataReader.NextResult%2A?displayProperty=nameWithType> 會繼續執行語句，直到下一個傳回結果，或直到到達批次結尾為止。 呼叫 <xref:System.Data.Common.DbDataReader.Dispose%2A?displayProperty=nameWithType> 或 <xref:System.Data.Common.DbDataReader.Close%2A> 會執行 `NextResult()`尚未使用的任何剩餘語句。 如果您未處置資料讀取器，完成項會嘗試執行其餘的語句，但它遇到的任何錯誤都會被忽略。 因此，在使用批次時，請務必處置 `DbDataReader` 物件。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BatchingSample/Program.cs?name=snippet_Batching)]

## <a name="see-also"></a>請參閱

* [Bulk Insert](bulk-insert.md)
