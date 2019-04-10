---
title: 運算子優先順序 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
ms.openlocfilehash: 722ebe5f0ec530f8c7f86e9f9901451b060903f0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59159129"
---
# <a name="operator-precedence-entity-sql"></a><span data-ttu-id="7bd8d-102">運算子優先順序 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="7bd8d-102">Operator Precedence (Entity SQL)</span></span>
<span data-ttu-id="7bd8d-103">當[!INCLUDE[esql](../../../../../../includes/esql-md.md)]查詢有多個運算子，運算子優先順序會決定作業的執行的順序。</span><span class="sxs-lookup"><span data-stu-id="7bd8d-103">When an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query has multiple operators, operator precedence determines the sequence in which the operations are performed.</span></span> <span data-ttu-id="7bd8d-104">執行的順序對於查詢結果有很大的影響。</span><span class="sxs-lookup"><span data-stu-id="7bd8d-104">The order of execution can significantly affect the query result.</span></span>  
  
 <span data-ttu-id="7bd8d-105">下表顯示運算子的優先順序層級。</span><span class="sxs-lookup"><span data-stu-id="7bd8d-105">Operators have the precedence levels shown in the following table.</span></span> <span data-ttu-id="7bd8d-106">先評估層級較高的運算子，再評估層級較低的運算子。</span><span class="sxs-lookup"><span data-stu-id="7bd8d-106">An operator with a higher level is evaluated before an operator with a lower level.</span></span>  
  
|<span data-ttu-id="7bd8d-107">層級</span><span class="sxs-lookup"><span data-stu-id="7bd8d-107">Level</span></span>|<span data-ttu-id="7bd8d-108">運算類型</span><span class="sxs-lookup"><span data-stu-id="7bd8d-108">Operation type</span></span>|<span data-ttu-id="7bd8d-109">運算子</span><span class="sxs-lookup"><span data-stu-id="7bd8d-109">Operator</span></span>|  
|-----------|--------------------|--------------|  
|<span data-ttu-id="7bd8d-110">1</span><span class="sxs-lookup"><span data-stu-id="7bd8d-110">1</span></span>|<span data-ttu-id="7bd8d-111">主要</span><span class="sxs-lookup"><span data-stu-id="7bd8d-111">Primary</span></span>|`. , [] ()`|  
|<span data-ttu-id="7bd8d-112">2</span><span class="sxs-lookup"><span data-stu-id="7bd8d-112">2</span></span>|<span data-ttu-id="7bd8d-113">一元</span><span class="sxs-lookup"><span data-stu-id="7bd8d-113">Unary</span></span>|`! not`|  
|<span data-ttu-id="7bd8d-114">3</span><span class="sxs-lookup"><span data-stu-id="7bd8d-114">3</span></span>|<span data-ttu-id="7bd8d-115">乘法類 (Multiplicative)</span><span class="sxs-lookup"><span data-stu-id="7bd8d-115">Multiplicative</span></span>|`* / %`|  
|<span data-ttu-id="7bd8d-116">4</span><span class="sxs-lookup"><span data-stu-id="7bd8d-116">4</span></span>|<span data-ttu-id="7bd8d-117">加法類 (Additive)</span><span class="sxs-lookup"><span data-stu-id="7bd8d-117">Additive</span></span>|`+ -`|  
|<span data-ttu-id="7bd8d-118">5</span><span class="sxs-lookup"><span data-stu-id="7bd8d-118">5</span></span>|<span data-ttu-id="7bd8d-119">排序</span><span class="sxs-lookup"><span data-stu-id="7bd8d-119">Ordering</span></span>|`< > <= >=`|  
|<span data-ttu-id="7bd8d-120">6</span><span class="sxs-lookup"><span data-stu-id="7bd8d-120">6</span></span>|<span data-ttu-id="7bd8d-121">相等</span><span class="sxs-lookup"><span data-stu-id="7bd8d-121">Equality</span></span>|`= != <>`|  
|<span data-ttu-id="7bd8d-122">7</span><span class="sxs-lookup"><span data-stu-id="7bd8d-122">7</span></span>|<span data-ttu-id="7bd8d-123">條件式 AND</span><span class="sxs-lookup"><span data-stu-id="7bd8d-123">Conditional AND</span></span>|`and &&`|  
|<span data-ttu-id="7bd8d-124">8</span><span class="sxs-lookup"><span data-stu-id="7bd8d-124">8</span></span>|<span data-ttu-id="7bd8d-125">條件式 OR</span><span class="sxs-lookup"><span data-stu-id="7bd8d-125">Conditional OR</span></span>|`or &#124;&#124;`|  
  
 <span data-ttu-id="7bd8d-126">當運算式中的兩個運算子有相同的運算子優先順序層級時，會依據它們在查詢中的位置，由左至右來評估它們。</span><span class="sxs-lookup"><span data-stu-id="7bd8d-126">When two operators in an expression have the same operator precedence level, they are evaluated left to right, based on their position in the query.</span></span> <span data-ttu-id="7bd8d-127">例如，`x+y-z` 會判斷值為 `(x+y)-z`。</span><span class="sxs-lookup"><span data-stu-id="7bd8d-127">For example, `x+y-z` is evaluated as `(x+y)-z`.</span></span>  
  
 <span data-ttu-id="7bd8d-128">您可以使用括號來覆寫查詢中已定義的運算子優先順序。</span><span class="sxs-lookup"><span data-stu-id="7bd8d-128">You can use parentheses to override the defined precedence of the operators in a query.</span></span> <span data-ttu-id="7bd8d-129">括號內的所有內容都會先評估得出單一結果，之後，括號外的任何運算子便可以使用這個結果。</span><span class="sxs-lookup"><span data-stu-id="7bd8d-129">Everything within parentheses is evaluated first to yield a single result before that result can be used by any operator outside the parentheses.</span></span> <span data-ttu-id="7bd8d-130">比方說，`x+y*z`乘以`y`所`z`，然後新增`x`，但`(x+y)*z`新增`x`來`y`，然後將結果乘以`z`。</span><span class="sxs-lookup"><span data-stu-id="7bd8d-130">For example, `x+y*z` multiplies `y` by `z` and then adds `x`, but `(x+y)*z` adds `x` to `y` and then multiplies the result by `z`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bd8d-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7bd8d-131">See also</span></span>

- [<span data-ttu-id="7bd8d-132">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="7bd8d-132">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
