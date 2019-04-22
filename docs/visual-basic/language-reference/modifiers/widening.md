---
title: Widening (Visual Basic)
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
ms.openlocfilehash: d7d43d4f5f931881d5c8b663c719fe7f92559799
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58825309"
---
# <a name="widening-visual-basic"></a><span data-ttu-id="08af4-102">Widening (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="08af4-102">Widening (Visual Basic)</span></span>
<span data-ttu-id="08af4-103">表示轉換運算子 (`CType`) 將類別或結構轉換成的型別，可以保留原始的類別或結構的所有可能的值。</span><span class="sxs-lookup"><span data-stu-id="08af4-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that can hold all possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-widening-keyword"></a><span data-ttu-id="08af4-104">轉換擴展關鍵字</span><span class="sxs-lookup"><span data-stu-id="08af4-104">Converting with the Widening Keyword</span></span>  
 <span data-ttu-id="08af4-105">轉換程序必須指定`Public Shared`除了`Widening`。</span><span class="sxs-lookup"><span data-stu-id="08af4-105">The conversion procedure must specify `Public Shared` in addition to `Widening`.</span></span>  
  
 <span data-ttu-id="08af4-106">擴展轉換時，一律在執行階段成功，而且永遠不會造成資料遺失。</span><span class="sxs-lookup"><span data-stu-id="08af4-106">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="08af4-107">範例包括`Single`要`Double`，`Char`到`String`，和其基底類型衍生型別。</span><span class="sxs-lookup"><span data-stu-id="08af4-107">Examples are `Single` to `Double`, `Char` to `String`, and a derived type to its base type.</span></span> <span data-ttu-id="08af4-108">因為衍生的型別包含基底類型的所有成員，因此是基底類型的執行個體，則會擴展這個最後一個轉換。</span><span class="sxs-lookup"><span data-stu-id="08af4-108">This last conversion is widening because the derived type contains all the members of the base type and thus is an instance of the base type.</span></span>  
  
 <span data-ttu-id="08af4-109">使用的程式碼不需要使用`CType`的擴展轉換，即使`Option Strict`是`On`。</span><span class="sxs-lookup"><span data-stu-id="08af4-109">The consuming code does not have to use `CType` for widening conversions, even if `Option Strict` is `On`.</span></span>  
  
 <span data-ttu-id="08af4-110">`Widening`關鍵字可以用在此內容中：</span><span class="sxs-lookup"><span data-stu-id="08af4-110">The `Widening` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="08af4-111">Operator 陳述式</span><span class="sxs-lookup"><span data-stu-id="08af4-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 <span data-ttu-id="08af4-112">定義擴展和縮小轉換運算子，例如看到[How to:定義轉換運算子](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="08af4-112">For example definitions of widening and narrowing conversion operators, see [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08af4-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08af4-113">See also</span></span>

- [<span data-ttu-id="08af4-114">Operator 陳述式</span><span class="sxs-lookup"><span data-stu-id="08af4-114">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="08af4-115">Narrowing</span><span class="sxs-lookup"><span data-stu-id="08af4-115">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="08af4-116">擴展和縮小轉換</span><span class="sxs-lookup"><span data-stu-id="08af4-116">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="08af4-117">如何：定義運算子</span><span class="sxs-lookup"><span data-stu-id="08af4-117">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="08af4-118">CType 函式</span><span class="sxs-lookup"><span data-stu-id="08af4-118">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
- [<span data-ttu-id="08af4-119">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="08af4-119">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="08af4-120">如何：定義轉換運算子</span><span class="sxs-lookup"><span data-stu-id="08af4-120">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
