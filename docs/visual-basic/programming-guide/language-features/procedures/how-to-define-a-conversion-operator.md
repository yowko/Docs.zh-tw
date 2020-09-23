---
title: 'How to: Define a Conversion Operator'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
ms.openlocfilehash: 2fabcf6c6ceb38fe77d4eed4f02dcb5a5e447bf1
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085668"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a><span data-ttu-id="a428a-102">如何：定義轉換運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a428a-102">How to: Define a Conversion Operator (Visual Basic)</span></span>

<span data-ttu-id="a428a-103">如果您已定義類別或結構，則可以在類別或結構的型別與另一個資料類型 (（例如 `Integer` 、或) ）之間定義型別轉換運算子 `Double` `String` 。</span><span class="sxs-lookup"><span data-stu-id="a428a-103">If you have defined a class or structure, you can define a type conversion operator between the type of your class or structure and another data type (such as `Integer`, `Double`, or `String`).</span></span>  
  
 <span data-ttu-id="a428a-104">將類型轉換定義為類別或結構中的 [CType 函數](../../../language-reference/functions/ctype-function.md) 程式。</span><span class="sxs-lookup"><span data-stu-id="a428a-104">Define the type conversion as a [CType Function](../../../language-reference/functions/ctype-function.md) procedure within the class or structure.</span></span> <span data-ttu-id="a428a-105">所有的轉換程式都必須是 `Public Shared` ，而且每一個都必須指定 [擴展](../../../language-reference/modifiers/widening.md) 或 [縮小](../../../language-reference/modifiers/narrowing.md)。</span><span class="sxs-lookup"><span data-stu-id="a428a-105">All conversion procedures must be `Public Shared`, and each one must specify either [Widening](../../../language-reference/modifiers/widening.md) or [Narrowing](../../../language-reference/modifiers/narrowing.md).</span></span>  
  
 <span data-ttu-id="a428a-106">在類別或結構上定義運算子 *也稱為多* 載運算子。</span><span class="sxs-lookup"><span data-stu-id="a428a-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a428a-107">範例</span><span class="sxs-lookup"><span data-stu-id="a428a-107">Example</span></span>  

 <span data-ttu-id="a428a-108">下列範例會定義名為和的結構之間的轉換運算子 `digit` `Byte` 。</span><span class="sxs-lookup"><span data-stu-id="a428a-108">The following example defines conversion operators between a structure called `digit` and a `Byte`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#27)]  
  
 <span data-ttu-id="a428a-109">您可以使用下列程式碼來測試結構 `digit` 。</span><span class="sxs-lookup"><span data-stu-id="a428a-109">You can test the structure `digit` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="a428a-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a428a-110">See also</span></span>

- [<span data-ttu-id="a428a-111">運算子程序</span><span class="sxs-lookup"><span data-stu-id="a428a-111">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="a428a-112">如何：定義運算子</span><span class="sxs-lookup"><span data-stu-id="a428a-112">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="a428a-113">如何：呼叫運算子程序</span><span class="sxs-lookup"><span data-stu-id="a428a-113">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="a428a-114">如何：使用定義運算子的類別</span><span class="sxs-lookup"><span data-stu-id="a428a-114">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
- [<span data-ttu-id="a428a-115">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="a428a-115">Operator Statement</span></span>](../../../language-reference/statements/operator-statement.md)
- [<span data-ttu-id="a428a-116">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="a428a-116">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="a428a-117">作法：宣告結構</span><span class="sxs-lookup"><span data-stu-id="a428a-117">How to: Declare a Structure</span></span>](../data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="a428a-118">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="a428a-118">Implicit and Explicit Conversions</span></span>](../data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="a428a-119">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="a428a-119">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)
