---
title: 資料類型
ms.date: 12/13/2019
description: 描述支持的數據類型及其周圍的一些限制。
ms.openlocfilehash: a11ff382f80cd979506d6195c299c8234c3eb8ea
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389048"
---
# <a name="data-types"></a>資料類型

SQLite 只有四種原始數據類型:INTEGER、真實、文本和 BLOB。 將資料庫值作為返回的`object`API 將僅返回這四種類型之一。 Microsoft.Data.Sqlite 支援其他 .NET 類型,但最終在這些類型的和四種基元類型之一之間強制使用值。

| .NET           | SQLite  | 備註                                                       |
| -------------- | ------- | ------------------------------------------------------------- |
| Boolean        | INTEGER | `0` 或 `1`                                                    |
| Byte           | INTEGER |                                                               |
| Byte[]         | BLOB    |                                                               |
| Char           | TEXT    | UTF-8                                                         |
| Datetime       | TEXT    | yyyy-MM-dd HH:mm:sss.森林論壇                                   |
| DateTimeOffset | TEXT    | yyyy-MM-dd HH:mm:sss.FFFFFFFfzzz                                |
| Decimal        | TEXT    | `0.0###########################`格式。 雷亞爾是虧損的。 |
| Double         | real    |                                                               |
| Guid           | TEXT    | 00000000-0000-0000-0000-000000000000                          |
| Int16          | INTEGER |                                                               |
| Int32          | INTEGER |                                                               |
| Int64          | INTEGER |                                                               |
| SByte          | INTEGER |                                                               |
| Single         | real    |                                                               |
| String         | TEXT    | UTF-8                                                         |
| TimeSpan       | TEXT    | d.hh:mm:s.fffffff                                            |
| UInt16         | INTEGER |                                                               |
| UInt32         | INTEGER |                                                               |
| UInt64         | INTEGER | 大值溢位                                         |

## <a name="alternative-types"></a>替代類型

某些 .NET 類型可以從其他 SQLite 類型讀取。 參數也可以配置為使用這些替代類型。 如需詳細資訊，請參閱[參數](parameters.md#alternative-types)。

| .NET           | SQLite  | 備註          |
| -------------- | ------- | ---------------- |
| Char           | INTEGER | UTF-16           |
| Datetime       | real    | 朱利安日值 |
| DateTimeOffset | real    | 朱利安日值 |
| Guid           | BLOB    |                  |
| TimeSpan       | real    | 在幾天內          |

例如,以下查詢從結果集中的 REAL 列讀取 TimeSpan 值。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_AlternativeType)]

## <a name="column-types"></a>資料行類型

SQLite 使用動態類型系統,其中值的類型與值本身相關聯,而不是與存儲值的列相關聯。 您可以自由使用所需的任何列類型名稱。 Microsoft.Data.Sqlite 不會對這些名稱應用任何其他語義。

列類型名稱確實對[類型相關性](https://www.sqlite.org/datatype3.html#type_affinity)有影響。 一個常見的錯誤是,使用 STRING 的列類型將嘗試將值轉換為 INTEGER 或 REAL,這可能導致意外的結果。 我們建議僅使用四個原始 SQLite 類型名稱:INTEGER、真實名稱、文本名稱和 BLOB。

SQLite 允許您指定長度、精度和比例等類型方面,但它們不是由資料庫引擎強制執行的。 你的應用負責執行這些。

## <a name="see-also"></a>另請參閱

- [SQLite 中的數據型態](https://www.sqlite.org/datatype3.html)
