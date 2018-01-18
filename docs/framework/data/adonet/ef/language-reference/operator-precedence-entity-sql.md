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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 537c9ae7c92c6abcbe597970f2b0ec29e399bc62
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="operator-precedence-entity-sql"></a><span data-ttu-id="32ab8-102">運算子優先順序 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="32ab8-102">Operator Precedence (Entity SQL)</span></span>
<span data-ttu-id="32ab8-103">當[!INCLUDE[esql](../../../../../../includes/esql-md.md)]查詢有多個運算子，運算子優先順序會決定作業的執行的順序。</span><span class="sxs-lookup"><span data-stu-id="32ab8-103">When an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query has multiple operators, operator precedence determines the sequence in which the operations are performed.</span></span> <span data-ttu-id="32ab8-104">執行的順序對於查詢結果有很大的影響。</span><span class="sxs-lookup"><span data-stu-id="32ab8-104">The order of execution can significantly affect the query result.</span></span>  
  
 <span data-ttu-id="32ab8-105">下表顯示運算子的優先順序層級。</span><span class="sxs-lookup"><span data-stu-id="32ab8-105">Operators have the precedence levels shown in the following table.</span></span> <span data-ttu-id="32ab8-106">先評估層級較高的運算子，再評估層級較低的運算子。</span><span class="sxs-lookup"><span data-stu-id="32ab8-106">An operator with a higher level is evaluated before an operator with a lower level.</span></span>  
  
|<span data-ttu-id="32ab8-107">層級</span><span class="sxs-lookup"><span data-stu-id="32ab8-107">Level</span></span>|<span data-ttu-id="32ab8-108">運算類型</span><span class="sxs-lookup"><span data-stu-id="32ab8-108">Operation type</span></span>|<span data-ttu-id="32ab8-109">運算子</span><span class="sxs-lookup"><span data-stu-id="32ab8-109">Operator</span></span>|  
|-----------|--------------------|--------------|  
|<span data-ttu-id="32ab8-110">1</span><span class="sxs-lookup"><span data-stu-id="32ab8-110">1</span></span>|<span data-ttu-id="32ab8-111">主要</span><span class="sxs-lookup"><span data-stu-id="32ab8-111">Primary</span></span>|`. , [] ()`|  
|<span data-ttu-id="32ab8-112">2</span><span class="sxs-lookup"><span data-stu-id="32ab8-112">2</span></span>|<span data-ttu-id="32ab8-113">一元</span><span class="sxs-lookup"><span data-stu-id="32ab8-113">Unary</span></span>|`! not`|  
|<span data-ttu-id="32ab8-114">3</span><span class="sxs-lookup"><span data-stu-id="32ab8-114">3</span></span>|<span data-ttu-id="32ab8-115">乘法類 (Multiplicative)</span><span class="sxs-lookup"><span data-stu-id="32ab8-115">Multiplicative</span></span>|`* / %`|  
|<span data-ttu-id="32ab8-116">4</span><span class="sxs-lookup"><span data-stu-id="32ab8-116">4</span></span>|<span data-ttu-id="32ab8-117">加法類 (Additive)</span><span class="sxs-lookup"><span data-stu-id="32ab8-117">Additive</span></span>|`+ -`|  
|<span data-ttu-id="32ab8-118">5</span><span class="sxs-lookup"><span data-stu-id="32ab8-118">5</span></span>|<span data-ttu-id="32ab8-119">排序</span><span class="sxs-lookup"><span data-stu-id="32ab8-119">Ordering</span></span>|`< > <= >=`|  
|<span data-ttu-id="32ab8-120">6</span><span class="sxs-lookup"><span data-stu-id="32ab8-120">6</span></span>|<span data-ttu-id="32ab8-121">相等</span><span class="sxs-lookup"><span data-stu-id="32ab8-121">Equality</span></span>|`= != <>`|  
|<span data-ttu-id="32ab8-122">7</span><span class="sxs-lookup"><span data-stu-id="32ab8-122">7</span></span>|<span data-ttu-id="32ab8-123">條件式 AND</span><span class="sxs-lookup"><span data-stu-id="32ab8-123">Conditional AND</span></span>|`and &&`|  
|<span data-ttu-id="32ab8-124">8</span><span class="sxs-lookup"><span data-stu-id="32ab8-124">8</span></span>|<span data-ttu-id="32ab8-125">條件式 OR</span><span class="sxs-lookup"><span data-stu-id="32ab8-125">Conditional OR</span></span>|`or &#124;&#124;`|  
  
 <span data-ttu-id="32ab8-126">當運算式中的兩個運算子有相同的運算子優先順序層級時，會依據它們在查詢中的位置，由左至右來評估它們。</span><span class="sxs-lookup"><span data-stu-id="32ab8-126">When two operators in an expression have the same operator precedence level, they are evaluated left to right, based on their position in the query.</span></span> <span data-ttu-id="32ab8-127">例如，`x+y-z` 會判斷值為 `(x+y)-z`。</span><span class="sxs-lookup"><span data-stu-id="32ab8-127">For example, `x+y-z` is evaluated as `(x+y)-z`.</span></span>  
  
 <span data-ttu-id="32ab8-128">您可以使用括號來覆寫查詢中已定義的運算子優先順序。</span><span class="sxs-lookup"><span data-stu-id="32ab8-128">You can use parentheses to override the defined precedence of the operators in a query.</span></span> <span data-ttu-id="32ab8-129">括號內的所有內容都會先評估得出單一結果，之後，括號外的任何運算子便可以使用這個結果。</span><span class="sxs-lookup"><span data-stu-id="32ab8-129">Everything within parentheses is evaluated first to yield a single result before that result can be used by any operator outside the parentheses.</span></span> <span data-ttu-id="32ab8-130">比方說，`x+y*z`乘以`y`由`z`，然後新增`x`，但`(x+y)*z`新增`x`至`y`然後相乘的結果和`z`。</span><span class="sxs-lookup"><span data-stu-id="32ab8-130">For example, `x+y*z` multiplies `y` by `z` and then adds `x`, but `(x+y)*z` adds `x` to `y` and then multiplies the result by `z`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32ab8-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="32ab8-131">See Also</span></span>  
 [<span data-ttu-id="32ab8-132">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="32ab8-132">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
