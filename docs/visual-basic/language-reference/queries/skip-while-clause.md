---
title: "Skip While 子句 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f447a6d9b2eb58fa546ced6c96b987caf68fb3e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="skip-while-clause-visual-basic"></a><span data-ttu-id="dc173-102">Skip While 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc173-102">Skip While Clause (Visual Basic)</span></span>
<span data-ttu-id="dc173-103">只要指定的條件為 `true`，即略過集合中的項目，然後傳回其餘項目。</span><span class="sxs-lookup"><span data-stu-id="dc173-103">Bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc173-104">語法</span><span class="sxs-lookup"><span data-stu-id="dc173-104">Syntax</span></span>  
  
```  
Skip While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="dc173-105">組件</span><span class="sxs-lookup"><span data-stu-id="dc173-105">Parts</span></span>  
  
|<span data-ttu-id="dc173-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="dc173-106">Term</span></span>|<span data-ttu-id="dc173-107">定義</span><span class="sxs-lookup"><span data-stu-id="dc173-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="dc173-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="dc173-108">Required.</span></span> <span data-ttu-id="dc173-109">表示要測試的項目條件的運算式。</span><span class="sxs-lookup"><span data-stu-id="dc173-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="dc173-110">此運算式必須傳回`Boolean`值或功能的同等權限，例如`Integer`評估成`Boolean`。</span><span class="sxs-lookup"><span data-stu-id="dc173-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc173-111">備註</span><span class="sxs-lookup"><span data-stu-id="dc173-111">Remarks</span></span>  
 <span data-ttu-id="dc173-112">`Skip While`子句會略過的項目從查詢結果的開始，直到提供`expression`傳回`false`。</span><span class="sxs-lookup"><span data-stu-id="dc173-112">The `Skip While` clause bypasses elements from the beginning of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="dc173-113">之後`expression`傳回`false`，此查詢會傳回所有其餘的項目。</span><span class="sxs-lookup"><span data-stu-id="dc173-113">After `expression` returns `false`, the query returns all the remaining elements.</span></span> <span data-ttu-id="dc173-114">`expression`會忽略其餘的結果。</span><span class="sxs-lookup"><span data-stu-id="dc173-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="dc173-115">`Skip While`子句不同於`Where`中的子句`Where`子句可以用來排除不符合特定條件的查詢中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="dc173-115">The `Skip While` clause differs from the `Where` clause in that the `Where` clause can be used to exclude all elements from a query that do not meet a particular condition.</span></span> <span data-ttu-id="dc173-116">`Skip While`子句不滿足條件的第一次只到排除項目。</span><span class="sxs-lookup"><span data-stu-id="dc173-116">The `Skip While` clause excludes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="dc173-117">`Skip While`子句是最有用，當您正在使用已排序的查詢結果。</span><span class="sxs-lookup"><span data-stu-id="dc173-117">The `Skip While` clause is most useful when you are working with an ordered query result.</span></span>  
  
 <span data-ttu-id="dc173-118">您可以藉由略過特定數目的開頭的查詢結果的結果`Skip`子句。</span><span class="sxs-lookup"><span data-stu-id="dc173-118">You can bypass a specific number of results from the beginning of a query result by using the `Skip` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc173-119">範例</span><span class="sxs-lookup"><span data-stu-id="dc173-119">Example</span></span>  
 <span data-ttu-id="dc173-120">下列程式碼範例使用`Skip While`子句來略過的結果，直到找到第一個客戶於美國。</span><span class="sxs-lookup"><span data-stu-id="dc173-120">The following code example uses the `Skip While` clause to bypass results until the first customer from the United States is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#3](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-while-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="dc173-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc173-121">See Also</span></span>  
 [<span data-ttu-id="dc173-122">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="dc173-122">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="dc173-123">查詢</span><span class="sxs-lookup"><span data-stu-id="dc173-123">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="dc173-124">Select 子句</span><span class="sxs-lookup"><span data-stu-id="dc173-124">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="dc173-125">From 子句</span><span class="sxs-lookup"><span data-stu-id="dc173-125">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="dc173-126">Skip 子句</span><span class="sxs-lookup"><span data-stu-id="dc173-126">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)  
 [<span data-ttu-id="dc173-127">Take While 子句</span><span class="sxs-lookup"><span data-stu-id="dc173-127">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 [<span data-ttu-id="dc173-128">Where 子句</span><span class="sxs-lookup"><span data-stu-id="dc173-128">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
