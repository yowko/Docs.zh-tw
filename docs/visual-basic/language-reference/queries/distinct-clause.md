---
title: Distinct 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
ms.openlocfilehash: 18d09d8018303aab6a69801c84c7ec9c6ea19ca9
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44083828"
---
# <a name="distinct-clause-visual-basic"></a><span data-ttu-id="24c56-102">Distinct 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24c56-102">Distinct Clause (Visual Basic)</span></span>
<span data-ttu-id="24c56-103">限制目前的範圍變數，以消除重複的值，在後續的查詢子句中的值。</span><span class="sxs-lookup"><span data-stu-id="24c56-103">Restricts the values of the current range variable to eliminate duplicate values in subsequent query clauses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24c56-104">語法</span><span class="sxs-lookup"><span data-stu-id="24c56-104">Syntax</span></span>  
  
```  
Distinct  
```  
  
## <a name="remarks"></a><span data-ttu-id="24c56-105">備註</span><span class="sxs-lookup"><span data-stu-id="24c56-105">Remarks</span></span>  
 <span data-ttu-id="24c56-106">您可以使用`Distinct`子句傳回唯一項目清單。</span><span class="sxs-lookup"><span data-stu-id="24c56-106">You can use the `Distinct` clause to return a list of unique items.</span></span> <span data-ttu-id="24c56-107">`Distinct`子句會使要忽略重複的查詢結果的查詢。</span><span class="sxs-lookup"><span data-stu-id="24c56-107">The `Distinct` clause causes the query to ignore duplicate query results.</span></span> <span data-ttu-id="24c56-108">`Distinct`子句會套用到重複的值，所有傳回所指定的欄位`Select`子句。</span><span class="sxs-lookup"><span data-stu-id="24c56-108">The `Distinct` clause applies to duplicate values for all return fields specified by the `Select` clause.</span></span> <span data-ttu-id="24c56-109">如果沒有`Select`指定子句，則`Distinct`子句會套用到查詢中所識別的範圍變數`From`子句。</span><span class="sxs-lookup"><span data-stu-id="24c56-109">If no `Select` clause is specified, the `Distinct` clause is applied to the range variable for the query identified in the `From` clause.</span></span> <span data-ttu-id="24c56-110">如果範圍變數不是不可變的類型，查詢將只略過查詢結果型別的所有成員符合現有的查詢結果。</span><span class="sxs-lookup"><span data-stu-id="24c56-110">If the range variable is not an immutable type, the query will only ignore a query result if all members of the type match an existing query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24c56-111">範例</span><span class="sxs-lookup"><span data-stu-id="24c56-111">Example</span></span>  
 <span data-ttu-id="24c56-112">下列查詢運算式會聯結一份客戶和客戶訂單的清單。</span><span class="sxs-lookup"><span data-stu-id="24c56-112">The following query expression joins a list of customers and a list of customer orders.</span></span> <span data-ttu-id="24c56-113">`Distinct`子句是包含要傳回的唯一客戶名稱清單，並在訂單日期。</span><span class="sxs-lookup"><span data-stu-id="24c56-113">The `Distinct` clause is included to return a list of unique customer names and order dates.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#20](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/distinct-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="24c56-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24c56-114">See Also</span></span>  
 [<span data-ttu-id="24c56-115">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="24c56-115">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="24c56-116">查詢</span><span class="sxs-lookup"><span data-stu-id="24c56-116">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)  
 [<span data-ttu-id="24c56-117">From 子句</span><span class="sxs-lookup"><span data-stu-id="24c56-117">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="24c56-118">Select 子句</span><span class="sxs-lookup"><span data-stu-id="24c56-118">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="24c56-119">Where 子句</span><span class="sxs-lookup"><span data-stu-id="24c56-119">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
