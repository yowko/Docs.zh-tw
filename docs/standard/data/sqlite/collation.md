---
title: Collation
ms.date: 12/13/2019
description: 瞭解如何建立自訂的排序次序。
ms.openlocfilehash: 9cc574a75c8f5347dd9bb44e36af72e50afa57b4
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777379"
---
# <a name="collation"></a><span data-ttu-id="b9c13-103">Collation</span><span class="sxs-lookup"><span data-stu-id="b9c13-103">Collation</span></span>

<span data-ttu-id="b9c13-104">比較文字值以判斷順序和相等時，SQLite 會使用排序次序。</span><span class="sxs-lookup"><span data-stu-id="b9c13-104">Collating sequences are used by SQLite when comparing TEXT values to determine order and equality.</span></span> <span data-ttu-id="b9c13-105">您可以指定在 SQL 查詢中建立資料行或每個作業時要使用的定序。</span><span class="sxs-lookup"><span data-stu-id="b9c13-105">You can specify which collation to use when creating columns or per-operation in SQL queries.</span></span> <span data-ttu-id="b9c13-106">SQLite 預設包含三個排序次序。</span><span class="sxs-lookup"><span data-stu-id="b9c13-106">SQLite includes three collating sequences by default.</span></span>

| <span data-ttu-id="b9c13-107">Collation</span><span class="sxs-lookup"><span data-stu-id="b9c13-107">Collation</span></span> | <span data-ttu-id="b9c13-108">描述</span><span class="sxs-lookup"><span data-stu-id="b9c13-108">Description</span></span>                               |
| --------- | ----------------------------------------- |
| <span data-ttu-id="b9c13-109">RTRIM</span><span class="sxs-lookup"><span data-stu-id="b9c13-109">RTRIM</span></span>     | <span data-ttu-id="b9c13-110">忽略尾端空白</span><span class="sxs-lookup"><span data-stu-id="b9c13-110">Ignores trailing whitespace</span></span>               |
| <span data-ttu-id="b9c13-111">NOCASE</span><span class="sxs-lookup"><span data-stu-id="b9c13-111">NOCASE</span></span>    | <span data-ttu-id="b9c13-112">ASCII 字元 a-z 的不區分大小寫</span><span class="sxs-lookup"><span data-stu-id="b9c13-112">Case-insensitive for ASCII characters A-Z</span></span> |
| <span data-ttu-id="b9c13-113">BINARY</span><span class="sxs-lookup"><span data-stu-id="b9c13-113">BINARY</span></span>    | <span data-ttu-id="b9c13-114">區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="b9c13-114">Case-sensitive.</span></span> <span data-ttu-id="b9c13-115">直接比較位元組</span><span class="sxs-lookup"><span data-stu-id="b9c13-115">Compares bytes directly</span></span>   |

## <a name="custom-collation"></a><span data-ttu-id="b9c13-116">自訂定序</span><span class="sxs-lookup"><span data-stu-id="b9c13-116">Custom collation</span></span>

<span data-ttu-id="b9c13-117">您也可以定義自己的定序序列，或使用 <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>覆寫內建的排序次序。</span><span class="sxs-lookup"><span data-stu-id="b9c13-117">You can also define your own collating sequences or override the built-in ones using <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>.</span></span> <span data-ttu-id="b9c13-118">下列範例會顯示覆寫 NOCASE 定序以支援 Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="b9c13-118">The following example shows overriding the NOCASE collation to support Unicode characters.</span></span> <span data-ttu-id="b9c13-119">[完整的範例程式碼](https://github.com/dotnet/samples/blob/master/snippets/standard/data/sqlite/CollationSample/Program.cs)可在 GitHub 上取得。</span><span class="sxs-lookup"><span data-stu-id="b9c13-119">The [full sample code](https://github.com/dotnet/samples/blob/master/snippets/standard/data/sqlite/CollationSample/Program.cs) is available on GitHub.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/CollationSample/Program.cs?name=snippet_Collation)]

## <a name="like-operator"></a><span data-ttu-id="b9c13-120">Like 運算子</span><span class="sxs-lookup"><span data-stu-id="b9c13-120">Like operator</span></span>

<span data-ttu-id="b9c13-121">SQLite 中的 LIKE 運算子不接受定序。</span><span class="sxs-lookup"><span data-stu-id="b9c13-121">The LIKE operator in SQLite doesn't honor collations.</span></span> <span data-ttu-id="b9c13-122">預設的實作為與 NOCASE 定序相同的語義。</span><span class="sxs-lookup"><span data-stu-id="b9c13-122">The default implementation has the same semantics as the NOCASE collation.</span></span> <span data-ttu-id="b9c13-123">ASCII 字元 A 到 Z 只會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="b9c13-123">It's only case-insensitive for the ASCII characters A through Z.</span></span>

<span data-ttu-id="b9c13-124">您可以使用下列 pragma 語句，輕鬆地讓 LIKE 運算子區分大小寫：</span><span class="sxs-lookup"><span data-stu-id="b9c13-124">You can easily make the LIKE operator case-sensitive by using the following pragma statement:</span></span>

```sql
PRAGMA case_sensitive_like = 0
```

<span data-ttu-id="b9c13-125">如需覆寫 LIKE 運算子之執行的詳細資訊，請參閱[使用者定義函數](user-defined-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="b9c13-125">See [User-defined functions](user-defined-functions.md) for details on overriding the implementation of the LIKE operator.</span></span>

## <a name="see-also"></a><span data-ttu-id="b9c13-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="b9c13-126">See also</span></span>

* [<span data-ttu-id="b9c13-127">使用者定義的函式</span><span class="sxs-lookup"><span data-stu-id="b9c13-127">User-defined functions</span></span>](user-defined-functions.md)
* [<span data-ttu-id="b9c13-128">SQL 語法</span><span class="sxs-lookup"><span data-stu-id="b9c13-128">SQL Syntax</span></span>](https://www.sqlite.org/lang.html)
