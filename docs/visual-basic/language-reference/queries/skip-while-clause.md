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
ms.openlocfilehash: 380372d6aaf8df3050e0ba8606b74eb3834dec67
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972595"
---
# <a name="skip-while-clause-visual-basic"></a><span data-ttu-id="c9b3f-102">Skip While 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9b3f-102">Skip While Clause (Visual Basic)</span></span>
<span data-ttu-id="c9b3f-103">只要指定的條件為 `true`，即略過集合中的項目，然後傳回其餘項目。</span><span class="sxs-lookup"><span data-stu-id="c9b3f-103">Bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9b3f-104">語法</span><span class="sxs-lookup"><span data-stu-id="c9b3f-104">Syntax</span></span>  
  
```  
Skip While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="c9b3f-105">組件</span><span class="sxs-lookup"><span data-stu-id="c9b3f-105">Parts</span></span>  
  
|<span data-ttu-id="c9b3f-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="c9b3f-106">Term</span></span>|<span data-ttu-id="c9b3f-107">定義</span><span class="sxs-lookup"><span data-stu-id="c9b3f-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="c9b3f-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="c9b3f-108">Required.</span></span> <span data-ttu-id="c9b3f-109">表示要測試的元素的條件運算式。</span><span class="sxs-lookup"><span data-stu-id="c9b3f-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="c9b3f-110">此運算式必須傳回`Boolean`值或功能對等項目，例如`Integer`評估為`Boolean`。</span><span class="sxs-lookup"><span data-stu-id="c9b3f-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9b3f-111">備註</span><span class="sxs-lookup"><span data-stu-id="c9b3f-111">Remarks</span></span>  
 <span data-ttu-id="c9b3f-112">`Skip While`子句會略過從查詢結果的開始，直到所提供的項目`expression`傳回`false`。</span><span class="sxs-lookup"><span data-stu-id="c9b3f-112">The `Skip While` clause bypasses elements from the beginning of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="c9b3f-113">在後`expression`傳回`false`，查詢會傳回所有剩餘的項目。</span><span class="sxs-lookup"><span data-stu-id="c9b3f-113">After `expression` returns `false`, the query returns all the remaining elements.</span></span> <span data-ttu-id="c9b3f-114">`expression`會忽略其餘的結果。</span><span class="sxs-lookup"><span data-stu-id="c9b3f-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="c9b3f-115">`Skip While`子句不同`Where`中的子句`Where`子句可以用來排除不符合特定條件的查詢中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="c9b3f-115">The `Skip While` clause differs from the `Where` clause in that the `Where` clause can be used to exclude all elements from a query that do not meet a particular condition.</span></span> <span data-ttu-id="c9b3f-116">`Skip While`子句會排除項目只會保存未滿足條件的第一次。</span><span class="sxs-lookup"><span data-stu-id="c9b3f-116">The `Skip While` clause excludes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="c9b3f-117">`Skip While`子句在當您正在使用的已排序的查詢結果時十分實用。</span><span class="sxs-lookup"><span data-stu-id="c9b3f-117">The `Skip While` clause is most useful when you are working with an ordered query result.</span></span>  
  
 <span data-ttu-id="c9b3f-118">您可以使用連線，略過特定數目的查詢結果的結果從一開始`Skip`子句。</span><span class="sxs-lookup"><span data-stu-id="c9b3f-118">You can bypass a specific number of results from the beginning of a query result by using the `Skip` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9b3f-119">範例</span><span class="sxs-lookup"><span data-stu-id="c9b3f-119">Example</span></span>  
 <span data-ttu-id="c9b3f-120">下列程式碼範例使用`Skip While`子句來略過的結果，直到找到第一個客戶，從美國傳為止。</span><span class="sxs-lookup"><span data-stu-id="c9b3f-120">The following code example uses the `Skip While` clause to bypass results until the first customer from the United States is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="c9b3f-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9b3f-121">See also</span></span>
- [<span data-ttu-id="c9b3f-122">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="c9b3f-122">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="c9b3f-123">查詢</span><span class="sxs-lookup"><span data-stu-id="c9b3f-123">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="c9b3f-124">Select 子句</span><span class="sxs-lookup"><span data-stu-id="c9b3f-124">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="c9b3f-125">From 子句</span><span class="sxs-lookup"><span data-stu-id="c9b3f-125">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="c9b3f-126">Skip 子句</span><span class="sxs-lookup"><span data-stu-id="c9b3f-126">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
- [<span data-ttu-id="c9b3f-127">Take While 子句</span><span class="sxs-lookup"><span data-stu-id="c9b3f-127">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [<span data-ttu-id="c9b3f-128">Where 子句</span><span class="sxs-lookup"><span data-stu-id="c9b3f-128">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
