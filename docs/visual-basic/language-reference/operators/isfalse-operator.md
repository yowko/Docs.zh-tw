---
title: IsFalse 運算子
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: bbcdb9bcf645a4e9cb54c657ccd46e04437d207e
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873378"
---
# <a name="isfalse-operator-visual-basic"></a><span data-ttu-id="19944-102">IsFalse 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19944-102">IsFalse Operator (Visual Basic)</span></span>

<span data-ttu-id="19944-103">判斷運算式是否為 `False` 。</span><span class="sxs-lookup"><span data-stu-id="19944-103">Determines whether an expression is `False`.</span></span>  
  
 <span data-ttu-id="19944-104">您無法 `IsFalse` 在程式碼中明確呼叫，但是 Visual Basic 編譯器可以使用它從子句產生程式碼 `AndAlso` 。</span><span class="sxs-lookup"><span data-stu-id="19944-104">You cannot call `IsFalse` explicitly in your code, but the Visual Basic compiler can use it to generate code from `AndAlso` clauses.</span></span> <span data-ttu-id="19944-105">如果您定義類別或結構，然後在子句中使用該類型的變數 `AndAlso` ，則必須 `IsFalse` 在該類別或結構上定義。</span><span class="sxs-lookup"><span data-stu-id="19944-105">If you define a class or structure and then use a variable of that type in an `AndAlso` clause, you must define `IsFalse` on that class or structure.</span></span>  
  
 <span data-ttu-id="19944-106">編譯器會將 `IsFalse` 和 `IsTrue` 運算子視為相符的 *配對*。</span><span class="sxs-lookup"><span data-stu-id="19944-106">The compiler considers the `IsFalse` and `IsTrue` operators as a *matched pair*.</span></span> <span data-ttu-id="19944-107">這表示，如果您定義其中一個，您也必須定義另一個。</span><span class="sxs-lookup"><span data-stu-id="19944-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="19944-108">可以多載 `IsFalse` 運算子*overloaded*，這表示類別或結構在其運算元具有該類別或結構的型別時，可以重新定義其行為。</span><span class="sxs-lookup"><span data-stu-id="19944-108">The `IsFalse` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="19944-109">如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="19944-109">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="19944-110">如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="19944-110">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="19944-111">範例</span><span class="sxs-lookup"><span data-stu-id="19944-111">Example</span></span>  

 <span data-ttu-id="19944-112">下列程式碼範例會定義結構的外框，其中包含 `IsFalse` 和運算子的定義 `IsTrue` 。</span><span class="sxs-lookup"><span data-stu-id="19944-112">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="19944-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19944-113">See also</span></span>

- [<span data-ttu-id="19944-114">IsTrue 運算子</span><span class="sxs-lookup"><span data-stu-id="19944-114">IsTrue Operator</span></span>](istrue-operator.md)
- [<span data-ttu-id="19944-115">如何：定義運算子</span><span class="sxs-lookup"><span data-stu-id="19944-115">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="19944-116">AndAlso 運算子</span><span class="sxs-lookup"><span data-stu-id="19944-116">AndAlso Operator</span></span>](andalso-operator.md)
