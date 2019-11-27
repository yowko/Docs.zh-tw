---
title: 如何：呼叫運算子程序
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedure calls [Visual Basic], operator overloading
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- overloaded operators [Visual Basic], calling
- operator overloading
ms.assetid: 0dce42cc-f0b0-4c14-9f62-018b21f33497
ms.openlocfilehash: a685be7cc3b346b271413e2c29faae5a839313f4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340237"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a><span data-ttu-id="eda5d-102">如何：呼叫運算子程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eda5d-102">How to: Call an Operator Procedure (Visual Basic)</span></span>
<span data-ttu-id="eda5d-103">您可以在運算式中使用運算子符號來呼叫運算子程式。</span><span class="sxs-lookup"><span data-stu-id="eda5d-103">You call an operator procedure by using the operator symbol in an expression.</span></span> <span data-ttu-id="eda5d-104">在轉換運算子的情況下，您可以呼叫[CType](../../../../visual-basic/language-reference/functions/ctype-function.md)函式，將值從一種資料類型轉換成另一種。</span><span class="sxs-lookup"><span data-stu-id="eda5d-104">In the case of a conversion operator, you call the [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) to convert a value from one data type to another.</span></span>  
  
 <span data-ttu-id="eda5d-105">您不會明確地呼叫運算子程式。</span><span class="sxs-lookup"><span data-stu-id="eda5d-105">You do not call operator procedures explicitly.</span></span> <span data-ttu-id="eda5d-106">您只要在指派語句或運算式中使用運算子或 `CType` 函數，就像平常使用運算子一樣。</span><span class="sxs-lookup"><span data-stu-id="eda5d-106">You just use the operator, or the `CType` function, in an assignment statement or an expression, the same way you ordinarily use an operator.</span></span> <span data-ttu-id="eda5d-107">Visual Basic 會呼叫運算子程式。</span><span class="sxs-lookup"><span data-stu-id="eda5d-107">Visual Basic makes the call to the operator procedure.</span></span>  
  
 <span data-ttu-id="eda5d-108">在類別或結構上定義運算子*也稱為多*載運算子。</span><span class="sxs-lookup"><span data-stu-id="eda5d-108">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
### <a name="to-call-an-operator-procedure"></a><span data-ttu-id="eda5d-109">呼叫運算子程式</span><span class="sxs-lookup"><span data-stu-id="eda5d-109">To call an operator procedure</span></span>  
  
1. <span data-ttu-id="eda5d-110">以一般方式在運算式中使用運算子符號。</span><span class="sxs-lookup"><span data-stu-id="eda5d-110">Use the operator symbol in an expression in the ordinary way.</span></span>  
  
2. <span data-ttu-id="eda5d-111">請確定運算元的資料類型適用于運算子，並以正確的順序排列。</span><span class="sxs-lookup"><span data-stu-id="eda5d-111">Be sure the data types of the operands are appropriate for the operator, and in the correct order.</span></span>  
  
3. <span data-ttu-id="eda5d-112">運算子會如預期般貢獻運算式的值。</span><span class="sxs-lookup"><span data-stu-id="eda5d-112">The operator contributes to the value of the expression as expected.</span></span>  
  
### <a name="to-call-a-conversion-operator-procedure"></a><span data-ttu-id="eda5d-113">呼叫轉換運算子程式</span><span class="sxs-lookup"><span data-stu-id="eda5d-113">To call a conversion operator procedure</span></span>  
  
1. <span data-ttu-id="eda5d-114">在運算式內使用 `CType`。</span><span class="sxs-lookup"><span data-stu-id="eda5d-114">Use `CType` inside an expression.</span></span>  
  
2. <span data-ttu-id="eda5d-115">請確定運算元的資料類型適用于轉換，並以正確的順序排列。</span><span class="sxs-lookup"><span data-stu-id="eda5d-115">Be sure the data types of the operands are appropriate for the conversion, and in the correct order.</span></span>  
  
3. <span data-ttu-id="eda5d-116">`CType` 會呼叫轉換運算子程式，並傳回轉換後的值。</span><span class="sxs-lookup"><span data-stu-id="eda5d-116">`CType` calls the conversion operator procedure and returns the converted value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eda5d-117">範例</span><span class="sxs-lookup"><span data-stu-id="eda5d-117">Example</span></span>  
 <span data-ttu-id="eda5d-118">下列範例會建立兩個 <xref:System.TimeSpan> 結構，將它們相加，然後將結果儲存在第三個 <xref:System.TimeSpan> 結構中。</span><span class="sxs-lookup"><span data-stu-id="eda5d-118">The following example creates two <xref:System.TimeSpan> structures, adds them together, and stores the result in a third <xref:System.TimeSpan> structure.</span></span> <span data-ttu-id="eda5d-119"><xref:System.TimeSpan> 結構會定義運算子程式來多載數個標準運算子。</span><span class="sxs-lookup"><span data-stu-id="eda5d-119">The <xref:System.TimeSpan> structure defines operator procedures to overload several standard operators.</span></span>  
  
 [!code-vb[VbVbcnProcedures#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#29)]  
  
 <span data-ttu-id="eda5d-120">因為 <xref:System.TimeSpan> 會多載標準 `+` 運算子，所以先前的範例會在計算 `combinedSpan`的值時呼叫 operator 程式。</span><span class="sxs-lookup"><span data-stu-id="eda5d-120">Because <xref:System.TimeSpan> overloads the standard `+` operator, the previous example calls an operator procedure when it calculates the value of `combinedSpan`.</span></span>  
  
 <span data-ttu-id="eda5d-121">如需呼叫交談運算子程式的範例，請參閱[如何：使用定義運算子的類別](./how-to-use-a-class-that-defines-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="eda5d-121">For an example of calling a conversation operator procedure, see [How to: Use a Class that Defines Operators](./how-to-use-a-class-that-defines-operators.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="eda5d-122">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="eda5d-122">Compiling the Code</span></span>  
 <span data-ttu-id="eda5d-123">請確定您所使用的類別或結構會定義您想要使用的運算子。</span><span class="sxs-lookup"><span data-stu-id="eda5d-123">Be sure the class or structure you are using defines the operator you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eda5d-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="eda5d-124">See also</span></span>

- [<span data-ttu-id="eda5d-125">運算子程序</span><span class="sxs-lookup"><span data-stu-id="eda5d-125">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="eda5d-126">如何：定義運算子</span><span class="sxs-lookup"><span data-stu-id="eda5d-126">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="eda5d-127">如何：定義轉換運算子</span><span class="sxs-lookup"><span data-stu-id="eda5d-127">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="eda5d-128">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="eda5d-128">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="eda5d-129">Widening</span><span class="sxs-lookup"><span data-stu-id="eda5d-129">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="eda5d-130">Narrowing</span><span class="sxs-lookup"><span data-stu-id="eda5d-130">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="eda5d-131">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="eda5d-131">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="eda5d-132">如何：宣告結構</span><span class="sxs-lookup"><span data-stu-id="eda5d-132">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="eda5d-133">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="eda5d-133">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="eda5d-134">擴展和縮小轉換</span><span class="sxs-lookup"><span data-stu-id="eda5d-134">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
