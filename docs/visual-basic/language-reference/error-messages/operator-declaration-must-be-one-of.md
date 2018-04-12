---
title: '運算子宣告必須為其中一個: +、-，*，-、-^， &amp;，Like、 Mod、 和，Or、 Xor、 Not、 &lt; &lt;， &gt; &gt;，=， &lt; &gt;， &lt;， &lt;=、 &gt;&gt;=、 CType、 IsTrue、 IsFalse'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 80c8358dd13105c18e73e94735a51b02d5bd22c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not-ltlt-gtgt"></a><span data-ttu-id="cc24e-102">運算子宣告必須為其中一個: +、-，\*，\,/、 ^， &amp;，Like、 Mod、，Or、 Xor、 Not、 &lt; &lt;， &gt; &gt;...</span><span class="sxs-lookup"><span data-stu-id="cc24e-102">Operator declaration must be one of:  +,-,\*,\,/,^, &amp;, Like, Mod, And, Or, Xor, Not, &lt;&lt;, &gt;&gt;...</span></span>
<span data-ttu-id="cc24e-103">您可以宣告適用於多載的運算子。</span><span class="sxs-lookup"><span data-stu-id="cc24e-103">You can declare only an operator that is eligible for overloading.</span></span> <span data-ttu-id="cc24e-104">下表列出您可以宣告的運算子。</span><span class="sxs-lookup"><span data-stu-id="cc24e-104">The following table lists the operators you can declare.</span></span>  
  
|<span data-ttu-id="cc24e-105">類型</span><span class="sxs-lookup"><span data-stu-id="cc24e-105">Type</span></span>|<span data-ttu-id="cc24e-106">運算子</span><span class="sxs-lookup"><span data-stu-id="cc24e-106">Operators</span></span>|  
|----------|---------------|  
|<span data-ttu-id="cc24e-107">一元</span><span class="sxs-lookup"><span data-stu-id="cc24e-107">Unary</span></span>|<span data-ttu-id="cc24e-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="cc24e-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|  
|<span data-ttu-id="cc24e-109">二元</span><span class="sxs-lookup"><span data-stu-id="cc24e-109">Binary</span></span>|<span data-ttu-id="cc24e-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="cc24e-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|  
|<span data-ttu-id="cc24e-111">轉換 (一元)</span><span class="sxs-lookup"><span data-stu-id="cc24e-111">Conversion (unary)</span></span>|`CType`|  
  
 <span data-ttu-id="cc24e-112">請注意，`=`二元清單中的運算子是比較運算子，而不是指派運算子。</span><span class="sxs-lookup"><span data-stu-id="cc24e-112">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="cc24e-113">**錯誤 ID:** BC33000</span><span class="sxs-lookup"><span data-stu-id="cc24e-113">**Error ID:** BC33000</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cc24e-114">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="cc24e-114">To correct this error</span></span>  
  
1.  <span data-ttu-id="cc24e-115">從一組可多載的運算子中選取運算子。</span><span class="sxs-lookup"><span data-stu-id="cc24e-115">Select an operator from the set of overloadable operators.</span></span>  
  
2.  <span data-ttu-id="cc24e-116">如果您需要多載無法直接多載之運算子的功能，請建立接受適當參數並傳回適當值的 `Function` 程序。</span><span class="sxs-lookup"><span data-stu-id="cc24e-116">If you need the functionality of overloading an operator that you cannot overload directly, create a `Function` procedure that takes the appropriate parameters and returns the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc24e-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc24e-117">See Also</span></span>  
 [<span data-ttu-id="cc24e-118">Operator 陳述式</span><span class="sxs-lookup"><span data-stu-id="cc24e-118">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="cc24e-119">運算子程序</span><span class="sxs-lookup"><span data-stu-id="cc24e-119">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [<span data-ttu-id="cc24e-120">如何：定義運算子</span><span class="sxs-lookup"><span data-stu-id="cc24e-120">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="cc24e-121">如何：定義轉換運算子</span><span class="sxs-lookup"><span data-stu-id="cc24e-121">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="cc24e-122">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="cc24e-122">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
