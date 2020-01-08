---
title: 記憶體內部資料庫
ms.date: 12/13/2019
description: 瞭解如何使用記憶體內部的 SQLite 資料庫。
ms.openlocfilehash: b125ff5aa4128bd4c3ff558c5573b7d11802090a
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447241"
---
# <a name="in-memory-databases"></a><span data-ttu-id="674ed-103">記憶體內部資料庫</span><span class="sxs-lookup"><span data-stu-id="674ed-103">In-memory databases</span></span>

<span data-ttu-id="674ed-104">SQLite 記憶體內部資料庫是完全儲存在記憶體中的資料庫，而不是在磁片上。</span><span class="sxs-lookup"><span data-stu-id="674ed-104">SQLite in-memory databases are databases stored entirely in memory, not on disk.</span></span> <span data-ttu-id="674ed-105">使用特殊的資料來源檔案名 `:memory:` 來建立記憶體內部資料庫。</span><span class="sxs-lookup"><span data-stu-id="674ed-105">Use the special data source filename `:memory:` to create an in-memory database.</span></span> <span data-ttu-id="674ed-106">當連接關閉時，就會刪除資料庫。</span><span class="sxs-lookup"><span data-stu-id="674ed-106">When the connection is closed, the database is deleted.</span></span> <span data-ttu-id="674ed-107">使用 `:memory:`時，每個連接都會建立自己的資料庫。</span><span class="sxs-lookup"><span data-stu-id="674ed-107">When using `:memory:`, each connection creates its own database.</span></span>

```ConnectionString
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a><span data-ttu-id="674ed-108">可共用的記憶體內部資料庫</span><span class="sxs-lookup"><span data-stu-id="674ed-108">Shareable in-memory databases</span></span>

<span data-ttu-id="674ed-109">記憶體內部資料庫可以使用連接字串中的 `Mode=Memory` 和 `Cache=Shared`，在多個連接之間共用。</span><span class="sxs-lookup"><span data-stu-id="674ed-109">In-memory databases can be shared between multiple connections by using `Mode=Memory` and `Cache=Shared` in the connection string.</span></span> <span data-ttu-id="674ed-110">`Data Source` 關鍵字是用來提供記憶體中的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="674ed-110">The `Data Source` keyword is used to give the in-memory database a name.</span></span> <span data-ttu-id="674ed-111">使用相同名稱的連接字串將會存取相同的記憶體內部資料庫。</span><span class="sxs-lookup"><span data-stu-id="674ed-111">Connection strings using the same name will access the same in-memory database.</span></span> <span data-ttu-id="674ed-112">只要至少有一個連接保持開啟狀態，資料庫就會持續存在。</span><span class="sxs-lookup"><span data-stu-id="674ed-112">The database persists as long as at least one connection to it remains open.</span></span> <span data-ttu-id="674ed-113">GitHub 上提供示範此功能的[範例](https://github.com/dotnet/samples/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs)。</span><span class="sxs-lookup"><span data-stu-id="674ed-113">A [sample](https://github.com/dotnet/samples/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) demonstrating this is available on GitHub.</span></span>

```ConnectionString
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
