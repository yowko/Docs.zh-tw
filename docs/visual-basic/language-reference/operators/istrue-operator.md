---
title: IsTrue 運算子
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: bc129d3a3aec76285d5ea8fb727fc72c3064c9cf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370644"
---
# <a name="istrue-operator-visual-basic"></a><span data-ttu-id="34ded-102">IsTrue 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34ded-102">IsTrue Operator (Visual Basic)</span></span>
<span data-ttu-id="34ded-103">判斷運算式是否為 `True` 。</span><span class="sxs-lookup"><span data-stu-id="34ded-103">Determines whether an expression is `True`.</span></span>  
  
 <span data-ttu-id="34ded-104">您無法 `IsTrue` 在程式碼中明確呼叫，但是 Visual Basic 編譯器可以使用它來產生來自子句的程式碼 `OrElse` 。</span><span class="sxs-lookup"><span data-stu-id="34ded-104">You cannot call `IsTrue` explicitly in your code, but the Visual Basic compiler can use it to generate code from `OrElse` clauses.</span></span> <span data-ttu-id="34ded-105">如果您定義了類別或結構，然後在子句中使用該類型的變數 `OrElse` ，您必須 `IsTrue` 在該類別或結構上定義。</span><span class="sxs-lookup"><span data-stu-id="34ded-105">If you define a class or structure and then use a variable of that type in an `OrElse` clause, you must define `IsTrue` on that class or structure.</span></span>  
  
 <span data-ttu-id="34ded-106">編譯器會將 `IsTrue` 和 `IsFalse` 運算子視為相符的*配對*。</span><span class="sxs-lookup"><span data-stu-id="34ded-106">The compiler considers the `IsTrue` and `IsFalse` operators as a *matched pair*.</span></span> <span data-ttu-id="34ded-107">這表示如果您定義其中一個，則也必須定義另一個。</span><span class="sxs-lookup"><span data-stu-id="34ded-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
## <a name="compiler-use-of-istrue"></a><span data-ttu-id="34ded-108">編譯器使用 IsTrue</span><span class="sxs-lookup"><span data-stu-id="34ded-108">Compiler Use of IsTrue</span></span>  
 <span data-ttu-id="34ded-109">當您定義了類別或結構時，可以在 `For` 、 `If` 、 `Else If` 或 `While` 語句中，或在 `When` 子句中使用該類型的變數。</span><span class="sxs-lookup"><span data-stu-id="34ded-109">When you have defined a class or structure, you can use a variable of that type in a `For`, `If`, `Else If`, or `While` statement, or in a `When` clause.</span></span> <span data-ttu-id="34ded-110">如果您這樣做，編譯器需要一個運算子，將您的型別轉換成 `Boolean` 值，讓它可以測試條件。</span><span class="sxs-lookup"><span data-stu-id="34ded-110">If you do this, the compiler requires an operator that converts your type into a `Boolean` value so it can test a condition.</span></span> <span data-ttu-id="34ded-111">它會依下列順序搜尋適合的運算子：</span><span class="sxs-lookup"><span data-stu-id="34ded-111">It searches for a suitable operator in the following order:</span></span>  
  
1. <span data-ttu-id="34ded-112">從您的類別或結構到的擴輾轉換運算子 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="34ded-112">A widening conversion operator from your class or structure to `Boolean`.</span></span>  
  
2. <span data-ttu-id="34ded-113">從您的類別或結構到的擴輾轉換運算子 `Boolean?` 。</span><span class="sxs-lookup"><span data-stu-id="34ded-113">A widening conversion operator from your class or structure to `Boolean?`.</span></span>  
  
3. <span data-ttu-id="34ded-114">`IsTrue`類別或結構上的運算子。</span><span class="sxs-lookup"><span data-stu-id="34ded-114">The `IsTrue` operator on your class or structure.</span></span>  
  
4. <span data-ttu-id="34ded-115">的縮小轉換 `Boolean?` 不牽涉到從轉換 `Boolean` 成的 `Boolean?` 。</span><span class="sxs-lookup"><span data-stu-id="34ded-115">A narrowing conversion to `Boolean?` that does not involve a conversion from `Boolean` to `Boolean?`.</span></span>  
  
5. <span data-ttu-id="34ded-116">從您的類別或結構到的縮小轉換運算子 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="34ded-116">A narrowing conversion operator from your class or structure to `Boolean`.</span></span>  
  
 <span data-ttu-id="34ded-117">如果您尚未定義任何對 `Boolean` 或運算子的轉換 `IsTrue` ，則編譯器會發出錯誤信號。</span><span class="sxs-lookup"><span data-stu-id="34ded-117">If you have not defined any conversion to `Boolean` or an `IsTrue` operator, the compiler signals an error.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="34ded-118">`IsTrue`運算子可以多載*overloaded*，這表示當類別或結構的運算元具有該類別或結構的類型時，可以重新定義其行為。</span><span class="sxs-lookup"><span data-stu-id="34ded-118">The `IsTrue` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="34ded-119">如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="34ded-119">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="34ded-120">如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="34ded-120">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="34ded-121">範例</span><span class="sxs-lookup"><span data-stu-id="34ded-121">Example</span></span>  
 <span data-ttu-id="34ded-122">下列程式碼範例會定義包含和運算子之定義的結構外框 `IsFalse` `IsTrue` 。</span><span class="sxs-lookup"><span data-stu-id="34ded-122">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="34ded-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34ded-123">See also</span></span>

- [<span data-ttu-id="34ded-124">IsFalse 運算子</span><span class="sxs-lookup"><span data-stu-id="34ded-124">IsFalse Operator</span></span>](isfalse-operator.md)
- [<span data-ttu-id="34ded-125">如何：定義運算子</span><span class="sxs-lookup"><span data-stu-id="34ded-125">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="34ded-126">OrElse 運算子</span><span class="sxs-lookup"><span data-stu-id="34ded-126">OrElse Operator</span></span>](orelse-operator.md)
