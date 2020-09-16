---
title: 概觀
ms.date: 12/13/2019
description: 介紹 Microsoft. Sqlite
ms.openlocfilehash: 7c952848f7e7ea04f11fe9340f77a1f376a1be07
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552436"
---
# <a name="microsoftdatasqlite-overview"></a>Microsoft. Sqlite 總覽

ADO.NET 是 SQLite 的輕量[ADO.NET](../../../framework/data/adonet/index.md)提供者。 SQLite 的 [Entity Framework Core](/ef/core/) 提供者是以這個程式庫為基礎。 不過，它也可以單獨使用，或與其他資料存取程式庫一起使用。

## <a name="installation"></a>安裝

您可以在 [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite)上取得最新的穩定版本。

### <a name="net-core-cli"></a>[.NET Core CLI](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite
```

### <a name="visual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite
```

---

## <a name="usage"></a>使用方式

此程式庫會針對連接、命令、資料讀取器，以及其他資訊，來執行一般的 ADO.NET 抽象概念。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_HelloWorld)]

## <a name="see-also"></a>另請參閱

* [連接字串](connection-strings.md)
* [API 參考](../../../../api/index.md?view=msdata-sqlite-3.0)
* [SQL 語法](https://www.sqlite.org/lang.html)
