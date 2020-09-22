---
title: Distinct 子句
ms.date: 07/20/2015
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
ms.openlocfilehash: 49eaab2e6a8c48d61518ea51ef2f644b6eb48314
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875278"
---
# <a name="distinct-clause-visual-basic"></a><span data-ttu-id="d2516-102">Distinct 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2516-102">Distinct Clause (Visual Basic)</span></span>

<span data-ttu-id="d2516-103">限制目前範圍變數的值，以消除後續查詢子句中的重複值。</span><span class="sxs-lookup"><span data-stu-id="d2516-103">Restricts the values of the current range variable to eliminate duplicate values in subsequent query clauses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2516-104">語法</span><span class="sxs-lookup"><span data-stu-id="d2516-104">Syntax</span></span>  
  
```vb  
Distinct  
```  
  
## <a name="remarks"></a><span data-ttu-id="d2516-105">備註</span><span class="sxs-lookup"><span data-stu-id="d2516-105">Remarks</span></span>  

 <span data-ttu-id="d2516-106">您可以使用 `Distinct` 子句來傳回唯一專案的清單。</span><span class="sxs-lookup"><span data-stu-id="d2516-106">You can use the `Distinct` clause to return a list of unique items.</span></span> <span data-ttu-id="d2516-107">`Distinct`子句會讓查詢忽略重複的查詢結果。</span><span class="sxs-lookup"><span data-stu-id="d2516-107">The `Distinct` clause causes the query to ignore duplicate query results.</span></span> <span data-ttu-id="d2516-108">`Distinct`子句會套用至子句所指定之所有傳回欄位的重複值 `Select` 。</span><span class="sxs-lookup"><span data-stu-id="d2516-108">The `Distinct` clause applies to duplicate values for all return fields specified by the `Select` clause.</span></span> <span data-ttu-id="d2516-109">如果未 `Select` 指定子句，則 `Distinct` 會將子句套用至子句中所識別之查詢的範圍變數 `From` 。</span><span class="sxs-lookup"><span data-stu-id="d2516-109">If no `Select` clause is specified, the `Distinct` clause is applied to the range variable for the query identified in the `From` clause.</span></span> <span data-ttu-id="d2516-110">如果範圍變數不是不可變的型別，則只有當型別的所有成員都符合現有的查詢結果時，查詢才會忽略查詢結果。</span><span class="sxs-lookup"><span data-stu-id="d2516-110">If the range variable is not an immutable type, the query will only ignore a query result if all members of the type match an existing query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2516-111">範例</span><span class="sxs-lookup"><span data-stu-id="d2516-111">Example</span></span>  

 <span data-ttu-id="d2516-112">下列查詢運算式會聯結客戶清單和客戶訂單清單。</span><span class="sxs-lookup"><span data-stu-id="d2516-112">The following query expression joins a list of customers and a list of customer orders.</span></span> <span data-ttu-id="d2516-113">`Distinct`包含的子句會傳回唯一客戶名稱和訂單日期的清單。</span><span class="sxs-lookup"><span data-stu-id="d2516-113">The `Distinct` clause is included to return a list of unique customer names and order dates.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#20)]  
  
## <a name="see-also"></a><span data-ttu-id="d2516-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2516-114">See also</span></span>

- [<span data-ttu-id="d2516-115">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="d2516-115">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="d2516-116">查詢</span><span class="sxs-lookup"><span data-stu-id="d2516-116">Queries</span></span>](index.md)
- [<span data-ttu-id="d2516-117">From 子句</span><span class="sxs-lookup"><span data-stu-id="d2516-117">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="d2516-118">Select 子句</span><span class="sxs-lookup"><span data-stu-id="d2516-118">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="d2516-119">Where 子句</span><span class="sxs-lookup"><span data-stu-id="d2516-119">Where Clause</span></span>](where-clause.md)
