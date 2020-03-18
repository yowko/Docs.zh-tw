---
title: 概觀
ms.date: 12/13/2019
description: 微軟概述.Data.Sqlite
ms.openlocfilehash: e84c68f0615f187e8dea7ab87ac917c0ad796a1c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "77543595"
---
# <a name="microsoftdatasqlite-overview"></a>微軟.資料.Sqlite 概述

微軟.Data.Sqlite是SQLite的羽量級[ADO.NET](../../../framework/data/adonet/index.md)供應商。 SQLite 的[實體框架核心](/ef/core/)提供程式構建在此庫之上。 但是，它也可以單獨使用，也可以與其他資料訪問庫一起使用。

## <a name="installation"></a>安裝

最新的穩定版本在[NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite)上可用。

### <a name="net-core-cli"></a>[.NET Core CLI](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite
```

### <a name="visual-studio"></a>[Visualstudio](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite
```

---

## <a name="usage"></a>使用量

此庫實現連接、命令、資料讀取器等的通用ADO.NET抽象。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_HelloWorld)]

## <a name="see-also"></a>另請參閱

* [連接字串](connection-strings.md)
* [API 參考](/dotnet/api/?view=msdata-sqlite-3.0)
* [SQL 語法](https://www.sqlite.org/lang.html)
