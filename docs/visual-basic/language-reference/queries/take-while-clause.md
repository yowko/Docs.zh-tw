---
title: Take While 子句 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5c8add6c55bb9353bac3489e68f497cb32785aad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="take-while-clause-visual-basic"></a><span data-ttu-id="fd25d-102">Take While 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fd25d-102">Take While Clause (Visual Basic)</span></span>
<span data-ttu-id="fd25d-103">只要指定的條件為 `true`，即包含集合中的項目，並略過其餘項目。</span><span class="sxs-lookup"><span data-stu-id="fd25d-103">Includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd25d-104">語法</span><span class="sxs-lookup"><span data-stu-id="fd25d-104">Syntax</span></span>  
  
```  
Take While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="fd25d-105">組件</span><span class="sxs-lookup"><span data-stu-id="fd25d-105">Parts</span></span>  
  
|<span data-ttu-id="fd25d-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="fd25d-106">Term</span></span>|<span data-ttu-id="fd25d-107">定義</span><span class="sxs-lookup"><span data-stu-id="fd25d-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="fd25d-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="fd25d-108">Required.</span></span> <span data-ttu-id="fd25d-109">表示要測試的項目條件的運算式。</span><span class="sxs-lookup"><span data-stu-id="fd25d-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="fd25d-110">此運算式必須傳回`Boolean`值或功能的同等權限，例如`Integer`評估成`Boolean`。</span><span class="sxs-lookup"><span data-stu-id="fd25d-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd25d-111">備註</span><span class="sxs-lookup"><span data-stu-id="fd25d-111">Remarks</span></span>  
 <span data-ttu-id="fd25d-112">`Take While`子句會包含從查詢結果的開始項目，直到提供`expression`傳回`false`。</span><span class="sxs-lookup"><span data-stu-id="fd25d-112">The `Take While` clause includes elements from the start of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="fd25d-113">之後`expression`傳回`false`，查詢將會略過所有其餘的項目。</span><span class="sxs-lookup"><span data-stu-id="fd25d-113">After the `expression` returns `false`, the query will bypass all remaining elements.</span></span> <span data-ttu-id="fd25d-114">`expression`會忽略其餘的結果。</span><span class="sxs-lookup"><span data-stu-id="fd25d-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="fd25d-115">`Take While`子句不同於`Where`中的子句`Where`子句可以用來包含查詢中所有符合特定條件的項目。</span><span class="sxs-lookup"><span data-stu-id="fd25d-115">The `Take While` clause differs from the `Where` clause in that the `Where` clause can be used to include all elements from a query that meet a particular condition.</span></span> <span data-ttu-id="fd25d-116">`Take While`子句之前不滿足條件的第一次只包含項目。</span><span class="sxs-lookup"><span data-stu-id="fd25d-116">The `Take While` clause includes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="fd25d-117">`Take While`子句是最有用，當您正在使用已排序的查詢結果。</span><span class="sxs-lookup"><span data-stu-id="fd25d-117">The `Take While` clause is most useful when you are working with an ordered query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd25d-118">範例</span><span class="sxs-lookup"><span data-stu-id="fd25d-118">Example</span></span>  
 <span data-ttu-id="fd25d-119">下列程式碼範例使用`Take While`子句用來擷取結果，直到找到沒有任何訂單的第一個客戶。</span><span class="sxs-lookup"><span data-stu-id="fd25d-119">The following code example uses the `Take While` clause to retrieve results until the first customer without any orders is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#2](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-while-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="fd25d-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd25d-120">See Also</span></span>  
 [<span data-ttu-id="fd25d-121">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="fd25d-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="fd25d-122">查詢</span><span class="sxs-lookup"><span data-stu-id="fd25d-122">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="fd25d-123">Select 子句</span><span class="sxs-lookup"><span data-stu-id="fd25d-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="fd25d-124">From 子句</span><span class="sxs-lookup"><span data-stu-id="fd25d-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="fd25d-125">Take 子句</span><span class="sxs-lookup"><span data-stu-id="fd25d-125">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)  
 [<span data-ttu-id="fd25d-126">Skip While 子句</span><span class="sxs-lookup"><span data-stu-id="fd25d-126">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [<span data-ttu-id="fd25d-127">Where 子句</span><span class="sxs-lookup"><span data-stu-id="fd25d-127">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
