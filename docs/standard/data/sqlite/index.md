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
# <a name="microsoftdatasqlite-overview"></a><span data-ttu-id="c22b3-103">Microsoft. Data Sqlite 總覽</span><span class="sxs-lookup"><span data-stu-id="c22b3-103">Microsoft.Data.Sqlite overview</span></span>

<span data-ttu-id="c22b3-104">Sqlite 是適用于 SQLite 的輕量[ADO.NET](../../../framework/data/adonet/index.md)提供者。</span><span class="sxs-lookup"><span data-stu-id="c22b3-104">Microsoft.Data.Sqlite is a lightweight [ADO.NET](../../../framework/data/adonet/index.md) provider for SQLite.</span></span> <span data-ttu-id="c22b3-105">SQLite 的[Entity Framework Core](/ef/core/)提供者是以這個程式庫為基礎。</span><span class="sxs-lookup"><span data-stu-id="c22b3-105">The [Entity Framework Core](/ef/core/) provider for SQLite is built on top of this library.</span></span> <span data-ttu-id="c22b3-106">不過，它也可以單獨使用，或與其他資料存取程式庫搭配使用。</span><span class="sxs-lookup"><span data-stu-id="c22b3-106">However, it can also be used independently or with other data access libraries.</span></span>

## <a name="installation"></a><span data-ttu-id="c22b3-107">安裝</span><span class="sxs-lookup"><span data-stu-id="c22b3-107">Installation</span></span>

<span data-ttu-id="c22b3-108">最新的穩定版本可在[NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite)上取得。</span><span class="sxs-lookup"><span data-stu-id="c22b3-108">The latest stable version is available on [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite).</span></span>

### <a name="net-core-clitabnetcore-cli"></a>[<span data-ttu-id="c22b3-109">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="c22b3-109">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite
```

### <a name="visual-studiotabvisual-studio"></a>[<span data-ttu-id="c22b3-110">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c22b3-110">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite
```

---

## <a name="usage"></a><span data-ttu-id="c22b3-111">使用</span><span class="sxs-lookup"><span data-stu-id="c22b3-111">Usage</span></span>

<span data-ttu-id="c22b3-112">此程式庫會針對連接、命令、資料讀取器等，執行常見的 ADO.NET 抽象概念。</span><span class="sxs-lookup"><span data-stu-id="c22b3-112">This library implements the common ADO.NET abstractions for connections, commands, data readers, and so on.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_HelloWorld)]

## <a name="see-also"></a><span data-ttu-id="c22b3-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="c22b3-113">See also</span></span>

* [<span data-ttu-id="c22b3-114">連接字串</span><span class="sxs-lookup"><span data-stu-id="c22b3-114">Connection strings</span></span>](connection-strings.md)
* [<span data-ttu-id="c22b3-115">API 參考</span><span class="sxs-lookup"><span data-stu-id="c22b3-115">API Reference</span></span>](/dotnet/api/?view=msdata-sqlite-3.0.0)
* [<span data-ttu-id="c22b3-116">SQL 語法</span><span class="sxs-lookup"><span data-stu-id="c22b3-116">SQL Syntax</span></span>](https://www.sqlite.org/lang.html)
