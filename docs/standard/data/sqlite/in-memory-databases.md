---
title: 記憶體內部資料庫
ms.date: 12/13/2019
description: 瞭解如何使用記憶體中的 SQLite 資料庫。
ms.openlocfilehash: fbda5787d95a9ce462752b985f847af0b0551fa6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555363"
---
# <a name="in-memory-databases"></a><span data-ttu-id="9688b-103">記憶體內部資料庫</span><span class="sxs-lookup"><span data-stu-id="9688b-103">In-memory databases</span></span>

<span data-ttu-id="9688b-104">SQLite 記憶體內部資料庫是完全儲存在記憶體中的資料庫，而不是儲存在磁片上。</span><span class="sxs-lookup"><span data-stu-id="9688b-104">SQLite in-memory databases are databases stored entirely in memory, not on disk.</span></span> <span data-ttu-id="9688b-105">使用特殊的資料來源檔案名 `:memory:` 來建立記憶體中的資料庫。</span><span class="sxs-lookup"><span data-stu-id="9688b-105">Use the special data source filename `:memory:` to create an in-memory database.</span></span> <span data-ttu-id="9688b-106">當連接關閉時，就會刪除資料庫。</span><span class="sxs-lookup"><span data-stu-id="9688b-106">When the connection is closed, the database is deleted.</span></span> <span data-ttu-id="9688b-107">使用時 `:memory:` ，每個連接都會建立自己的資料庫。</span><span class="sxs-lookup"><span data-stu-id="9688b-107">When using `:memory:`, each connection creates its own database.</span></span>

```connectionstring
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a><span data-ttu-id="9688b-108">可共用的記憶體內部資料庫</span><span class="sxs-lookup"><span data-stu-id="9688b-108">Shareable in-memory databases</span></span>

<span data-ttu-id="9688b-109">在連接字串中使用和，可以在多個連接之間共用記憶體內部資料庫 `Mode=Memory` `Cache=Shared` 。</span><span class="sxs-lookup"><span data-stu-id="9688b-109">In-memory databases can be shared between multiple connections by using `Mode=Memory` and `Cache=Shared` in the connection string.</span></span> <span data-ttu-id="9688b-110">`Data Source`關鍵字是用來提供記憶體中資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="9688b-110">The `Data Source` keyword is used to give the in-memory database a name.</span></span> <span data-ttu-id="9688b-111">使用相同名稱的連接字串將會存取相同的記憶體內資料庫。</span><span class="sxs-lookup"><span data-stu-id="9688b-111">Connection strings using the same name will access the same in-memory database.</span></span> <span data-ttu-id="9688b-112">只要至少有一個連接維持開啟狀態，資料庫就會持續存在。</span><span class="sxs-lookup"><span data-stu-id="9688b-112">The database persists as long as at least one connection to it remains open.</span></span> <span data-ttu-id="9688b-113">您可以在 GitHub 上取得示範這項功能的 [範例](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) 。</span><span class="sxs-lookup"><span data-stu-id="9688b-113">A [sample](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) demonstrating this is available on GitHub.</span></span>

```connectionstring
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
