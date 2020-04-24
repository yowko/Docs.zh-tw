---
title: 非同步限制
ms.date: 12/13/2019
description: 說明非同步 Api 的限制，以及您可以改用的一些替代方案。
ms.openlocfilehash: 350237dc5c03023f60e9680e8b9c94aabb62606f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447080"
---
# <a name="async-limitations"></a><span data-ttu-id="3be1a-103">非同步限制</span><span class="sxs-lookup"><span data-stu-id="3be1a-103">Async limitations</span></span>

<span data-ttu-id="3be1a-104">SQLite 不支援非同步 i/o。</span><span class="sxs-lookup"><span data-stu-id="3be1a-104">SQLite doesn't support asynchronous I/O.</span></span> <span data-ttu-id="3be1a-105">非同步 ADO.NET 方法會在 Microsoft. Sqlite 中以同步方式執行。</span><span class="sxs-lookup"><span data-stu-id="3be1a-105">Async ADO.NET methods will execute synchronously in Microsoft.Data.Sqlite.</span></span> <span data-ttu-id="3be1a-106">請避免呼叫它們。</span><span class="sxs-lookup"><span data-stu-id="3be1a-106">Avoid calling them.</span></span>

<span data-ttu-id="3be1a-107">相反地，請使用[預先寫入記錄](https://www.sqlite.org/wal.html)來改善效能和平行存取。</span><span class="sxs-lookup"><span data-stu-id="3be1a-107">Instead, use [write-ahead logging](https://www.sqlite.org/wal.html) to improve performance and concurrency.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/AsyncSample/Program.cs?name=snippet_WAL)]

> [!TIP]
> <span data-ttu-id="3be1a-108">在使用[Entity Framework Core](/ef/core/)建立的資料庫上，預設會啟用預先寫入記錄。</span><span class="sxs-lookup"><span data-stu-id="3be1a-108">Write-ahead logging is enabled by default on databases created using [Entity Framework Core](/ef/core/).</span></span>
