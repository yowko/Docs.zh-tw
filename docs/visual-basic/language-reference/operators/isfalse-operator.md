---
title: IsFalse 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: 49b8493575685a220808df1522ce16835b3ce0ed
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917149"
---
# <a name="isfalse-operator-visual-basic"></a><span data-ttu-id="b6c7c-102">IsFalse 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6c7c-102">IsFalse Operator (Visual Basic)</span></span>
<span data-ttu-id="b6c7c-103">判斷運算式是否為`False`。</span><span class="sxs-lookup"><span data-stu-id="b6c7c-103">Determines whether an expression is `False`.</span></span>  
  
 <span data-ttu-id="b6c7c-104">您無法在`IsFalse`程式碼中明確呼叫, 但是 Visual Basic 編譯器可以使用它來產生來自子句`AndAlso`的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b6c7c-104">You cannot call `IsFalse` explicitly in your code, but the Visual Basic compiler can use it to generate code from `AndAlso` clauses.</span></span> <span data-ttu-id="b6c7c-105">如果您定義了類別或結構, 然後在`AndAlso`子句中使用該類型的變數, 您必須在該類別或結構上定義。 `IsFalse`</span><span class="sxs-lookup"><span data-stu-id="b6c7c-105">If you define a class or structure and then use a variable of that type in an `AndAlso` clause, you must define `IsFalse` on that class or structure.</span></span>  
  
 <span data-ttu-id="b6c7c-106">編譯器會將`IsFalse`和`IsTrue`運算子視為相符的*配對*。</span><span class="sxs-lookup"><span data-stu-id="b6c7c-106">The compiler considers the `IsFalse` and `IsTrue` operators as a *matched pair*.</span></span> <span data-ttu-id="b6c7c-107">這表示如果您定義其中一個, 則也必須定義另一個。</span><span class="sxs-lookup"><span data-stu-id="b6c7c-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b6c7c-108">運算子可以多載, 這表示當類別或結構的運算元具有該類別或結構的類型時, 可以重新定義其行為。 `IsFalse`</span><span class="sxs-lookup"><span data-stu-id="b6c7c-108">The `IsFalse` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="b6c7c-109">如果您的程式碼在這類類別或結構上使用這個運算子, 請務必瞭解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="b6c7c-109">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="b6c7c-110">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="b6c7c-110">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6c7c-111">範例</span><span class="sxs-lookup"><span data-stu-id="b6c7c-111">Example</span></span>  
 <span data-ttu-id="b6c7c-112">下列程式碼範例會定義包含`IsFalse`和`IsTrue`運算子之定義的結構外框。</span><span class="sxs-lookup"><span data-stu-id="b6c7c-112">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="b6c7c-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6c7c-113">See also</span></span>

- [<span data-ttu-id="b6c7c-114">IsTrue 運算子</span><span class="sxs-lookup"><span data-stu-id="b6c7c-114">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [<span data-ttu-id="b6c7c-115">如何：定義運算子</span><span class="sxs-lookup"><span data-stu-id="b6c7c-115">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="b6c7c-116">AndAlso 運算子</span><span class="sxs-lookup"><span data-stu-id="b6c7c-116">AndAlso Operator</span></span>](../../../visual-basic/language-reference/operators/andalso-operator.md)
