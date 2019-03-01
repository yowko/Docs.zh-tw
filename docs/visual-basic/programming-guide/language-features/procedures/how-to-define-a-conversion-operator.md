---
title: HOW TO：定義轉換運算子 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
ms.openlocfilehash: fe5c314fe4e39c8a06803037da29b51148188e14
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974636"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a><span data-ttu-id="e3076-102">HOW TO：定義轉換運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3076-102">How to: Define a Conversion Operator (Visual Basic)</span></span>
<span data-ttu-id="e3076-103">如果您已定義類別或結構，您可以定義您自己的類別或結構的類型與另一個資料類型之間的型別轉換運算子 (例如`Integer`， `Double`，或`String`)。</span><span class="sxs-lookup"><span data-stu-id="e3076-103">If you have defined a class or structure, you can define a type conversion operator between the type of your class or structure and another data type (such as `Integer`, `Double`, or `String`).</span></span>  
  
 <span data-ttu-id="e3076-104">定義類型轉換成[CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)類別或結構內的程序。</span><span class="sxs-lookup"><span data-stu-id="e3076-104">Define the type conversion as a [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) procedure within the class or structure.</span></span> <span data-ttu-id="e3076-105">所有的轉換程序必須是`Public Shared`，以及每一個都必須指定[Widening](../../../../visual-basic/language-reference/modifiers/widening.md)或是[Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)。</span><span class="sxs-lookup"><span data-stu-id="e3076-105">All conversion procedures must be `Public Shared`, and each one must specify either [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) or [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).</span></span>  
  
 <span data-ttu-id="e3076-106">類別或結構上定義的運算子，也稱為*多載*運算子。</span><span class="sxs-lookup"><span data-stu-id="e3076-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3076-107">範例</span><span class="sxs-lookup"><span data-stu-id="e3076-107">Example</span></span>  
 <span data-ttu-id="e3076-108">下列範例會定義結構，稱為之間的轉換運算子`digit`和`Byte`。</span><span class="sxs-lookup"><span data-stu-id="e3076-108">The following example defines conversion operators between a structure called `digit` and a `Byte`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#27)]  
  
 <span data-ttu-id="e3076-109">您可以測試結構`digit`為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="e3076-109">You can test the structure `digit` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="e3076-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3076-110">See also</span></span>
- [<span data-ttu-id="e3076-111">運算子程序</span><span class="sxs-lookup"><span data-stu-id="e3076-111">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="e3076-112">如何：定義運算子</span><span class="sxs-lookup"><span data-stu-id="e3076-112">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="e3076-113">如何：呼叫運算子程序</span><span class="sxs-lookup"><span data-stu-id="e3076-113">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="e3076-114">如何：使用定義運算子的類別</span><span class="sxs-lookup"><span data-stu-id="e3076-114">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
- [<span data-ttu-id="e3076-115">Operator 陳述式</span><span class="sxs-lookup"><span data-stu-id="e3076-115">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="e3076-116">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="e3076-116">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="e3076-117">如何：宣告結構</span><span class="sxs-lookup"><span data-stu-id="e3076-117">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="e3076-118">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="e3076-118">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="e3076-119">擴展和縮小轉換</span><span class="sxs-lookup"><span data-stu-id="e3076-119">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
