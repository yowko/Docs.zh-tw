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
# <a name="microsoftdatasqlite-overview"></a><span data-ttu-id="6f78e-103">微軟.資料.Sqlite 概述</span><span class="sxs-lookup"><span data-stu-id="6f78e-103">Microsoft.Data.Sqlite overview</span></span>

<span data-ttu-id="6f78e-104">微軟.Data.Sqlite是SQLite的羽量級[ADO.NET](../../../framework/data/adonet/index.md)供應商。</span><span class="sxs-lookup"><span data-stu-id="6f78e-104">Microsoft.Data.Sqlite is a lightweight [ADO.NET](../../../framework/data/adonet/index.md) provider for SQLite.</span></span> <span data-ttu-id="6f78e-105">SQLite 的[實體框架核心](/ef/core/)提供程式構建在此庫之上。</span><span class="sxs-lookup"><span data-stu-id="6f78e-105">The [Entity Framework Core](/ef/core/) provider for SQLite is built on top of this library.</span></span> <span data-ttu-id="6f78e-106">但是，它也可以單獨使用，也可以與其他資料訪問庫一起使用。</span><span class="sxs-lookup"><span data-stu-id="6f78e-106">However, it can also be used independently or with other data access libraries.</span></span>

## <a name="installation"></a><span data-ttu-id="6f78e-107">安裝</span><span class="sxs-lookup"><span data-stu-id="6f78e-107">Installation</span></span>

<span data-ttu-id="6f78e-108">最新的穩定版本在[NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite)上可用。</span><span class="sxs-lookup"><span data-stu-id="6f78e-108">The latest stable version is available on [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite).</span></span>

### <a name="net-core-cli"></a>[<span data-ttu-id="6f78e-109">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="6f78e-109">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite
```

### <a name="visual-studio"></a>[<span data-ttu-id="6f78e-110">Visualstudio</span><span class="sxs-lookup"><span data-stu-id="6f78e-110">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite
```

---

## <a name="usage"></a><span data-ttu-id="6f78e-111">使用量</span><span class="sxs-lookup"><span data-stu-id="6f78e-111">Usage</span></span>

<span data-ttu-id="6f78e-112">此庫實現連接、命令、資料讀取器等的通用ADO.NET抽象。</span><span class="sxs-lookup"><span data-stu-id="6f78e-112">This library implements the common ADO.NET abstractions for connections, commands, data readers, and so on.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_HelloWorld)]

## <a name="see-also"></a><span data-ttu-id="6f78e-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f78e-113">See also</span></span>

* [<span data-ttu-id="6f78e-114">連接字串</span><span class="sxs-lookup"><span data-stu-id="6f78e-114">Connection strings</span></span>](connection-strings.md)
* [<span data-ttu-id="6f78e-115">API 參考</span><span class="sxs-lookup"><span data-stu-id="6f78e-115">API Reference</span></span>](/dotnet/api/?view=msdata-sqlite-3.0)
* [<span data-ttu-id="6f78e-116">SQL 語法</span><span class="sxs-lookup"><span data-stu-id="6f78e-116">SQL Syntax</span></span>](https://www.sqlite.org/lang.html)
