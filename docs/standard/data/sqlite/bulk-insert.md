---
title: Bulk insert
ms.date: 12/13/2019
description: 當您對資料庫進行大量變更時，可以使用的效能秘訣。
ms.openlocfilehash: 9d87d5c8d70f8e70479f9aa02b7802f73b88de9e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447038"
---
# <a name="bulk-insert"></a><span data-ttu-id="f7cc8-103">Bulk insert</span><span class="sxs-lookup"><span data-stu-id="f7cc8-103">Bulk insert</span></span>

<span data-ttu-id="f7cc8-104">SQLite 沒有任何特殊的方式可大量插入資料。</span><span class="sxs-lookup"><span data-stu-id="f7cc8-104">SQLite doesn't have any special way to bulk insert data.</span></span> <span data-ttu-id="f7cc8-105">若要在插入或更新資料時獲得最佳效能，請務必執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="f7cc8-105">To get optimal performance when inserting or updating data, ensure that you do the following:</span></span>

- <span data-ttu-id="f7cc8-106">使用交易。</span><span class="sxs-lookup"><span data-stu-id="f7cc8-106">Use a transaction.</span></span>
- <span data-ttu-id="f7cc8-107">重複使用相同的參數化命令。</span><span class="sxs-lookup"><span data-stu-id="f7cc8-107">Reuse the same parameterized command.</span></span> <span data-ttu-id="f7cc8-108">後續執行會重複使用第一個執行的編譯。</span><span class="sxs-lookup"><span data-stu-id="f7cc8-108">Subsequent executions will reuse the compilation of the first one.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BulkInsertSample/Program.cs?name=snippet_BulkInsert)]
