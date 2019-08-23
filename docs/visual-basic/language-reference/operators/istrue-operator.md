---
title: IsTrue 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: 1152f4b512a85ae183f8fc8d476b69685e2926ef
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966923"
---
# <a name="istrue-operator-visual-basic"></a><span data-ttu-id="cc56e-102">IsTrue 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc56e-102">IsTrue Operator (Visual Basic)</span></span>
<span data-ttu-id="cc56e-103">判斷運算式是否為`True`。</span><span class="sxs-lookup"><span data-stu-id="cc56e-103">Determines whether an expression is `True`.</span></span>  
  
 <span data-ttu-id="cc56e-104">您無法在`IsTrue`程式碼中明確呼叫, 但是 Visual Basic 編譯器可以使用它來產生來自子句`OrElse`的程式碼。</span><span class="sxs-lookup"><span data-stu-id="cc56e-104">You cannot call `IsTrue` explicitly in your code, but the Visual Basic compiler can use it to generate code from `OrElse` clauses.</span></span> <span data-ttu-id="cc56e-105">如果您定義了類別或結構, 然後在`OrElse`子句中使用該類型的變數, 您必須在該類別或結構上定義。 `IsTrue`</span><span class="sxs-lookup"><span data-stu-id="cc56e-105">If you define a class or structure and then use a variable of that type in an `OrElse` clause, you must define `IsTrue` on that class or structure.</span></span>  
  
 <span data-ttu-id="cc56e-106">編譯器會將`IsTrue`和`IsFalse`運算子視為相符的*配對*。</span><span class="sxs-lookup"><span data-stu-id="cc56e-106">The compiler considers the `IsTrue` and `IsFalse` operators as a *matched pair*.</span></span> <span data-ttu-id="cc56e-107">這表示如果您定義其中一個, 則也必須定義另一個。</span><span class="sxs-lookup"><span data-stu-id="cc56e-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
## <a name="compiler-use-of-istrue"></a><span data-ttu-id="cc56e-108">編譯器使用 IsTrue</span><span class="sxs-lookup"><span data-stu-id="cc56e-108">Compiler Use of IsTrue</span></span>  
 <span data-ttu-id="cc56e-109">當您定義了類別或結構時, 可以在`For`、 `If`、 `Else If`或`While`語句中, 或在`When`子句中使用該類型的變數。</span><span class="sxs-lookup"><span data-stu-id="cc56e-109">When you have defined a class or structure, you can use a variable of that type in a `For`, `If`, `Else If`, or `While` statement, or in a `When` clause.</span></span> <span data-ttu-id="cc56e-110">如果您這樣做, 編譯器需要一個運算子, 將您的型別轉換`Boolean`成值, 讓它可以測試條件。</span><span class="sxs-lookup"><span data-stu-id="cc56e-110">If you do this, the compiler requires an operator that converts your type into a `Boolean` value so it can test a condition.</span></span> <span data-ttu-id="cc56e-111">它會依下列順序搜尋適合的運算子:</span><span class="sxs-lookup"><span data-stu-id="cc56e-111">It searches for a suitable operator in the following order:</span></span>  
  
1. <span data-ttu-id="cc56e-112">從您的類別或結構到`Boolean`的擴輾轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="cc56e-112">A widening conversion operator from your class or structure to `Boolean`.</span></span>  
  
2. <span data-ttu-id="cc56e-113">從您的類別或結構到`Boolean?`的擴輾轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="cc56e-113">A widening conversion operator from your class or structure to `Boolean?`.</span></span>  
  
3. <span data-ttu-id="cc56e-114">類別`IsTrue`或結構上的運算子。</span><span class="sxs-lookup"><span data-stu-id="cc56e-114">The `IsTrue` operator on your class or structure.</span></span>  
  
4. <span data-ttu-id="cc56e-115">的縮小轉換`Boolean?`不牽涉到從`Boolean`轉換成`Boolean?`的。</span><span class="sxs-lookup"><span data-stu-id="cc56e-115">A narrowing conversion to `Boolean?` that does not involve a conversion from `Boolean` to `Boolean?`.</span></span>  
  
5. <span data-ttu-id="cc56e-116">從您的類別或結構到`Boolean`的縮小轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="cc56e-116">A narrowing conversion operator from your class or structure to `Boolean`.</span></span>  
  
 <span data-ttu-id="cc56e-117">如果您尚未定義任何對`Boolean` `IsTrue`或運算子的轉換, 則編譯器會發出錯誤信號。</span><span class="sxs-lookup"><span data-stu-id="cc56e-117">If you have not defined any conversion to `Boolean` or an `IsTrue` operator, the compiler signals an error.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cc56e-118">運算子可以多載, 這表示當類別或結構的運算元具有該類別或結構的類型時, 可以重新定義其行為。 `IsTrue`</span><span class="sxs-lookup"><span data-stu-id="cc56e-118">The `IsTrue` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="cc56e-119">如果您的程式碼在這類類別或結構上使用這個運算子, 請務必瞭解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="cc56e-119">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="cc56e-120">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="cc56e-120">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc56e-121">範例</span><span class="sxs-lookup"><span data-stu-id="cc56e-121">Example</span></span>  
 <span data-ttu-id="cc56e-122">下列程式碼範例會定義包含`IsFalse`和`IsTrue`運算子之定義的結構外框。</span><span class="sxs-lookup"><span data-stu-id="cc56e-122">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="cc56e-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc56e-123">See also</span></span>

- [<span data-ttu-id="cc56e-124">IsFalse 運算子</span><span class="sxs-lookup"><span data-stu-id="cc56e-124">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [<span data-ttu-id="cc56e-125">如何：定義運算子</span><span class="sxs-lookup"><span data-stu-id="cc56e-125">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="cc56e-126">OrElse 運算子</span><span class="sxs-lookup"><span data-stu-id="cc56e-126">OrElse Operator</span></span>](../../../visual-basic/language-reference/operators/orelse-operator.md)
