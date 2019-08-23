---
title: Boolean 資料類型
ms.date: 03/30/2017
ms.assetid: 57f7376b-4b11-4b35-98a9-780382053ceb
ms.openlocfilehash: f200445d2ba7846f9dc467c7f06bce4225c88865
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964087"
---
# <a name="boolean-data-types"></a><span data-ttu-id="ce131-102">Boolean 資料類型</span><span class="sxs-lookup"><span data-stu-id="ce131-102">Boolean Data Types</span></span>
<span data-ttu-id="ce131-103">除了不會轉譯最少運算行為以外，在 Common Language Runtime (CLR) 中布林運算子會如預期運作。</span><span class="sxs-lookup"><span data-stu-id="ce131-103">Boolean operators work as expected in the common language runtime (CLR), except that short-circuiting behavior is not translated.</span></span> <span data-ttu-id="ce131-104">例如，Visual Basic `AndAlso` 運算子的行為方式如同 `And` 運算子。</span><span class="sxs-lookup"><span data-stu-id="ce131-104">For example, the Visual Basic `AndAlso` operator behaves like the `And` operator.</span></span> <span data-ttu-id="ce131-105">而 C# `&&` 運算子的行為方式則如同 `&` 運算子。</span><span class="sxs-lookup"><span data-stu-id="ce131-105">The C# `&&` operator behaves like the `&` operator.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="ce131-106">支援下列運算子。</span><span class="sxs-lookup"><span data-stu-id="ce131-106">supports the following operators.</span></span>  
  
|<span data-ttu-id="ce131-107">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ce131-107">Visual Basic</span></span>|<span data-ttu-id="ce131-108">C#</span><span class="sxs-lookup"><span data-stu-id="ce131-108">C#</span></span>|  
|------------------|---------|  
|[<span data-ttu-id="ce131-109">And 運算子</span><span class="sxs-lookup"><span data-stu-id="ce131-109">And Operator</span></span>](../../../../../visual-basic/language-reference/operators/and-operator.md)|[<span data-ttu-id="ce131-110">& 運算子</span><span class="sxs-lookup"><span data-stu-id="ce131-110">& Operator</span></span>](../../../../../csharp/language-reference/operators/boolean-logical-operators.md#logical-and-operator-)|  
|[<span data-ttu-id="ce131-111">AndAlso 運算子</span><span class="sxs-lookup"><span data-stu-id="ce131-111">AndAlso Operator</span></span>](../../../../../visual-basic/language-reference/operators/andalso-operator.md)|[<span data-ttu-id="ce131-112">&& 運算子</span><span class="sxs-lookup"><span data-stu-id="ce131-112">&& Operator</span></span>](../../../../../csharp/language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-)|  
|[<span data-ttu-id="ce131-113">Or 運算子</span><span class="sxs-lookup"><span data-stu-id="ce131-113">Or Operator</span></span>](../../../../../visual-basic/language-reference/operators/or-operator.md)|[<span data-ttu-id="ce131-114">&#124;操作</span><span class="sxs-lookup"><span data-stu-id="ce131-114">&#124; Operator</span></span>](../../../../../csharp/language-reference/operators/boolean-logical-operators.md#logical-or-operator-)|  
|[<span data-ttu-id="ce131-115">OrElse 運算子</span><span class="sxs-lookup"><span data-stu-id="ce131-115">OrElse Operator</span></span>](../../../../../visual-basic/language-reference/operators/orelse-operator.md)|[<span data-ttu-id="ce131-116">&#124;&#124;操作</span><span class="sxs-lookup"><span data-stu-id="ce131-116">&#124;&#124; Operator</span></span>](../../../../../csharp/language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-)|  
|[<span data-ttu-id="ce131-117">Xor 運算子</span><span class="sxs-lookup"><span data-stu-id="ce131-117">Xor Operator</span></span>](../../../../../visual-basic/language-reference/operators/xor-operator.md)|[<span data-ttu-id="ce131-118">^ 運算子</span><span class="sxs-lookup"><span data-stu-id="ce131-118">^ Operator</span></span>](../../../../../csharp/language-reference/operators/boolean-logical-operators.md#logical-exclusive-or-operator-)|  
|[<span data-ttu-id="ce131-119">Not 運算子</span><span class="sxs-lookup"><span data-stu-id="ce131-119">Not Operator</span></span>](../../../../../visual-basic/language-reference/operators/not-operator.md)|[<span data-ttu-id="ce131-120">\! 運算子</span><span class="sxs-lookup"><span data-stu-id="ce131-120">\! Operator</span></span>](../../../../../csharp/language-reference/operators/boolean-logical-operators.md#logical-negation-operator-)|  
  
## <a name="see-also"></a><span data-ttu-id="ce131-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce131-121">See also</span></span>

- [<span data-ttu-id="ce131-122">資料類型和函式</span><span class="sxs-lookup"><span data-stu-id="ce131-122">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
