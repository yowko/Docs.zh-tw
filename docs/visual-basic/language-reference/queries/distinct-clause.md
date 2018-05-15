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
ms.openlocfilehash: 4b0ce12f6361d3dc6e5cc3601e96fc3a9bcf3841
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="distinct-clause-visual-basic"></a><span data-ttu-id="1be2b-102">Distinct 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1be2b-102">Distinct Clause (Visual Basic)</span></span>
<span data-ttu-id="1be2b-103">限制目前的範圍變數，以消除重複的值，在後續的查詢子句中的值。</span><span class="sxs-lookup"><span data-stu-id="1be2b-103">Restricts the values of the current range variable to eliminate duplicate values in subsequent query clauses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1be2b-104">語法</span><span class="sxs-lookup"><span data-stu-id="1be2b-104">Syntax</span></span>  
  
```  
Distinct  
```  
  
## <a name="remarks"></a><span data-ttu-id="1be2b-105">備註</span><span class="sxs-lookup"><span data-stu-id="1be2b-105">Remarks</span></span>  
 <span data-ttu-id="1be2b-106">您可以使用`Distinct`子句，傳回唯一項目清單。</span><span class="sxs-lookup"><span data-stu-id="1be2b-106">You can use the `Distinct` clause to return a list of unique items.</span></span> <span data-ttu-id="1be2b-107">`Distinct`子句會讓查詢略過重複的查詢結果。</span><span class="sxs-lookup"><span data-stu-id="1be2b-107">The `Distinct` clause causes the query to ignore duplicate query results.</span></span> <span data-ttu-id="1be2b-108">`Distinct`子句套用到重複的值，所有傳回指定的欄位`Select`子句。</span><span class="sxs-lookup"><span data-stu-id="1be2b-108">The `Distinct` clause applies to duplicate values for all return fields specified by the `Select` clause.</span></span> <span data-ttu-id="1be2b-109">如果沒有`Select`指定子句，`Distinct`子句會套用到查詢中所識別的範圍變數`From`子句。</span><span class="sxs-lookup"><span data-stu-id="1be2b-109">If no `Select` clause is specified, the `Distinct` clause is applied to the range variable for the query identified in the `From` clause.</span></span> <span data-ttu-id="1be2b-110">如果範圍變數不是不可變的類型，查詢將只略過查詢結果型別的所有成員符合現有查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="1be2b-110">If the range variable is not an immutable type, the query will only ignore a query result if all members of the type match an existing query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1be2b-111">範例</span><span class="sxs-lookup"><span data-stu-id="1be2b-111">Example</span></span>  
 <span data-ttu-id="1be2b-112">下列查詢運算式會聯結一份客戶與客戶訂單的清單。</span><span class="sxs-lookup"><span data-stu-id="1be2b-112">The following query expression joins a list of customers and a list of customer orders.</span></span> <span data-ttu-id="1be2b-113">`Distinct`子句也會傳回一份唯一客戶名稱及訂購日期。</span><span class="sxs-lookup"><span data-stu-id="1be2b-113">The `Distinct` clause is included to return a list of unique customer names and order dates.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#20](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/distinct-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1be2b-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1be2b-114">See Also</span></span>  
 [<span data-ttu-id="1be2b-115">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="1be2b-115">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="1be2b-116">查詢</span><span class="sxs-lookup"><span data-stu-id="1be2b-116">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="1be2b-117">From 子句</span><span class="sxs-lookup"><span data-stu-id="1be2b-117">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="1be2b-118">Select 子句</span><span class="sxs-lookup"><span data-stu-id="1be2b-118">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="1be2b-119">Where 子句</span><span class="sxs-lookup"><span data-stu-id="1be2b-119">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
