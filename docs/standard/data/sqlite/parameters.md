---
title: 參數
ms.date: 12/13/2019
description: 瞭解如何使用 SQL 參數。
ms.openlocfilehash: 1d2f818ad392a919faedd785394de28a9c6f56c3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447185"
---
# <a name="parameters"></a><span data-ttu-id="f20c1-103">參數</span><span class="sxs-lookup"><span data-stu-id="f20c1-103">Parameters</span></span>

<span data-ttu-id="f20c1-104">參數是用來防止 SQL 插入式攻擊。</span><span class="sxs-lookup"><span data-stu-id="f20c1-104">Parameters are used to protect against SQL injection attacks.</span></span> <span data-ttu-id="f20c1-105">請使用參數來確保輸入只會被視為常值，而且永遠不會執行，而不會將使用者輸入與 SQL 語句串連。</span><span class="sxs-lookup"><span data-stu-id="f20c1-105">Instead of concatenating user input with SQL statements, use parameters to ensure input is only ever treated as a literal value and never executed.</span></span> <span data-ttu-id="f20c1-106">在 SQLite 中，參數通常可在 SQL 語句中允許常值的任何位置使用。</span><span class="sxs-lookup"><span data-stu-id="f20c1-106">In SQLite, parameters are typically allowed anywhere a literal is allowed in SQL statements.</span></span>

<span data-ttu-id="f20c1-107">參數的前面可以是 `:`、`@`或 `$`。</span><span class="sxs-lookup"><span data-stu-id="f20c1-107">Parameters can be prefixed with either `:`, `@`, or `$`.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_Parameter)]

<span data-ttu-id="f20c1-108">如需 .NET 值如何對應至 SQLite 值的詳細資訊，請參閱[資料類型](types.md)。</span><span class="sxs-lookup"><span data-stu-id="f20c1-108">See [Data types](types.md) for details about how .NET values are mapped to SQLite values.</span></span>

## <a name="truncation"></a><span data-ttu-id="f20c1-109">截斷</span><span class="sxs-lookup"><span data-stu-id="f20c1-109">Truncation</span></span>

<span data-ttu-id="f20c1-110">使用 <xref:Microsoft.Data.Sqlite.SqliteParameter.Size> 屬性來截斷文字和 BLOB 值。</span><span class="sxs-lookup"><span data-stu-id="f20c1-110">Use the <xref:Microsoft.Data.Sqlite.SqliteParameter.Size> property to truncate TEXT and BLOB values.</span></span>

```csharp
// Truncate name to 30 characters
command.Parameters.AddWithValue("$name", name).Length = 30;
```

## <a name="alternative-types"></a><span data-ttu-id="f20c1-111">替代類型</span><span class="sxs-lookup"><span data-stu-id="f20c1-111">Alternative types</span></span>

<span data-ttu-id="f20c1-112">有時候，您可能會想要使用替代的 SQLite 類型。</span><span class="sxs-lookup"><span data-stu-id="f20c1-112">Sometimes, you may want to use an alternative SQLite type.</span></span> <span data-ttu-id="f20c1-113">藉由設定 <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType> 屬性來執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="f20c1-113">Do this by setting the <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType> property.</span></span>

<span data-ttu-id="f20c1-114">您可以使用下列替代型別對應。</span><span class="sxs-lookup"><span data-stu-id="f20c1-114">The following alternative type mappings can be used.</span></span> <span data-ttu-id="f20c1-115">如需預設對應，請參閱[資料類型](types.md)。</span><span class="sxs-lookup"><span data-stu-id="f20c1-115">For the default mappings, see [Data types](types.md).</span></span>

| <span data-ttu-id="f20c1-116">{2&gt;值&lt;2}</span><span class="sxs-lookup"><span data-stu-id="f20c1-116">Value</span></span>          | <span data-ttu-id="f20c1-117">SqliteType</span><span class="sxs-lookup"><span data-stu-id="f20c1-117">SqliteType</span></span> | <span data-ttu-id="f20c1-118">備註</span><span class="sxs-lookup"><span data-stu-id="f20c1-118">Remarks</span></span>          |
| -------------- | ---------- | ---------------- |
| <span data-ttu-id="f20c1-119">Char</span><span class="sxs-lookup"><span data-stu-id="f20c1-119">Char</span></span>           | <span data-ttu-id="f20c1-120">整數</span><span class="sxs-lookup"><span data-stu-id="f20c1-120">Integer</span></span>    | <span data-ttu-id="f20c1-121">UTF-16</span><span class="sxs-lookup"><span data-stu-id="f20c1-121">UTF-16</span></span>           |
| <span data-ttu-id="f20c1-122">DateTime</span><span class="sxs-lookup"><span data-stu-id="f20c1-122">DateTime</span></span>       | <span data-ttu-id="f20c1-123">Real</span><span class="sxs-lookup"><span data-stu-id="f20c1-123">Real</span></span>       | <span data-ttu-id="f20c1-124">Julian 日值</span><span class="sxs-lookup"><span data-stu-id="f20c1-124">Julian day value</span></span> |
| <span data-ttu-id="f20c1-125">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="f20c1-125">DateTimeOffset</span></span> | <span data-ttu-id="f20c1-126">Real</span><span class="sxs-lookup"><span data-stu-id="f20c1-126">Real</span></span>       | <span data-ttu-id="f20c1-127">Julian 日值</span><span class="sxs-lookup"><span data-stu-id="f20c1-127">Julian day value</span></span> |
| <span data-ttu-id="f20c1-128">GUID</span><span class="sxs-lookup"><span data-stu-id="f20c1-128">Guid</span></span>           | <span data-ttu-id="f20c1-129">blob</span><span class="sxs-lookup"><span data-stu-id="f20c1-129">Blob</span></span>       |                  |
| <span data-ttu-id="f20c1-130">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="f20c1-130">TimeSpan</span></span>       | <span data-ttu-id="f20c1-131">Real</span><span class="sxs-lookup"><span data-stu-id="f20c1-131">Real</span></span>       | <span data-ttu-id="f20c1-132">以天為單位</span><span class="sxs-lookup"><span data-stu-id="f20c1-132">In days</span></span>          |

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_SqliteType)]

## <a name="output-parameters"></a><span data-ttu-id="f20c1-133">輸出參數</span><span class="sxs-lookup"><span data-stu-id="f20c1-133">Output parameters</span></span>

<span data-ttu-id="f20c1-134">SQLite 不支援輸出參數。</span><span class="sxs-lookup"><span data-stu-id="f20c1-134">SQLite doesn't support output parameters.</span></span> <span data-ttu-id="f20c1-135">改為傳回查詢結果中的值。</span><span class="sxs-lookup"><span data-stu-id="f20c1-135">Return values in the query results instead.</span></span>

## <a name="see-also"></a><span data-ttu-id="f20c1-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="f20c1-136">See also</span></span>

* [<span data-ttu-id="f20c1-137">資料類型</span><span class="sxs-lookup"><span data-stu-id="f20c1-137">Data types</span></span>](types.md)
