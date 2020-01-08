---
title: 使用者定義函式
ms.date: 12/13/2019
description: 瞭解如何建立使用者定義的純量和彙總函式。
ms.openlocfilehash: 9ee3fbac73215353c8dc82199203b0d25e580cdb
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447171"
---
# <a name="user-defined-functions"></a>使用者定義函式

大部分的資料庫都具有 SQL 的程式性方言，您可以用它來定義自己的函式。 不過，SQLite 會使用您的應用程式在同進程中執行。 您不需要學習新的 SQL 方言，只要使用應用程式的程式設計語言就可以了。

## <a name="scalar-functions"></a>純量函式

純量函數會針對查詢中的每個資料列傳回單一純量值。 定義新的純量函數，並使用 <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateFunction%2A>覆寫內建的函式。

如需 `func` 引數的支援參數和傳回類型清單，請參閱[資料類型](types.md)。

指定 `state` 引數會將該值傳遞至函式的每個調用。 使用此來避免結束。

如果您的函式具有決定性，可讓 SQLite 在編譯查詢時使用額外的優化，請指定 `isDeterministic`。

下列範例顯示如何新增純量函數來計算圓柱的半徑。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ScalarFunctionSample/Program.cs?name=snippet_CreateFunction)]

## <a name="operators"></a>運算子

下列 SQLite 運算子會由對應的純量函式來執行。 在您的應用程式中定義這些純量函數將會覆寫這些運算子的行為。

| 運算子          | 函數      |
| ----------------- | ------------- |
| X GLOB Y          | glob （Y，X）    |
| X，例如 Y          | like （Y，X）    |
| X，如同 Y ESCAPE Z | like （Y，X，Z） |
| X 符合 Y         | match （Y，X）   |
| X REGEXP Y        | RegExp （Y，X）  |

下列範例顯示如何定義 RegExp 函式，以啟用其對應的運算子。 SQLite 不包含 RegExp 函數的預設執行。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/RegularExpressionSample/Program.cs?name=snippet_Regex)]

## <a name="aggregate-functions"></a>彙總函式

彙總函式會針對查詢中的所有資料列傳回單一匯總的值。 使用 <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateAggregate%2A>定義和覆寫彙總函式。

`seed` 引數會指定內容的初始狀態。 請使用此來避免同時結束。

每個資料列會叫用一次 `func` 引數。 使用內容來累積最終的結果。 傳回內容。 此模式可讓內容是實值型別或不可變的。

如果未指定 `resultSelector`，則會使用內容的最終狀態做為結果。 這可簡化函式的定義，例如 sum 和 count，這只需要每個資料列遞增一個數位，然後傳回它。

指定 `resultSelector`，以便在逐一查看所有資料列之後，計算內容的最終結果。

如需 `resultSelector`的 `func` 引數和傳回類型的支援參數類型清單，請參閱[資料類型](types.md)。

如果您的函式具決定性，請指定 `isDeterministic`，以允許 SQLite 在編譯查詢時使用額外的優化。

下列範例會定義彙總函式來計算資料行的標準差。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/AggregateFunctionSample/Program.cs?name=snippet_CreateAggregate)]

## <a name="errors"></a>錯誤

如果使用者定義的函式擲回例外狀況，則訊息會傳回 SQLite。 接著，SQLite 會引發錯誤和 SqliteException。 Sqlite 會擲回一個。 如需詳細資訊，請參閱[資料庫錯誤](database-errors.md)。

根據預設，錯誤 SQLite 錯誤碼將會 SQLITE_ERROR （或1）。 不過，您可以在函式中擲回 <xref:Microsoft.Data.Sqlite.SqliteException>，並指定所需的 <xref:Microsoft.Data.Sqlite.SqliteException.SqliteErrorCode> 來變更它。

## <a name="debugging"></a>偵錯

SQLite 會直接呼叫您的實作為。 這可讓您新增在 SQLite 正在評估查詢時觸發的中斷點。 完整的 .NET 偵錯工具體驗可協助您建立使用者定義函數。

## <a name="see-also"></a>請參閱

* [資料類型](types.md)
* [SQLite 核心函式](https://www.sqlite.org/lang_corefunc.html)
* [SQLite 彙總函式](https://www.sqlite.org/lang_aggfunc.html)
