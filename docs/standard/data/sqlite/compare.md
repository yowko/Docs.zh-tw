---
title: 與 System.object 的比較
ms.date: 12/13/2019
description: 描述 Microsoft. Data Sqlite 和 system.string 程式庫之間的一些差異。
ms.openlocfilehash: 076bbc6f746cf9296c96ec73047397a21a3b2558
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900704"
---
# <a name="comparison-to-systemdatasqlite"></a>與 System.object 的比較

在2005中，Robert Simpson 已建立 ADO.NET 2.0 的 SQLite 提供者。 在2010中，SQLite 團隊接管了專案的維護和開發。 另外值得一提的是，Mono 小組會將2007中的程式碼分叉為 Mono。 SQLite 有很長的歷程記錄，並已演變為穩定且功能完整的 ADO.NET 提供者，並使用 Visual Studio 工具完成。 新版本會繼續將與每個版本 .NET Framework 相容的元件送回2.0 版，甚至 .NET Compact Framework 3.5。

第一版的 .NET Core （于2016發行）是 .NET 的單一、輕量、現代化且跨平臺的執行。 已刻意移除具有更多新式替代專案的過時 Api 和 Api。 ADO.NET 未包含任何資料集 Api （包括 DataTable 和 DataAdapter）。

Entity Framework 小組有點熟悉 System.object 程式碼基底。 Brice Lambson 是 EF 小組的成員，先前已協助 SQLite 團隊新增 Entity Framework 版本5和6的支援。 Brice 也會在規劃 .NET Core 的同時，透過自己的 SQLite ADO.NET 提供者執行進行實驗。 經過一段時間的討論之後，Entity Framework 小組決定根據 Brice 的原型建立 Microsoft 資料 Sqlite。 這可讓他們建立新的輕量和現代化的執行，以配合 .NET Core 的目標。

做為我們的重要性，我們的程式碼如下所示：在 system.string 和. sqlite 中建立[使用者定義函數](user-defined-functions.md)。

```csharp
// System.Data.SQLite
connection.BindFunction(
    new SQLiteFunctionAttribute("ceiling", 1, FunctionType.Scalar),
    (Func<object[], object>)((object[] args) => Math.Ceiling((double)((object[])args[1])[0])),
    null);

// Microsoft.Data.Sqlite
connection.CreateFunction(
    "ceiling",
    (double arg) => Math.Ceiling(arg));
```

在2017中，.NET Core 2.0 在策略方面有變更。 它決定與 .NET Framework 的相容性對於 .NET Core 的成功非常重要。 許多已移除的 Api，包括資料集 Api，都已新增回來。 與其他許多人一樣，這會解除封鎖的 System.object，讓它也可以移植到 .NET Core。 但是，Microsoft 的原始目標是輕量且現代化的資料，不過仍會保持不變。 如需 ADO.NET 不是由 Microsoft 所實行之 Api 的詳細資料，請參閱[ADO.NET 限制](adonet-limitations.md)。

將新功能新增至 [Sqlite] 時，會將 System.object 的設計納入考慮。 我們盡可能嘗試將兩者之間的變更降至最低，以減輕兩者之間的轉換。

## <a name="data-types"></a>資料類型

Microsoft. Sqlite 和 System.object 的最大差異在於資料類型的處理方式。 如[資料類型](types.md)中所述，Microsoft. Sqlite 不會嘗試隱藏 Sqlite 的基礎 quirkiness，這可讓任何任一字元串指定為數據行類型，而且只有四種基本類型：整數、實數、文字和 BLOB。

SQLite 會將其他的語義套用至資料行類型，將它們直接對應至 .NET 類型。 這讓提供者具有更強型別風格，但有一些粗略的邊緣。 例如，他們必須引進新的 SQL 語句（類型），以在 SELECT 語句中指定運算式的資料行類型。

## <a name="connection-strings"></a>連接字串

Sqlite 的[連接字串](connection-strings.md)關鍵字較少。 下表顯示可以改為使用的替代方案。

| 關鍵字          | 替代函式                                         |
| ---------------- | --------------------------------------------------- |
| 快取大小       | 發送`PRAGMA cache_size = <pages>`                  |
| 預設逾時  | 在 SqliteConnection 上使用 DefaultTimeout 屬性 |
| FailIfMissing    | 使用`Mode=ReadWrite`                                |
| FullUri          | 使用資料來源關鍵字                         |
| 記錄模式     | 發送`PRAGMA journal_mode = <mode>`                 |
| 舊版格式    | 發送`PRAGMA legacy_file_format = 1`                |
| 最大頁面計數   | 發送`PRAGMA max_page_count = <pages>`              |
| 頁面大小        | 發送`PRAGMA page_size = <bytes>`                   |
| 唯讀        | 使用`Mode=ReadOnly`                                 |
| 同步      | 發送`PRAGMA synchronous = <mode>`                  |
| Uri              | 使用資料來源關鍵字                         |
| UseUTF16Encoding | 發送`PRAGMA encoding = 'UTF-16'`                   |

## <a name="authorization"></a>授權

Microsoft. Sqlite 沒有任何 API 公開 SQLite 的授權回呼。 使用 [問題[#13835](https://github.com/dotnet/efcore/issues/13835) ] 來提供有關此功能的意見反應。

## <a name="data-change-notifications"></a>資料變更通知

Microsoft. Sqlite 沒有任何 API 公開 SQLite 的資料變更通知。 使用 [問題[#13827](https://github.com/dotnet/efcore/issues/13827) ] 來提供有關此功能的意見反應。

## <a name="virtual-table-modules"></a>虛擬資料表模組

在建立虛擬資料表模組時，Sqlite 沒有任何 API。 使用 [問題[#13823](https://github.com/dotnet/efcore/issues/13823) ] 來提供有關此功能的意見反應。

## <a name="see-also"></a>另請參閱

* [資料類型](types.md)
* [連接字串](connection-strings.md)
* [加密][](encryption.md)
* [ADO.NET 限制](adonet-limitations.md)
* [Dapper 限制](dapper-limitations.md)
