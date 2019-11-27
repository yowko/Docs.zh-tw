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
# <a name="take-while-clause-visual-basic"></a><span data-ttu-id="3a0b4-102">Take While 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a0b4-102">Take While Clause (Visual Basic)</span></span>
<span data-ttu-id="3a0b4-103">只要指定的條件為 `true`，即包含集合中的項目，並略過其餘項目。</span><span class="sxs-lookup"><span data-stu-id="3a0b4-103">Includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a0b4-104">語法</span><span class="sxs-lookup"><span data-stu-id="3a0b4-104">Syntax</span></span>  
  
```vb  
Take While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="3a0b4-105">組件</span><span class="sxs-lookup"><span data-stu-id="3a0b4-105">Parts</span></span>  
  
|<span data-ttu-id="3a0b4-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="3a0b4-106">Term</span></span>|<span data-ttu-id="3a0b4-107">定義</span><span class="sxs-lookup"><span data-stu-id="3a0b4-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="3a0b4-108">必要。</span><span class="sxs-lookup"><span data-stu-id="3a0b4-108">Required.</span></span> <span data-ttu-id="3a0b4-109">運算式，表示要測試元素的條件。</span><span class="sxs-lookup"><span data-stu-id="3a0b4-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="3a0b4-110">運算式必須傳回 `Boolean` 值或函式對等功能，例如要評估為 `Boolean`的 `Integer`。</span><span class="sxs-lookup"><span data-stu-id="3a0b4-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a0b4-111">備註</span><span class="sxs-lookup"><span data-stu-id="3a0b4-111">Remarks</span></span>  
 <span data-ttu-id="3a0b4-112">`Take While` 子句包含查詢結果開頭的元素，直到提供的 `expression` 傳回 `false`為止。</span><span class="sxs-lookup"><span data-stu-id="3a0b4-112">The `Take While` clause includes elements from the start of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="3a0b4-113">在 `expression` 傳回 `false`之後，查詢將會略過所有剩餘的元素。</span><span class="sxs-lookup"><span data-stu-id="3a0b4-113">After the `expression` returns `false`, the query will bypass all remaining elements.</span></span> <span data-ttu-id="3a0b4-114">會忽略其餘結果的 `expression`。</span><span class="sxs-lookup"><span data-stu-id="3a0b4-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="3a0b4-115">`Take While` 子句與 `Where` 子句不同之處在于，`Where` 子句可以用來包含符合特定條件之查詢中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="3a0b4-115">The `Take While` clause differs from the `Where` clause in that the `Where` clause can be used to include all elements from a query that meet a particular condition.</span></span> <span data-ttu-id="3a0b4-116">`Take While` 子句只有在第一次未滿足條件時才會包含元素。</span><span class="sxs-lookup"><span data-stu-id="3a0b4-116">The `Take While` clause includes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="3a0b4-117">當您使用已排序的查詢結果時，`Take While` 子句最有用。</span><span class="sxs-lookup"><span data-stu-id="3a0b4-117">The `Take While` clause is most useful when you are working with an ordered query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a0b4-118">範例</span><span class="sxs-lookup"><span data-stu-id="3a0b4-118">Example</span></span>  
 <span data-ttu-id="3a0b4-119">下列程式碼範例會使用 `Take While` 子句來抓取結果，直到找不到任何訂單的第一個客戶為止。</span><span class="sxs-lookup"><span data-stu-id="3a0b4-119">The following code example uses the `Take While` clause to retrieve results until the first customer without any orders is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="3a0b4-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="3a0b4-120">See also</span></span>

- [<span data-ttu-id="3a0b4-121">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="3a0b4-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="3a0b4-122">查詢</span><span class="sxs-lookup"><span data-stu-id="3a0b4-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="3a0b4-123">Select 子句</span><span class="sxs-lookup"><span data-stu-id="3a0b4-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="3a0b4-124">From 子句</span><span class="sxs-lookup"><span data-stu-id="3a0b4-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="3a0b4-125">Take 子句</span><span class="sxs-lookup"><span data-stu-id="3a0b4-125">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
- [<span data-ttu-id="3a0b4-126">Skip While 子句</span><span class="sxs-lookup"><span data-stu-id="3a0b4-126">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="3a0b4-127">Where 子句</span><span class="sxs-lookup"><span data-stu-id="3a0b4-127">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
