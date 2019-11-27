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
ms.openlocfilehash: 94471898807ef4552564c3e01465f2b2f6211d0c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335370"
---
# <a name="distinct-clause-visual-basic"></a><span data-ttu-id="9cb01-102">Distinct 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9cb01-102">Distinct Clause (Visual Basic)</span></span>
<span data-ttu-id="9cb01-103">限制目前範圍變數的值，以排除後續查詢子句中的重複值。</span><span class="sxs-lookup"><span data-stu-id="9cb01-103">Restricts the values of the current range variable to eliminate duplicate values in subsequent query clauses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cb01-104">語法</span><span class="sxs-lookup"><span data-stu-id="9cb01-104">Syntax</span></span>  
  
```vb  
Distinct  
```  
  
## <a name="remarks"></a><span data-ttu-id="9cb01-105">備註</span><span class="sxs-lookup"><span data-stu-id="9cb01-105">Remarks</span></span>  
 <span data-ttu-id="9cb01-106">您可以使用 `Distinct` 子句來傳回唯一專案的清單。</span><span class="sxs-lookup"><span data-stu-id="9cb01-106">You can use the `Distinct` clause to return a list of unique items.</span></span> <span data-ttu-id="9cb01-107">`Distinct` 子句會導致查詢忽略重複的查詢結果。</span><span class="sxs-lookup"><span data-stu-id="9cb01-107">The `Distinct` clause causes the query to ignore duplicate query results.</span></span> <span data-ttu-id="9cb01-108">`Distinct` 子句適用于 `Select` 子句所指定之所有傳回欄位的重複值。</span><span class="sxs-lookup"><span data-stu-id="9cb01-108">The `Distinct` clause applies to duplicate values for all return fields specified by the `Select` clause.</span></span> <span data-ttu-id="9cb01-109">如果未指定任何 `Select` 子句，則 `Distinct` 子句會套用至 `From` 子句中所識別查詢的範圍變數。</span><span class="sxs-lookup"><span data-stu-id="9cb01-109">If no `Select` clause is specified, the `Distinct` clause is applied to the range variable for the query identified in the `From` clause.</span></span> <span data-ttu-id="9cb01-110">如果範圍變數不是不可變的類型，則只有當類型的所有成員符合現有的查詢結果時，查詢才會忽略查詢結果。</span><span class="sxs-lookup"><span data-stu-id="9cb01-110">If the range variable is not an immutable type, the query will only ignore a query result if all members of the type match an existing query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9cb01-111">範例</span><span class="sxs-lookup"><span data-stu-id="9cb01-111">Example</span></span>  
 <span data-ttu-id="9cb01-112">下列查詢運算式會聯結客戶清單和客戶訂單清單。</span><span class="sxs-lookup"><span data-stu-id="9cb01-112">The following query expression joins a list of customers and a list of customer orders.</span></span> <span data-ttu-id="9cb01-113">包含 `Distinct` 子句，以傳回唯一客戶名稱和訂單日期的清單。</span><span class="sxs-lookup"><span data-stu-id="9cb01-113">The `Distinct` clause is included to return a list of unique customer names and order dates.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#20)]  
  
## <a name="see-also"></a><span data-ttu-id="9cb01-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="9cb01-114">See also</span></span>

- [<span data-ttu-id="9cb01-115">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="9cb01-115">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="9cb01-116">查詢</span><span class="sxs-lookup"><span data-stu-id="9cb01-116">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="9cb01-117">From 子句</span><span class="sxs-lookup"><span data-stu-id="9cb01-117">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="9cb01-118">Select 子句</span><span class="sxs-lookup"><span data-stu-id="9cb01-118">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="9cb01-119">Where 子句</span><span class="sxs-lookup"><span data-stu-id="9cb01-119">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
