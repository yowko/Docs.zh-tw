---
title: ADO.NET 限制
ms.date: 12/13/2019
description: 說明您可能會遇到的一些 ADO.NET 限制。
ms.openlocfilehash: 8664b73071fc859ed30080f549b05e7d6ed020f4
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901257"
---
# <a name="adonet-limitations"></a>ADO.NET 限制

ADO.NET 提供許多抽象概念的執行，但有一些限制。

## <a name="database-schema-information"></a>資料庫架構資訊

您可以使用<xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A>方法來取得有關查詢結果的中繼資料。

`DbConnection.GetSchema()`未執行。 此 API 未妥善定義，因此建議您直接使用標準 SQLite Api （例如[sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema)資料表和[table_info](https://www.sqlite.org/pragma.html#pragma_table_info) PRAGMA）來抓取資料庫中繼資料。

如需詳細資訊，請參閱[中繼資料](metadata.md)。

## <a name="systemtransactions"></a>System.Transactions

Microsoft. Sqlite 尚未支援 System.object。 請改用 ADO.NET 的交易。 如需詳細資訊，請參閱[交易](transactions.md)。

提供有關缺少系統支援的意見反應[#13825](https://github.com/dotnet/efcore/issues/13825)的問題。

## <a name="data-adapters"></a>資料介面卡

`DbDataAdapter`尚未由 Microsoft. Sqlite 執行。 這表示您只能使用 ADO.NET `DataSet`和`DataTable`來載入資料，而不會進行更新。

使用問題[#13838](https://github.com/dotnet/efcore/issues/13838) ，提供有關執行`DbDataAdapter`的意見反應。

## <a name="output-parameters"></a>輸出參數

SQLite 不支援輸出參數。

## <a name="positional-parameters"></a>位置參數

Sqlite 僅支援命名[參數](parameters.md)。 不支援位置參數。

## <a name="stored-procedures"></a>預存程序

SQLite 不支援預存程式。

## <a name="isolation-levels"></a>隔離層級

SQLite `Chaos`交易`Snapshot`中不支援和隔離等級。

## <a name="see-also"></a>另請參閱

* [非同步限制](async.md)
* [資料類型](types.md)
* [異動](transactions.md)
