---
title: Skip While 子句
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: b357320a92ace1b7a261991737ed653d54d0eeab
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359641"
---
# <a name="skip-while-clause-visual-basic"></a><span data-ttu-id="63dd7-102">Skip While 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63dd7-102">Skip While Clause (Visual Basic)</span></span>
<span data-ttu-id="63dd7-103">只要指定的條件為 `true`，即略過集合中的項目，然後傳回其餘項目。</span><span class="sxs-lookup"><span data-stu-id="63dd7-103">Bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63dd7-104">語法</span><span class="sxs-lookup"><span data-stu-id="63dd7-104">Syntax</span></span>  
  
```vb  
Skip While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="63dd7-105">組件</span><span class="sxs-lookup"><span data-stu-id="63dd7-105">Parts</span></span>  
  
|<span data-ttu-id="63dd7-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="63dd7-106">Term</span></span>|<span data-ttu-id="63dd7-107">定義</span><span class="sxs-lookup"><span data-stu-id="63dd7-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="63dd7-108">必要。</span><span class="sxs-lookup"><span data-stu-id="63dd7-108">Required.</span></span> <span data-ttu-id="63dd7-109">運算式，表示要測試元素的條件。</span><span class="sxs-lookup"><span data-stu-id="63dd7-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="63dd7-110">運算式必須傳回 `Boolean` 值或功能對等用法，例如 `Integer` 要評估為的 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="63dd7-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63dd7-111">備註</span><span class="sxs-lookup"><span data-stu-id="63dd7-111">Remarks</span></span>  
 <span data-ttu-id="63dd7-112">`Skip While`子句會略過查詢結果開頭的元素，直到提供的傳回 `expression` 為止 `false` 。</span><span class="sxs-lookup"><span data-stu-id="63dd7-112">The `Skip While` clause bypasses elements from the beginning of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="63dd7-113">傳回 `expression` 之後 `false` ，查詢會傳回所有剩餘的元素。</span><span class="sxs-lookup"><span data-stu-id="63dd7-113">After `expression` returns `false`, the query returns all the remaining elements.</span></span> <span data-ttu-id="63dd7-114">`expression`會忽略其餘結果的。</span><span class="sxs-lookup"><span data-stu-id="63dd7-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="63dd7-115">`Skip While`子句與子句不同之處在于 `Where` ， `Where` 子句可以用來排除不符合特定條件之查詢中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="63dd7-115">The `Skip While` clause differs from the `Where` clause in that the `Where` clause can be used to exclude all elements from a query that do not meet a particular condition.</span></span> <span data-ttu-id="63dd7-116">`Skip While`子句只會排除元素，直到第一次不符合條件為止。</span><span class="sxs-lookup"><span data-stu-id="63dd7-116">The `Skip While` clause excludes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="63dd7-117">`Skip While`當您使用已排序的查詢結果時，子句最有用。</span><span class="sxs-lookup"><span data-stu-id="63dd7-117">The `Skip While` clause is most useful when you are working with an ordered query result.</span></span>  
  
 <span data-ttu-id="63dd7-118">您可以使用子句，從查詢結果的開頭略過特定數目的結果 `Skip` 。</span><span class="sxs-lookup"><span data-stu-id="63dd7-118">You can bypass a specific number of results from the beginning of a query result by using the `Skip` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63dd7-119">範例</span><span class="sxs-lookup"><span data-stu-id="63dd7-119">Example</span></span>  
 <span data-ttu-id="63dd7-120">下列程式碼範例會使用 `Skip While` 子句來略過結果，直到找到美國的第一個客戶為止。</span><span class="sxs-lookup"><span data-stu-id="63dd7-120">The following code example uses the `Skip While` clause to bypass results until the first customer from the United States is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="63dd7-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63dd7-121">See also</span></span>

- [<span data-ttu-id="63dd7-122">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="63dd7-122">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="63dd7-123">查詢</span><span class="sxs-lookup"><span data-stu-id="63dd7-123">Queries</span></span>](index.md)
- [<span data-ttu-id="63dd7-124">Select 子句</span><span class="sxs-lookup"><span data-stu-id="63dd7-124">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="63dd7-125">From 子句</span><span class="sxs-lookup"><span data-stu-id="63dd7-125">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="63dd7-126">Skip 子句</span><span class="sxs-lookup"><span data-stu-id="63dd7-126">Skip Clause</span></span>](skip-clause.md)
- [<span data-ttu-id="63dd7-127">Take While 子句</span><span class="sxs-lookup"><span data-stu-id="63dd7-127">Take While Clause</span></span>](take-while-clause.md)
- [<span data-ttu-id="63dd7-128">Where 子句</span><span class="sxs-lookup"><span data-stu-id="63dd7-128">Where Clause</span></span>](where-clause.md)
