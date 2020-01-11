---
title: Dapper 限制
ms.date: 12/13/2019
description: 說明您在使用 Dapper 時會遇到的一些限制。
ms.openlocfilehash: 396507f25f591a9ab5c3bb07c0af6fd8d175e4ea
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901202"
---
# <a name="dapper-limitations"></a>Dapper 限制

當您使用[Dapper](https://stackexchange.github.io/Dapper/)時，您應該注意一些限制。

## <a name="parameters"></a>參數

SQLite 參數名稱會區分大小寫。 請確定 SQL 中所使用的參數名稱符合匿名物件屬性的大小寫。 問題[#18861](https://github.com/dotnet/efcore/issues/18861)會改善這項體驗。

Dapper 也預期參數會使用 `@` 前置詞。 其他首碼將無法使用。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_Parameter)]

## <a name="data-types"></a>資料類型

Dapper 會使用 SqliteDataReader 索引子來讀取值。 此索引子的傳回型別為 object，這表示它只會傳回 long、double、string 或 byte [] 值。 如需詳細資訊，請參閱[資料類型](types.md)。 Dapper 會處理這些和其他基本類型之間的大部分轉換。 可惜的是，它不會處理 `DateTimeOffset`、`Guid`或 `TimeSpan`。 如果您想要在結果中使用這些類型，請建立類型處理常式。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_TypeHandlers)]

在查詢之前，請不要忘記加入型別處理程式。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_AddTypeHandlers)]

## <a name="see-also"></a>請參閱

* [資料類型](types.md)
* [非同步限制](async.md)
