---
title: 查詢運算式 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c36f327b-e230-48d4-bbd5-78dc6478c447
ms.openlocfilehash: 4428286890f41573a02daf31a4593d0c8f9ad34b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249280"
---
# <a name="query-expressions-entity-sql"></a><span data-ttu-id="02ae0-102">查詢運算式 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="02ae0-102">Query Expressions (Entity SQL)</span></span>
<span data-ttu-id="02ae0-103">查詢運算式將許多不同的查詢運算子結合成單一語法。</span><span class="sxs-lookup"><span data-stu-id="02ae0-103">A query expression combines many different query operators into a single syntax.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="02ae0-104">提供各種類型的運算式，包括：[常值](literals-entity-sql.md)、[參數](parameters-entity-sql.md)、[變數](variables-entity-sql.md)、運算子、[函式](functions-entity-sql.md)、集合運算子等等。</span><span class="sxs-lookup"><span data-stu-id="02ae0-104">provides various kinds of expressions, including the following: [literals](literals-entity-sql.md), [parameters](parameters-entity-sql.md), [variables](variables-entity-sql.md), operators, [functions](functions-entity-sql.md), set operators, and so on.</span></span> <span data-ttu-id="02ae0-105">如需詳細資訊，請參閱[Entity SQL 參考](entity-sql-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="02ae0-105">For more information, see [Entity SQL Reference](entity-sql-reference.md).</span></span>  
  
## <a name="clauses"></a><span data-ttu-id="02ae0-106">子句</span><span class="sxs-lookup"><span data-stu-id="02ae0-106">Clauses</span></span>  
 <span data-ttu-id="02ae0-107">查詢運算式是由一系列將後續運算套用到物件集合的子句組成。</span><span class="sxs-lookup"><span data-stu-id="02ae0-107">A query expression is composed of a series of clauses that apply successive operations to a collection of objects.</span></span> <span data-ttu-id="02ae0-108">它們是以在標準 SQL select 語句中找到的相同子句為基礎：[SELECT](select-entity-sql.md)、 [FROM](from-entity-sql.md)、 [WHERE](where-entity-sql.md)、 [GROUP BY](group-by-entity-sql.md)、 [HAVING](having-entity-sql.md)和[ORDER by](order-by-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="02ae0-108">They are based on the same clauses found in standard a SQL select statement: [SELECT](select-entity-sql.md), [FROM](from-entity-sql.md), [WHERE](where-entity-sql.md), [GROUP BY](group-by-entity-sql.md), [HAVING](having-entity-sql.md), and [ORDER BY](order-by-entity-sql.md).</span></span>  
  
## <a name="scope"></a><span data-ttu-id="02ae0-109">`Scope`</span><span class="sxs-lookup"><span data-stu-id="02ae0-109">Scope</span></span>  
 <span data-ttu-id="02ae0-110">FROM 子句中定義的名稱會依出現的順序 (從左到右) 導入 FROM 範圍內。</span><span class="sxs-lookup"><span data-stu-id="02ae0-110">Names defined in the FROM clause are introduced into the FROM scope in order of appearance, left to right.</span></span> <span data-ttu-id="02ae0-111">在 JOIN 清單中，運算式可以參考之前定義在清單中的名稱。</span><span class="sxs-lookup"><span data-stu-id="02ae0-111">In the JOIN list, expressions can refer to names defined earlier in the list.</span></span> <span data-ttu-id="02ae0-112">在 FROM 子句中識別之元素的公用屬性不會加入至 FROM 範圍：必須一律透過別名限定的名稱來參考它們。</span><span class="sxs-lookup"><span data-stu-id="02ae0-112">Public properties of elements identified in the FROM clause are not added to the FROM scope: They must be always referenced through the alias-qualified name.</span></span> <span data-ttu-id="02ae0-113">一般而言，SELECT 運算式的所有部分都視為在 FROM 範圍中。</span><span class="sxs-lookup"><span data-stu-id="02ae0-113">Normally, all parts of the select expression are considered within the FROM scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02ae0-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02ae0-114">See also</span></span>

- [<span data-ttu-id="02ae0-115">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="02ae0-115">Entity SQL Reference</span></span>](entity-sql-reference.md)
