---
title: Boolean 資料類型
ms.date: 03/30/2017
ms.assetid: 57f7376b-4b11-4b35-98a9-780382053ceb
ms.openlocfilehash: 2535d72a89691466b977e1d4c460ff73e3b93dc2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61877392"
---
# <a name="boolean-data-types"></a><span data-ttu-id="66622-102">Boolean 資料類型</span><span class="sxs-lookup"><span data-stu-id="66622-102">Boolean Data Types</span></span>
<span data-ttu-id="66622-103">除了不會轉譯最少運算行為以外，在 Common Language Runtime (CLR) 中布林運算子會如預期運作。</span><span class="sxs-lookup"><span data-stu-id="66622-103">Boolean operators work as expected in the common language runtime (CLR), except that short-circuiting behavior is not translated.</span></span> <span data-ttu-id="66622-104">例如，Visual Basic `AndAlso` 運算子的行為方式如同 `And` 運算子。</span><span class="sxs-lookup"><span data-stu-id="66622-104">For example, the Visual Basic `AndAlso` operator behaves like the `And` operator.</span></span> <span data-ttu-id="66622-105">而 C# `&&` 運算子的行為方式則如同 `&` 運算子。</span><span class="sxs-lookup"><span data-stu-id="66622-105">The C# `&&` operator behaves like the `&` operator.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="66622-106">支援下列運算子。</span><span class="sxs-lookup"><span data-stu-id="66622-106">supports the following operators.</span></span>  
  
|<span data-ttu-id="66622-107">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="66622-107">Visual Basic</span></span>|<span data-ttu-id="66622-108">C#</span><span class="sxs-lookup"><span data-stu-id="66622-108">C#</span></span>|  
|------------------|---------|  
|[<span data-ttu-id="66622-109">And 運算子</span><span class="sxs-lookup"><span data-stu-id="66622-109">And Operator</span></span>](~/docs/visual-basic/language-reference/operators/and-operator.md)|[<span data-ttu-id="66622-110">& 運算子</span><span class="sxs-lookup"><span data-stu-id="66622-110">& Operator</span></span>](~/docs/csharp/language-reference/operators/boolean-logical-operators.md#logical-and-operator-)|  
|[<span data-ttu-id="66622-111">AndAlso 運算子</span><span class="sxs-lookup"><span data-stu-id="66622-111">AndAlso Operator</span></span>](~/docs/visual-basic/language-reference/operators/andalso-operator.md)|[<span data-ttu-id="66622-112">&& 運算子</span><span class="sxs-lookup"><span data-stu-id="66622-112">&& Operator</span></span>](~/docs/csharp/language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-)|  
|[<span data-ttu-id="66622-113">Or 運算子</span><span class="sxs-lookup"><span data-stu-id="66622-113">Or Operator</span></span>](~/docs/visual-basic/language-reference/operators/or-operator.md)|[<span data-ttu-id="66622-114">&#124; Operator</span><span class="sxs-lookup"><span data-stu-id="66622-114">&#124; Operator</span></span>](~/docs/csharp/language-reference/operators/boolean-logical-operators.md#logical-or-operator-)|  
|[<span data-ttu-id="66622-115">OrElse 運算子</span><span class="sxs-lookup"><span data-stu-id="66622-115">OrElse Operator</span></span>](~/docs/visual-basic/language-reference/operators/orelse-operator.md)|[<span data-ttu-id="66622-116">&#124;&#124;運算子</span><span class="sxs-lookup"><span data-stu-id="66622-116">&#124;&#124; Operator</span></span>](~/docs/csharp/language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-)|  
|[<span data-ttu-id="66622-117">Xor 運算子</span><span class="sxs-lookup"><span data-stu-id="66622-117">Xor Operator</span></span>](~/docs/visual-basic/language-reference/operators/xor-operator.md)|[<span data-ttu-id="66622-118">^ 運算子</span><span class="sxs-lookup"><span data-stu-id="66622-118">^ Operator</span></span>](~/docs/csharp/language-reference/operators/boolean-logical-operators.md#logical-exclusive-or-operator-)|  
|[<span data-ttu-id="66622-119">Not 運算子</span><span class="sxs-lookup"><span data-stu-id="66622-119">Not Operator</span></span>](~/docs/visual-basic/language-reference/operators/not-operator.md)|[<span data-ttu-id="66622-120">\! 運算子</span><span class="sxs-lookup"><span data-stu-id="66622-120">\! Operator</span></span>](~/docs/csharp/language-reference/operators/boolean-logical-operators.md#logical-negation-operator-)|  
  
## <a name="see-also"></a><span data-ttu-id="66622-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66622-121">See also</span></span>

- [<span data-ttu-id="66622-122">資料類型和函式</span><span class="sxs-lookup"><span data-stu-id="66622-122">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
