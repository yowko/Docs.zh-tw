---
title: 記憶體內部資料庫
ms.date: 12/13/2019
description: 瞭解如何使用記憶體中 SQLite 資料庫。
ms.openlocfilehash: 408c81f538e27dcfffad20db74b7809912b7905f
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391204"
---
# <a name="in-memory-databases"></a><span data-ttu-id="c54a5-103">記憶體內部資料庫</span><span class="sxs-lookup"><span data-stu-id="c54a5-103">In-memory databases</span></span>

<span data-ttu-id="c54a5-104">SQLite 記憶體中資料庫是完全存儲在記憶體中的資料庫，而不是存儲在磁片上。</span><span class="sxs-lookup"><span data-stu-id="c54a5-104">SQLite in-memory databases are databases stored entirely in memory, not on disk.</span></span> <span data-ttu-id="c54a5-105">使用特殊的資料來源檔案名`:memory:`創建記憶體中資料庫。</span><span class="sxs-lookup"><span data-stu-id="c54a5-105">Use the special data source filename `:memory:` to create an in-memory database.</span></span> <span data-ttu-id="c54a5-106">關閉連接時，將刪除資料庫。</span><span class="sxs-lookup"><span data-stu-id="c54a5-106">When the connection is closed, the database is deleted.</span></span> <span data-ttu-id="c54a5-107">使用`:memory:`時，每個連接將創建其自己的資料庫。</span><span class="sxs-lookup"><span data-stu-id="c54a5-107">When using `:memory:`, each connection creates its own database.</span></span>

```ConnectionString
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a><span data-ttu-id="c54a5-108">可共用記憶體中資料庫</span><span class="sxs-lookup"><span data-stu-id="c54a5-108">Shareable in-memory databases</span></span>

<span data-ttu-id="c54a5-109">記憶體中資料庫可以通過使用`Mode=Memory`和`Cache=Shared`在連接字串中在多個連接之間共用。</span><span class="sxs-lookup"><span data-stu-id="c54a5-109">In-memory databases can be shared between multiple connections by using `Mode=Memory` and `Cache=Shared` in the connection string.</span></span> <span data-ttu-id="c54a5-110">關鍵字`Data Source`用於為記憶體中資料庫指定名稱。</span><span class="sxs-lookup"><span data-stu-id="c54a5-110">The `Data Source` keyword is used to give the in-memory database a name.</span></span> <span data-ttu-id="c54a5-111">使用相同名稱的連接字串將訪問相同的記憶體內資料庫。</span><span class="sxs-lookup"><span data-stu-id="c54a5-111">Connection strings using the same name will access the same in-memory database.</span></span> <span data-ttu-id="c54a5-112">只要資料庫至少保持一個連接保持打開狀態，資料庫就將保持不變。</span><span class="sxs-lookup"><span data-stu-id="c54a5-112">The database persists as long as at least one connection to it remains open.</span></span> <span data-ttu-id="c54a5-113">GitHub 上提供了演示此[示例](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs)。</span><span class="sxs-lookup"><span data-stu-id="c54a5-113">A [sample](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) demonstrating this is available on GitHub.</span></span>

```ConnectionString
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
