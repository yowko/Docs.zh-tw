---
title: '運算子宣告必須是其中一個: +、-，*，-、-、 ^， &amp;，喜歡，Mod、 和，Or、 Xor、 不是，<<>>、 =、 <>、 <、 < =、 >、 > =、 CType、 IsTrue、 IsFalse'
ms.date: 07/20/2015
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
ms.openlocfilehash: 4283547109ec312cc4fe07a054bbb8db3bff660f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59299185"
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not--"></a><span data-ttu-id="b5440-102">運算子宣告必須是其中一個: +、-，\*，\,/、 ^， &amp;，例如，Mod、，Or、 Xor、 不是， \< \<，>>...</span><span class="sxs-lookup"><span data-stu-id="b5440-102">Operator declaration must be one of:  +,-,\*,\,/,^, &amp;, Like, Mod, And, Or, Xor, Not, \<\<, >>...</span></span>
<span data-ttu-id="b5440-103">您可以宣告適用於多載的運算子。</span><span class="sxs-lookup"><span data-stu-id="b5440-103">You can declare only an operator that is eligible for overloading.</span></span> <span data-ttu-id="b5440-104">下表列出您可以宣告的運算子。</span><span class="sxs-lookup"><span data-stu-id="b5440-104">The following table lists the operators you can declare.</span></span>  
  
|<span data-ttu-id="b5440-105">類型</span><span class="sxs-lookup"><span data-stu-id="b5440-105">Type</span></span>|<span data-ttu-id="b5440-106">運算子</span><span class="sxs-lookup"><span data-stu-id="b5440-106">Operators</span></span>|  
|----------|---------------|  
|<span data-ttu-id="b5440-107">一元</span><span class="sxs-lookup"><span data-stu-id="b5440-107">Unary</span></span>|`+`<span data-ttu-id="b5440-108">, `-`, `IsFalse`, `IsTrue`,</span><span class="sxs-lookup"><span data-stu-id="b5440-108">, `-`, `IsFalse`, `IsTrue`,</span></span> `Not`|  
|<span data-ttu-id="b5440-109">二元</span><span class="sxs-lookup"><span data-stu-id="b5440-109">Binary</span></span>|`+`<span data-ttu-id="b5440-110">, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`,</span><span class="sxs-lookup"><span data-stu-id="b5440-110">, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`,</span></span> `Xor`|  
|<span data-ttu-id="b5440-111">轉換 (一元)</span><span class="sxs-lookup"><span data-stu-id="b5440-111">Conversion (unary)</span></span>|`CType`|  
  
 <span data-ttu-id="b5440-112">請注意， `=` ，二元清單中的運算子為比較運算子，而不是指派運算子。</span><span class="sxs-lookup"><span data-stu-id="b5440-112">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="b5440-113">**錯誤 ID:** BC33000</span><span class="sxs-lookup"><span data-stu-id="b5440-113">**Error ID:** BC33000</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b5440-114">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="b5440-114">To correct this error</span></span>  
  
1. <span data-ttu-id="b5440-115">從一組可多載的運算子中選取運算子。</span><span class="sxs-lookup"><span data-stu-id="b5440-115">Select an operator from the set of overloadable operators.</span></span>  
  
2. <span data-ttu-id="b5440-116">如果您需要多載無法直接多載之運算子的功能，請建立接受適當參數並傳回適當值的 `Function` 程序。</span><span class="sxs-lookup"><span data-stu-id="b5440-116">If you need the functionality of overloading an operator that you cannot overload directly, create a `Function` procedure that takes the appropriate parameters and returns the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5440-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5440-117">See also</span></span>

- [<span data-ttu-id="b5440-118">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="b5440-118">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="b5440-119">運算子程序</span><span class="sxs-lookup"><span data-stu-id="b5440-119">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="b5440-120">HOW TO：定義運算子</span><span class="sxs-lookup"><span data-stu-id="b5440-120">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="b5440-121">HOW TO：定義轉換運算子</span><span class="sxs-lookup"><span data-stu-id="b5440-121">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="b5440-122">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="b5440-122">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
