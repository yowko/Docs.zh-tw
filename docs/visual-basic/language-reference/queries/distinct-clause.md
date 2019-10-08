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
ms.openlocfilehash: e8d3e38261a04c4d29faab351d24d6710413b09a
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004799"
---
# <a name="distinct-clause-visual-basic"></a><span data-ttu-id="4bfd2-102">Distinct 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4bfd2-102">Distinct Clause (Visual Basic)</span></span>
<span data-ttu-id="4bfd2-103">限制目前範圍變數的值，以排除後續查詢子句中的重複值。</span><span class="sxs-lookup"><span data-stu-id="4bfd2-103">Restricts the values of the current range variable to eliminate duplicate values in subsequent query clauses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bfd2-104">語法</span><span class="sxs-lookup"><span data-stu-id="4bfd2-104">Syntax</span></span>  
  
```vb  
Distinct  
```  
  
## <a name="remarks"></a><span data-ttu-id="4bfd2-105">備註</span><span class="sxs-lookup"><span data-stu-id="4bfd2-105">Remarks</span></span>  
 <span data-ttu-id="4bfd2-106">您可以使用 `Distinct` 子句來傳回唯一專案的清單。</span><span class="sxs-lookup"><span data-stu-id="4bfd2-106">You can use the `Distinct` clause to return a list of unique items.</span></span> <span data-ttu-id="4bfd2-107">@No__t 0 子句會導致查詢忽略重複的查詢結果。</span><span class="sxs-lookup"><span data-stu-id="4bfd2-107">The `Distinct` clause causes the query to ignore duplicate query results.</span></span> <span data-ttu-id="4bfd2-108">@No__t-0 子句適用于 `Select` 子句所指定之所有傳回欄位的重複值。</span><span class="sxs-lookup"><span data-stu-id="4bfd2-108">The `Distinct` clause applies to duplicate values for all return fields specified by the `Select` clause.</span></span> <span data-ttu-id="4bfd2-109">如果未指定任何 `Select` 子句，則 `Distinct` 子句會套用至在 `From` 子句中識別之查詢的範圍變數。</span><span class="sxs-lookup"><span data-stu-id="4bfd2-109">If no `Select` clause is specified, the `Distinct` clause is applied to the range variable for the query identified in the `From` clause.</span></span> <span data-ttu-id="4bfd2-110">如果範圍變數不是不可變的類型，則只有當類型的所有成員符合現有的查詢結果時，查詢才會忽略查詢結果。</span><span class="sxs-lookup"><span data-stu-id="4bfd2-110">If the range variable is not an immutable type, the query will only ignore a query result if all members of the type match an existing query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4bfd2-111">範例</span><span class="sxs-lookup"><span data-stu-id="4bfd2-111">Example</span></span>  
 <span data-ttu-id="4bfd2-112">下列查詢運算式會聯結客戶清單和客戶訂單清單。</span><span class="sxs-lookup"><span data-stu-id="4bfd2-112">The following query expression joins a list of customers and a list of customer orders.</span></span> <span data-ttu-id="4bfd2-113">包含的 `Distinct` 子句會傳回唯一客戶名稱和訂單日期的清單。</span><span class="sxs-lookup"><span data-stu-id="4bfd2-113">The `Distinct` clause is included to return a list of unique customer names and order dates.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#20)]  
  
## <a name="see-also"></a><span data-ttu-id="4bfd2-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4bfd2-114">See also</span></span>

- [<span data-ttu-id="4bfd2-115">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="4bfd2-115">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="4bfd2-116">查詢</span><span class="sxs-lookup"><span data-stu-id="4bfd2-116">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="4bfd2-117">From 子句</span><span class="sxs-lookup"><span data-stu-id="4bfd2-117">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="4bfd2-118">Select 子句</span><span class="sxs-lookup"><span data-stu-id="4bfd2-118">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="4bfd2-119">Where 子句</span><span class="sxs-lookup"><span data-stu-id="4bfd2-119">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
