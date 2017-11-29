---
title: "如何：呼叫運算子程序 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0abff0a81ebcdacb59b69d0c307bb4aa219906c3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a><span data-ttu-id="cd7d2-102">如何：呼叫運算子程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd7d2-102">How to: Call an Operator Procedure (Visual Basic)</span></span>
<span data-ttu-id="cd7d2-103">您可以在運算式中使用運算子符號，以呼叫運算子程序。</span><span class="sxs-lookup"><span data-stu-id="cd7d2-103">You call an operator procedure by using the operator symbol in an expression.</span></span> <span data-ttu-id="cd7d2-104">如果是轉換運算子，您呼叫[CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)將值從一種資料類型轉換到另一個。</span><span class="sxs-lookup"><span data-stu-id="cd7d2-104">In the case of a conversion operator, you call the [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) to convert a value from one data type to another.</span></span>  
  
 <span data-ttu-id="cd7d2-105">您無法明確呼叫運算子程序。</span><span class="sxs-lookup"><span data-stu-id="cd7d2-105">You do not call operator procedures explicitly.</span></span> <span data-ttu-id="cd7d2-106">您只使用運算子，或`CType`函式，在指派陳述式或運算式，您通常使用運算子的相同方式。</span><span class="sxs-lookup"><span data-stu-id="cd7d2-106">You just use the operator, or the `CType` function, in an assignment statement or an expression, the same way you ordinarily use an operator.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="cd7d2-107">運算子程序呼叫。</span><span class="sxs-lookup"><span data-stu-id="cd7d2-107"> makes the call to the operator procedure.</span></span>  
  
 <span data-ttu-id="cd7d2-108">在類別或結構上定義運算子，也稱為*多載*運算子。</span><span class="sxs-lookup"><span data-stu-id="cd7d2-108">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
### <a name="to-call-an-operator-procedure"></a><span data-ttu-id="cd7d2-109">若要呼叫運算子程序</span><span class="sxs-lookup"><span data-stu-id="cd7d2-109">To call an operator procedure</span></span>  
  
1.  <span data-ttu-id="cd7d2-110">在運算式中使用運算子符號，以一般方式。</span><span class="sxs-lookup"><span data-stu-id="cd7d2-110">Use the operator symbol in an expression in the ordinary way.</span></span>  
  
2.  <span data-ttu-id="cd7d2-111">請確定資料類型的運算元是適用於運算子，且有正確的順序。</span><span class="sxs-lookup"><span data-stu-id="cd7d2-111">Be sure the data types of the operands are appropriate for the operator, and in the correct order.</span></span>  
  
3.  <span data-ttu-id="cd7d2-112">如預期般，運算子就是計算運算式的值。</span><span class="sxs-lookup"><span data-stu-id="cd7d2-112">The operator contributes to the value of the expression as expected.</span></span>  
  
### <a name="to-call-a-conversion-operator-procedure"></a><span data-ttu-id="cd7d2-113">若要呼叫轉換運算子程序</span><span class="sxs-lookup"><span data-stu-id="cd7d2-113">To call a conversion operator procedure</span></span>  
  
1.  <span data-ttu-id="cd7d2-114">使用`CType`在運算式中。</span><span class="sxs-lookup"><span data-stu-id="cd7d2-114">Use `CType` inside an expression.</span></span>  
  
2.  <span data-ttu-id="cd7d2-115">請確定資料類型的運算元不適當的轉換，並且以正確的順序。</span><span class="sxs-lookup"><span data-stu-id="cd7d2-115">Be sure the data types of the operands are appropriate for the conversion, and in the correct order.</span></span>  
  
3.  <span data-ttu-id="cd7d2-116">`CType`呼叫轉換運算子程序，並傳回已轉換的值。</span><span class="sxs-lookup"><span data-stu-id="cd7d2-116">`CType` calls the conversion operator procedure and returns the converted value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd7d2-117">範例</span><span class="sxs-lookup"><span data-stu-id="cd7d2-117">Example</span></span>  
 <span data-ttu-id="cd7d2-118">下列範例會建立兩個<xref:System.TimeSpan>、 將它們相加，並將結果儲存在第三個<xref:System.TimeSpan>結構。</span><span class="sxs-lookup"><span data-stu-id="cd7d2-118">The following example creates two <xref:System.TimeSpan> structures, adds them together, and stores the result in a third <xref:System.TimeSpan> structure.</span></span> <span data-ttu-id="cd7d2-119"><xref:System.TimeSpan>結構會定義數個標準的運算子多載的運算子程序。</span><span class="sxs-lookup"><span data-stu-id="cd7d2-119">The <xref:System.TimeSpan> structure defines operator procedures to overload several standard operators.</span></span>  
  
 [!code-vb[VbVbcnProcedures#29](./codesnippet/VisualBasic/how-to-call-an-operator-procedure_1.vb)]  
  
 <span data-ttu-id="cd7d2-120">因為<xref:System.TimeSpan>多載標準`+`運算子，前一個範例會呼叫運算子程序計算的值時`combinedSpan`。</span><span class="sxs-lookup"><span data-stu-id="cd7d2-120">Because <xref:System.TimeSpan> overloads the standard `+` operator, the previous example calls an operator procedure when it calculates the value of `combinedSpan`.</span></span>  
  
 <span data-ttu-id="cd7d2-121">如需呼叫交談運算子程序的範例，請參閱[How to： 使用類別，該定義的運算子](./how-to-use-a-class-that-defines-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="cd7d2-121">For an example of calling a conversation operator procedure, see [How to: Use a Class that Defines Operators](./how-to-use-a-class-that-defines-operators.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cd7d2-122">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="cd7d2-122">Compiling the Code</span></span>  
 <span data-ttu-id="cd7d2-123">請確定該類別或結構會使用定義您想要使用的運算子。</span><span class="sxs-lookup"><span data-stu-id="cd7d2-123">Be sure the class or structure you are using defines the operator you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd7d2-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd7d2-124">See Also</span></span>  
 [<span data-ttu-id="cd7d2-125">運算子程序</span><span class="sxs-lookup"><span data-stu-id="cd7d2-125">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="cd7d2-126">如何：定義運算子</span><span class="sxs-lookup"><span data-stu-id="cd7d2-126">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)  
 [<span data-ttu-id="cd7d2-127">如何：定義轉換運算子</span><span class="sxs-lookup"><span data-stu-id="cd7d2-127">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="cd7d2-128">Operator 陳述式</span><span class="sxs-lookup"><span data-stu-id="cd7d2-128">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="cd7d2-129">Widening</span><span class="sxs-lookup"><span data-stu-id="cd7d2-129">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)  
 [<span data-ttu-id="cd7d2-130">Narrowing</span><span class="sxs-lookup"><span data-stu-id="cd7d2-130">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [<span data-ttu-id="cd7d2-131">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="cd7d2-131">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="cd7d2-132">如何：宣告結構</span><span class="sxs-lookup"><span data-stu-id="cd7d2-132">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="cd7d2-133">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="cd7d2-133">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="cd7d2-134">擴展和縮小轉換</span><span class="sxs-lookup"><span data-stu-id="cd7d2-134">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
