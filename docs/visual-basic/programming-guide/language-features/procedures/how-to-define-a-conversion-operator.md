---
title: "如何：定義轉換運算子 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b0f9e63ba039a48226186fa4ce118d3e47b5673e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a><span data-ttu-id="c079f-102">如何：定義轉換運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c079f-102">How to: Define a Conversion Operator (Visual Basic)</span></span>
<span data-ttu-id="c079f-103">如果您已定義類別或結構，您可以定義類別或結構的類型和其他資料型別之間型別轉換運算子 (例如`Integer`， `Double`，或`String`)。</span><span class="sxs-lookup"><span data-stu-id="c079f-103">If you have defined a class or structure, you can define a type conversion operator between the type of your class or structure and another data type (such as `Integer`, `Double`, or `String`).</span></span>  
  
 <span data-ttu-id="c079f-104">定義型別轉換為[CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)類別或結構中的程序。</span><span class="sxs-lookup"><span data-stu-id="c079f-104">Define the type conversion as a [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) procedure within the class or structure.</span></span> <span data-ttu-id="c079f-105">所有的轉換程序必須是`Public Shared`，和每個必須指定[Widening](../../../../visual-basic/language-reference/modifiers/widening.md)或[Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)。</span><span class="sxs-lookup"><span data-stu-id="c079f-105">All conversion procedures must be `Public Shared`, and each one must specify either [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) or [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).</span></span>  
  
 <span data-ttu-id="c079f-106">在類別或結構上定義運算子，也稱為*多載*運算子。</span><span class="sxs-lookup"><span data-stu-id="c079f-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c079f-107">範例</span><span class="sxs-lookup"><span data-stu-id="c079f-107">Example</span></span>  
 <span data-ttu-id="c079f-108">下列範例會定義稱為結構之間的轉換運算子`digit`和`Byte`。</span><span class="sxs-lookup"><span data-stu-id="c079f-108">The following example defines conversion operators between a structure called `digit` and a `Byte`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#27](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_1.vb)]  
  
 <span data-ttu-id="c079f-109">您可以測試的結構`digit`為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="c079f-109">You can test the structure `digit` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#28](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c079f-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c079f-110">See Also</span></span>  
 [<span data-ttu-id="c079f-111">運算子程序</span><span class="sxs-lookup"><span data-stu-id="c079f-111">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="c079f-112">如何：定義運算子</span><span class="sxs-lookup"><span data-stu-id="c079f-112">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)  
 [<span data-ttu-id="c079f-113">如何：呼叫運算子程序</span><span class="sxs-lookup"><span data-stu-id="c079f-113">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)  
 [<span data-ttu-id="c079f-114">如何：使用定義運算子的類別</span><span class="sxs-lookup"><span data-stu-id="c079f-114">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)  
 [<span data-ttu-id="c079f-115">Operator 陳述式</span><span class="sxs-lookup"><span data-stu-id="c079f-115">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="c079f-116">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="c079f-116">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="c079f-117">如何：宣告結構</span><span class="sxs-lookup"><span data-stu-id="c079f-117">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="c079f-118">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="c079f-118">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="c079f-119">擴展和縮小轉換</span><span class="sxs-lookup"><span data-stu-id="c079f-119">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
