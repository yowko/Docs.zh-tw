---
title: 定序
ms.date: 12/13/2019
description: 瞭解如何建立自訂的排序次序。
ms.openlocfilehash: 9879846cc191a62c4cb47a0fbaa47c59153ba61c
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242968"
---
# <a name="collation"></a>定序

比較文字值以判斷順序和相等時，SQLite 會使用排序次序。 您可以指定在 SQL 查詢中建立資料行或每個作業時要使用的定序。 SQLite 預設包含三個排序次序。

| 定序 | 說明                               |
| --------- | ----------------------------------------- |
| RTRIM     | 忽略尾端空白               |
| NOCASE    | ASCII 字元 a-z 的不區分大小寫 |
| BINARY    | 區分大小寫。 直接比較位元組   |

## <a name="custom-collation"></a>自訂定序

您也可以定義自己的定序序列，或使用<xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>覆寫內建的排序次序。 下列範例會顯示覆寫 NOCASE 定序以支援 Unicode 字元。 [完整的範例程式碼](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/CollationSample/Program.cs)可在 GitHub 上取得。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/CollationSample/Program.cs?name=snippet_Collation)]

## <a name="like-operator"></a>Like 運算子

SQLite 中的 LIKE 運算子不接受定序。 預設的實作為與 NOCASE 定序相同的語義。 ASCII 字元 A 到 Z 只會區分大小寫。

您可以使用下列 pragma 語句，輕鬆地讓 LIKE 運算子區分大小寫：

```sql
PRAGMA case_sensitive_like = 1
```

如需覆寫 LIKE 運算子之執行的詳細資訊，請參閱[使用者定義函數](user-defined-functions.md)。

## <a name="see-also"></a>另請參閱

* [使用者定義的函式](user-defined-functions.md)
* [SQL 語法](https://www.sqlite.org/lang.html)
