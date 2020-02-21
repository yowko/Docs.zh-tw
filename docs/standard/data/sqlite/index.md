---
title: 概觀
ms.date: 12/13/2019
description: Microsoft 資料 Sqlite 的總覽
ms.openlocfilehash: e84c68f0615f187e8dea7ab87ac917c0ad796a1c
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543595"
---
# <a name="microsoftdatasqlite-overview"></a><span data-ttu-id="99dff-103">Microsoft. Data Sqlite 總覽</span><span class="sxs-lookup"><span data-stu-id="99dff-103">Microsoft.Data.Sqlite overview</span></span>

<span data-ttu-id="99dff-104">Sqlite 是適用于 SQLite 的輕量[ADO.NET](../../../framework/data/adonet/index.md)提供者。</span><span class="sxs-lookup"><span data-stu-id="99dff-104">Microsoft.Data.Sqlite is a lightweight [ADO.NET](../../../framework/data/adonet/index.md) provider for SQLite.</span></span> <span data-ttu-id="99dff-105">SQLite 的[Entity Framework Core](/ef/core/)提供者是以這個程式庫為基礎。</span><span class="sxs-lookup"><span data-stu-id="99dff-105">The [Entity Framework Core](/ef/core/) provider for SQLite is built on top of this library.</span></span> <span data-ttu-id="99dff-106">不過，它也可以單獨使用，或與其他資料存取程式庫搭配使用。</span><span class="sxs-lookup"><span data-stu-id="99dff-106">However, it can also be used independently or with other data access libraries.</span></span>

## <a name="installation"></a><span data-ttu-id="99dff-107">安裝</span><span class="sxs-lookup"><span data-stu-id="99dff-107">Installation</span></span>

<span data-ttu-id="99dff-108">最新的穩定版本可在[NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite)上取得。</span><span class="sxs-lookup"><span data-stu-id="99dff-108">The latest stable version is available on [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite).</span></span>

### <a name="net-core-cli"></a>[<span data-ttu-id="99dff-109">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="99dff-109">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite
```

### <a name="visual-studio"></a>[<span data-ttu-id="99dff-110">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="99dff-110">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite
```

---

## <a name="usage"></a><span data-ttu-id="99dff-111">使用量</span><span class="sxs-lookup"><span data-stu-id="99dff-111">Usage</span></span>

<span data-ttu-id="99dff-112">此程式庫會針對連接、命令、資料讀取器等，執行常見的 ADO.NET 抽象概念。</span><span class="sxs-lookup"><span data-stu-id="99dff-112">This library implements the common ADO.NET abstractions for connections, commands, data readers, and so on.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_HelloWorld)]

## <a name="see-also"></a><span data-ttu-id="99dff-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99dff-113">See also</span></span>

* [<span data-ttu-id="99dff-114">連接字串</span><span class="sxs-lookup"><span data-stu-id="99dff-114">Connection strings</span></span>](connection-strings.md)
* [<span data-ttu-id="99dff-115">API 參考</span><span class="sxs-lookup"><span data-stu-id="99dff-115">API Reference</span></span>](/dotnet/api/?view=msdata-sqlite-3.0)
* [<span data-ttu-id="99dff-116">SQL 語法</span><span class="sxs-lookup"><span data-stu-id="99dff-116">SQL Syntax</span></span>](https://www.sqlite.org/lang.html)
