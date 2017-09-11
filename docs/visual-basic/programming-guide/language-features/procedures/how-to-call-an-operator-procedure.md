---
title: "如何︰ 呼叫運算子程序 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- operator procedures, calling
- procedures, operator
- procedure calls, operator overloading
- syntax, Operator procedures
- operators [Visual Basic], overloading
- return values, Operator procedures
- overloaded operators, calling
- operator overloading
ms.assetid: 0dce42cc-f0b0-4c14-9f62-018b21f33497
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: cd85a14a6f5534e90497268134f4b2b0cc292249
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a><span data-ttu-id="ed0c4-102">如何：呼叫運算子程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ed0c4-102">How to: Call an Operator Procedure (Visual Basic)</span></span>
<span data-ttu-id="ed0c4-103">您可以在運算式中使用運算子符號呼叫運算子程序。</span><span class="sxs-lookup"><span data-stu-id="ed0c4-103">You call an operator procedure by using the operator symbol in an expression.</span></span> <span data-ttu-id="ed0c4-104">轉換運算子，在您呼叫[CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)將值從一種資料類型轉換到另一個。</span><span class="sxs-lookup"><span data-stu-id="ed0c4-104">In the case of a conversion operator, you call the [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) to convert a value from one data type to another.</span></span>  
  
 <span data-ttu-id="ed0c4-105">您無法明確地呼叫運算子程序。</span><span class="sxs-lookup"><span data-stu-id="ed0c4-105">You do not call operator procedures explicitly.</span></span> <span data-ttu-id="ed0c4-106">您只使用運算子，或`CType`函式，在指派陳述式或運算式相同的方式，您通常使用的運算子。</span><span class="sxs-lookup"><span data-stu-id="ed0c4-106">You just use the operator, or the `CType` function, in an assignment statement or an expression, the same way you ordinarily use an operator.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="ed0c4-107">呼叫運算子程序。</span><span class="sxs-lookup"><span data-stu-id="ed0c4-107"> makes the call to the operator procedure.</span></span>  
  
 <span data-ttu-id="ed0c4-108">在類別或結構上定義運算子，也稱為*多載*運算子。</span><span class="sxs-lookup"><span data-stu-id="ed0c4-108">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
### <a name="to-call-an-operator-procedure"></a><span data-ttu-id="ed0c4-109">若要呼叫運算子程序</span><span class="sxs-lookup"><span data-stu-id="ed0c4-109">To call an operator procedure</span></span>  
  
1.  <span data-ttu-id="ed0c4-110">在運算式中使用運算子符號，以一般方式。</span><span class="sxs-lookup"><span data-stu-id="ed0c4-110">Use the operator symbol in an expression in the ordinary way.</span></span>  
  
2.  <span data-ttu-id="ed0c4-111">請確定資料類型的運算元是適用於運算子，且正確的順序。</span><span class="sxs-lookup"><span data-stu-id="ed0c4-111">Be sure the data types of the operands are appropriate for the operator, and in the correct order.</span></span>  
  
3.  <span data-ttu-id="ed0c4-112">如預期般，運算子會提供給運算式的值。</span><span class="sxs-lookup"><span data-stu-id="ed0c4-112">The operator contributes to the value of the expression as expected.</span></span>  
  
### <a name="to-call-a-conversion-operator-procedure"></a><span data-ttu-id="ed0c4-113">若要呼叫的轉換運算子程序</span><span class="sxs-lookup"><span data-stu-id="ed0c4-113">To call a conversion operator procedure</span></span>  
  
1.  <span data-ttu-id="ed0c4-114">使用`CType`運算式內。</span><span class="sxs-lookup"><span data-stu-id="ed0c4-114">Use `CType` inside an expression.</span></span>  
  
2.  <span data-ttu-id="ed0c4-115">請務必運算元的資料型別是正確的轉換，和正確的順序。</span><span class="sxs-lookup"><span data-stu-id="ed0c4-115">Be sure the data types of the operands are appropriate for the conversion, and in the correct order.</span></span>  
  
