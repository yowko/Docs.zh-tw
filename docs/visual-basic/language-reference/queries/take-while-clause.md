---
title: Take While 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: fe6ee470698504bc0434930cc9aa6de712e04254
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004682"
---
# <a name="take-while-clause-visual-basic"></a><span data-ttu-id="97012-102">Take While 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="97012-102">Take While Clause (Visual Basic)</span></span>
<span data-ttu-id="97012-103">只要指定的條件為 `true`，即包含集合中的項目，並略過其餘項目。</span><span class="sxs-lookup"><span data-stu-id="97012-103">Includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97012-104">語法</span><span class="sxs-lookup"><span data-stu-id="97012-104">Syntax</span></span>  
  
```vb  
Take While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="97012-105">組件</span><span class="sxs-lookup"><span data-stu-id="97012-105">Parts</span></span>  
  
|<span data-ttu-id="97012-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="97012-106">Term</span></span>|<span data-ttu-id="97012-107">定義</span><span class="sxs-lookup"><span data-stu-id="97012-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="97012-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="97012-108">Required.</span></span> <span data-ttu-id="97012-109">運算式，表示要測試元素的條件。</span><span class="sxs-lookup"><span data-stu-id="97012-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="97012-110">運算式必須傳回 `Boolean` 值或函式對等用法，例如要評估為 `Boolean` 的 `Integer`。</span><span class="sxs-lookup"><span data-stu-id="97012-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97012-111">備註</span><span class="sxs-lookup"><span data-stu-id="97012-111">Remarks</span></span>  
 <span data-ttu-id="97012-112">@No__t-0 子句包含查詢結果開頭的元素，直到提供的 `expression` 傳回 `false` 為止。</span><span class="sxs-lookup"><span data-stu-id="97012-112">The `Take While` clause includes elements from the start of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="97012-113">在 `expression` 傳回 `false` 之後，查詢將會略過所有剩餘的元素。</span><span class="sxs-lookup"><span data-stu-id="97012-113">After the `expression` returns `false`, the query will bypass all remaining elements.</span></span> <span data-ttu-id="97012-114">針對其餘的結果，會忽略 `expression`。</span><span class="sxs-lookup"><span data-stu-id="97012-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="97012-115">@No__t-0 子句與 `Where` 子句不同之處在于，@no__t 2 子句可以用來包含符合特定條件之查詢中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="97012-115">The `Take While` clause differs from the `Where` clause in that the `Where` clause can be used to include all elements from a query that meet a particular condition.</span></span> <span data-ttu-id="97012-116">只有在第一次未滿足條件時，@no__t 0 子句才會包含元素。</span><span class="sxs-lookup"><span data-stu-id="97012-116">The `Take While` clause includes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="97012-117">當您使用已排序的查詢結果時，`Take While` 子句最有用。</span><span class="sxs-lookup"><span data-stu-id="97012-117">The `Take While` clause is most useful when you are working with an ordered query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97012-118">範例</span><span class="sxs-lookup"><span data-stu-id="97012-118">Example</span></span>  
 <span data-ttu-id="97012-119">下列程式碼範例會使用 `Take While` 子句來抓取結果，直到找不到任何訂單的第一個客戶為止。</span><span class="sxs-lookup"><span data-stu-id="97012-119">The following code example uses the `Take While` clause to retrieve results until the first customer without any orders is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="97012-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97012-120">See also</span></span>

- [<span data-ttu-id="97012-121">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="97012-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="97012-122">查詢</span><span class="sxs-lookup"><span data-stu-id="97012-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="97012-123">Select 子句</span><span class="sxs-lookup"><span data-stu-id="97012-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="97012-124">From 子句</span><span class="sxs-lookup"><span data-stu-id="97012-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="97012-125">Take 子句</span><span class="sxs-lookup"><span data-stu-id="97012-125">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
- [<span data-ttu-id="97012-126">Skip While 子句</span><span class="sxs-lookup"><span data-stu-id="97012-126">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="97012-127">Where 子句</span><span class="sxs-lookup"><span data-stu-id="97012-127">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
