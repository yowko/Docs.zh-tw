---
title: SKIP (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: 19d3001fb8f226b02f16167dfb51ce1caa80ba3b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249225"
---
# <a name="skip-entity-sql"></a><span data-ttu-id="5595c-102">SKIP (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="5595c-102">SKIP (Entity SQL)</span></span>

<span data-ttu-id="5595c-103">您可以在 ORDER BY 子句中使用 SKIP 子句執行實際分頁。</span><span class="sxs-lookup"><span data-stu-id="5595c-103">You can perform physical paging by using the SKIP sub-clause in the ORDER BY clause.</span></span> <span data-ttu-id="5595c-104">SKIP 不可單獨使用於 ORDER BY 子句之外。</span><span class="sxs-lookup"><span data-stu-id="5595c-104">SKIP cannot be used separately from the ORDER BY clause.</span></span>

## <a name="syntax"></a><span data-ttu-id="5595c-105">語法</span><span class="sxs-lookup"><span data-stu-id="5595c-105">Syntax</span></span>

```
[ SKIP n ]
```

## <a name="arguments"></a><span data-ttu-id="5595c-106">引數</span><span class="sxs-lookup"><span data-stu-id="5595c-106">Arguments</span></span>

`n` \
<span data-ttu-id="5595c-107">要略過的項目數目。</span><span class="sxs-lookup"><span data-stu-id="5595c-107">The number of items to skip.</span></span>

## <a name="remarks"></a><span data-ttu-id="5595c-108">備註</span><span class="sxs-lookup"><span data-stu-id="5595c-108">Remarks</span></span>

<span data-ttu-id="5595c-109">如果 ORDER BY 子句中有 SKIP 運算式次子句，結果將會依據排序規格排序，而且結果集將會包括從 SKIP 運算式後面一個資料列開始的資料列。</span><span class="sxs-lookup"><span data-stu-id="5595c-109">If a SKIP expression sub-clause is present in an ORDER BY clause, the results will be sorted according the sort specification and the result set will include rows starting from the next row immediately after the SKIP expression.</span></span> <span data-ttu-id="5595c-110">例如，SKIP 5 將會略過前五個資料列，並且傳回從第六個資料列以後的資料列。</span><span class="sxs-lookup"><span data-stu-id="5595c-110">For example, SKIP 5 will skip the first five rows and return from the sixth row forward.</span></span>

> [!NOTE]
> <span data-ttu-id="5595c-111">如果 TOP 修飾詞和 SKIP 之子句兩者出現在同一個查詢運算式中，則 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢會變成無效。</span><span class="sxs-lookup"><span data-stu-id="5595c-111">An [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query is invalid if both the TOP modifier and the SKIP sub-clause are present in the same query expression.</span></span> <span data-ttu-id="5595c-112">請將 TOP 運算式變更為 LIMIT 運算式來重新撰寫此查詢。</span><span class="sxs-lookup"><span data-stu-id="5595c-112">The query should be rewritten by changing the TOP expression to the LIMIT expression.</span></span>

> [!NOTE]
> <span data-ttu-id="5595c-113">在 SQL Server 2000 中, 在非索引鍵資料行上使用 SKIP 搭配 ORDER BY 可能會傳回不正確的結果。</span><span class="sxs-lookup"><span data-stu-id="5595c-113">In SQL Server 2000, using SKIP with ORDER BY on non-key columns might return incorrect results.</span></span> <span data-ttu-id="5595c-114">如果非索引鍵資料行中有重複的資料，可能會略過超過所指定數目的資料行。</span><span class="sxs-lookup"><span data-stu-id="5595c-114">More than the specified number of rows might be skipped if the non-key column has duplicate data in it.</span></span> <span data-ttu-id="5595c-115">這是因為 SQL Server 2000 的略過轉譯方式所致。</span><span class="sxs-lookup"><span data-stu-id="5595c-115">This is due to how SKIP is translated for SQL Server 2000.</span></span> <span data-ttu-id="5595c-116">舉例來講，在以下程式碼中，如果 `E.NonKeyColumn` 中有重複的值，就會略過超過五個資料行：</span><span class="sxs-lookup"><span data-stu-id="5595c-116">For example, in the following code more than five rows might be skipped if `E.NonKeyColumn` has duplicate values:</span></span>
>
> `SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L`

<span data-ttu-id="5595c-117">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中[的查詢如何:透過查詢結果](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))的頁面會使用 ORDER BY 運算子搭配 SKIP 來指定 SELECT 語句所傳回之物件所使用的排序次序。</span><span class="sxs-lookup"><span data-stu-id="5595c-117">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query in [How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) uses the ORDER BY operator with SKIP to specify the sort order used on objects returned in a SELECT statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="5595c-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5595c-118">See also</span></span>

- [<span data-ttu-id="5595c-119">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="5595c-119">ORDER BY</span></span>](order-by-entity-sql.md)
- <span data-ttu-id="5595c-120">[如何：逐頁查看查詢結果](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5595c-120">[How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>
- [<span data-ttu-id="5595c-121">分頁</span><span class="sxs-lookup"><span data-stu-id="5595c-121">Paging</span></span>](paging-entity-sql.md)
- [<span data-ttu-id="5595c-122">TOP</span><span class="sxs-lookup"><span data-stu-id="5595c-122">TOP</span></span>](top-entity-sql.md)
