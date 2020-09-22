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
ms.openlocfilehash: 632e9e2195f21a3aa1d1ffd28e9838905c471156
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869655"
---
# <a name="take-while-clause-visual-basic"></a><span data-ttu-id="1ac56-102">Take While 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ac56-102">Take While Clause (Visual Basic)</span></span>

<span data-ttu-id="1ac56-103">只要指定的條件為 `true`，即包含集合中的項目，並略過其餘項目。</span><span class="sxs-lookup"><span data-stu-id="1ac56-103">Includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ac56-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="1ac56-104">Syntax</span></span>  
  
```vb  
Take While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="1ac56-105">組件</span><span class="sxs-lookup"><span data-stu-id="1ac56-105">Parts</span></span>  
  
|<span data-ttu-id="1ac56-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="1ac56-106">Term</span></span>|<span data-ttu-id="1ac56-107">定義</span><span class="sxs-lookup"><span data-stu-id="1ac56-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="1ac56-108">必要。</span><span class="sxs-lookup"><span data-stu-id="1ac56-108">Required.</span></span> <span data-ttu-id="1ac56-109">運算式，表示要測試元素的條件。</span><span class="sxs-lookup"><span data-stu-id="1ac56-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="1ac56-110">運算式必須傳回 `Boolean` 值或功能對等專案，例如 `Integer` 要評估為的 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="1ac56-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ac56-111">備註</span><span class="sxs-lookup"><span data-stu-id="1ac56-111">Remarks</span></span>  

 <span data-ttu-id="1ac56-112">`Take While`子句包含從查詢結果開頭開始的元素，直到提供的傳回 `expression` 為止 `false` 。</span><span class="sxs-lookup"><span data-stu-id="1ac56-112">The `Take While` clause includes elements from the start of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="1ac56-113">傳回之後 `expression` `false` ，查詢會略過所有其餘的元素。</span><span class="sxs-lookup"><span data-stu-id="1ac56-113">After the `expression` returns `false`, the query will bypass all remaining elements.</span></span> <span data-ttu-id="1ac56-114">`expression`其餘的結果會忽略。</span><span class="sxs-lookup"><span data-stu-id="1ac56-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="1ac56-115">`Take While`子句與子句不同之處 `Where` 在於， `Where` 子句可以用來包含符合特定條件之查詢中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="1ac56-115">The `Take While` clause differs from the `Where` clause in that the `Where` clause can be used to include all elements from a query that meet a particular condition.</span></span> <span data-ttu-id="1ac56-116">`Take While`子句只會包含專案，直到第一次未滿足條件為止。</span><span class="sxs-lookup"><span data-stu-id="1ac56-116">The `Take While` clause includes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="1ac56-117">`Take While`當您使用已排序的查詢結果時，子句最為有用。</span><span class="sxs-lookup"><span data-stu-id="1ac56-117">The `Take While` clause is most useful when you are working with an ordered query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ac56-118">範例</span><span class="sxs-lookup"><span data-stu-id="1ac56-118">Example</span></span>  

 <span data-ttu-id="1ac56-119">下列程式碼範例會使用 `Take While` 子句來取得結果，直到找不到任何訂單的第一個客戶為止。</span><span class="sxs-lookup"><span data-stu-id="1ac56-119">The following code example uses the `Take While` clause to retrieve results until the first customer without any orders is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="1ac56-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ac56-120">See also</span></span>

- [<span data-ttu-id="1ac56-121">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="1ac56-121">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="1ac56-122">查詢</span><span class="sxs-lookup"><span data-stu-id="1ac56-122">Queries</span></span>](index.md)
- [<span data-ttu-id="1ac56-123">Select 子句</span><span class="sxs-lookup"><span data-stu-id="1ac56-123">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="1ac56-124">From 子句</span><span class="sxs-lookup"><span data-stu-id="1ac56-124">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="1ac56-125">Take 子句</span><span class="sxs-lookup"><span data-stu-id="1ac56-125">Take Clause</span></span>](take-clause.md)
- [<span data-ttu-id="1ac56-126">Skip While 子句</span><span class="sxs-lookup"><span data-stu-id="1ac56-126">Skip While Clause</span></span>](skip-while-clause.md)
- [<span data-ttu-id="1ac56-127">Where 子句</span><span class="sxs-lookup"><span data-stu-id="1ac56-127">Where Clause</span></span>](where-clause.md)