3.  <span data-ttu-id="ed0c4-116">`CType`呼叫轉換運算子程序，並傳回已轉換的值。</span><span class="sxs-lookup"><span data-stu-id="ed0c4-116">`CType` calls the conversion operator procedure and returns the converted value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed0c4-117">範例</span><span class="sxs-lookup"><span data-stu-id="ed0c4-117">Example</span></span>  
 <span data-ttu-id="ed0c4-118">下列範例會建立兩個<xref:System.TimeSpan>、 將它們相加，並將結果儲存在第三個<xref:System.TimeSpan>結構。</xref:System.TimeSpan> </xref:System.TimeSpan></span><span class="sxs-lookup"><span data-stu-id="ed0c4-118">The following example creates two <xref:System.TimeSpan> structures, adds them together, and stores the result in a third <xref:System.TimeSpan> structure.</span></span> <span data-ttu-id="ed0c4-119"><xref:System.TimeSpan>結構會定義數個標準的運算子多載的運算子程序。</xref:System.TimeSpan></span><span class="sxs-lookup"><span data-stu-id="ed0c4-119">The <xref:System.TimeSpan> structure defines operator procedures to overload several standard operators.</span></span>  
  
 <span data-ttu-id="ed0c4-120">[!code-vb[VbVbcnProcedures #&29;](./codesnippet/VisualBasic/how-to-call-an-operator-procedure_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="ed0c4-120">[!code-vb[VbVbcnProcedures#29](./codesnippet/VisualBasic/how-to-call-an-operator-procedure_1.vb)]</span></span>  
  
 <span data-ttu-id="ed0c4-121">因為<xref:System.TimeSpan>多載標準`+`運算子前, 一個範例則會呼叫運算子程序計算的值時`combinedSpan`。</xref:System.TimeSpan></span><span class="sxs-lookup"><span data-stu-id="ed0c4-121">Because <xref:System.TimeSpan> overloads the standard `+` operator, the previous example calls an operator procedure when it calculates the value of `combinedSpan`.</span></span>  
  
 <span data-ttu-id="ed0c4-122">呼叫交談運算子程序的範例，請參閱[How to︰ 使用類別的定義運算子](./how-to-use-a-class-that-defines-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="ed0c4-122">For an example of calling a conversation operator procedure, see [How to: Use a Class that Defines Operators](./how-to-use-a-class-that-defines-operators.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ed0c4-123">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="ed0c4-123">Compiling the Code</span></span>  
 <span data-ttu-id="ed0c4-124">請確定您使用的結構或類別定義您想要使用的運算子。</span><span class="sxs-lookup"><span data-stu-id="ed0c4-124">Be sure the class or structure you are using defines the operator you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed0c4-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed0c4-125">See Also</span></span>  
 <span data-ttu-id="ed0c4-126">[運算子程序](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="ed0c4-126">[Operator Procedures](./operator-procedures.md) </span></span>  
<span data-ttu-id="ed0c4-127"> [如何︰ 定義運算子](./how-to-define-an-operator.md) </span><span class="sxs-lookup"><span data-stu-id="ed0c4-127"> [How to: Define an Operator](./how-to-define-an-operator.md) </span></span>  
<span data-ttu-id="ed0c4-128"> [如何︰ 定義轉換運算子](./how-to-define-a-conversion-operator.md) </span><span class="sxs-lookup"><span data-stu-id="ed0c4-128"> [How to: Define a Conversion Operator](./how-to-define-a-conversion-operator.md) </span></span>  
<span data-ttu-id="ed0c4-129"> [Operator 陳述式](../../../../visual-basic/language-reference/statements/operator-statement.md) </span><span class="sxs-lookup"><span data-stu-id="ed0c4-129"> [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md) </span></span>  
<span data-ttu-id="ed0c4-130"> [擴展](../../../../visual-basic/language-reference/modifiers/widening.md) </span><span class="sxs-lookup"><span data-stu-id="ed0c4-130"> [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) </span></span>  
<span data-ttu-id="ed0c4-131"> [縮小](../../../../visual-basic/language-reference/modifiers/narrowing.md) </span><span class="sxs-lookup"><span data-stu-id="ed0c4-131"> [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md) </span></span>  
<span data-ttu-id="ed0c4-132"> [Structure 陳述式](../../../../visual-basic/language-reference/statements/structure-statement.md) </span><span class="sxs-lookup"><span data-stu-id="ed0c4-132"> [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md) </span></span>  
<span data-ttu-id="ed0c4-133"> [如何︰ 宣告結構](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md) </span><span class="sxs-lookup"><span data-stu-id="ed0c4-133"> [How to: Declare a Structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md) </span></span>  
<span data-ttu-id="ed0c4-134"> [隱含和明確轉換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="ed0c4-134"> [Implicit and Explicit Conversions](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) </span></span>  
<span data-ttu-id="ed0c4-135"> [擴展和縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)</span><span class="sxs-lookup"><span data-stu-id="ed0c4-135"> [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)</span></span>
