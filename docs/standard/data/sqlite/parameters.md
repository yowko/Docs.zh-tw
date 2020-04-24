---
title: 參數
ms.date: 12/13/2019
description: 瞭解如何使用 SQL 參數。
ms.openlocfilehash: 1d2f818ad392a919faedd785394de28a9c6f56c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400453"
---
# <a name="parameters"></a>參數

參數是用來防止 SQL 插入式攻擊。 請使用參數來確保輸入只會被視為常值，而且永遠不會執行，而不會將使用者輸入與 SQL 語句串連。 在 SQLite 中，參數通常可在 SQL 語句中允許常值的任何位置使用。

參數的前面可以是`:`、 `@`或。 `$`

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_Parameter)]

如需 .NET 值如何對應至 SQLite 值的詳細資訊，請參閱[資料類型](types.md)。

## <a name="truncation"></a>截斷

使用<xref:Microsoft.Data.Sqlite.SqliteParameter.Size>屬性來截斷文字和 BLOB 值。

```csharp
// Truncate name to 30 characters
command.Parameters.AddWithValue("$name", name).Length = 30;
```

## <a name="alternative-types"></a>替代類型

有時候，您可能會想要使用替代的 SQLite 類型。 藉由設定<xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType>屬性來執行此動作。

您可以使用下列替代型別對應。 如需預設對應，請參閱[資料類型](types.md)。

| 值          | SqliteType | 備註          |
| -------------- | ---------- | ---------------- |
| Char           | 整數    | UTF-16           |
| Datetime       | Real       | Julian 日值 |
| DateTimeOffset | Real       | Julian 日值 |
| Guid           | Blob       |                  |
| TimeSpan       | Real       | 以天為單位          |

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_SqliteType)]

## <a name="output-parameters"></a>輸出參數

SQLite 不支援輸出參數。 改為傳回查詢結果中的值。

## <a name="see-also"></a>另請參閱

* [資料類型](types.md)
