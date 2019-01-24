---
title: 範圍變數&lt;變數&gt;隱藏了封閉區塊、 預先定義的範圍變數或查詢運算式中隱含宣告的變數中的變數
ms.date: 07/20/2015
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
ms.openlocfilehash: aef52ea912a4180a6505949c8077296628592c72
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54748112"
---
# <a name="range-variable-ltvariablegt-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a><span data-ttu-id="4ec1b-102">範圍變數&lt;變數&gt;隱藏了封閉區塊、 預先定義的範圍變數或查詢運算式中隱含宣告的變數中的變數</span><span class="sxs-lookup"><span data-stu-id="4ec1b-102">Range variable &lt;variable&gt; hides a variable in an enclosing block, a previously defined range variable, or an implicitly declared variable in a query expression</span></span>
<span data-ttu-id="4ec1b-103">中指定的範圍變數的名稱`Select`， `From`， `Aggregate`，或`Let`子句重複查詢，或查詢所隱含宣告的變數名稱已先前指定的範圍變數的名稱例如，欄位名稱或彙總函式的名稱。</span><span class="sxs-lookup"><span data-stu-id="4ec1b-103">A range variable name specified in a `Select`, `From`, `Aggregate`, or `Let` clause duplicates the name of a range variable already specified previously in the query, or the name of a variable that is implicitly declared by the query, such as a field name or the name of an aggregate function.</span></span>  
  
 <span data-ttu-id="4ec1b-104">**錯誤 ID:** BC36633</span><span class="sxs-lookup"><span data-stu-id="4ec1b-104">**Error ID:** BC36633</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4ec1b-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="4ec1b-105">To correct this error</span></span>  
  
-   <span data-ttu-id="4ec1b-106">請確定在特定的查詢範圍中的所有範圍變數都有唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="4ec1b-106">Ensure that all range variables in a particular query scope have unique names.</span></span> <span data-ttu-id="4ec1b-107">您可以將查詢括在括號，以確保巢狀的查詢都有唯一的範圍。</span><span class="sxs-lookup"><span data-stu-id="4ec1b-107">You can enclose a query in parentheses to ensure that nested queries have a unique scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ec1b-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ec1b-108">See also</span></span>
- [<span data-ttu-id="4ec1b-109">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="4ec1b-109">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="4ec1b-110">From 子句</span><span class="sxs-lookup"><span data-stu-id="4ec1b-110">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="4ec1b-111">Let 子句</span><span class="sxs-lookup"><span data-stu-id="4ec1b-111">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)
- [<span data-ttu-id="4ec1b-112">Aggregate 子句</span><span class="sxs-lookup"><span data-stu-id="4ec1b-112">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="4ec1b-113">Select 子句</span><span class="sxs-lookup"><span data-stu-id="4ec1b-113">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
