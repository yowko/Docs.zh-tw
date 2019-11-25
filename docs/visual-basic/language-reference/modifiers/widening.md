---
title: Widening
ms.date: 07/20/2015
f1_keywords:
- vb.widening
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Widening keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 646ae263-94d3-40a2-b0cc-64f619292f56
ms.openlocfilehash: 1c9aa78549ca6e41c9fe54c12e0aaec8e7cc30cb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347837"
---
# <a name="widening-visual-basic"></a><span data-ttu-id="3afa6-102">Widening (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3afa6-102">Widening (Visual Basic)</span></span>
<span data-ttu-id="3afa6-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that can hold all possible values of the original class or structure.</span><span class="sxs-lookup"><span data-stu-id="3afa6-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that can hold all possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-widening-keyword"></a><span data-ttu-id="3afa6-104">Converting with the Widening Keyword</span><span class="sxs-lookup"><span data-stu-id="3afa6-104">Converting with the Widening Keyword</span></span>  
 <span data-ttu-id="3afa6-105">The conversion procedure must specify `Public Shared` in addition to `Widening`.</span><span class="sxs-lookup"><span data-stu-id="3afa6-105">The conversion procedure must specify `Public Shared` in addition to `Widening`.</span></span>  
  
 <span data-ttu-id="3afa6-106">Widening conversions always succeed at run time and never incur data loss.</span><span class="sxs-lookup"><span data-stu-id="3afa6-106">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="3afa6-107">Examples are `Single` to `Double`, `Char` to `String`, and a derived type to its base type.</span><span class="sxs-lookup"><span data-stu-id="3afa6-107">Examples are `Single` to `Double`, `Char` to `String`, and a derived type to its base type.</span></span> <span data-ttu-id="3afa6-108">This last conversion is widening because the derived type contains all the members of the base type and thus is an instance of the base type.</span><span class="sxs-lookup"><span data-stu-id="3afa6-108">This last conversion is widening because the derived type contains all the members of the base type and thus is an instance of the base type.</span></span>  
  
 <span data-ttu-id="3afa6-109">The consuming code does not have to use `CType` for widening conversions, even if `Option Strict` is `On`.</span><span class="sxs-lookup"><span data-stu-id="3afa6-109">The consuming code does not have to use `CType` for widening conversions, even if `Option Strict` is `On`.</span></span>  
  
 <span data-ttu-id="3afa6-110">The `Widening` keyword can be used in this context:</span><span class="sxs-lookup"><span data-stu-id="3afa6-110">The `Widening` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="3afa6-111">Operator 陳述式</span><span class="sxs-lookup"><span data-stu-id="3afa6-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 <span data-ttu-id="3afa6-112">For example definitions of widening and narrowing conversion operators, see [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="3afa6-112">For example definitions of widening and narrowing conversion operators, see [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3afa6-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="3afa6-113">See also</span></span>

- [<span data-ttu-id="3afa6-114">Operator 陳述式</span><span class="sxs-lookup"><span data-stu-id="3afa6-114">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="3afa6-115">Narrowing</span><span class="sxs-lookup"><span data-stu-id="3afa6-115">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="3afa6-116">擴展和縮小轉換</span><span class="sxs-lookup"><span data-stu-id="3afa6-116">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="3afa6-117">如何：定義運算子</span><span class="sxs-lookup"><span data-stu-id="3afa6-117">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="3afa6-118">CType 函式</span><span class="sxs-lookup"><span data-stu-id="3afa6-118">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
- [<span data-ttu-id="3afa6-119">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="3afa6-119">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="3afa6-120">如何：定義轉換運算子</span><span class="sxs-lookup"><span data-stu-id="3afa6-120">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
