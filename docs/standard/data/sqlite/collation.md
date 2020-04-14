---
title: 定序
ms.date: 12/13/2019
description: 瞭解如何創建自定義整理序列。
ms.openlocfilehash: 9879846cc191a62c4cb47a0fbaa47c59153ba61c
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242968"
---
# <a name="collation"></a><span data-ttu-id="b18b6-103">定序</span><span class="sxs-lookup"><span data-stu-id="b18b6-103">Collation</span></span>

<span data-ttu-id="b18b6-104">SQLite 在比較 TEXT 值以確定順序和相等性時使用分字序列。</span><span class="sxs-lookup"><span data-stu-id="b18b6-104">Collating sequences are used by SQLite when comparing TEXT values to determine order and equality.</span></span> <span data-ttu-id="b18b6-105">您可以指定在 SQL 查詢中建立列或每個操作時要使用的排序規則。</span><span class="sxs-lookup"><span data-stu-id="b18b6-105">You can specify which collation to use when creating columns or per-operation in SQL queries.</span></span> <span data-ttu-id="b18b6-106">預設情況下,SQLite 包括三個整理序列。</span><span class="sxs-lookup"><span data-stu-id="b18b6-106">SQLite includes three collating sequences by default.</span></span>

| <span data-ttu-id="b18b6-107">定序</span><span class="sxs-lookup"><span data-stu-id="b18b6-107">Collation</span></span> | <span data-ttu-id="b18b6-108">描述</span><span class="sxs-lookup"><span data-stu-id="b18b6-108">Description</span></span>                               |
| --------- | ----------------------------------------- |
| <span data-ttu-id="b18b6-109">RTRIM</span><span class="sxs-lookup"><span data-stu-id="b18b6-109">RTRIM</span></span>     | <span data-ttu-id="b18b6-110">忽略尾隨空格</span><span class="sxs-lookup"><span data-stu-id="b18b6-110">Ignores trailing whitespace</span></span>               |
| <span data-ttu-id="b18b6-111">無案例</span><span class="sxs-lookup"><span data-stu-id="b18b6-111">NOCASE</span></span>    | <span data-ttu-id="b18b6-112">ASCII 字元 A-Z 不區分大小寫</span><span class="sxs-lookup"><span data-stu-id="b18b6-112">Case-insensitive for ASCII characters A-Z</span></span> |
| <span data-ttu-id="b18b6-113">BINARY</span><span class="sxs-lookup"><span data-stu-id="b18b6-113">BINARY</span></span>    | <span data-ttu-id="b18b6-114">區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="b18b6-114">Case-sensitive.</span></span> <span data-ttu-id="b18b6-115">直接比較位元組</span><span class="sxs-lookup"><span data-stu-id="b18b6-115">Compares bytes directly</span></span>   |

## <a name="custom-collation"></a><span data-ttu-id="b18b6-116">自訂排序規則</span><span class="sxs-lookup"><span data-stu-id="b18b6-116">Custom collation</span></span>

<span data-ttu-id="b18b6-117">您可以定義的更新序列或使用 重寫的<xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>序列 。</span><span class="sxs-lookup"><span data-stu-id="b18b6-117">You can also define your own collating sequences or override the built-in ones using <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>.</span></span> <span data-ttu-id="b18b6-118">下面的範例顯示涵蓋 NOCASE 排序規則以支援 Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="b18b6-118">The following example shows overriding the NOCASE collation to support Unicode characters.</span></span> <span data-ttu-id="b18b6-119">[完整的範例代碼](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/CollationSample/Program.cs)在 GitHub 上可用。</span><span class="sxs-lookup"><span data-stu-id="b18b6-119">The [full sample code](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/CollationSample/Program.cs) is available on GitHub.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/CollationSample/Program.cs?name=snippet_Collation)]

## <a name="like-operator"></a><span data-ttu-id="b18b6-120">Like 運算子</span><span class="sxs-lookup"><span data-stu-id="b18b6-120">Like operator</span></span>

<span data-ttu-id="b18b6-121">SQLite 中的 LIKE 運算元不遵循排序規則。</span><span class="sxs-lookup"><span data-stu-id="b18b6-121">The LIKE operator in SQLite doesn't honor collations.</span></span> <span data-ttu-id="b18b6-122">預設實現具有與 NOCASE 排序規則相同的語義。</span><span class="sxs-lookup"><span data-stu-id="b18b6-122">The default implementation has the same semantics as the NOCASE collation.</span></span> <span data-ttu-id="b18b6-123">它僅對 ASCII 字元 A 到 Z 不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="b18b6-123">It's only case-insensitive for the ASCII characters A through Z.</span></span>

<span data-ttu-id="b18b6-124">通過使用以下雜注語句,可以輕鬆地使 LIKE 運算符區分大小寫:</span><span class="sxs-lookup"><span data-stu-id="b18b6-124">You can easily make the LIKE operator case-sensitive by using the following pragma statement:</span></span>

```sql
PRAGMA case_sensitive_like = 1
```

<span data-ttu-id="b18b6-125">有關重寫 LIKE 運算子實現的詳細資訊,請參閱[使用者定義的函數](user-defined-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="b18b6-125">See [User-defined functions](user-defined-functions.md) for details on overriding the implementation of the LIKE operator.</span></span>

## <a name="see-also"></a><span data-ttu-id="b18b6-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b18b6-126">See also</span></span>

* [<span data-ttu-id="b18b6-127">使用者自訂函數</span><span class="sxs-lookup"><span data-stu-id="b18b6-127">User-defined functions</span></span>](user-defined-functions.md)
* [<span data-ttu-id="b18b6-128">SQL 語法</span><span class="sxs-lookup"><span data-stu-id="b18b6-128">SQL Syntax</span></span>](https://www.sqlite.org/lang.html)
