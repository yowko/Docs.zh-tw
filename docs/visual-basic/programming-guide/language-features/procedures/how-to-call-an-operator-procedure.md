---
title: HOW TO：呼叫運算子程序 (Visual Basic)
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
ms.openlocfilehash: d68781aa12ab7c1c717031ca252c5f3120649edc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61863931"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a><span data-ttu-id="9af6b-102">HOW TO：呼叫運算子程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9af6b-102">How to: Call an Operator Procedure (Visual Basic)</span></span>
<span data-ttu-id="9af6b-103">您可以在運算式中使用運算子符號，以呼叫運算子程序。</span><span class="sxs-lookup"><span data-stu-id="9af6b-103">You call an operator procedure by using the operator symbol in an expression.</span></span> <span data-ttu-id="9af6b-104">轉換運算子，在您呼叫[CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)將值從一種資料類型轉換到另一個。</span><span class="sxs-lookup"><span data-stu-id="9af6b-104">In the case of a conversion operator, you call the [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) to convert a value from one data type to another.</span></span>  
  
 <span data-ttu-id="9af6b-105">您未明確呼叫運算子程序。</span><span class="sxs-lookup"><span data-stu-id="9af6b-105">You do not call operator procedures explicitly.</span></span> <span data-ttu-id="9af6b-106">您只使用運算子，或`CType`函式，在指派陳述式或運算式，您通常會使用運算子相同的方式。</span><span class="sxs-lookup"><span data-stu-id="9af6b-106">You just use the operator, or the `CType` function, in an assignment statement or an expression, the same way you ordinarily use an operator.</span></span> <span data-ttu-id="9af6b-107">Visual Basic 可讓運算子程序的呼叫。</span><span class="sxs-lookup"><span data-stu-id="9af6b-107">Visual Basic makes the call to the operator procedure.</span></span>  
  
 <span data-ttu-id="9af6b-108">類別或結構上定義的運算子，也稱為*多載*運算子。</span><span class="sxs-lookup"><span data-stu-id="9af6b-108">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
### <a name="to-call-an-operator-procedure"></a><span data-ttu-id="9af6b-109">若要呼叫運算子程序</span><span class="sxs-lookup"><span data-stu-id="9af6b-109">To call an operator procedure</span></span>  
  
1. <span data-ttu-id="9af6b-110">在運算式中使用運算子符號，以一般方式。</span><span class="sxs-lookup"><span data-stu-id="9af6b-110">Use the operator symbol in an expression in the ordinary way.</span></span>  
  
2. <span data-ttu-id="9af6b-111">請確定資料類型的運算元是適用於運算子，且有正確的順序。</span><span class="sxs-lookup"><span data-stu-id="9af6b-111">Be sure the data types of the operands are appropriate for the operator, and in the correct order.</span></span>  
  
3. <span data-ttu-id="9af6b-112">如預期般，運算子會提供給運算式的值。</span><span class="sxs-lookup"><span data-stu-id="9af6b-112">The operator contributes to the value of the expression as expected.</span></span>  
  
### <a name="to-call-a-conversion-operator-procedure"></a><span data-ttu-id="9af6b-113">若要呼叫的轉換運算子程序</span><span class="sxs-lookup"><span data-stu-id="9af6b-113">To call a conversion operator procedure</span></span>  
  
1. <span data-ttu-id="9af6b-114">使用`CType`在運算式中。</span><span class="sxs-lookup"><span data-stu-id="9af6b-114">Use `CType` inside an expression.</span></span>  
  
2. <span data-ttu-id="9af6b-115">請確定資料類型的運算元會適當轉換，並以正確的順序。</span><span class="sxs-lookup"><span data-stu-id="9af6b-115">Be sure the data types of the operands are appropriate for the conversion, and in the correct order.</span></span>  
  
3. <span data-ttu-id="9af6b-116">`CType` 呼叫轉換運算子程序，並傳回已轉換的值。</span><span class="sxs-lookup"><span data-stu-id="9af6b-116">`CType` calls the conversion operator procedure and returns the converted value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9af6b-117">範例</span><span class="sxs-lookup"><span data-stu-id="9af6b-117">Example</span></span>  
 <span data-ttu-id="9af6b-118">下列範例會建立兩個<xref:System.TimeSpan>、 將它們相加，並將結果儲存在第三個<xref:System.TimeSpan>結構。</span><span class="sxs-lookup"><span data-stu-id="9af6b-118">The following example creates two <xref:System.TimeSpan> structures, adds them together, and stores the result in a third <xref:System.TimeSpan> structure.</span></span> <span data-ttu-id="9af6b-119"><xref:System.TimeSpan>結構會定義數個標準運算子的多載的運算子程序。</span><span class="sxs-lookup"><span data-stu-id="9af6b-119">The <xref:System.TimeSpan> structure defines operator procedures to overload several standard operators.</span></span>  
  
 [!code-vb[VbVbcnProcedures#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#29)]  
  
 <span data-ttu-id="9af6b-120">因為<xref:System.TimeSpan>多載標準`+`運算子，前一個範例會呼叫運算子程序計算的值時`combinedSpan`。</span><span class="sxs-lookup"><span data-stu-id="9af6b-120">Because <xref:System.TimeSpan> overloads the standard `+` operator, the previous example calls an operator procedure when it calculates the value of `combinedSpan`.</span></span>  
  
 <span data-ttu-id="9af6b-121">如需呼叫交談運算子程序的範例，請參閱[How to:使用定義運算子的類別](./how-to-use-a-class-that-defines-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="9af6b-121">For an example of calling a conversation operator procedure, see [How to: Use a Class that Defines Operators](./how-to-use-a-class-that-defines-operators.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9af6b-122">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="9af6b-122">Compiling the Code</span></span>  
 <span data-ttu-id="9af6b-123">請務必在類別或您使用的結構會定義您想要使用的運算子。</span><span class="sxs-lookup"><span data-stu-id="9af6b-123">Be sure the class or structure you are using defines the operator you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9af6b-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9af6b-124">See also</span></span>

- [<span data-ttu-id="9af6b-125">運算子程序</span><span class="sxs-lookup"><span data-stu-id="9af6b-125">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="9af6b-126">如何：定義運算子</span><span class="sxs-lookup"><span data-stu-id="9af6b-126">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="9af6b-127">如何：定義轉換運算子</span><span class="sxs-lookup"><span data-stu-id="9af6b-127">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="9af6b-128">Operator 陳述式</span><span class="sxs-lookup"><span data-stu-id="9af6b-128">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="9af6b-129">Widening</span><span class="sxs-lookup"><span data-stu-id="9af6b-129">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="9af6b-130">Narrowing</span><span class="sxs-lookup"><span data-stu-id="9af6b-130">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="9af6b-131">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="9af6b-131">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="9af6b-132">如何：宣告結構</span><span class="sxs-lookup"><span data-stu-id="9af6b-132">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="9af6b-133">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="9af6b-133">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="9af6b-134">擴展和縮小轉換</span><span class="sxs-lookup"><span data-stu-id="9af6b-134">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
