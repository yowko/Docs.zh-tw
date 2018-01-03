---
title: "查詢運算式 (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c36f327b-e230-48d4-bbd5-78dc6478c447
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 8ad130797be55b33b319ca4e85de09ec3e00a554
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="query-expressions-entity-sql"></a><span data-ttu-id="8ea84-102">查詢運算式 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8ea84-102">Query Expressions (Entity SQL)</span></span>
<span data-ttu-id="8ea84-103">查詢運算式將許多不同的查詢運算子結合成單一語法。</span><span class="sxs-lookup"><span data-stu-id="8ea84-103">A query expression combines many different query operators into a single syntax.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8ea84-104">提供許多不同種類的運算式，包括下列：[常值](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md)，[參數](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)，[變數](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md)，運算子[函式](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)、 設定運算子，等等。</span><span class="sxs-lookup"><span data-stu-id="8ea84-104"> provides various kinds of expressions, including the following: [literals](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md), [parameters](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md), [variables](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md), operators, [functions](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md), set operators, and so on.</span></span> <span data-ttu-id="8ea84-105">如需詳細資訊，請參閱[Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="8ea84-105">For more information, see [Entity SQL Reference](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md).</span></span>  
  
## <a name="clauses"></a><span data-ttu-id="8ea84-106">子句</span><span class="sxs-lookup"><span data-stu-id="8ea84-106">Clauses</span></span>  
 <span data-ttu-id="8ea84-107">查詢運算式是由一系列將後續運算套用到物件集合的子句組成。</span><span class="sxs-lookup"><span data-stu-id="8ea84-107">A query expression is composed of a series of clauses that apply successive operations to a collection of objects.</span></span> <span data-ttu-id="8ea84-108">它們所根據相同的子句中標準 SQL select 陳述式：[選取](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)， [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md)，[其中](../../../../../../docs/framework/data/adonet/ef/language-reference/where-entity-sql.md)， [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md)， [具有](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md)，和[ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="8ea84-108">They are based on the same clauses found in standard a SQL select statement: [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md), [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [WHERE](../../../../../../docs/framework/data/adonet/ef/language-reference/where-entity-sql.md), [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md), and [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md).</span></span>  
  
## <a name="scope"></a><span data-ttu-id="8ea84-109">範圍</span><span class="sxs-lookup"><span data-stu-id="8ea84-109">Scope</span></span>  
 <span data-ttu-id="8ea84-110">FROM 子句中定義的名稱會依出現的順序 (從左到右) 導入 FROM 範圍內。</span><span class="sxs-lookup"><span data-stu-id="8ea84-110">Names defined in the FROM clause are introduced into the FROM scope in order of appearance, left to right.</span></span> <span data-ttu-id="8ea84-111">在 JOIN 清單中，運算式可以參考之前定義在清單中的名稱。</span><span class="sxs-lookup"><span data-stu-id="8ea84-111">In the JOIN list, expressions can refer to names defined earlier in the list.</span></span> <span data-ttu-id="8ea84-112">FROM 子句中所識別項目的公用屬性不會加入到 FROM 範圍：它們一定要透過別名限定的名稱來參考。</span><span class="sxs-lookup"><span data-stu-id="8ea84-112">Public properties of elements identified in the FROM clause are not added to the FROM scope: They must be always referenced through the alias-qualified name.</span></span> <span data-ttu-id="8ea84-113">一般而言，SELECT 運算式的所有部分都視為在 FROM 範圍中。</span><span class="sxs-lookup"><span data-stu-id="8ea84-113">Normally, all parts of the select expression are considered within the FROM scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ea84-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="8ea84-114">See Also</span></span>  
 [<span data-ttu-id="8ea84-115">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="8ea84-115">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
