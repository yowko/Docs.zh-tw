---
title: Take While 子句
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: 23b7c84a9f896161a66059fcb1f30753d3b863d5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347104"
---
# <a name="take-while-clause-visual-basic"></a><span data-ttu-id="5d43f-102">Take While 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d43f-102">Take While Clause (Visual Basic)</span></span>
<span data-ttu-id="5d43f-103">只要指定的條件為 `true`，即包含集合中的項目，並略過其餘項目。</span><span class="sxs-lookup"><span data-stu-id="5d43f-103">Includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d43f-104">語法</span><span class="sxs-lookup"><span data-stu-id="5d43f-104">Syntax</span></span>  
  
```vb  
Take While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="5d43f-105">組件</span><span class="sxs-lookup"><span data-stu-id="5d43f-105">Parts</span></span>  
  
|<span data-ttu-id="5d43f-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="5d43f-106">Term</span></span>|<span data-ttu-id="5d43f-107">定義</span><span class="sxs-lookup"><span data-stu-id="5d43f-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="5d43f-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="5d43f-108">Required.</span></span> <span data-ttu-id="5d43f-109">An expression that represents a condition to test elements for.</span><span class="sxs-lookup"><span data-stu-id="5d43f-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="5d43f-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="5d43f-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d43f-111">備註</span><span class="sxs-lookup"><span data-stu-id="5d43f-111">Remarks</span></span>  
 <span data-ttu-id="5d43f-112">The `Take While` clause includes elements from the start of a query result until the supplied `expression` returns `false`.</span><span class="sxs-lookup"><span data-stu-id="5d43f-112">The `Take While` clause includes elements from the start of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="5d43f-113">After the `expression` returns `false`, the query will bypass all remaining elements.</span><span class="sxs-lookup"><span data-stu-id="5d43f-113">After the `expression` returns `false`, the query will bypass all remaining elements.</span></span> <span data-ttu-id="5d43f-114">The `expression` is ignored for the remaining results.</span><span class="sxs-lookup"><span data-stu-id="5d43f-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="5d43f-115">The `Take While` clause differs from the `Where` clause in that the `Where` clause can be used to include all elements from a query that meet a particular condition.</span><span class="sxs-lookup"><span data-stu-id="5d43f-115">The `Take While` clause differs from the `Where` clause in that the `Where` clause can be used to include all elements from a query that meet a particular condition.</span></span> <span data-ttu-id="5d43f-116">The `Take While` clause includes elements only until the first time that the condition is not satisfied.</span><span class="sxs-lookup"><span data-stu-id="5d43f-116">The `Take While` clause includes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="5d43f-117">The `Take While` clause is most useful when you are working with an ordered query result.</span><span class="sxs-lookup"><span data-stu-id="5d43f-117">The `Take While` clause is most useful when you are working with an ordered query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d43f-118">範例</span><span class="sxs-lookup"><span data-stu-id="5d43f-118">Example</span></span>  
 <span data-ttu-id="5d43f-119">The following code example uses the `Take While` clause to retrieve results until the first customer without any orders is found.</span><span class="sxs-lookup"><span data-stu-id="5d43f-119">The following code example uses the `Take While` clause to retrieve results until the first customer without any orders is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="5d43f-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="5d43f-120">See also</span></span>

- [<span data-ttu-id="5d43f-121">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="5d43f-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="5d43f-122">查詢</span><span class="sxs-lookup"><span data-stu-id="5d43f-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="5d43f-123">Select 子句</span><span class="sxs-lookup"><span data-stu-id="5d43f-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="5d43f-124">From 子句</span><span class="sxs-lookup"><span data-stu-id="5d43f-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="5d43f-125">Take 子句</span><span class="sxs-lookup"><span data-stu-id="5d43f-125">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
- [<span data-ttu-id="5d43f-126">Skip While 子句</span><span class="sxs-lookup"><span data-stu-id="5d43f-126">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="5d43f-127">Where 子句</span><span class="sxs-lookup"><span data-stu-id="5d43f-127">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
