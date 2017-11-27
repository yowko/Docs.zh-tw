---
title: "運算子優先順序 (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 484eedffeaffb625cd43352dadedb8c99fbc65ed
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="operator-precedence-entity-sql"></a><span data-ttu-id="e1939-102">運算子優先順序 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e1939-102">Operator Precedence (Entity SQL)</span></span>
<span data-ttu-id="e1939-103">當[!INCLUDE[esql](../../../../../../includes/esql-md.md)]查詢有多個運算子，運算子優先順序會決定作業的執行的順序。</span><span class="sxs-lookup"><span data-stu-id="e1939-103">When an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query has multiple operators, operator precedence determines the sequence in which the operations are performed.</span></span> <span data-ttu-id="e1939-104">執行的順序對於查詢結果有很大的影響。</span><span class="sxs-lookup"><span data-stu-id="e1939-104">The order of execution can significantly affect the query result.</span></span>  
  
 <span data-ttu-id="e1939-105">下表顯示運算子的優先順序層級。</span><span class="sxs-lookup"><span data-stu-id="e1939-105">Operators have the precedence levels shown in the following table.</span></span> <span data-ttu-id="e1939-106">先評估層級較高的運算子，再評估層級較低的運算子。</span><span class="sxs-lookup"><span data-stu-id="e1939-106">An operator with a higher level is evaluated before an operator with a lower level.</span></span>  
  
|<span data-ttu-id="e1939-107">層級</span><span class="sxs-lookup"><span data-stu-id="e1939-107">Level</span></span>|<span data-ttu-id="e1939-108">運算類型</span><span class="sxs-lookup"><span data-stu-id="e1939-108">Operation type</span></span>|<span data-ttu-id="e1939-109">運算子</span><span class="sxs-lookup"><span data-stu-id="e1939-109">Operator</span></span>|  
|-----------|--------------------|--------------|  
|<span data-ttu-id="e1939-110">1</span><span class="sxs-lookup"><span data-stu-id="e1939-110">1</span></span>|<span data-ttu-id="e1939-111">主要</span><span class="sxs-lookup"><span data-stu-id="e1939-111">Primary</span></span>|`. , [] ()`|  
|<span data-ttu-id="e1939-112">2</span><span class="sxs-lookup"><span data-stu-id="e1939-112">2</span></span>|<span data-ttu-id="e1939-113">一元</span><span class="sxs-lookup"><span data-stu-id="e1939-113">Unary</span></span>|`! not`|  
|<span data-ttu-id="e1939-114">3</span><span class="sxs-lookup"><span data-stu-id="e1939-114">3</span></span>|<span data-ttu-id="e1939-115">乘法類 (Multiplicative)</span><span class="sxs-lookup"><span data-stu-id="e1939-115">Multiplicative</span></span>|`* / %`|  
|<span data-ttu-id="e1939-116">4</span><span class="sxs-lookup"><span data-stu-id="e1939-116">4</span></span>|<span data-ttu-id="e1939-117">加法類 (Additive)</span><span class="sxs-lookup"><span data-stu-id="e1939-117">Additive</span></span>|`+ -`|  
|<span data-ttu-id="e1939-118">5</span><span class="sxs-lookup"><span data-stu-id="e1939-118">5</span></span>|<span data-ttu-id="e1939-119">排序</span><span class="sxs-lookup"><span data-stu-id="e1939-119">Ordering</span></span>|`< > <= >=`|  
|<span data-ttu-id="e1939-120">6</span><span class="sxs-lookup"><span data-stu-id="e1939-120">6</span></span>|<span data-ttu-id="e1939-121">相等</span><span class="sxs-lookup"><span data-stu-id="e1939-121">Equality</span></span>|`= != <>`|  
|<span data-ttu-id="e1939-122">7</span><span class="sxs-lookup"><span data-stu-id="e1939-122">7</span></span>|<span data-ttu-id="e1939-123">條件式 AND</span><span class="sxs-lookup"><span data-stu-id="e1939-123">Conditional AND</span></span>|`and &&`|  
|<span data-ttu-id="e1939-124">8</span><span class="sxs-lookup"><span data-stu-id="e1939-124">8</span></span>|<span data-ttu-id="e1939-125">條件式 OR</span><span class="sxs-lookup"><span data-stu-id="e1939-125">Conditional OR</span></span>|`or &#124;&#124;`|  
  
 <span data-ttu-id="e1939-126">當運算式中的兩個運算子有相同的運算子優先順序層級時，會依據它們在查詢中的位置，由左至右來評估它們。</span><span class="sxs-lookup"><span data-stu-id="e1939-126">When two operators in an expression have the same operator precedence level, they are evaluated left to right, based on their position in the query.</span></span> <span data-ttu-id="e1939-127">例如，`x+y-z` 會判斷值為 `(x+y)-z`。</span><span class="sxs-lookup"><span data-stu-id="e1939-127">For example, `x+y-z` is evaluated as `(x+y)-z`.</span></span>  
  
 <span data-ttu-id="e1939-128">您可以使用括號來覆寫查詢中已定義的運算子優先順序。</span><span class="sxs-lookup"><span data-stu-id="e1939-128">You can use parentheses to override the defined precedence of the operators in a query.</span></span> <span data-ttu-id="e1939-129">括號內的所有內容都會先評估得出單一結果，之後，括號外的任何運算子便可以使用這個結果。</span><span class="sxs-lookup"><span data-stu-id="e1939-129">Everything within parentheses is evaluated first to yield a single result before that result can be used by any operator outside the parentheses.</span></span> <span data-ttu-id="e1939-130">比方說，`x+y*z`乘以`y`由`z`，然後新增`x`，但`(x+y)*z`新增`x`至`y`然後相乘的結果和`z`。</span><span class="sxs-lookup"><span data-stu-id="e1939-130">For example, `x+y*z` multiplies `y` by `z` and then adds `x`, but `(x+y)*z` adds `x` to `y` and then multiplies the result by `z`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1939-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1939-131">See Also</span></span>  
 [<span data-ttu-id="e1939-132">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="e1939-132">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
