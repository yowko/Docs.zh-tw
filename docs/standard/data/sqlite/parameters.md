---
title: 參數
ms.date: 12/13/2019
description: 瞭解如何使用 SQL 參數。
ms.openlocfilehash: 1d2f818ad392a919faedd785394de28a9c6f56c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400453"
---
# <a name="parameters"></a><span data-ttu-id="6de94-103">參數</span><span class="sxs-lookup"><span data-stu-id="6de94-103">Parameters</span></span>

<span data-ttu-id="6de94-104">參數用於防止 SQL 注入攻擊。</span><span class="sxs-lookup"><span data-stu-id="6de94-104">Parameters are used to protect against SQL injection attacks.</span></span> <span data-ttu-id="6de94-105">使用參數確保輸入僅被視為文本值，並且永遠不會執行，而不是將使用者輸入與 SQL 語句串聯。</span><span class="sxs-lookup"><span data-stu-id="6de94-105">Instead of concatenating user input with SQL statements, use parameters to ensure input is only ever treated as a literal value and never executed.</span></span> <span data-ttu-id="6de94-106">在 SQLite 中，參數通常允許在 SQL 語句中允許文本的任何位置。</span><span class="sxs-lookup"><span data-stu-id="6de94-106">In SQLite, parameters are typically allowed anywhere a literal is allowed in SQL statements.</span></span>

<span data-ttu-id="6de94-107">參數可以使用`:`或`@``$`的預綴。</span><span class="sxs-lookup"><span data-stu-id="6de94-107">Parameters can be prefixed with either `:`, `@`, or `$`.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_Parameter)]

<span data-ttu-id="6de94-108">有關如何將 .NET 值對應到 SQLite 值的詳細資訊，請參閱[資料類型](types.md)。</span><span class="sxs-lookup"><span data-stu-id="6de94-108">See [Data types](types.md) for details about how .NET values are mapped to SQLite values.</span></span>

## <a name="truncation"></a><span data-ttu-id="6de94-109">截斷</span><span class="sxs-lookup"><span data-stu-id="6de94-109">Truncation</span></span>

<span data-ttu-id="6de94-110">使用<xref:Microsoft.Data.Sqlite.SqliteParameter.Size>屬性截截 TEXT 和 BLOB 值。</span><span class="sxs-lookup"><span data-stu-id="6de94-110">Use the <xref:Microsoft.Data.Sqlite.SqliteParameter.Size> property to truncate TEXT and BLOB values.</span></span>

```csharp
// Truncate name to 30 characters
command.Parameters.AddWithValue("$name", name).Length = 30;
```

## <a name="alternative-types"></a><span data-ttu-id="6de94-111">替代類型</span><span class="sxs-lookup"><span data-stu-id="6de94-111">Alternative types</span></span>

<span data-ttu-id="6de94-112">有時，您可能需要使用替代 SQLite 類型。</span><span class="sxs-lookup"><span data-stu-id="6de94-112">Sometimes, you may want to use an alternative SQLite type.</span></span> <span data-ttu-id="6de94-113">通過設置屬性來<xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType>執行此操作。</span><span class="sxs-lookup"><span data-stu-id="6de94-113">Do this by setting the <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType> property.</span></span>

<span data-ttu-id="6de94-114">可以使用以下替代類型映射。</span><span class="sxs-lookup"><span data-stu-id="6de94-114">The following alternative type mappings can be used.</span></span> <span data-ttu-id="6de94-115">有關預設映射，請參閱[資料類型](types.md)。</span><span class="sxs-lookup"><span data-stu-id="6de94-115">For the default mappings, see [Data types](types.md).</span></span>

| <span data-ttu-id="6de94-116">值</span><span class="sxs-lookup"><span data-stu-id="6de94-116">Value</span></span>          | <span data-ttu-id="6de94-117">Sqlite 類型</span><span class="sxs-lookup"><span data-stu-id="6de94-117">SqliteType</span></span> | <span data-ttu-id="6de94-118">備註</span><span class="sxs-lookup"><span data-stu-id="6de94-118">Remarks</span></span>          |
| -------------- | ---------- | ---------------- |
| <span data-ttu-id="6de94-119">Char</span><span class="sxs-lookup"><span data-stu-id="6de94-119">Char</span></span>           | <span data-ttu-id="6de94-120">整數 </span><span class="sxs-lookup"><span data-stu-id="6de94-120">Integer</span></span>    | <span data-ttu-id="6de94-121">UTF-16</span><span class="sxs-lookup"><span data-stu-id="6de94-121">UTF-16</span></span>           |
| <span data-ttu-id="6de94-122">Datetime</span><span class="sxs-lookup"><span data-stu-id="6de94-122">DateTime</span></span>       | <span data-ttu-id="6de94-123">Real</span><span class="sxs-lookup"><span data-stu-id="6de94-123">Real</span></span>       | <span data-ttu-id="6de94-124">朱利安日值</span><span class="sxs-lookup"><span data-stu-id="6de94-124">Julian day value</span></span> |
| <span data-ttu-id="6de94-125">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="6de94-125">DateTimeOffset</span></span> | <span data-ttu-id="6de94-126">Real</span><span class="sxs-lookup"><span data-stu-id="6de94-126">Real</span></span>       | <span data-ttu-id="6de94-127">朱利安日值</span><span class="sxs-lookup"><span data-stu-id="6de94-127">Julian day value</span></span> |
| <span data-ttu-id="6de94-128">Guid</span><span class="sxs-lookup"><span data-stu-id="6de94-128">Guid</span></span>           | <span data-ttu-id="6de94-129">Blob</span><span class="sxs-lookup"><span data-stu-id="6de94-129">Blob</span></span>       |                  |
| <span data-ttu-id="6de94-130">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="6de94-130">TimeSpan</span></span>       | <span data-ttu-id="6de94-131">Real</span><span class="sxs-lookup"><span data-stu-id="6de94-131">Real</span></span>       | <span data-ttu-id="6de94-132">在幾天內</span><span class="sxs-lookup"><span data-stu-id="6de94-132">In days</span></span>          |

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_SqliteType)]

## <a name="output-parameters"></a><span data-ttu-id="6de94-133">輸出參數</span><span class="sxs-lookup"><span data-stu-id="6de94-133">Output parameters</span></span>

<span data-ttu-id="6de94-134">SQLite 不支援輸出參數。</span><span class="sxs-lookup"><span data-stu-id="6de94-134">SQLite doesn't support output parameters.</span></span> <span data-ttu-id="6de94-135">返回查詢結果中的值。</span><span class="sxs-lookup"><span data-stu-id="6de94-135">Return values in the query results instead.</span></span>

## <a name="see-also"></a><span data-ttu-id="6de94-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6de94-136">See also</span></span>

* [<span data-ttu-id="6de94-137">資料類型</span><span class="sxs-lookup"><span data-stu-id="6de94-137">Data types</span></span>](types.md)
