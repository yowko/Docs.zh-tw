---
title: 記憶體內部資料庫
ms.date: 12/13/2019
description: 瞭解如何使用記憶體內部的 SQLite 資料庫。
ms.openlocfilehash: 408c81f538e27dcfffad20db74b7809912b7905f
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391204"
---
# <a name="in-memory-databases"></a><span data-ttu-id="68fc2-103">記憶體內部資料庫</span><span class="sxs-lookup"><span data-stu-id="68fc2-103">In-memory databases</span></span>

<span data-ttu-id="68fc2-104">SQLite 記憶體內部資料庫是完全儲存在記憶體中的資料庫，而不是在磁片上。</span><span class="sxs-lookup"><span data-stu-id="68fc2-104">SQLite in-memory databases are databases stored entirely in memory, not on disk.</span></span> <span data-ttu-id="68fc2-105">使用特殊的資料來源檔案名`:memory:`來建立記憶體內部資料庫。</span><span class="sxs-lookup"><span data-stu-id="68fc2-105">Use the special data source filename `:memory:` to create an in-memory database.</span></span> <span data-ttu-id="68fc2-106">當連接關閉時，就會刪除資料庫。</span><span class="sxs-lookup"><span data-stu-id="68fc2-106">When the connection is closed, the database is deleted.</span></span> <span data-ttu-id="68fc2-107">使用`:memory:`時，每個連接都會建立自己的資料庫。</span><span class="sxs-lookup"><span data-stu-id="68fc2-107">When using `:memory:`, each connection creates its own database.</span></span>

```ConnectionString
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a><span data-ttu-id="68fc2-108">可共用的記憶體內部資料庫</span><span class="sxs-lookup"><span data-stu-id="68fc2-108">Shareable in-memory databases</span></span>

<span data-ttu-id="68fc2-109">記憶體內部資料庫可以在連接字串中使用`Mode=Memory`和， `Cache=Shared`在多個連接之間共用。</span><span class="sxs-lookup"><span data-stu-id="68fc2-109">In-memory databases can be shared between multiple connections by using `Mode=Memory` and `Cache=Shared` in the connection string.</span></span> <span data-ttu-id="68fc2-110">`Data Source`關鍵字是用來提供記憶體中的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="68fc2-110">The `Data Source` keyword is used to give the in-memory database a name.</span></span> <span data-ttu-id="68fc2-111">使用相同名稱的連接字串將會存取相同的記憶體內部資料庫。</span><span class="sxs-lookup"><span data-stu-id="68fc2-111">Connection strings using the same name will access the same in-memory database.</span></span> <span data-ttu-id="68fc2-112">只要至少有一個連接保持開啟狀態，資料庫就會持續存在。</span><span class="sxs-lookup"><span data-stu-id="68fc2-112">The database persists as long as at least one connection to it remains open.</span></span> <span data-ttu-id="68fc2-113">GitHub 上提供示範此功能的[範例](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs)。</span><span class="sxs-lookup"><span data-stu-id="68fc2-113">A [sample](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) demonstrating this is available on GitHub.</span></span>

```ConnectionString
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
