---
title: IsFalse 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: 85fd6b9264fa80c3636f2cb839c8fc5ed855ddc8
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965653"
---
# <a name="isfalse-operator-visual-basic"></a><span data-ttu-id="337bc-102">IsFalse 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="337bc-102">IsFalse Operator (Visual Basic)</span></span>
<span data-ttu-id="337bc-103">判斷運算式是否為`False`。</span><span class="sxs-lookup"><span data-stu-id="337bc-103">Determines whether an expression is `False`.</span></span>  
  
 <span data-ttu-id="337bc-104">您不能呼叫`IsFalse`明確地在您的程式碼，但 Visual Basic 編譯器可以用它來產生程式碼從`AndAlso`子句。</span><span class="sxs-lookup"><span data-stu-id="337bc-104">You cannot call `IsFalse` explicitly in your code, but the Visual Basic compiler can use it to generate code from `AndAlso` clauses.</span></span> <span data-ttu-id="337bc-105">如果您定義類別或結構，然後使用 在該類型的變數`AndAlso`子句中，您必須定義`IsFalse`該類別或結構上。</span><span class="sxs-lookup"><span data-stu-id="337bc-105">If you define a class or structure and then use a variable of that type in an `AndAlso` clause, you must define `IsFalse` on that class or structure.</span></span>  
  
 <span data-ttu-id="337bc-106">編譯器會考慮`IsFalse`並`IsTrue`做為運算子*比對組*。</span><span class="sxs-lookup"><span data-stu-id="337bc-106">The compiler considers the `IsFalse` and `IsTrue` operators as a *matched pair*.</span></span> <span data-ttu-id="337bc-107">這表示，如果您定義其中一個，您也必須定義，另一個。</span><span class="sxs-lookup"><span data-stu-id="337bc-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="337bc-108">`IsFalse`運算子只能*多載*，這表示，類別或結構可以重新定義其行為時其運算元的該類別或結構的類型。</span><span class="sxs-lookup"><span data-stu-id="337bc-108">The `IsFalse` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="337bc-109">如果您的程式碼會使用這個運算子，這類類別或結構上，請務必了解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="337bc-109">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="337bc-110">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="337bc-110">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="337bc-111">範例</span><span class="sxs-lookup"><span data-stu-id="337bc-111">Example</span></span>  
 <span data-ttu-id="337bc-112">下列程式碼範例會定義結構，其中包含定義的外框`IsFalse`和`IsTrue`運算子。</span><span class="sxs-lookup"><span data-stu-id="337bc-112">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="337bc-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="337bc-113">See also</span></span>
- [<span data-ttu-id="337bc-114">IsTrue 運算子</span><span class="sxs-lookup"><span data-stu-id="337bc-114">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [<span data-ttu-id="337bc-115">如何：定義運算子</span><span class="sxs-lookup"><span data-stu-id="337bc-115">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="337bc-116">AndAlso 運算子</span><span class="sxs-lookup"><span data-stu-id="337bc-116">AndAlso Operator</span></span>](../../../visual-basic/language-reference/operators/andalso-operator.md)
