---
title: 範圍變數 <variable> 隱藏了封閉區塊中的變數、預先定義的範圍變數或查詢運算式中隱含宣告的變數
ms.date: 07/20/2015
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
ms.openlocfilehash: e31f728de228bea743f6c7b5cbfef3cd73367262
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822709"
---
# <a name="range-variable-variable-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a><span data-ttu-id="aae5b-102">範圍變數\<變數 > 隱藏了封閉區塊、 預先定義的範圍變數或查詢運算式中隱含宣告的變數中的變數</span><span class="sxs-lookup"><span data-stu-id="aae5b-102">Range variable \<variable> hides a variable in an enclosing block, a previously defined range variable, or an implicitly declared variable in a query expression</span></span>
<span data-ttu-id="aae5b-103">中指定的範圍變數的名稱`Select`， `From`， `Aggregate`，或`Let`子句重複查詢，或查詢所隱含宣告的變數名稱已先前指定的範圍變數的名稱例如，欄位名稱或彙總函式的名稱。</span><span class="sxs-lookup"><span data-stu-id="aae5b-103">A range variable name specified in a `Select`, `From`, `Aggregate`, or `Let` clause duplicates the name of a range variable already specified previously in the query, or the name of a variable that is implicitly declared by the query, such as a field name or the name of an aggregate function.</span></span>  
  
 <span data-ttu-id="aae5b-104">**錯誤 ID:** BC36633</span><span class="sxs-lookup"><span data-stu-id="aae5b-104">**Error ID:** BC36633</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="aae5b-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="aae5b-105">To correct this error</span></span>  
  
-   <span data-ttu-id="aae5b-106">請確定在特定的查詢範圍中的所有範圍變數都有唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="aae5b-106">Ensure that all range variables in a particular query scope have unique names.</span></span> <span data-ttu-id="aae5b-107">您可以將查詢括在括號，以確保巢狀的查詢都有唯一的範圍。</span><span class="sxs-lookup"><span data-stu-id="aae5b-107">You can enclose a query in parentheses to ensure that nested queries have a unique scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aae5b-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aae5b-108">See also</span></span>

- [<span data-ttu-id="aae5b-109">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="aae5b-109">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="aae5b-110">From 子句</span><span class="sxs-lookup"><span data-stu-id="aae5b-110">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="aae5b-111">Let 子句</span><span class="sxs-lookup"><span data-stu-id="aae5b-111">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)
- [<span data-ttu-id="aae5b-112">Aggregate 子句</span><span class="sxs-lookup"><span data-stu-id="aae5b-112">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="aae5b-113">Select 子句</span><span class="sxs-lookup"><span data-stu-id="aae5b-113">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
