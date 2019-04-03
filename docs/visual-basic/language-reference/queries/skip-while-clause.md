---
title: Skip While 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: 3d6caeb1938e8e53e8ec2575f740cd5e49496f62
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839895"
---
# <a name="skip-while-clause-visual-basic"></a><span data-ttu-id="6cc78-102">Skip While 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6cc78-102">Skip While Clause (Visual Basic)</span></span>
<span data-ttu-id="6cc78-103">只要指定的條件為 `true`，即略過集合中的項目，然後傳回其餘項目。</span><span class="sxs-lookup"><span data-stu-id="6cc78-103">Bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cc78-104">語法</span><span class="sxs-lookup"><span data-stu-id="6cc78-104">Syntax</span></span>  
  
```  
Skip While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="6cc78-105">組件</span><span class="sxs-lookup"><span data-stu-id="6cc78-105">Parts</span></span>  
  
|<span data-ttu-id="6cc78-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="6cc78-106">Term</span></span>|<span data-ttu-id="6cc78-107">定義</span><span class="sxs-lookup"><span data-stu-id="6cc78-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="6cc78-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="6cc78-108">Required.</span></span> <span data-ttu-id="6cc78-109">表示要測試的元素的條件運算式。</span><span class="sxs-lookup"><span data-stu-id="6cc78-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="6cc78-110">此運算式必須傳回`Boolean`值或功能對等項目，例如`Integer`評估為`Boolean`。</span><span class="sxs-lookup"><span data-stu-id="6cc78-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6cc78-111">備註</span><span class="sxs-lookup"><span data-stu-id="6cc78-111">Remarks</span></span>  
 <span data-ttu-id="6cc78-112">`Skip While`子句會略過從查詢結果的開始，直到所提供的項目`expression`傳回`false`。</span><span class="sxs-lookup"><span data-stu-id="6cc78-112">The `Skip While` clause bypasses elements from the beginning of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="6cc78-113">在後`expression`傳回`false`，查詢會傳回所有剩餘的項目。</span><span class="sxs-lookup"><span data-stu-id="6cc78-113">After `expression` returns `false`, the query returns all the remaining elements.</span></span> <span data-ttu-id="6cc78-114">`expression`會忽略其餘的結果。</span><span class="sxs-lookup"><span data-stu-id="6cc78-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="6cc78-115">`Skip While`子句不同`Where`中的子句`Where`子句可以用來排除不符合特定條件的查詢中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="6cc78-115">The `Skip While` clause differs from the `Where` clause in that the `Where` clause can be used to exclude all elements from a query that do not meet a particular condition.</span></span> <span data-ttu-id="6cc78-116">`Skip While`子句會排除項目只會保存未滿足條件的第一次。</span><span class="sxs-lookup"><span data-stu-id="6cc78-116">The `Skip While` clause excludes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="6cc78-117">`Skip While`子句在當您正在使用的已排序的查詢結果時十分實用。</span><span class="sxs-lookup"><span data-stu-id="6cc78-117">The `Skip While` clause is most useful when you are working with an ordered query result.</span></span>  
  
 <span data-ttu-id="6cc78-118">您可以使用連線，略過特定數目的查詢結果的結果從一開始`Skip`子句。</span><span class="sxs-lookup"><span data-stu-id="6cc78-118">You can bypass a specific number of results from the beginning of a query result by using the `Skip` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6cc78-119">範例</span><span class="sxs-lookup"><span data-stu-id="6cc78-119">Example</span></span>  
 <span data-ttu-id="6cc78-120">下列程式碼範例使用`Skip While`子句來略過的結果，直到找到第一個客戶，從美國傳為止。</span><span class="sxs-lookup"><span data-stu-id="6cc78-120">The following code example uses the `Skip While` clause to bypass results until the first customer from the United States is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="6cc78-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6cc78-121">See also</span></span>

- [<span data-ttu-id="6cc78-122">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="6cc78-122">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="6cc78-123">查詢</span><span class="sxs-lookup"><span data-stu-id="6cc78-123">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="6cc78-124">Select 子句</span><span class="sxs-lookup"><span data-stu-id="6cc78-124">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="6cc78-125">From 子句</span><span class="sxs-lookup"><span data-stu-id="6cc78-125">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="6cc78-126">Skip 子句</span><span class="sxs-lookup"><span data-stu-id="6cc78-126">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
- [<span data-ttu-id="6cc78-127">Take While 子句</span><span class="sxs-lookup"><span data-stu-id="6cc78-127">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [<span data-ttu-id="6cc78-128">Where 子句</span><span class="sxs-lookup"><span data-stu-id="6cc78-128">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
