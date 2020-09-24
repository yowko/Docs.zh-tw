---
title: Boolean 資料類型
ms.date: 03/30/2017
ms.assetid: 57f7376b-4b11-4b35-98a9-780382053ceb
ms.openlocfilehash: e2175afc24cfc7db38c1b8e1dbb11757f633960a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156065"
---
# <a name="boolean-data-types"></a><span data-ttu-id="291de-102">Boolean 資料類型</span><span class="sxs-lookup"><span data-stu-id="291de-102">Boolean Data Types</span></span>

<span data-ttu-id="291de-103">除了不會轉譯最少運算行為以外，在 Common Language Runtime (CLR) 中布林運算子會如預期運作。</span><span class="sxs-lookup"><span data-stu-id="291de-103">Boolean operators work as expected in the common language runtime (CLR), except that short-circuiting behavior is not translated.</span></span> <span data-ttu-id="291de-104">例如，Visual Basic `AndAlso` 運算子的行為方式如同 `And` 運算子。</span><span class="sxs-lookup"><span data-stu-id="291de-104">For example, the Visual Basic `AndAlso` operator behaves like the `And` operator.</span></span> <span data-ttu-id="291de-105">而 C# `&&` 運算子的行為方式則如同 `&` 運算子。</span><span class="sxs-lookup"><span data-stu-id="291de-105">The C# `&&` operator behaves like the `&` operator.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="291de-106">支援下列運算子。</span><span class="sxs-lookup"><span data-stu-id="291de-106">supports the following operators.</span></span>  
  
|<span data-ttu-id="291de-107">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="291de-107">Visual Basic</span></span>|<span data-ttu-id="291de-108">C#</span><span class="sxs-lookup"><span data-stu-id="291de-108">C#</span></span>|  
|------------------|---------|  
|[<span data-ttu-id="291de-109">And 運算子</span><span class="sxs-lookup"><span data-stu-id="291de-109">And Operator</span></span>](../../../../../visual-basic/language-reference/operators/and-operator.md)|[<span data-ttu-id="291de-110">& 運算子</span><span class="sxs-lookup"><span data-stu-id="291de-110">& Operator</span></span>](../../../../../csharp/language-reference/operators/boolean-logical-operators.md#logical-and-operator-)|  
|[<span data-ttu-id="291de-111">AndAlso 運算子</span><span class="sxs-lookup"><span data-stu-id="291de-111">AndAlso Operator</span></span>](../../../../../visual-basic/language-reference/operators/andalso-operator.md)|[<span data-ttu-id="291de-112">&& 運算子</span><span class="sxs-lookup"><span data-stu-id="291de-112">&& Operator</span></span>](../../../../../csharp/language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-)|  
|[<span data-ttu-id="291de-113">Or 運算子</span><span class="sxs-lookup"><span data-stu-id="291de-113">Or Operator</span></span>](../../../../../visual-basic/language-reference/operators/or-operator.md)|[<span data-ttu-id="291de-114">&#124; 運算子</span><span class="sxs-lookup"><span data-stu-id="291de-114">&#124; Operator</span></span>](../../../../../csharp/language-reference/operators/boolean-logical-operators.md#logical-or-operator-)|  
|[<span data-ttu-id="291de-115">OrElse 運算子</span><span class="sxs-lookup"><span data-stu-id="291de-115">OrElse Operator</span></span>](../../../../../visual-basic/language-reference/operators/orelse-operator.md)|[<span data-ttu-id="291de-116">&#124;&#124; 運算子</span><span class="sxs-lookup"><span data-stu-id="291de-116">&#124;&#124; Operator</span></span>](../../../../../csharp/language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-)|  
|[<span data-ttu-id="291de-117">Xor 運算子</span><span class="sxs-lookup"><span data-stu-id="291de-117">Xor Operator</span></span>](../../../../../visual-basic/language-reference/operators/xor-operator.md)|[<span data-ttu-id="291de-118">^ 運算子</span><span class="sxs-lookup"><span data-stu-id="291de-118">^ Operator</span></span>](../../../../../csharp/language-reference/operators/boolean-logical-operators.md#logical-exclusive-or-operator-)|  
|[<span data-ttu-id="291de-119">Not 運算子</span><span class="sxs-lookup"><span data-stu-id="291de-119">Not Operator</span></span>](../../../../../visual-basic/language-reference/operators/not-operator.md)|[<span data-ttu-id="291de-120">\! 運算元</span><span class="sxs-lookup"><span data-stu-id="291de-120">\! Operator</span></span>](../../../../../csharp/language-reference/operators/boolean-logical-operators.md#logical-negation-operator-)|  
  
## <a name="see-also"></a><span data-ttu-id="291de-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="291de-121">See also</span></span>

- [<span data-ttu-id="291de-122">資料類型與函式</span><span class="sxs-lookup"><span data-stu-id="291de-122">Data Types and Functions</span></span>](data-types-and-functions.md)
