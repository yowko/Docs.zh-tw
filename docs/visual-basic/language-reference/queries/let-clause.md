---
title: Let 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: 34c0fd239d9e08dab4a107cb8447941e7ab3ecbe
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2018
ms.locfileid: "43255817"
---
# <a name="let-clause-visual-basic"></a><span data-ttu-id="ae08f-102">Let 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae08f-102">Let Clause (Visual Basic)</span></span>
<span data-ttu-id="ae08f-103">計算值，並將它指派給在查詢中的新變數。</span><span class="sxs-lookup"><span data-stu-id="ae08f-103">Computes a value and assigns it to a new variable within the query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae08f-104">語法</span><span class="sxs-lookup"><span data-stu-id="ae08f-104">Syntax</span></span>  
  
```  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="ae08f-105">組件</span><span class="sxs-lookup"><span data-stu-id="ae08f-105">Parts</span></span>  
  
|<span data-ttu-id="ae08f-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="ae08f-106">Term</span></span>|<span data-ttu-id="ae08f-107">定義</span><span class="sxs-lookup"><span data-stu-id="ae08f-107">Definition</span></span>|  
|---|---|  
|`variable`|<span data-ttu-id="ae08f-108">必要。</span><span class="sxs-lookup"><span data-stu-id="ae08f-108">Required.</span></span> <span data-ttu-id="ae08f-109">別名可以用來參考提供運算式的結果。</span><span class="sxs-lookup"><span data-stu-id="ae08f-109">An alias that can be used to reference the results of the supplied expression.</span></span>|  
|`expression`|<span data-ttu-id="ae08f-110">必要。</span><span class="sxs-lookup"><span data-stu-id="ae08f-110">Required.</span></span> <span data-ttu-id="ae08f-111">運算式，會進行評估，並指派給指定的變數。</span><span class="sxs-lookup"><span data-stu-id="ae08f-111">An expression that will be evaluated and assigned to the specified variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae08f-112">備註</span><span class="sxs-lookup"><span data-stu-id="ae08f-112">Remarks</span></span>  
 <span data-ttu-id="ae08f-113">`Let`子句可讓您計算值，每個查詢結果，並使用別名來參考它們。</span><span class="sxs-lookup"><span data-stu-id="ae08f-113">The `Let` clause enables you to compute values for each query result and reference them by using an alias.</span></span> <span data-ttu-id="ae08f-114">別名可用於其他子句，例如`Where`子句。</span><span class="sxs-lookup"><span data-stu-id="ae08f-114">The alias can be used in other clauses, such as the `Where` clause.</span></span> <span data-ttu-id="ae08f-115">`Let`子句可讓您建立可以更輕鬆地讀取，因為您可以指定包含在查詢運算式子句的別名，並以別名取代每次使用運算式子句的查詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="ae08f-115">The `Let` clause enables you to create a query statement that is easier to read because you can specify an alias for an expression clause included in the query and substitute the alias each time the expression clause is used.</span></span>  
  
 <span data-ttu-id="ae08f-116">您可以包含任意數目的`variable`並`expression`中的指派`Let`子句。</span><span class="sxs-lookup"><span data-stu-id="ae08f-116">You can include any number of `variable` and `expression` assignments in the `Let` clause.</span></span> <span data-ttu-id="ae08f-117">請以逗號 （，） 分隔每個指派。</span><span class="sxs-lookup"><span data-stu-id="ae08f-117">Separate each assignment with a comma (,).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae08f-118">範例</span><span class="sxs-lookup"><span data-stu-id="ae08f-118">Example</span></span>  
 <span data-ttu-id="ae08f-119">下列程式碼範例使用`Let`子句來計算產品的 10%折扣。</span><span class="sxs-lookup"><span data-stu-id="ae08f-119">The following code example uses the `Let` clause to compute a 10 percent discount on products.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#16](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/let-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ae08f-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae08f-120">See Also</span></span>  
 [<span data-ttu-id="ae08f-121">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="ae08f-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="ae08f-122">查詢</span><span class="sxs-lookup"><span data-stu-id="ae08f-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)  
 [<span data-ttu-id="ae08f-123">Select 子句</span><span class="sxs-lookup"><span data-stu-id="ae08f-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="ae08f-124">From 子句</span><span class="sxs-lookup"><span data-stu-id="ae08f-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="ae08f-125">Where 子句</span><span class="sxs-lookup"><span data-stu-id="ae08f-125">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
