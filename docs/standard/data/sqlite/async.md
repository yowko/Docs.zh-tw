---
title: 非同步限制
ms.date: 09/04/2020
description: 說明非同步 Api 的限制，以及您可以改用的一些替代方案。
ms.openlocfilehash: 8b14fcfeb12d331d8d43ca6d77332007a12ae5dc
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89515991"
---
# <a name="async-limitations"></a><span data-ttu-id="87533-103">非同步限制</span><span class="sxs-lookup"><span data-stu-id="87533-103">Async limitations</span></span>

<span data-ttu-id="87533-104">SQLite 不支援非同步 i/o。</span><span class="sxs-lookup"><span data-stu-id="87533-104">SQLite doesn't support asynchronous I/O.</span></span> <span data-ttu-id="87533-105">非同步 ADO.NET 方法會在 Microsoft 中以同步方式執行。</span><span class="sxs-lookup"><span data-stu-id="87533-105">Async ADO.NET methods will execute synchronously in Microsoft.Data.Sqlite.</span></span> <span data-ttu-id="87533-106">避免呼叫它們。</span><span class="sxs-lookup"><span data-stu-id="87533-106">Avoid calling them.</span></span>

<span data-ttu-id="87533-107">相反地，請使用 [共用](connection-strings.md#cache) 快取和預先 [寫入記錄](https://www.sqlite.org/wal.html) ，以改善效能和平行存取。</span><span class="sxs-lookup"><span data-stu-id="87533-107">Instead, use a [shared cache](connection-strings.md#cache) and [write-ahead logging](https://www.sqlite.org/wal.html) to improve performance and concurrency.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/AsyncSample/Program.cs?name=snippet_WAL)]

> [!TIP]
> <span data-ttu-id="87533-108">依預設，會在使用 [Entity Framework Core](/ef/core/)建立的資料庫上啟用預先寫入記錄。</span><span class="sxs-lookup"><span data-stu-id="87533-108">Write-ahead logging is enabled by default on databases created using [Entity Framework Core](/ef/core/).</span></span>
