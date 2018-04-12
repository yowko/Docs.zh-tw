---
title: 範圍變數&lt;變數&gt;隱藏了封閉區塊、 預先定義的範圍變數或查詢運算式中隱含宣告的變數中的變數
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ccbac48694a13daa09f2511cf39d5dbd51cdaaf7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="range-variable-ltvariablegt-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a><span data-ttu-id="24ce7-102">範圍變數&lt;變數&gt;隱藏了封閉區塊、 預先定義的範圍變數或查詢運算式中隱含宣告的變數中的變數</span><span class="sxs-lookup"><span data-stu-id="24ce7-102">Range variable &lt;variable&gt; hides a variable in an enclosing block, a previously defined range variable, or an implicitly declared variable in a query expression</span></span>
<span data-ttu-id="24ce7-103">中指定的範圍變數名稱`Select`， `From`， `Aggregate`，或`Let`子句會重複已經在查詢或查詢所隱含宣告的變數名稱中先前指定的範圍變數的名稱例如，欄位名稱或彙總函式的名稱。</span><span class="sxs-lookup"><span data-stu-id="24ce7-103">A range variable name specified in a `Select`, `From`, `Aggregate`, or `Let` clause duplicates the name of a range variable already specified previously in the query, or the name of a variable that is implicitly declared by the query, such as a field name or the name of an aggregate function.</span></span>  
  
 <span data-ttu-id="24ce7-104">**錯誤 ID:** BC36633</span><span class="sxs-lookup"><span data-stu-id="24ce7-104">**Error ID:** BC36633</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="24ce7-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="24ce7-105">To correct this error</span></span>  
  
-   <span data-ttu-id="24ce7-106">請確定特定查詢範圍中的所有範圍變數都有唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="24ce7-106">Ensure that all range variables in a particular query scope have unique names.</span></span> <span data-ttu-id="24ce7-107">您可以將查詢括在括號可確保巢狀的查詢具有唯一的範圍中。</span><span class="sxs-lookup"><span data-stu-id="24ce7-107">You can enclose a query in parentheses to ensure that nested queries have a unique scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24ce7-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24ce7-108">See Also</span></span>  
 [<span data-ttu-id="24ce7-109">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="24ce7-109">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="24ce7-110">From 子句</span><span class="sxs-lookup"><span data-stu-id="24ce7-110">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="24ce7-111">Let 子句</span><span class="sxs-lookup"><span data-stu-id="24ce7-111">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)  
 [<span data-ttu-id="24ce7-112">Aggregate 子句</span><span class="sxs-lookup"><span data-stu-id="24ce7-112">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="24ce7-113">Select 子句</span><span class="sxs-lookup"><span data-stu-id="24ce7-113">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
