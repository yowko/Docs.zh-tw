---
title: IsTrue 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: cb8ad8cb4a1ec13611edfcc3de7f4b7eb33fc553
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829924"
---
# <a name="istrue-operator-visual-basic"></a><span data-ttu-id="98f48-102">IsTrue 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98f48-102">IsTrue Operator (Visual Basic)</span></span>
<span data-ttu-id="98f48-103">判斷運算式是否為`True`。</span><span class="sxs-lookup"><span data-stu-id="98f48-103">Determines whether an expression is `True`.</span></span>  
  
 <span data-ttu-id="98f48-104">您不能呼叫`IsTrue`明確地在您的程式碼，但 Visual Basic 編譯器可以用它來產生程式碼從`OrElse`子句。</span><span class="sxs-lookup"><span data-stu-id="98f48-104">You cannot call `IsTrue` explicitly in your code, but the Visual Basic compiler can use it to generate code from `OrElse` clauses.</span></span> <span data-ttu-id="98f48-105">如果您定義類別或結構，然後使用 在該類型的變數`OrElse`子句中，您必須定義`IsTrue`該類別或結構上。</span><span class="sxs-lookup"><span data-stu-id="98f48-105">If you define a class or structure and then use a variable of that type in an `OrElse` clause, you must define `IsTrue` on that class or structure.</span></span>  
  
 <span data-ttu-id="98f48-106">編譯器會考慮`IsTrue`並`IsFalse`做為運算子*比對組*。</span><span class="sxs-lookup"><span data-stu-id="98f48-106">The compiler considers the `IsTrue` and `IsFalse` operators as a *matched pair*.</span></span> <span data-ttu-id="98f48-107">這表示，如果您定義其中一個，您也必須定義，另一個。</span><span class="sxs-lookup"><span data-stu-id="98f48-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
## <a name="compiler-use-of-istrue"></a><span data-ttu-id="98f48-108">IsTrue 的編譯器使用</span><span class="sxs-lookup"><span data-stu-id="98f48-108">Compiler Use of IsTrue</span></span>  
 <span data-ttu-id="98f48-109">當您已定義類別或結構時，您可以使用在該類型的變數`For`， `If`， `Else If`，或`While`陳述式，或在`When`子句。</span><span class="sxs-lookup"><span data-stu-id="98f48-109">When you have defined a class or structure, you can use a variable of that type in a `For`, `If`, `Else If`, or `While` statement, or in a `When` clause.</span></span> <span data-ttu-id="98f48-110">如果您這麼做時，編譯器需要轉換成您類型的運算子`Boolean`值讓它可以測試條件。</span><span class="sxs-lookup"><span data-stu-id="98f48-110">If you do this, the compiler requires an operator that converts your type into a `Boolean` value so it can test a condition.</span></span> <span data-ttu-id="98f48-111">它會搜尋適當的運算子，以下列順序：</span><span class="sxs-lookup"><span data-stu-id="98f48-111">It searches for a suitable operator in the following order:</span></span>  
  
1.  <span data-ttu-id="98f48-112">擴展的轉換運算子，從您的類別或結構`Boolean`。</span><span class="sxs-lookup"><span data-stu-id="98f48-112">A widening conversion operator from your class or structure to `Boolean`.</span></span>  
  
2.  <span data-ttu-id="98f48-113">擴展的轉換運算子，從您的類別或結構`Boolean?`。</span><span class="sxs-lookup"><span data-stu-id="98f48-113">A widening conversion operator from your class or structure to `Boolean?`.</span></span>  
  
3.  <span data-ttu-id="98f48-114">`IsTrue`運算子，在您自己的類別或結構。</span><span class="sxs-lookup"><span data-stu-id="98f48-114">The `IsTrue` operator on your class or structure.</span></span>  
  
4.  <span data-ttu-id="98f48-115">若要縮小轉換`Boolean?`，未牽涉到從轉換`Boolean`至`Boolean?`。</span><span class="sxs-lookup"><span data-stu-id="98f48-115">A narrowing conversion to `Boolean?` that does not involve a conversion from `Boolean` to `Boolean?`.</span></span>  
  
5.  <span data-ttu-id="98f48-116">縮小的轉換運算子，從您的類別或結構`Boolean`。</span><span class="sxs-lookup"><span data-stu-id="98f48-116">A narrowing conversion operator from your class or structure to `Boolean`.</span></span>  
  
 <span data-ttu-id="98f48-117">如果您還沒有定義任何轉換成`Boolean`或`IsTrue`運算子，編譯器會發出錯誤信號。</span><span class="sxs-lookup"><span data-stu-id="98f48-117">If you have not defined any conversion to `Boolean` or an `IsTrue` operator, the compiler signals an error.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98f48-118">`IsTrue`運算子只能*多載*，這表示，類別或結構可以重新定義其行為時其運算元的該類別或結構的類型。</span><span class="sxs-lookup"><span data-stu-id="98f48-118">The `IsTrue` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="98f48-119">如果您的程式碼會使用這個運算子，這類類別或結構上，請務必了解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="98f48-119">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="98f48-120">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="98f48-120">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="98f48-121">範例</span><span class="sxs-lookup"><span data-stu-id="98f48-121">Example</span></span>  
 <span data-ttu-id="98f48-122">下列程式碼範例會定義結構，其中包含定義的外框`IsFalse`和`IsTrue`運算子。</span><span class="sxs-lookup"><span data-stu-id="98f48-122">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="98f48-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98f48-123">See also</span></span>

- [<span data-ttu-id="98f48-124">IsFalse 運算子</span><span class="sxs-lookup"><span data-stu-id="98f48-124">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [<span data-ttu-id="98f48-125">如何：定義運算子</span><span class="sxs-lookup"><span data-stu-id="98f48-125">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="98f48-126">OrElse 運算子</span><span class="sxs-lookup"><span data-stu-id="98f48-126">OrElse Operator</span></span>](../../../visual-basic/language-reference/operators/orelse-operator.md)
