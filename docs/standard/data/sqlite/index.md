---
title: 概觀
ms.date: 12/13/2019
description: Microsoft 資料 Sqlite 的總覽
ms.openlocfilehash: a5dc1366cc0ddfcd5501e26bf2a994456bcd5d98
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447227"
---
# <a name="microsoftdatasqlite-overview"></a>Microsoft. Data Sqlite 總覽

Sqlite 是適用于 SQLite 的輕量[ADO.NET](../../../framework/data/adonet/index.md)提供者。 SQLite 的[Entity Framework Core](/ef/core/)提供者是以這個程式庫為基礎。 不過，它也可以單獨使用，或與其他資料存取程式庫搭配使用。

## <a name="installation"></a>安裝

最新的穩定版本可在[NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite)上取得。

### <a name="net-core-clitabnetcore-cli"></a>[.NET Core CLI](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite
```

### <a name="visual-studiotabvisual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite
```

---

## <a name="usage"></a>使用

此程式庫會針對連接、命令、資料讀取器等，執行常見的 ADO.NET 抽象概念。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_HelloWorld)]

## <a name="see-also"></a>請參閱

* [連接字串](connection-strings.md)
* [API 參考](/dotnet/api/?view=msdata-sqlite-3.0.0)
* [SQL 語法](https://www.sqlite.org/lang.html)
