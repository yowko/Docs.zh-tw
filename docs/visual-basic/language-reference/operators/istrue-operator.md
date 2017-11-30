---
title: "IsTrue 運算子 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c0d261186ce68f06cec95251e815248a189f6da5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="istrue-operator-visual-basic"></a><span data-ttu-id="42fca-102">IsTrue 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42fca-102">IsTrue Operator (Visual Basic)</span></span>
<span data-ttu-id="42fca-103">判斷運算式是否為`True`。</span><span class="sxs-lookup"><span data-stu-id="42fca-103">Determines whether an expression is `True`.</span></span>  
  
 <span data-ttu-id="42fca-104">您不能呼叫`IsTrue`明確地在您的程式碼，但 Visual Basic 編譯器可以用它來產生程式碼從`OrElse`子句。</span><span class="sxs-lookup"><span data-stu-id="42fca-104">You cannot call `IsTrue` explicitly in your code, but the Visual Basic compiler can use it to generate code from `OrElse` clauses.</span></span> <span data-ttu-id="42fca-105">如果您定義類別或結構，然後使用 在該類型的變數`OrElse`子句，您必須定義`IsTrue`該類別或結構上。</span><span class="sxs-lookup"><span data-stu-id="42fca-105">If you define a class or structure and then use a variable of that type in an `OrElse` clause, you must define `IsTrue` on that class or structure.</span></span>  
  
 <span data-ttu-id="42fca-106">編譯器會考慮`IsTrue`和`IsFalse`運算子*相符配對*。</span><span class="sxs-lookup"><span data-stu-id="42fca-106">The compiler considers the `IsTrue` and `IsFalse` operators as a *matched pair*.</span></span> <span data-ttu-id="42fca-107">這表示，如果您定義其中一個，您也必須定義，另一個。</span><span class="sxs-lookup"><span data-stu-id="42fca-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
## <a name="compiler-use-of-istrue"></a><span data-ttu-id="42fca-108">IsTrue 的編譯器使用</span><span class="sxs-lookup"><span data-stu-id="42fca-108">Compiler Use of IsTrue</span></span>  
 <span data-ttu-id="42fca-109">當您已經定義類別或結構時，您可以使用在該類型的變數`For`， `If`， `Else``If`，或`While`陳述式，或在`When`子句。</span><span class="sxs-lookup"><span data-stu-id="42fca-109">When you have defined a class or structure, you can use a variable of that type in a `For`, `If`, `Else``If`, or `While` statement, or in a `When` clause.</span></span> <span data-ttu-id="42fca-110">如果這樣做，編譯器會要求將轉換成您類型的運算子`Boolean`值讓它可以測試條件。</span><span class="sxs-lookup"><span data-stu-id="42fca-110">If you do this, the compiler requires an operator that converts your type into a `Boolean` value so it can test a condition.</span></span> <span data-ttu-id="42fca-111">它會搜尋適當的運算子，以下列順序：</span><span class="sxs-lookup"><span data-stu-id="42fca-111">It searches for a suitable operator in the following order:</span></span>  
  
1.  <span data-ttu-id="42fca-112">擴展的轉換運算子，從您的類別或結構`Boolean`。</span><span class="sxs-lookup"><span data-stu-id="42fca-112">A widening conversion operator from your class or structure to `Boolean`.</span></span>  
  
2.  <span data-ttu-id="42fca-113">擴展的轉換運算子，從您的類別或結構`Boolean?`。</span><span class="sxs-lookup"><span data-stu-id="42fca-113">A widening conversion operator from your class or structure to `Boolean?`.</span></span>  
  
3.  <span data-ttu-id="42fca-114">`IsTrue`上類別或結構的運算子。</span><span class="sxs-lookup"><span data-stu-id="42fca-114">The `IsTrue` operator on your class or structure.</span></span>  
  
4.  <span data-ttu-id="42fca-115">若要縮小轉換`Boolean?`並不會從轉換`Boolean`至`Boolean?`。</span><span class="sxs-lookup"><span data-stu-id="42fca-115">A narrowing conversion to `Boolean?` that does not involve a conversion from `Boolean` to `Boolean?`.</span></span>  
  
5.  <span data-ttu-id="42fca-116">從您的類別或結構，以縮小轉換運算子`Boolean`。</span><span class="sxs-lookup"><span data-stu-id="42fca-116">A narrowing conversion operator from your class or structure to `Boolean`.</span></span>  
  
 <span data-ttu-id="42fca-117">如果您還沒有定義任何轉換`Boolean`或`IsTrue`運算子，編譯器會發出錯誤信號。</span><span class="sxs-lookup"><span data-stu-id="42fca-117">If you have not defined any conversion to `Boolean` or an `IsTrue` operator, the compiler signals an error.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="42fca-118">`IsTrue`運算子可以是*多載*，這表示，類別或結構可以重新定義它的行為時其運算元的該類別或結構的類型。</span><span class="sxs-lookup"><span data-stu-id="42fca-118">The `IsTrue` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="42fca-119">如果您的程式碼會使用此運算子，這類類別或結構上，請確定您了解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="42fca-119">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="42fca-120">如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="42fca-120">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="42fca-121">範例</span><span class="sxs-lookup"><span data-stu-id="42fca-121">Example</span></span>  
 <span data-ttu-id="42fca-122">下列程式碼範例定義的結構，其中包含定義外框`IsFalse`和`IsTrue`運算子。</span><span class="sxs-lookup"><span data-stu-id="42fca-122">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/istrue-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="42fca-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42fca-123">See Also</span></span>  
 [<span data-ttu-id="42fca-124">IsFalse 運算子</span><span class="sxs-lookup"><span data-stu-id="42fca-124">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)  
 [<span data-ttu-id="42fca-125">如何：定義運算子</span><span class="sxs-lookup"><span data-stu-id="42fca-125">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="42fca-126">OrElse 運算子</span><span class="sxs-lookup"><span data-stu-id="42fca-126">OrElse Operator</span></span>](../../../visual-basic/language-reference/operators/orelse-operator.md)
