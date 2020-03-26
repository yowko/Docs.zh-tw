---
title: 定序
ms.date: 12/13/2019
description: 瞭解如何創建自訂整理序列。
ms.openlocfilehash: b93c82a4ace154b8293b05effa8f9e9294fa7708
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79506537"
---
# <a name="collation"></a>定序

SQLite 在比較 TEXT 值以確定順序和相等性時使用分字序列。 您可以指定在 SQL 查詢中創建列或每個操作時要使用的排序規則。 預設情況下，SQLite 包括三個整理序列。

| 定序 | 描述                               |
| --------- | ----------------------------------------- |
| RTRIM     | 忽略尾隨空格               |
| 無案例    | ASCII 字元 A-Z 不區分大小寫 |
| BINARY    | 區分大小寫。 直接比較位元組   |

## <a name="custom-collation"></a>自訂排序規則

您還可以定義自己的整理序列或使用 重寫的序列<xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>。 下面的示例顯示覆蓋 NOCASE 排序規則以支援 Unicode 字元。 [完整的示例代碼](https://github.com/dotnet/samples/blob/master/snippets/standard/data/sqlite/CollationSample/Program.cs)在 GitHub 上可用。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/CollationSample/Program.cs?name=snippet_Collation)]

## <a name="like-operator"></a>Like 運算子

SQLite 中的 LIKE 運算子不遵循排序規則。 預設實現具有與 NOCASE 排序規則相同的語義。 它僅對 ASCII 字元 A 到 Z 不區分大小寫。

通過使用以下雜注語句，可以輕鬆地使 LIKE 運算子區分大小寫：

```sql
PRAGMA case_sensitive_like = 1
```

有關重寫 LIKE 運算子實現的詳細資訊，請參閱[使用者定義的函數](user-defined-functions.md)。

## <a name="see-also"></a>另請參閱

* [使用者定義的函數](user-defined-functions.md)
* [SQL 語法](https://www.sqlite.org/lang.html)
