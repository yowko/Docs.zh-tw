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

參數用於防止 SQL 注入攻擊。 使用參數確保輸入僅被視為文本值，並且永遠不會執行，而不是將使用者輸入與 SQL 語句串聯。 在 SQLite 中，參數通常允許在 SQL 語句中允許文本的任何位置。

參數可以使用`:`或`@``$`的預綴。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_Parameter)]

有關如何將 .NET 值對應到 SQLite 值的詳細資訊，請參閱[資料類型](types.md)。

## <a name="truncation"></a>截斷

使用<xref:Microsoft.Data.Sqlite.SqliteParameter.Size>屬性截截 TEXT 和 BLOB 值。

```csharp
// Truncate name to 30 characters
command.Parameters.AddWithValue("$name", name).Length = 30;
```

## <a name="alternative-types"></a>替代類型

有時，您可能需要使用替代 SQLite 類型。 通過設置屬性來<xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType>執行此操作。

可以使用以下替代類型映射。 有關預設映射，請參閱[資料類型](types.md)。

| 值          | Sqlite 類型 | 備註          |
| -------------- | ---------- | ---------------- |
| Char           | 整數     | UTF-16           |
| Datetime       | Real       | 朱利安日值 |
| DateTimeOffset | Real       | 朱利安日值 |
| Guid           | Blob       |                  |
| TimeSpan       | Real       | 在幾天內          |

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_SqliteType)]

## <a name="output-parameters"></a>輸出參數

SQLite 不支援輸出參數。 返回查詢結果中的值。

## <a name="see-also"></a>另請參閱

* [資料類型](types.md)
